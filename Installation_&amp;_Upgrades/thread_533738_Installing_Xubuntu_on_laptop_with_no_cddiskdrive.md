---
title: "Installing Xubuntu on laptop with no cd/diskdrive"
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by sirasgeirr on 2007-08-24
Hello!

Iim very new to linux and have just tried it out quickly, recently I got my hands on a fairly old laptop. Its a Toshiba Portege 2000 and its a very small and light computer but it is a couple of years old, so i thought Xubuntu would be good for it.

Now, the problem is i cant find any means to install  linuxt, it already has win xp installed but id like to do a clean install of linux.

It has the possibility to boot from HD, Network  PCMIA card CD or Diskdrive (USB is not possible, plus its only got USB 1.0 ports) but the problem is i neither have a Diskdrive, CD or PCMIA card for it. After Googling the subject the only solution ive found so far is this link [http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html) but its seems a little bit to complicated for me :( Ive also found some sugestions to ppl in similair situationsthat they should remove the HD and put it in another computer and from there install it, but i fail to see how that would work since it will have a completly different hardware setup, I also own another laptop so that would probably be possible though.

I know that to install windows in this way. It would be to install dos on the HD using another computer and then copy /i386 to the c: and then run the install from there. Is there perhaps a similair way to do it with linux?

Ive also checked out wubi but thats not an option since its a "fake" install from what i understand

sirasgeirr

---

### Post by Pumalite on 2007-08-24
What you need is a net install: [http://www.wrigley.me.uk/wp/?p=71](http://www.wrigley.me.uk/wp/?p=71)
[http://ubuntuforums.org/archive/index.php/t-2068.html](http://ubuntuforums.org/archive/index.php/t-2068.html)
Here you have one from winblows: [https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

---

### Post by sirasgeirr on 2007-08-24
Thanks for the quick answer, im gonna check it out and see how it goes :)

---

### Post by tahnok on 2007-08-24
You could use wubi and then move the virtual disk to it's own partition using LVPM
[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)
It's kind of tricky because you've got to repartition the drive a bit, but you don't need a CD drive just an internet connection.

---

### Post by sirasgeirr on 2007-08-26
Ok, ive been a little busy last days but today i finally sat down and tried to fix this install, I was going to try Tahnoks method first by partitioning the drive and then move the wubi install to that partition, because it seemed easier and if it fails i can always try the network install.

But I havent managed to get very far :( I cant seem to get the partition manager to work, It loads up ok untill i have to choose my resolution and color depth, then i get this message.

xuath:  creating new authority fle /root/serverauth.3549
(WW) Could not open RGB file "/usr/X11R6/lib/X11/rgb.txt; Will use built-in copy.

And then it just stops there, and it doesnt continue.I've checked the Gparted forums but i cant seem to find any solution and neither on google, so I would appriciate if someone could help out :)

---

### Post by tahnok on 2007-08-26
That's really odd, I have no idea what the means. Sorry I can't be of any help.

---

### Post by cmjones222 on 2007-08-27
I did mine, I got lucky I had an old Dell L400, I have no CD, and it had only 98, and could not use a memory stick. I had to take the HD and put it into another pc that had cd, (Dell Also), move the UBUNTU file to the DESKTOP and put the HD back into the PC and Install it from there. You can not use the CD ISO copy, you have to use the UBUNTU 6.06 copy I located on the net, I cant recall where. 

Also I did try to install ubuntu on the other PC first, and then put it in the OTHER PC I wanted it in, and it just froze, it never loaded, that why I had to do it the other way.. 

GOOD Luck 

CJ

---

