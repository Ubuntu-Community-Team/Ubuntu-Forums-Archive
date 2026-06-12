---
title: "partitions dual booting and problems"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by cdoublejj on 2010-03-29
i'm trying to install 98se to a 110gb partition so i can dual boot with ubuntu 10 for 98 and 100 for ubuntu after the resize. when i tried making multiple partitions manually for ubutnu putting it on separate partitions i got grub boot errors.
the problem i am having every time i try to install 98 it forces me to scandisk it then i have to hit space bar to fix every error i thinks it finds wich is impossible to press it 2 million times. now if I format in a non 98 format and tell it to format in lba it keeps asking for a boot disc, i burned one off but, still kept asking for it. if i do it in non lba, it only saw 2 gigs in 98 and when i went to install ubuntu it was a giant hard drive no partitions.  i did try making 3 fat 32s 1 for 98 and then swap and linux partition but, the i got grub errors 17 and 18.

any ideas? the problem is that bios a cap of 130gb for each drive or in this case partition. it's 320gb WD blue Scorpio. 

the short i want to dual boot 98se and ubuntu 9.04 with 2 fat32 partitions for storage 110 +100 + 80 = 320

also some visuals.

---

### Post by zvacet on 2010-03-29
If I understand you correctly you have Ubuntu and want to install Windows 98.With Ubuntu live CD shrink Ubuntu partition and unallocated space format as NTFS.The boot Windows install CD and tell it to install on NTFS.When Windows are installed you will have to [reinstall grub.]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD")

---

### Post by cdoublejj on 2010-03-29
well really i have neither on right now. any idea on what hor how to install first just looking for ideas i've been at it for days, i understand manual partition i've been playing with different ways to install with different partitions.

---

### Post by zvacet on 2010-03-30
Install windows first and give it how much space you like.On rest of unallocated space install Ubuntu using manual way.It will be good to have separate home partition.For root you don't need more then 10GB.You can give 2GB to swap and rest for home.

---

### Post by Mark Phelps on 2010-03-30
I could be wrong (it was so LONG ago ...), but I believe that Win98 is not going to be able to use an NTFS-formatted partition.  You should probably format it to FAT instead.

---

### Post by cdoublejj on 2010-03-30
you are right sir, it wil also reformat an ntfs partition during install too. you also need large disk drivers too. i installed just ubuntu on the entire drive and it maxed at 275.5gb i'm going to try an manual partition it again does the swap need to be before or after the linux partition?

---

### Post by Herman on 2010-03-30
I still have my old Windows 98 SE computer running and mine works great! Windows 98 is light and very fast when it's well defragged and it's a good combination with Ubuntu for a dual boot setup. We can use Ubuntu for the internet and avoid bogging Windows 98 down with security software which slows it down. I love watching Windows 98 defrag utility at work. It's worth having a Windows 98 install just to sit and watch it defrag.
Here are some pictures of my Windows 98 / Ubuntu rig, [Book PC Gets Big Power Supply]("http://sites.google.com/site/herman543/bookpcgetsbigpowersupply2").

Mine uses the FAT32 file system and I agree with Mark Phelps, I was not aware that Windows 98 can be installed in NTFS, I think NTFS was invented after Windows 98. There could be tricks I don't know about of to get it to work in NTFS.

One thing is for sure, it's a lot easier to install Windows 98 first and give Windows 98 the whole disk. With mine, the Windows 98 installer gives up if it detects a logical partition. 
I can't remember for sure now if I ever managed to get Win98 to install after Ubuntu by deleting all logical and extended partitions and then following an obscure Win98 installation procedure. 
I do know for sure that it is simpler to install Win 98 in an empty hard disk, then install Ubuntu.

My old computer has a 33 GB BIOS HDD size limit and no way have I managed to get this particular computer I have to work with a larger size hard disk drive.
Yours will most likely be able to though, and the way to get around the GRUB Error 18 is to install a separate /boot partition for Ubuntu somewhere inside the BIOS HDD size limit. The Linux kernel will be within range where the BIOS can see it and the Linux kernel has the drivers to map the rest of your hard disk which the BIOS doesn't know about, so you can have the rest of your Ubuntu outside the BIOS limit.

Here's my blog for GRUB Legacy about separate /boot partitions, [How to make a separate /boot partition]("http://members.iinet.net.au/%7Eherman546/p15.html#How_to_make_a_separate_boot_partition").
And here's the same thing for GRUB2,  - :shock: - !! ... oops! I don't have any GRUB2 version of how to make a separate /boot partition yet, but it shouldn't be too much different than for GRUB Legacy anyway.

---

### Post by Herman on 2010-03-30
:idea: An idea to trick Windows 98 and your BIOS might be to install Windows 98 in a different hard disk, (a small one), then use the dd command to copy it to a partition in your larger HDD.
That should work.

---

### Post by Herman on 2010-03-30
:idea: Another idea if you have a computer with plenty of RAM and CPU is to install Windows 98 inside Ubuntu in Virtual Box or VMware etc, then you can have Windows 98 and Ubuntu running at the same time! 
You can switch from Windows 98 to Ubuntu with your workspace switcher! :)

---

### Post by cdoublejj on 2010-03-31
the ghosting (copying) idea you had using the little drive is a good one. as afar a VMware we are talking 900mhz 384 mb max. You know if you use log me in or  something you can eject your cd tray from work and have some coffee  going by the time you get home.

---

