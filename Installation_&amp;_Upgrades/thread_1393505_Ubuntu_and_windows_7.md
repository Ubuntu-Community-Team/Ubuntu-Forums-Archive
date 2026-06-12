---
title: "Ubuntu and windows 7"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by ABMJ on 2010-01-29
Hi Gents,

I have windows 7 installed in my internal laptop hard disk, and I have installed Ubuntu  9.10 " the Karmic Koala - released in October 2009 and supported until April 2011", on my external hard disk.

The problem I am facing is that the GRUB have been installed on the hard disk, for that reason if my laptop have restarted i need the hard disk to be attached to it to load the GRUB and to log in to windows, which is pain :)

I need your help by guiding me in moving the GRUB to my internal hard disk or return the windows boot loader in charge, so I can boot my windows without the hard disk.

Best regards,
ABMJ

---

### Post by darkod on 2010-01-29
It's the other way around. Grub2 got installed on the int hdd but its configuration files are always on the ubuntu partition which is on the ext hdd. So booting without the ext hdd is impossible.

You can do the following:
Unplug the ext hdd. Boot with the ubuntu cd, Try Ubuntu option. In terminal execute:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

That will install generic windows MBR on your int hdd (/dev/sda). Reboot without the ubuntu cd and your windows should boot straight away.

After that is working, you need to reinstall grub2 to the MBR of your ext hdd (most likely called /dev/sdb). You can follow the instructions from here but make sure you are using the instructions for 9.10 and you are using 9.10 cd:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by ebharv on 2010-01-29
You try going into the bios and setting the hard disk as the inital boot device. This sort of happened to me one time on my desktop and it worked for me. 

It's worth a try.

---

### Post by presence1960 on 2010-01-29
> You try going into the bios and setting the hard disk as the inital boot device. This sort of happened to me one time on my desktop and it worked for me.

It's worth a try.

That will not work as GRUB was installed to MBR of sda (internal disk) so when the machine boots it looks for grub.cfg on the ubuntu partition to bring up the GRUB menu. If the external is unplugged at boot the OP gets a GRUB error because grub.cfg is on the ubuntu partition on the external disk.

The OP wants to do what Darko said. restore windows to MBR of internal disk this way when the external is unplugged it boots right to windows. Then install GRUB2 to MBR of the external. Set the external in BIOS to boot before the internal disk. Now when the external is plugged at boot GRUB will take over and OP can boot into Ubuntu, if the external is unplugged the machine will boot to windows.

---

