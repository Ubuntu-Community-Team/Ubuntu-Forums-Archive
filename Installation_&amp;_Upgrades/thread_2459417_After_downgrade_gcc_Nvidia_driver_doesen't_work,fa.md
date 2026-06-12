---
title: "After downgrade gcc Nvidia driver doesen't work,fallback to default gcc doesn't work"
date: 2021-03-18
forum: Installation &amp; Upgrades
---

### Post by fritzmuster on 2021-03-18
Hello together

as I downgrade the gcc to 4.4 I changed the symlinks to the 4.4 Version. This doesen't work and now my System doesen't boot. As I learned now the Nvidia driver need the gcc compiler to work. Now I would like to get back to the default gcc but it doesen't work. What I done yet

```
$ sudo apt remove build-essential
$ sudo apt purge gcc
$ sudo apt-get autoremove
$ sudo apt update
$ sudo apt upgrade
$ sudo apt full-upgrade
```

Then

```
sudo dpkg --configure -a
```

and

```
sudo apt-get install -f
```

After that I tried to install the build essential package, but this ended with errors. The gcc and g++ package is not configured and so the dependencies of build essential are failed

```
sudo apt-get install build-essential
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.
Statusinformationen werden eingelesen.... Fertig
Die folgenden zusätzlichen Pakete werden installiert:
g++ g++-9 gcc libstdc++-9-dev
Vorgeschlagene Pakete:
g++-multilib g++-9-multilib gcc-9-doc gcc-multilib autoconf automake libtool flex bison gcc-doc libstdc++-9-doc
Die folgenden NEUEN Pakete werden installiert:
build-essential g++ g++-9 gcc libstdc++-9-dev
0 aktualisiert, 5 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
Es müssen noch 0 B von 10,1 MB an Archiven heruntergeladen werden.
Nach dieser Operation werden 46,8 MB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren? [J/n] j
Vormals nicht ausgewähltes Paket gcc wird gewählt.
(Lese Datenbank ... 262920 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Entpacken von .../gcc_4%3a9.3.0-1ubuntu2_amd64.deb ...
Entpacken von gcc (4:9.3.0-1ubuntu2) ...
Vormals nicht ausgewähltes Paket libstdc++-9-dev:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../libstdc++-9-dev_9.3.0-17ubuntu1~20.04_amd64.deb ...
Entpacken von libstdc++-9-dev:amd64 (9.3.0-17ubuntu1~20.04) ...
Vormals nicht ausgewähltes Paket g++-9 wird gewählt.
Vorbereitung zum Entpacken von .../g++-9_9.3.0-17ubuntu1~20.04_amd64.deb ...
Entpacken von g++-9 (9.3.0-17ubuntu1~20.04) ...
Vormals nicht ausgewähltes Paket g++ wird gewählt.
Vorbereitung zum Entpacken von .../g++_4%3a9.3.0-1ubuntu2_amd64.deb ...
Entpacken von g++ (4:9.3.0-1ubuntu2) ...
Vormals nicht ausgewähltes Paket build-essential wird gewählt.
Vorbereitung zum Entpacken von .../build-essential_12.8ubuntu1.1_amd64.deb ...
Entpacken von build-essential (12.8ubuntu1.1) ...
libstdc++-9-dev:amd64 (9.3.0-17ubuntu1~20.04) wird eingerichtet ...
gcc (4:9.3.0-1ubuntu2) wird eingerichtet ...
update-alternatives: Fehler: Alternativen-Pfad /usr/bin/gcc existiert nicht
dpkg: Fehler beim Bearbeiten des Paketes gcc (--configure):
»installiertes gcc-Skript des Paketes post-installation«-Unterprozess gab den Fehlerwert 2 zurück
g++-9 (9.3.0-17ubuntu1~20.04) wird eingerichtet ...
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von g++:
g++ hängt ab von gcc (= 4:9.3.0-1ubuntu2); aber:
Paket gcc ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten des Paketes g++ (--configure):
Abhängigkeitsprobleme - verbleibt unkonfiguriert
Es wurde kein Apport-Bericht verfasst, da die Fehlermeldung darauf hindeutet, dass dies lediglich ein Folgefehler eines vorherigen Problems ist.
Es wurde kein Apport-Bericht verfasst, da die Fehlermeldung darauf hindeut
et, dass dies lediglich ein Folgefehler eines vorherigen Problems ist.
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von build-essential:
build-essential hängt ab von gcc (>= 4:9.2); aber:
Paket gcc ist noch nicht konfiguriert.
build-essential hängt ab von g++ (>= 4:9.2); aber:
Paket g++ ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten des Paketes build-essential (--configure):
Abhängigkeitsprobleme - verbleibt unkonfiguriert
Trigger für man-db (2.9.1-1) werden verarbeitet ...
Fehler traten auf beim Bearbeiten von:
gcc
g++
build-essential
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

The actual symlinks are

```
lrwxrwxrwx 1 root root           5 Mär 20  2020  x86_64-linux-gnu-g++ -> g++-9
-rwxr-xr-x 1 root root     1158288 Aug  8  2020  x86_64-linux-gnu-g++-9
lrwxrwxrwx 1 root root           5 Mär 20  2020  x86_64-linux-gnu-gcc -> gcc-9
-rwxr-xr-x 1 root root     1154192 Aug  8  2020  x86_64-linux-gnu-gcc-9
lrwxrwxrwx 1 root root           8 Mär 20  2020  x86_64-linux-gnu-gcc-ar -> gcc-ar-9
-rwxr-xr-x 1 root root       35464 Aug  8  2020  x86_64-linux-gnu-gcc-ar-9
lrwxrwxrwx 1 root root           8 Mär 20  2020  x86_64-linux-gnu-gcc-nm -> gcc-nm-9
-rwxr-xr-x 1 root root       35464 Aug  8  2020  x86_64-linux-gnu-gcc-nm-9
lrwxrwxrwx 1 root root          12 Mär 20  2020  x86_64-linux-gnu-gcc-ranlib -> gcc-ranlib-9
-rwxr-xr-x 1 root root       35464 Aug  8  2020  x86_64-linux-gnu-gcc-ranlib-9
```

My question is how can I install the default gcc.Thanks for any hints.

---

### Post by ubfan1 on 2021-03-18
Take a look at the /usr/bin/gcc, /usr/bin/g++, /usr/bin/gcc-9, /usr/bin/g++-9 links and fix those too. (Along with all the nm, ar, and ranlib links).

---

### Post by fritzmuster on 2021-03-18
> **ubfan1 said:**
> Take a look at the /usr/bin/gcc, /usr/bin/g++, /usr/bin/gcc-9, /usr/bin/g++-9 links and fix those too. (Along with all the nm, ar, and ranlib links).

As I could see there are no symlinks like /usr/bin/gcc, /usr/bin/g++, /usr/bin/gcc-9, /usr/bin/g++-9.

---

### Post by ubfan1 on 2021-03-18
The executable is /usr/bin/x86_64-linux-gnu-gcc-9, but there should be a a chain of symlinks /usr/bin/gcc-9 -> x86_64-linux-gnu-gcc-9, and finally /usr/bin/gcc -> gcc-9.  The gcc should always remain linked to what the release supplied, because that's what gets used to rebuild drivers when updates occur.  Changing system-wide defaults with things like update-alternatives or changing the symlinks is not wise for the compilers, since you are likely to find "update broke my system", when a vital video driver fails to get recompiled.  Installing additional compilers is no problem, since the symlinks don't get changed.  You can set your own ~/bin symlinks for gcc to these (older/newer?) compilers, without causing problems for the system. Or have a project specific setup file to source and change gcc to what you need for that project.

---

### Post by fritzmuster on 2021-03-19
OK, that means I have to set several symlinks. I searched for the broken links and found these

```
$ /usr/bin$ find . -xtype l
./gcc-nm
./gcc-ar
./x86_64-linux-gnu-gcc
./x86_64-linux-gnu-gcc-nm
./gcc-ranlib
./x86_64-linux-gnu-gcc-ar
./clhsdb
./x86_64-linux-gnu-gcc-ranlib
./gcc
./hsdb
```

Now my question is how can I fix these broken links? I know the syntax  to define the links but how are the sources / targets of the links?

---

### Post by ubfan1 on 2021-03-19
Here's what my 20.04 system has for gcc. g++, ar and nm  will be similar.
$ ls -l *gcc* |fgrep 9
-rwxr-xr-x 1 root root     428 May  7  2006 c89-gcc
-rwxr-xr-x 1 root root     454 Apr 11  2011 c99-gcc
lrwxrwxrwx 1 root root       5 Mar 20  2020 gcc -> gcc-9
lrwxrwxrwx 1 root root      22 Aug  8  2020 gcc-9 -> x86_64-linux-gnu-gcc-9
lrwxrwxrwx 1 root root       8 Mar 20  2020 gcc-ar -> gcc-ar-9
lrwxrwxrwx 1 root root      25 Aug  8  2020 gcc-ar-9 -> x86_64-linux-gnu-gcc-ar-9
lrwxrwxrwx 1 root root       8 Mar 20  2020 gcc-nm -> gcc-nm-9
lrwxrwxrwx 1 root root      25 Aug  8  2020 gcc-nm-9 -> x86_64-linux-gnu-gcc-nm-9
lrwxrwxrwx 1 root root      12 Mar 20  2020 gcc-ranlib -> gcc-ranlib-9
lrwxrwxrwx 1 root root      29 Apr  2  2020 gcc-ranlib-8 -> x86_64-linux-gnu-gcc-ranlib-8
lrwxrwxrwx 1 root root      29 Aug  8  2020 gcc-ranlib-9 -> x86_64-linux-gnu-gcc-ranlib-9
lrwxrwxrwx 1 root root       5 Mar 20  2020 x86_64-linux-gnu-gcc -> gcc-9
-rwxr-xr-x 1 root root 1154192 Aug  8  2020 x86_64-linux-gnu-gcc-9
lrwxrwxrwx 1 root root       8 Mar 20  2020 x86_64-linux-gnu-gcc-ar -> gcc-ar-9
-rwxr-xr-x 1 root root   35464 Aug  8  2020 x86_64-linux-gnu-gcc-ar-9
lrwxrwxrwx 1 root root       8 Mar 20  2020 x86_64-linux-gnu-gcc-nm -> gcc-nm-9
-rwxr-xr-x 1 root root   35464 Aug  8  2020 x86_64-linux-gnu-gcc-nm-9
lrwxrwxrwx 1 root root      12 Mar 20  2020 x86_64-linux-gnu-gcc-ranlib -> gcc-ranlib-9
-rwxr-xr-x 1 root root   35464 Aug  8  2020 x86_64-linux-gnu-gcc-ranlib-9


$ ls -l *ar* |fgrep ar-
lrwxrwxrwx 1 root root        8 Mar 20  2020 gcc-ar -> gcc-ar-9
lrwxrwxrwx 1 root root       25 Aug  8  2020 gcc-ar-9 -> x86_64-linux-gnu-gcc-ar-9
lrwxrwxrwx 1 root root        8 Mar 20  2020 x86_64-linux-gnu-gcc-ar -> gcc-ar-9
-rwxr-xr-x 1 root root    35464 Aug  8  2020 x86_64-linux-gnu-gcc-9
lrwxrwxrwx 1 root root 19 Jan 21 07:23 ar -> x86_64-linux-gnu-ar
etc.

Probably lots of unnecessary links, but allows multiple versions/architectures to be installed simultaneously.




lrwxrwxrwx 1 root root       19 Jan 21 07:23 ar -> x86_64-linux-gnu-ar
lrwxrwxrwx 1 root root        8 Mar 20  2020 gcc-ar -> gcc-ar-9
lrwxrwxrwx 1 root root       25 Aug  8  2020 gcc-ar-9 -> x86_64-linux-gnu-gcc-ar-9
lrwxrwxrwx 1 root root        8 Mar 20  2020 x86_64-linux-gnu-gcc-ar -> gcc-ar-9
-rwxr-xr-x 1 root root    35464 Aug  8  2020 x86_64-linux-gnu-gcc-ar-9

---

### Post by fritzmuster on 2021-03-22
Thanks a lot!  With your post I was able to define my missing symlinks and also check my existing ones if they are correct. The missing ones I defined like that:

```
sudo ln -s gcc-9 gcc
sudo ln -s gcc-nm-9 gcc-nm
sudo ln -s gcc-ar-9 gcc-ar
sudo ln -s x86_64-linux-gnu-gcc-nm-9 gcc-nm-9
sudo ln -s gcc-ranlib-9 gcc-ranlib
sudo ln -s x86_64-linux-gnu-gcc-ar-9 gcc-ar-9
sudo ln -s x86_64-linux-gnu-gcc-ranlib-9 gcc-ranlib-9
```

After that I was able the reinstall the gcc package with sudo apt-get install --reinstall gcc

And at the end I installad the package build-essentials. Now gcc is OK and the nvidia driver works perfectly.

---

