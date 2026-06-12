---
title: "An idiots guide to uninstalling Ubuntu"
date: 2011-05-26
forum: Installation &amp; Upgrades
---

### Post by njrb on 2011-05-26
Hello,

I installed Ubuntu as a dual boot ages ago. I've never used it - but now I have no idea how to uninstall it - I kind of ignored it and hoped it would go away. But now I need to use the space on my HD for other stuff.

Not sure why I installed it in the first place - my mate said it was better - I'm sure he is right, but I prefer what I had to start with Vista, (sorry I'm a heathen).

Anyway, I need a complete idiots guide to get it off my PC.  As in "Step one: punch yourself for getting yourself into this mess" etc, etc.

Sorry to be a pain in the backside,

but if anyone here has the kindness in their heart to help a numpty who is out of his depth - I'd really appreciate it :D

:-({|=

---

### Post by coffeecat on 2011-05-26
Question is: did you install it in Wubi or in its own dedicated partition. Wubi is a way of installing Ubuntu in a virtual drive within the Windows C: partition.

If you have a wubi installation, simply uninstall it in the same way as any Windows app by using add/remove apps or whatever the equivalent in Vista is.

If you installed Ubuntu to its own partition, you will see a grub menu when you first boot up. You uninstall Ubuntu by simply deleting its partitions and re-using the freed space, but don't do that before you repair the Windows mbr, otherwise you'll have an unbootable system. Another question: do you have a Vista installation DVD? That's a proper Microsoft one, not an OEM restore disc. You need it to repair the mbr. If you don't, don't despair. I can post a link to a downloadable Vista repair CD which can do the job, or you can even use an Ubuntu live CD to repair the Wndows mbr. Do you still have your Ubuntu live CD?

---

### Post by Hedgehog1 on 2011-05-27
**Fix MBR:** To get your PC to boot directly into Windows again:

To make a Windows 7 / Vista emergency repair disk (in case you don't already have one made):

[IMG]http://img24.imageshack.us/img24/3200/fixmbr01.png[/IMG]

If you are unable to make a recovery disk, you can download the ISO for [VISTA]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or [WINDOWS7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Boot from the windows 7 / Vista  emergency repair disk, do the following:

[IMG]http://img848.imageshack.us/img848/1335/fixmbr02.png[/IMG]

[IMG]http://img802.imageshack.us/img802/7531/fixmbr03.png[/IMG]

[IMG]http://img803.imageshack.us/img803/530/fixmbr04.png[/IMG]

```
bootrec /FixMbr
```

---

### Post by Hedgehog1 on 2011-05-27
To remove Ubuntu:
[IMG]http://img718.imageshack.us/img718/7687/small55diskmanagement.png[/IMG]
Remove Swap Partiton
[IMG]http://img97.imageshack.us/img97/4905/small56deleteswap.png[/IMG]
[IMG]http://img231.imageshack.us/img231/2992/small57freespace.png[/IMG]
Remove Ubuntu Partition
[IMG]http://img96.imageshack.us/img96/5986/small58deleteubuntu.png[/IMG]
Remove extended Partition
[IMG]http://img848.imageshack.us/img848/8053/small59deleteextended.png[/IMG]
Expand windows partition to use all the space
[IMG]http://img3.imageshack.us/img3/7880/small61extendwin7volume.png[/IMG]


***The Hedge***

:KS

---

### Post by shahverdy on 2011-05-27
As these guys mentioned if you have installed it directly on a hard drive then you must remove linux partitions and expand your windows pastition, but you need to remove grub too, there are many tools to do that, but I recoment you download HirenCD, its a bootable CD with a lot of tools, here you can download it : 

[http://dl.asandownload.com/SoftWare/Utility/Useful_Tool/Hirens_BootCD_v13.2_Keyboard_Patch_www.AsanDownload.com.zip](http://dl.asandownload.com/SoftWare/Utility/Useful_Tool/Hirens_BootCD_v13.2_Keyboard_Patch_www.AsanDownload.com.zip)

and the password is :  [www.asandownload.com](www.asandownload.com)



for you to solve your problem, I recomend you boot from HirenCD and use a tool named paragon partition manager to remove the linux partitions and expand the windows partition, after that to fix MBR again boot from HirenCD and go to "MBR Work". fifth option is an option to install "standard MBR". by using that you can now solve your problem.

---

### Post by njrb on 2011-06-05
Hi everyone!
 
Sorry for ages to reply, been rather busy. Many thanks for all your help, I will have a proper look tomorrow when I'm off work for the first time in ages!
 
Hold tight!
Cheers,
 
Nath

---

