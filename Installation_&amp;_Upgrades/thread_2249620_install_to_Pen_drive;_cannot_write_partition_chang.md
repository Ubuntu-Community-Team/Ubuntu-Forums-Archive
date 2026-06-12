---
title: "install to Pen drive; cannot write partition changes"
date: 2014-10-23
forum: Installation &amp; Upgrades
---

### Post by andreazzz on 2014-10-23
Hi everyone!

Recently my USB-drive containing some obscure distro (which was running on my granny's pc for listening to church) died, so I needed to reinstall Linux. I need a distro which does need absolutely no maintenance (my granny has never touched a pc, except, since a year, the on/off-button) and does not suddently stop working. Therefore I have tried all the main distro's (Ubuntu, Lubuntu, Xubuntu, openSUSE, Fedora, Debian). 
However, somehow 75% of all tried distro's give a modprobe error at booting and get stuck there. The other 25% runs well live, but when _installing_ they fail when formatting the partitions (after which the drive isn't recognized anymore) or during the installing itself. I have formatted the live-media in Gdisk and/or Gparted (or with HP disk format tool) and wrote the images with the appropriate methods (dd, unetbootin, YUMI). I have made some live dvd's as well, but they have the same problems (burned with K3B and Brasero).

Does anyone of you have an idea what I should do?

Thanks so far!

Andrew

P.S. my story is probably not clear (for which I am sorry), so ask questions if anything is unclear.
P.S. 2 : short version: some live-distro's fail to load, others fail installing on my USB-drive.

System:
Asrock E350M1 with AMD E-350
2GB RAM DDR3
_CONTAINS NO HDD!_ Only the Pen drive!

---

### Post by yancek on 2014-10-23
Are you trying to use a flash drive/DVD to install to an external usb hard drive?
Are you just trying to put a persistent usb together to attache to her computer.  Given the simple needs, it would seem a persistent Ubuntu or derivative would be the solution.  Have you tried that or am I missing something here?

---

### Post by andreazzz on 2014-10-23
No, I haven't really tried that, I have only tried Puppy, but that didn't want to play audio. 
I have earlier tried to make a persistent drive, but that did not succeed. Will I then be able to add a line to the startup-files, so I can start VLC?

Edit: formatted in Gdisk, Unetbootin Lubuntu 14.04 image with 100MB persistent storage, only a blinking cursor...:/

---

### Post by andrew163 on 2014-10-23
In regard to the partitioning issues, have you tried formating the Stick to an Ext4 format before booting / install ? This shouldnt matter because the Linux installation should do this for you..... but it is a possible that it is being difficult.

After formatting but before install, check your BIOS settings to see if the USB stick you want to use in place of the HDD is actually mounted as the primary storage disk

After looking at your system specs I do not recommend using a Bootable USB to install, if you have an optical drive, use it.

As for what OS, for Computer unfriendly folks I would always recomend Windows, but I understand you wanting to run Linux. I am always partial to Linux Mint, I believe the most current version is 17. I have not had any problem out of this build, aside from virtualisation..... but that is a story for another time.

If you are having ANY trouble installing from a USB, I would reccomend using a Live CD instead. There are some great resources for curating a bootable USB drive @ [http://www.pendrivelinux.com]("http://pendrivelinux.com") , Download the Live USB program.... Works best on Windows (Sorry Linux) after downloading the Live USB software, get your hands on a "<Your favorite Linux Flavour>.iso" preferably straight from the legitimate repository (I.E. Dont torrent the ISO from a skethchy source). Follow the prompts in th Live USB program, install away.

Changing gears, if you cant get it to install and keep having trouble there may be another hardware issue going on.... possibly on the Main Board, if that is the case take down some "lessons learned" and decommission the box.... I hate to see them go after so much time and effort, but sometime this is the only option.

---

### Post by yancek on 2014-10-23
How are you trying to create the bootable usb?  Are you using a windows computer with a windows version of unetbootin?  Have you checked her computer to see if it is bootable by usb?  Are you test booting this on another computer?  Have you formatted the flash disk FAT32 before using unetbootin?  Do you get any warning/error messages from unetbootin?

---

### Post by Vladlenin5000 on 2014-10-23
And you cannot install to the same pendrive you're booting from...

---

### Post by andreazzz on 2014-10-24
Thanks all for your help!
For the live-usb's: I have formatted them both in ext4 as in fat32, both in Linux and in Windows. In Windows I have used Unetbootin and for Fedora it's own program, to be honest I haven't tried the live-usb's elsewhere, so it might be the pc (what seems very odd to me).

I have tried Mint too, but that one (LMDE and normal Ubuntu-based) get stuck with the modprobe error at booting (is a known error, but should disappear, what is does not in my case).

I have made some live cd's of Ubuntu 14.04, Lubuntu 13.10 + 14.04, openSUSE 13.1 + 11.3, Debian Squeezy, Pear 7 (lying around) and probably some others (and both i386 and x64 images). Somehow my workhorse Mint laptop does not recognize empty cd's anymore.

Yeah, I am affraid something like that is the problem too, but what exactly might cause this? Broken USB-controller? I am currently hooking the external DVD-player to the SATA-port, hope it works.

@Galiza, don't worry;)

Edit: formatting in terminal (on a working pc) results in this:
```

mke2fs 1.42.5 (29-Jul-2012)
/dev/sdb is entire device, not just one partition!
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
473280 inodes, 1891071 blocks
94553 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=1937768448
58 block groups
32768 blocks per group, 32768 fragments per group
8160 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (32768 blocks): mkfs.ext3: Invalid argument 
    while trying to create journal

```

Trying it again gives me: "mkfs.ext3: No such device or address while trying to determine filesystem size", cannot find it in filemanager... Again Pen-drive-problems?
SUSE installer error: "warning, had trouble writing out superblocks" (and the failure of creating ext4 filesystem.

---

### Post by andreazzz on 2014-10-25
I have installed another live-usb maker program in Mint with KDE USB creator, but after completion, the filesystem is unknown (according to gparted; fdisk returns "cannot open /dev/sdb"). I think the USB is broken, is that correct?

---

### Post by /ADM on 2014-10-25
Why not just add a small and cheap 20GB hard drive to the computer and install from dvd or usb onto that?

---

### Post by andreazzz on 2014-10-25
I think that's the thing I am going to do. I am getting tired of these USB-drives. The orginal idea was that a USB-drive-installed Linux was easier to fix (get it with me without having to unscrew the case), and, most important for my granny: it's cheaper (only 2,5" will fit in the case). 
Leaves the question whether it is a coincedence that both (same brand & type) USB drives suddently crash (replacement didn't even work), or that it is a PC hardware problem...

---

### Post by yancek on 2014-10-25
> (according to gparted; fdisk returns "cannot open /dev/sdb"). I think the USB is broken, is that correct? 		

Looks like you did not create a partition on it on which to put the filesystem which is the cause of the error.

> mke2fs 1.42.5 (29-Jul-2012)
/dev/sdb is entire device, not just one partition!
Proceed anyway? (y,n) y

From your earlier post, usually doesn't work and did not in your case.
[/QUOTE]

---

