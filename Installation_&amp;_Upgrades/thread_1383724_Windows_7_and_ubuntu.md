---
title: "Windows 7 and ubuntu"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by Sale 666 on 2010-01-17
Hello i have a HDD 500GB that contains windows 7 installed!
Now i would like to add ubuntu 9.10 on it by shrinking the windows partition to 300GB and 200GB for Ubuntu!
The thing is i would like to use the windows loader instead of grub
because i heard it has compatibility problems!

Thanks!
Sasha

---

### Post by tachuela on 2010-01-17
Defrag, partition the drive FROM Windows and take a look at this link:
[http://www.ditii.com/2009/01/28/how-to-modify-windows-7-boot-loader/](http://www.ditii.com/2009/01/28/how-to-modify-windows-7-boot-loader/)

---

### Post by cariboo on 2010-01-17
Use the Windows disk management tools to shrink your Windows partition. Both Grub2 and grub-legacy work with Windows 7 with zero problems.

---

### Post by Sale 666 on 2010-01-17
Is it necesary to defrag? Cause i have auto defrag on!

---

### Post by Sale 666 on 2010-01-17
So groub will work if i just install ubuntu now? will i be able to boot into win? Should i chose write MBR?
I dont have the usb stick with me with my instalation so if i mess up im without my pc till tomorow =/

---

### Post by oldfred on 2010-01-17
Just be sure to shrink/resize your 7  partition from within 7 and reboot it several times so it can adjust to the new size. Often changing it outside windows does not give it a chance to repair itself on reboot and grub gets blamed.

I also like having a NTFS data partition for shared data so you can use your firefox and thunderbird profiles from one place.

Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

