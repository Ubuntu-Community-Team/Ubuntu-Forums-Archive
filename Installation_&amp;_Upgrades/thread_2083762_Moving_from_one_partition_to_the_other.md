---
title: "Moving from one partition to the other"
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by Viper1987 on 2012-11-13
I googled a few things about moving my Linux primary partition to a logical partition. I really wish i did this on the install... Anyway, what i'd like to do is change up some partitioning so i have room for a boot partition. 
[B][U]
Current Setup:[/U][/B]
 Partition 1: Windows
 P2: Ubuntu
 P3: Swap
 P4: Shared documents (with files and the "program files" folders from Windows)

_**Desired Setup:**_
 P1: Boot
 P2: Windows
 P3: (Extended) Ubuntu
      P3-A: OS (logical)
      P3-B: /home (logical)
      P3-C: Swap (logical)
 P4: Shared Documents

Now, i know i can fumble around with gparted, copy the image of the Ubuntu partition to the shared documents partition, create the extended (and hence logical partition), move the image back to the created logical partition.

My question: are there any other precautions i should take? Like -- are there config files that are going to look to /dev/sda(old) instead of /dev/sda(new)? and how do i seamlessly change the settings in the OS to look for /dev/sda(new)?

Thanks in advance!

Kyle

---

### Post by pkadeel on 2012-11-13
Yes there can be consequences when a windows is involved. You might end up not being able to boot up any of the 2. One of the lessons I learnt regarding windows is that if you want to do something with it do it from within or at-least from using its partition manager available in its installer.

---

### Post by Viper1987 on 2012-11-13
not too concerned with Windows partition. I plan on deleting that to repartition it with a boot partition in front of the Windows partition. I, too, learned that lesson... which is why my ideal setup has a boot partition in front of the Windows partition

---

### Post by pkadeel on 2012-11-13
if you are not worried about the windows in that case you might be able to do such jugglery with linux. I would suggest a different approach though which I used during my transitional phase.

Create a live backup of your ubuntu using [remastersys]("http://www.geekconnection.org/remastersys/")
create a usb or DVD from that backup and test it as a live session. If found working then delete everything and create the new partition table as per your liking and reinstall both windows and ubuntu (ubuntu from your newly created live DVD/USB)

---

