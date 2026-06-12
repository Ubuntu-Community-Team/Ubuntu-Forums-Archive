---
title: "Installing on a second internal drive ?"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by Dennis McClary on 2008-02-09
I have a Dell Inspiron 530N that came with 7.04 installed. I have the desire to have a second bootable hard drive to try 7.10 and other linux distros while maintaining my 7.04 system which I am quite happy with. I have had no success booting with a USB drive on this computer although I could get the drive to boot on other computers! I am considering purchasing a SATA II internal drive to install as a second internal drive. I have read all of the cautions about disconnecting an internal drive while installing to a USB drive so that grub gets installed on the proper hard drive. When installing Ubuntu to a second internal hard drive is it necessary to disconnect the first hard drive? This is assuming that I select the appropriate drive during installation. When booting the computer, can I simply enter the boot menu and select which drive to boot from? I suspect these questions are quite basic but I am new to linux. Thanks in advance.

---

### Post by confused57 on 2008-02-10
> **Dennis McClary said:**
> I have a Dell Inspiron 530N that came with 7.04 installed. I have the desire to have a second bootable hard drive to try 7.10 and other linux distros while maintaining my 7.04 system which I am quite happy with. I have had no success booting with a USB drive on this computer although I could get the drive to boot on other computers! I am considering purchasing a SATA II internal drive to install as a second internal drive. I have read all of the cautions about disconnecting an internal drive while installing to a USB drive so that grub gets installed on the proper hard drive. When installing Ubuntu to a second internal hard drive is it necessary to disconnect the first hard drive? This is assuming that I select the appropriate drive during installation. When booting the computer, can I simply enter the boot menu and select which drive to boot from? I suspect these questions are quite basic but I am new to linux. Thanks in advance.
You should have no problem installing Gutsy on a 2nd hard drive & you wouldn't have to disconnect the other drive when you install.

What you can do is near the end of the install, click on the "Advanced" button in the lower right bottom of the screen...another screen will appear which allows you to type in where you want to install grub, you would need to enter /dev/sdb1 or however your root partitions is designated during the install/partitioning...the default is (hd0), which is the first drive's mbr.  Even if this happens, it's no problem to reinstall whichever OS's grub to the primary mbr, using any Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

If you install Gutsy's grub to it's root partition, you can add an entry to your Feisty's menu.lst to boot Gutsy:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
then you can add an entry to boot Gutsy, using chainloading, to the very end of your menu.lst(after the line ###END DEBIAN AUTOMAGIC KERNELS LIST), something like:
```
title  Gutsy on /dev/sdb1
rootnoverify  (hd1,0)
chainloader +1
```

Here's more info on booting other distros from grub:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

Instead of using the entire 2nd drive for Gutsy, you may want to set up a separate ext3 data partition, that you can share between the 2 distros...you would need to select manual partitioning to do this...let me or anyone else who can assist you, if you may want to do this.

---

