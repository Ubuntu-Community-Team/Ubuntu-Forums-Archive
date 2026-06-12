---
title: "Installation Help - How do I go back to Step 1?"
date: 2014-05-25
forum: Installation &amp; Upgrades
---

### Post by balkrish999 on 2014-05-25
Hello, Long story short, How do i go back to step 1

1) I had a Windows 7 PC 
2) Shrinked Partion 
3) Booted Ubuntu 14 of USB and install its (Dual Boot) Grub on that Unallocated space
4) The grub works, and windows 7 work


(I made a stupid mistake in the Installation PROCESS :( )

I Want to go back and re do everything 

How do i go to step 1?   Normal

I was thinking should i go inside Windows 7 Simply delete the partion, and re do everything BUT my problem is that, will that affect Grub/anything?

Thank You :D

---

### Post by sudodus on 2014-05-25
The best way is to make a backup before starting to edit partitions and install operating systems. Then you can simply restore your original system from the backup.

I'm afraid there is no other way to get back to exactly the same system as before. But maybe you can get back to almost the same system. If you simply delete the Ubuntu partition, grub will also be removed and you have to repair the booting. If you have a Windows install disk, you can use it and repair (reset) the bootloader to boot only Windows. Otherwise you should keep the Ubuntu partition to be able to boot into Windows.

-o- 

So if I understand the situation correctly, you can boot into Windows, but not into Ubuntu. Before doing anything more, you should backup your system. I suggest that you make a Clonezilla live USB drive or CD disk and use it to make an image of the whole internal drive. Put the image on an external drive. Test that the image is good, that you can really restore your system from it (to a new drive). After that you can do risky things with your internal drive and still have peace of mind.

-o-

You did not write what is your final goal: do you want to stay with Windows, or do you want to repair or reinstall Ubuntu. Both options are possible.

---

### Post by balkrish999 on 2014-05-25
> **sudodus said:**
> The best way is to make a backup before starting to edit partitions and install operating systems. Then you can simply restore your original system from the backup.

I'm afraid there is no other way to get back to exactly the same system as before. But maybe you can get back to almost the same system. If you simply delete the Ubuntu partition, grub will also be removed and you have to repair the booting. If you have a Windows install disk, you can use it and repair (reset) the bootloader to boot only Windows. Otherwise you should keep the Ubuntu partition to be able to boot into Windows.

-o- 

So if I understand the situation correctly, you can boot into Windows, but not into Ubuntu. Before doing anything more, you should backup your system. I suggest that you make a Clonezilla live USB drive or CD disk and use it to make an image of the whole internal drive. Put the image on an external drive. Test that the image is good, that you can really restore your system from it (to a new drive). After that you can do risky things with your internal drive and still have peace of mind.

-o-

You did not write what is your final goal: do you want to stay with Windows, or do you want to repair or reinstall Ubuntu. Both options are possible.



Sorry for my mistake 

I can boot in to BOTH W7 and Ubunut perfectly 

the problem i have is i simply to want to restart everything and install dual boot ubunut again ( Long story short - i made a stupid mistake, in the ubunutu install PROCESS)   thats why, i simply want to restart everything)


So can i simply delete the ubuntu partion,   and re do the dual boot?  or will the Grub crash?  and i have to Fix it first ?

Thanks

---

### Post by sudodus on 2014-05-25
Since you boot from another drive (a CD/DVD/USB drive) when you install Ubuntu, you are not depending on grub in the internal drive. So during the installation, select something else at the partitioning page, select the same partition as before for Ubuntu and format the partition.

Good luck :-)

---

