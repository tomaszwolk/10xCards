# Dokument wymagań produktu (PRD) - 10xCards

## 1. Przegląd produktu

Inteligentne Fiszki to aplikacja internetowa zaprojektowana, aby zautomatyzować i przyspieszyć proces tworzenia fiszek edukacyjnych. Wykorzystując sztuczną inteligencję, aplikacja pozwala użytkownikom generować zestawy fiszek poprzez proste wklejenie tekstu, co eliminuje czasochłonny proces manualnego przepisywania. MVP skupia się na podstawowych funkcjonalnościach generowania, zarządzania fiszkami oraz integracji z gotowym algorytmem powtórek, z naciskiem na prostotę i szybkość działania.

## 2. Problem użytkownika

Głównym problemem, który rozwiązuje aplikacja, jest czasochłonność i wysiłek wymagany do manualnego tworzenia wysokiej jakości fiszek. Wielu uczniów i studentów rezygnuje z efektywnej metody nauki, jaką jest spaced repetition, ponieważ proces przygotowywania materiałów jest zbyt żmudny. Użytkownicy potrzebują narzędzia, które zminimalizuje pracę manualną, pozwoli im skupić się na nauce, a nie na tworzeniu, i zautomatyzuje ekstrakcję kluczowych informacji z ich materiałów źródłowych.

## 3. Wymagania funkcjonalne

- RF-001: Generowanie fiszek przez AI: System umożliwi generowanie fiszek na podstawie tekstu wklejonego przez użytkownika.
  - RF-001a: Integracja z Gemini API do przetwarzania tekstu.
  - RF-001b: Możliwość określenia dziedziny wiedzy przez użytkownika (za pomocą presetów lub własnego tekstu) w celu poprawy jakości generowanych fiszek.
  - RF-001c: Dzienny limit 50 fiszek generowanych przez AI na użytkownika.
- RF-002: Zarządzanie fiszkami: Użytkownicy muszą mieć pełną kontrolę nad swoimi fiszkami.
  - RF-002a: Manualne tworzenie fiszek w formacie przód-tył.
  - RF-002b: Przeglądanie listy wszystkich zapisanych fiszek.
  - RF-002c: Edycja treści (pytania i odpowiedzi) istniejących fiszek.
  - RF-002d: Usuwanie fiszek z zestawu.
- RF-003: System kont użytkowników: Prosty system do przechowywania i zarządzania fiszkami.
  - RF-003a: Rejestracja użytkownika za pomocą adresu e-mail i hasła.
  - RF-003b: Logowanie do istniejącego konta.
  - RF-003c: Opcja sesji gościnnej, która pozwala na korzystanie z aplikacji bez rejestracji (dane przechowywane tymczasowo, czyszczone po 24h lub zamknięciu sesji).
- RF-004: System powtórek: Integracja z algorytmem spaced repetition.
  - RF-004a: Wykorzystanie gotowej biblioteki open-source `spaced-repetition-js` do zarządzania harmonogramem powtórek.
  - RF-004b: Interfejs do przeprowadzania sesji powtórek, w którym użytkownikowi prezentowane są fiszki zgodnie z algorytmem.
- RF-005: Przechowywanie i eksport danych:
  - RF-005a: Dane o fiszkach i użytkownikach przechowywane w sposób zapewniający skalowalność i bezpieczeństwo.
- RF-006: Śledzenie jakości AI: Wewnętrzny mechanizm do mierzenia kryteriów sukcesu.
  - RF-006a: System powinien śledzić, czy wygenerowana przez AI fiszka została zaakceptowana, odrzucona czy zaakceptowana po edycji przez użytkownika.
- RF-007: Interfejs użytkownika:
  - RF-007a: Prosty, liniowy i intuicyjny przepływ użytkownika.
  - RF-007b: Jasne powiadomienia, np. o osiągnięciu limitu generowania fiszek przez AI.

## 4. Granice produktu

Następujące funkcje nie wchodzą w zakres MVP, aby zapewnić szybkie dostarczenie podstawowej wartości produktu:

- Własny, zaawansowany algorytm powtórek (jak w SuperMemo czy Anki).
- Import plików w różnych formatach (np. PDF, DOCX, Markdown).
- Funkcje społecznościowe, takie jak współdzielenie zestawów fiszek między użytkownikami.
- Integracje z zewnętrznymi platformami edukacyjnymi (np. Moodle, Google Classroom).
- Dedykowane aplikacje mobilne na systemy iOS i Android (MVP będzie aplikacją webową).
- Zaawansowany edytor tekstu z formatowaniem, obsługą obrazów czy audio.
- Analiza i raportowanie postępów w nauce.
- Testy A/B w celu optymalizacji interfejsu lub jakości generowania fiszek.

## 5. Historyjki użytkowników

### Zarządzanie Kontem

- ID: US-001
- Tytuł: Rejestracja nowego konta
- Opis: Jako nowy użytkownik, chcę móc założyć konto za pomocą mojego adresu e-mail i hasła, aby bezpiecznie przechowywać moje fiszki.
- Kryteria akceptacji:
  1. Formularz rejestracji zawiera pola na adres e-mail i hasło.
  2. Hasło jest maskowane podczas wpisywania.
  3. System waliduje poprawność formatu adresu e-mail.
  4. Po pomyślnej rejestracji jestem automatycznie zalogowany i widzę główny panel aplikacji.

- ID: US-002
- Tytuł: Logowanie do systemu
- Opis: Jako powracający użytkownik, chcę móc zalogować się na moje konto przy użyciu e-maila i hasła, aby uzyskać dostęp do moich zapisanych fiszek.
- Kryteria akceptacji:
  1. Formularz logowania zawiera pola na adres e-mail i hasło.
  2. Po poprawnym uwierzytelnieniu uzyskuję dostęp do swojego panelu z fiszkami.
  3. W przypadku podania błędnych danych wyświetlany jest odpowiedni komunikat.

- ID: US-003
- Tytuł: Korzystanie z aplikacji jako gość
- Opis: Jako nowy użytkownik, chcę wypróbować aplikację bez konieczności zakładania konta, aby szybko ocenić jej funkcjonalność.
- Kryteria akceptacji:
  1. Mogę uzyskać dostęp do kluczowych funkcji (generowanie AI, manualne tworzenie) bez logowania.
  2. Wyświetlany jest wyraźny komunikat informujący, że moje dane zostaną usunięte po 24 godzinach lub zamknięciu sesji.
  3. Aplikacja zachęca do założenia konta w celu trwałego zapisania danych.

### Tworzenie i Zarządzanie Fiszkami

- ID: US-004
- Tytuł: Generowanie fiszek z tekstu przez AI
- Opis: Jako użytkownik, chcę wkleić notatki w pole tekstowe i jednym kliknięciem wygenerować zestaw fiszek, aby zaoszczędzić czas.
- Kryteria akceptacji:
  1. Na stronie głównej znajduje się duże pole tekstowe do wklejania treści.
  2. Po wklejeniu tekstu i kliknięciu przycisku "Generuj", system przetwarza tekst i wyświetla listę proponowanych fiszek.
  3. Każda proponowana fiszka ma oddzielone pytanie i odpowiedź.

- ID: US-005
- Tytuł: Określanie dziedziny wiedzy dla AI
- Opis: Jako użytkownik, chcę móc określić dziedzinę wiedzy (np. "historia", "biologia"), z której pochodzi mój tekst, aby AI mogło wygenerować bardziej trafne fiszki.
- Kryteria akceptacji:
  1. Przed generowaniem fiszek mogę wybrać dziedzinę z predefiniowanej listy (matematyka, historia, biologia, język angielski, chemia, fizyka, literatura).
  2. Mogę również wpisać własną, niestandardową dziedzinę w polu tekstowym.
  3. Wybrana dziedzina jest przekazywana do AI jako kontekst.

- ID: US-006
- Tytuł: Weryfikacja fiszek wygenerowanych przez AI
- Opis: Jako użytkownik, chcę przejrzeć wygenerowane przez AI fiszki i zdecydować, które z nich zapisać, które odrzucić, a które poprawić.
- Kryteria akceptacji:
  1. Lista wygenerowanych fiszek jest wyświetlana w czytelny sposób.
  2. Przy każdej fiszce znajdują się opcje: "Zaakceptuj", "Edytuj", "Odrzuć".
  3. Fiszki zaakceptowane są dodawane do mojej głównej kolekcji.
  4. Fiszki odrzucone są usuwane.
  5. Opcja "Edytuj" pozwala na modyfikację treści fiszki przed jej zaakceptowaniem.
  6. Akcje użytkownika (akceptacja, edycja, odrzucenie) są wewnętrznie śledzone na potrzeby metryk.

- ID: US-007
- Tytuł: Manualne tworzenie fiszki
- Opis: Jako użytkownik, chcę mieć możliwość ręcznego dodania nowej fiszki, wpisując własne pytanie i odpowiedź.
- Kryteria akceptacji:
  1. Dostępny jest formularz z dwoma polami: "Pytanie" i "Odpowiedź".
  2. Po wypełnieniu pól i zapisaniu, nowa fiszka pojawia się na mojej liście fiszek.

- ID: US-008
- Tytuł: Przeglądanie kolekcji fiszek
- Opis: Jako użytkownik, chcę widzieć listę wszystkich moich zapisanych fiszek, aby mieć wgląd w moją bazę wiedzy.
- Kryteria akceptacji:
  1. Dostępna jest sekcja, w której wyświetlane są wszystkie moje fiszki.
  2. Lista jest przejrzysta i czytelna.

- ID: US-009
- Tytuł: Edycja istniejącej fiszki
- Opis: Jako użytkownik, chcę móc edytować treść pytania lub odpowiedzi w już zapisanej fiszce, aby poprawić błędy lub zaktualizować informacje.
- Kryteria akceptacji:
  1. Przy każdej fiszce na liście znajduje się opcja "Edytuj".
  2. Po kliknięciu "Edytuj" mogę zmodyfikować tekst pytania i odpowiedzi.
  3. Zmiany są zapisywane w mojej kolekcji.

- ID: US-010
- Tytuł: Usuwanie fiszki
- Opis: Jako użytkownik, chcę móc na stałe usunąć fiszkę, której już nie potrzebuję.
- Kryteria akceptacji:
  1. Przy każdej fiszce na liście znajduje się opcja "Usuń".
  2. Przed ostatecznym usunięciem system prosi o potwierdzenie tej akcji.
  3. Po potwierdzeniu fiszka jest trwale usuwana z mojej kolekcji.

### Nauka i Eksport

- ID: US-011
- Tytuł: Rozpoczynanie sesji powtórek
- Opis: Jako użytkownik, chcę rozpocząć sesję nauki, podczas której aplikacja będzie mi prezentować fiszki zgodnie z algorytmem spaced repetition.
- Kryteria akceptacji:
  1. Dostępny jest przycisk "Rozpocznij naukę" lub podobny.
  2. Po jego kliknięciu rozpoczyna się sesja, w której wyświetlana jest jedna fiszka na raz.
  3. Po zobaczeniu odpowiedzi mogę ocenić swoją znajomość fiszki (np. "łatwe", "trudne"), co wpłynie na harmonogram przyszłych powtórek.

- ID: US-012
- Tytuł: Eksportowanie fiszek do pliku
- Opis: Jako użytkownik, chcę móc wyeksportować wszystkie moje fiszki do pliku JSON lub CSV, aby mieć ich kopię zapasową.
- Kryteria akceptacji:
  1. W ustawieniach lub na głównym panelu znajduje się opcja "Eksportuj".
  2. Po jej wybraniu mogę wybrać format (JSON lub CSV).
  3. Aplikacja generuje i pozwala pobrać plik zawierający wszystkie moje fiszki.

### Ograniczenia i Scenariusze Brzegowe

- ID: US-013
- Tytuł: Osiągnięcie dziennego limitu generowania AI
- Opis: Jako użytkownik, po wygenerowaniu 50 fiszek przy użyciu AI w ciągu jednego dnia, chcę zostać poinformowany o osiągnięciu limitu.
- Kryteria akceptacji:
  1. System śledzi liczbę fiszek wygenerowanych przez AI dla każdego użytkownika dziennie.
  2. Po osiągnięciu limitu 50 fiszek, przycisk "Generuj" staje się nieaktywny.
  3. Wyświetlony zostaje czytelny komunikat informujący o limicie i zachęcający do manualnego tworzenia fiszek lub powrotu następnego dnia.

## 6. Metryki sukcesu

Sukces MVP będzie mierzony za pomocą następujących kluczowych wskaźników, które zostaną zaimplementowane jako mechanizmy śledzące wewnątrz aplikacji (działające lokalnie w przeglądarce):

1. Jakość generowania AI:
   - Cel: 75% fiszek wygenerowanych przez AI jest akceptowanych przez użytkownika (bez edycji lub po drobnej edycji).
   - Sposób pomiaru: Wewnętrzna tabela śledząca będzie zapisywać status każdej wygenerowanej fiszki (zaakceptowana, edytowana, odrzucona). Metryka będzie obliczana jako stosunek fiszek zaakceptowanych do wszystkich wygenerowanych.

2. Adopcja funkcji AI:
   - Cel: Użytkownicy tworzą 75% wszystkich swoich fiszek przy użyciu generatora AI.
   - Sposób pomiaru: System będzie zliczał liczbę fiszek utworzonych manualnie oraz za pomocą AI. Metryka będzie obliczana jako stosunek fiszek stworzonych przez AI do łącznej liczby wszystkich fiszek w systemie użytkownika.
