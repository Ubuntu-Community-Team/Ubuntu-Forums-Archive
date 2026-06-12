---
title: "Hard drive clone/Partition copy..."
date: 2011-01-16
forum: Installation &amp; Upgrades
---

### Post by kliffs on 2011-01-16
Hi,
I have a very specific issue that I am having trouble resolving. I have an old laptop and a new laptop with a smaller HDD. I want to copy the windows partition from the new lappy to the old bigger HDD so I have room for Ubuntu. All of my files are on a Maverick install on the old lappy. How can I get all my files and windows to the old HDD and into the new laptop. I am a little stuck on this one because of my limited options.
Thanks,

Kliffs

---

### Post by bryanl on 2011-01-16
Do be careful to adhere to the windows EULA.

The easiest thing to do would be to first make a backup, partition the drives as you want them, reinstall windows from the rescue disks, restore the backup user files, then reinstall Ubuntu and restore its home directory backup.

If the Windows partition is NTFS, Ubuntu has some good utilities for partition imaging and restoring. The tools you need are gparted, which may need to be installed (apt-get install gparted) and ntfsclone, which, I think, is a part of the standard install (it is a part of the ntfs tools package).

If the reinstall from rescue disks doesn't work, then you can size a destination partition to match the old one, ntfsclone the windows partition, boot from it so Windows can checkdsk, then use gparted to re-size it as needed. Once you get the Windows partition sized as you want it, then you can install Ubuntu.

When you install Windows from the rescue disks, it will set up the disk bootstrap code. When you install Ubuntu, it replaces that with GRUB. It is easiest to let the install keep things bootable. Otherwise, you'll need to figure out how to initialize Grub or the Windows bootloader on the disk.

A laptop drive to USB adapter may be needed to mount both disks to make things easier. These are not that expensive.

---

### Post by kliffs on 2011-01-18
Thanks for the reply.

As for the install disks, these are not an option. My computer came with a 10GB recovery partition which is now corrupt. I want to simply copy the 120GB disk to the 320GB disk and stick ubuntu in the empty space. I have done this in the past with a simple command line program but I just can't remember the name... I'm thinking now just to leave the 120GB partition on and use the old laptop as a server using Amahi and access all my vids and pics through that.

P.S. If anyone knows the command line program let me know!

Thanks 

Kliffs

---

### Post by srs5694 on 2011-01-18
IMHO, it's not worth the effort to try to preserve a bootable Windows installation when transferring between computers; Windows is just too fussy about its hardware, its boot partition's start sector, etc., etc. This is above and beyond the legal/EULA issues, which are bizarre and (usually) very restrictive.

If, however, you just want to preserve your user data, there are other ways to do it. For instance, you could set the two machines up on a network, enable file sharing, and then drag-and-drop all your user files between the machines. Using low-level tools like ntfsclone can also work in this case, with the caveat that Windows itself (if on the same partition you clone) will become a useless waste of disk space.

---

### Post by kliffs on 2011-01-19
Hi,
I'm sorry if I wasn't clear on this above. All I want to do is upgrade the HDD. The vista partition will not be switching computers. The other laptop is only mentioned for its HDD.

Thanks

Kliffs

---

### Post by hello2012 on 2011-01-19
[FONT=Times New Roman][SIZE=3]Yeah, I am very pleased that you can turn to Partition Assistant 3.0 for help on your Windows OS. This is the update version and disk/partition copy are two added features. You can read the related article at: [/SIZE][/FONT]
[[FONT=Times New Roman][SIZE=3][COLOR=#800080]http://www.extend-partition.com/resource/hard-disk-copy.html[/COLOR][/SIZE][/FONT]]("http://www.extend-partition.com/resource/hard-disk-copy.html")[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]There is another good news is the Partition Assistant Professional Edition 3.0 will giveaway for three days from Jan. 25 to Jan. 27. You also can free download. Please take expectation.[/SIZE][/FONT]

---

### Post by srs5694 on 2011-01-20
> **kliffs said:**
> Hi,
I'm sorry if I wasn't clear on this above. All I want to do is upgrade the HDD. The vista partition will not be switching computers. The other laptop is only mentioned for its HDD.

OK, this makes sense now. There are quite a few ways to do this. The easiest methods involve hooking both hard disks up to one computer. If you've got an external enclosure or if one of the laptops has two disk connectors, you can do so with one of the laptops; if not, perhaps you can connect both hard disks to a desktop computer. It's also desirable to be able to boot using another medium -- an emergency CD/DVD, a USB flash drive, or a third hard disk.

If you can get both disks connected to one computer and boot using another medium, then you should first use fdisk, GParted, or some other tool to positively identify the disks by size or the partitions they contain. Suppose /dev/sdb is the drive you want to copy and /dev/sdc is the bigger drive you want to use. The simplest (but most time-consuming) command to do what you want is:

```

sudo dd if=/dev/sdb of=/dev/sdc

```

This copies the contents of /dev/sdb over /dev/sdc. (You may have to change these device identifiers, of course.) ***It's imperative that you get the if= and of= options right!*** If you mix them up, you'll end up overwriting the drive you want to copy with most of the contents of the bigger disk.

There are also tools like [Clonezilla](http://clonezilla.org) that will do the backup in a "smarter" way by omitting unused sectors from the copy. Such a program is likely to take longer to learn to use, though, so although it'll get the copying done faster, you may end up spending more time at the keyboard than you would if you used dd. Take your pick about which approach to use.

If you can't hook both disks up to the same machine at the same time, you should be able to do it by using a backup tool to back up to DVDs, tapes, a network server, or whatever; and then swap hard disks and reverse the process. Alternatively, you could boot both computers into Linux, set up a network link, and do a network transfer in any of several ways. What software and method to use depends on your available resources, so if you need to go this route, you need to tell us more about what hardware you have, aside from the two laptops and two hard disks.

---

### Post by kliffs on 2011-01-20
Hi,
Thanks, yes that is the terminal code I was looking for. I have done this in the past but my external HDD enclosure isn't very reliable so I was looking for some other method. To make the enclosure work I have to put the USB cable in just right and hope it stays there during the copy. I would be interested to hear about this dual linux over network method and what I would need to set that up. I am not sure what other specifications of my computers would be helpful but they are both 32bit and have bootable vista partitions and bootable ubuntu 10.10. They both have 1GB of ram and 1GHz processors.

Thanks for all the help

Kliffs

---

### Post by srs5694 on 2011-01-21
There are several ways to do this over a network. The most direct is to use a network block device (NBD), which is a way for one computer to share its low-level block device files (the kind that are used to access disks, like /dev/sda). So on the system with the big empty disk, you'd set up an NBD server; and on the system with the small disk with data, you'd set up an NBD client. You could then use the client to do a copy using dd (or Clonezilla or whatever) just as if both disks were hooked up locally. (You could reverse the client/server roles, too; it's just a matter of where you're typing the actual copy command.) It'd be slower than a transfer with both disks in one computer, in all probability, but it'd work. I used this method to transfer a Linux installation to a new computer one time and it worked fine.

I wrote a piece about NBDs for Linux Journal a bit over two years ago:

[http://www.linux-mag.com/id/7118](http://www.linux-mag.com/id/7118)

One caveat: NBD requires support in the client's kernel, and I'm not sure if the standard Ubuntu kernels provide this support. If not, it's conceivable you could find an emergency rescue disk to use for doing the transfer.

---

