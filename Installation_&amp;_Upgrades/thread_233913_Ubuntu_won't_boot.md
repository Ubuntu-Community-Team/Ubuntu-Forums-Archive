---
title: "Ubuntu won't boot"
date: 2006-08-10
forum: Installation &amp; Upgrades
---

### Post by david_1982 on 2006-08-10
I'm having some real problems booting into Ubuntu - everything installed fine, but I don't know where GRUB was installed (I didn't get the option of choosing where it went).

I have three hard drives, set up as follows:

SATA hard drive:
/dev/sda1 - NTFS (Windows XP)

IDE hard drive 1:
/dev/hda1 - NTFS (personal data in Windows)

IDE hard drive 2:
/dev/hdb1 - ext3
/dev/hdb2 - (extended partition)
/dev/hdb5 - linux-swap

Windows XP is installed on /dev/sda1 and is listed as the first hard drive to boot off in BIOS. Ubuntu created the partitions on /dev/hdb.

I've tried to reinstall GRUB using the following instructions:

[LIST=1]
[*]Boot with Live CD
[*]As root, mkdir /mnt/ubuntu
[*]Look up my Ubuntu partition with fdisk -l; I get /dev/hdb1
[*]Mount Ubuntu with mount /dev/hdb1 /mnt/ubuntu
[*]Then run chroot /mnt/ubuntu (not too sure what this does!)
[*]Finally, run grub-install /dev/hdb1
[/LIST]

I'm not sure about the last step - what partition should I install GRUB to? Whatever I try, be it /dev/hdb1, /deb/hdb, /dev/sda1 or /dev/sda I always get the error '/dev/whatever: Not found or not a block device'. I don't understand why I get this, or what it means!

My BIOS allows me to configure the hard drive boot order (as well as the boot order of other drives), and if I set it to boot off the SATA drive first, it boots straight into Windows XP no problems.

If I change this order to IDE drive 1, IDE drive 2, SATA drive, I get the dreaded GRUB Error 17.

I've also tried to use the Windows bootloader to get me into Ubuntu, but when I select the menu option for Ubuntu all I get is a blank screen with GRUB in the corner (no errors).

I'm at a bit of a loss, and want to solve this without destruction of my Windows installation, but don't know what to try next!

Any help or suggestions would be greatly appreciated!

---

### Post by zxee on 2006-08-10
I think as far as linux goes it sees the 1st IDE drive as the boot drive.
The simplest method might be to use the live cd and from a terminal do > sudo grub-install hd0  have your bios set up with the master ide drive to boot 1st. Grub should see you windows install and create an entry for it. Even if it doesn't you can edit your /boot/grub/menu.lst by hand to get windows available from grub.

Added: Re-reading your post I see you want to install to a partition rather than the mbr. That can be done but you need another bootloader to start up from then. I don't see installing to the mbr of the 1st ide disc as a problem, but if you don't feel comfortable doing that then you can install to the root partition of the install. If you do > root from the grub prompt i.e "grub with a blank screen" it will show all the the bootable partitions in grub notation. Using the partiton grub returns from that command you can then do > setup hdx,x replace the x's with the actual values. BTW grub starts counting from 0 so hdb2=hd1,1 and a sata drive is still an "hd" usually hd2 or 4-whatever.
I've probably forgotten something here-oh yeah for a bootloader you can use with windows to access a grub installed to a partition search for smartbootloader. Hope that helps.

---

### Post by david_1982 on 2006-08-10
Thanks for the reply. I did
> 
sudo grub-install hd0

but get the error

> Could not find device for /boot: not found or not a block device

So I followed the steps above again, and when I get to the last step (this time doing grub-install hd0) I get the errror

> /dev/hdb1: Not found or not a block device

In response to your addition, I don't know if I want to install GRUB to the MBR or not! Does it make much difference?

---

### Post by randell6564 on 2006-08-10
> **david_1982 said:**
> 
In response to your addition, I don't know if I want to install GRUB to the MBR or not! Does it make much difference?

I think that it does if you want to dual-boot.

---

### Post by confused57 on 2006-08-10
You could try reinstalling grub to hdb1 using this method:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
Edit: Should have mentioned to check out 5-HT's reply...

You might be able to boot your Windows using a mapping command(if the reinstalling grub gets Ubuntu to boot):
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

None of this may work, I'm not personally experienced with SATA drives, but it may be some options for you to explore.

---

### Post by zxee on 2006-08-10
>  /dev/hdb1: Not found or not a block device

hd0 is not the same as hdb unless you have your bios set up abnormally.
You can install to the ubuntu root partition but then you have to have another boot loader i.e smartbootmanager.

If you can still get to the grub prompt > grub>
try > find /boot/grub/stage1
then > root
take the results from root and do > setup hd?the ? to be replaced with the actual output.

---

### Post by david_1982 on 2006-08-11
Thanks for the replies! I'm at work at the moment so will have a go later on, when I get home.

One thing that I just thought of, the menu.lst file that Ubuntu created automatically does have an entry for Windows XP, which looks right (in terms of it pointing to the right drive and partition). So given that, is it safe to install GRUB to the MBR?

---

### Post by zxee on 2006-08-11
> **david_1982 said:**
> Thanks for the replies! I'm at work at the moment so will have a go later on, when I get home.

One thing that I just thought of, the menu.lst file that Ubuntu created automatically does have an entry for Windows XP, which looks right (in terms of it pointing to the right drive and partition). So given that, is it safe to install GRUB to the MBR?

Nothing is completely predictable, but based on my experiance with multibooting up to a dozen distros from one computer I'd say yes.
I don't have a windows install although I used to-it was too much trouble to maintain-really. Ubuntu IMO is very good at detecting other installations including the one from Redmond.

---

### Post by david_1982 on 2006-08-11
Thanks, I'll have a go later. I'm not totally disinclined to start again from scratch and vape Windows completely - I'm fairly disciplined in keeping my personal data on a different volume to Windows. Might be a weekend project! Will let you all know how I get on.

---

### Post by Herman on 2006-08-11
Try with a [**Super Grub Disk** : En]("http://adrian15.raulete.net/grub/"), only a 500kB free download that you can  extract and then burn to a CD. 

Super Grub disk can be used in either text based mode, it has lots of menus for selecting all the main features of Super Grub with, or you can use the Grub CLI mode from it too. 

To enter Command Line mode from a Super Grub Disk, see this thread, [http://www.ubuntuforums.org/showthread.php?t=229909](http://www.ubuntuforums.org/showthread.php?t=229909)

The following features are only a few of those available in text mode Super Grub,

'Special Boot ->Boot your Gnu/Linux (or other OS) again -> Boot Automatically -> AUTO,
This option will make SGD automatically search your computer for a partition continaing a Grub configuration file, and then boot the first operating system it finds that has one. 

'Manual Boot -> /boot/grub/menu.lst -> hdx -> hdaX
Boot the system with the non-first Grub configuration file that SGD finds. (If I wanted to boot (hd0,6) instead of (hd0,1), for example. 

[I] Also, 'Classic Boot' -> Boot MBR -> hda ' 
That would find a MBR that has a bootloader installed in it, especially this would be handy where someone installs Ubuntu in a computer with multiple hard disks and especially when IDE and SCSI or sata disks are both used, and only Windows will boot because Grub went to the non-first MBR by mistake. [/I]:D

and 'Classic Boot -> Boot Partition -> hdx -> hdaX
That would boot a partition that has a bootloader installed to the first sector of the partition. I do that as an extra method for booting, I like to [install Lilo to the partition]("http://www.ubuntuforums.org/Install%20Lilo%20from%20terminal."), and Grub to MBR as well. We can have both, so if one doesn't work for some reason (user's crazy experiments and errors for example), the other loader will still work. That method boots all my operating systems with SGD as well. :D

If SGD won't boot your Ubuntu installation for you, then I don't know what will, but never, ever give up! 

Another very good alternative is to install Lilo (or Grub) to the first sector of your Ubuntu partition and then use GAG Boot Manager to manage your  bootloaders  for you. GAG Boot Manger is another free software download, and works for a floppy disk drive, CD, and can also be installed to MBR if you like it. For more info on GAG Boot Manager, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p12.htm")

Good luck with it, Regards, Herman :D

---

### Post by david_1982 on 2006-08-12
Okay, so I've been trying some of these suggestions, which I'm really grateful for, but I still can't book Ubuntu.

I thought I'd try and be smart and install GRUB onto my SATA drive, /dev/sd1. This gave me the GRUB menu on boot, but broke Windows. Managed to fix that with an XP bootdisk, but now when I select Windows from the boot menu, I get the error 'NTLDR missing'. Pressing any key takes me back to the GRUB menu, and weirdly if I choose Windows again it boots fine! I think I have GRUB installed twice now (once on /dev/sda1 and another on /dev/hdb1 - is this possible? If so, how do I check and remove one of the instances?)

Selecting Ubuntu from the GRUB menu gives me Error 17. I've Googled this error, but don't seem able to find any ways to solve the problem!

I'm going to try Super Grub Disk now, to see if that works. But what I really want is a GRUB that works and will boot properly.

Any further help would be appreciated!

---

### Post by Herman on 2006-08-12
david_1982, here's my new [Super Grub Disk Page]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")
just in case you need some extra info about how to use Super Grub Disk. I hope the info there will be clear enough.
Also, here's my [GRUB Page ]("http://users.bigpond.net.au/hermanzone/p15.htm"),in case there's anything there that might help.
I hope you can solve it easily, maybe it's some kind of a mapping problem.
Good Luck with it, Regards, Herman :)

---

### Post by david_1982 on 2006-08-13
Well, I don't know *how *or *why *it's working, but it is now!

I had one more try last night, and in GRUB did

```
grub> find /boot/grub/stage2
```
which reported

```
(hd2,0)
```

Now, this is /dev/sda1... my Windows partition! But I thought I'll run with this and see if it works. Edited menu.lst to point here, and hey presto it worked!

I have no idea why this works, and I still get NTLDR missing the first time I choose Windows from the GRUB menu, but I'm willing to live with that!

Unfortunately this is being posted from Windows - I'm now battling with ndiswrapper to get my wireless card working!

---

### Post by Herman on 2006-08-13
That's great! Good luck with your wireless card. I am sure you will get that fixed too if you are persistent enough.
Regards, Herman :grin:

---

