---
title: "Question regarding GParted and new partition"
date: 2014-03-15
forum: Installation &amp; Upgrades
---

### Post by Brian_Daniels on 2014-03-15
Long story short, I have a system running 12.04 and basically copied the partition because I needed to make room. I have officially copied the partition and have two exact same copies, as you can see below.
[ATTACH=CONFIG]251189[/ATTACH]
The working partition is the highlighted one, the new one is the sda7. The main reason I copied the partition was due to not having very much space left on the active one. All of the unallocated (before copying) was whenever I had a Windows XP installed, and had removed it upon copying necessary files to my Precise install. I'm slightly confused because if you take a look, the new partition still only has 5% of room, even though there was considerably more room than the one I had copied it from. Have I messed up here, or what is the deal? I didn't want to delete the old partition in the case that the new one did not work, which it obviously has not.
[ATTACH=CONFIG]251190[/ATTACH]
Upon reading this, most of you could probably guess what I want to do already - Successfully copy partition to new space, delete old partition upon confirmation of new one's working, and delete all others, causing an end result of one precise partition and a swap with plenty of room to work with. So the question is, how do I go about doing this? Lol I should have known better that it wouldn't be *just* that easy.

If it helps any, I tried to update grub whenever I loaded my old partition, the one that I'm typing off of now, and had these results.
```
owners4life5@owners4life5-OptiPlex-GX270:~$ sudo update-grubGenerating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-18-generic
Found initrd image: /boot/initrd.img-3.11.0-18-generic
Found linux image: /boot/vmlinuz-3.11.0-15-generic
Found initrd image: /boot/initrd.img-3.11.0-15-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 12.04.4 LTS (12.04) on /dev/sda5
done
owners4life5@owners4life5-OptiPlex-GX270:~$ 
```

Thanks in advance for the help,
Brian

P.S. if it makes any difference, i used grub's LIVECD (usb) to edit my partitions.

---

### Post by Herman on 2014-03-16
My assumption is the partition has been resized but the file system hasn't. I have seen this kind fo thing before.
After GParted has worked on most partitions it normally runs a file system check and then resizes the file system to fill the partition.
It could be that something has gone wrong this time and for some reason it didn't finish the job properly.

You should be able to right-click on the partition in GParted and click 'check', and confirm that you do want the file system checked.
After the file system check, GParted will run resize2fs on the file system and that should fix your problem.

---

### Post by Brian_Daniels on 2014-03-18
Turns out that after following your suggestion, all I had to do was boot the LiveCD again, delete the old partition, resize, reboot, and fix grub. In other words though, all is good now! Thanks so much for the help. Marking as solved.

---

