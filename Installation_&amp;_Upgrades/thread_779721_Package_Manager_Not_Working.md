---
title: "Package Manager Not Working"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by jim8433 on 2008-05-02
I thought I had a clean install until today.  I try to startup Synaptic Package Manager and get whirling icon followed by nothing. I get the same result for several Administration menu items.  I would appreciate help getting problem fixed. 

Thanks

---

### Post by scragar on 2008-05-02
lanch a terminal, try the command(s) in the terminal, and let us know the output```
gksu /usr/sbin/synaptic
```

---

### Post by sickenmcsluggets on 2008-05-02
Yeah, I can't get mine to work either. When I try starting it up I get the "Starting Administrative Application" box in my window selector, but then nothing happens. Ugh.

---

### Post by sickenmcsluggets on 2008-05-02
> **scragar said:**
> lanch a terminal, try the command(s) in the terminal, and let us know the output```
gksu /usr/sbin/synaptic
```

Tried that, and it does the same thing

---

### Post by scragar on 2008-05-02
firstly don't double post, and secondly what's the terminals output? any errors, messages etc?

---

### Post by dakotadare2b on 2008-05-03
I'm experiencing the same as the previous two posters. Using both the Synaptic Package Manager, the Add/Remove, or the terminal with "gksu /usr/sbin/synaptic" results in only a short-term display of the process starting and then the process quits; with no results and no errors. I have a fresh install of 8.04 Hardy.

Thanks in advance.

---

### Post by ChameleonDave on 2008-05-03
If you try to install something from the command line (without Synaptic), does it work?

For example, you could type:

```
sudo apt-get install synaptic
```

to install Synaptic itself.

---

### Post by dakotadare2b on 2008-05-03
Okay, I've resolved my issue. Thanks to ChameleonDave's suggestion to run sudo, I received an error in the terminal "sudo:unable to resolve host (hostname)". I found other posts regarding hostname issues after installing 8.04 Hardy, and once I resolved the hostname I an now able to use Synaptic Package Manager, The Update Manager & the Add/Remove Applications.

To check out the resolution for the hostname issue check out these posts:
[http://ubuntuforums.org/showthread.php?t=779589&highlight=unable+resolve+host](http://ubuntuforums.org/showthread.php?t=779589&highlight=unable+resolve+host)
[http://ubuntuforums.org/showthread.php?t=779034&highlight=unable+resolve+host](http://ubuntuforums.org/showthread.php?t=779034&highlight=unable+resolve+host)
[http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851)
[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

One of these will help.

---

### Post by sickenmcsluggets on 2008-05-03
> **scragar said:**
> firstly don't double post, and secondly what's the terminals output? any errors, messages etc?

Double-posting does not simply mean posting twice in a row. It was in response to your post. 
 
Oh and thanks Dakotadare2b, that was my problem as well. Solved.

---

### Post by dakotadare2b on 2008-05-03
> **sickenmcsluggets said:**
>  
 
Oh and thanks Dakotadare2b, that was my problem as well. Solved.

I'm glad it helped!! :)

---

### Post by anirudhphadke on 2009-02-21
Hi, I am a complete newbie, though have been using Ubuntu for a while now. For the last month or so, when I try Update Manager, it shows me this error:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/Ubuntu-Studio%208.10%20%5fIntrepid%20Ibex%5f%20-%20Release%20i386%20(20081028)_dists_intrepid_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'


So then from this thread, I tried the command: gksu /usr/sbin/synaptic

It gave this error:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/Ubuntu-Studio%208.10%20%5fIntrepid%20Ibex%5f%20-%20Release%20i386%20(20081028)_dists_intrepid_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Next, I tried this command with the following error:

anirudh@anirudh-laptop:~$ sudo apt-get install synaptic
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/Ubuntu-Studio%208.10%20%5fIntrepid%20Ibex%5f%20-%20Release%20i386%20(20081028)_dists_intrepid_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
anirudh@anirudh-laptop:~$ 

I assume that I don't know something very basic. Please help.

Thanks in advance!

Anirudh

---

### Post by Hrusther on 2011-05-05
Hey.
I have installed ubuntu today and i have to tell you that i know NOTHING about that os, i used windows 7 before (i have it now too). The problem is..when i want to ope syntapic package manager some wierd error pops up. I wanted to install utorrent and wow (world of warcraft) so i checked a few sites on google, well...i think i cant do anything without syntapic package manager.


This is the massage.
E: Type '--2011-05-05' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Thanks.

---

### Post by ssn116 on 2011-05-13
I have the same problem as user anirudhphadke two posts above. I get the same message when I try the gksu /usr/sbin/synaptic command, namely:
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
My Update Manager is also not working, for the same reason. 
I have used Synaptic Package Manager and Update Manager for this (11.04) install just a few days earlier.
Please help; thanks in advance.

---

