# Git

Git jest to system kontroli wersji. Umożliwia zarządzanie różnymi wersjami
kodów, tekstów, itd.

Niniejszy tekst pomaga w zrozumieniu oraz zainstalowaniu aplikacji Git.

Autor: vir.

## Konto na Github.com

Przed zainstalowaniem Git-a dobrze jest utworzyć konto na stronie 
github.com. To konto będzie skojarzone z naszą aplikacją Git.
Utworzenie konta jest dosyć intuicyjne i nie będę go tutaj opisywać.

## Instalacja

### Linuks

    sudo apt install git
    sudo apt install git-all

### Windows i Mac

Na oficjalnej stronie dokumentacji Git można znaleźć sposób instalacji
w systemach Windows oraz Mac.

## Konfiguracja

Po zainstalowaniu Git-a przechodzimy do terminala. Podajemy komendę:

    git --version

W ten sposób możemy dowiedzieć się jaką wersję Git-a mamy zainstalowaną
na naszej maszynie.

Git korzysta z komend. Posiada własne komendy, które umożliwiają nam
obsługiwanie go. Na oficjalnej stronie Git-a możemy znaleźć komendy
Git.

Podajemy nasze imię i nazwisko, e-mail oraz edytor, z którego korzystamy.

    git config --global user.name "Imię i nazwisko"
    git config --global user.email adres@email.com
    git config --global core.editor edytor

Żeby sprawdzić ustawienia Git podajemy komendę

    git config --list

## Klucz SSH

Klucz SSH pozwala nam zachować bezpieczeństwo podczas łączenia się ze
zdalnym repozytorium. Repozytorium na miejsce na serwerze, na którym
znajdują się nasze pliki.

Żeby wygenerować klucz SSH w systemie Linuks podajemy odpowiednie komendy.

    ssh-keygen -t ed25519 -C "adres@email.com"

Najlepiej nic nie zmieniać w nazwie klucza, aczkolwiek jeżeli chcemy
możemy to zrobić. Jeżeli nie zmieniamy nazwy to po prostu naciskamy
klawisz Enter.

Dodajemy klucz do agenta SSH.

    eval "$(ssh-agent -s)"

    ssh-add ~/.ssh/id_ed25519

Po wygenerowaniu klucza SSH otwieramy go.

    cat ~/.ssh/id_ed25519.pub

Otwieramy przeglądarkę, logujemy się na naszym koncie github.com. Klikamy
w ikonę w prawym górnym rogu i przechodzimy do zakładki Settings. Następnie
klikamy w SSH and GPG keys. Naciskamy przycisk New SSH key.

W "Title" podajemy dowolną nazwę np. klucz SSH, a w "Key" wklejamy klucz
SSH wyświetlony w terminalu. Następnie naciskamy przycisk Add SSH key.

Od teraz nasze połączenie z repozytorium jest bezpieczne.

## Hasło

Podczas wczytywania projektów Git może prosić nas o podanie loginu i hasła.
Hasło tworzymy w zakładce Settings -> Developer settings -> Personal
access tokens -> Tokens (classic). 

Klikamy w Generate new token. W polu Note podajemy nazwę np. "Hasło."
Zaznaczamy wszystkie pola niżej, tj. repo, workflow, itd. Expiration
możemy zostawić na 30 dni lub ustawić na dłuższy lub krótszy czas.

Po zaznaczeniu wszystkich opcji klikamy w przycisk Generate token.
Kopiujemy hasło i zapisujemy je w pliku tekstowym na komputerze.
Podczas wczytywania plików do repozytorium Git może nas poprosić o hasło,
wtedy podajemy mu właśnie to hasło i login do strony github.com.

## Podstawowe komendy

Git posiada parę podstawowych komend.

    git init

Tej komendy używamy podczas inicjacji repozytorium czyli za każdym razem
kiedy zaczynamy pracę z projektem. Użycie polecenia w innym folderze
jest równoznaczne z zainicjowaniem repo w innym miejscu.

    git add .

Komenda dodaje wszystkie pliki do repozytorium.

    git commit -m "Wiadomość"

Podajemy komentarz do "wrzutki", np. git commit -m "Dodałem nowe tło."

    git push

Wysłanie plików na serwer. Z poziomu Git wysyłamy pliki na serwer.

## Utworzenie repozytorium

Przechodzimy na stronę github.com. Tworzymy nowe repozytorium.
Podajemy nazwę, opis oraz zasięg publiczny lub prywatny. Tworzymy
nowe repozytorium.

W nowym oknie pokazują się nam komendy. Wklejamy je po kolei do terminala.
Może je trochę zmienić, np. zamiast wpisywać git add README.md możemy podać
komendę git add . itd. 

Kiedy Git wyświetli nam linię "Username for github.com: " podajemy login,
a w "Password for ..." podajemy hasło, czyli nasz token. Odświeżamy stronę
i powinniśmy zobaczyć pliki, które wrzuciliśmy w taki sposób do naszego
repozytorium.

Uwaga. Każde repozytorium powinno mieć osobny folder. Pliki nie powinny
ważyć zbyt dużo. Git obsługuje głównie pliki tekstowe, muzykę. Nie powinno
się wrzucać bardzo dużych grafik po "ileśset mega", filmów pełnometrażowych,
itd.

## Ominięcie tokena

Żeby ominąć wpisywanie nazwy użytkownika i tokena należy ustawić 
repozytorium z automatycznym dodawaniem ustawień podczas wczytywania.

    git remote set-url origin https://uzytkownik:token@github.com/uzytkownik/repozytorium.git

Użytkownik to nazwa użytkownika, token to wygenerowane hasło, a repozytorium
to nazwa repozytorium.
