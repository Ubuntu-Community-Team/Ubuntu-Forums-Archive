---
title: "Ubuntu 14.04 display does not work anymore after normal package upgrade"
date: 2015-01-26
forum: Installation &amp; Upgrades
---

### Post by erotavlas on 2015-01-26
Hi all,

I have a strange problem. Today, I normally started Ubuntu 14.04.1 64 bit and I updated the packages (they were few since I update the system at least every 2 days). Then, I rebooted the system and now I'm not able to login any more. Moreover, if I start the system I cannot see the login screen whereas if I start the system in recovery mode by pressing resume I can reach the login screen, but the system freeze after the login screen.
I tried to fix the package dpkg without success since seem that the PC is not properly connected to Internet, but it has the same configuration of yesterday...
What can I do? I work with my PC.
Thank you

P.S.
I forgot to say that I'm using old gnome session with session fallback packages and I have nvidia geforce 720m with proprietary nvidia driver installed.

P.S.2 
I launched a live xubuntu in order to try to recover my ubuntu. I can mount my system drive, but I cannot access to home partition even if I do not use any encryption. Can this be the source of the problem or it is normal?

---

### Post by Bashing-om on 2015-01-26
erotavlas; Hi !

Maybe what we have here is 2, now unrelated, problems.
1) broken propietary graphics driver
2) Loss of authorization to access X or your /home directory.

Let's address the 2nd, and see if we can gain access to the GUI.
Try booting to TTY1 from grub's boot menu.
Boot the system and as soon as the bios screen clears, depress and hold the right -shift- key -> grub boot menu;
With the latest ubuntu kernel selected in the boot menu press the 'e' key for edit mode -> boot parameters screen;
In the parameters screen arrow down to the line stating with "linux" arrow over to "quiet splash" and replace these with the term "text" - without the quotes;
Key combo ctl+x to continue the boot process to TTY.

Log in here with your username and password - there is no response to the screen when pass word is entered .. enter pass word blindly and hit the enter  key .
OK, now who owns these :
```

ls -al .Xauthority
ls -al .ICEauthority
ls -al /home
ls -al /home/erotavlas

```
Example:
```

sysop@1404mini:~$ ls -al .Xauthority
-rw------- 1 sysop sysop 209 Aug  1 10:10 .Xauthority
sysop@1404mini:~$ 

sysop@1404mini:~$ ls -al .ICEauthority
-rw------- 1 sysop sysop 326 Jan 26 11:26 .ICEauthority
sysop@1404mini:~$

sysop@1404mini:~$ ls -al /home
total 28
drwxr-xr-x  4 root  root   4096 May 19  2013 .
drwxr-xr-x 25 root  root   4096 Jan 12 20:21 ..
drwx------  2 root  root  16384 May 19  2013 lost+found
drwxr-xr-x 29 sysop sysop  4096 Jan 26 11:26 sysop
sysop@1404mini:~$ 

sysop@1404mini:~$ ls -al /home/sysop
total 4572
drwxr-xr-x 29 sysop sysop    4096 Jan 26 11:26 .
drwxr-xr-x  4 root  root     4096 May 19  2013 ..
drwx------  2 sysop sysop    4096 Sep 13 22:43 #133454 • Fedora Project Pastebin_files
-rw-r-----  1 sysop sysop   11389 Sep 13 22:43 #133454 • Fedora Project Pastebin.html
drwx------  2 sysop sysop    4096 May  7  2014 .aptitude
-rw-------  1 sysop sysop   37495 Jan 25 23:07 .bash_history
-rw-r--r--  1 sysop sysop     309 Jul  8  2013 .bash_logout
<snip>

```
Where my username is 'sysop' .. are "you" grouped and the owner of your files ?

Once we have the GUI accessable, we focus on getting the graphics driver (re-)installed . - that is what I think -

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by erotavlas on 2015-01-27
Hi Bashing-om,

thank you very much for your help. With your suggestion about boot parameters I was able to login in my system and to remove nvidia drivers by typing:
```
sudo apt-get remove nvidia*
```

Now, the system is working properly with open source driver. Moreover, I experimented that the battery life is one hour longer with respect to the case with proprietary nvidia driver.
Fortunately, I'm able to access the home folder again: probably because it is located in different partition and the liveCD was not able to correctly recognize it.

Thank you again :=)

---

### Post by Bashing-om on 2015-01-27
erotavlas; Outstanding .

Pleased to be of some small help.

[INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT]

---

### Post by erotavlas on 2015-01-28
> **Bashing-om said:**
> erotavlas; Outstanding .

Pleased to be of some small help.
[INDENT][INDENT]all for 1 and one for all
[/INDENT]
[/INDENT]


You are right this is the spirit of open source and social collaboration.

---

