---
title: "install longman dictionary of con. english"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by erdogan aldemir on 2010-03-23
i can not install contemporary english IDM 2005 on ubuntu
there are  installation.sh file in linux folder...
i run it on terminal but i can't install
can you help me about it
thank you......

---

### Post by lemming465 on 2010-03-24
I haven't used the Longman dictionaries, so I'm guessing here, after looking briefly at their web site.  I infer you have purchased in installable version of the dictionary, probably on 2 CD's.  The first 3 things I can think of off-hand that might be issues are where it expects to be run from, which shell it expects to be used, and the likely need to run as root.  I'm going to be brave and assume your ubuntu version is sufficiently similar to the Debian 3.0 they claimed to support in 2008 so that things can work.

If there is a file named "README" or "INSTALL" check it for helpful directions.  Try reading it with "less" if it's a text file, "firefox" if it's an HTML file, or "evince" if it's a PDF file.

The install script probably expects to be run from its own directory (using relative paths).  Alternatively, it might expect to be run from the root directory.  As a last resort, in the directory you want to install to, possibly your home directory.

Probably the install script is written for Bash, or some Posix compliant shell.  However, on recent versions of Ubuntu, the /bin/sh shell is not bash (/bin/bash), but "dash", a smaller, faster, mostly compatible shell.  If the install script starts of "#!/bin/sh" it will be run by "dash", and that might not work.  Debian 3 used bash as /bin/sh, as did early versions of Ubuntu.

Also, it's highly likely that the install script has to be run as root.  So my first try would be:

1. pop in the first CD
2. change into the linux installation directory using "cd", e.g. "cd /media/cdrom/linux", or wherever
3. Run the script as root using the bash shell as the interpreter and specifying the full path to the script, i.e. "sudo bash $PWD/installation.sh"

Other things that could go wrong:  it might be inheriting an insufficient PATH environment variable that doesn't include /sbin and /usr/sbin (try "echo $PATH" to see what you've got).  A fix for that is "PATH=$PATH:/sbin:/usr/sbin".

If the installer is sufficiently archaic, it might not expect to be run in a UTF-8 locale.  Try doing "export LC_ALL=C" before running the install script.

---

### Post by liedan on 2010-04-08
Hi Erdogan,

Try solution presented here: [http://ubuntuforums.org/showthread.php?t=1387641&highlight=longman](http://ubuntuforums.org/showthread.php?t=1387641&highlight=longman)

I have ubuntu karmic 64bit and LDOCE4_2 (or something like that) and this is what I did.

1.I  ran installation.sh from cd by :

```
linux32 /media/cdrom/linux/installation.sh 
```A terminal-based installer launched with the message "You are running an x86 machine with glibc-2.1", I pressed OK, then I agreed with the licence and chose the instalation directory. Then the installer did it's work.

2. If you had LDOCE5, you are probably good to go already. However, i had to install library libgtk1.2 as well. It is not in karmic repositories, so I had to download it (32bit version) from Jaunty repositories [http://packages.ubuntu.com/jaunty/libgtk1.2](http://packages.ubuntu.com/jaunty/libgtk1.2) together with its dependencies ([libglib1.2ldbl]("http://packages.ubuntu.com/jaunty/libglib1.2ldbl") and [libgtk1.2-common]("http://packages.ubuntu.com/jaunty/libgtk1.2-common")      ).

I installed them manually by running:
```
dpkg -i --force_architecture *i386.deb
```(not nice, but i don' t know better solution)

And that's it!:guitar: All basic things works (searching,sound..), although i did not test anything special.

Hope this helps.

Liedan

---

### Post by ogai on 2010-07-21
> **liedan said:**
> 

I have ubuntu karmic 64bit and LDOCE4_2 (or something like that) and this is what I did.

1.I  ran installation.sh from cd by :

```
linux32 /media/cdrom/linux/installation.sh 
```A terminal-based installer launched with the message "You are running an x86 machine with glibc-2.1", I pressed OK, then I agreed with the licence and chose the instalation directory. Then the installer did it's work.

2. If you had LDOCE5, you are probably good to go already. However, i had to install library libgtk1.2 as well. It is not in karmic repositories, so I had to download it (32bit version) from Jaunty repositories [http://packages.ubuntu.com/jaunty/libgtk1.2](http://packages.ubuntu.com/jaunty/libgtk1.2) together with its dependencies ([libglib1.2ldbl]("http://packages.ubuntu.com/jaunty/libglib1.2ldbl") and [libgtk1.2-common]("http://packages.ubuntu.com/jaunty/libgtk1.2-common")      ).

I installed them manually by running:
```
dpkg -i --force_architecture *i386.deb
```(not nice, but i don' t know better solution)



This instructions also work for Ubuntu Lucid 64bit. In order to get sound working, I have done the following:

1. aptitude install alsa-oss

2. Add your username to the group audio in /etc/group

---

