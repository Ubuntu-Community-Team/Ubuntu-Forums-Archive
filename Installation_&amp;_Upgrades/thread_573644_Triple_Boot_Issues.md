---
title: "Triple Boot Issues"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by closetosomethingreal on 2007-10-11
i just installed kubuntu and i am loving it! but my vista partition has had some issues since. i had a dual boot with kubuntu and vista with grub and all was going well, but then i installed windows xp which put the xp bootloader in and 2 entries, one for xp home and one for xp profesional (i didnt have 2 xp installations). i reinstalled grub, and when i boot the vista option, it goes to that stupid xp loader. the xp home option runs fine, the xp professional option doesnt work, and vista is nowhere to be found. i tried repairing the bootloader from the vista install disk, but to my suprise it says that there is nothing wrong with the vista bootloader!! i am so confused. ive tried programs such as vista boot pro as well and they cannot even find my vista bootloader. help please!

---

### Post by Shazaam on 2007-10-11
A couple of links that might help...
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Others may be along to help out.

---

### Post by Herman on 2007-10-12
Well I'm not sure about Vista because I haven't got that myself, but with all other versions of Windows if you want to boot two Windows on the same hard disk, you just need to use the 'hide' and 'unhide' commands in GRUB.

Would you like to try that?

Here is a link that should show you what I mean, [More than one Windows on the same disk]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_more_on_the_same_disk")  ...use hide and unhide commands

First you'll need to get your /boot/grub/menu.lst in kubuntu, 
```
kdesu kate  /boot/grub/menu.lst
```Then you'll need to add the 'hide' and 'unhide' commands to your existing Windows XP entyr in your Kubuntu GRUB menu.

You'll need to make up a new entry for Vista with 'hide' and 'unhide' commands too.

Something like this might work,
```
title     Microsoft Windows XP
hide      (hd0,1)
unhide    (hd0,0)
rootnoverify      (hd0,0)
savedefault
makeactive
chainloader +1

title      Microsoft Windows Vista
unhide     (hd0,1)
hide       (hd0,0)
rootnoverify       (hd0,1)
savedefault
makeactive
chainloader +1
```Now, you'll probably have different partition numbers.

You'll need to replace the example partition numbers I used here with the actual partition numbers in your computer, they will most likely be different.
For example yours might have Windows Vista in (hd0,0) , Kubuntu in (hd0,1), and Windows XP in (hd0,2) maybe, (I'm just guessing, probably I'm wrong).
Please use a partition editor like GParted to look at your partitions or a command like 'sudo fdisk -lu' to check and get the right partition numbers, 
```
sudo fdisk -lu
```I hope that will work for you, please post back and let me know how you go,
Regards, Herman :)

If you need more help please post the output from 'sudo fdisk -lu' here and lte me know whaich partition is which and I'll have another try making up the boot entry commands for you.

---

### Post by closetosomethingreal on 2007-11-11
thanks for the great information, but i decided to make the complete leap to ubuntu an am now happily running vista only in vmware. i appreciate your response though! maybe it can help someone else. :)

---

