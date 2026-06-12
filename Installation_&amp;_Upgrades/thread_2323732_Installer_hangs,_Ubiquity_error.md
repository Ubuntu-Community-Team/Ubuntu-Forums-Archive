---
title: "Installer hangs, Ubiquity error"
date: 2016-05-07
forum: Installation &amp; Upgrades
---

### Post by Roger_Lipsett on 2016-05-07
I have posted this to the askUbuntu stackexchange site. Apologies if it's considered bad form to cross-post here; if that's the case, please tell me.

I have an HP Ultrabook 4 that currently contains some version of Windows (I think Windows 8), and I'm trying to completely replace it with Ubuntu 16.04 LTS. I have a bootable USB stick that runs fine on the machine. When I try to install from the stick, I eventually get to the Installation Type screen, which displays an empty partition list; the New Partition Table button is grayed out. If I press "+", either just crashes silently or I get a message about an internal error involving Ubiquity. Any suggestions?

Note that I do not get the screen that asks whether I want to install 16.04 alongside or instead of 14.04. The only installer screens I see are the one asking about the language, the next screen with questions about automatic updates and third party drivers, and then the Installation Type screen with an empty partition list. By the way, related or not, on the initial screen, when selecting a language, I don't get the graphics on the right side containing large buttons asking about live vs install (the buttons that are shown on the Ubuntu pages relating to installation) - that part of the window is just blank.

I have also tried the identical USB stick on another computer (an Ubuntu 14.04 LTS box), and it correctly gets to the missing Installation Type screen.  So I think perhaps there's something odd about either the HP box or the way its filesystem is configured that confuses the installer.

Screenshots of parted and lsblk of the HP filesystems are below: 
[https://i.stack.imgur.com/YnY2u.png](https://i.stack.imgur.com/YnY2u.png)
[https://i.stack.imgur.com/s4RMf.png](https://i.stack.imgur.com/s4RMf.png)[COLOR=#111111][FONT=Ubuntu][FONT=arial]
[/FONT]
[/FONT][/COLOR]

---

### Post by Dennis N on 2016-05-07
On the first "Installation Type" screen, can you select "Erase disk and Install Ubuntu"? Why not use that option?

---

### Post by Roger_Lipsett on 2016-05-07
That *is* the first Installation Type screen. The screens I see are the language selection screen, the screen about automatically installing updates, and the screen in question.

---

### Post by Dennis N on 2016-05-08
I am referring to the graphical Ubuntu installer. Please see the image on this guide under the section "InstallationType" to see the screen.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by Roger_Lipsett on 2016-05-08
> **Dennis N said:**
> I am referring to the graphical Ubuntu installer. Please see the image on this guide under the section "InstallationType" to see the screen.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

I am using the graphical installer. After clicking on Install Ubuntu, I see the following screens, in order:
[http://imgur.com/gX3l4bG](http://imgur.com/gX3l4bG)
[http://imgur.com/nhM8QlC](http://imgur.com/nhM8QlC)
[http://imgur.com/2ChrCLU](http://imgur.com/2ChrCLU)
[http://imgur.com/GZHcZYO](http://imgur.com/GZHcZYO)

---

### Post by Bucky Ball on 2016-05-09
In the last screen, click the 'Show Details' button and post the output there here, please.

---

### Post by Roger_Lipsett on 2016-05-10
> **Bucky Ball said:**
> In the last screen, click the 'Show Details' button and post the output there here, please.

See attached files
[http://imgur.com/ZymYLMd](http://imgur.com/ZymYLMd)
[http://imgur.com/UpSJIT4](http://imgur.com/UpSJIT4)

---

### Post by Roger_Lipsett on 2016-05-10
It looks from the bug report mentioned in the screen shots that I just posted (I kinda wish I'd looked at those before) that this is perhaps a RAID-related issue, and that if I simply erase the existing disk with dd or fdisk that things may go OK. Is that your reading of the situation as well?

---

### Post by Bucky Ball on 2016-05-10
I couldn't spot a reference to RAID in there, but that's not saying much. Either way, I know nothing much about RAID so can't advise on that, sorry. 

I'd imagine if you removed partitions and deleted the partition table it would remove all traces of anything (re. RAID), but again, no RAID guru. ;)

You might be able to find some facts on it with further digging.

---

### Post by Roger_Lipsett on 2016-05-11
If you look at the screen shots, one of the lines is DuplicateOf [https://bugs.launchpad.net/bugs/1064151](https://bugs.launchpad.net/bugs/1064151). This appears to refer to issues with RAID. But in any case, did you see anything in the screen shots that would lead me in a particular direction?

---

