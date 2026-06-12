---
title: "Install errors with Grub to /dev/mmcblk0 ..."
date: 2017-10-17
forum: Installation &amp; Upgrades
---

### Post by Hangman_ on 2017-10-17
My first post, Wahoo !!!
Here's the situation:  Toshiba Protege (older model W7) but it's fast enough.  I bought a new SSD drive (120G) to run Ubuntu, no Dbl Booting.  I want to get as far from Windows as I possibly can, it's a corrupting parasite ... sorry, I digress.
So, fresh install on a new SSD drive using USB (16G).  I found a Ubuntu Gnome 16.04 ISO from a Canonical affiliate < [https://ubuntugnome.org/download/](https://ubuntugnome.org/download/) > & have used it on an HP laptop without a problem.  I've also used the Ubuntu 16.04 from Canonical < [https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop) > on two other HP laptops & desktop without any hickups what-so-ever.
I run through the setup phase all the way to the end of the hardware configuring & it wants to finish loading any excess files & then I get "Unable to install GRUB in /dev/mmcblk0".  This is trying to access a media drive & I can't unmount the CD drive while doing a fresh install ... can I?  I did not have this problem with the desktop & there's a lot more media drives on that one.
Anyways, I get a choice of selecting a new drive to continue the install (/dev/sda or /dev/sda1), select to finish this install & install Grub manually, or quit the install altogether.
HOWEVER, I cannot make any of those choices because the install has already failed & there's no response to any of it.  I simply have to power off the machine (cold boot, power killer, the names go on)

I've tried loading the USB with Ubuntu Gnome 16.04 ISO using unetbootin & then the Startup Disk Creator, same error.  Then I figured perhaps Ubuntu Gnome doesn't like the Toshiba so I loaded the USB with Ubuntu 16.04 from Canonical using unetbootin & then the Startup Disk Creator, same error.

My research has taken me along the idea of the Toshiba locking out writing to the MBR but I don't believe this is the case.  I have access to the BIOS & cannot find anything in there to give me the impression there's area's I cannot write to.
I've stumbled across several dual boot errors with Grub not installing to /dev/sda but I cannot find any similar circumstances where Grub is erroring to /dev/mmcblk0.

Your questions / suggestions would be much appreciated, Thank you.

---

### Post by efflandt on 2017-10-18
Usually /dev/mmcblk0 is the SD card slot on a laptop, and usually you cannot boot from that unless it is internally USB connected, in which case it would NOT be /dev/mmcblk0. If you have a card inserted in that slot, remove it. If your laptop is capable of booting from that slot, check boot order in BIOS and make sure that it is far down the list if on the list at all.

Assuming that you are using BIOS, not UEFI, you may have better luck using "Other" when it gets to the partitioning part, set up the partitions yourself, and there is a dropdown list to select where to install grub, which would most commonly be /dev/sda if that is your only drive. I sometimes put grub on a partition with the boot flag moved to that partition instead of mbr on a PC with Win7 because rarely some Win7 updates fail if using grub instead of standard mbr, in which case I can temporarily move the boot flag to Windows until the update is successful. But you do not have to be concerned with that if not using Windows at all.

---

### Post by Hangman_ on 2017-10-18
Thanks for the reply & the extra info.  I'll double check my SD card slot again just to be doubly sure.  In my BIOS I have a setting for UEFI (not sure what that is) which is default so I left it there.  
Q, when creating the partitions manually, do you have suggested sizes?  I keep wondering how much I need for each (Last time I came up short, then when I tried to update it I screwed something up & lost my drive) so I usually let the install take care of it.

Q, Concerning the Ubuntu Gnome from a Canonical affiliate, I can assume it is an alpha version of what Canonical is going to in v18?  I would prefer to install it & use Gnome now just because of the route Canonical has chosen to take.  A fresh install, might as well get started on what is inevitable, right?

Thanks again.

---

### Post by oldfred on 2017-10-18
Sizes of partiitons is very personal and depends a lot on what you want or your configuration.

Several suggestions in various threads. 

 It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot. 
   For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)

---

### Post by Hangman_ on 2017-10-19
So, after learning a wealth from Efflandt & OldFred & doing some additional research on UEFI & GPT I decided I'd just use the Legacy booting option.  After setting the BIOS to such, I tried again, this time creating my own partitions according to OldFred's suggestions & ... whalla, Success.  I also researched the Ubuntu Gnome 16.04.3 & decided this was best.  Loving it even now.  Thanks guys.

---

