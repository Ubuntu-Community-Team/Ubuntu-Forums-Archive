---
title: "dependency problem during install"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by Timokl on 2006-08-27
Hi,

I try to install the XHTML-SCORM-Editor eXe. The eXe project provides on their website two .deb-files for Ubuntu ([http://www.exelearning.org/?q=downloads]("http://www.exelearning.org/?q=downloads")) which I cannot install due to dependency problems and version collisions.

eXe makes use of the twisted framework ([http://twistedmatrix.com/]("http://twistedmatrix.com/")) which is also part of the Ubuntu repository. The problem is: eXe requires a different version of twisted (2.0.1-999) than the version in the ubuntu repository (2.2.0-2ubuntu1) - and that lead me into a deadlock.

Here's a log when I try to install the .deb file. Sorry, it's in German, but I did not find out how to activate English language on Ubuntu. Basically it names dependency problems (Abhängigkeitsprobleme). I marked the version numbers and programs in bold print:

```
timo@ubuntu:~/Desktop$ sudo dpkg -i python2.4-exe_0.15-0.1ubuntu1_all.deb
Wähle vormals abgewähltes Paket python2.4-exe.
(Lese Datenbank ... 176136 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke python2.4-exe (aus python2.4-exe_0.15-0.1ubuntu1_all.deb) ...
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von python2.4-exe:
 **python2.4-exe** hängt ab von **python2.4-nevow (= 0.4.1-1.1ubuntu1)**; aber:
  Version von python2.4-nevow auf dem System ist** 0.6.0-2ubuntu3**.
 python2.4-exe hängt ab von **python2.4-twisted (= 2.0.1-999)**; aber:
  Version von python2.4-twisted auf dem System ist **2.2.0-2ubuntu1**.
dpkg: Fehler beim Bearbeiten von python2.4-exe (--install):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
Fehler traten auf beim Bearbeiten von:
 python2.4-exe
```

After that, I have to "repair" apt-get with ```
sudo apt-get install -f

```.

Also, I cannot install the provided version of twisted from the eXe website. Ubuntu won't install this version:

```
timo@ubuntu:~/Desktop$ sudo dpkg -i python2.4-twisted_2.0.1-999_all.deb
Password:
dpkg - Warnung: deaktualisiere python2.4-twisted von 2.2.0-2ubuntu1 zu 2.0.1-999.
dpkg: Betrachte python2.4-twisted_2.0.1-999_all.deb, welches python2.4-twisted enthält:
 python2.4-twisted-names kollidiert mit python2.4-twisted (<< 2.1)
  python2.4-twisted (Version 2.0.1-999) soll installiert werden.
dpkg: Fehler beim Bearbeiten von python2.4-twisted_2.0.1-999_all.deb (--install):
 kollidierende Pakete - installiere python2.4-twisted nicht
Fehler traten auf beim Bearbeiten von:
 python2.4-twisted_2.0.1-999_all.deb
```

I need this editor for my work, and I don't really want to boot up Windows XP just for this programm when I could use it with Ubuntu.

Any idea how I can do the install without breaking my computer? :-)

Any help is appreciated!

Cheers,
Timo

---

### Post by Timokl on 2006-08-27
Anybody with an idea??? Any kind of help is highly(!) appreciated!!!

---

### Post by fpalm on 2007-02-24
Hi Timok

First download exelearning source

```
$wget http://eduforge.org/frs/download.php/455/exe-0.21-source.tgz
```then unpackage
```
$tar xzvf exe-0.21-source.tgz
```and install
```
$cd exe-0.21
$sudo python setup.py install
```(You need thar python-setuptools is installed)
then run!
```

$exe &

```and go to firefox using this address
[http://localhost:51235](http://localhost:51235)

You can change this port editing exe.conf file that is in the .exe folder on your home.

---

### Post by Timokl on 2007-02-25
Hi Francisco,

thanks for your reply. Actually, I got quite fine without eXe now, but I tried to install it following your instructions anyway. However, it did not work because the Zope Interface is not installed. So, I downloaded the Zope from [http://zope.org/Products/ZopeInterface/](http://zope.org/Products/ZopeInterface/), but I failed to install it, too. The installer cannot execute gcc for some reason. Installing Zope looks like this:

```
timo@aristoteles:~/Desktop/ZopeInterface-3.0.1$ sudo python setup.py install
running install
running build
running build_py
running build_ext
building 'zope.interface._zope_interface_coptimizations' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -fPIC -IDependencies/zope.interface-ZopeInterface-3.0.1/zope.interface -I/usr/include/python2.4 -c Dependencies/zope.interface-ZopeInterface-3.0.1/zope.interface/_zope_interface_coptimizations.c -o build/temp.linux-i686-2.4/Dependencies/zope.interface-ZopeInterface-3.0.1/zope.interface/_zope_interface_coptimizations.o
Dependencies/zope.interface-ZopeInterface-3.0.1/zope.interface/_zope_interface_coptimizations.c:339: error: static declaration of ‘SpecType’ follows non-static declaration
Dependencies/zope.interface-ZopeInterface-3.0.1/zope.interface/_zope_interface_coptimizations.c:73: error: previous declaration of ‘SpecType’ was here
error: command 'gcc' failed with exit status 1
```

Anyway, thanks for your help.

Regards,
Timo

---

