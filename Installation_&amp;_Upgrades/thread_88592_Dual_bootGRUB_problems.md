---
title: "Dual boot/GRUB problems"
date: 2005-11-10
forum: Installation &amp; Upgrades
---

### Post by kevinwh on 2005-11-10
OK, here's my story -

I have an IBM t41p laptop with an unformatted 60 gig hard disk.  I Install Windows 2003 Server on the first 30 gig partition using FAT32.  Windows installs fine - I can boot Windows 2K3 without issues.

I install Ubuntu (I have a 5.0.4/Hoary Hedgehog release CD) on the second partition.  I follow the installation and allow Ubuntu to use the largest contiguous space on the hard disk.  The install detects that Windows is installed, and asks to istall GRUB on the MBR, which I allow.  Ubuntu installation continues and finishes - I can now boot Ubuntu from the GRUB menu.

When I reboot and select Windows from the GRUB menu, I am greeted with a promising Windows loading screen, which is abruptly interrupted with a blue screen of death - the message contains something about UNMOUNTABLE_BOOT_VOLUME - It goes by too fast for me to make it out.

Any ideas on what I am doing wrong?

Thank you very much for your help, and please pardon my frustration.  I need Windows for work, but I really like Ubuntu...

---

### Post by kevinwh on 2005-11-11
This is a bump - anyone have any ideas on this one?

I know there are a million dual boot threads, but I haven't found my issue in any of them.  I have tried many dual boot instruction sets, but I haven't found one that will work on my single disk.  If anyone could help, I would sure appreciate it...

---

### Post by Herman on 2005-11-12
I was waiting for a while to see if someone else who knows more about GRUB might respond,...but no-one has yet. There is a new 'Boot Loader Help' page in the website on my signature link (below). See if anything in that helps you. I'd think if you have a floppy drive, a GAG boot floppy would at least get you booting Windows for now, if not than A GAG CD-ROM. (Just until you get a chance to fix GRUB properly).  You might need to re-install GRUB, but there might be a way someone knows about to fix the chainloader or something by modifying a text file somewhere, that would be easier. I'm studying the GRUB manual, but I haven't really learned enough yet to be able to help you really. Hopefully someone else will be able to tell you exactly the easiest way. (Herman).:smile:

---

### Post by kevinwh on 2005-11-14
Thanks for the response - I checked your site, and the process you described is roughly equivalent to what I did, only I did not need to resize my Windows partition.  What you did confirm was that my partitioning process should technically work, as I just let Ubuntu take the second partition (the largest free space).

Has anyone successfully dual booted with Windows 2003 Server?

---

### Post by Herman on 2005-11-14
It sounds like you didn't find the 'boot loader help page', but that's okay. If you had it would have only taken a few minutes to make a GAG floppy disk or CD which if it will probably boot Windows, if you were in a hurry with important work to do. Nevermind. :D  
There's a file in your /boot/grub directory called menu.lst (short for 'menu list), we can take a look at that if you like and see if there's a line in there we need to alter. Would you be interested in having a look? There should be some lines right down at the bottom of it which refer to your Windows system. If you can copy those last five or so lines even, that might give us a clue. They might look a little like this:
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
Only yours will say Windows 2003 server probably. :smile:

---

### Post by daibak on 2005-11-15
<<<UPDATED 16-NOV-05 WITH THIS EDIT> 
Just had opportunity to read up on GAG boot loader option suggested by Herman [http://users.bigpond.net.au/hermanzone/p6.htm](http://users.bigpond.net.au/hermanzone/p6.htm)
Good info how to avoid messing with Windows C: root drive and its MBR if you only want to boot Linux from an external disk like mine.
Except GAG's own FAQ (you can read it when booting off your GAG floppy before actually doing the GAG bootloader setup) talks only of LILO installed in your Linux partition, it never mentions GRUB. Perhaps Herman or another Ubuntu guru can clarify this - if only LILO, can I re-run the Breezy 5.10 Install CD with existing setup detailed below and from the Install menu choose a LILO loader in addition to the GRUB loader already installed in the Linux partition /dev/sda1 but never used?
<END OF EDIT TO UPDATE THIS POST>>>


Hi all - Hope someone can help on a dual-boot GRUB query. All my Breezy Badger external disk installed info is listed at the foot of this post. I use a mostly-docked notebook PC (with WinXP Home Edition I'd like to dump) but am leery of wasting yet another week re-installing WinXP HE SP2 from scratch so here's my story and question for the forum. Please help this newbie. TIA.

[QUOTE=Herman]It sounds like you didn't find the 'boot loader help page', but that's okay. If you had it would have only taken a few minutes to make a GAG floppy disk or CD which if it will probably boot Windows, if you were in a hurry with important work to do. Nevermind. :D  
[/QUOTE]

First time I tried to dual-boot following a Breezy Badger Install CD "Guided Partitioning" session I was unable to boot this notebook PC to Windows even with FIXMBR or XPquick rescue floppies as MBR destroyed by Breezy Install CD. No Linux Live CD would let me boot either.

So when finally re-installed Breezy Badger Install CD today to my external Seagate (Firewire) disk I was careful to
(1) set Linux root as the first partition on the disk, followed by another for Linux swap, just to keep things simple so I can learn, and
(2) NOT allow installation of GRUB bootloader to the Master Boot Record on hda - Windows C: drive.
In this way I could investigate in a Breezy Live CD session exactly what Breezy Install CD has installed in Linux root partition /dev/sda1 and I safely saved my Windows XP intact. So far so good, but now need a bootloader to load Linux.

So I question, to be able to use GRUB as a bootloader can I safely now in a Breezy Live CD session type in a terminal,

1. sudo mkdir /mnt/ubuntu
2. sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
3. sudo chroot /mnt/ubuntu
4. sudo grub-install /dev/hda
5. Exit shell and reboot

or will this leave me back in the same mess with an unusuable computer as a week ago as soon as I attempt reboot? This HP notebook IDE disk has two WinXP partitions, first is hidden HP Utilities (Hibernation) partition FAT16 and second one is Windows XP root NTFS.

Here's what Breezy Install CD installed on my external Seagate hard disk - logical Windows NTFS partitions are in a separate extended partition plus there's another primary FAT32 partition to share between Linux and Windows:

<fdisk>
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1557    12506571   83  Linux
/dev/sda2            1558        1679      979965   82  Linux swap / Solaris
/dev/sda3            1680        3719    16386300    c  W95 FAT32 (LBA)
/dev/sda4            3720       19457   126415485    f  W95 Ext'd (LBA)
/dev/sda5            3720        7403    29591698+   7  HPFS/NTFS
/dev/sda6            7404       11036    29182041    7  HPFS/NTFS
/dev/sda7           11037       19457    67641651    7  HPFS/NTFS

Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2           9       64260   84  OS/2 hidden C: drive
/dev/hda2   *          10        3648    29230267+   7  HPFS/NTFS

<GRUB menu.lst and GRUB device.map>
GRUB menu list at /media/ieee1394disk/boot/grub/menu.lst and GRUB's /media/ieee1394disk/boot/grub/device.map showing
(hd0)	/dev/hda
(hd1)	/dev/sda

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-do

...
...

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
chainloader	+1

Apologies for long post but wanted to include full detail to help anyone interested. I'm especially troubled by the last GRUB entry

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2

as I read someplace in forums that specifying anything other than install-grub /dev/hda (my step 4. to the drive only, not to the partition on the root drive) will always mess up the MBR unrecoverably for any dual-boot scenario with Windows.

---

### Post by kevinwh on 2005-11-16
Just by way of a followup, I have a working dual boot installation now.  Unfortunately, I don't have a good idea why it worked the second time around.  The only change I made was that I created an additional FAT32 partition for inter-OS file sharing after I installed Windows.  Then, after allowing Ubuntu to install to the largest free space and put grub on the MBR, I am now able to boot both OSes from the grub menu.

???

Well, at least now I can have my cake and eat it too...  Thanks to everyone for responding...

---

