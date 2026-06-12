---
title: "System requirements??"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by xeddog on 2008-05-07
I have an old computer onto which I am trying to install a version of *ubuntu.  I have selected "all variants" because I have the same problem with Ubuntu 8.04 LTS, Mythbuntu 8.04, and kubuntu 8.04 (with KDE4) and with all of them I have the exact same problem  I think the problem is hardware incompatability but I am no expert so I thought I would ask here.

This is what happens.  When I boot from the cd, I get the kernel loading message, and that appears to complete.  Then I get the *buntu logo with the bar that goes back and forth for a few seconds.  Then the screen goes to black and two lines of text  and a prompt appear.  They read:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)

This happens regardless of the option I select after the cd gets booted.  Install without changing . . ., Install, even just checking the validity of the cd, and with all versions mentioned above.

So here is my hardware:
Older Tyan Tiger dual processor motherboard
two 800 Mhz Pentium III cpu's
768MB ram
one 60GB and one 30GB IDE disk drive
Riva TNT2 pro64 graphics card
Soundblaster pci128 sound card
one 3Com Etherlink ethernet card

One last thing.  I know all the hardware works because I can run Windows XP and Windows Vista on the machine.

Any ideas??

Thanks,

Wayne

---

### Post by pytheas22 on 2008-05-07
Actually your hardware doesn't seem as low-end to me as you might think (processors are slow but you have two of them, and a good amount of memory); it should be able to run Linux without a problem.

I'm not sure what the problem could be, but one more thing to try would be to install using the alternate install CD instead of the Live CD--go to [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download) , select the appropriate options but make sure you check the box that says "Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer."  Then burn this CD and try to use it to install.  The Live CD uses a weird hybridized kernel and does some other special stuff that might be causing the problem.  The alternate install is ugly but no more difficult than its graphical counterpart.

---

### Post by wpshooter on 2008-05-07
Are you checking the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

---

### Post by Slim Odds on 2008-05-07
As I've mentioned in quite a few posts, Hardy run fine on an old 800MHz P-III with 384M RAM. So your machine should be fine.

---

### Post by xeddog on 2008-05-07
Before starting my update, I AM booting up the *buntu cd's and using the check disk for errors option on the *buntu menu.  But as I said earlier, even that has to be done on another machine.

I've done some more testing but things still are not working.  I have downloaded kubuntu 8.04 (with KDE4) alternate and have tried installing it.  Using the alternate cd the install goes as far as checking hardware, and selecting the keyboard.  Then it starts loading but stops at about 8% with a message that it can no longer read the cd.  

The machine had an old dvd reader installed (it also reads cd's) so I swapped it out with a wroking cd drive from another machine.  I am certain that the replacement cd drive works properly because I used it to install Vista, XP, and Hardy on another machine.  

The machine I put the old dvd reader into doesn't have any problems with it and I can check the cd's for errors.  I can also boot the LiveCD's.  

So all that means that there is something quirky about that particular machine.  I'll do a little more testing.

Wayne

---

### Post by byte69 on 2008-05-08
Your not the only one.   I am trying to install it on a HP DC5750 with a 80GB drive with Windows XP, a Dual Layer DVD-rw drive and a 500GB drive.   All are sata and I get to the same spot. I also have tried every option I know and it just stops at the same place as yours does.   I also tried stipping the system down to just the 500GB drive.   I have run out of ideas.   The system has AMD64 X2 4400+ processor and 1GB of ram.   

Any ideas???   I have been running Ubuntu since 5.05 and have dug some holes but never seen this.

Here are the system specs:

 Athlon 64 X2 4400+; 1GB RAM; integrated ATI Radeon X1150; 80GB hard disk; DVD-ROM 16x drive; I added a 500GB Hard disk, Integrated Realtek AC'97 Audio

I am working on another attempt to install by use a 6.06 64bit cd.   Then try an upgrade from there.

---

### Post by pytheas22 on 2008-05-08
Maybe another strategy would be to try a different distribution or an earlier version of Ubuntu.  This would help isolate the problem.

EDIT: or, another approach, if you have Windows on the machine, would be using wubi, [http://wubi-installer.org/](http://wubi-installer.org/) .  This would allow you to avoid all the problems of the live CD.

---

### Post by xeddog on 2008-05-08
I think I have found my problem, much to my dismay.  I think the secondary IDE bus on the motherboard is knackered.  I removed everything from the computer except the 60GB disk, a known good cd drive, and the video card.  I also replaced the ribbon cable for the secondary IDE with a brand new cable, and I still had the same problem.  On a whim, I moved the cd drive to primary IDE bus (as primary slave) and the installation proceeded without a hitch.  I even did a re-install using the original dvd reader and it worked too.

Oh well.  I guess I can still use this system for it's intended purpose.  That being to try out kubuntu with the KDE4 desktop.  Don't really need any more IDE devices to do that.  Maybe if I need more IDE devices I can get a cheap expansion card.

Wayne

---

### Post by wpshooter on 2008-05-08
> **xeddog said:**
> I think I have found my problem, much to my dismay.  I think the secondary IDE bus on the motherboard is knackered.  I removed everything from the computer except the 60GB disk, a known good cd drive, and the video card.  I also replaced the ribbon cable for the secondary IDE with a brand new cable, and I still had the same problem.  On a whim, I moved the cd drive to primary IDE bus (as primary slave) and the installation proceeded without a hitch.  I even did a re-install using the original dvd reader and it worked too.

Oh well.  I guess I can still use this system for it's intended purpose.  That being to try out kubuntu with the KDE4 desktop.  Don't really need any more IDE devices to do that.  Maybe if I need more IDE devices I can get a cheap expansion card.

Wayne

I read this very quickly, so are you sure that the secondary IDE controller has not gotten disabled in BIOS somehow ?

Also, when you had the CD drive on the secondary controller, did you have it jumped as MASTER and not slave ?

---

### Post by xeddog on 2008-05-19
wpshooter - 

Sorry for taking so long to respond, but I'm sure that the bus had NOT been disabled.  I checked everything I could think of in the bios and it was all the same as the Primary IDE.  Also, if it had been disabled, I would not even be able to have started an install, much less have it fail.

xeddog

---

