---
title: "Different Kind of Dual Boot..."
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by ivanjs on 2005-10-15
I already have Windows XP installed on a drive, and have a new 120gig ide that I"m putting Ubuntu on. So I'll have windows on 1 drive, and ubuntu on  a completely separate drive.

On bootup, how do I get Ubuntu to know about the windows drive, or the windows drive to know about the ubuntu drive so that I can choose the OS at startup? 

I know if you have them both on the same drive but different partitions, you can use grub, but if they're on separate drives, then what?

If it's still GRUB, what is the syntax for adding a separate bootable drive that has windows? Or should I edit the windows boot list (somehow) to add ubuntu (can that be done?).

So many questions...

thanks.

---

### Post by renzokuken on 2005-10-15
i could be wrong here, but it dont think it matters where u install ubuntu.....

the installation should still recognise the windows partition and add it automatically to Grub regardless of what drive it is on

i.e. it does it all for you

(if i am wrong here, let me know and i'll slap myself and keep quiet in future  >_<  )

---

### Post by Omnios on 2005-10-15
I have a 120Gdrive partitioned in two with XP and Vfat as a shared document drive and also a second 40Gig drive with Ubuntu. Grub set me all up just fine only be carefull that you set the installer to install Ubuntu onto the drive you actualy want it to go.

---

### Post by chajuram on 2005-10-15
Hi,

It still is grub. just make sure you install ubuntu after you install windows. 

Chajuram.

---

### Post by jpkotta on 2005-10-15
I recently set up Ubuntu on a computer at school.  Windows is on an SATA drive, and Ubuntu is on an IDE drive.  The BIOS doesn't seem to allow the IDE drive to boot, and Ubuntu didn't set GRUB up correctly for that senario.  Anyway, I changed Ubuntu's root in the menu.lst from hd0 to hd1 and windows from hd1 to hd0.  Then I installed grub to the (bootable) windows drive:
```
sudo grub-install --root-directory=/boot /dev/sda
```
Also, when I updated the kernel, it changed everything back again.  I think changing the line
```
# groot=(hd0,0)
```
to
```
# groot=(hd1,0)
```
will fix that, but I haven't updated the kernel since, so who knows.  If someone knows for sure, please post the answer.

Hope this helps.

---

### Post by BLTicklemonster on 2005-11-18
[QUOTE=jpkotta]I recently set up Ubuntu on a computer at school.  Windows is on an SATA drive, and Ubuntu is on an IDE drive.  The BIOS doesn't seem to allow the IDE drive to boot, and Ubuntu didn't set GRUB up correctly for that senario.  Anyway, I changed Ubuntu's root in the menu.lst from hd0 to hd1 and windows from hd1 to hd0.  Then I installed grub to the (bootable) windows drive:
```
sudo grub-install --root-directory=/boot /dev/sda
```
Also, when I updated the kernel, it changed everything back again.  I think changing the line
```
# groot=(hd0,0)
```
to
```
# groot=(hd1,0)
```
will fix that, but I haven't updated the kernel since, so who knows.  If someone knows for sure, please post the answer.

Hope this helps.[/QUOTE]


Would you step by step that for me please? I have a hd with windows on it, and I want to dual boot. At present, it would just be nice if ubuntu even recognized it's existance even. I don't want to reinstall, either. So could you please post a step by step on exactly what actions were taken when and where please?

---

