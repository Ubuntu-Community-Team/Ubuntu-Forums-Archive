---
title: "Remove Windows after dual booting"
date: 2015-09-06
forum: Installation &amp; Upgrades
---

### Post by SebastianoS on 2015-09-06
Good afternoon folks, 

I have a doubt on my dual boot system. I once installed both ubuntu 15.04 and windows 7, but now I want to get rid of windows because it's just sucking up space. What's the procedure now? Can i simply delete the partition? What about UEFI and grub? Here's a screenshot of how my HD looks like now, which partitions can I delete?

[IMG]http://s15.postimg.org/numu8vrnv/Screenshot_from_2015_09_06_16_00_53.png[/IMG]

---

### Post by yancek on 2015-09-06
You have an EFI partition so if you are using that, both Ubuntu and windows files are there.  Do not delete that (sda1).  I would not delete any partitions.  If you have no data on the windows partition (sda3) which seems to be the case, just format that partition ext4 and create a mount point in Ubuntu for it and use it as a data partition.

---

### Post by SebastianoS on 2015-09-06
Would you suggest to merge it into my main ubuntu partition?

---

### Post by Bucky Ball on 2015-09-06
To merge sda3 with sda4 boot from live media (USB or disk), 'try ubuntu', once at a desktop launch Gparted.

Delete sda3 and grow sda4 into the free, unallocated space that creates.

PS: Best to attach screenshots via 'Adv Reply' (or 'Go Advanced') and use the paperclip icon. Spare a thought for those with slow net speeds and/or visual impairment. Thanks. :)

---

### Post by yancek on 2015-09-06
>  					Would you suggest to merge it into my main ubuntu partition? 				

No.  It's not like you might run out of space with your root filesystem partition as it is 315GB.  I'd just format sda3 and create a mount point in Ubuntu and mount it as a data partition.  It's your computer so if you want to merge sda3 and sda5, they are contingent and you should be able to do that.  I would expect all your files to be moved to the beginning of the disk but am not really sure as I don't usually move to the left.  If so, this could cause problems booting as the boot files are in a different location.  The first options is easier and less risky in my opinion but your choice.

---

### Post by SebastianoS on 2015-09-07
Point taken, thanks for your suggestions! I'll probably stick to having that extra partition for a while, in fact I still have plenty of space!

---

