---
title: "installing updates and programs on new install"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by jeff0149 on 2007-07-06
I just loaded Ubuntu on my drive.  As part of the process, I checked for updates and got 75.  When I tried to install these updates, I got an error '... must manually run dpkg --configure -a'.
To run this command, I must be a superuser (what is that).  I installed the program from a disk with the Live CD.  Should I use the text installer?

How can I fix that?
Jeff0149

---

### Post by bmorency on 2007-07-06
> **jeff0149 said:**
> I just loaded Ubuntu on my drive.  As part of the process, I checked for updates and got 75.  When I tried to install these updates, I got an error '... must manually run dpkg --configure -a'.
To run this command, I must be a superuser (what is that).  I installed the program from a disk with the Live CD.  Should I use the text installer?

How can I fix that?
Jeff0149

it means you must type in that command with "sudo" in front of it. it means you will run that command as root (aka administrator)

---

### Post by jeff0149 on 2007-07-06
I have tried the sudo command and now am told there isn't enough space on the device.  I installed this on a hard drive I formated with Windows XP and removed all data.  In the Gnome Partition Editor I have three entries, dev/sda1 ext3  the mountpoint is /media/disk, the size is 36.3GiB and it shows all used.  The installation, which is all that is on the drive only takes up 909.93MiB.

How do I clear the 36.3GiB for use????

Thanks,

---

### Post by bmorency on 2007-07-06
type in "df -h" check to see how much space is left on your partition that /var is on. when you download updates the are put into that folder. all the packages are extracted there too.

---

