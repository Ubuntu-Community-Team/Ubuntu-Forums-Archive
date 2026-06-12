---
title: "install 12.04 onto RAID 0"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by kuldaoo on 2012-04-28
Hi,
I have 2 x 200GB HDD in RAID 0 and mainboard with AMD controller. In this array I have 300GB partition with windows 7 and 100GB free partition where I want to install Ubuntu 12.04. Problem is the Ubuntu installer doesn't recognize the Raid. Gparted doesn't see the Raid too. I've tried to install kpartx (I've read somewhere it can help) but without effect. In windows I had to install special raid driver during the installation...

Can someone give me any advice?

---

### Post by filipe_fazanaro on 2012-04-28
Did you try to use the Alternate image?

---

### Post by kuldaoo on 2012-04-28
Yes I did. I can only create new raid there...

---

### Post by darkod on 2012-04-28
It might be a driver issue, since you needed to install a driver for windows too. Without a correct driver it would be logical that it doesn't see the array.

You are sure that you created a fakeraid array with the controller, not a software raid in windows right?

Just in case, when you boot into live mode with the live cd, if you try to activate the array does it work:
sudo dmraid -ay

After that does it show with:
sudo fdisk -l (small L)

---

### Post by kuldaoo on 2012-04-28
"sudo dmraid -ay" returns:

ERROR: pdc: wrong # of devices in RAID set "pdc_eidggfji" [1/2] on /dev/sdc
ERROR: removing inconsistent RAID set "pdc_eidggfji"
ERROR: no RAID set found
no raid sets

I created RAID with utility that I allowed in BIOS and before booting. RAID driver for windows is necessary according to instructions in manual.

---

### Post by darkod on 2012-04-28
It finds some kind of error and that's why it's not reading it properly. But I can't translate that error. Maybe if you google it, you can find something.

---

