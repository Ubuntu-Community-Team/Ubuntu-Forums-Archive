---
title: "creating a boot list for Win 7 and Umbutu on separate HDD"
date: 2012-11-23
forum: Installation &amp; Upgrades
---

### Post by nekollx on 2012-11-23
So here's my situation I have a desktop (IDE/PATA) running Umbutu 12 and our laptop (SATA) craped out but the OS is fine (it the CPU that died.) So I slapped it into a usb case and plugged it into desktop.

with the IDE unplugged it boots to Windows so I know that works. but with the IDE in it boot to Umbutu and I'm trying to find a way to modify the book loader so there is a choice to boot into one or the other.

---

### Post by darkod on 2012-11-23
When you are in ubuntu and with the sata disk connected, open terminal and run:
sudo update-grub

That will detect windows and make the necessary entry in the grub boot menu.

---

### Post by nekollx on 2012-11-24
Well that worked perfectly but i'm seeing a new problem and i'm not sure how to solve it, wheni boot windows from GRUB i'm getting a loop of "windows is loading files..." then reboots. I know when in the laptop i can get to the user screen but not in the desktop.

---

### Post by darkod on 2012-11-24
Windows is not very flexible to changes after it's installed. Not sure if it would work when the internal hdd is installed into a usb case.

For example, after you install windows in your computer, it's enough to go into BIOS and change the sata port mode and it will stop booting.

So, I am not sure if you expect it to work from the usb case. You might wanna investigate that on the windows forums. Grub tried to boot it as it seems. After that, windows needs to take care of things, not ubuntu/grub.

---

### Post by Mark Phelps on 2012-11-25
Although MS is allowing for "portable" utilization of Win8, it does not allow that for earlier versions.  So, there is really no way to run Win7 from an external drive.

---

