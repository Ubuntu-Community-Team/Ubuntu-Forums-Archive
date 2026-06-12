---
title: "partitioner freezes at 50%"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by neba on 2008-10-25
hello,
I am trying to install Ubuntu on my desktop. It is almost same as my laptop. I have installed Ubuntu successfully on my laptop, now when I try to install it onto my desktop. I get to step 3 of 7, right after the keyboard layout. A little window pops up and tells me 'starting up the partitioner'. it only gets to 50% then nothing happens. I can exit out of it start again. I used several cds. I even downloaded Ubuntu again. I don't know what to do. I don't know Ubuntu well enough to partition to my self also I don't even get to that page. please help. 
Thanks,
Neba

---

### Post by bulldog on 2008-10-25
Manual partitioning isn't that hard to do,but it can be a little intimidating the first time you use this.
If your hdd is empty and there is no need for a dual boot hdd,try the next steps.
When the partitioner starts up,choose manual,create a partition 10GB and set it to format as ext3,turn bootflag on and mount it as /
Create a partition 2GB,set it to format as swap,and mount it as swap.
Create a partition as big as you want [/home] set it to format as ext3,mount it as /home.
If there's space left on your hdd you can create another partition for data or what ever,but this can be done later if you like.
If your done creating partitions,scroll down, and choose to write the changes to the hdd.
Continue the install.

---

### Post by neba on 2008-10-26
thank you. Now that you put it that way it really does not seam hard. :) I want to have dual boot with ubuntu and xp. When it is loading the partitioner, it stops at 50% I can't even get to the partition step. :(   ??? I don't know whats wrong. I used this cd on my laptop and on my girlfriends pc. I thought that the cd was bad, so I reburned it. still the same problem.

---

### Post by tommcd on 2008-10-26
This is just a guess here, but did you defrag Windows before trying to install Ubuntu? You can have problems with partitioning if Windows is badly fragmented. In any case, defragmenting Windows won't hurt, so you may as well defrag Windows and try again.

If that don't work, get the Gparted live CD or Parted Magic live CD and try partitioning the disk as Bulldog said, and then try to install Ubuntu to the root partition you created.
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

---

### Post by neba on 2008-10-26
I started a defrag after it didn't work the second time. then I saw that it was only 3% fragmented. Thats when I stoped the defrag. I will give it another try, thank you.

---

### Post by neba on 2008-10-26
also something I thought of, when I try to get into partition editor with the live cd. It will not open. it keeps scanning all devices. hmmm?

---

### Post by tommcd on 2008-10-27
Did you try Parted Magic or Gparted live CD? I'm wondering if Ubuntu doesn't recognize your hard drive controller. What kind of motherboard chipset are you using? Do you have a raid setup? Is your hard drive plugged directly into the motherboard, or are you using a sata pci card? Is your computer very new?
Boot the Ubuntu live CD and run **sudo lspci -v** and post the output here. Do a google search for your motherboard chipset and linux compatibility. Perhaps when Intrepid comes out in a few days it will not give you this problem. I can't think of anything else.

---

