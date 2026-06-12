---
title: "Reboot and Select proper Boot device after instalation of Lubuntu"
date: 2017-07-22
forum: Installation &amp; Upgrades
---

### Post by honzanav on 2017-07-22
I recently found an old computer with Windows XP and also one separate  Seagate HDD so I decided to install Lubuntu 16.04 LTS on it.
However after succesful installation I get message "**reboot and Select proper Boot device or Insert Boot Media in Selected Boot Device and press a key**"
I  changed the boot order, ran Boot-repair, reinstalled it, removed and  inserted again CMOS and the message still persists. It is interresting  that during the second and third reinstallation, it couldn´t install  Grub, but now it doesn´t report any problem.
The computer has an older motherboard **P5L-MX** with AMIBIOS v02.53. There isn´t any option about UEFI, only things such as Enhanced mode (now selected) and Compatible mode.

Output of boot repair:[http://paste.ubuntu.com/25146348/](http://paste.ubuntu.com/25146348/)
Thanks for any support

---

### Post by oldfred on 2017-07-22
You show the advanced LVM install. Usually used with encrypted installs or servers. Is that what you really wanted?

Some older systems have issues booting from larger drives. Often drive setting is IDE not AHCI, but that may be your enhanced setting? If you have AHCI make sure that is set for internal drive.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)

If you reinstalled several times, you may have an older grub in MBR, which is not correctly seeing the newer /boot partition.
Boot-Repair in its advanced options can do a full uninstall/reinstall of grub. But if encrypted LVM, you have to make sure you have mounted & unencrypted / (root) so the reinstall of grub will work correctly.

---

### Post by honzanav on 2017-07-24
I always used unencrypted LVM on all of my newer computers and there was no trouble with it.
However I tried to install Lubunntu without LVM and run boot-repair two times. It didn´t help to get rid of that error, but it installed GRUB on disk with Windows (Originally I didn´t want to do that) and from there *it boots into Lubuntu*. 
But there are some problems. When the GRUB starts it shows **Error: no device connected.** four times. Then I get the GRUB selection. When I boot to Lubuntu it shows blank screen for five minutes.  That´s more longer than booting from USB. (I think that Disk causes this.) When I´m booting Windows XP I get: "**Setting partition type to 0x7. Error: device format "ata4,msdos1" invalid: must be (f|h)dH, with 0 <s N < 128. Press any key to continue...**" Then there´s black screen for one minute and then it boots into Windows. Is there any option to tweak this?

What I didn´t mention is that disk with Windows is connected via SATA and Ubuntu via PATA if that is the cause. 
And Compatible and Enhance mode reffers to this BIOS setting: Onboard IDE operate mode.

---

### Post by honzanav on 2017-07-25
Also when I boot liveCD I´m getting these errors: > [IMG]http://img.ctrlv.in/img/17/07/25/5976e5bf1ba34.jpg[/IMG]
And I think this happens even when I boot from the drive, but instead of this there is just black screen.

---

### Post by oldfred on 2017-07-25
Seems like drive errors?
In Disks and upper right corner is Smart Status.
It can run lots of tests on a drive, but all I really know is whether drive is considered good or bad.

---

### Post by honzanav on 2017-07-27
So apparently Disk is OK, one attribute failed in the past. When I tried out of curiosity run the SMART test on disk with Windows it failed.
[ATTACH=CONFIG]276154[/ATTACH]

---

### Post by oldfred on 2017-07-27
Anytime temps are an issue, you need to clean system & make sure fans are all working. And vents are not blocked.

---

