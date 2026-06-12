---
title: "Ubuntu reinstall"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by hbbliss on 2007-12-05
I had a directory disaster on the hard drive of my IBM 600e laptop. It was dual booted with 6.10 and Win 98SE. I installed a new drive and installed 7.10 from a CD. I then installed the old drive in my removeable holder. Inserted it and asked Gparted to look at it. It reported that Win98 was in its directory and that something was wrong with the directory that held Ubuntu. I used fsck and it offered to fix the directory, success. When I reintalled this old disk as the primary it went into the GRUB menu and offered to load either OS. Both worked normally. My question is if I have my new 7.10 in the primary drive and 6.10 and Win98 in the insertable drive how do I get GRUB to offer to load 6.10, Win98, or the new 7.10? Suggestions please.

---

### Post by monktbd on 2007-12-05
post your output of
```
sudo fdisk -l
```
and
```
cat /boot/grub/menu.lst
```

basically you need to add the new removeable drive to the menu.lst of your new primary boot device, the harddisk where gutsy is on.

if you mounted also the old removeable disc where 6.10 is on you can go look there for the boot/grub folder and also post the contents of the menu.lst there.

---

### Post by mikewhatever on 2007-12-05
You have to set your BIOS to try and boot from USB first. If the external disk is present, you'll see your old grub menu, if not the new one with 7.10.

---

