---
title: "&quot;GRUB will be installed to&quot;... hd0?"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by lefty on 2006-10-30
I currently have a Windows XP installation and intend to have a dual-boot installation with Ubuntu 6.10. I have the following partitions:

80GB HDD (master)
hda1 Windows XP (NTFS)
hda5 NTFS
hda6 NTFS
hda7 NTFS

40GB HDD (slave)
hdb1 ext3 (yet to be formatted)
hdb2 linux-swap (yet to be formatted)
hdb3 NTFS

I've reached the last step of the installation where it says 'GRUB will be installed to (hd0)', and '(hd0)' being the default value. Should I leave it as it is, or should I change it to '(hda1)' or something else completely different? I've searched the forums but couldn't find an answer to this ](*,) .

Thanks in advance.

---

### Post by wieman01 on 2006-10-30
"hd0" is correct. That refers to the MBR (master boot record) of "hda1" (numbering is a bit different) whereby "hda1" is the partition on which Windows resides in your case. It's correct to install it there.

---

### Post by mozetti on 2006-10-30
GRUB uses a different numbering scheme than Linux. hd0 in grub = hda in Linux, hd1 in grub = hdb in Linux. What the default is saying is that GRUB will be installed to the Master Boot Record (MBR) of your Master HDD (hd0/hda). The MBR isn't an actual partition on the HDD, it's a bit of space at the very beginning. The alternative is to create a seperate /boot partition and install GRUB there.

That's about as far as I can go because I'm still learning, and I've always just used the default GRUB installation method.

**EDIT** And looks like I was beat to the punch. :D **/EDIT**

---

### Post by wieman01 on 2006-10-30
> **mozetti said:**
> **EDIT** And looks like I was beat to the punch. :D **/EDIT**
I am simply typing much faster than you, mate. :-) I think he has got the idea now.

---

### Post by lefty on 2006-10-30
Thanks a lot for the quick replies, wieman01 & mozetti, really appreciate it. :-D

---

### Post by wieman01 on 2006-10-30
> **lefty said:**
> Thanks a lot for the quick replies, wieman01 & mozetti, really appreciate it. :-D
Have fun with Ubuntu. You'll love it. It's highly addictive. We're all Ubuntu-junkies in here if you know what I mean.

---

### Post by lefty on 2006-10-30
> **wieman01 said:**
> Have fun with Ubuntu. You'll love it. It's highly addictive. We're all Ubuntu-junkies in here if you know what I mean.

I am already having fun with it and loving it! I use it at work (Dapper Drake), so I'm pretty familiar with it but I never came across this particular question before (about hd0) so yeah I was pretty stumped. Anyway, thanks again!

---

### Post by gn2 on 2006-10-30
Bear in mind that after kernel upgrades and / or re-installing / removing OS, you may need to do some grub editing.

Also with Grub in the MBR you may not be able to boot XP at all if Grub needs editing.

This is how I would have advised you to proceed:
[http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by Herman on 2006-10-30
Grub updates itrself automagically when a new kernel is installed for Ubuntu during an update, so don't worry about that.
If you ever need to re-install or add another Ubuntu or Linux operating system, Grub can be re-installed. 

If you re-install Windows it will install it's bootloader code in your MBR without asking. If you ever need to do that, it's easy to fix, you just re-install Grub. There are many ways to do that. The easiest is with a [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php"). 
However, if you use Ubuntu for all your internet browsing, and preserve your Windows for non-internet use, you will immediately notice that spyware and adware scans in Windows will all come up blank.
If you use Evolution for receiving email, you can prevent Windows from the possibility of receving a virus. Therefore, it is possible that you will never need to re-install Windows ever again, because Ubuntu can do all the hard work with ease, thus sheilding and protecting your Windows installaion. However, as you learn Ubuntu, you will find fewer and fewer reasons to bother booting Windows, as Ubuntu is much better.

Grub is simple for most people to edit and even customize. Here is a web page that is relevant to Ubuntu users, [GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm"). I think it is explained in simple enough terms, so most new people should be able to understand it easily. It even has lots of illustrations to make sure.

Regards, Herman :D
> **A Quick Guide to Grub's Numbering System  **[FONT=Bitstream Vera Sans Mono]
     [/FONT][FONT=Bitstream Vera Sans Mono]                                                 
    [/FONT][FONT=Bitstream Vera Sans Mono]floppy disk drive = (fd0)[/FONT]
    [FONT=Bitstream Vera Sans Mono][B][FONT=Bitstream Vera Sans Mono][FONT=Bitstream Vera Sans Mono]First hard drive = (hd0)  
    second hard drive = (hd1)
      third hard drive= (hd2) ... and so on.
[/FONT]
     [FONT=Bitstream Vera Sans Mono]                                                 first partition on first hard drive = (hd0,0)    = /dev/hda1 in Linux (or /dev/sda1 in Linux if you have an SCSI or Sata disk).[/FONT]
     [FONT=Bitstream Vera Sans Mono]                                                   2nd partition on first hard drive = (hd0,1)[/FONT][FONT=Bitstream Vera Sans Mono]    = /dev/hda2 in Linux[/FONT]
    [FONT=Bitstream Vera Sans Mono]  3rd partition on first hard drive = (hd0,2)[/FONT][FONT=Bitstream Vera Sans Mono]    = /dev/hda3 in Linux[/FONT]
    [FONT=Bitstream Vera Sans Mono]  4th [/FONT][FONT=Bitstream Vera Sans Mono]partition on first hard drive = (hd0,3)[/FONT][FONT=Bitstream Vera Sans Mono]    = /dev/hda4 in Linux[/FONT]
    [FONT=Bitstream Vera Sans Mono] 
    [/FONT][FONT=Bitstream Vera Sans Mono]first partition on second hard drive= (hd1,0)[/FONT][FONT=Bitstream Vera Sans Mono]    = /dev/hdb1 in Linux[/FONT][FONT=Bitstream Vera Sans Mono]          
      2nd partition on second hard drive= (hd1,1)[/FONT][FONT=Bitstream Vera Sans Mono][FONT=Bitstream Vera Sans Mono]    = /dev/hdb2 in Linux[/FONT][FONT=Bitstream Vera Sans Mono]         
      3rd partition on second hard drive= (hd1,2)[/FONT][FONT=Bitstream Vera Sans Mono]    = /dev/hdb3 in Linux[/FONT]
     [FONT=Bitstream Vera Sans Mono]4th [/FONT][FONT=Bitstream Vera Sans Mono]partition on [/FONT][FONT=Bitstream Vera Sans Mono]second hard drive= (hd1,3)[/FONT][FONT=Bitstream Vera Sans Mono]    = /dev/hdb4 in Linux[/FONT][FONT=Bitstream Vera Sans Mono] 
    
     [/FONT][FONT=Bitstream Vera Sans Mono]                                                 Grub makes no distinction between sda and hda drives[/FONT][/FONT][/FONT][/B][/FONT] We can install Grub to (fd0), which means to install it to a floppy disk.

Normally, the most popular and standard location to install Grub to is (hd0), which means the first hard disk's MBR. 
Grub actually lives in the Ubuntu partition, but a small 'IPL' (pointer), for Grub is written to the MBR The MBR is in the first sector of the hard disk.

If you have more than one hard disk, it is also quite alright to install Grub's 'IPL' (pointer), to some other non-first hard disk, such as (hd1), (hd2) and so on. Normally the BIOS will only look to the MBR of (hd0) when booting unless you do something like press your F8 or F12 key during boot-up.

Another place to install Grub of Lilo is to your first sector of your Ubuntu partition. Then it can be chainloaded by a boot manager, such as [GAG]("http://users.bigpond.net.au/hermanzone/p12.htm"). To do that, you need to know which is your Ubuntu partition,you find that out by looking with a 'sudo fdisk -lu' command, or with GParted. If your Ubuntu partition is (hd0,1) then you can install Grub to (hd0,1).

DO NOT EVER try to install Grub to a Windows partition (boot sector). [-(
 The Windows partition is (hd0,0) in 90% of computers. You should check first by looking with GParted or with the 'sudo fdisk -lu' command. Grub is not useful there and it will damage your Windows installation. 
Most of the time you will not be able to anyway, you will receive an error message if you try.  I always recommend people use the [grub shell]("http://users.bigpond.net.au/hermanzone/p15.htm#GRUB_shell") method to install Grub, it is safer. The grub-install command is not so safe for new users, as some people are not aware of the difference between an MBR and a boot sector.  Never install Grub to (hd0,0) if that is your Windows partition.
(hd0), the MBR, is a good place to intall Grub, but the Windows partition, (hd0,0) is not a good place for Grub, if that is your Windows partition.

Regards, Herman :D

---

### Post by lowracer on 2006-11-17
So I installed Edgy and manually edited my partition table to have a / partition 8GB, a /home partition (450GB), and a swap (2.7GB) partition.

Install went fine but when I went to boot, it did not load grub.  Instead tried to run some sort of Intel boot loader (it's an intel motherboard).  This of course did not work.

So I tried to reinstall Edgy, noticed that grub wants to be in hd0 but I only have /sda drives.  Why wouldn't grub work if it was installed in hd0?  I am now trying to install grub in sda1.  

What do I do next?  Edgy installs grub just fine if I let it erase the whole drive to one partition, but I've got to have a separate /home partition.

---

### Post by Bartender on 2006-11-17
low - 
Take another look at herman's comments.  GRUB doesn't make any distinction between sda & hda.

---

### Post by technogeeky on 2007-05-22
> **Bartender said:**
> low - 
Take another look at herman's comments.  GRUB doesn't make any distinction between sda & hda.


I just want to make the distinction - if someone got here along the same lines as I did:

grub [/b]does[/b] make a distinction between sda & hda using an internal map (see /boot/grub/device.map) that maps devices to "disks".

---

### Post by Herman on 2007-05-22
Hmmm, well if that's the case then how would you explain what happens when you are booting  using [Grub's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") from a Grub CD or floppy disk? :D  A Grub CD or floppy disk can be used to boot up any computer without needing a device map file. Would need to tell Grub if it's an IDE or an SCSI disk you are trying to boot? :D I just type something like (hdx,y), to tell Grub which disk it is I want to boot. Therefore I don't think Grub makes a distinction (in Grub's numbering system) between SCSI disks and IDE hard disks. :D
Regards, Herman :D

---

