# _Git Workshops_ at infoShare Academy

👨‍🏫 Dominik Młynarczyk | 📧 [hello@dominikmlynarczyk.com](mailto:hello@dominikmlynarczyk.com)

## Garść linków na dzień dobry 🧐

1. [Dokumentacja Gita](https://git-scm.com/doc)
2. [Learn Git Branching](https://learngitbranching.js.org/?locale=pl) - fajny _tutorial_ wizualizujący pracę z Gitem w kontekście gałęzi i _mergowania_
3. [Introduction to GitHub](https://lab.github.com/githubtraining/introduction-to-github) - materiały wprowadzające do nauki _Githuba_
4. [Git Guts - JustJoin.IT](https://www.youtube.com/watch?v=bfmVOYaKoVI) - fajny materiał pokazujący Gita "od środka"

## Git 🧠

GIT jest to tzw. **rozproszony system kontroli wersji, (_ang. DVCS_ - _Distributed Version Control System_**). GIT powstał 7 kwietnia 2005 roku, a jego autorem jest _Linus Torvalds_ który także jest twórcą jądra Linuxa. Chcąc historycznie poznać rozwój Gita i zrozumieć ideę powstania tego narzędzia idealnym źródłem na start jest jego wystąpienie pod [tym linkiem (Google Tech Talk: Linus Torvalds on git, maj 2007)](https://www.youtube.com/watch?v=4XpnKHJAok8), gdzie mocno krytykuje systemy scentralizowane.

## Wymagane narzędzia 🔨

W ramach dzisiejszych zajęć będziemy potrzebować:

- [Gita](https://git-scm.com/)
- [Visual Studio Code](https://code.visualstudio.com/)

W ramach zajęć będziemy pracować albo z plikiem HTML, albo z plikiem Markdown (o rozszerzeniu `.md`). Jeżeli nie znasz języka _Markdown_ [tutaj](https://www.markdownguide.org/cheat-sheet/) znajdziesz ściągawkę.

## Podstawowe komendy linii poleceń 💻

Przygodę w linii poleceń (potocznie _terminalu_) zaczynamy domyślnie zawsze w folderze domowym i jaki to jest folder zależy od systemu z jakiego korzystamy.

Aby poznać ścieżkę folderu domowego, czy katalogu w jakim się znajdujemy używamy komendy:

```bash
pwd
```

Przykładowo, na macOS będzie to katalog `/Users/nazwa_usera` np. `/Users/admin`. Komenda `pwd` to skrót od słów _Print Working Directory_ i jej celem jest poinformowanie w jakiej lokalizacji aktualnie jesteśmy.

Aby "rozejrzeć" się po katalogu w którym się znajdujemy, czyli zobaczyć jego zawartość wykorzystujemy komendę:

```bash
ls
```

Zobaczymy dzięki niej wszystkie foldery i pliki w katalogu w którym aktualnie się znajdujemy.

Nie zobaczymy jednak ukrytych folderów i plików, czyli tych których nazwa na ogół jest poprzedzona kropką i aby je wyświetlić używamy komendy `ls` z przełącznikiem `-a`:

```bash
ls -a
```

---

By utworzyć nowy folder z poziomu katalogu w którym aktualnie jesteśmy używamy komendy:

```bash
mkdir moj-katalog
```

Powyżej utworzyliśmy folder o nazwie _moj-katalog_. Nazwa komendy `mkdir` pochodzi od angielskiego _"Make directory"_, czyli utwórz katalog. Chcąc się upewnić, że taki folder stworzyliśmy wystarczy go wylistować za pomocą poznanej komendy `ls`.

Aby wejść do wyżej utworzonego katalogu używamy komendy:

```bash
cd moj-katalog
```

Po prostu po komendzie `cd` podajemy ścieżkę do konkretnego katalogu pod który chcemy przejść.

Komenda `cd` pochodzi od słów _Change Directory_, czyli zmień katalog.

Chcąc wrócić do folderu nadrzędnego jako ścieżkę podajemy dwie kropki:

```bash
cd ..
```

W systemach _UNIX'owych_ aktualny folder jest oznaczany kropką, a dwie kropki to folder rodzic. Tym samym chcąc przejść kilka poziomów wyżej piszemy:

```bash
# przejście trzy foldery wyżej
cd ../../../
```

Jeżeli chcemy wrócić do poprzedniego folderu w prosty sposób, możemy wykorzystać komendę:

```bash
cd -
```

---

Używając komendy `ls` w katalogu _moj-katalog_ nie zobaczymy nic, bo jest to pusty, dopiero co utworzony katalog. Aby stworzyć plik w katalogu _moj-katalog_ używamy komendy:

```bash
touch plik-testowy.txt
```

Dzięki temu w katalogu _moj-katalog_ utworzyliśmy plik `plik-testowy.txt` i na dowód znów możemy użyć komendy `ls`.

---

Usuwanie realizujemy za pomocą komendy:

```bash
rm nazwa-pliku
```

`rm` to skrót od `remove`. Chcąc usuwać katalogi należy użyć powyższej komendy z przełącznikiem `-r`, ponieważ `-r` oznacza `recursive`, czyli usuwamy folder i rekursywnie całą jego zawartość.

# 🏠 Praca lokalna z repozytorium

Poniżej znajdują się materiały i ćwiczenia do wykonania, które pozwolą Ci opanować podstawy pracy z Gitem.

## Challenge 1 - Podstawowa konfiguracja _Gita_

Zanim zaczniemy pracę z Gitem, warto się gitowi przedstawić 😊. Wprowadź do linii poleceń następujące komendy (oczywiście podając swoje imię i nazwisko oraz swój adres e-mail):

```bash
git config --global user.name "Adam Nowak"
git config --global user.email "adam.nowak@example.com"
```

Powyższe informacje będą wykorzystane do zapisania naszych zmian w historii projektu. Dzięki temu wiadomo kto dane zmiany wprowadził i jak się z autorem zmian skontaktować.

`user.name` oraz `user.email` to klucze pod którymi Git zapamiętuje daną wartość konfiguracji.

Wykorzystaliśmy przełącznik `--global` by skonfigurować gita w kontekście całego użytkownika w systemie operacyjnym, co oznacza, że powyższe ustawienia będą zaaplikowane dla dowolnego [repozytorium](https://chcenawczoraj.pl/software/czym-jest-repozytorium-kodu-strony) na Twoim komputerze.

Dodaj jeszcze następującą konfigurację:

```bash
git config --global core.editor "code --wait"
git config --global credential.helper "cache --timeout=3600"
```

Program [Vim](https://www.vim.org/) jest to domyślny edytor tekstowy w Gicie i jest on trochę skomplikowany, szczególnie dla osób początkujących. Zmieniamy go za pomocą klucza `core.editor` ustawiając go na _Visual Studio Code_. Przełącznik `--wait` będzie kazał oczekiwać Gitowi za każdym razem jak otworzony zostanie _Visual Studio Code_ na potwierdzenie realizowanej operacji.

Dodatkowo, wybiegając nieco w przyszłość, dodamy klucz `credential.helper`. Podczas komunikacji ze zdalnym repozytorium (o czym powiemy więcej później) będziemy często używać protokołu HTTPS. Wymaga on podawania loginu i hasła. Aby nie musieć tego podawać za każdą operacją przesyłania danych do zdalnego repozytorium możemy na określony czas zapamiętać dane uwierzytelniające na poziomie systemu operacyjnego.

---

Aby zweryfikować czy Git faktycznie zapisał nasze ustawienia konfiguracyjne posłużymy się tymi samymi komendami, tylko w trybie do odczytu:

```bash
# Przykłady
git config user.name
git config user.email
```

Możemy też wypisać wszystkie ustawienia konfiguracyjne w następujący sposób:

```bash
git config --list
# lub wersja skrócona
git config -l
```

Możemy też podejrzeć jak wygląda globalna konfiguracja _Gita_ za pomocą komendy:

```bash
git config --global -e
```

<u>Jeżeli widzisz tam wprowadzone przez siebie zmiany konfiguracyjne, to wykonałeś/aś wszystko poprawnie!</u>

> Jeżeli będziesz potrzebować szybkiego opisu często używanych komend wpisz w linii poleceń:
>
> ```bash
> git help
> ```

## Challenge 2 - Początek pracy, tworzymy repozytorium

Początek pracy z GITem zaczyna się od utworzenia <u>repozytorium</u>.

**Repozytorium (potocznie: repo) to katalog** (znajdujący się np. na naszym dysku twardym) zawierający wszystkie informacje o aktualnym stanie projektu i jego historii. Twoje repozytorium może zawierać odwołania (linki) do innych repozytoriów (co zobaczymy w ramach pracy zdalnej).

**Twoim zadaniem będzie utworzenie repozytorium na dysku**. Aby zainicjować nowe repozytorium należy:

1. Utworzyć katalog za pomocą komendy `mkdir`
2. Wejść do niego za pomocą komendy `cd`
3. Zainicjować nowe repozytorium za pomocą komendy `git init` - **komenda ta w dowolnie wybranym katalogu tworzy lokalne repozytorium GITa**.

<u>Na tym etapie GIT jest gotowy do pracy :blush:</u>

---

Dzięki komendzie `git init` GIT utworzył w wybranym przez nas katalogu swój własny, **ukryty katalog** o nazwie _.git_, w nim będą znajdować się wszystkie informacje o repozytorium. W tym katalogu znajdują się głównie pliki tekstowe i możemy otworzyć je w dowolnym edytorze.

Struktura katalogowa wygląda następująco:

```
.git
└───branches/ (empty)
└───hooks/
|   └───applypatch-msg.sample
│   └───commit-msg.sample
│   └───fsmonitor-watchman.sample
│   └───post-update.sample
|   └───pre-applypatch.sample
│   └───pre-commit.sample
│   └───prepare-commit-msg.sample
│   └───pre-push.sample
│   └───pre-rebase.sample
│   └───pre-receive.sample
│   └───update.sample
└───info/
|   └───exclude
└───objects/
|   └───info/ (empty)
|   └───pack/ (empty)
└───refs/
|   └───heads/ (empty)
|   └───tags/ (empty)
└───config
└───description
└───FETCH_HEAD
└───HEAD
```

<u>Warto już na początku przejrzeć te pliki, aby przekonać się, że w większości są to zwyczajne pliki z treścią tekstową.</u>

## Challenge 3 - Pierwszy _commit_

**Commit** (inaczej: _changeset_, _revision_, _version_) - **stan repozytorium**, czyli **konkretna wersja projektu w danym momencie w czasie**. W Gicie wersja oznaczona jest wyliczonym identyfikatorem [SHA1](https://pl.wikipedia.org/wiki/SHA-1).

Historia Twojego projektu będzie właśnie składać się z _commitów_. Oprócz informacji o zmienionych plikach, każdy _commit_ zawiera także informacje o:

1. **autorze**, (imię i nazwisko oraz adres e-mail wcześniej skonfigurowane)
2. **czasie utworzenia zmiany**,
3. **commit message (opis zmian)**.

Pierwszy _commit_ to punkt początkowy nowego repozytorium i nazywany jest **root commit**, aby zaznaczyć, że jest to punkt startowy dla naszego repozytorium.

**Na podstawie wiedzy z zajęć utwórz swój pierwszy _commit_.**

## Challenge 4 - Zaprzyjaźniamy się z _Gitem_

Na podstawie wiedzy z zajęć wiemy na czym polega poniższy diagram w gicie:

![git 3 areas example](https://miro.medium.com/max/800/1*tl3B9CRamhIw54usIfXubw.png)

Przećwicz mechanizm _stage'owania_ oraz _commitowania_, obserwując całe _worfklow_ _Gita_ za pomocą poznanych komend:

- `git add <nazwa-pliku>` - dodaje zmiany z wybranego pliku do _Staging area_ (inaczej nazywany _indexem_). Możesz dodać wszystkie zmiany dodając w miejsce `<nazwa_pliku>` kropkę.
- `git commit` - komenda dobrze Ci już znana. Możesz wykorzystać przełącznik `-m` aby przekazać z poziomu linii poleceń opis _commita_.
- `git status` - pokazuje aktualny status zmian (aktualnie zmienione pliki oraz pliki znajdujące się w indeksie)
- `git restore` - komenda pozwala na wycofanie aktualnie wprowadzonych zmian, najczęściej wykorzystywana na zmianach jeszcze _niezacommitowanych_. Domyślnie usunie zmiany _untracked_ (nie dodane do _Staging area_), z flagą `--staged` wycofa zmiany ze _Staging area_ (znają się one jako zmiany _untracked_ / _not staged_).
- `git reset --soft HEAD^` - usunięcie ostatniego _commita_ (czym jest `HEAD` powiemy w _Challenge 5_)

**Dodaj kilka _commitów_ analizując co się dzieje kiedy wprowadzasz każdą komendę _Gita_. Na podstawie wiedzy z zajęć zajrzyj do katalogu `.git` i obserwuj co się dzieje (w szczególności skup się w ramach warsztatów na katalogu `refs` i/lub bezpośrednio na pliku `HEAD`)**

## Challenge 5 - Analiza zmian i historii oraz nawigacja po historii w Gicie

Wykorzystaj poznane komendy analizując zmiany nie śledzone oraz te aktualnie znajdujące się w _Staging area_:

- `git diff` oraz `git diff --staged` - pokazuje zmiany naniesione na plikach oraz zmiany które aktualnie znajdują się w _Staging Area_.
- `git log` - wyświetla historię projektu, można wykorzystać bardzo przydatne przełączniki do zmodyfikowania sposobu wyświetlania historii:
  - przełącznik `--oneline` - wyświetli skróconą historię projektu, gdzie każdy _commit_ zajmie jedną linię w wierszu poleceń
  - przełącznik `--graph` - graficzna reprezentacja historii projektu (przyda się przy poznaniu _branchy_)
  - filtorwanie danych za pomocą `--author` celem sprawdzenia zmian od danej osoby, a także za pomoca `--after` czy `--before` celem określenia _commitów_ z danego zakresu dat

---

**HEAD** (**uwaga: <u>pisane WIELKIMI literami</u>**) - jest to jeden, konkretny commit będący źródłem aktualnej zawartości _Working Copy_ (katalogu roboczego w którym aktualnie jesteśmy). <u>Można o tym myśleć o nim jako o aktualnym commicie na który patrzymy 👀.</u> Innymi słowy, mówimy tutaj o _commicie_ który jest źródłem plików znajdujących się teraz w _Working Directory_.

Skrótem (aliasem) do HEAD, czyli aktualnego _commita_ jest "@". Git zapisuje HEAD w `.git/HEAD`, w tym pliku zapisana jest ścieżka do commita który został _wycheckoutowany_ jako ostatni.

- Aby przejść do dowolnego _commita_ w ramach repozytorium wykorzystujemy komendę `git checkout` np. podając unikalne SHA _commita_.
- Możemy nawigować w _Gicie_ używając znaków `^` (_commit wcześniej_) oraz `~1` (zadana ilość _commitów wcześniej_). Wcześniej użyliśmy komendy `git reset --soft HEAD^` która właśnie oznacza wycofanie zmian z _commita_ wcześniej od naszego aktualnego `HEAD`.

Przetestuj nawigację w Gicie z użyciem komendy `git checkout` oraz wykorzystaj do tego symbole `^` oraz `~`.

## Challenge 6 - Gałęzie

**Gałąź (ang. branch)** - jest to **kopia repozytorium**, umożliwiająca pracę niezależną od pozostałych kopii (nie jest to kopia fizyczna, a jedynie koncepcyjna).

**Master** - jest to **domyślna nazwa pierwszej gałęzi** w repozytorium Gita. W innych systemach kontroli wersji nazywana jest jako _main_ lub rzadziej _default_.

Mając główną gałąź (domyślnie jest to master) i gałąź np. `dev` możemy pracować na obu nie mieszając niczego ze sobą aż do chwili gdy będzie nam to potrzebne. Możemy np. rozwijać jakąś funkcjonalność na gałęzi `dev` i jednocześnie na masterze (a najlepiej na jeszcze jednej osobnej gałęzi) robić np. szybkie fixy dla wykrytych bugów.

Podstawowe komendy do pracy z gałęziami:

- `git branch` - wylistuje lokalne gałęzie
- `git branch my-new-branch` - tworzy branch o nazwie `my-new-branch` który znajdzie się w tym samym miejscu w którym aktualnie jest nasze HEAD (miejsce w którym aktualnie się znajdujemy w historii projektu)
- `git checkout my-other-branch` - przełącza HEAD na ostatni _commit_ brancha `my-other-branch`
- `git checkout -b my-third-branch` - połączenie dwóch powyższych. Tworzy nowy branch oraz "przechodzi na niego" (zmienia HEAD)

**Twoim zadaniem będzie utworzenie nowej gałęzi, przejście na nią, a następnie wykonanie _commita_. Następnie wróć z powrotem na gałąź `main` i wykonaj komendę:**

```bash
git merge --no-ff -m "Merge branch test"
```

Wykonaliśmy tzw. _merge_, czyli zintegrowanie zmian z gałęzi do gałęzi `main`. i omówimy dokładnie co ta komenda robi w ramach kolejnych zajęć. 😊 Sprawdź teraz jedynie historię projektu.

# 🌎 Praca z repozytorium zdalnym

Najbardziej "banalnym" powodem dla którego wykorzystujemy kontrolę wersji to **możliwość wymiany plików, czyli synchronizacja pracy między różnymi członkami zespołu.** W tej części przećwiczymy jak publikować zmiany "do internetu" 😃.

## Challenge 1 - pobranie zmian ze zdalnego repozytorium

Na podstawie wiedzy z zajęć wybierz dowolne repozytorium udostępniające kod _open-source_, a następnie je "sklonuj", czyli utwórz niezależną kopię repozytorium na swojej maszynie. **W ramach tego ćwiczenia możesz np. sklonować aktualne repozytorium.**

Aby pobrać repozytorium wykorzystujemy komendę:

```bash
# dla protokołu HTTPS:
git clone https://github.com/infoshareacademy/jfddr6-workshops-git.git
# dla protokołu SSH:
git clone git@github.com:infoshareacademy/jfddr6-workshops-git.git
```

Komenda `clone` domyślnie tworzy katalog o nazwie takiej jak nazwa repozytorium i kopiuje do niego zawartość zdalnego repozytorium. Jeśli chcemy aby zmiany zostały pobrane do aktualnego katalogu do komendy na końcu dodajemy kropkę.

## Challenge 2 - puste repozytorium zdalne i wysyłanie zmian

**Słowo _remote_ to nic innego jak zdalne repozytorium.** Repozytorium może być podłączone/podpięte/zlinkowane, czyli posiadać skonfigurowane adresy do wielu różnych innych, zdalnych repozytoriów. **Każde zdalne repozytorium z którym nasze repozytorium jest połączone nazywane jest jako "_remote repository_".**

**Słowo `origin` to domyślna nazwa zdalnego repozytorium będącego źródłem komendy`clone`. ** Tak jak `master` wiemy, że jest domyślną nazwą pierwszej gałęzi w repozytorium (konwencja), tak `origin` jest domyślną nazwą zdalnego repozytorium (konwencja).

**Upstream branch jest to gałąź, a konkretniej jest to odpowiednik lokalnej gałęzi w zdalnym repozytorium.**

---

Na podstawie wiedzy z zajęć utwórz w Github puste repozytorium (nie dodawaj żadnych plików), a następnie opublikuj (_wypushuj_) swoje zmiany do zdalnego repozytorium.

Podstawowe komendy przy wysłaniu zmian do zdalnego _repo_:

- `git remote` - wyświetlane zdalne repozytoria do których jesteśmy "podpięci"
- `git remote add nasza-nazwa-zdalnego-repo adres-url` - dodawanie zdalnego repozytorium
- `git remote remove nasza-nazwa-zdalnego-repo` - w dowolnej chwili możemy "odłączyć się" od zdalnego repozytorium za pomocą tej komendy
- `git push` - wysyłanie zmian do zdalnego repozytorium
- `git push origin --set-upstream master`, lub `git push origin -u master` - wysyłanie lokalnej gałęzi `master` do zdalnego repozytorium, które nazywamy jako `origin` wraz z zmapowaniem lokalnej gałęzi `master` do gałęzi `master` na zdalnym repozytorium

## Challenge 3 - pobieranie zmian ze zdalnego repozytorium

W _Gicie_ mamy dwa sposoby, czyli dwie komendy za pomocą których możemy pobierać zmiany ze zdalnego repozytorium, są to komendy:

1. `fetch`
2. `pull`

**Komenda `fetch` charakteryzuje się tym, że ona tylko ściąga zmiany i nie integruje ich z kodem w lokalnym repozytorium. Komenda `fetch` aktualizuje tzw. _<u>tracking branch</u>._**

**_Tracking branch_ - jest to lokalna gałąź reprezentująca zdalną gałąź.** Taką gałęzią jest np. `origin/master`

**Jest to gałąź którą _Git_ posiada lokalnie w repozytorium, ale nie pracujemy na takim _tracking branch_ bezpośrednio**. Jej celem jest tylko reprezentowanie w lokalnym repozytorium gałęzi która znajduje się w repozytorium zdalnym.

**_Tracking branch_ jest aktualizowana przy operacjach integrujących zmiany ze zdalnego repozytorium, czyli podczas korzystania z komend wymagających kontaktu ze zdalnym repozytorium. Takie komendy to `fetch`, `pull` i `push`.**

**Komenda `pull` realizuje działanie komendy `fetch`, czyli pobiera zmiany ze zdalnego repozytorium, a następnie _merguje_ zmiany z lokalną gałęzią. Można więc o niej myśleć jako o `pull = fetch + merge`.**

---

Z poziomu edytora plików na Githubie dodaj zmiany do wybranego pliku, zacommituj je (też możesz to zrobić z poziomu _Githuba_), a następnie za pomocą poznanych komend pobierz zmiany ze zdalnego repozytorium. Zacznij od wykorzystania komendy `git fetch`, następnie sprawdź na podstawie poznanych komend jaki jest status repozytorium i jak wygląda historia w Gicie.

Następnie zintegruj te zmiany z użyciem komendy `git pull`.

## Challenge 4 - wysyłanie swojej gałęzi na zdalne repozytorium

Tym razem spróbujesz wysłać swoje zmiany do tego repozytorium warsztatowego (tego na którym aktualnie się znajdujemy), przesyłając swoją własną gałąź.

W tym celu:

1. Sklonuj to repozytorium (lub jeśli to zrobiłeś/aś wcześniej to upewnij się, że masz je lokalnie 😃).

2. Utwórz nową, gałąź w swoim repozytorium.

   ```bash
   git checkout -b student/twoje-imie-i-nazwisko
   ```

3. Dodaj nowy plik `twoje-imie-i-nazwisko.md`, wprowadź do niego przykładową treść, a następnie _zacommituj_

4. Wyślij nowo utworzoną gałąź do zdalnego repozytorium:

   ```bash
   git push origin -u student/twoje-imie-i-nazwisko
   ```
