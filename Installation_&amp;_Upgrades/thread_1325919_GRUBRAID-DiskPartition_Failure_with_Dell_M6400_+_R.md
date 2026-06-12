---
title: "GRUB/RAID-Disk/Partition Failure with Dell M6400 + RAID"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by dmgub on 2009-11-13
Trying to install on a Dell M6400. Previously contained Windows-7.
Ubuntu 9.10 (obtained from this download mirror:    [http://mirror.its.uidaho.edu/pub/ubuntu-releases/karmic/ubuntu-9.10-desktop-amd64.iso](http://mirror.its.uidaho.edu/pub/ubuntu-releases/karmic/ubuntu-9.10-desktop-amd64.iso))


Booting from CD, install runs smoothly up to 94%, whereupon it coughs with an error that it could not install GRUB on /target/. On continue, it pops into what I presume is the liveCD GUI environment.

On a second attempt, I tried specifying a size for the /boot partition - I set /boot to 1GB, swap to 25GB, and the rest as partition mounting to "/". This changed the behavior somewhat. Installing from with LiveCD environment, install claimed to succeed with this partitioning, then on restart it said it could not find the root environment; installing when booting from CD, install failed as before, but now GRUB tries to start but immediately produces an "Error 15" message.

The machine has two hard-drives, arranged in a RAID-0 array. Both drives are model ST9320423ASG, which is a Seagate SATA 3Gb/s 320GB.

As far as I can make out, the RAID-0 (which was pre-configured by Dell) is a hardware RAID, with Intel RAID controller. There is a RAID configuration program in the BIOS, titled "Intel(R) Matrix Storage Manager option ROM v8.0.1039 ICH9M-E".
The RAID config program shows 2 x 298GB, RAID0 (Stripe), 128KB stripe. The Raid Array is shown as 596GB, bootable.
In Ubuntu installer, the RAID Array is shown, though as 640GB. The installer is apparently able to partition the array, format partitions, and copy files to the partitions successfully during install.

Can anyone suggest a suitable partitioning setup for a 640GB array? I could try that...

Or anyone got any other suggestions? Any thing special need for RAID in general, or this RAID controller in particular?

Thanks much!
DMG

---

### Post by ed-koala on 2009-11-13
I have a 64 bit system with RAID 0 also, this thread has the only solution that worked for me - [http://ubuntuforums.org/showthread.php?t=1322005]("http://ubuntuforums.org/showthread.php?t=1322005")

That grub error 15 sure looks familiar ... lol ... hope it helps ya!

---

### Post by finwake on 2009-11-13
From what I understand, you have Fake RAID.  Not to worry, it is just a differentiation from true hardware RAID that you would find in the server community.  
Take a look at the following from the Ubuntu Community Documentation and see if it helps:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Take a close look at the "Why not use a linux software RAID."  Since you are no longer using Windows (super choice, bty), you needn't keep the array controlled from the BIOS's [Fake]RAID Controller.  You may need to figure out how to release the two drives from the controller so they are just two seperate disks going into your installation of ubuntu.
Take a look here:  [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

I run software RAID.  Have two RAID 0 partitions, one for my root directory and one just for fun, and a RAID 1 partition.  I keep my /home directory elsewhere; high value files go into the RAID 1 partition.  (Note:  always backup -- RAID 1 does NOT protect you from an errant Delete command or other operator error type accidents).  Also:  definitely put your /boot diretory into a small partition of its own.  From my understanding /boot partitions cannot be RAID partitions.

---

### Post by dmgub on 2009-11-15
Thanks [finwake]("http://ubuntuforums.org/member.php?u=803849")! It's better, but still GRUB is an issue.

I think you must be right about the fake RAID on the M6400. I disabled the fake RAID in the BIOS, which simply leaves the two raw disks. 

Then installed using the Alternate Install CD (9.10, AMD-64).

I set three RAID partitions - /boot (1GB, RAID1, EXT4, /dev/md0), swap (25 GB, RAID 0), and "/" (590GB, ext4, RAID0, /dev/md2).

Install appears to complete successfully, leading to reboot.

On reboot, I get a GRUB error (something like Ünable to find C/S/A values) and am dropped into "GRUB rescue." md0 is definitely visible, e,g, via ls (md0).

If I boot from the Ubuntu install CD, and select "boot from first hard drive". the OS boots fine, and of course the RAID disks are available (both /boot and /). The boot sequences must be configured fine, at least on the first hard-drive (I would expect to be able to boot from either hard-drive, since they are copies of each other, or from both, given it is RAID-1 and hence for /boot the two drives are replicas).

Any advice on how to get GRUB to boot OK from the RAID-1 setup, i.e. without CD?

Thanks again.

---

### Post by finwake on 2009-11-15
I have always put /boot on an entire separate HDD, so I am not 100% certain on following, but pretty sure...

[INDENT]1.   /boot needs to be in a non-RAID partition on one of the disks.  Create a small partition (ext3 or ext4) on one of the HDs.  (I do about 500MB, although could be less).  

2.   On install, make this non-RAID partition your /boot directory.  I believe this has to do with /boot attempting to coexist with the MBR of the disk it is upon -- although someone can clarify.
[/INDENT]

This should do it. Please try and let me know.  

MORE:  allow me to also quickly add that 'swap' should not be RAID.  The way swap works is already RAID-like as the system will go to the first available swap area and hop from swap to swap as it needs swap space (given that you give all swap the same priority -- advanced topic that is discussed in swap documentation -- they default to having same priority).

So, given you have no more than the two HDDs.  Put two independent 'swap' partitions at the start of each drive (faster).  Then put root directory in RAID 0 array, then /home in RAID 1 array, then /boot in a small partition on one drive only, and at the end of the HDD.  Create a similar partition on the other drive or leave as free space.

Again, let me know how this goes...

---

### Post by dmgub on 2009-11-15
Thanks again.

So, I setup a 600MB /boot EXT4 on first disk and (to keep later partitions aligned across the two disks) a corresponding /spare partition on second disk. No RAID here of course.

Then set up 2 x 12.5GB swap partitions on the two disks respectively (not RAIDed together).

Then set the remaining space to RAID partitions, and assigned the RAID to EXT4 mountpoint "/".

All this using the alternative install CD, amd64.

Install runs, system boots. Wilreless network, sound, working, even proprietary video driver after checking for device driver updates. "df" on the network drices show "/" partition has full access across the RAID. Great :-)

Only remaining wrinkle - on startup, Grub throws up an error, "Can't find [something]" I think, but goes to graphical boot so quickly I can't read the message. Any idea what this is, or is there a grub log file somewhere I could inspect?

---

### Post by maxol on 2009-11-15
[http://ubuntuforums.org/showthread.php?t=1308472]("http://ubuntuforums.org/showthread.php?t=1308472")

---

### Post by dmgub on 2009-11-15
So I was able to spot the error message in GRUB.
Grub prints "Error: Cannot find C/H/S values" and then immediately (in milliseconds) proceeds to a graphical boot-sequence  screen. The boot succeeds.

Anyone know what this means, whether it matters, how to fix?

---

### Post by NaOH on 2009-11-17
Is this absolutely the only way to do it?  Forgive my ignorance, but it seems like we've thrown the baby out with the bath water having this one boot partition to rely on--aka a single point of failure.  Any way to circumvent this aside from routinely running a dd of this drive to another?

---

### Post by finwake on 2009-11-17
dmgub, like myself, is doing RAID 0.  This is not actually RAID because there is no Redundancy in the Redundant Array of Independent Disks.

Thus, if a drive goes, and therefore takes out the singular /boot partition, you are done anyway.  

The argument against RAID 0 -- for those concerned with points of failure -- is that if either drive fails, you lose all your data.  I do RAID 0 on my root partition and not elsewhere.  root is real easy to rebuild and doesn't contain unrecoverable data, same for /boot -- like personal documents and pictures; I put those on a RAID 1 array and make sure I back it up frequently.  RAID 1 prevents against single disk failure but doesn't prevent against an errant 'delete' command, nor other runtime corruptions of data.

---

### Post by dmgub on 2009-11-18
NaOH, I had attempted to configure two /boot partitons, as RAID-1 (not 0).
Once we had established that the M6400 built-in RAID was "Fake RAID", we know RAID-0 cannot work for /boot - RAID0 stripes the data between the two disks, fake RAID means OS support for the RAID, but OS support cannot work until after boot has happened...
I have had RAID-1 work on other Linuxes in this situation - RAID-1 makes the two disks copies of each other, so in theory the system could boot from either the first disk, or second, or both simultaneously via RAID, and achieve the same result. And if first disk /boot fails, can change boot config to boot from the second hard drive, and boot will then work again. Great in theory. Absolutely did not work in practice with Ubuntu. Maybe someone knows the reasons...
Anyhow, when I just set /boot to be a simple non-RAID partition, but use RAID-0 for "/" for performance, it seems to work OK.

---

### Post by dmgub on 2009-11-18
Further to my previous post about "cannot find C/H/S" via GRUB loader. I think this is GRUB not being able to find the disk geometry (C/H/S equals Cylinders / Heads / Sectors).
In the system BIOS of the M6400, under system config, I changed the disk config from RAID to AHCI. This seems to make GRUB load correctly. Note that it made a difference even though I had previously turned off RAID in the RAID-controller config (CTRL-I to turn-off RAID setup was what I did before, now I did F12 for BIOS boot options and selected system to choose AHCI).
Any one care to explain what's going on? :-)

---

### Post by August59 on 2010-03-28
I have a Dell M4400 with this same setup as far as the Intel Option ROM booting. I can tell you this is that Dell has modified the normal "Option ROM" from Intel to block access during boot up (typically "Ctrl" & "i"). It (bios) is hard coded to use "Raid0 - Striping" and the actual Intel Matrix Storage Manager application cannot mofify it as it is setup to use the "Dell" recovery partition only. I believe you can still setup a Raid, but not through the "Option ROM".
The only thing that bypasses this is to change bios to "AHCI", instead of "IRRT". The thing that I find wierd is if you install as "IRRT" the chipset is setup as "Storage Controller" in "Device Manager" and I believe it uses a SCSI port. If you pick "AHCI" the chipset appears under "IDE ATA/Atapi Controller" and uses an "IDE" channel??????? I don't understand this and not even sure it makes a difference, but it just seems to me like it would.
If you leave it on "IRRT" there will be performance drops as the hard coded Intel Raid setup will be looking for a hard drive or updating the Dell Recovery partition.
Why Dell would do something this stupid in a laptop is beyond me, but they could at least give the functionality that is suppose to exist to disable or change to manual update.
I know this is an old post, but maybe it can help in the chance that someone knows much more than me and can come up with a "fix". Thanks!

---

