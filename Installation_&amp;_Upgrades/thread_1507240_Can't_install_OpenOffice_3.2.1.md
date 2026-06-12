---
title: "Can't install OpenOffice 3.2.1"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by Tombgeek on 2010-06-11
Hey guys.

I have a small little problem. I recently removed OpenOffice.org 3.2.0 from Ubuntu 10.04 and downloaded the OO.o3.2.1 debs from the site. All fine and well, I got a 139mb file and I unzipped it to my desktop, until I tried to install it. 
49 deb files!
No problem, just search Google and use the terminal, right?
[IMG]http://www.zippoc.com/blog/wp-content/uploads/2007/02/lex-luthor-wrong1.jpg[/IMG]

It was suggested that I use this tutorial, but the terminal gives me an error.
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

I already unzipped the file to my desktop, and I got a file called "OOO320_m18_native_packed-1_en-GB.9502."

Using the terminal, I get an error saything the file does not exist.

> christopher@christopher-desktop:~$ cd OOO320_m18_native_packed-1_en-GB.9502/DEBSbash: cd: OOO320_m18_native_packed-1_en-GB.9502/DEBS: No such file or directory
christopher@christopher-desktop:~$ sudo dpkg -i *.deb
[sudo] password for christopher: 
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb


Sooo, what am I doing wrong?
I am a newbie to Linux and Ubuntu, so I do not fully understand how things work, especially with the terminal.
Is there another way I can install the thing other than manually installing every deb file, because I tried that, some of them refuse to install?

---

### Post by dino99 on 2010-06-11
all you need is to use synaptic packages

---

### Post by darkmire on 2010-06-11
> **Tombgeek said:**
> Hey guys.

I have a small little problem. I recently removed OpenOffice.org 3.2.0 from Ubuntu 10.04 and downloaded the OO.o3.2.1 debs from the site. All fine and well, I got a 139mb file and I unzipped it to my desktop, until I tried to install it. 
49 deb files!
No problem, just search Google and use the terminal, right?
[IMG]http://www.zippoc.com/blog/wp-content/uploads/2007/02/lex-luthor-wrong1.jpg[/IMG]

It was suggested that I use this tutorial, but the terminal gives me an error.
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)




I already unzipped the file to my desktop, and I got a file called "OOO320_m18_native_packed-1_en-GB.9502."

Using the terminal, I get an error saything the file does not exist.



Sooo, what am I doing wrong?
I am a newbie to Linux and Ubuntu, so I do not fully understand how things work, especially with the terminal.
Is there another way I can install the thing other than manually installing every deb file, because I tried that, some of them refuse to install?



Hi

As you're a newbie to Ubuntu I think I'd say that this isn't quite the best way of going about getting Open Office 3.2.1.   Actually, I understand that this version is only a bugfix and 3.2.0 that comes with 10.04 shouldn't give you any problems.  To get 3.2.0 then go on to Synaptic Package Manager and install it.   It will be quick and painless.

If you really do want 3.2.1, there is a repository that has it in at [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

Follow the instructions to get it.   The ppa will be added to your repository list so it will then automatically update for all updates and newer versions of Open Office as they come out, so it will keep OO up to date quicker than Ubuntu releases.

Installing software in Ubuntu should be much easier than in Windows - it's just a matter of knowing how.   This link should take you to the info pages which should help  [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

Mark

---

### Post by Tombgeek on 2010-06-11
> **darkmire said:**
> Hi

As you're a newbie to Ubuntu I think I'd say that this isn't quite the best way of going about getting Open Office 3.2.1.   Actually, I understand that this version is only a bugfix and 3.2.0 that comes with 10.04 shouldn't give you any problems.  To get 3.2.0 then go on to Synaptic Package Manager and install it.   It will be quick and painless.

If you really do want 3.2.1, there is a repository that has it in at [https://launchpad.net/~openoffice-pkgs/+archive/ppa]("https://launchpad.net/%7Eopenoffice-pkgs/+archive/ppa")

Follow the instructions to get it.   The ppa will be added to your repository list so it will then automatically update for all updates and newer versions of Open Office as they come out, so it will keep OO up to date quicker than Ubuntu releases.

Installing software in Ubuntu should be much easier than in Windows - it's just a matter of knowing how.   This link should take you to the info pages which should help  [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

Mark

Hey thanks.

I found a video on YouTube that helped me out (the user actually provided the right commands that actually worked!).
So it is fine, I got OpenOffice 3.2.1 to work now.
The reason I upgraded was because 3.2.0 took too long to open a file. It took a split second to open up the program, but an actual file, probably 25 seconds.
I am a bit disappointed with 3.2.1 because it is still slow, but at least it loads files quicker than 3.2.0.

---

### Post by Hagar Delest on 2010-06-11
I can't see why you couldn't get it to work with the command line! Have you tried the autocompletion feature of the terminal? Basically, for a folder not found error, it means that there is a mistake in the file name given.

Note that the PPA version can have problems (it has had such big troubles at the beginning of 3.0 for example). Command line is not that difficult once you understand what you're doing.

You can also open a terminal directly in the folder from the file browser: select the folder and hit F4. Then you just have to type the dpkg command line (and then cd to the desktop-integration subfolder).

---

### Post by tractor on 2010-06-12
Most likely the problem you had with not get the file to work properly in the terminal was that the rpm version and not the deb version was downloaded and extracted. If you follow the instructions here, OO 3.2.1 will download and install fine.

---

### Post by tractor on 2010-06-12
Oops!!!!!!! Here are the instructions. Sorry!!!!!!!!
[http://ubuntuforums.org/showthread.php?p=9410791](http://ubuntuforums.org/showthread.php?p=9410791)

---

