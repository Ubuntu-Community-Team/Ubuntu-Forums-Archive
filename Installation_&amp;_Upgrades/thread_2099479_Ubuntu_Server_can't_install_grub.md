---
title: "Ubuntu Server can't install grub"
date: 2012-12-29
forum: Installation &amp; Upgrades
---

### Post by Gunzinger on 2012-12-29
Hello, since some days I have problems with Ubuntu, first i had a Ubuntu 12.04 desktop edition, this worked for some weeks, then I shut it down ("sudo shutdown -h now"), because I took the whole hardware out of the case, but didnt change anything on the hardware side, after everything was out of the case and connected everything correctly again, it didnt want to boot, so i tried to reinstall Grub, but grub-install /dev/sda says: "/usr/sbin/grub-setup: error: hd0 appears to contain a ufs2 filesystem which isnt known to reserve space for DOS-style boot. Installing GRUB there could result in FILESYSTEM DESTRUCTION if valuable data is overwritten by grub-setup (--skip-fs-probe disables this check, use at your own risk).". So I was like: "Fk this."

I had backups of everything important, so today I tried to install Ubuntu 12.04 Server, everything seems perfect, but then the grub-installation failed, it couldnt write into the MBR.

I hope that you can help me :)
Here is my Hardware I try to run it on:

Mainboard: MSI IM-945GC with a Intel Atom 330 @ 1.6Ghz (HT on)
RAM: 2GB of Kingston DDR2 RAM
HDD: Hitachi HDT725032VLA360 (320GB)

---

### Post by oldfred on 2012-12-29
Welcome to the forums.

It seems to be saying a CD image was written to hard drive?

Lets see what BootInfo report says. You can install to your Desktop liveCD, but not a server install CD as that is not a liveCD. Or you can download a full ISO.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Gunzinger on 2012-12-29
I'm on it :)

AAAND it's there: [http://paste2.org/p/2666368](http://paste2.org/p/2666368)

---

### Post by oldfred on 2012-12-29
Other than grub2's boot loader not being in MBR I do not see anything. If you run the suggested repair from Boot-Repair does it work?

The only other issue we have seen with only some BIOS is larger / (root) partitions. There was a bug with grub on very large (over 600GB) but there sometimes are issues with / partitions that end up with boot files near beginning of drive and beyond 100GB. May be BIOS setting (should be AHCI or LBA, not IDE). But may be grub? Some just use smaller / and make rest of drive /home or just a data partition. So if still not working after Boot-Repair you might try shrinking /.

---

### Post by Gunzinger on 2012-12-29
Thank you so much! Now it works! Im so happy right now :)

But now there is a server waiting for me configuring it :D
This is going to be a long night, now it's 11:34PM in Germany :)

---

### Post by oldfred on 2012-12-29
Glad you got it working. :)

Have fun configuring.

---

