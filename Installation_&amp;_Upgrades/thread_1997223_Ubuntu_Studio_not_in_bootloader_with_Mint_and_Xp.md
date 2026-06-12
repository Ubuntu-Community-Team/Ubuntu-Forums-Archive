---
title: "Ubuntu Studio not in bootloader with Mint and Xp"
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by sticksix on 2012-06-04
currently I have XP installed on one drive and Linux Mint on a second drive..have tried several times to install Ubuntu Studio on the drive with Mint..every time I do it never shows up in the bootloader at startup...what am I doing wrong???..I installed it along side Mint...can anyone help??

thanxs

---

### Post by darkod on 2012-06-05
And which is the bootloader at start? Windows bootloader? Grub1 from Mint? Grub2?

---

### Post by sticksix on 2012-06-05
bootloader is from mint....the options are mint first then windows..but studio is not there

---

### Post by darkod on 2012-06-05
If I am not mistaken, Mint uses grub1 which doesn't add new OSs automatically like grub2. That's why the latest OS installed, Ubuntu, is not there.

You will need to edit the /boot/grub/menu.lst manually and create an entry for ubuntu. Here you have an example of a grub1 entry for ubuntu:
[http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)

You will have to adjust it with your ubuntu root partition details, like /dev/sdXY and the correct UUID.

---

### Post by sticksix on 2012-06-05
ok makes sense...I'm pretty new to these systems but I will read on and give it a shot..thanks for your help

---

### Post by sticksix on 2012-06-05
so does Studio have Grub 2??...would it be easier for me to install Studio first then Mint second??

---

### Post by darkod on 2012-06-05
Ubuntu comes with grub2 since version 9.10 but I am not sure about the studio version.

There is no need to reinstall, and the order doesn't make much difference. In fact, the bootloader from the latest installation should stay on the MBR, in your case Ubuntu Studio.

Since you have two disks, did you try in bios to change to boot from the other hdd as first option? You might actually have grub2/grub1 from studio on the other hdd.

---

### Post by sticksix on 2012-06-05
did not try booting to other hard drive...would have to change things around a bit everytime...so what I need to do is add ubuntu into grub1 booloader options then?

---

### Post by darkod on 2012-06-05
> **sticksix said:**
> did not try booting to other hard drive...would have to change things around a bit everytime...so what I need to do is add ubuntu into grub1 booloader options then?

Adding ubuntu to the Mint grub1 is one of the options, yes.

---

