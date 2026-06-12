---
title: "Can I move the bootloader to a different partition?"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by RCC2k7 on 2007-01-27
Hello all,

This is my first post. I'm a Ubuntu newbie, though I've tried other Linux distros in the past.

I installed Ubuntu Edgy 6.10 - actually had to install 6.06 and then upgrade to 6.10 online, but that story is for a different thread. ;)

I want to keep a dual-boot setup with Windows XP Pro and Ubuntu. My hard drive is currently partitioned like this:

Windows XP Pro partition (/dev/sda1)
Ubuntu Linux ext3 (/dev/sda3)
Ubuntu swap (/dev/sda4)
Extended partition (/dev/sda2)
NTFS partition for data storage (/dev/sda5)

When I installed Ubuntu, it installed its bootloader so it overwrote master boot record on the first hard drive - in the manner typical of most Linux distros when setting up dual-boot. I'd rather have GRUB booting Ubuntu from the Linux partition sda3 instead of loading something from the first partition, because of two reasons:

1. The GRUB menu is UGLY! I'd rather use a third-party boot manager with a more professional interface to select between XP and Ubuntu.

2. If for whatever reason, I decide to uninstall Ubuntu and return to a Windows-only system, it's less of a pain to just kill the Linux and Swap partitions and resetting a third-party OS selector, than having to boot with the XP CD, load the SATA drivers from a floppy and get into the Recovery Console so I can repair the Windows XP MBR and boot records.

Is it possible to move Ubuntu's boot loader into the Linux partition, without having to reinstall?

Thanks.

---

### Post by Dr. Nick on 2007-01-27
How did you install ubuntu? live or alternate cd?

The live cd picks mbr without asking while the alternate cd lets you choose between no bootloader, mbr, or first sector of root partition. I imagine it can be done without reinstalling the entire os, just not exactly sure how atm.

I am in a similar situation myself with multiple boot loaders fighting for the mbr but haven't straightened it out yet

---

### Post by RCC2k7 on 2007-01-27
I used the Live CD.

---

### Post by RCC2k7 on 2007-02-03
In what is probably my first huge success with Ubuntu, I finally managed to move grub to the main Linux partition, and it wasn't too complicated after all! I don't know if these steps will work for anyone (I hope they do), but it's worth trying, especially if you have a backup of the OS to fall back to just in case.

This is needed _only if you will be using a third-party boot manager_ to select operating systems at boot time.

Installing GRUB to the Linux partition (instead of launching it from the master boot record), when  Ubuntu has been installed from the Live CD or Live DVD:

1. Boot into Ubuntu the normal way. (no need to go into Rescue Mode or a text-only environment)
2. Launch a Terminal.
3. Type **df** and press RETURN or ENTER.
4. Note the first entry on the list - the one mounted as **/**. This is the one we want. In my case it was /dev/sda3.
(Windows partition(s), usually mounted as /media/hda1 or  /media/sda1 _should never be used to install GRUB_.)
5. Type **sudo grub-install /dev/sda3** - replace /dev/sda3 with the correct entry for your system.
6. Enter your Password and press RETURN or ENTER.
7. Close the terminal window and restart your system.
8. Install or reinstall your third-party boot manager, booting into the appropriate OS if needed.
9. Add your Linux main partition to the OS selections, if your program doesn't detect the OS automatically.
10. Reboot the system and test all the OS choices you want to boot from the third-party boot manager menu, to make sure all of them boot.
11. Boot back into Ubuntu.
12. Open a terminal window.
13. Edit the GRUB menu list by entering **sudo gedit /boot/grub/menu.lst**.
(You can use a different text editor if you want to.)
14. Type your Password and press RETURN or ENTER.
15. If you have changed the default OS choice to boot Windows, you need to change it now so that it boots Ubuntu by default. (usually changing **default** to 0)
16. Remove the # sign in front of the line that only contains **hiddenmenu**. Since you'll be using the menu from a third-party boot manager, there's no need to have a second menu displayed every time you boot. You can always display the GRUB menu by pressing ESC during the first five seconds of booting from the Ubuntu partition if you need to access recovery modes or memtest.
17. Save the file and close the text editor.

That's it!

---

### Post by Herman on 2007-02-03
Hello RCC2k7, and other readers,
First of all, congratulations on your success. You did a good job not only being able to accompllsh what you wanted to do, but also passing on the info so others can do the same if they wish. That's what we are all supposed to do, it's good. :)

But just a warning, new users should avoid using the grub-install command. The grub-install command will do exactly as you tell it without any warning messages or fail-safes. That means new users who don't know the difference between a bootsector and their MBR will be able to make a mistake and install Grub to their Windows bootsector and hose their Windows installation.
*Please*, new users, use the Grub shell for installing Grub somewhere, as it will refuse and give an error message if you try to install Grub to your Windows bootsector.  Link: [GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#GRUB_shell")
Don't use grub-install unless you absolutely have no other choice. It can be dangerous!
Especially for those who don't understand yet the difference between a Master Boot Record and a partition's bootsector and where either of those are situated. (The Master Boot Record is not part of the Windows partition at all).

Just trying to save some people from the risk of serious data loss, that's all.

Other than that small point, I'd like to encourage you to keep up the good work,RCC2k7, and keep on doing what you are doing, trying out commands and sharing the successful ones with others. I do the same thing when I can  and I'm still learning things too, and I learn the most by making mistakes. Sometimes I even 'hose' things deliberately to find out what will happen and how to fix things, that's how I now the grub-install command can be dangerous. I have used it already to 'hose' one or two Windows operating systems on purpose, so I can fix it again to learn how to help other people fix theirs. Linux can recover a hosed Windows FAT32 filesystem, but probably not an NTFS one.
I hope I'm being constructive here, and I mean this post in a freindly way, I hope it comes across okay.

Regards, Herman :)

---

### Post by RCC2k7 on 2007-02-03
Thanks, Herman. That's really good info. The purpose of the thread, and the reason I used grub-install was to place GRUB on the Linux partition for those of us who want to use a third-party boot manager (System Commander, BootMagic, Acronis OS Selector, that kind of thing) to select an OS to boot. I added some clarifications to my previous post, based on your observation. 

Users who do not have these boot managers (including most new users) will do just fine using GRUB to boot either Linux or Windows with Ubuntu's default of starting GRUB from the master boot record (MBR).

---

### Post by Benoone on 2007-05-04
> **Dr. Nick said:**
> How did you install ubuntu? live or alternate cd?

The live cd picks mbr without asking while the alternate cd lets you choose between no bootloader, mbr, or first sector of root partition. 

Thanks for this important piece of information found almost nowhere else.

I'm running an IBM T30 multi-boot i386 with Windows 3.11 on P0, XP on P1 and W2K on P2.  My ntfs common and aps files are in the extended partition.  To round things out, I decided to put Ubuntu "/" in P9 and then added  /usr and /home just for fun and giggles.  I did not make a /boot partition and in the end, it seems to not care but I'm nowhere an expert on why.

I have used Vcom's System Commander for years but for this Ubuntu install it was an absolute total loss in the process and cost me two days before I gave up on it and switched to Nortons (PowerQuest) Boot Magic.  BM is down and dirty but it sure does work.  It seems to want to be placed in the first 2g of the drive on a primary partition which makes sense to me.  I had DOS there anyway so it was a nice fit. I'm glad I had the RescueDisk floppy as it got a lot of use.  (USB Floppy)

I also use Acronis True Image v9 to make complete backups.  Acronis ghosts files, partitions or whole disks to another drive via local, CardBus, the network or USB.  It is a very cool "must have" CYA program.  I also use MBRtool, a shareware floppy to backup/restore the MBR and/or Track0.  Another cool one is PTD (Partition Table Doctor) which boots from CD or floppy.

First, I used Partition Magic to format the ext3 partitions but then Ubuntu wanted to reformat them so in the end, I just used Ubuntu to partion that free space segment of the drive. 

The "Live" install just dumps the GRUB in the MBR... without notice! That cost me another two days of screwing around and then I came across this thead.  So, to give back, Im adding some of my findings (sort of) with this post. 

I put the "Live CD" aside and downloaded the alternative distro.  Started the text install which is easy and really cool. But, I would suggest that the hard disk already be laid out and partitioned using Partition Magic (or similar) and that there is free space to drop Ubuntu into.  IMHO, letting the distro mess with other partitions is sort of crazy and of course, not having a backup... is just plain nuts.  

During the process, to set up root "/",  you must "tick" the box, make this partition boot. 

Then it wants a Swap partition  (type swap... not/swap) and then add whatever other partions you like.  Of course none of these others will be marked to boot.  Be sure to write down the device numbers as you will need them later, especially the dev name for the / partition.  I think mine was sda9 or there abouts.

The install process then formats the partitions, completes the install routine and then the GRUB setup appears :) 

Just type in the device name (like /dev/sda9) where you want it to reside.  For me (using Boot Magic), MBR would not be a good choice.

I used the BM floppy to restart BootMagic and it (now) finds the Ubuntu / partition marked bootable.  I add it to my BM list.  Save, exit and restart.

Gee!  Ubuntu is in my boot list. I select it...

It boots.:) :) :) 

Sweet.

I hope this helps someone as this forum and these posts has helped me.

Take care

Benoone

PS
I was surprised as I can view the ntfs partitions and even open the files... cool!

---

