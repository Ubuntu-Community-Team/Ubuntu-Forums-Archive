---
title: "2 Linux?"
date: 2005-02-08
forum: Installation &amp; Upgrades
---

### Post by D4_B34M on 2005-02-08
I have installed Mandrake linux 10 and Windows XP on my computer
I also have one empty part on my hdb ( ~9g ) without format.

Can i install Ubuntu to that partition and keep Mandrake and XP working?

I have Mandrake Linux in ReiserFS ( /usr in hdb ) and rest in hda also in reiser..
Ive got a swap in hdb and NTFS on both hd's but xp installed on hda.
And.. in hda i got LiLo

If its possible should ubuntu be able to read files from an folder in my mandrake partition (i set RW rights).

And how much the normal install of ubuntu needs diskspace?

---

### Post by DJ_Max on 2005-02-08
You shouldn't have a problem with anything. Ubuntu, or any POSIX os can read other filesystems, you just have to mount it, normally.

---

### Post by D4_B34M on 2005-02-09
[QUOTE=DJ_Max]You shouldn't have a problem with anything. Ubuntu, or any POSIX os can read other filesystems, you just have to mount it, normally.[/QUOTE]


Yeah but does my mandrake keep still working?

---

### Post by Hezekiah on 2005-02-09
You can have Ubuntu, Mandrake and WinXP/2k/etc working together on one system.  I have had Ubuntu Warty, Mandrake 10.1 and Win2k all setup on different partitions on my harddrive in the past.  Just make sure you're careful when selecting partitions during the Ubuntu install :-)

The only significant roadblock that I have found is getting your bootloader, either LILO or grub to properly recognize both Linux distros.  grub seems to be a little easier to configure for this, but either way it will take some tweaking.

I don't remember the details on how to do this though.  The man pages for lilo/grub will be helpful in figuring it out.  Also, Mandrake's 1st install cd will let you reinstall the Mandrake bootloader from its recovery console.  So even if you do have trouble, this is a way to restore your boot settings.

---

### Post by Joeb on 2005-02-09
[QUOTE=D4_B34M]Yeah but does my mandrake keep still working?[/QUOTE]

The short answer is yes.  But, you will need to decide if you want to use Mandrake's pretty graphical LILO boot loader or Ubuntu's plain looking text based Grub.  Both have their advantages and disadvantages.

If you want lilo, then you should tell Ubuntu to not install the boot loader.  After Ubuntu is installed, then you would need to boot into Mandrake and manually add the information to /etc/lilo.conf, rerun lilo and then reboot (you only need to do this once).  After that, you should be able to select Ubuntu from the lilo screen.

If you use Ubuntu's grub, it may or may not pick up your mandrake installation.  If it doesn't, then you will need to add the Mandrake info to your grub configuration file in ubuntu.

Check out man lilo or man grub for more info.

---

### Post by crane on 2005-02-09
I have a test system that is multyboot also. (CentOS, Blag, Ubuntu, and Mandrake) Like stated earlier Just do some good reading on setting up boot loader and you should be fine. :grin:

---

