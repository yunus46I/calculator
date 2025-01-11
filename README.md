import os
import pygame
import sys

# Program Başlatma
pygame.init()

# Ekran boyutları
SCREEN_WIDTH = 800
SCREEN_HEIGHT = 600

# Renkler
BLACK = (0, 0, 0)
WHITE = (255, 255, 255)
BLUE = (0, 0, 255)

# Ekranı oluştur
screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))
pygame.display.set_caption("Animasyon Video Oluşturucu")

# Yazı tipi
font = pygame.font.Font(None, 36)

# Butonlar için sınıf
def draw_button(text, rect, color, text_color):
    pygame.draw.rect(screen, color, rect)
    text_surface = font.render(text, True, text_color)
    text_rect = text_surface.get_rect(center=rect.center)
    screen.blit(text_surface, text_rect)

# Uygulamanın ana fonksiyonu
def main():
    running = True

    # Butonların konumu
    preview_button = pygame.Rect(150, 400, 200, 50)
    start_button = pygame.Rect(450, 400, 200, 50)

    while running:
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                running = False

            elif event.type == pygame.MOUSEBUTTONDOWN:
                if preview_button.collidepoint(event.pos):
                    print("Ön İzleme Başlatıldı!")
                    # Buraya animasyon ön izleme kodu gelecek

                elif start_button.collidepoint(event.pos):
                    print("Animasyon Oluşturuluyor!")
                    # Buraya animasyon oluşturma ve kaydetme kodu gelecek

        # Ekranı temizle
        screen.fill(WHITE)

        # Başlık
        title_surface = font.render("Senaryoya Bağlı Animasyon Oluşturma", True, BLACK)
        title_rect = title_surface.get_rect(center=(SCREEN_WIDTH // 2, 100))
        screen.blit(title_surface, title_rect)

        # Butonları çiz
        draw_button("Ön İzleme", preview_button, BLUE, WHITE)
        draw_button("Başlat", start_button, BLUE, WHITE)

        # Ekranı güncelle
        pygame.display.flip()

    pygame.quit()

if __name__ == "__main__":
    main()
