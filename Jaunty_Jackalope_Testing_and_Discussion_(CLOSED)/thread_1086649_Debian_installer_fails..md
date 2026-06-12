---
title: "Debian installer fails."
date: 2009-03-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by GARoss on 2009-03-04
Using Jaunty Alpha 5 with some but not all updates. The problem is in installing .deb files.
I need debian to install a Turboprint.deb file for my printer. The package manager says debian is installed but when I try to install the file, it just appears to start & nothing else (no install window - only a 10 second Gdebi Package Installer in the taskbar that closes on it's own & cannot be opened).
How can I check my system to see where the error occurs? There's no error warning of any kind.  
Any ideas?

---

### Post by Speque on 2009-03-04
> **GARoss said:**
> How can I check my system to see where the error occurs? There's no error warning of any kind.  
Any ideas?

Try to install the package from the command line like this (in the folder where the deb-file is located)

```
sudo dpkg -i turboprint.deb
```

and see what kind of error message is printed.

---

### Post by GARoss on 2009-03-04
> **Speque said:**
> Try to install the package from the command line like this (in the folder where the deb-file is located)

```
sudo dpkg -i turboprint.deb
```

and see what kind of error message is printed.
Thanks, Speque
The exact name of the file is *turboprint_2.07-1_amd64.deb* It reads;

george@kgeorge-desktop:~$ sudo dpkg -i turboprint_2.07-1_amd64.deb
dpkg: error processing turboprint_2.07-1_amd64.deb (--install):
 **cannot access archive: No such file or directory**
Errors were encountered while processing:
 turboprint_2.07-1_amd64.deb

I may be barking up the wrong tree but viewing permissions to */usr/share/perl/5.10.0/Archive* folder says, **Only the owner can change permissions**. Ownership at the bottom says, 
[B]User: root
Group: root[/B]

Is ownership the problem? How is this changed?

George

---

### Post by glotz on 2009-03-04
dpkg is the Debian package manager.

Debian-installer is the tool used when you install Debian, the GNU/Linux distribution.

Are you in the correct folder? Did you typ0 the filename? You wrote Turboprint and turboprint, which one is it?

---

### Post by GARoss on 2009-03-04
> **glotz said:**
> dpkg is the Debian package manager.

Debian-installer is the tool used when you install Debian, the GNU/Linux distribution.

Are you in the correct folder? Did you typ0 the filename? You wrote Turboprint and turboprint, which one is it?
The file, .*deb file, turboprint_2.07-1_amd64.deb* is located in my desktop folder. I believe I did this correctly;
  
george@kgeorge-desktop:~$ sudo dpkg -i turboprint_2.07-1_amd64.deb
dpkg: error processing turboprint_2.07-1_amd64.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
turboprint_2.07-1_amd64.deb

I've used this same file in Ubuntu 8.10 & Kubuntu jaunty alpha 4 without problems. 
I also tried Speque's, sudo dpkg -i turboprint.deb

george@kgeorge-desktop:~$ sudo dpkg -i turboprint.deb
[sudo] password for george:
dpkg: error processing turboprint.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 turboprint.deb

Also tried a 0 in the file name'
george@kgeorge-desktop:/$ sudo dpkg -i 0turboprint_2.07-1_amd64.deb
dpkg: error processing 0turboprint_2.07-1_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 0turboprint_2.07-1_amd64.deb
george@kgeorge-desktop:/$

 George

---

### Post by glotz on 2009-03-04
Please humor me,```
pwd
```

---

### Post by GARoss on 2009-03-04
> **glotz said:**
> Please humor me,```
pwd
```

I'll try;)

[I]george@kgeorge-desktop:~$ pwd
/home/george[/I]

I have the deb file located in /home/george/turboprint_2.07-1_amd64.deb
George

---

### Post by glotz on 2009-03-04
Does ls agree?```
ls /home/george/turboprint_2.07-1_amd64.deb
```
I don't think it's a permissions issue since you are using sudo.

---

### Post by GARoss on 2009-03-04
Apparently there is a bug report on this. I found this post @ kubuntuforums.net.

[http://kubuntuforums.net/forums/index.php?topic=3102087.0](http://kubuntuforums.net/forums/index.php?topic=3102087.0)

His first work-a-round suggestion, *try KPackageKit*, worked perfectly. Now I can print!
Thanks glotz & Speque for your suggestions.
George

---

### Post by glotz on 2009-03-04
Wow, didn't see that coming! :)

And you're quite welcome.

---

