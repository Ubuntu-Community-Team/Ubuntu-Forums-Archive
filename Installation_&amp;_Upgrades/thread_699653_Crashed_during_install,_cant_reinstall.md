---
title: "Crashed during install, cant reinstall?"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by anglico on 2008-02-17
I tried installing Ubuntu 7.10 onto an older computer, over XP Pro, needless to say it didnt do too well. It got to the installation screen ( I think step 8 ) and then when it said it was installing it sat for hours without doing anything. So the system is hosed I think as of now, I cant access the old Win XP Pro but I CAN get a prompt in linux.
 My question is how do I install the XUbuntu desktop from a CD (That it wont boot from) when all I have is this prompt:

Busybox ver 1.1.3 (debian etc...)

(initramfs)_

 All I know is that it has 192MB of ram when it boots, it gives me an option to go to WinXP or Ubuntu, if I choose WinXP I get the BSOD (Obviously) and when I reboot and select Ubuntu, I have an option: Normal mode or graphics safe mode, either one I choose I get some text (gate a20 I think) then it gives me a colorful Ubuntu progress bar while accessing the CD drive. 

EDIT: I noticed it said my BIOS failed the cutoff of 2000, its 1999, CAN I even install any of these versions?

Then an acpi something and an error at the same time mentioning something about forced mode and then the prompt shown above. 

 What am I looking for? 
	How do I get this to install the xubuntu from the CD since apparently my machine isnt strong enough for the full ubuntu install. 

 What have I tried: 
 	inserting the ubuntu live CD and trying to boot from it 
	inserting the xubuntu desktop CD and restarting to try and boot from THAT one

My computer's boot order is CD, HDD, floppy

Thank you for any help.

---

### Post by Pumalite on 2008-02-17
With that RAM, you should try this:
[http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)
(Alternate)

---

### Post by anglico on 2008-02-17
I have that already and have inserted it into the cd drive and restarted. when I choose ubuntu, it accesses the xubuntu cd for a little while then it gives me the prompt mentioned in the original post. I was wondering what should I do to get it to install xubunu (alternate), forgive me, truly forgive me for what Im about to say:
 In a windows system I would type:

 e:\install.exe and let it install, so what is the equivilant of this in linux to get this to go to the cd drive and let me install xubuntu over everything else (Ubuntu and any win xp pro left)

thank you

---

### Post by wpshooter on 2008-02-17
> **anglico said:**
> I have that already and have inserted it into the cd drive and restarted. when I choose ubuntu, it accesses the xubuntu cd for a little while then it gives me the prompt mentioned in the original post. I was wondering what should I do to get it to install xubunu (alternate), forgive me, truly forgive me for what Im about to say:
 In a windows system I would type:

 e:\install.exe and let it install, so what is the equivilant of this in linux to get this to go to the cd drive and let me install xubuntu over everything else (Ubuntu and any win xp pro left)

thank you

First make sure that you have checked the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu.

Then go to [www.killdisk.com](www.killdisk.com) and download killdisk and use it to **WIPE** the hard drive of the computer that you are trying to install Ubuntu on **COMPLETELY CLEAN** and THEN go back to the Alternate Ubuntu CD and try the installation again.

Good luck.

---

### Post by anglico on 2008-02-17
thank you, I ran it from CD and wiped the drive. Unfortunately when I restart with any cd in the drive it doesnt access it long enough to boot from the CD. It reads the cd drive first because when I put in the killdisk cd it opens up killdisk. I can see it access the cd drive when booting but it is so quick that it goes to the floppy drive then the hdd and then just fails out with "error loading operating system " and then just sits there. So thank you but it looks like all I can do is try reinstalling windows then try to install the xubuntu alternate as dual boot.

---

### Post by Pumalite on 2008-02-17
Make sure CD-Drive is first in the boot order in BIOS.

---

### Post by wpshooter on 2008-02-18
If you have WIPED the hard drive completely clean and if you have the CD as the first boot device for the machine and unless there is some MAJOR physical damage to either the ALTERNATE CD and/or to your CD drive itself, then the computer in all likelyhood should boot up to the initial boot menu of the ALTERNATE Ubuntu CD, where you can then check the integrity of the CD by running the verify function that is found on the initial Ubuntu boot screen menu.

Good luck.

---

### Post by anglico on 2008-02-18
So to test whether the xubuntu's I had (desktop, Alternate) were indeed corrupted, I stuck in the Ubuntu Live CD on a system that kept telling me OS not found. The live CD popped up, ran through an 'installation' and is now functional. 

 What I am wondering is if I can pop out this Ubuntu Live CD and then put in one of my Xubuntu CD's and try to install Xubuntu that way. As I understand the Ubuntu Live CD only lets you run it from the CD, so hence taking it out will screw things up. If I am wrong great, Im more than happy to pop in the Xubuntu desktop and try that installation.
 Another thing Im wondering about is why is it running the Live CD without a problem, a little slow, but wouldnt install Ubuntu 7.10 desktop. Could it have been a fluke and I should try installing Ubuntu again?

 Just in case I am downloading another copy of xubuntu desktop.

By the way, thank you for all your help.

---

### Post by Pumalite on 2008-02-18
Good Luck. Don't forget to do md5sum on the iso, burn as image at 4x or less in good quality CD-R and check CD integrity before install.
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

