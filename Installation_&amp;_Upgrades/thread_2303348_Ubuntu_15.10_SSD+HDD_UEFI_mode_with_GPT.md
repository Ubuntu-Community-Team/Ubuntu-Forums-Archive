---
title: "Ubuntu 15.10 SSD+HDD UEFI mode with GPT"
date: 2015-11-18
forum: Installation &amp; Upgrades
---

### Post by Doominq on 2015-11-18
Hello guys,
at first I would say hello, because it's my first post :)


I have some troubles with install Ubuntu 15.10 on my Lenovo Thinkpad E550.
I have two drives: SSD and HDD (instead optical drive).


I would like install OS at SSD and rest of all that means /home, swap /tmp at HDD.
So I created partitions:
SSD:
1)  EFI System Partition (ESP) with size 1024 MB
2) / (root) with size about 119 GB


HDD:
1) swap with size 8192 MB
2) /tmp with size 10240 MB
3) /home with size about 940 GB


Ubuntu would be standalone system at my laptop.
When I try do this I get message which inform me that i try to force install OS with UEFI mode, when installator has found other OS which is compatibility with BIOS mode. 
BUT I don't have any other system. All drive are clear and formatted (by GParted) at GPT.


What is more I have tried install Ubuntu 14.04.3 and everything was OK.


In BIOS/UEFI I tried turn off/on Secure boot, it doesn't change anything.


Any suggestions ?


Btw. Sorry for my english... I know that is not well polished.

---

### Post by sudodus on 2015-11-18
Welcome to the Ubuntu Forums :-)

Ubuntu 14.04.3 works well in the computer and it will be supported until April 2019.

Why do you want to install 15.10, that is only supported for 9 months?

You may need the latest and greatest

1. in a new computer to manage some new piece of hardware,

2. if you need a new version of an application program, that is only available in a newer version of Ubuntu.

-o-

Ubuntu promises support of 14.04.1 LTS until April 2019. If you start update/upgrading it to new point releases ...2, ...3, ...4, you should continue until 14.04.5 LTS, which will also be supported until April 2019. See this link

[LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

***Edit:*** It is risky to update the LTS Enablement Stack, and I would recommend installing 14.04.**1** LTS, if it works for you. Then you just do the regular updates/dist-upgrades, or via the Graphical update manager, which stays with the same 'Trusty' kernel series.

---

### Post by Doominq on 2015-11-18
Maybe you're right :) But referring to partition scheme. Do you think that everything is right ? Or Should I change something ?

---

### Post by sudodus on 2015-11-18
Keep it simple :-)

I would only have a root partition and a swap partition, both on the SSD (for speed). I have a data partition on a separate HDD, and systematically save documents, pictures, music, video-clips in the data partition. That way I can backup the personal data separately (and in a simple way). I suggest that you consider such a solution too.

If you wish, you can have a home partition in the HDD, that is also a common way to install systems. But I suggest that you avoid a separate partition for tmp.

If you boot in UEFI mode, you need an EFI System Partition (ESP), but you can let the Ubuntu installer (ubiquity) create it automatically.

---

### Post by ajgreeny on 2015-11-18
> **sudodus said:**
> Keep it simple :-)

I would only have a root partition and a swap partition, both on the SSD (for speed). I have a data partition on a separate HDD, and systematically save documents, pictures, music, video-clips in the data partition. That way I can backup the personal data separately (and in a simple way). I suggest that you consider such a solution too.

If you wish, you can have a home partition in the HDD, that is also a common way to install systems. But I suggest that you avoid a separate partition for tmp.

If you boot in UEFI mode, you need an EFI System Partition (ESP), but you can let the Ubuntu installer (ubiquity) create it automatically.
+1 ^^^
Making /tmp a separate partition is a total waste of time unless you have some unknown and specific reason for needing it, which I doubt is likely.

You already have an EFI/ESP partition for Windows, and as I understand things related to dual booting with Windows, the installer will find that automatically , so I don't think you need to add another; I think it will just confuse the system if you do.

A separate /home or data partition is certainly worth adding and there are ongoing discussions about which is the better.  I have machines which I have installed using one or other of those partitions and have to admit that a separate /home is easier to set up as there is no need to edit /etc/fstab after installing, which easy enough to do, but is another step for a new user to have to take.

Setting up symbolic links to the data folders in the data partition also is very helpful; it makes it look as if all those files are sitting in the root partition's /home folder (that's where /home will be if you have a separate data partition) when they are really taking space only in the data partition.

If all that makes no sense to you, come back for more help.
As sudodus says, "Keep it simple :-)"

---

### Post by Doominq on 2015-11-18
Thanks a lot guys. I will correct my scheme :)
But like i said I don't have any other system and I will not have. Ubuntu will be standalone. So in this case do I need to create ESP/EFI partition ? Or can I just make /(root) on SSD and /home on HDD ?

---

### Post by sudodus on 2015-11-18
If you don't want to let the installer do its job automatically, you can refer to this link

[Creating_an_EFI_System_Partition](https://help.ubuntu.com/community/UEFI#Creating_an_EFI_System_Partition)

For more information you read the next link and links from it about UEFI.

[FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

---

### Post by oldfred on 2015-11-18
If drives are gpt you need either the ESP - efi system partition for UEFI boot or a bios_grub partition for BIOS boot.

I prefer to add both to all drives and usually have at least one install on every drive. A bare install does not take much space on these newer large hard drive.
My SSD & HDD has two root partitions on SSD of 25GB each and I do not know what to do with all the extra space. But I do copy some data from each drive to the other drive.

I prefer the separate /mnt/data partition but you cannot create that during install, so it is a bit more advance. It is easier to use /home as separate partition as you can create that during install

       The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by Doominq on 2015-11-18
Guys thanks alot for your help. Every answer was very helpful.


I have solved this trouble. 
When i tried accept partition scheme I recived that message:


[IMG]http://www.tecmint.com/wp-content/uploads/2015/04/Force-UEFI-Installation-600x450.jpeg[/IMG]


At this moment my installator have been stopped and I could do anything.
I thought that it's becouse of UEFI/BIOS setup, but no...


The trouble was in option 'Download updates...'. I selected this at begining of installation and this coused the issue.


So, I'm putting this message for 'next generation'... maybe for someone will be helpful :)


Once again thanks for answers.
Cheers ;)

---

### Post by sudodus on 2015-11-19
Congratulations and thanks for sharing your solution :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by dswaugh on 2015-12-10
<<[COLOR=#000000]A separate /home or data partition is certainly worth adding and there are ongoing discussions about which is the better. I have machines which I have installed using one or other of those partitions and have to admit that a separate /home is easier to set up as there is no need to edit /etc/fstab after installing, which easy enough to do, but is another step for a new user to have to take.[/COLOR]

[COLOR=#000000]Setting up symbolic links to the data folders in the data partition also is very helpful; it makes it look as if all those files are sitting in the root partition's /home folder (that's where /home will be if you have a separate data partition) when they are really taking space only in the data partition.>>
[/COLOR]
ajgreeny: Could you please share the steps for "setting up symbolic links" to HDD data folders?  I have an SSD and an HDD, and I want to do what Dooming has done here, clean-install Ubuntu 15.10 on a 62GB ext4 partition of the SSD, but link /home to a data partition on my HDD. Can you help me, or is there an existing thread that addresses this? Thanks much.

---

### Post by oldfred on 2015-12-10
See post #8 above.
In link on splitting /home & data in post #4 oldfred has all the details you should need.

Or directly to that post:
[http://ubuntuforums.org/showthread.php?t=1811198&p=11081384#post11081384](http://ubuntuforums.org/showthread.php?t=1811198&p=11081384#post11081384)

---

