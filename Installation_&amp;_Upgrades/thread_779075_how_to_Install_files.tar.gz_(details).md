---
title: "how to Install files.tar.gz (details)"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by blacappuccino on 2008-05-02
Hey guys i tried to install a lot of programs using console but every time it give an error, the problem is that all the posts that i read doesn't explain completely the installation process, i lot of them say that before decompressed process type:

./configure
make
make install

But it doesn't mean nothing, i browser other post and i find out the the correct process is:

tar -xvzf file-to-install.tar.gz
[ENTER]
cd file-to-install
[ENTER]
sudo ./configure
[ENTER]
(type my log in password)

So far so good, but before that i try to use command "make", just typing, it gives and error, the same happened with make install. A kind of, no targets specified, so i don't know how to specify

So i count with u guys to give me clear details. below i made a copy past what i try to explain u.

cheers 

> ceoc@Carmo:~$ tar xvzf gwget-0.99.tar.gz
gwget-0.99/
gwget-0.99/po/
gwget-0.99/po/ChangeLog
gwget-0.99/po/Makefile.in.in
gwget-0.99/po/POTFILES.in
gwget-0.99/po/ar.po
gwget-0.99/po/bg.po
gwget-0.99/po/ca.po
gwget-0.99/po/cs.po
gwget-0.99/po/da.po
gwget-0.99/po/de.po
gwget-0.99/po/dz.po
gwget-0.99/po/el.po
gwget-0.99/po/en_CA.po
gwget-0.99/po/en_GB.po
gwget-0.99/po/es.po
gwget-0.99/po/eu.po
gwget-0.99/po/fi.po
gwget-0.99/po/fr.po
gwget-0.99/po/hu.po
gwget-0.99/po/it.po
gwget-0.99/po/ja.po
gwget-0.99/po/lt.po
gwget-0.99/po/mk.po
gwget-0.99/po/ne.po
gwget-0.99/po/nl.po
gwget-0.99/po/pa.po
gwget-0.99/po/pl.po
gwget-0.99/po/pt.po
gwget-0.99/po/pt_BR.po
gwget-0.99/po/ro.po
gwget-0.99/po/ru.po
gwget-0.99/po/rw.po
gwget-0.99/po/sk.po
gwget-0.99/po/sq.po
gwget-0.99/po/sv.po
gwget-0.99/po/tr.po
gwget-0.99/po/uk.po
gwget-0.99/po/vi.po
gwget-0.99/po/zh_CN.po
gwget-0.99/po/zh_HK.po
gwget-0.99/po/zh_TW.po
gwget-0.99/README
gwget-0.99/Makefile.in
gwget-0.99/configure
gwget-0.99/AUTHORS
gwget-0.99/COPYING
gwget-0.99/ChangeLog
gwget-0.99/INSTALL
gwget-0.99/Makefile.am
gwget-0.99/NEWS
gwget-0.99/THANKS
gwget-0.99/TODO
gwget-0.99/aclocal.m4
gwget-0.99/config.guess
gwget-0.99/config.h.in
gwget-0.99/config.sub
gwget-0.99/configure.in
gwget-0.99/depcomp
gwget-0.99/gwget.desktop.in
gwget-0.99/install-sh
gwget-0.99/ltmain.sh
gwget-0.99/missing
gwget-0.99/mkinstalldirs
gwget-0.99/intltool-extract.in
gwget-0.99/intltool-merge.in
gwget-0.99/intltool-update.in
gwget-0.99/src/
gwget-0.99/src/Makefile.in
gwget-0.99/src/Makefile.am
gwget-0.99/src/gwget-application-service.h
gwget-0.99/src/gwget-application-client.h
gwget-0.99/src/main.c
gwget-0.99/src/main_window.c
gwget-0.99/src/main_window.h
gwget-0.99/src/main_window_cb.c
gwget-0.99/src/main_window_cb.h
gwget-0.99/src/gwget_data.c
gwget-0.99/src/gwget_data.h
gwget-0.99/src/wget-log.c
gwget-0.99/src/wget-log.h
gwget-0.99/src/utils.c
gwget-0.99/src/utils.h
gwget-0.99/src/custom-cell-renderer-progressbar.c
gwget-0.99/src/custom-cell-renderer-progressbar.h
gwget-0.99/src/new_window.c
gwget-0.99/src/new_window.h
gwget-0.99/src/systray.c
gwget-0.99/src/systray.h
gwget-0.99/src/gwget-application.c
gwget-0.99/src/gwget-application.h
gwget-0.99/src/md5.h
gwget-0.99/src/md5.c
gwget-0.99/src/gwget-application-service.xml
gwget-0.99/pixmaps/
gwget-0.99/pixmaps/Makefile.in
gwget-0.99/pixmaps/Makefile.am
gwget-0.99/pixmaps/gwget.xpm
gwget-0.99/pixmaps/gwget.png
gwget-0.99/pixmaps/gwget-off.png
gwget-0.99/pixmaps/gwget-large.png
gwget-0.99/pixmaps/downloading.png
gwget-0.99/pixmaps/newdownload.png
gwget-0.99/data/
gwget-0.99/data/Makefile.in
gwget-0.99/data/Makefile.am
gwget-0.99/data/preferences.glade
gwget-0.99/data/gwget.glade
gwget-0.99/data/org.gnome.gwget.service.in
gwget-0.99/data/gwget.schemas.in
gwget-0.99/epiphany-extension/
gwget-0.99/epiphany-extension/Makefile.in
gwget-0.99/epiphany-extension/Makefile.am
gwget-0.99/epiphany-extension/ephy-gwget.c
gwget-0.99/epiphany-extension/ephy-gwget-extension.c
gwget-0.99/epiphany-extension/ephy-gwget-extension.h
gwget-0.99/epiphany-extension/gwget.xml.in.in
ceoc@Carmo:~$ cd gwget-0.99
ceoc@Carmo:~/gwget-0.99$ sudo ./configure
[sudo] password for ceoc:
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gconftool-2... /usr/bin/gconftool-2
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name...
configure: error: C compiler cannot create executables
See `config.log' for more details.
ceoc@Carmo:~/gwget-0.99$ make
make: *** No targets specified and no makefile found.  Stop.
ceoc@Carmo:~/gwget-0.99$ make install
make: *** No rule to make target `install'.  Stop.
ceoc@Carmo:~/gwget-0.99$ sudo make
make: *** No targets specified and no makefile found.  Stop.

---

### Post by oldos2er on 2008-05-02
If you want to compile gwget, you first need to install the package build-essential. But, it looks like this program has an install.sh file, so after extracting it you would type "sh ./install.sh". It helps to read the README  and INSTALL files to find out exactly what to do.

 But I think the easiest way to install this program would be to type "sudo aptitude install gwget" in a terminal.

 Also see [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by blacappuccino on 2008-05-02
Ok, i don't know if you know what i mean... i tried to read a lot of READ ME and INSTALL, but they give error the same error in "make" or "make install" command (no target specified )

Can u install an application using console and make a copy-paste to here... is what i need to finish all installation.

I use gwget as example. i tried, with provoxy, thunderbird...

Cheers

---

### Post by GavinZac on 2008-05-02
As he has said, its probably best not to compile and install programs like this until you're quite used to using Ubuntu a lot.

You can install this and those other programs easily with the package manager.

---

### Post by uchuunoyanushi on 2008-05-02
This line:

> configure: error: C compiler cannot create executables

Is telling you that configure can't find a complier to compile the code into a format that your computer will understand. Without that, make won't work. Are you sure you have build-essential package installed?

In my experience, installing from source is always a little touch and go.  Unlike a package manager, when you install from source, it won't automatically install dependencies, you will have to install them yourself before you can install the program.  I would recommend installing anything you can from the package manager (synaptic or apt-get/aptitude from the terminal), but if you have to install from source, here are a few tips.

1) Check the website of the program you are installing. They should list the required dependencies there.  Make sure you have these dependencies installed. You may need to have at least a specific version or the -dev files.  Also, read the README file and/or any installation documentation on the site.

2) Run ./configure. This will check your system for the required dependencies. The lines that ./configure output to your terminal are also outputted to a text file in the directory of the source files you unpacked from the tar.gz.  It should be called something like 'config.log'. Check this file to make sure that all the necessary elements were recognized. Depending on what you are installing, it may be ok if some things were not recognized depending on which features of the program you don't want to install. If you've read the documentation, you should know what you absolutely have to have.

3) Now run make and then **sudo** make install. And cross your fingers.

If you have any problems, read over the messages outputted to the terminal.  It may look like a bunch of junk that your computer is spitting out at you, but it's fairly self-explanatory if you read it carefully.

More information on installing files in Ubuntu is here: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Hope this helps.

---

### Post by oldos2er on 2008-05-02
> **blacappuccino said:**
> Ok, i don't know if you know what i mean... i tried to read a lot of READ ME and INSTALL, but they give error the same error in "make" or "make install" command (no target specified )

 As I said, you need to install the package build-essential.

---

