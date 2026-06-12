---
title: "Dual Boot with NTLDR"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by Jonthenet on 2007-02-12
Finally decided to install Ubuntu, without losing my XP (yet). I have a Dual Core Intel Proc. so I'm using the 64-bit version.

Four HDD:
- 74GB (MBR) with currently XP on it (NTFS)
- 2 x 400GB in RAID mirror (NTFS)
- 1 x 400GB for Ubuntu

I wish to use NTLDR to choose between XP and Ubuntu. When I attempt to install Ubuntu I don't see my 74 GB drive (not that it should be of any importance). Installing on my fourth HDD doesn't pose any problems.

How do I set NTLDR up to add an entry for Ubuntu?

Thanks

---

### Post by confused57 on 2007-02-12
Here's one way:
[http://ubuntuforums.org/showthread.php?t=56723](http://ubuntuforums.org/showthread.php?t=56723)

---

### Post by Jonthenet on 2007-02-12
Thanks for the link. I don't have a floppy drive (unfortunately).

I would need two USB keys (I only have one with 256MB) to copy the boot.lnx on it, it seems. 

Any easier directions? Each poster seems to have a different way of working it out, with several installations. Trying to minimize time/risks when installing Ubuntu.

Thanks!

---

### Post by confused57 on 2007-02-12
See the reply by "Indras" in this thread, looks relatively easy:
[http://www.ubuntuforums.org/showthread.php?t=236846&highlight=ntldr+boot](http://www.ubuntuforums.org/showthread.php?t=236846&highlight=ntldr+boot)

---

### Post by Jonthenet on 2007-02-12
What Indras seems to do is install GRUB on the MBR then reset the MBR so that it uses NTLDR. Is that correct? Before I reset the MBR, Grub will be used to boot to XP or Ubuntu?

In any case, the problem is that I don't have a floppy to boot from, so I can't run fdisk /mbr from DOS.

---

### Post by confused57 on 2007-02-13
Since I've never used the Windows ntldr to boot Linux, I'm not really qualified to give you any specific instructions.

The Super Grub Disk can boot Windows or Linux, as well as, restore the Windows mbr or Linux grub(it's only a 500 kb download):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

If you can set your bios to boot first to your drive that you want to install Ubuntu on, you could install Ubuntu & use grub to boot Windows, without installing grub to your Windows mbr...similar to what's described here:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

This would require that you set this drive to boot first before installing Ubuntu, and leave your system set that way...if Ubuntu crashes(not likely), you can just set your bios to boot your Windows drive first, until you can resolve boot issues with Ubuntu.

You might want to boot up the live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
The -l is a small "L".

I'm not familiar with RAID, so Ubuntu may show it as one drive?

---

### Post by Jonthenet on 2007-02-13
Thanks for your response. I attempted an install on my fourth HDD (the one for Ubuntu). Install went ok (it created two partitions I believe, one Swap and one EXT3) - I left it as proposed by the installation program. As I restarted my computer (with my fourth HDD set as 1st drive to boot from) I get "Error loading operating system". What did I do wrong in the installation ?

---

### Post by confused57 on 2007-02-13
> **Jonthenet said:**
> Thanks for your response. I attempted an install on my fourth HDD (the one for Ubuntu). Install went ok (it created two partitions I believe, one Swap and one EXT3) - I left it as proposed by the installation program. As I restarted my computer (with my fourth HDD set as 1st drive to boot from) I get "Error loading operating system". What did I do wrong in the installation ?

Does Windows boot if your Windows drive is selected as the first boot device?  If it does, then grub wasn't installed on your Windows mbr.

Boot up the live cd and post the output of:
```
sudo fdisk -l
```
as described in my previous reply.

Did you have the drive you were installing Ubuntu on set in bios as the first hard drive booted before you installed Ubuntu?

If the Windows drive boots Ok from Windows bootloader, you could try reinstalling grub, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub)

For example, if "find /boot/grub/stage1" shows root (hd0,0), then use "setup (hd0)", as described in the link.

Before you try reinstalling grub, you might want to post the output of "sudo fdisk -l".

---

### Post by Jonthenet on 2007-02-13
Can I download a live cd for 6.10? I currently have the alternate version (amd64). I don't seem to be able to run it 'live'. Am I missing something?

Grub was not installed on MBR, windows runs fine.

---

### Post by confused57 on 2007-02-13
> **Jonthenet said:**
> Can I download a live cd for 6.10? I currently have the alternate version (amd64). I don't seem to be able to run it 'live'. Am I missing something?

Grub was not installed on MBR, windows runs fine.

Glad to hear that your Windows drive wasn't affected.
The Desktop install cd is the live cd, find a mirror nearest to you by clicking on the "Download" link in the upper right:
[http://www.ubuntu.com/](http://www.ubuntu.com/)

It's really best to run the live cd, before actually trying to install Ubuntu...that way you'll determine if there may be any hardware incompatibilities with your system...if the 64-bit version doesn't run acceptably, you may want to try the 32-bit version.

---

### Post by Jonthenet on 2007-02-13
Thanks for the explanation and time. I will start downloading it now. Once I run the live cd, will I be able to install it on my /dev/sdc (the Ubuntu HDD), without affecting the MBR?

I just ran a shell from the install and  ran fdisk -l:

```

/dev/sdc1  boot   248976 blocks  System: linux
/dev/sdc2           390459825 blocks System: Extended
/dev/sdc3           6032376 blocks System: Linux swap / Solaris
/dev/sdc6           384427386 blocks System: Linux LVM
```

Just thought I'd give out that bit of information before downloading Live CD.

PS: I think I may be able to copy the boot.lnx file to an SD card (I seem to be able to emulate it as a HDD in my bios)

---

### Post by confused57 on 2007-02-13
> **Jonthenet said:**
> Thanks for the explanation and time. I will start downloading it now. Once I run the live cd, will I be able to install it on my /dev/sdc (the Ubuntu HDD), without affecting the MBR?

I just ran a shell from the install and  ran fdisk -l:

```

/dev/sdc1  boot   248976 blocks  System: linux
/dev/sdc2           390459825 blocks System: Extended
/dev/sdc3           6032376 blocks System: Linux swap / Solaris
/dev/sdc6           384427386 blocks System: Linux LVM
```

Just thought I'd give out that bit of information before downloading Live CD.

PS: I think I may be able to copy the boot.lnx file to an SD card (I seem to be able to emulate it as a HDD in my bios)

Yes, you can designate where to install grub with the live cd...were you able to access your Ubuntu install to post the output of  the above command?  Copying the boot.lnx to an SD card may work.

---

### Post by Jonthenet on 2007-02-13
Yes, I'm running the Live cd right now. The 74GB HDD (sdh) is where the MBR is, this is where Windows is running from. sda and sdb run in RAID. These are used for apps/docs when I run windows. The last HDD, sdc, is for use by Ubuntu only. What should I attempt next?

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48640   390700768+   7  HPFS/NTFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48640   390700768+   7  HPFS/NTFS

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          31      248976   83  Linux
/dev/sdc2              32       48641   390459825    5  Extended
/dev/sdc5              32         782     6032376   82  Linux swap / Solaris
/dev/sdc6             783       48641   384427386   8e  Linux LVM

Disk /dev/sdh: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *           1        9038    72597703+   7  HPFS/NTFS

```

---

### Post by confused57 on 2007-02-13
> **Jonthenet said:**
> Yes, I'm running the Live cd right now. The 74GB HDD (sdh) is where the MBR is, this is where Windows is running from. sda and sdb run in RAID. These are used for apps/docs when I run windows. The last HDD, sdc, is for use by Ubuntu only. What should I attempt next?

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48640   390700768+   7  HPFS/NTFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48640   390700768+   7  HPFS/NTFS

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          31      248976   83  Linux
/dev/sdc2              32       48641   390459825    5  Extended
/dev/sdc5              32         782     6032376   82  Linux swap / Solaris
/dev/sdc6             783       48641   384427386   8e  Linux LVM

Disk /dev/sdh: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *           1        9038    72597703+   7  HPFS/NTFS

```

Set your Ubuntu drive in bios as the first hard drive booted, then boot up with the live cd & reinstall grub to the Ubuntu drive's mbr, using the previous link I gave or this one:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

As I mentioned, when you run:
```
find /boot/grub/stage1
```
it "should" return something like "root (hd0,0)"...hd0 is the hard drive designation and the 0 after the comma is the root partition.
you would then enter:
```
setup (hd0)
```
this will setup grub to the Ubuntu drive's mbr(hd0)

If your results are other than "root (hd0,0)", you might just want to just type in "quit", without quotes, to exit grub setup...for now.

I would still recommend that you burn a Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

just to see if SGD can boot your Ubuntu drive.

---

### Post by Jonthenet on 2007-02-13
Just to make sure I understand this correctly. I change in bios the drive to boot up then run live cd and the reinstall grub using the link you provided? at what point to I actually install Ubuntu? Sorry for the ignorance! So (hd0,0) will be /sdc then rather than /sda or /sdb because I change the boot drive in the BIOS, correct?

Thanks!

---

### Post by confused57 on 2007-02-13
> **Jonthenet said:**
> Just to make sure I understand this correctly. I change in bios the drive to boot up then run live cd and the reinstall grub using the link you provided? at what point to I actually install Ubuntu? Sorry for the ignorance! So (hd0,0) will be /sdc then rather than /sda or /sdb because I change the boot drive in the BIOS, correct?

Thanks!
No problem...my thinking was that you might be able to reinstall grub to the Ubuntu mbr, using the live cd, without actually reinstalling...by all means, make sure your Ubuntu drive is first in your hard drive boot order and if "find /boot/grub/stage1" returns something other than "root (hd0,0), just enter "quit".   Then you may need to reinstall, setting your Ubuntu drive as first hard drive booted in bios, before booting up the live cd to install.

Please, read over the links I gave you so that you understand the steps for reinstalling grub.

Added:  I have to go for now...Herman or someone else may be able to help you...I'll check back later on in several hours...

---

### Post by Jonthenet on 2007-02-13
I had actually already removed Ubuntu from my /sdc, so I will install it again (this time from Live cd). In the live cd setup I have created two partitions on my /sdc : one swap and one ext3 for /. Before the installation begins it asks me where to install GRUB - right now it is (hd0). I have looked at the GRUB page and executed find /boot/grub/stage1 but it of course doesn't exist because my HDD is formatted at this time. Is it safe to install to (hd0) ? Can I somehow ensure that (hd0) is on /sdc and not on my other HDD's ? Thanks!

---

### Post by confused57 on 2007-02-13
> **Jonthenet said:**
> I had actually already removed Ubuntu from my /sdc, so I will install it again (this time from Live cd). In the live cd setup I have created two partitions on my /sdc : one swap and one ext3 for /. Before the installation begins it asks me where to install GRUB - right now it is (hd0). I have looked at the GRUB page and executed find /boot/grub/stage1 but it of course doesn't exist because my HDD is formatted at this time. Is it safe to install to (hd0) ? Can I somehow ensure that (hd0) is on /sdc and not on my other HDD's ? Thanks!

Good timing, I just logged back onto the forums...I'm not really sure with using the live cd, but on the alternate cd, you specify by entering /dev/sdc for where you want to install grub.
I'm not sure, but I believe you can do so with the live cd, also.

If you want to try installing again with the alternate cd, at the last step, where it asks to install grub to (hd0), select "no", then on the next screen, type in **/dev/sdc**, instead of (hd0)...that way, you know that grub will be installed to the Ubuntu drive's mbr.

Personally, I've always installed Ubuntu with the alternate cd...with Breezy, that was the only way to install...I mainly wanted you to use the live cd to test for compatibility issues with your hardware, as well as having a tool to rescue Ubuntu, if the need arises.
The Desktop live cd will probably work fine, I'm just not that familiar with using it, but from what I've read from other posters, you can designate where to install grub.  I mainly don't want to give you any advice that I can't substantiate through personal experience, that could compromise your system as far as booting OS.

See Herman's reply(#13), regarding installing grub, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=342663&page=2](http://www.ubuntuforums.org/showthread.php?t=342663&page=2)

---

### Post by Jonthenet on 2007-02-13
I have attempted an install from LiveCD with installing GRUB on /dev/sdc. It seemed to go well and when I restarted (after removing the CD) I get to GRUB (which is normal I guess since I told it to install GRUB on /dev/sdc and I'm booting off /sdc) :

Ubuntu, kernel 2.6.17-10-generic
Ubuntu, kernel 2.6.17-10-generic (recovery mode)
Ubuntu, memtest86+
Other operating systems:
Microsoft Windows XP Professional

When clicking any Ubuntu I get : Error 22: no such partition
When clicking XP I get: Error 21: selected disk does not exist

Does this problem have something to do with my installation or does this have something to do with GRUB?

I now restarted my computer with LiveCD and did find /boot/grub/stage1. The response is (hd2,1). Is this correct? What should I do?

I feel we're getting a little closer to completion.

Thanks!

---

### Post by confused57 on 2007-02-13
> **Jonthenet said:**
> I have attempted an install from LiveCD with installing GRUB on /dev/sdc. It seemed to go well and when I restarted (after removing the CD) I get to GRUB (which is normal I guess since I told it to install GRUB on /dev/sdc and I'm booting off /sdc) :

Ubuntu, kernel 2.6.17-10-generic
Ubuntu, kernel 2.6.17-10-generic (recovery mode)
Ubuntu, memtest86+
Other operating systems:
Microsoft Windows XP Professional

When clicking any Ubuntu I get : Error 22: no such partition
When clicking XP I get: Error 21: selected disk does not exist

Does this problem have something to do with my installation or does this have something to do with GRUB?

I now restarted my computer with LiveCD and did find /boot/grub/stage1. The response is (hd2,1). Is this correct? What should I do?

I feel we're getting a little closer to completion.

Thanks!

You might want boot up the live cd & try the fdisk -l command again:
```
sudo fdisk -l
```

Make sure to have your sdc drive with Ubuntu as the first boot drive...are you still able to boot your Windows drive, when it is selected to boot first?

---

### Post by Jonthenet on 2007-02-13
This is what I get when I sudo fdisk -l. I'm still able to run Windows. What do you think I should modify in Ubuntu or GRUB for it to work? 

Thanks!

```
ubuntu@ubuntu:/dev$ sudo fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48640   390700768+   7  HPFS/NTFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48640   390700768+   7  HPFS/NTFS

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1275    10241406   82  Linux swap / Solaris
/dev/sdc2            1276       48641   380467395   83  Linux

Disk /dev/sdh: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *           1        9038    72597703+   7  HPFS/NTFS

```

---

### Post by confused57 on 2007-02-13
If I'm reading your fdisk output correctly, that's definitely more than enough swap space...all you really need is 1-2 Gb...don't worry about that for now, though.

You can try this:  boot up your Ubuntu drive, and at the grub menu, make sure that the entry to boot Ubuntu is highlighted, then press "e" to edit, then change the line "root (hd2,1)" to "root (hd0,1)", without the quotes...you might also want to just check the kernel line and make sure root=/dev/sdc2, then press "b" to boot...there's a list of options at the bottom of the grub screen that may help.   This change is temporary, but if it works, then you can make it permanent in your /boot/grub/menu.lst.

---

### Post by Jonthenet on 2007-02-13
It works!
How can I change this permanently? What should I modify to get XP to work from Grub? I'm tempted to just leave it like that - boot from dev/sdc every time. Any perfomance disadvantage on running GRUB from a 7200 RPM HDD rather than NTLDR from a 10000 RPM HDD?

Thanks!

---

### Post by confused57 on 2007-02-13
> **Jonthenet said:**
> It works!
How can I change this permanently? What should I modify to get XP to work from Grub? I'm tempted to just leave it like that - boot from dev/sdc every time. Any perfomance disadvantage on running GRUB from a 7200 RPM HDD rather than NTLDR from a 10000 RPM HDD?

Thanks!
Great, you can edit your menu.lst as described in this thread:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

You first change directories:
```
cd /boot/grub
```

backup your menu.lst file:
```
sudo cp menu.lst menu.lst_backup
```
menu.lst is short for menu.list

open your menu.lst in the text editor, gedit:
```
gksudo gedit menu.lst
```
it'll give you an error before the file opens, but just ignore

make the necessary changes to boot Ubuntu, i.e. the changes you made at the boot menu

To boot Windows from grub, you could actually go ahead and add a couple of entries to the very bottom of the file(after ###END DEBIAN...) & see which one works, e.g.

title              Windows XP test 1
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)   <===there's a space between (hd0) & (hd1)
map                (hd1) (hd0)
chainloader        +1

title              Windows XP test 2
root               (hd2,0)
savedefault
makeactive
map                (hd0) (hd2)
map                (hd2) (hd0)
chainloader        +1

After title, you can actually put anything descriptive here that you want...I think it's a good idea to attempt booting Windows from grub first, shouldn't be any speed issues booting.

If you want to see how grub recognizes your hard drive boot order:
```
cat /boot/grub/device.map
```

---

### Post by Jonthenet on 2007-02-14
I won't be working on any modifications for the next few days. As soon as I've implemented the change I'll be sure to post back here. In the meantime, thank you so much for your help!

---

