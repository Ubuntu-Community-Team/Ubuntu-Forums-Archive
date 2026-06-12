---
title: "dell inspiron 1525 partitions - can I remove the restore partition? + mediadirect?"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by FSHero on 2008-10-06
Hello all at UbuntuForums,

I got a Dell Inspiron 1525 laptop today, and it's great! I booted Kubuntu 8.04 live-cd and it worked like a charm! Because I asked for an Intel 3945 wireless card to be installed, it connected to my WPA-PSK wireless network immediately, without any fuss. Also, the Intel X3100 graphics enabled me to run glxgears (after running "sudo apt-get install mesa-utils") immediately, which is promising.

I have not installed it permanently however, because I anticipate partitioning problems. Note that the laptop came with Windows Vista Home Premium preloaded. Let me give information about the partitions below:

(as shown in Kubuntu's installer)
Device, type, size, used
/dev/sda1, fat16, 106MB, 33MB
/dev/sda2, ntfs, 10737MB, unknown
/dev/sda3, ntfs, 236529MB, 17770MB
/dev/sda5, fat32, 2683MB, 1800MB

This is what Windows Vista sees (in Disk Management):

Label, size, format, flags (correct term?)
<none given>, 102MB, <none given>, Healthy (EISA configuration)
RECOVERY (D:), 10GB, NTFS, Healthy (Primary partition)
OS (C:), 220.29GB, NTFS, Healthy (System, boot, page file, active, crash dump, primary partition)
<none given>, 2.50GB, <none given>, Healthy (primary partition)

I presume that the 10GB RECOVERY (D:) holds recovery files to factory-restore Windows Vista. Also, I presume that Vista is installed to C (/dev/sda3) and that MediaDirect is installed to 2.5GB /dev/sda5.

My laptop *did* come with an operating system reinstallation DVD : Windows Vista Home Premium 32BIT SP1.

My aim is to dual-boot Windows Vista with Ubuntu, but leave as much free space as possible for my files (so I would like to get rid of the recovery partition).

Can someone confirm that I will not need the contents of my restore partition (10GB D: /dev/sda2) since I have the DVD? Then, would I just use (for example) QTParted in Knoppix 5.3.1 to remove all the partitions, and do this sort of layout:
20GB NTFS at beginning for Win Vista
1GB at end for swap
10GB before swap for /home
12GB before /home for / (root partition for Kubuntu)
everything between Vista and Kubuntu's / : for data (as NTFS)

I would then use the restore DVD to install Vista to the appropriate partition. Then after this I would use Kubuntu 8.04.1 amd64 live-cd to install to the appropriate partition.

My last question is: I may or may not get rid of MediaDirect. But if I do, I've read that in UbuntuForums that pressing the home-button can render the laptop useless! (Some lucky people find it directs them straight to Linux...). Based on this, is it safe to remove MediaDirect if I want to? (I'm not sure which version of MediaDirect I have, but I can find out if that helps.)

Thanks everyone!

---

### Post by FSHero on 2008-10-06
Hello, 
I found out that I have MediaDirect 3.5.3320D. It seems mildly useful... but it seems pointless as it wouldn't be as fast as ASUS ExpressGate... and hopefully my Kubuntu will boot up as fast as MediaDirect! I'll decide later whether to keep it...

... and I forgot to mention that if I do keep MediaDirect, I will likely just leave it at the end of the hard drive for convenience. (It would be nice if I could move it somehow so it fits in between my data partition and my kubuntu root partition ;)

---

### Post by Therion on 2008-10-06
> **FSHero said:**
> My laptop *did* come with an operating system reinstallation DVD : Windows Vista Home Premium 32BIT SP1.
Your plan sounds solid to me... But... The disk you have:  Is that a Windows Vista *install disc* or is it a Dell factory-RESTORE disc that has Vista ON it?  

The important difference is that the latter will "install" the Recovery Partition on your hard drive - rendering your plan useless - while a Vista install DVD will not.

---

### Post by FSHero on 2008-10-07
Therion, thanks for replying.

I looked at the box of manuals + discs that came with the laptop. I spotted a manual for reinstalling Dell MediaDirect. Also inside were the Windows Vista reinstallation DVD and a disc for "reinstalling Dell Mediadirect 3.5 on Dell Inspirion Computers"

What it contains is promising. The instructions for re-installing MediaDirect are roughly as follows:

1) Insert Dell MediaDirect CD into drive
2) Select the option to partition the hard drive
2.1) Option 1: use all of hard disk for operating system installation. (how the computer was shipped to you)
2.2) Option 2: Designate a size for the OS partition, leaving the remainder of the hard drive configured as a "data" partition ("D:")
3) Once finished preparing the drive, remove the MediaDirect CD. Reboot.
4) Install Windows operating system, selecting "primary partition" when prompted.

5) To re-install MediaDirect, run Windows and insert the MediaDirect CD into the drive.
6) Press enter to start installing...
7) After this has finished, you can shut the computer and press the MediaDirect button to start MediaDirect.

Thus... it sounds like I can repartition the hard-disk with the MediaDirect CD and then install Windows Vista to the partition of my choice. Then when I install Kubuntu GRUB will take over. I shall try this procedure this weekend then report back.

I haven't tried any of these steps yet. I have pressed the MediaDirect button (looks like a "home" symbol) and the startup is actually pretty zippy (fast). It is 2GB at the end of the disk which if I wanted to get rid of, only the swap partition could make use of it. To keep or not to keep... (sorry, thinking out loud...!)

So, I'll try to repartition this weekend. I'll definitely get rid of the restore partition to pave way for Kubuntu, Vista and my data partition. After all this, I'll set Vista to install programs and put user data on my data partition so that it is available for both Kubuntu and Vista to see.

---

### Post by bht-at-home on 2008-10-09
Closed & reposted

---

### Post by billstei on 2008-10-10
I just bought this laptop, and am attempting the same dual boot configuration.

What is the 106 meg sda1 partition for?  The entire factory partitioning seems very odd.

Bill

---

### Post by billstei on 2008-10-10
Apparently the way that MediaDirect works is to reassign the hidden (HPA ?) sda5 partition (temporarily) to sda4 and then boot it ?  What I'm wondering is if I put Ubuntu into sda4 will MediaDirect trash it when it does the unhiding/re-hiding trick ?

FSHero: Looking forward to updates on your progress.

Bill

---

### Post by billstei on 2008-10-10
My plan at this point is to be as unintrusive as possible to Dell's setup (I'm too nice).  Apparently (?) the Dell Diagnostic Utilities can be run off their CD rather than off sda1, so here is what I hope to do, without having to reinstall Vista/Recovery/MediaDirect:

sda1 - Resized extended/logical partitions for Ubuntu root, home, swap
sda2 - Recovery ( as Vista F: )
sda3 - Resized extended/logical partitions for Vista C:, D:, E:
sda5 - MediaDirect (hidden)

Can I do all this with GParted/Live without trashing anything (except sda1 obviously) ?

Bill

---

### Post by billstei on 2008-10-10
Okay, I guess this is educational if nothing else... I now understand that you can't have more than one extended partition present, so maybe this:

sda1 - Ubuntu root
sda2 - swap
sda3 - Vista C:
sda4 - Extended/logical
__ sda5 - MediaDirect (hidden)
__ sda6 - Vista D:
__ sda7 - Vista E:
__ sda8 - Recovery ( as Vista F: )

After setting this up in GPartEd I booted to Vista and it is "Attempting repairs...".  I am losing my niceness.  I may just blow it away and re-install Vista.  One thing that is a potential problem is that the MediaDirect front panel button is sensed by the BIOS (correct?) and there may not be a way to turn it off, so at the very least it may be necessary to keep sda4/sda5 as the MediaDirect partition.

Bill

---

### Post by billstei on 2008-10-11
Here is my final configuration:

sda1 - 100 GB, reiserfs, Ubuntu root
sda2 - 3 GB, Linux swap
sda3 - 30 GB, ntfs, Vista C:
sda4 - 100 GB, extended
__ sda5 - 40 GB, ntfs, Vista D: (non-system critical applications)
__ sda6 - 60 GB, ntfs, Vista E: (user data)
__ sda7 - 5 GB, ntfs, Dell Recovery

Notes: (Disclaimer - memory fades; much wrangling along the way; this is only a fuzzy summary; YMMV)

It was not necessary to reinstall Vista (yay).  Initially in Vista I re-lettered D: to H:, and the CD drive to G:, in anticipation of the new D:, E:, and F:.  I used GParted Live CD for most of the partitioning work.  The extended partition was created first, deleting the MediaDirect partition.  I resized and moved the partitions as needed to get the sizes noted above.  Booting back into Vista I got a long "Attempting repairs...", which was "successful" in that it did not trash anything.  In Vista I moved the files from the old Recovery partition (sda2) to the new sda7 F: volume.  I am not entirely sure that the Dell recovery software would be happy about this, and I will probably never use it anyway, but since my goal was to retain as much default factory functionality as possible, well, there it is.  Being completely new to Vista I would note that: 1) It adds a lot of eye candy, and 2) It is Microsoft's greatest OS-for-stupid-people yet.  Example: When I asked for a file count of the folders I had transfered to the new recovery partition, Vista felt that it should not tell me about certain files because I didn't have permission to view them.  Being lied to is not a level of security I need, and like HAL, I have become paranoid... where was I...

Restarting with Ubuntu Hardy 8.04.1 I installed to sda1, with sda2 as the swap.  Initially the wireless Broadcom BCM4310 card was not working (kernel 2.6.24-19-generic with linux-restricted-modules-2.6.24-19) but after changing software sources to include hardy-proposed and hardy-backports, and then doing a complete update (via hard wired ethernet), wireless is now working without any issues with 2.6.24-21.  I simply used the network manager applet to pick my wireless router, and viola.

And then there was much singing and dancing and wine.

Regarding MediaDirect, pushing the front panel button from a completely shutdown machine shows the MediaDirect splash, and then it bails and goes to the boot loader.  Good enough for me.  This MediaDirect partition wrangling scheme is IMHO a Very Bad Idea (tm).

Bill

---

### Post by anubhav2k on 2008-10-20
I want to completely format my dell 1525 and install dual os VISTA + KUBUNTU ???? Please help me in detail...........

---

### Post by FSHero on 2009-04-13
@everyone: I apologise for not replying earlier! Fast-forward to the future, and I have got my laptop working. I'll describe it below.

@billstei: I am glad that you managed to get your system working! Especially your MediaDirect button: whenever I created my own partitioning scheme, pressing the MD button destroyed it!!!

@anubhav2k: I'll tell you what I did to get my Inspiron 1525 working. (I made notes using pen and paper; I'll just summarise what I did below.)

At the very beginning, I used the Dell MediaDirect CD to "prepare" the hard disk. I chose the option to allocate 20GB to the C:\ drive, and the remainder as free space.

I installed Vista using the appropriate Windows Vista CD., to the 20GB partition created by the MediaDirect CD. I noted that at the partitioning stage in the Vista installer, everything after the first 20GB appeared "free".

I then messed about with the partitions. I think I used Knoppix 5.x (a Linux that can boot off a CD). I set up the partitions as follows on my 250 GB hard disk ('additions' are in bold):

47.03 MB - fat16
20.00 GB - NTFS partition (my C: drive in Windows)
[b]
12.00 GB - to be the root folder in Kubuntu
200.83 GB - EXTENDED
__ 191.33 GB - to be a data partition, for accessing files in Windows and Linux
__ 8.00 GB - to be /home in Kubuntu
__ 1.50 GB - to be a Linux swap partition
[/b]

After this had finished, I exit Knoppix and booted the Kubuntu 8.04.1 desktop amd64 CD. However, I did not start installation yet:

The 191 GB ext3 partition is to be used to store files to be accessible from both Windows and Linux; in Windows I use ext2 IFS to access the ext3 file system ([http://www.fs-driver.org/](http://www.fs-driver.org/)). However, this requires the ext3 partition to have an inode size of 128. I don't know what that means, but the following command must be run to make the files accessible in Windows:

```

sudo mkfs.ext3 -I 128 /dev/sda7

```

You may choose not to do this and instead use a FAT32 or NTFS partition. (In fact, there's a nasty limitation in the ext2 IFS driver for Win Vista: you cannot run programs as an administrator if they are stored on this ext3 partition!!)

I started the installation, and used a custom partitioning scheme, as described above. The following assigments were made:

/dev/sda1 - 49 MB fat16 partition
/dev/sda2 - 21476 MB ntfs (drive c: in Windows)
/dev/sda3 - 12889MB ext3 partition (mount point: /)
/dev/sda7 - 205434 MB ext3 partition (mount point: /media/data)
/dev/sda5 - 8587 MB ext3 (mount point: /home)
/dev/sda6 - 1612 MB swap partition.

On the last screen before the files are copied, I changed the device for bootloader installation as (hd0,2) for the **3rd** primary partition on my first (and only) hard disk. This is /dev/sda3, the partition that Linux is installed to.

This odd scheme may seem long-winded and unnecessary... but it is in fact extremely important to do. It will make sense in the next step.

Finally, upon restarting Kubuntu after installation, I got booted into Windows Vista (no GRUB boot menu). I inserted my MediaDirect CD **when running Windows**, and found a program caled rmbr.exe. In an administrator command prompt, I ran:

```

rmbr.exe DELL 2 3

```

This sets up the buttons so that from a power off state, pressing the MediaDirect button (looks like a home) will boot from the 2nd partition, i.e. Windows. Pressing the power button (looks like a 1 on top of an O) will boot from the 3rd partition, i.e. Kubuntu Linux.

Limitations:
* You don't get to keep MediaDirect (the quick-boot Windows that is like a media centre)
* To boot Windows, I MUST shut down the computer then press the MD button. If I try to selected it from the GRUB menu after pressing the power button, I can get into Windows but nothing works properly. It seems as though the drive letters are messed up: there's no C: drive, and what should be C: is now E: (weird!!)

I hope this helps you. I'm afraid that my typing has been a bit rushed; I haven't had time to explain certain parts. Also: sorry for the extreme length! Use my instructions as a guideline; search the internet for explanations. Ask back here if you aren't sure about anything.

GLHF!
- FSHero

---

