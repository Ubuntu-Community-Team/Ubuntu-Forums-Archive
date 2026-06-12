---
title: "HP ProBook 4510s Partition Problem"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by xpfenech on 2010-02-10
My first post: :p

Thread: I just bought a HP notebook. I have installed Windows 7 and do not want to uninstall it to intall UBUNTU. This could be easily solved by partition of disk but when trying to do an extra partition for UBUNTU it says: "Not possible to do more than 4 partitions". 
It occurs with windows and with UBUNTU. The space prepared to install UBUNTU says: "UNALLOCATED" 

I actually have four partitions: SYSTEM, C:/, HP RECOVERY in NTFS and HP TOOLS in FAT32. They all look important, so:

How do I add an extra partition for UBUNTU? 
:guitar: ):P :guitar: 
Thank you

---

### Post by shriramrs31 on 2010-02-10
It seems the partitions you have are primary partitions. You can have a maximum of 4 primary partitions only. If you want more, you have to choose the one partition as secondary and make several logical partitions in it.

Usually we choose the last partition to contain all the logical paritions. 

Before I make a suggestion for your problem, can you list the sizes and physical order of all these partitions ?

---

### Post by darkod on 2010-02-10
> **xpfenech said:**
> My first post: :p

Thread: I just bought a HP notebook. I have installed Windows 7 and do not want to uninstall it to intall UBUNTU. This could be easily solved by partition of disk but when trying to do an extra partition for UBUNTU it says: "Not possible to do more than 4 partitions". 
It occurs with windows and with UBUNTU. The space prepared to install UBUNTU says: "UNALLOCATED" 

I actually have four partitions: SYSTEM, C:/, HP RECOVERY in NTFS and HP TOOLS in FAT32. They all look important, so:

How do I add an extra partition for UBUNTU? 
:guitar: ):P :guitar: 
Thank you

If you just now installed win7, I would suggest to reinstall it before you start loading a lot of software and data on it.
You don't need to cancel having win7.
The SYSTEM partition you named, is this the 100MB boot partition that is created by win7 installer? If it is, it is absolutely useless and it's just making you have one partition less for other stuff. As you noticed, it can be important.

If I'm right about the above, I would suggest: Boot with ubuntu cd, Try Ubuntu option and open Gparted. Delete both the SYSTEM partition and the C: partition. In that space, again using Gparted, create a single ntfs partition for win7. Execute the commands in Gparted with the green button.
Then boot with win7 dvd and install it on the ntfs partition you prepared. Because it already has existing partition it will NOT try to create the 100MB partition this time.

So you will end up still having win7 in the same space, and a total of 3 partitions so you can install ubuntu in the unallocated space you have set aside that you mentioned.

---

### Post by xpfenech on 2010-02-10
I have:

**Partition    Type  Size   STATUS  Pri/Log USED UNUSED**

\system      NFTS  300 MB system primary  260 39
c:           NFTS  279 GB boot   primary  242 37
HP RECOVERY  NFTS  15  GB none   primary  7.8 7.18
HP_TOOLS     FAT32 2   GB none   primary 82MB  1.9GB

I do not want to unisntall Windows 7 because I have installed thing on it that are important and do not know if I could reinstall them again without much effort.

If I can have only 4 primaries, then, only solution seems to merge them. For instance, HP RECOVERY and system or C.

1: Would it affect recovery or system or C?
2: How to do it?

:popcorn::lolflag:

---

### Post by darkod on 2010-02-10
As far as I know, you can't merge partitions. You can only resize them making them smaller/bigger. Of course, you can make a partition bigger only if you have unallocated space next to it.

What do you have on your recovery partition? You said you installed win7. Which means it didn't come with the laptop. Usually the recovery partition would have the image of the OS that came with the laptop. If that was vista for example, and you are using win7 now, you don't need that 15GB recovery partition any more because it would only be able to recover vista back on your computer. And in the process it would probably destroy all your data in windows and the whole ubuntu install.

Think about it, and also if you are nervous about all of this, maybe ask a friend who knows more to come over and help you out looking at those partitions and try to figure out if you need them at all.

I'm 99% sure you don't need them any more, both the HP RECOVERY and HP TOOLS partitions. But the decision whether to keep them is yours. This is only my opinion and I can't be 100% sure without even seeing the laptop.

PS. You asked if handling partition would affect C:. Yes, while working with partitions there is always some risk, usually low level of risk, but it exists. You should always have a backup of any important data.

---

### Post by xpfenech on 2010-02-10
Thanx for the info. I did not explain myself well, Windows 7 came with the laptop and I installed office, and yes, the problem are these HP "things" wich actually need 2 partitions. 

So, If all the partitions came with the laptop, what's the path to follow?:-({|=](*,):-({|=

---

### Post by darkod on 2010-02-10
If you have a manual for your computer, read about this recovery partition. In most cases, when doing such a recovery, those partitions are designed to wipe the whole hdd and create the same setup as from factory. This would be explained in the manual, at least it should be.
If that is the case, that partition is worthless for you, because if win7 get corrupted and you use the recovery partition, it would not only wipe ubuntu but also any windows data you have not just on C: but on any other ntfs partition on the hdd. Is that the recovery you want?

Win7 has in control panel a Backup&Restore tool. It allows you to create startup cd which you can use to boot from and restore your win7 from an image you made with this Backup&Restore tool. You keep this image on external hdd for example. So you just boot with the startup cd and restore from the image on the ext hdd. Once in a while you create new updated image and you can easily return win7 to how it was the last time you made the image, WITHOUT affecting any other partitions or OSs on the hdd.

In your place, I would create this cd and image, and delete HP RECOVERY partition because I don't need a "recovery" which will wipe my hdd. Most people keep it only because they never receive win7 dvd so they can reinstall if needed, and the above tool allows you to overcome that obstacle. Plus you can use the 15GB freed by deleting it.

That is what I would do, the way I think. You should consider all options and do what ever you think is best. :)

PS. Read more information about the B&R tool and how to create image of your whole C: so you can restore everything back. Not just a part of win7.

---

### Post by Leophys on 2010-02-15
> **darkod said:**
> 
In your place, I would create this cd and image, and delete HP RECOVERY partition because I don't need a "recovery" which will wipe my hdd. Most people keep it only because they never receive win7 dvd so they can reinstall if needed, and the above tool allows you to overcome that obstacle. Plus you can use the 15GB freed by deleting it.


Hi.
I have the same partition problem and, as I red on hp website, they suggest to remove the recovery partition (only after the creation of a set of restore disks) to install "other operating systems". Furthermore, I thought to delete the HP_TOOLS partition, but exploring it I found a *.efi file: it's a high level BIOS part, as I red on wikipedia ([http://en.wikipedia.org/wiki/Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Extensible_Firmware_Interface)). A friend (an electronic engineer, not fool at all) deleted that partition from a hp laptop whose cooling system broke down after a while.

Anyone knows the meaning of this mess? Should I really delete the recovery partition?

Thanks for the help

---

### Post by darkod on 2010-02-15
> **Leophys said:**
> Hi.
I have the same partition problem and, as I red on hp website, they suggest to remove the recovery partition (only after the creation of a set of restore disks) to install "other operating systems". Furthermore, I thought to delete the HP_TOOLS partition, but exploring it I found a *.efi file: it's a high level BIOS part, as I red on wikipedia ([http://en.wikipedia.org/wiki/Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Extensible_Firmware_Interface)). A friend (an electronic engineer, not fool at all) deleted that partition from a hp laptop whose cooling system broke down after a while.

Anyone knows the meaning of this mess? Should I really delete the recovery partition?

Thanks for the help

For the Recovery part you can delete it after creating the set of DVDs. There was another thread about HP laptop where the person even asked HP Support and they told him to delete it after creating the DVDs. He also deleted the HP Tools partition, I don't know if anything will brake down later. :) But he was happy, ubuntu installed just fine after that.

It's strange to have a BIOS file on the hdd, usually the BIOS is just a chip and hold all the info inside it. Yes, there can be files to restore or flash a BIOS, but nothing the BIOS would regularly use from the hdd. At least I haven't heard of it but it all depends how HP designed it.

At least it's sure you can delete the Recovery part and that will allow you to install ubuntu because the installer installs it inside one single extended partition, so deleting only one from the 4 you have is enough.

---

### Post by picot_negre on 2010-02-28
Hi all,
I was in the same situation one week ago, with a new hp probook 4510s windows 7 "from factory", and all these strange partitions already, but I wanted to install some linux OS without losing windows. Finally, after reading this thread and many others, decided to delete HP_RECOVERY and HP_TOOLS partitions and could install kubuntu. 
 
and by now everything works ok!! :-)
 
so thanks! the existence of all these threads are very helpful ^^

---

