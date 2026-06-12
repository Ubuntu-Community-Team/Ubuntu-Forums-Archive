---
title: "Ubuntu 8.10 64bit version installation: detecting/creating partitions problem"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by rdexter on 2008-11-02
Hello ubuntu users,

first of all my hardware config:
Medion MD98300 laptop with
- AMD Turion 64 X2 LT-50 Dual-Core-Processor 1,6 GHz
- 1GB RAM
- Nvidia GeForce Go 6150
- 120GB sata hdd, WDC WD1200BEVS-00RST0-(S1)

I use the new Ubuntu8.10 64bit version.


Now the problem:
When I install ubuntu, at the part when the partion manager starts following first strange thing is that the "before view" of the partitions nevers shows anything, it is empty. If I click on "manual", I never see any partitions. I tried several scenarios, which were for example
(1) no partition, only un-partitionated hdd space
(2) windows xp and its partitions installed
(3) large linux partition created.
But this partitions never occur in the manager. I alway would have to click on "new partion table", if I want to install manually.


OK, if I click on automatic installation (option selected is "SCSI1 (0,0,0) (sda) - 120GB GB ATA WDC WD1200BEVS-0") and enter my username and so on, when the partitionating starts following error occurs after "installing basic system":
"the swap space on partition 5 SCSI1 (0,0,0) sda could not be created". Installation aborts.

I get the same error, If I try to created manuall partitions. They also are never created.

If i look at the log file "tail -f /var/log/messages" I see one message (which may be important):

[sda] write cache: enabled, read cache: enabled, doens't support DPO or FUA.
ubuntu partman: /dev/sda5/: no such file or directory

In the /dev/ directory, only the entry "sda" exists.

If I boot ubuntu live cd, and for example start "gparted" it says: "No devices detected." FDisk says "unable to open /dev/sda".

When I use a differnt live cd from different linux os, the fdisk and gparted work, I can created partitions, it sees my partitions and so on so it seams to be an ubuntu problem.

Any suggestions?

Thanks for reading so far,
Dex

---

### Post by Pumalite on 2008-11-02
Burn a new CD. Do md5sum, burn at 4x or less. Do not use CD-RW. Clean the lens in your burner.
Download and install ImgBurn:
[http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Once installed; go to Mode>ISO>Burn
Select 1x for your speed of burn.

---

### Post by rdexter on 2008-11-02
Hello Pumalite,

I already checked the md5 sum. For burning, I used InfraRecorder, I burned at 4x speed with a CD-R. Do you think that burning again, with the program you mentioned at speed 1x can solve the problem?

I already had this problem with the pre-release of Ubuntu 8.10.

Dex

---

### Post by Pumalite on 2008-11-02
These OS disks are very sensitive. You don't loose anything with trying. If that doesn't work; try the Alternate CD.

---

### Post by rdexter on 2008-11-02
OK I will do so and report the results.

Dex


Edit:
Reburning the CD with 1x speed did not solve the problem.

---

### Post by piege on 2008-11-02
I have the same problem ... except I'm using unetbootin to spare me some burning ...

it's weird since gparted seems to work fine!

---

### Post by rdexter on 2008-11-02
> **piege said:**
> I have the same problem ... except I'm using unetbootin to spare me some burning ...

it's weird since gparted seems to work fine!

In my situation, gparted on the Ubuntu Linux Live CD does NOT work, but the gparted on different Linux Live OSs works... I do not understand that. Maybe it is a kernel problem? Any ideas how to work around? I had no problems installing Linux on this laptop since this ubuntu release...

---

### Post by Pumalite on 2008-11-02
Did you try the Gparted Live CD?

---

### Post by mhartnett on 2008-11-02
Hi Everyone,

I had the same 8.10 installation problem as rdexter with detecting / creating partitions.  I have an existing trixbox (Centos Linux) install that I want to completely overwrite with Ubuntu 8.10.

You can read the details below but here's the summary of a workaround to get past the partitioning issue:

Short Answer:
-------------
Ubuntu 8.10 Live CD and alternate CD installers both could not detect existing Centos partitions or create new partitions.

So, I wiped HD 1 clean with Autoclave - included on Ultimate Boot CD from [www.ultimatebootcd.com](www.ultimatebootcd.com) (free).  I know, that's pretty extreme.

Then booted up 8.10 Live CD again
gparted now detected HD 1
am currently wiping HD 2 clean with Autoclave
will reattempt install from alternate installer CD and report results.  In any case, gparted can now see the HD 1.

There must be a better solution and I am curious to know it.  But this method looks like it will get you past the partitioning problem.

Sincerely,
Mark


DETAILS:  
--------
HW config:
32-bit AMD Thunderbird 1.4 GHz CPU
Asus A7M 266 Socket A Mainboard
1 GB RAM
2 x 300 GB Seagate Ultra ATA/100 HD

Existing OS:
Trixbox (Centos Linux)

Symptoms - 1st attempt:
-----------------------
Booted from 8.10 Live CD
Attempted to install by double-clicking install folder on desktop
Installer could not partition the first HD
(error message similar to rdexter's)
Cancelled the installation

Launched gparted from Live CD
"No devices detected."

sudo fdisk -l gave no output
sudo fdisk /dev/sda gave "unable to open /dev/sda".

Symptoms - 2nd attempt:
-----------------------
Booted from 8.10 Alternate installation CD
Installer detected both hard drives - called them sda and sdb

Guided partion failed to create partitions on sda
Tried guided partition on sdb next - also failed

Tried manual partitions multiple times.  Could not create any partitions on sda or sdb.

Symptoms - 3rd attempt:
-----------------------
Booted into existing trixbox/Centos
Centos calls HD's hda and hdb (looked under /dev.  No listing for sda or sdb)

Decided to blow away both disks.  Maybe there's something about the Centos filesystem that prevents Ubuntu from reading and partitioning it.
Used Autoclave on Ultimate Boot CD to wipe HD 1 clean.
[www.ultimatebootcd.com](www.ultimatebootcd.com)

Resolution:
-----------
After wiping HD 1 clean, launched gparted from Ubuntu 8.10 Live CD and gparted recognized the disk.  Am wiping HD 2 clean now and will then reattempt partition and install.

---

### Post by rdexter on 2008-11-03
@mhartnett:
I will try your description for solving this problem, thank you very much. On my laptop, windows vista was installed once, perhaps Ubuntu has problems with that...

I will also report the results here.

Dex


Edit:
@mhartnett

I cannot find a tool named autoclave on that boot cd... I downloaded 4.1.1. Where can this tool be found, when I boot up from cd?

---

### Post by Marcel-X on 2008-11-03
I had similar problems in 8.04 64-bit when I upgraded my hardware.
Now I have the same problem upgrading to 8.10 64-bit.

The first time I "solved" this issue by enabling the AHCI mode in the BIOS of my Gigabyte GA-EP45-DS4 for my brand new SATA disk. Unfortunately, it takes more time to boot and the system has random freezes.

This time I want to install without the f**king AHCI, but again there is no disk or partition in the "Prepare partitions" dialogue!

GParted does show my disk and partitions. Also Nautilus can mount the partitions without any problems.

I believe this is an ugly flaw in the install routine.

So try to enable AHCI and see if that make a difference. But think twice before installing on an AHCI enabled mobo!!

I opened a bug report for ubiquity;
[https://bugs.launchpad.net/ubuntu/+bug/293314](https://bugs.launchpad.net/ubuntu/+bug/293314)

---

### Post by Marcel-X on 2008-11-03
Update: I found a workaround for this bug!

Because my disk has already ext3 and linux-swap partitions, the Live-CD will automatic mount the existing linux-swap!

By unmounting (if any) ext2 and/or ext3 partitions, and right-click "Swap Off" on the linux-swap in GParted. The installer now find and display all partitions!

See if this helps!


BTW, this is a very well known issue.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/288675](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/288675)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/291352](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/291352)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/291360](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/291360)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/290415](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/290415)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/84780](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/84780)
etc.

---

### Post by rdexter on 2008-11-04
In my situation, I cannot even see any partitions in the live cd mode... other live cd os's detect them. So ubuntu installer won't mount any partitions.

I tried wiping the disk, but this did not help.

---

### Post by Pumalite on 2008-11-04
> **Marcel-X said:**
> Update: I found a workaround for this bug!

Because my disk has already ext3 and linux-swap partitions, the Live-CD will automatic mount the existing linux-swap!

By unmounting (if any) ext2 and/or ext3 partitions, and right-click "Swap Off" on the linux-swap in GParted. The installer now find and display all partitions!

See if this helps!


BTW, this is a very well known issue.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/288675](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/288675)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/291352](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/291352)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/291360](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/291360)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/290415](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/290415)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/84780](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/84780)
etc.

That why I recommended the Gparted Live CD. It works with unmounted drives/partitions at boot.

---

### Post by Veevose on 2008-11-04
I have a similar problem.
Right now i am using Vista, i have 2 partitions and some free space for instaling ubuntu.
Ok now when i try to install ubuntu on my free space i get this error: "no root sistem defined" (or something like that)
and i cant install ubuntu on my free space altho i have alot of free space for it.
Any suggestions? thank you

---

### Post by Marcel-X on 2008-11-04
> **Veevose said:**
> I have a similar problem.
Right now i am using Vista, i have 2 partitions and some free space for instaling ubuntu.
Ok now when i try to install ubuntu on my free space i get this error: "no root sistem defined" (or something like that)
and i cant install ubuntu on my free space altho i have alot of free space for it.
Any suggestions? thank you

If you are installing and can't continue to step 5 (or 6), you have to assign the free space to "/" (root) first.
Also check "format this partition" for the free space.

---

### Post by Marcel-X on 2008-11-04
> **rdexter said:**
> In my situation, I cannot even see any partitions in the live cd mode... other live cd os's detect them. So ubuntu installer won't mount any partitions.

I tried wiping the disk, but this did not help.

Did you try "System" > "Administration" > "Partition Editor" (gparted)?
Can you post the output of "sudo fdisk -l"

---

### Post by rdexter on 2008-11-04
> **Marcel-X said:**
> Did you try "System" > "Administration" > "Partition Editor" (gparted)?

Yes, I did. GParted stays gray, in the status line at the bottom it says "No devices detected."


> **Marcel-X said:**
> Can you post the output of "sudo fdisk -l"
That's simple: There is no output. Program starts and shows nothing.

I tried it out: Excactly the same code "sudo fdisk -l" works on a other linux live os and shows my hdd. So it is a ubuntu problem.

---

### Post by Veevose on 2008-11-04
> **Marcel-X said:**
> If you are installing and can't continue to step 5 (or 6), you have to assign the free space to "/" (root) first.
Also check "format this partition" for the free space.

Thank you man. 
Now i am running ubuntu 8.10 with no problem (i guess), altho when i selected  the "/" it asked me about the swap thing.... and that somehow will afect the installation, but the intall was fine and its all good now.

P.S the only thing i need to fighure out now is how to adjust the brightness.. its very dark..:P:P

---

### Post by Marcel-X on 2008-11-04
@rdexter

Very strange, this might be an bug in Ubuntu indeed!
You might want to report a bug?
[https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)


@Veevose

Good to hear you are up-and-running.

I have forgotten to mention the swap. In my case I can't assign the linux-swap because I use gparted to chop and format my disk in partitions, even before I start the installer.

So if you don't have the swap and notice performance issues, try to resize the root partition with gparted. And in case of a re-install don't forget to turn the swap off! ;)

I have besides the root and swap, some partitions which I assign in ubiquity and they integrate very nice in the tree.
/home
/music
/usr/local
/windows

---

### Post by boehr on 2008-11-18
> **Marcel-X said:**
> Update: I found a workaround for this bug!

Because my disk has already ext3 and linux-swap partitions, the Live-CD will automatic mount the existing linux-swap!

By unmounting (if any) ext2 and/or ext3 partitions, and right-click "Swap Off" on the linux-swap in GParted. The installer now find and display all partitions!

See if this helps!

I was having the same infuriating problem with the Live CD install. After reading Marcel's advice above, I tried unmounting only my new external (eSATA) hard drive. I didn't want to have to do everything else he suggested so I tried the installer again at that point, and it worked! The partition step showed all my drives accurately. Hooray.

---

