---
title: "Fakeraid problems with Raid 0"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by bigfoot150 on 2007-11-02
Hello folks. New user here. I have previewed the Live CD and I like what i see. Before installing i did some research on installing with onto a fakeraid setup. My motherboard has the ICH5 and Fastrak 378 raid controllers. I followed the community tutorial for Gutsy but have ran into a couple problems. They are as follows:

1. Cannot partition the drive properly. I have 2x 34GB WesternDigital SATA drives hooked up and while dmraid recognizes the array with no problem but Gparted really seems to blow. I will try to partition the drive but as soon as it completes an operation the damn thing crashes and disappears. Then when i reopen it, it has a single partition using all available space. If i try to resize and add a swap partition it again crashes. 

If i abandon Gparted and do my partitioning through the live disk installer it will only partition the entire array as one whole partition again using all available space. This is fine because i figure i could always go back and implement a swap file instead of a swap partition.

2. With the installer using the whole array as a partition i can go though the install however if i tell it to have grub installed to my /dev/mapper/isw_behihke_cec the installer pretty much tanks. If i go ahead and leave it at the default(hd0) and let the installer tank anyway, when i go through the grub install in the Fakeraid guide i get an error code shown below. 
```

grub> find /boot/grub/stage1Unknown partition table signature

Error 15: File not found

```  
So at this point i am pretty much stuck. 

3. Providing that i can't get this to work can anybody recommend a good PCI Hardware controller that will work with Ubuntu?

Thanks ahead of time.

---

### Post by bigfoot150 on 2007-11-02
bump

---

### Post by joffy on 2008-02-27
I've had pretty much the exact same problem as above.  I can mount the raid partition just fine when its one big drive and write files to them and reboot and everything stays persistent.  But I can not get grub to work (same error as above) and gparted seems to crash very often  (also as mentioned above) when I try to make an Extended partition or change any thing.  I've followed so many guides that at this point I think I may need to give myself a bios update just in case.  I am using the 7050m-m mother board.  Any ideas to throw at me would be great and appreciated. Thx.

---

