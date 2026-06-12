---
title: "Upgrading via CD"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by jayjay960 on 2008-11-14
I'm trying to upgrade from Ubuntu 7.10 to 8.04 using a CD. The Ubuntu website says this:

1. Download the alternate installation CD
2. Burn the ISO to a CD and insert it into the CD-ROM drive of the computer to be upgraded.

If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by mounting the ISO as a drive with a command like:

sudo mount -o loop ~/Desktop/ubuntu-8.10-alternate-i386.iso /media/cdrom0

3. A dialog will be displayed offering you the opportunity to upgrade using that CD.
4. Follow the on-screen instructions.

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

gksu "sh /cdrom/cdromupgrade"



I have the cd burnt and I put it in, the dialog did not pop up. I typed in the command, it asked for my password and nothing happened.

Also there's no "cdromupgrade" folder on the disk for some reason.

Can anyone help?

---

### Post by inobe on 2008-11-14
> I'm trying to upgrade from Ubuntu **7.10 to 8.04** using a CD

the command your using has version 8.10 in it !

```
sudo mount -o loop ~/Desktop/ubuntu-8.10-alternate-i386.iso /media/cdrom0
```

edit: i guess what i am trying to say' you can't upgrade from 7.10 to 8.10.

---

