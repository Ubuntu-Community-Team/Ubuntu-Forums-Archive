---
title: "Multiple OS's... (x3)"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by Cybergrinder on 2008-02-07
Hi all,

I'm trying to install Ubuntu onto my system which I already have Win 98, Win 2000 installed, each with their own partitions.I'm trying to get Ubuntu installed so that I can boot any OS from the hard drive. I've got the partition set up for Ubuntu, the problem comes when setting up the boot devices (GRUB/LILO & windows)  This is of course the ideal....:guitar:

Otherwise how do I make a bootable CD & still be able to maintain my MBR?

---

### Post by logos34 on 2008-02-07
So, you've installed ubuntu and can boot into it but you can't boot windows entry from grub menu, is that what you mean?  

Because if that is the case you could check /boot/grub/menu.lst file--for windows root try (hd0,0) or (hd0,1)...one of the two should work.  You may also need to flag the windows parition as bootable using gparted

---

### Post by Cybergrinder on 2008-02-07
I've managed to get Ubuntu to pick up Win 2000 during the install, but not a peek of Win 98....,which I use more than 2000. The funny thing is I've got 98 set as the default OS under the current (microsoft) setup.

---

### Post by sandysandy on 2008-02-07
> **Cybergrinder said:**
> I've managed to get Ubuntu to pick up Win 2000 during the install, but not a peek of Win 98....,which I use more than 2000. The funny thing is I've got 98 set as the default OS under the current (microsoft) setup.

in ur menu.lst file on Ubuntu check whether the win 98 entry is there and whether the partition is mentioned correctly. 

when u boot up what all options does grub give u.

also post output of sudo fdisk -lu

regards

---

