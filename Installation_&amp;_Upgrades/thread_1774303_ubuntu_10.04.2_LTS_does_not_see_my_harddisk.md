---
title: "ubuntu 10.04.2 LTS does not see my harddisk"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by bunizz on 2011-06-03
Hello,

I would like to install ubuntu 10.04.2 LTS in my desktop-pc. It boots, I select time zone and keyboard layout, but then it could not see my hard disk, so i cant go further.

But i can see the disk in console while typing:
```
# sudo fdisk -l /dev/sda
```

and I can also make changes in disk such as deleting all partions etc.

What do you suggest to me to solve this issue :popcorn:?

---

### Post by Hedgehog1 on 2011-06-03
If you have no other operating system on the hard disk (***if it is safe to wipe the disk completely clean***) you can create a clean partition map on the hard disk using the MBR style of partiton map by doing these steps in Gparted Partition Manager from the LiveCD/LiveUSB:

[IMG]http://img534.imageshack.us/img534/9282/mbrpariondemo01.png[/IMG]

[IMG]http://img858.imageshack.us/img858/9979/mbrpariondemo03.png[/IMG]

Then please attempt to install Ubuntu again.


***If you have another operating system on the Disk*** that you need to save (dual boot with Windows for example), then please do this from the LiveCD/LiveUSB so we can see what your options are:

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

[IMG]http://img854.imageshack.us/img854/4563/codetags.png[/IMG]


***The Hedge***

:KS

---

### Post by bunizz on 2011-06-03
I do not have any other operating system in my hard-disk. So the first advice has worked for me.

Thank you very much for your very well explained answer.

---

### Post by Hedgehog1 on 2011-06-03
Hurray!

Happy Ubuntu(ing)!!!!


***The Hedge***

:KS

---

