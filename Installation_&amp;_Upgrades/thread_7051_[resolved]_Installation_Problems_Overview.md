---
title: "[resolved] Installation Problems Overview"
date: 2004-12-03
forum: Installation &amp; Upgrades
---

### Post by Nathanael Reveal on 2004-12-03
I've been stumped getting Ubuntu Warty installed at home and though I'd post my problems and my research here to see what other think and can contribute.

**First off, a brief summary of my hardware.**

Intel PII 350 Processor, Award 4.51PG BIOS, 128MB RAM, Seagate IDE 4.2GB Hard disk, IDE CDROM Drive, Belkin 802.11g PCI Card, 3Com NIC (I'm at work so this is my best memory of the parts. I'll update later if I got something wrong.)

**About the Installer CD Itself**

I used the excellent software md5summer ([SourceForge md5summer Project](http://sourceforge.net/projects/md5summer/) ) to check that the CD was okay. There is also a CD integrity option on the install menu that can be used as well. The md5 sums for the various installation CD's is available from the [ Ubuntu Primary Download Site](http://releases.ubuntu.com/warty/MD5SUMS)

Consequently, I'm confident the CD is correct.

**My Installation Attempts**

**Attempt 1**
[list=1]
[*]I did a default installation in English with a US Keyboard.
[*]I declined to setup the network card as the wired network card wasn't connected and I know the Broadcom chip in the Belkin card needs ndiswrapper.
[*]I let the installer partition the entire 4GB drive automatically.
[*]The installation completed to the point where it asked me to remove the CD and reboot.
[*]Upon rebooting GRUB stopped with Error 18.
[/list]

**Discussion of Attempt 1**
According to the [relevant GRUB documentation](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2%20errors), Error 18 means that GRUB cannot access all the files needed to boot because they are beyond the part of the disk accessible by the BIOS.

A bug as been submitted to the Ubuntu Bugzilla ([Bug #2284](https://bugzilla.ubuntu.com/show_bug.cgi?id=2284) )which requests a more graceful handling of this problem by the Ubuntu installer.

The Ubuntu wiki proposes a solution on a [GRUB Error 18 page](http://www.ubuntulinux.org/wiki/WartyWarthogInstallNotes). This page suggests creating a 32MB bootable partition with mount point /boot at the beginning of the disk to hold GRUB. (It seems that it will also hold other files too but I'm unclear which ones. The kernel?)

This is a reasonable suggestion. However, when I researched further into the GRUB documentation, it became clear that, in my case, GRUB probably shouldn't be producing the error. The [features page](http://www.gnu.org/software/grub/manual/html_node/Features.html) of the GRUB manual reports that GRUB supports LBA mode. Therefore, as long as LBA mode was enabled on that drive, GRUB should be able to access my entire 4GB drive.

Any thoughts? It appears that in this case the Ubuntu Installer and GRUB should have "just worked."

I later discovered that the Ubuntu Live CD has a boot option to "Boot from the First Partition." It appears that I could have used the Ubuntu Live CD to try and boot the hard drive installation and proceed with the installation. But by the time I figured this out, I had already moved on to my 2nd attempt.


**Attempt 2**
Every the pragmatist, I tried the solution proposed in the Ubuntu wiki anyway and created a bootable /boot partition at the beginning of the drive.

[list=1]
[*]I did a default installation in English with a US Keyboard.
[*]I declined to setup the network card as only the wired network card wasn't connected and I know the Broadcom chip in the Belkin card needs ndiswrapper.
[*]I created a 32MB /boot partition a 4GB / partition and a 256MB swap partition.
[*]The installation stopped about 80% through the installation of the Ubuntu Core  progress bar and declared: "no installable kernel was found in the
defined APT sources. Current default package is 'linux -386' . You may try to continue though this strange error is probably fatal"
[/list]

**Attempt 2 Discussion**

This has been [previously reported](http://ubuntuforums.org/archive/index.php/t-3444.html) in other places in the forums. A defective CD was suggested. I don't suspect that in my case. Read errors from the CD perhaps?

An interesting parallel between my case and the earlier case is that neither of us had a working network connection.

**Where to go from here?**

I have considered using the [Knoppix Live CD Ubuntu installation](http://www.ubuntulinux.org/wiki/InstallFromKnoppixHowto) approach mentioned in the Ubuntu Wiki. I confess I'm a little intimidated by this approach. If my system didn't respond as expected I wouldn't know how to fix it.

---

### Post by Nathanael Reveal on 2004-12-05
**GRUB Error 18**

Additional research has suggested a possible cause for the error. It appears that since the 2.5.51 kernel, the kernel is reading disk geometry data directly from the disk rather than asking the BIOS. Since the BIOS needs to use LBA mode to address the entire disk, this creates a situation where the installation process appears to break the BIOS settings.

Using the BIOS auto detect, disk geometry settings are reported as:

C: 523 H: 255 S: 63 LBA mode which impliles a size of 4.3GB

But after rebooting and GRUB starts and gives Error 18, the BIOS settings have changed to:

C: 480 H: 32 S 63 LBA which implies a size of 495MB

So now the questions is, how to I fix this? A note on installing the new Fedora core talks about have to explicitly pass the translated disk geometry to the installer. Is this the case with Ubuntu?

Is there another way to fix this without having to reinstall Ubuntu?

---

### Post by Nathanael Reveal on 2004-12-06
**Insight from the Large Disk HOWTO and the cfdisk man page**

The [Large Disk HOWTO](http://www.tldp.org/HOWTO/Large-Disk-HOWTO.html) provides some insight to the question of disk geometry. Based on that, I think the following are true:

[list=1]
[*]The BIOS needs geometry data so that it can boot the disk, i.e. access the GRUB files. If it can't reach the GRUB files, GRUB can't start and access the rest of the disk.

[*]Since GRUB and linux kernel bypass the BIOS disk geometry data completely, the disk geometry data stored in the BIOS doesn't matter except for getting GRUB started.

[*]Provided you can boot from the primary drive, a secondary disk isn't subject to BIOS imposed size limitations since the linux kernel gets geometry data directly from the drive. In fact, it's usually beneficial to tell the BIOS that the second drive doesn't even exist.

[*]The BIOS geometry data isn't static. That is to say, it reads the drive geometry from the partition table. So just because I'm setting it up as C: 523 H: 255 S: 63 LBA dosen't mean it's going to stay that way after the disk is partitioned.
[/list]

**So here's the problem**
Ubuntu, when it partitions my drive, sets the geometry data in the partition table to C: 480 H: 32 S 63 LBA. Which places the GRUB files beyond the reach of the BIOS.

So this leads to these questions... 
[list=1]
[*]Why does Ubuntu do this?
[*]Where does this disk geometry come from?
[*]Can I change the geometry data in the partition table and return it to C: 523 H: 255 S: 63 LBA?
[*]And if I do will this fix the problem?
[/list]

**A Beginning of an Answer**
According to the [cfdisk documentation](http://www.rt.com/man/cfdisk.8.html) I can use it to change the drive geometry stored in the partition table. 

Any cautionary notes aside from the usual "WARNING: This option should only be used by people who know what they are doing."? Of coure, if knew what I was doing, I wouldn't be stuck. Ah the irony.

---

### Post by Nathanael Reveal on 2004-12-07
**Well I solved it.**

Ubuntu is now completely installed and generally appears to be running well.

To get my machine to boot successfully after the initial installation of the Ubuntu core, I changed the BIOS disk geometry settings to Normal which gives CHS values of ~8800 , 15, 63. (I know the 8800 number is rounded down. I just can't remember the exact value now.)

Then GRUB started up and booted Ubuntu and the installation process finished.

The question of course is why did this work?

The data reported by parted still says the 1024th cylinder is at about 495MB. The BIOS still thinks the drive size is 495MB. That's the same size that the BIOS saw using LBA mode. So how is it that the BIOS can now load GRUB completely?

Maybe there's a kernel of truth here than belongs on the GRUB Error 18 page in the wiki, but I'm just not confident enough that I understand why it works.

---

### Post by mage.merlyn on 2004-12-09
I must apolgise from the outset as I am not able to offer any advice on the subject.

However I have been of the 'mistaken' impression that GRUB was 'immune' to the way in which the BIOS handled larger drives, unlike LILO.

For example I have an 80Gb drive on my system the first 20Gb of which is relegated to M$ 2K the remainder to Fedora Core 3. The /boot partition is placed at the beginning of the Fedora install. This is managed by GRUB flawlessly, (so far).

I have experienced none of the difficulties that you have mentioned here, is this perhaps idiosyncratic to Ubuntu. I sincerely hope not as I am about to install a second drive on which to install Ubuntu. 

Thankyou though for providing a well researched and presented commentary of the problem I will be watching this thread eagerly.

Cheers

Dave.

---

### Post by Nathanael Reveal on 2004-12-28
**Resolution of Installation Problems** 

Well, I've tried this on three different Award BIOS 4.51PG BIOS based machines each using the Intel BX440 chipset. These are all variants of a Intel PII or PIII platform. I believe I have figured out the problem. 

As with most things, it was painifully obvious.

At the bottom of the Auto HDD Detection screen is this statement, "Some OSs Like BSD / Linux Require Normal Mode for Installation."

So I ignored other posts that said, "Enable LBA Mode" and chose the "Normal" geometry from the autodetected list of geometry suggestions.

In all three cases, the installation went perfectly smoothly and GRUB booted up with out a hitch.

This is the nugget of wisdom that I'll post to the GRUB error 18 page of the wiki.

Best to all!

---

