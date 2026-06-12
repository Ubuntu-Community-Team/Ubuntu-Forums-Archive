---
title: "How to install?"
date: 2012-03-29
forum: Installation &amp; Upgrades
---

### Post by intel 4004 on 2012-03-29
I always afraid of messing up. I tried it before, but just ended up messing the whole laptop and need to format the Harddrive and reinstall everything.
Just to make sure I'm telling everything correctly, I posted a few screenshots.

Ok. I tried the Wubi installation before and Ubuntu is great in most ways, but I heard a Wubi installation is not set to last long.

[IMG]http://i806.photobucket.com/albums/yy341/gunz207/Clipboard01.jpg[/IMG]

Ok, here is my disk management. My dad suggest me to do this. The smaller size is for the Windows 7 system. The larger one is  for junks. The healthy partition...have no idea what it is (only option is "delete volume")

My goal is to install Ubuntu on the larger partition. So...thanks

---

### Post by oldfred on 2012-03-29
You have an unusual install. It looks like g: is your primary partition that you use to boot, but the logical partition is c:.

Windows has to boot from a primary partition. Sometimes second installs of Windows are in a logical partition but they only can boot thru the first install in a primary partition.

Usually Ubuntu is installed in logical partitions as it works just fine from logical partitions.

Which partition do you want use? One is 47GB and the other is 50GB.

---

### Post by intel 4004 on 2012-03-29
I want to use the G: partition. Or should I combine the C: and G: and cut a new one?

---

### Post by oldfred on 2012-03-29
Part of the issue is that you can only have 4 primary partitions and the extended partition is one of the four. You have used 3 and Ubuntu will want 2. You could install it in just one and use a swap file instead of a swap partition. 

But you have to keep g: as a Windows partition or else you will not be able to boot. You should use Windows to shrink it but do not create partitions with Windows use gparted from Linux or the installer with manual install. Since your configuration is as it is, I do not think any of the auto installs will work other that the erase entire drive which you do not want.

If you can shrink c: by 2GB you can put swap into the extended. Your extended looks like it has only the Windows partition in it now but can have many logicals inside it.

Lots of details on installing.
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

So shrink g:, possibly shrink c: by 2GB in Windows. Then with gparted from the liveCD create a new partition that your will use a / (root) from the unallocated space next to g: (in gparted it will not be g: but sdaX where X is a number). And if you shrank c: create a 2GB logical partition and  in gparted to make it swap.

Then in the installer use the new partition you create as / (root) and format to ext4. Be sure not to use any of your NTFS partitions as that will overwrite your data. The installer will find swap automatically and the install should proceed normally.

---

### Post by intel 4004 on 2012-03-29
Is that means my Windows 7 is messed up? When I install windows 7, I choose to install on C:

So if I need to format the whole drive, how I'm suppose to do properly?

---

### Post by intel 4004 on 2012-03-29
So I did this. Is it right? Do I need to format the unallocted space. I already left 2GB more for swap.
[IMG]http://i806.photobucket.com/albums/yy341/gunz207/Clipboard01-1.jpg[/IMG]

---

### Post by oldfred on 2012-03-29
Ubuntu may not auto install to the unallocated space or you can in gparted from the liveCD create two partitions one for swap and the other will be / (root) formated ext4 when you install.

You will use all 4 primary partitions and will not be able to expand or add other partitions with this layout, but it will work.

---

### Post by intel 4004 on 2012-03-29
> **oldfred said:**
> Ubuntu may not auto install to the unallocated space or you can in gparted from the liveCD create two partitions one for swap and the other will be / (root) formated ext4 when you install.

You will use all 4 primary partitions and will not be able to expand or add other partitions with this layout, but it will work.

Couldn't wait longer, tried and it did! Installed in that partition. Yay! :p thanks for helping.

---

### Post by oldfred on 2012-03-30
Glad you have it working. 

But if you only have a Intel 4004 you may not have enough of a processor to run the 64bit version. :)

---

### Post by intel 4004 on 2012-03-30
> **oldfred said:**
> Glad you have it working. 

But if you only have a Intel 4004 you may not have enough of a processor to run the 64bit version. :)

Don't worry, I'm let my grandson, great grandson, great great grandson...to do the job. :P I just sit there and watch.

---

