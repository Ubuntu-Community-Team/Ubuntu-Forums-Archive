---
title: "Boot on external drive using CD as bootloader"
date: 2017-10-14
forum: Installation &amp; Upgrades
---

### Post by piggeywig2000 on 2017-10-14
Hi, I'm really new to Ubuntu and I think I'm misunderstanding something.

So, I want to install it onto an external drive connected via esata. I found a very helpful tutorial [here]("https://askubuntu.com/questions/446682/how-to-install-ubuntu-on-portable-external-hard-drive") which shows you how to do that.

Now here's where I'm getting confused. In the tutorial it has it set up where every time you want to boot Ubuntu you need to boot with the usb stick plugged in which tells the computer to boot from the external hard drive. I want to instead use a CD which tells it it boot from the external hard drive. How would I go about doing that?

Would I burn the install iso to a usb stick, then in the partition manager thing during install set the bootinstaller to a blank CD?

I'm sorry if this is a dumb question, I'm just really confused as to how this works. Thanks.

---

### Post by oldfred on 2017-10-14
UEFI or BIOS?
Not sure about CD boot, but probably possible.
But why not boot from eSata drive? Or from a flash drive.
What brand/model system.

It sounds like example is for some very old systems that would not boot from an external USB drive and had to boot using CD & plop tool.
Or encrypted internal drive where you had to have everything totally separate.

BIOS boots from MBR and every drive has one MBR which is first sector on drive. Boot-Loader normally starts boot process by BIOS to MBR to more boot code elsewhere on drive.
UEFI boots from ESP - efi system partition. UEFI uses folders/files in ESP to start boot process & you can have multiple installs in one ESP. Somewhat like having many MBR all on one drive. Every drive can have an ESP, but grub normally installs only to first internal drive, so some work arounds required for full UEFI install to external drive.

---

### Post by piggeywig2000 on 2017-10-15
Ok, I'm using a BIOS not UEFI. I don't want to boot from a flash drive because I don't have a spare one knocking around, and I don't want to boot from the esata drive itself because I don't think the BIOS likes it very much (although I might try re-installing as I think I messed up the install last time I tried that). That's why I want to boot from a CD. And it's a dell Latitude E-4300

---

### Post by oldfred on 2017-10-15
How much RAM.
If 2GB or more,  64 bit better.
But since older system, you may prefer a lighter weight flavor/gui. But full Ubuntu should work.
       Lightweight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

Usually eSATA drives are seen as an internal drive, but some systems only like to boot from internal drives. Issue usually is with removable DVD/drive caddy.
But if installing Ubuntu to any drive other than internal drive/sda, you must use Something Else install option and choose the install drive using combo box at bottom of partitioning screen. All installs and even default on Something Else will install grub to drive seen as sda.

       
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)

---

### Post by C.S.Cameron on 2017-10-15
Try unplugging the internal drive before installing to the external drive. 
Create a partition for the OS before proceeding, use "Something else" to install on that partition.
The computer should be able to boot an external drive unless it is very old.
If the computer is like 10 or 15 years old, try **Plop boot manager**, which works from a CD, (or floppy), and can boot USB.

---

### Post by sudodus on 2017-10-15
I think Dell Latitude E-4300 was manufactured around 2009. I agree with C.S.Cameron and think it will boot directly via eSATA, at least I suggest that you try. Things will be simpler that way (instead of booting via some extra drive). Have a look at the following link, where installing to an external drive is described,

[Boot Ubuntu from external drive - Introduction and Instructions](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

---

### Post by efflandt on 2017-10-18
Something to note with Dell computers is that even if you set something higher up in the boot order, it may skip that when booting automatically if it is a removable drive, unless it was the last drive you booted from. So you may need to still use the hot key (F12?) during BIOS splash to select boot device, at least the first time you boot from eSATA or USB if normally then booting that same drive.

That is probably so a PC with Windows does not accidentally get infected by a malicious bootable CD, DVD, USB memory, etc. The only virus I caught (Monkey or Stoned Empire Monk) was a boot sector virus spread by accidentally booting an infected floppy disk many years ago that would spread to any floppy inserted in that computer.

---

