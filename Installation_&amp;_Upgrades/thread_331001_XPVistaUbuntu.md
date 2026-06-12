---
title: "XP/Vista/Ubuntu"
date: 2007-01-03
forum: Installation &amp; Upgrades
---

### Post by Chip17 on 2007-01-03
Hello Everyone!  Im new to ubuntu and want to set up my laptop in a triple boot environment with XP, Vista and ubuntu.  I currently have my laptop harddrive configured with three partitions.  The first partition has 40gig for xp, the next partition has 30gig for Vista, and the rest is for ubuntu and is 24gig in size.  Ive read the forum and feel that these three partitions are large enough to utilize XP, play with Vista and start the transition to ubuntu for a while.  My question is this:  I have XP installed and am waiting on Vista.  I want to load ubuntu now along with XP.  If I load ubuntu now and wait for vista am I going to have problems loading vista after having ubuntu installed?

Any help from you smart ubuntu guys would be appreciated.  Im new to all this and want to do the right thing.

---

### Post by quartzy on 2007-01-04
> **Chip17 said:**
> If I load ubuntu now and wait for vista am I going to have problems loading vista after having ubuntu installed?

I don't really know how vista handles boot managing, but if it's anything like XP the easiest option will be to have ubuntu handle the boot sector.  This means your problem is backwards to what you implied, if you install ubuntu then vista you will have to 'recover' ubuntu and rewrite the boot sector.  I would suggest installing ubuntu last if you can wait and don't want to mess around.

But that's just me :)

---

### Post by dlehman on 2007-01-04
Well I am no expert, but If you install ubuntu now and vista later your will have to reinstall grub and make sure a menu option gets put in your menu.lst file

In my experience it is better to load windows first then ubuntu because windows does not like to play nice and will overwrite your mbr with its info 

ubuntu auto detected that I had XP and made a menu entry for it when I installed but if you install vista latter I don't know how that will work out

My advice is be careful win installing pay close attention to what partition you are installing on and BACKUP BACKUP BACKUP 


good luck and welcome to ubuntu 

p. s. BACKUP your partition table

---

### Post by Chip17 on 2007-01-04
Thanks!!!  I thought that I would get the "wait and load Ubuntu after Vista" answer.  But, I like Ubuntu to much to wait.  Besides I was just gonna play around a little with Vista.  Im not really sure that I want to invest any time or dollars in Vista when I have Ubuntu.  I may not even load it.  The only reason that I am looking at is that I get it free as an upgrade since I purchased my new laptop after October - else I wouldnt even bother!!!!

Thanks again!!!  This forum and the Ubuntu Community are first class!

---

### Post by Neobuntu on 2007-01-04
I wish you well with your tri-boot. While it's more to keep up with, experimenting and comparisons can be done in a minutes reboot. 

1. Yes, Windows is stupid. It can't admit anything else exists or that one might want to use (or be using) GRUB. Messing with "boot.ini" (in XP) is trouble. Microsoft hopes for the stupidity of users and does not believe we can get the word out and explain it in layman's terms. I do. To keep things simple, when you get Vista, install it First and then re-install *Ubuntu. You may want to image XP and lay it down on (non-vista first) partition while setting GRUB to call it. Remember, GRUB keeps it's (secondary) files in your Ubuntu /boot directory (normally.) DO NOT MANUALLY REINSTALL GRUB and mistakenly write over the first part of one of your partitions. Only the "root (hd0,2)" command should use the two numbers. "setup (hd0)" is for the (separate from partitions) MBR and NOT two numbers, or you'll write over your OS's startup files. If you use Ubuntu to install GRUB automatically, you will NOT have to think about this.

2. You know, your Vista is indeed not free at all. You paid for it already. I know they make it easy but we really should think before feeding the Microsoft. Even if Windows was made completely free to you at purchase, we pay the Microsoft price one way, or another.

If one wants singular KISS simplicity, just use Kubuntu (with over 256MB RAM). This is why I say open software must do every real benefit of Windows and then some. Most people will be happier with TODAYS Kubuntu, and *ubuntu improves the fastest.

---

