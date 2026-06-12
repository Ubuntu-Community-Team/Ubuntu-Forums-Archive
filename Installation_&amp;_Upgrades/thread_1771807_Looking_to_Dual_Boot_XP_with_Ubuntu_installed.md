---
title: "Looking to Dual Boot XP with Ubuntu installed"
date: 2011-05-30
forum: Installation &amp; Upgrades
---

### Post by royalflush5 on 2011-05-30
Hey everybody, I finally made the jump to Ubuntu when I built my PC. and I really love it so far. Obviously, some Windows programs just wont run and my virtual machine just wont cut it because I need more resources. So, i want to dual boot Ubuntu 11.04 along with Xp (obviously) and i have a couple of questions:


[LIST=1]
[*]I have a 64 bit processor, so will Xp even work?
[*]Natty is my primary OS and I have a second HDD that i plan to install Xp on, how would I be able to select which OS to boot at startup?
[*]is there anything else I should know?
[/LIST]
I am a super noob with this stuff, and any help would be greatly appreciated, I've searched around but I haven't found what I was looking for.

Thanks!

---

### Post by David D. on 2011-05-30
1.  XP should run on a 64-bit processor.

2.  Windows tends to not recognize other OS's when installing and takes over the system.  Normally one would install Windows first, then Ubuntu (which will recognize that you already have windows installed).  In your case, you should remove the HHD with Natty, then install Windows XP on the remaining drive.  Reinstall the Natty drive.  

3.  A reboot will then either take you into Natty, or into XP. 
 
If into Natty, then run in terminal (CONT-ALT-T to open) ```
sudo update-grub
```to let grub find XP.  You will then have boot options for Natty or XP when you boot.

If into XP, do a search in these forums for reinstalling grub from a live CD (your Natty install disc will work)and follow the instructions for installing grub onto the Natty HHD.

I am sure that someone will correct me if I am mistaken with something.  This is a very knowledgeable and helpful group.

Welcome to Ubuntu and the forums.

---

### Post by oldfred on 2011-05-30
When you install XP it will think it is sda or drive 0 and have that in its boot.ini. I would then make sure when you reinstall the Ubuntu drive you make Ubuntu sdb. It will probably depend on which ports you plug which drive into. The in BIOS set to boot the Ubuntu drive. Windows does not like drive changes, Ubuntu boots with UUIDs as defaults and will work even if drive changes.

XP may not have SATA drivers and does not have AHCI drivers by default. My XP worked with SATA without problems.  It is a bit easier if you install those as part of the install. I tried changing my new motherboard to AHCI and Ubuntu still booted, but XP would not work, so I am in IDE mode to allow booting XP. Supposedly only a minor disadvantage.

---

### Post by royalflush5 on 2011-05-30
Wow, thank you for all the help guys :)

I'm going to install Xp tomorrow and see what happens, if I boot into Xp, would it be possible to just select my Natty HDD from the boot manager at startup, boot into Ubuntu, and do sudo update-grub? Or is there a different set of commands I need to type?

Thanks again :P

---

### Post by oldfred on 2011-05-30
If you have the Natty grub2 bootloader in the Natty drive all you should have to do is this to add XP to menu:

sudo update-grub

---

### Post by royalflush5 on 2011-05-31
Wow, I got it! Thank you guys so much for the help, this is fantastic! :) :) :)
I'm going to assume Memtest is part of the Ubuntu install?

Thanks so much again!

---

