---
title: "partition hell?"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by downset13 on 2008-06-30
So here is the run down:

HDD1
C:Vista Primary
E:Vista Recover
HDD2
D:Vista Storage
F:XP

So I booted up the ubuntu install planning to get rid of the vista primary
partition and install ubuntu on about 20 gig of it and leave the rest
for ntfs storage.  I deleted the vista primary partition and created a 2 gig
swap partition, a 12 gig root directory, and left the rest unformatted.  This was all done under the manual settings of the ubuntu install.  I told it to continue and went on my way.

Well when i restarted the system it only gave me the longhorn (loader) option under other operating systems.  I installed the gnome partition manager to find this:

Disk1:
dev/sda1:reiserfs
dev/sda2:linux-swap
unallocated
dev/sda3: ntfs

Disk2:
unallocated

Please please PLEASE tell me it didn't format disk2 when i didn't ask it to.  If it didn't... how can i convince GRUB to let me boot to XP?

Thanks!

---

### Post by RATM_Owns on 2008-06-30
If all that is on disk 2 is unallocated...the drive is wiped.

---

### Post by downset13 on 2008-06-30
hmm... i kind of feared for the worst

guess the back up transfer process starts now... woohoo

---

### Post by untermensch on 2008-06-30
You could use testdisk. I think it is used to get deleted information off of hard drives.

---

### Post by 2598matt on 2008-06-30
Your lucky... I don't have any partitions on the computer I'm trying to install Ubuntu on... Its like HELL I  CANT GET UBUNTU ON IT BECAUSE THERE'S NOTHING TO INSTALL IT TO! It says...

---

### Post by downset13 on 2008-06-30
okay... so now i put in my windows xp disc so that i can install it on the unformatted second drive: but now it says windows could not find any drives to install on.  Do I need to find some way to format it as an ntsf drive or something first?

---

### Post by smalt18 on 2008-07-02
I'm in the same boat. Any suggestions? Please help.

---

### Post by Bliepo32 on 2008-07-02
The same happened to me really. Acronis could see the partitions, but Ubuntu could not. Only option was backing-up, format, and use gparted to make new partitions. The disk didn't contain many files though, so making a back-up was quick and easy.

---

