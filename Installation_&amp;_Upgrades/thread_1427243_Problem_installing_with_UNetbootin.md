---
title: "Problem installing with UNetbootin"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by crashcrew on 2010-03-11
I partitioned my hardrive in order to dual boot with Win XP (just for gaming).
 
My partition is as follows: NTFS 200GB for XP, EXT4 145GB for Ubuntu, SWAP 5GB.
 
Everything goes smoothly until I get the following message:
 
***Installer needs to commit changes to partition tables but cannot do so because partitions on the following mount points could not be unmounted:***
 
***/cdrom***
 
***Please close any applications using these mount points.***


I don't have a CD in the drive nor is anything (that I'm aware of) using the drive.
 
Any ideas? 
 
Thanks in advance!

---

### Post by crashcrew on 2010-03-11
Any ideas as to what may be causing this?

---

### Post by C.S.Cameron on 2010-03-11
Are you installing from Live CD or Live USB?
/cdrom is the folder in /filesystem where the "Live" files reside.

---

### Post by crashcrew on 2010-03-11
> **C.S.Cameron said:**
> Are you installing from Live CD or Live USB?
/cdrom is the folder in /filesystem where the "Live" files reside.
 
 
I downloaded the iso image and am using unetbootin to install from there. I'm not sure I understand what you are asking.

---

### Post by C.S.Cameron on 2010-03-12
There are several ways to install Ubuntu using UNetbootin.
You can install to a thumbdive, (and make a Live USB), then boot from this Live USB to install Ubuntu to your hard drive, (similar to using the Live CD).
Or you can use UNetbootin Type: Hard Disk option to install to Drive C:\.
This option puts sort of a virtual Live CD on your C drive so the next time you boot you have the option of booting this virtual Live CD and installing Ubuntu.

---

### Post by crashcrew on 2010-03-13
> **C.S.Cameron said:**
> There are several ways to install Ubuntu using UNetbootin.
You can install to a thumbdive, (and make a Live USB), then boot from this Live USB to install Ubuntu to your hard drive, (similar to using the Live CD).
Or you can use UNetbootin Type: Hard Disk option to install to Drive C:\.
This option puts sort of a virtual Live CD on your C drive so the next time you boot you have the option of booting this virtual Live CD and installing Ubuntu.
 
 
I chose the "hard drive" option. Everything went well until it started to actually make the partitions, as described above. Then the partitioning stopped and the part where it said it couldn't "unmount" my /cdrom came up and it started over from the beginning.

---

### Post by C.S.Cameron on 2010-03-13
It sounds like it is trying to install to the same partition the "virtual" Live CD is installed on except make an install flash drive instead. a drive 1GB or over should work.

---

### Post by crashcrew on 2010-03-13
> **C.S.Cameron said:**
> It sounds like it is trying to install to the same partition the "virtual" Live CD is installed on except make an install flash drive instead. a drive 1GB or over should work.

Thank you...Thank you...Thank YOU!!

Your post got me thinking. I was choosing to install the LiveCD, but as I stated earlier it wasnt working. So, when UNetbootin gave me the option of which distro I chose the HD option! 

After a few tweaks Im nearly fully operational!

Main problem now. How do I change my keyboard layout? I cant use commas, apostrophes, etc etc.

Other than that, I LOVE LINUX! :D

---

### Post by C.S.Cameron on 2010-03-13
You can select your keyboard preferences during setup or change them using System/Preferences/Keyboard.

---

