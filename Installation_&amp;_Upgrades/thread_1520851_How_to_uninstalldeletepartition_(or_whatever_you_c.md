---
title: "How to uninstall/delete/partition (or whatever you call it) UBUNTU?"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by joker225 on 2010-06-30
Hello, i recently installed Ubuntu 10.04 LTS, because a lot of people said it is faster and better than windows XP, so i listened to them and delited XP. 
    Now i have only Ubuntu, which I do not like. When I looked on the internet to see how to uninstall/remove/delete/partition Ubuntu I found only "Download Gnome partition editor, partition the hard disk, change it to NTFS and install Windows XP". I do not understand what that even means.
    Can someone explain to me how can i remove/delete/partition Ubuntu and install Windows XP with more details, cause i also seen posts in which they say you can't just delete the hard disk cause you can make your system unusable?

---

### Post by howefield on 2010-06-30
Have you tried the disk partitioner via the Windows installer ?

---

### Post by joker225 on 2010-06-30
When i insert Windows CD the computer does not recognize it, eventhough i have it set to boot from CD/DVD.

---

### Post by howefield on 2010-06-30
> **joker225 said:**
> When i insert Windows CD the computer does not recognize it, eventhough i have it set to boot from CD/DVD.

What, the CD ?

Where did you get the CD from ?

---

### Post by tommcd on 2010-06-30
The Windows XP install CD should be able to delete any partition, whether it is a Windows NTFS partition or a linux partition. I have used the XP install CD to delete partitions many times when I was repartitioning my hard drive.
Just use the XP CD to delete the Ubuntu partition. Then create whatever partitions you want for Windows from the XP CD.
You could also use a Parted Magic live CD to delete or reformat any partition:
[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by darkod on 2010-06-30
You can just delete ubuntu but because it's the only OS you have, what will you boot after that?
Since you plan to install XP it's better to do it at once, while installing XP you will have the option to delete all existing partitions on the disk and create new ntfs partitions.

But booting with the XP cd doesn't work for you, you have to sort out that first. That has nothing to do with ubuntu.

---

### Post by stlsaint on 2010-06-30
You also can use whatever medium you used to install ubuntu (livecd) and use it to format the partition as ntfs allowing windows to read the disk. Then boot to the windows disk and with your drive being ntfs windows will see it and you can install windows! (you sure you want to take that route?!  ( ):P )

---

### Post by WinRiddance on 2010-06-30
> **stlsaint said:**
> You also can use whatever medium you used to install ubuntu (livecd) and use it to format the partition as ntfs allowing windows to read the disk. Then boot to the windows disk and with your drive being ntfs windows will see it and you can install windows! (you sure you want to take that route?!  ( ):P )

Exactly, that's what I would have suggested too since the Ubuntu LiveCD already has Gparted built in which allows you to reformat the existing Ubuntu partition back to NTFS instead. After formatting your current Ubuntu partition back to NTFS your Windows CD should have no problem at all booting up with the computer (assuming of course that your software is proper, legal software)

Wow, I'm amazed that anyone would blindly install a new OS, [COLOR=DarkRed]**and wiping out the old OS**[/COLOR], just because someone said to do that? That's the whole reason why you have the dual-boot option which allows you to use Windows side by side with Ubuntu until you can decide for yourself after some extensive testing _over a few months of time_ which one is right/better for you.

**BTW, there is one other solution too ....**
If your Windows CD is legal and you have the installation key for it you can also install a Virtual Box from the free Ubuntu software center. Once installed you can install WindowsXP directly on top of that. If you want to use WinXP primarily then you'd just have to assign more hard disk space, ram, and graphic ram to the WinXP Virtual Box installation. Just another suggestion since you'd be the first person I'd ever heard of who didn't like the latest Ubuntu better than that 10 year old WinXP. Perhaps you just need to give it a bit more time and get used to Ubuntu before right away deciding that it's no good ... ???

---

