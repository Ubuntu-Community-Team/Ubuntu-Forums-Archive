---
title: "Ubuntu T60 install: Something went wrong"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by Ohwii on 2008-04-04
Hi Guys ,

I just installed Ubuntu according to this guide 

[URL="http://lifeisaventure.wordpress.com/2007/06/13/installing-ubuntu-feisty-fawn-704-on-a-thinkpad-t60/"]
 [COLOR="Orange"]1. Here[/COLOR][/URL]

and 

[[COLOR="Orange"]2. here [/COLOR](without the grub)]("http://users.bigpond.net.au/hermanzone/p3.htm")

and now I cannt get into Ubuntu. My windows works fine but my ubuntu wont start. Only a blinking courser.

well I donot know what more information to give. 

It would be good if you could help me.

Cheers 

Oh Wii

---

### Post by mikewhatever on 2008-04-04
Without GRUB? How, may I ask, were you planning to start Ubuntu without a boot loader?

---

### Post by dstew on 2008-04-04
The guide you listed gives instructions on how to multi-boot Windows XP and Ubuntu using the Windows boot system. You can do this, but it is difficult. The linked page on how to create the ubuntu.bin file has an error. It has you entering Linux commands on the command line of a Windows System Rescue CD, which will not work. You have to use the command line from an Ubuntu Live CD. Did you get this far?

To which partition did you install the grub boot loader? If you install grub to the wrong partition, it will not work. Did you successfuly create the ubuntu.bin file to put into the Windows root directory?

Is there a specific reason you want to use the Windows boot system to boot Ubuntu, instead of using grub?

Anyway, to debug your Windows boot problem, post the contents of a directory listing of your Windows root partition, and the contents of your Windows boot.ini file. And, from an Ubuntu Live CD boot, open a terminal and enter the command```
sudo fdisk -l
```Post the output.

---

### Post by Ohwii on 2008-04-04
Hi (i assume ) Drew,

Well first of all thanks for the help. I really appreciate it. 

Ok to your first question:
> **dstew said:**
>  You have to use the command line from an Ubuntu Live CD. Did you get this far?

yes I did it. I typed while running the ubuntu liveCD in the terminal   

```
# sudo dd if=/dev/sda3 of=/mnt/share/ubuntu.bin bs=512 count=1
``` 

I copied the ubuntu.bin into my Window-root drive. In this case C:\

> **dstew said:**
>  To which partition did you install the grub boot loader? If you install grub to the wrong partition, it will not work. 

Well I gues installed it on 

```
(hd0,1)
```
according to 
> 
In the next screen after you select NO to install GRUB on MBR, you are asked to enter the partition to install GRUB. You should type (hd0,1) to indicate first hard drive and second partition (the Ubuntu partition). If you have multiple hard drives, you need to figure this out by yourself. DO NOT use the /dev/sda3 option as indicated on the screen. That does not work. If you do that, GRUB will be install onto the MBR.

> **dstew said:**
> Did you successfuly create the ubuntu.bin file to put into the Windows root directory?

I answered it earlier 

> **dstew said:**
> Is there a specific reason you want to use the Windows boot system to boot Ubuntu, instead of using grub?

yes the reason is as follows 
> 

if you load GRUB on the MBR,

1) the ThinkVantage button will not work

2) the backup and rescue partition on the Thinkpad is lost.

If you dont care about the above two, you can load GRUB on the MBR and the installation becomes much simpler - you can just follow the standard installation procedure for Windows dual boot.


Let me make clear that I CAN chose between Ubuntu and XP. And XP is running the only problem is that I cannot get into Ubuntu. my machine just freezes after i chose ubuntu :(

again. Thanks for the help. 

for ```
 sudo fdisk -l 
```
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2456    19727788+   7  HPFS/NTFS
/dev/sda2            9140        9729     4732560   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3            2457        7805    42965842+  83  Linux
/dev/sda4            7806        9139    10715355    5  Extended
/dev/sda5            7925        9139     9759487+   b  W95 FAT32
/dev/sda6            7806        7923      947772   82  Linux swap / Solaris

Partition table entries are not in disk order
``` 

boot.ini

```

[boot loader ]
default=multi(0)disk(0)rdisk(0)partition(1)\windows 
[Operating systems]
multi(0)disk(0)rdisk(0)partition(1)\windows="microsoft Windows XP Professional" / noexecute=optin /fastdetect
C:\ubuntu.bin="Ubuntu Linux" 


```
Ok I still donot know what to do but it would be great if you could have a second look.

Cheers 

Oh Wii

---

### Post by dstew on 2008-04-04
If you installed grub onto (hd0,1), but made your ubuntu.bin file from /dev/sda3, there is your problem. According to fdisk, /dev/sda3 is your Linux partition, but (hd0,1) is your Compaq Diagnostic partition. So, your ubuntu.bin file probably has garbage in it, and not the grub boot loader.

(hd0,2) is probably the same as /dev/sda3. All you need to do is reinstall grub into (hd0,2), then make your ubuntu.bin file using the same command you did before. To install grub there, boot a live CD, open a terminal, and enter **sudo grub**. That should get you the grub command line with the **grub>** prompt. At the grub> prompt enter these commands:```
root (hd0,2)
setup (hd0,2)
quit
```Then, make your ubuntu.bin again. Hopefully it will work now.

---

### Post by Ohwii on 2008-04-04
Hi stew,

it works like a charm :popcorn:

many, many thanks. 

I will now update some software.

thanks, Stew

Oh wii

---

