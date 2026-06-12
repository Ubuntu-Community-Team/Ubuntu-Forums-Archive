---
title: "Help: UnInstalling Win8 RP &amp; Installing Ubuntu"
date: 2013-01-24
forum: Installation &amp; Upgrades
---

### Post by waterdr0ps on 2013-01-24
In my laptop I had Windows Vista. When Windows 8 Release Preview came, I installed it as dual boot. Now, I want to uninstall Win8 RP and install Ubuntu in its partition. I still want to keep Vista in its own partition. How can I do it? I have Vista and Win8 RP in separate partitions, and after Ubuntu installation, I want to have just Vista and Ubuntu in my boot menu. Please help

---

### Post by Bucky Ball on 2013-01-24
When you get to the partitioning section of the Ubuntu install select 'Something Else'. Kill the Win install which will create free space (delete the partition). Install Ubuntu to the free space. Ubuntu uses EXT4 partitions so the NTFS Windows one can not be used and should be deleted.

---

### Post by waterdr0ps on 2013-01-24
> **Bucky Ball said:**
> When you get to the partitioning section of the Ubuntu install select 'Something Else'. Kill the Win install which will create free space (delete the partition). Install Ubuntu to the free space. Ubuntu uses EXT4 partitions so the NTFS Windows one can not be used and should be deleted.

Thanks. So, when I do this my boot menu will also get updated to show just Ubuntu and Vista?

---

### Post by Bucky Ball on 2013-01-25
Once Ubuntu is installed, in a terminal run:

```
sudo update-grub
```That will pick up any installed operating systems if they are not showing already. If you have trouble booting when you're done, you can try creating and booting from a Boot Repair CD (you can install it via Software Centre or Synaptics, depending on what you're using, and run it while running from the desktop from the Ubuntu install CD also).

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Mark Phelps on 2013-01-25
If Win8 and Vista shared one physical drive, Win8 would have installed its boot loader files into the Vista partition; thus, when you erase Win8, you might not be able to boot into Vista if Win8 is the default OS in the Win8 boot menu.

---

### Post by waterdr0ps on 2013-01-26
> **Mark Phelps said:**
> If Win8 and Vista shared one physical drive, Win8 would have installed its boot loader files into the Vista partition; thus, when you erase Win8, you might not be able to boot into Vista if Win8 is the default OS in the Win8 boot menu.

Please see my current boot screen in attachment. I do not have Win 8 CP. It didnt went away whn I installed Win 8 RP. I currently set Win8 RP as the default. 

I had (and still have) Vista in my C: and I created a new partition to install Win 8 CP. I installed Win 8 RP in the same partition I had CP. So, currently I have two partitions with OS in it. 1. Vista 2. Win8 RP. I have a 3rd partiton with a very small space just for specific use.

Can some one please help me what will happen if I try to install ubuntu? I tried installing it and it has an option of 'REplace Win 8'. Not sure if I can choose it and still get ubuntu and vista.

---

### Post by Mark Phelps on 2013-01-26
The boot screen you attached still shows Win8 CP -- which is what happens if you install a newer Windows OS when an older one is still present on the same physical drive -- the Win8 boot loader files overwrote the ones in Vista.

Since you want to keep Vista -- let's fix that first.  Go into your boot screen and choose Vista as the default.  Then, reboot.

You should now get the old Vista boot screen -- the one with the sliding green bar, instead of the Win8 boot screen.

Once you boot back into Vista, use the Disk Management utility to remove the old Win8 partition.  Do NOT create a new partition in the unallocated space -- leave it empty.

Then, reboot using the Ubuntu live CD/USB and choose Something Else to create a Linux filesystem in the unallocated space.

---

### Post by waterdr0ps on 2013-01-27
> **Mark Phelps said:**
> The boot screen you attached still shows Win8 CP -- which is what happens if you install a newer Windows OS when an older one is still present on the same physical drive -- the Win8 boot loader files overwrote the ones in Vista.

Since you want to keep Vista -- let's fix that first.  Go into your boot screen and choose Vista as the default.  Then, reboot.

You should now get the old Vista boot screen -- the one with the sliding green bar, instead of the Win8 boot screen.

Once you boot back into Vista, use the Disk Management utility to remove the old Win8 partition.  Do NOT create a new partition in the unallocated space -- leave it empty.

Then, reboot using the Ubuntu live CD/USB and choose Something Else to create a Linux filesystem in the unallocated space.

Thanks a lot.. I was able to install Ubuntu without much confusions. My Windows boot screen still shows 3: Win8 RP, Win 8 CP and Vista, even after I used the Win 8 partition for Ubuntu. 
btw, I didnt do a 'swap' partition during installation. Is that ok? 
The only issue I'm experiencing right now is with Chrome/You Tube (Yellow/ Green dots). But, it looks like a known issue.

---

