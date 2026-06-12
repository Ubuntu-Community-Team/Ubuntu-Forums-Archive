---
title: "Another GRUB error 17"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by khm on 2007-01-22
So I am still quite new to linux installs but here is my setup:

3 hard disks:
IDE 1/hda1: 80 gig (XP Pro installed here)
IDE 2/hda2: 120 gig (NTFS storage)
SATA 1/sda1: 160 gig (formatted and installed Kubuntu 6.10, auto install)

when I try to boot it comes up with error 17.  I looked in the BIOS and it doesn't seem able to select the SATA drive as an option to boot from.  

Any ideas (I did search the site and found similar issues, but wasn't able to completely understand them)

Thanks!

---

### Post by khm on 2007-01-22
Also, I noticed in the advanced BIOS settings I could set "Alternative Boot" to Enabled.  This changed the GRUB (Stage 1.5) error to 21.  I loaded up the live cd to try and reinstall GRUB "grub-install /dev/sda1" but am not permitted to do this.  I tried su'ing to root, but dont know the password.  Is there a default pass for root on a live cd?  I also tried a program called GAG... It allowed me to boot to XP again, but still can't log on to Kubuntu.  Is there a way to make the SATA drive visible during boot?

---

### Post by austin on 2007-01-22
if you want root

sudo passwd root

then enter a passwor dof your choice

though you don't need it if you start every line you type with sudo 

About the grub-error: I have the same, am currently investigating. I think this is about loading the right (usb) modules "earlier", before the booting happens, haven't found proper instruction yet ...

---

### Post by khm on 2007-01-22
Okay, so I'm still having issues.  I have re-installed about 5 times.  I have tried specifying GRUB to be installed on my master IDE hd (where windows is installed) and on my SATA drive where Kubuntu is installed.  When GRUB is installed on the IDE windows drive, I get an error 17 or an error 21 from grub stage 1.5.  When GRUB is installed on the SATA drive, I get no errors at boot up, and it will automatically boot to windows.  It seems like my SATA drive is not being recognized, (even though the Kubuntu installer sees it just fine).  

I have also tried GAG boot loader, which does not see the boot sector for linux.

Another odd issue is that in my **/boot/grub** folder, I have only one file which is **device.map** which looks like this:

[B](fd0) /dev/fdo
(hd0) /dev/hda
(hd1) /dev/hdb
(hd2) /dev/sda[/B]

I tried a find command for **grub.com** and it does not exist.

When I try **grub-install /dev/sda**, I get this message:
**Could not find device for /boot: Not found or not a boot device**

I also tried:[B]
sudo grub
find /boot/grub/stage1[/B]
and got **Error 15: File not found**

here is my fstab:[B]
cat /etc/fstab
union fd / untion fs rw 0 0
tmpfs /tmp tmpfs no suid, nodev 0 0[/B]

Any advice?

---

### Post by austin on 2007-02-15
how are you? still problems?

---

