---
title: "new user with installation problems"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by agraebner on 2010-11-07
my installation goes fine up to  (EE) VESA : Kernel mode setting driver in use, refusing to load              along with (EE) no devices detected.             I have been a long time windows user but after seeing many good words about ubuntu I decided to give it a try before taking the windows 7 dive on 4 pcs.     All my computers are home builds the one im trying the first install on is a pentium 4 on soyo P4I865PE Plus Dragon 2 board   HIS agp version of   HD 4670 video card.   any help would be greatly appreciated since i have NO knowledge of this operating system.   I am using wubi to install from a downloaded iso image im using version 10.4   the long term support version.   If i do the restart X option everything seems to come up fine but i would like to make sure everything's working correctly as I'm judging whether to use this on other computers.

---

### Post by P4man on 2010-11-07
You are not getting that error message *during* the install are you? I guess you mean you installed ubuntu, and you get that error when you boot it?

Have you installed the proprietary ATI drivers ?

Anyway, check my signature for possible cause and solution. However, Im not sure its exactly accurate for wubi, I havent used wubi in ages and I recommend strongly against it for anything but a quick trial (which might be the case here).

If you have installed the ATI drivers, you might want to try opening a terminal and typing

```
sudo aticonfig --initial
```

---

### Post by agraebner on 2010-11-08
well that problem was just the lack of ati software as you suspected.  It worked so much faster for what this machine is used for that i went ahead uninstalled wubi and started an actual installation of the same 10.4 version ubuntu,  heres where thing went really bad.  It made it to the point where you select the partition to install to and started copying files then had a fatal error with no warning and rebooted.  now i cant get anything to load and bios apears corrupted.  i cant even change settings in bios now it wont save any changes.  I cant find the exact file i need to reflash my bios so i had a new bios chip flashed and its in the mail.  As soon as i get the bios in and running again ill try again.  If anyone has any theries or warnings about what happened here i would love to know before i risk the new bios chip.

---

### Post by P4man on 2010-11-08
Wow. Thats not good lol. Theory? Well, the machine is old, the mainboard battery maybe depleted and corrupted the bios settings? If thats what happened, you dont need a new bios chip, all you need is resetting the bios, usually shorting a jumper on the motherboard.

---

### Post by agraebner on 2010-11-08
Ive replaced battery about 6 months ago.  Ive had bios problems off and on since i built this machine when the prescot first came out.  this board was supposed to support springdale processors with the origonal bios and prescot through a bios update .  Ive never bothered to do anything about it cause ive never been able to find the file that i needed to flash it right.  For most internet surfing and media its works great so I decideed to keep the old girl around for a few more years.  I figured that it wasnt worth messing with since windows worked ok 99% of the time.  I have a new machine thats 99% complete amd 6 core black edition  and 2 xfx hd5970 video cards with ssd raid for boot and 2 WD  1TB raid 0 hard drive for eveything else and that is set to back up to a 2 tb green drive automatically for security.  all im waiting for is money for the best ram i can throw in it since i dont want to limit the machine by that.  I already have a win 7 64 bit to install as soon as i get memory.  will ther be any point in installing ubuntu in a dual boot on the new one???????   main reason im going to ubuntu is its so much simpler and does everything I need faster  for basic use and business.(from what ive seen so far playing with wubi on the p4 machine and my amd laptop.  I am going to put a new larger drive in my laptop and do the dual boot on there as well.  and keep the old drive intact just in case somthing goes wrong.  the whole grub thing confuses me with what it puts in which place.  I am used to windows logic or lack of it depending on your perspective.  Info is very plentiful about ubuntu but there a lot of contradiction in info forums.  i really like the layout and feel of ii so im am just hlding my breath that it will work for me.

---

