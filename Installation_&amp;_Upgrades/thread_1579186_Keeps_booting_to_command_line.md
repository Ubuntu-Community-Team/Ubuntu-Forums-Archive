---
title: "Keeps booting to command line"
date: 2010-09-21
forum: Installation &amp; Upgrades
---

### Post by PaulM1985 on 2010-09-21
Hi

I am running 64bit 10.04 (Lucid) with Kernel 2.6.32.24-generic and I keep finding that Ubuntu keeps booting to command line.  I have found that by typing "startx" I am able to load up the GUI.  Is there a way I can get it to start like this every time?  

I used to get the GUI login screen but I don't anymore.  Is there a way I can change this?

Paul

---

### Post by sanderd17 on 2010-09-21
try this:

```

sudo dpkg -reconfigure xserver-xorg

```

---

### Post by PaulM1985 on 2010-09-21
That didn't seem to work.  The output looks like it got confused by the command:

```

paul@paul-desktop:~$ sudo dpkg -reconfigure xserver-xorg
[sudo] password for paul: 
dpkg: conflicting actions -e (--control) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

```

Any ideas?

Paul

---

### Post by sanderd17 on 2010-09-21
sorry, was wrong, maybe you can look at this thread:

[http://www.linuxquestions.org/questions/ubuntu-63/boot-into-console-command-line-instead-of-x-549292/]("http://www.linuxquestions.org/questions/ubuntu-63/boot-into-console-command-line-instead-of-x-549292/")

---

### Post by PaulM1985 on 2010-09-21
Hi

reconfigure does not seem to be an option dpkg recognises:

```

paul@paul-desktop:~$ sudo dpkg --reconfigure xserver-xorg
dpkg: unknown option --reconfigure

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

```

I tried --configure and it already said that it was installed and configured.  I looked at the thread you linked in your last post.  That seems to be the opposite of what I want to do.  I don't want to keep booting to the command line.  I want to boot to the GUI.

Sorry if my original post wasn't clear.

Paul

---

### Post by PaulM1985 on 2010-09-21
Regarding the previous posts I think you may have meant:

```

sudo dpkg-reconfigure xserver-xorg

```

(No gap between dpkg and -reconfigure)

That did not solve the problem.

I found another thread which seemed to be pointing fingers towards nvidia graphics card drivers. It suggested that removing and re-installing gdm may solve the problem.

I tried this doing:

```

sudo apt-get remove gdm
sudo apt-get install gdm

```

This is reported to be a temporary fix on the thread:
[http://ulyssesonline.com/2010/08/14/gdm-does-not-start-in-ubuntu-10-04/](http://ulyssesonline.com/2010/08/14/gdm-does-not-start-in-ubuntu-10-04/)

And although it has fixed my problem after the first reboot I don't know if this will stay fixed.

Thanks for the help.

Paul

---

