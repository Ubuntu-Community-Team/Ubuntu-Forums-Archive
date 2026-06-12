---
title: "Compillation and installation of katalog-0.4 on Edgy"
date: 2007-01-25
forum: Installation &amp; Upgrades
---

### Post by mslonik on 2007-01-25
Dear All,

There is excellent application for indexing resources (database like application) called "katalog". This application is designed for KDE. It is my favourite application of its kind, fully integrated with "Konqueror". On second day of Christmas new improved version was realised by Stefano Salvador. So couple of days later I decided to install my own brand new version of "Katalog". Unfortunately no new packet for "Kubuntu" 6.10 is available. The only way to have it was to compile a code from sources. Compilation process wasn't easy, but finally I am successful. It is time to share with others of my experience, step by step.

```

cd ~
maciej@maciej-laptop:~$ 
maciej@maciej-laptop:~$ mkdir --verbose temp1
mkdir: utworzony katalog `temp1'
maciej@maciej-laptop:~/temp1$ wget http://kde-apps.org/content/download.php?content=12426&id=1
maciej@maciej-laptop:~/temp1$ ls -l
razem 212
-rw-r--r-- 1 maciej maciej 209439 2006-12-25 23:48 12426-katalog-0.4.tar.gz

maciej@maciej-laptop:~/temp1$ gzip -dc 12426-katalog-0.4.tar.gz | tar xvfp -

maciej@maciej-laptop:~/temp1$ ls -l
razem 216
-rw-r--r--  1 maciej maciej 209461 2006-12-25 23:48 12426-katalog-0.4.tar.gz
drwxr-xr-x 14 maciej maciej   4096 2006-12-25 22:31 katalog-0.4

maciej@maciej-laptop:~/temp1$ cd katalog-0.4/
maciej@maciej-laptop:~/temp1/katalog-0.4$ ./configure
Checking for Python               :  -e /usr/bin/python
Checking for SCons                :  -e not found, will use mini distribution.
./configure: 83: [[: not found
calling scons configure with parameters
Checking for kde-config           :  kde-config was found as /usr/bin/kde-config
Checking for kde version          :  3.5.5
Checking for the qt library       :  qt was not found
Please set QTDIR first (/usr/lib/qt3?) or try scons -h for more options

maciej@maciej-laptop:~/temp1/katalog-0.4$ apt-cache search qt3 library
libqt3-mt-dev - Qt development files (Threaded)
libqt4-qt3support - Qt 3 compatibility library for Qt 4
qt3-designer - Qt3 Designer
libqt3-i18n - i18n files for Qt3 library
libqt4-qt3support-kdecopy - Qt 3 compatibility library for Qt 4
libavahi-qt3-1 - Avahi QT3 integration library
libavahi-qt3-dev - Development headers for the Avahi QT3 integration library
kadu-aosound - ao library sound module for Kadu

maciej@maciej-laptop:~/temp1/katalog-0.4$ sudo apt-get install libqt3-mt-dev

maciej@maciej-laptop:~/temp1/katalog-0.4$ ./configure
Checking for Python               :  -e /usr/bin/python
Checking for SCons                :  -e not found, will use mini distribution.
./configure: 83: [[: not found
calling scons configure with parameters
Checking for kde-config           :  kde-config was found as /usr/bin/kde-config
Checking for kde version          :  3.5.5
Checking for the qt library       :  qt was not found
Please set QTDIR first (/usr/lib/qt3?) or try scons -h for more options

maciej@maciej-laptop:~/temp1/katalog-0.4$ export QTDIR=/usr/lib/qt3

maciej@maciej-laptop:~/temp1/katalog-0.4$ ./configure
Checking for Python               :  -e /usr/bin/python
Checking for SCons                :  -e not found, will use mini distribution.
./configure: 83: [[: not found
calling scons configure with parameters
Checking for kde-config           :  kde-config was found as /usr/bin/kde-config
Checking for kde version          :  3.5.5
Checking for the qt library       :  qt is in /usr/lib/qt3
Checking for uic                  :  uic was found as /usr/bin/uic
Checking for moc                  :  moc was found as /usr/bin/moc
Checking for the qt includes      :  the qt headers were found in /usr/include/qt3/
Checking for the kde includes     :  The kde includes were NOT found

maciej@maciej-laptop:~/temp1/katalog-0.4$ sudo apt-get install kde-devel

maciej@maciej-laptop:~/temp1/katalog-0.4$ ./configure
Checking for Python               :  -e /usr/bin/python
Checking for SCons                :  -e not found, will use mini distribution.
./configure: 83: [[: not found
calling scons configure with parameters
Checking for kde-config           :  kde-config was found as /usr/bin/kde-config
Checking for kde version          :  3.5.5
Checking for the qt library       :  qt is in /usr/lib/qt3
Checking for uic                  :  uic was found as /usr/bin/uic
Checking for moc                  :  moc was found as /usr/bin/moc
Checking for the qt includes      :  the qt headers were found in /usr/include/qt3/
Checking for the kde includes     :  the kde headers were found in /usr/include/kde/
Checking for pkg-config           :  ok
Checking for sqlite3 >= 3.1       :  failed
sqlite >= 3.1 was not found (mandatory).

maciej@maciej-laptop:~/katalog-0.4/katalog-0.4$ sudo apt-get install libsqlite3-0 libsqlite3-dev

```

Now it is time for something not obvious. It could be a pitful to you, so pay some extra attention. We already have installed the following libraries: "libsqlite3-0" and "libsqlite3-dev", but ./configure script is still compaining:

```

maciej@maciej-laptop:~/katalog-0.4/katalog-0.4$ ./configure
Checking for Python               :  -e /usr/bin/python
Checking for SCons                :  -e not found, will use mini distribution.
./configure: 83: [[: not found
calling scons configure with parameters
Checking for kde-config           :  kde-config was found as /usr/bin/kde-config
Checking for kde version          :  3.5.5
Checking for the qt library       :  qt is in /usr/lib/qt3
Checking for uic                  :  uic was found as /usr/bin/uic
Checking for moc                  :  moc was found as /usr/bin/moc
Checking for the qt includes      :  the qt headers were found in /usr/include/qt3/
Checking for the kde includes     :  the kde headers were found in /usr/include/kde/
Checking for pkg-config           :  ok
Checking for sqlite3 >= 3.1       :  failed
sqlite >= 3.1 was not found (mandatory). 

```

The only way that I know to round that obstacle looks as follows:
```

maciej@maciej-laptop:~/katalog-0.4/katalog-0.4$ sudo apt-get install scons

```

Since then everything goes smooth as it should be from the beginning:
```

maciej@maciej-laptop:~/katalog-0.4/katalog-0.4$ ./configure
Checking for Python               :  -e /usr/bin/python
Checking for SCons                :  -e /usr/bin/scons
./configure: 83: [[: not found
calling scons configure with parameters
Checking for kde-config           :  kde-config was found as /usr/bin/kde-config
Checking for kde version          :  3.5.5
Checking for the qt library       :  qt is in /usr/lib/qt3
Checking for uic                  :  uic was found as /usr/bin/uic
Checking for moc                  :  moc was found as /usr/bin/moc
Checking for the qt includes      :  the qt headers were found in /usr/include/qt3/
Checking for the kde includes     :  the kde headers were found in /usr/include/kde/

```

Now we can proceed further, down to the compilation.

```

maciej@maciej-laptop:~/katalog-0.4/katalog-0.4$ sudo apt-get install g++ 

```

Remark. It is not enough just to install the packet "g++-4.1". You should install the "g++", as it was written above.

```

maciej@maciej-laptop:~/katalog-0.4/katalog-0.4$ make
maciej@maciej-laptop:~/katalog-0.4/katalog-0.4$ sudo make install 

```

If everything went fine, we have brand new, fantastic plugin for "Konqueror", ready at our service. Enjoy!


How to use "Katalog"? What is it for?

Example: We would like to have a database of our audio cds in well established format. "Konqueror" (KDE default browser) is able to detect and recognize audio cd. After that it sends a query to "freedb.org". If our audio cd is already present in "freedb.org" database then after couple of seconds all songs are named in the manner: title / artist. Now to the scene comes "Katalog". With a few mouse clicks we get build index of all .cda (audio) files. In "Konqueror" window choose address entry (shortcut: F6). Enter:

media:/

After a short while, inside of a main "Konqueror" panel we should see between others an icon of audio cd. Lets click on it (clicking once is enough). Now "Konqueror" should display couple of folders, e.g. CDA, FLAC, MP3, etc. We are interested in CDA folder. Click on it with right mouse button (or take a shortcut "Shift+F10" or windows keyboard special key "options"). From the menu choose: "Action" -> "Create catalog". It is done! "Katalog" will ask us about name of the index file.

Now we would like to see our new index file. Again, lets start at address entry in "Konqueror" (F6):

katalog:/

If there is nothing in "catalogs" folder, then refresh its content with "Ctrl+R" shortcut.

You can index any folder you like. Have a good time with it!

Kind regards,
Maciej (mslonik)

---

