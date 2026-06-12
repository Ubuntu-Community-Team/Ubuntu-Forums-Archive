---
title: "Dual Boot not booting Windows 2000 inaccessibla_boot_device"
date: 2006-05-13
forum: Installation &amp; Upgrades
---

### Post by BillyPilgrim on 2006-05-13
I recently did a fresh Fedora Core 5 and found out I was unable to build an AMD64 bit version of Scilab.  I had this running on Fedora Core 4.  As a result I decided to give Ubuntu a try.  Installation went ok and Ubuntu 5.10 is running fine but I cannot no longer boot into my Windoze 2000 partition.  (Yes I still have to occaisionally use it),

The Win2000 splash screen comes but now I get the blue sceen of death with inaccessibla_boot_device error.

here is my /boot/grub/menu.lst

title           Ubuntu, kernel 2.6.12-10-amd64-generic Default
root            (hd0,1)
kernel          /boot/vmlinuz root=/dev/hdc2 ro quiet splash
initrd          /boot/initrd.img
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-amd64-generic Default (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz root=/dev/hdc2 ro single
initrd          /boot/initrd.img
boot

title           Ubuntu, kernel 2.6.12-9-amd64-generic Previous
root            (hd0,1)
kernel          /boot/vmlinuz.old root=/dev/hdc2 ro quiet splash
initrd          /boot/initrd.img.old
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-amd64-generic Previous (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz.old root=/dev/hdc2 ro single
initrd          /boot/initrd.img.old
boot

title           Ubuntu, kernel 2.6.12-10-amd64-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-10-amd64-generic root=/dev/hdc2 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-amd64-generic
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-amd64-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-10-amd64-generic root=/dev/hdc2 ro single
initrd          /boot/initrd.img-2.6.12-10-amd64-generic
boot

title           Ubuntu, kernel 2.6.12-9-amd64-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/hdc2 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-amd64-generic
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-amd64-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/hdc2 ro single
initrd          /boot/initrd.img-2.6.12-9-amd64-generic
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title           Microsoft Windows 2000 Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

Now grub and win2000 worked fine under FC4 and FC6, and I can't figure out why it is not working under Ubuntu.  It was working just prior to the install of Ubuntu.

Any help would be appreciated.  I really don't want to resintsall Win2000 again if I can help it. ](*,)

---

### Post by Herman on 2006-05-13
> # This entry automatically added by the Debian installer for a non-linux OS
 # on /dev/hdc1
 title Microsoft Windows 2000 Professional
 root (hd0,0)
 savedefault
 makeactive
 chainloader +1
Is your Windows system on your first partition of your first hard drive? You didn't mention whether you had one, two or three hard drives, but this bit '/dev/hdc1' seems to imply Windows 2000 is on your third hard drive, and does not seem to match the later command 'root (hd0,0). Is it just a typo? 
If not, then try changing 'root (hd0,0)' to 'root (hd2,0)' and see if that helps.
Regards, Herman
Edit: It looks to me as if you have a seperate /boot partition as the second partition on your first hard drive and Ubuntu is partition 2 on the third hard drive, and Windows is the first. Is that the situation?

---

### Post by BillyPilgrim on 2006-05-13
[QUOTE=Herman]Is your Windows system on your first partition of your first hard drive? You didn't mention whether you had one, two or three hard drives, but this bit '/dev/hdc1' seems to imply Windows 2000 is on your third hard drive, and does not seem to match the later command 'root (hd0,0). Is it just a typo? 
If not, then try changing 'root (hd0,0)' to 'root (hd2,0)' and see if that helps.
Regards, Herman[/QUOTE]

Thanks for the reply Herman.

I only have one drive installed on IDE channel 2.  Don't ask why the machine is set up that way.  (My son builds overclocked machines and I got this one when he bought a new motherboard ... it is the original conifguration) The hard drive designators are correct for grub.  FC5 which worked produced the essential the same configuration.

I now know how the problem was created.  When Ubuntu installed it created a large primary partiiton and placed the swap file in an extended partition which was near the end of a 250 G drive.  Although I have Win2000 set up to only use a single 40 GB primary partition it obviously didn't like the way Ubuntu set itself up on the hard drive.  I reinstalled FC5 and my Win2000 was accessable again.  The only difference between the installs is that FC5 creates a small boot partition and installs itself in a LVM file system in the extended. partition.

I will try another install of Ubuntu but I won't let it automatically partition the hard disk.

---

### Post by Herman on 2006-05-13
>  FC5 creates a small boot partition and installs itself in a LVM file system in the extended. partition. That's something I'll file for future reference, thanks for letting me know about that, it's interesting. I was trying to help another FC5 /Ubuntu user two days ago and I'm not sure whether the problem there was finally solved or not. LVM is a little out of my depth and I'm not too certain about how to handle your different IDE channelling... :-k  Hmmm.

Hey, here's a link to a great website I was reading just last night on GRUB.
[http://www.troubleshooters.com/linux/grub/index.htm](http://www.troubleshooters.com/linux/grub/index.htm)
It's called 'Grub Grotto', and there are three pages linked off the home page for it, called 'Grub From the Ground Up',' Grub Special Boots and other Tips', and 'Making a Dedicated Grub Partition'.
That web-site, by Steve Litt, is a treasure-trove of good information about Grub, I highly recommend it.
In particular, there is some information on the page called 'Making a Dedicated Grub Partition', that might be relevant to you, since you have a dedicted Grub partition. Basically, it recommends when adding subsequent operating systems, not to install the new bootloader to MBR, but just to create a new entry for your new OS in the existing menu.lst in the grub (boot) partition instead.

Actually, in my new Kubunu system I'm typing to your now from, I removed the /boot/grub directory completely and all but the kernel and initial ramdisk from the /boot directory as an experiment. It booted okay from the menu.lst in my Ubuntu OS.
I was just experimenting to find out the minimum files needed to boot with. So you may not need grub at all when you re-install. You would need have your FC5 correctly edited beforehand though.  I would suggest (if you go that way), install you Lilo to your Ubuntu partition and set your FC5 grub partition to point to that maybe.
 (Interestingly, after my experiment, the removed files were replaced again by kernel upgrade during a subsequent system update). 

A simpler solution which does not require so much reading and studying is to try out [GAG Boot Manager]("http://gag.sourceforge.net/") (which also requires GRUB or Lilo installed in the OS partition or a seperate boot partition). That should boot your systems for you too. 
 Here's an extra help page I made for GAG: [http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)

I hope you find something here useful, Regards, Herman :D

Edit: PS, What would happen if you follow Steve Litt's instructions on his 'Grub From the Ground Up' page under 'Having Grub Do Your Research For You'. You should be able to use gruc from the command line and by following those instructions, access your FC5 boot partition and then boot via that. (Just an idea).

---

### Post by BillyPilgrim on 2006-05-13
Thanks for the usefull links.  I have bookmarked them for a rainy day.

The problem was definately related to the auto-partioning scheme of Ubuntu.  I reinstalled, manually partioning the drive; swap in a primary partion and ext3 / in the extended partion.  Win2000 now boots ok.

I have built a 64 bit version of Scilab 4.0 on Ubuntu so I am happy.  I just could not get it to build under FC5.  Configure kept complaining about not being able to find a TK library although it was defiinately installed. 

This is my first experience with Ubuntu.  It'll take a while for me to get use to it.  I am not completely happy with sudo this and sudo that but will give it a try.

Thanks again for your help.

---

### Post by Herman on 2006-05-13
Aha! So your logical partitions were non-contiguous, it was a partitioning problem rather than a Grub problem, now I see. :p 
I'm glad you got everything to work our for you, and thanks for letting me know how you fixed it too.
All the best and I'm glad you are enjoying Ubuntu. Regards, Herman :D

---

### Post by BillyPilgrim on 2006-05-14
[QUOTE=Herman]Aha! So your logical partitions were non-contiguous, it was a partitioning problem rather than a Grub problem, now I see. :p 
I'm glad you got everything to work our for you, and thanks for letting me know how you fixed it too.
All the best and I'm glad you are enjoying Ubuntu. Regards, Herman :D[/QUOTE]

The problem wasn't the install being non-contiguous but it was the physical location of the extended partition. Ubuntu automatically created roughly a 100 GB primary partion (hc1) and the 3 GB swap partion (hc5) in the extended partition, Win 2000 was install on a 40 GB primary partion (hc0) .  The extended partition contained only the swap file.  Win2000 couldn't handle the extended partition in that location even though it wasn't using it.

Regards .... Billy

---

### Post by N0thing on 2006-05-18
I know the problem has been solved but im having the same exact problem here. I did manual partitioning and it still doesn't work.

The layout is
/dev/hda1 40GB NTFS WIN2k
/dev/hda2 15GB ext3 ubuntu
/dev/hda3 100 GB vfat data
/dev/hda4 1 GB swap

Ive tried turning on the boot flag for both /dev/hda2 /and /dev/hda1 and im still not getting it. Grub is pretty much the same as listed however i only have two ubuntu kernels listed and win2k is the default.  Any help would be appreciated.

---

### Post by Herman on 2006-05-18
Hello, N0thing, please enter the following command into your terminal and copy the results and paste them in your next post here.  ```
$ sudo fdisk -l
```
Also I would like to see  your menu.lst,  please.
:D  Regards, Herman

---

### Post by N0thing on 2006-05-18
I think i got this figured out but the soultioun is not the most efficient. I realized that windows 2k was giving my hd as 132GB when it 160GB. My scheme was where all 160GB was used knocking it back to 132GB of 160GB partitioned makes windows boot now. However this leaves 27 GB of space unused. 

any how heres fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/hda2            5100        6923    14651280   83  Linux
/dev/hda3            6924        7045      979965   82  Linux swap / Solaris
/dev/hda4            7046       16163    73240335   83  Linux

any idea about getting windows to recognize all 160GB.

---

### Post by Herman on 2006-05-19
>  The layout is
/dev/hda1 40GB NTFS WIN2k
/dev/hda2 15GB ext3 ubuntu
/dev/hda3 100 GB vfat data
/dev/hda4 1 GB swap  (your old partitions)
>  Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, **[COLOR=Red]19457 cylinders[/COLOR]**
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/hda2            5100        6923    14651280   83  Linux
/dev/hda3            6924        7045      979965   82  Linux swap / Solaris
/dev/hda4            7046       **[COLOR=Red]16163[/COLOR]**    73240335   83  Linux

any idea about getting windows to recognize all 160GB.       . (your new partitions) 

Well, N0thing, I notice that in both your earlier partitioning arrangement and the one you have now, that you are sticking with only 'primary' partitions. (I can tell because the partition numbers are 1,2,3 and 4). We can make a maximum of four primary partitions. That's okay as long as this is all the partitions you need.  However, if you ever decide you'd like to add any more partitions than that some day though, you won't be able to do that successfully.

It looks to me like you have 19457 cylinders there that you should be able to use, and you have only used 16163 cylinders. What is it you want to do? You could re-size your /dev/hda4 partition to fill up the rest of the space.

Otherwise there is nothing else you can do without deleting your swap and /dev/hda4 and re-creating them as 'logical' partitions.  We are allowed quite a number of 'logical' partitions as long as they are all in a line end to end with one another inside an 'extended' partition. (Not seperated by a primary partition in the middle). "Contiguous" is the word for it.

If you are using the Ubuntu install partitioner, it makes an 'extended' partition automatically with the 'logical' partitions inside it. Most other partitioning software  just needs you to tell it to make an 'extended' partition first. Then you can specify the details of the logical partitions you want inside it afterwards. (An 'extended' partition is like a box for making the 'logical' partitions in.)
If you do it that way, your new 'extended' partition will probably be given the number 3, and your logical partitions will be numbered from 5 to whatever number you stop making more partitions at. There will be a note on the bottom of your sudo fdisk -l output to tell you 'your partitions are not in disk order'. That is normal, we all have that. It doesn't matter if the partitions are not listed in disk order, don't worry about it. :D 
I hope this is what you wanted to know, Regards, Herman

---

### Post by N0thing on 2006-05-20
All right thanks for the response i just did the root partition under the installer and the rest under fdisk. Anyhow my hope was just to be able to use that other 27GB but windows wont boot if its used. That is whats stumping ive tried extended partitions as well. Ill just leave it as is for now.

---

### Post by BillyPilgrim on 2006-05-21
Sorry I didn't get back to your post.  I think you pretty much have it figured out.

You should check the Micrsoft knowledge base on getting windows to recognize all 160GB.  They have a fix for it.  I can't recall from memory where exactly I found it but have successfully used it on a few machines.

.... Billy

---

### Post by Herman on 2006-05-22
> I realized that windows 2k was giving my hd as 132GB when it 160GB. My scheme was where all 160GB was used knocking it back to 132GB of 160GB partitioned makes windows boot now. However this leaves 27 GB of space unused. N0thing, I realise you said '132 GB', but could your problem possibly be anything to do with the  [137 GB Limit?]("http://64.233.167.104/search?q=cache:Hc2AhUFqrH4J:www.maxtor.com/en/documentation/white_papers/big_drives_white_papers.pdf+137+GB+limit&hl=en&gl=au&ct=clnk&cd=16")

[http://www.tldp.org/HOWTO/Large-Disk-HOWTO-4.html]("http://www.tldp.org/HOWTO/Large-Disk-HOWTO-4.html")

If this is the case, you might need some kind of [URL="http://www.ontrack.com/diskmanager/"]Disk Manager
[/URL] I am only providing that link for an example for you, not recommending any partitcular brand.  maybe try your hard disk manufacturer, they may provide a free one to suit your particular make and model of hard disk.

I am not certian whether this is even your problem or not, much less the correct solution, but it's something that might be worth some further investigation, I hope this helps you. Regards, Herman
> You should check the Micrsoft knowledge base on getting windows to recognize all 160GB. They have a fix for it. I can't recall from memory where exactly I found it but have successfully used it on a few machines.
 EDIT: On second thought, Billy's answer is probably right.

---

