---
title: "Installation problem (7.10)"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by farbror_ace on 2007-11-07
Hi

I have problems installing Ubuntu as a dual boot with my exsisting XP Pro.
Ive setup the following:

/dev/sda1 ntfs /media/sda1 (Exsisting XP 40Gb)
/dev/sda2 ext3 / (Root partition 6Gb)
/dev/sda5 ext3 /home ( Home partition 12Gb)
/dev/sda6 swap (1Gb)

Installation goes all the way through but I never get the last Installation successful/Reboot message.
If I reboot manually I get "No operation system found".
And if I restart the installation from cd sda2 and sda5 are mounted to /media/sda2 and /media/sda5. (Not / and /home)

What is wrong? Desperate for help this is my work pc....

Ace

---

### Post by farbror_ace on 2007-11-07
Follow-up question:

My drive displays as sda is it correct that bootloader should install to (hd0)?
I only have one harddrive.

---

### Post by Pumalite on 2007-11-07
(hd0) is fine. Start again. Do md5sum on iso. If OK., burn new CD at 4x. Install again.

---

### Post by farbror_ace on 2007-11-07
Seems like the copying of files are ok.
It does all the configuring hardware, loading modules etc after file copying.
Then at 96% - configuring bootloader it just exits without error.

---

### Post by farbror_ace on 2007-11-07
My /var/log/installer/debug contains the following error:

File "/usr/share/ubiquity/install.py", line 1308, in configure_bootloader
dbfilter = grubinstaller.GrubInstaller(None)
AttributeError: 'module' object has no attribute 'GrubInstaller'

---

### Post by Pumalite on 2007-11-07
Try Alternate CD.

---

### Post by farbror_ace on 2007-11-07
Thanks

Managed to get my XP booting again atleast.
Will try alternate CD tomorrow if I dare..

---

### Post by Pumalite on 2007-11-07
Life has to be lived with courage.

---

### Post by farbror_ace on 2007-11-15
Ok 'solved' this one.
For some reason Gparted(probably on my request) had created my swap as a logical drive not connected to any primary/extended partition and this made GRUB crash upon installation.

Once this was fixed the installation was good to go.

---

