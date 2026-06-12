---
title: "Installing Calibre for xubuntu 16.04"
date: 2017-08-13
forum: Installation &amp; Upgrades
---

### Post by Jorhel on 2017-08-13
Hi,
just did a bit of readig around the forum to find how to convert .pdf files to .epub format and calibre seems to be the way to do it.
However while browsing I also found a few people having issues after installing Calibre (Like stuffing up their desktop). 
Since it's more a "would be nice" thing than a "I really need it now" I thought I will make sure I got my bases covered before trying.

the calibre website recommend to use:
```
sudo -v && wget -nv -O- https://download.calibre-ebook.com/linux-installer.py | sudo python -c "import sys; main=lambda:sys.stderr.write('Download failed\n'); exec(sys.stdin.read()); main()"
```
to install rather than from the apt-get command.

It also specify:>              You must have xdg-utils, wget and python &#8805; 2.6 installed on your system before running the installer.         


So my first question is how do I know if I have them?
I did a fresh install of xubuntu 16.04 on a Compacq Presario desktop. 32 bits CPU AMD Athlon XP a couple of month ago. Quite a few things have gone wrong with it but most of it is sorted now so I'm a bit weary of getting it wrong.

Thanks

---

### Post by oldos2er on 2017-08-13
```
apt policy xdg-utils
``` will show if that package is installed, and its version. Repeat for each package you wish to know about. Or you could check in Synaptic Package Manager, if you have that installed.

Tip: When checking python with apt policy, type ```
apt policy python2
``` then hit Tab twice to have the shell autocomplete the package names for you.

---

### Post by vasa1 on 2017-08-13
```
apt list --installed | grep -E "(^python2|wget|xdg-utils)"
```should work too:```
$ apt list --installed | grep -E "(^python2|wget|xdg-utils)"

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

python2.7/xenial-updates,xenial-security,now 2.7.12-1ubuntu0~16.04.1 amd64 [installed]
python2.7-minimal/xenial-updates,xenial-security,now 2.7.12-1ubuntu0~16.04.1 amd64 [installed]
wget/xenial-updates,now 1.17.1-1ubuntu1.2 amd64 [installed]
xdg-utils/xenial-updates,now 1.1.1-1ubuntu1.16.04.1 all [installed]
$ 
```

---

### Post by vocx on 2017-08-13
> **Jorhel said:**
> 
It also specify:
```

You must have xdg-utils, wget and python &#8805; 2.6 installed on your system before running the installer.         

```

So my first question is how do I know if I have them?
I did a fresh install of xubuntu 16.04 on a Compacq Presario desktop. 32 bits CPU AMD Athlon XP a couple of month ago. Quite a few things have gone wrong with it but most of it is sorted now so I'm a bit weary of getting it wrong.

Thanks
The "wget" program is an extremely common utility used to download files from the Internet. I think it should be present in your system by default.

Python is an extremely common programming language used in the free software world. Ubuntu uses it for many small utilities here and there. It is already installed in your system. The standard Python version is 2.7 so you are already satisfying this requirement. There is also a Python version 3, maybe 3.5 currently, which is still developing further. Many programs nowadays are intended to work with the Python 3.x series, but probably work fine with 2.7. So the 2.7 version is a minimum requirement, which most Linux distributions surely have.

I don't recall hearing about "xdg-utils" before, but surely you can install it simply.
```

sudo apt install xdg-utils

```

---

### Post by ajgreeny on 2017-08-13
I have used calibre quite a lot and the version I use in Xubuntu 16.04-64bit is from the standard universe repos, calibre 2.55.0+dfsg-1.

I have never had a problem with it so I wonder what exactly are the problems you have read about?  What do you mean by "stuffing up their desktop"; stuffing it up with what?

---

### Post by vasa1 on 2017-08-13
> **vocx said:**
> ...
I don't recall hearing about "xdg-utils" before, but surely you can install it simply.
```

sudo apt install xdg-utils

```Even that should be installed by default on Xubuntu:```
$ apt rdepends xdg-utils | grep --color=auto xubuntu

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

  Depends: xubuntu-desktop
  Depends: xubuntu-core
$
```And, as ajgreeny indicates, why do you not want the standard version?

---

### Post by oldos2er on 2017-08-13
Calibre's one of the few programs I recommend installing from the website, rather than the repositories. It's under heavy development and is updated with both bug fixes and new features frequently, so the repository ones are outdated by a large margin.

If it's working for you though, nothing wrong with that.

---

### Post by ajgreeny on 2017-08-13
Following oldfred's comment in post #7 I have now installed direct from the calibre website using the first wget command shown on the download page, not from source as that appears to be a bit problematic according to the website itself.
That command ran very quickly on my system, downloading and installing version 3.6 in less than 60 seconds, and it found all my configuration from the old version 2.55.

Thanks for the tip oldfred!

---

### Post by oldos2er on 2017-08-13
I'm not oldfred (by a long shot!) but you're welcome.

---

### Post by Jorhel on 2017-08-13
> **ajgreeny said:**
> I have used calibre quite a lot and the version I use in Xubuntu 16.04-64bit is from the standard universe repos, calibre 2.55.0+dfsg-1.

I have never had a problem with it so I wonder what exactly are the problems you have read about?  What do you mean by "stuffing up their desktop"; stuffing it up with what?

I was referring to that post [https://ubuntuforums.org/showthread.php?t=2335346&highlight=calibre+desktop](https://ubuntuforums.org/showthread.php?t=2335346&highlight=calibre+desktop) by stuffed i meaned broken.

---

### Post by Jorhel on 2017-08-13
> **vasa1 said:**
> ```
apt list --installed | grep -E "(^python2|wget|xdg-utils)"
```should work too:```
$ apt list --installed | grep -E "(^python2|wget|xdg-utils)"

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

python2.7/xenial-updates,xenial-security,now 2.7.12-1ubuntu0~16.04.1 amd64 [installed]
python2.7-minimal/xenial-updates,xenial-security,now 2.7.12-1ubuntu0~16.04.1 amd64 [installed]
wget/xenial-updates,now 1.17.1-1ubuntu1.2 amd64 [installed]
xdg-utils/xenial-updates,now 1.1.1-1ubuntu1.16.04.1 all [installed]
$ 
```

Thanks that works fine. out of curiosity why the warning about apt? If I get it right apt replace apt-get now? But I installed a few things using apt-get and it still works.

---

### Post by vasa1 on 2017-08-13
*man apt* has this:```

SCRIPT USAGE AND DIFFERENCES FROM OTHER APT TOOLS
       The apt(8) commandline is designed as an end-user tool and it may change behavior between versions. While it tries not to break backward
       compatibility this is not guaranteed either if a change seems beneficial for interactive use.

       All features of apt(8) are available in dedicated APT tools like apt-get(8) and apt-cache(8) as well.  apt(8) just changes the default
       value of some options (see apt.conf(5) and specifically the Binary scope). So you should prefer using these commands (potentially with
       some additional options enabled) in your scripts as they keep backward compatibility as much as possible.
```

---

### Post by vocx on 2017-08-13
> **Jorhel said:**
> I was referring to that post [https://ubuntuforums.org/showthread.php?t=2335346&highlight=calibre+desktop](https://ubuntuforums.org/showthread.php?t=2335346&highlight=calibre+desktop) by stuffed i meaned broken.
I don't know what this Calibre software does, but it seems that it was conflicting in some strange ways with the MATE desktop.

The error messages in that thread mentioned stuff about the icons, and Gtk warnings, so it was very confusing.

But I don't think you should worry as it seems the error disappeared quickly by itself.

> **watchpocket said:**
> This issue was solved today with a simple upgrade using the Software Updater.  I think a new version of the MATE desktop was updated, and I think this was as a result of my having added a key ubuntu-mate repository that I did not previoulsy have in my software sources.

---

### Post by vasa1 on 2017-08-13
> **Jorhel said:**
> I was referring to that post [https://ubuntuforums.org/showthread.php?t=2335346&highlight=calibre+desktop](https://ubuntuforums.org/showthread.php?t=2335346&highlight=calibre+desktop) by stuffed i meaned broken.
Thanks for linking to that thread. The title of that thread, *Calibre (epub reader) install totally hosed my desktop*, could do with a removal of "Calibre (epub reader)" from the title even though it accurately reflected the poster's thoughts at the time but **not** by the time the thread was solved. I wonder how many potential users of Calibre were dissuaded by seeing such a title in their search results :???:

---

### Post by Jorhel on 2017-08-13
OK thanks guys I tried installing it and this happened
 ```
 snukies@LN-PN067AA-ABE-SR1259ES-ES441:~$ sudo -v && wget -nv -O- https://download.calibre-ebook.com/linux-installer.py | sudo python -c "import sys; main=lambda:sys.stderr.write('Download failed\n'); exec(sys.stdin.read()); main()"
[sudo] password for snukies: 
2017-08-14 14:04:34 URL:https://download.calibre-ebook.com/linux-installer.py [27407/27407] -> "-" [1]
Installing to /opt/calibre
Downloading tarball signature securely...
Will download and install calibre-3.6.0-i686.txz 
                       Downloading calibre-3.6.0-i686.txz                       
100% [======================================================================]
                                                                                Downloaded 60455872 bytes 
Checking downloaded file integrity... 
Extracting files to /opt/calibre ...
Extracting application files... 
Creating symlinks...
    Symlinking /opt/calibre/lrs2lrf to /usr/bin/lrs2lrf
    Symlinking /opt/calibre/ebook-device to /usr/bin/ebook-device
    Symlinking /opt/calibre/ebook-polish to /usr/bin/ebook-polish
    Symlinking /opt/calibre/ebook-viewer to /usr/bin/ebook-viewer
    Symlinking /opt/calibre/calibre-smtp to /usr/bin/calibre-smtp
    Symlinking /opt/calibre/calibre-server to /usr/bin/calibre-server
    Symlinking /opt/calibre/calibre-customize to /usr/bin/calibre-customize
    Symlinking /opt/calibre/calibre-debug to /usr/bin/calibre-debug
    Symlinking /opt/calibre/calibre-parallel to /usr/bin/calibre-parallel
    Symlinking /opt/calibre/web2disk to /usr/bin/web2disk
    Symlinking /opt/calibre/calibre to /usr/bin/calibre
    Symlinking /opt/calibre/markdown-calibre to /usr/bin/markdown-calibre
    Symlinking /opt/calibre/ebook-convert to /usr/bin/ebook-convert
    Symlinking /opt/calibre/ebook-meta to /usr/bin/ebook-meta
    Symlinking /opt/calibre/lrfviewer to /usr/bin/lrfviewer
    Symlinking /opt/calibre/lrf2lrs to /usr/bin/lrf2lrs
    Symlinking /opt/calibre/calibredb to /usr/bin/calibredb
    Symlinking /opt/calibre/fetch-ebook-metadata to /usr/bin/fetch-ebook-metadata
    Symlinking /opt/calibre/ebook-edit to /usr/bin/ebook-edit
Setting up command-line completion...
Installing zsh completion to: /usr/share/zsh/vendor-completions/_calibre
[COLOR=#ff0000]Failed to find directory to install bash completions, using default.[/COLOR]
Installing bash completion to: /usr/share/bash-completion/completions/calibre
Run "calibre" to start calibre 
snukies@LN-PN067AA-ABE-SR1259ES-ES441:~$ calibre
N[COLOR=#ff0000]o write acces to /home/snukies/.config/calibre using a temporary dir instead
Illegal instruction (core dumped)[/COLOR]
snukies@LN-PN067AA-ABE-SR1259ES-ES441:~$ 
```

I was kicked out of the internet connection during the download process but when I went back in line and restarted it it seemed to have picked up where it had stopped without problem.
I also get a pop up window from ubuntu saying calibre has stopped unexpectely do I want to send a report.
Calibre does not appear in my list of program but I guess that because it was installed from a tarball and not from the repository?
I'm the administrator on that computer so I don't understand why I have no write access.
I also noticed on the calibre web page that there is a warning > You need GLIBC 2.17 or higher and libstdc++.so.6.0.17 (from gcc 4.7.0) or higher to run calibre
But that would not cause that kind of message would it? 
tried:
```
apt list --installed | grep -E "(^GLIBC 2.17|libstdc++.so.6.0.17)"

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.


```
Does that mean I don't have it or is that not the right command for it?

I tried to remove calibre and reinstall with the same result.

---

### Post by ajgreeny on 2017-08-14
> **oldos2er said:**
> I'm not oldfred (by a long shot!) but you're welcome.
Whoops!!!

No, you're not are you. Sorry about that.

The new calibre version 3.6 seems to be working brilliantly, by the way.

---

### Post by Jorhel on 2017-08-21
Ok did a bit more digging and it seems I have GLIBC 2.23 
```
ldd --version
ldd (Ubuntu GLIBC 2.23-0ubuntu9) 2.23
Copyright (C) 2016 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
Written by Roland McGrath and Ulrich Drepper.
```
 
and the apt list --installed command returns
   ```
libstdc++6/xenial-updates,xenial-security,now 5.4.0-6ubuntu1~16.04.4 i386 [installed]
```
 
Amongst lines and lines of stuff starting with lib so I assume its OK too. on the other hand it is not 
libstdc++.so.6.0.17 so maybe not

Also tried ```
calibre-debug -g
No write acces to /home/snukies/.config/calibre using a temporary dir instead
calibre 3.6  embedded-python: True is64bit: False
Linux-4.10.0-32-generic-i686-athlon-with-debian-stretch-sid Linux ('32bit', 'ELF')
('Linux', '4.10.0-32-generic', '#36~16.04.1-Ubuntu SMP Wed Aug 9 09:18:53 UTC 2017')
Python 2.7.12
Linux: ('debian', 'stretch/sid', '')
Interface language: None
Illegal instruction (core dumped)
```



Anybody has any idea on why Calibre crashes on start up?

---

