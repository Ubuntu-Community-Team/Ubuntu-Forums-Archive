---
title: "Installing 10.04.3 x64 to brand new drive, system will not POST upon completion TWICE"
date: 2011-10-07
forum: Installation &amp; Upgrades
---

### Post by mdlueck on 2011-10-07
Greetings Ubuntu'ers,

Perhaps someone has seen something similar.

My trusty main Linux machine, still loaded with Ubuntu 9.04 x86.

Intel DG33BUC motherboard, latest BIOS rev
Intel(R) Core(TM)2 Duo CPU E8500

So to upgrade, I purchased a new drive:

Hitachi Deskstar 7K1000.C 0F10383 1TB 7200 RPM 32MB Cache SATA 3.0Gb/s 3.5" Internal Hard Drive

BIOS saw the drive fine, Ubuntu 10.04.3 x64 boots / installed smoothly

Eject the CD, reboot, system WILL NOT POST! I see the nVidia BIOS screen, then blacks out, loan cursor at the top of the screen, FDD light stuck on.

Switch drives back to the 9.04 drive, system boots fine. Switch back, same symptoms.

I end up sending that drive back to Hitachi.

With another brand new drive this evening, the SAME THING has happened.

How can installing an OS to a drive prevent the MB from POSTing!?!?!?

So, back on 9.04. Does anyone have suggestions what might be going wrong?

---

### Post by oldfred on 2011-10-08
I think it was the change from 9.04 to 9.10 (or not, do not get old & forgetfull:)) that I had to start adding nomodeset on LiveCD and first boot with my nVidia card.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place

---

### Post by mdlueck on 2011-10-08
Seems like a "chicken in the egg" situation to me... If I attach the drive which I installed 10.04.3 x64 on, the system will not even POST properly.

I see the nVidia BIOS screen.

Next is a black screen, with cursor, and the FDD light is stuck on.

I never see the Intel BIOS screen.

Previously, 10.04.3 x64 LiveCD had booted perfectly fine and installed the OS to the drive.

Sounds at least similar, though I do not see how a Grub option will resolve a system which will no longer POST properly.

---

### Post by mdlueck on 2011-10-08
Update...

Well the HDD will boot just fine in a system with an Intel P4 631 and Intel 945 based motherboard. (I found it odd it could boot x64 code.)

I tried the various Grub options. None worked.

Finally switching back to my 9.04 drive would not even work... hhhmmm...

Then I noticed the heat sync for the nVidia board laying on top of the SCSI board.

(sigh....) Haffa swap the nVidia board prior to further testing. Perhaps THAT was the trouble all along. (shrug)

---

### Post by oldfred on 2011-10-08
Some Intel board have a BIOS that assumes Windows. You have to have a boot flag on a primary partition or the BIOS will not let you boot. Grub does not use boot flag, but put one on any primary partition if you have no Windows.

---

### Post by mdlueck on 2011-10-14
Update upon dropping a new nVidia board in the system last evening.

On a bare new HDD, I installed Ubuntu 10.04.3 x86 version this time. Same thing happens, MB will not POST with a drive attached which Ubuntu 10.04.3 has prepared.

The 10.04.3 x64 drive boots up just fine in a machine with Intel 945 GNTL MB and Intel P4 631 CPU. Probably this 10.04.3 x86 drive will also boot up in that other machine.

What in the world is Ubuntu 10.04.3 able to do to a drive to prevent the MB from POSTing?

This system has been booting Ubuntu 9.04 x86 perfectly fine on yet another HDD. So I know the system is "Linux Compatible" in general. Suggestions?

---

### Post by oldfred on 2011-10-14
Did you put a boot flag on a primary partition?

---

### Post by mdlueck on 2011-10-14
I popped the drive back into the machine with Intel 945 GNTL / Intel P4 631 which it will boot in and verified the following:

```
mdlueck@jacob:~$ sudo fdisk /dev/sda

[sudo] password for mdlueck: 

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): p

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000f1f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          25      194560   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              25      121602   976565249    5  Extended
/dev/sda5              25        2456    19529728   83  Linux
/dev/sda6            2456      121602   957034496   83  Linux
```

As usual, the Ubuntu installer set the boot partition as active. I have never seen Ubuntu, nor Debian prior to Ubuntu, not set the active/boot flag on the /boot partition.

Also, what ever gripe fdisk has about the cylinder boundary, it was the LiveCD GUI partitioner which created the partitions in the first place.

I am thinking to wipe the disk in the machine which will POST / boot-up and see if putting a wiped disk back into my system results in restoring POST.

---

### Post by mdlueck on 2011-10-14
I used GDisk to wipe the beginning of the drive, C-A-D after a minute or so, and wiping the front of the drive restores ability of my computer to POST correctly.

Evidently Ubuntu 10.04.3 both x64 and x86 do something to drives that make POST fail on Intel DG33BUC motherboards with the latest BIOS version.

---

### Post by mdlueck on 2011-10-14
I logged my troubles here...

"Ubuntu Lucid prevents system POST once installed"
[https://bugs.launchpad.net/bugs/874698](https://bugs.launchpad.net/bugs/874698)

---

### Post by mdlueck on 2011-10-19
I am thinking that perhaps Grub2 is once again causing troubles and would like to select Lilo in its place during installation.

I recall in the past (I thought during 10.04's development) that it was possible to select Lilo in place of Grub2 installing from the Alternate CD. I pulled down the 10.04.3 Alternate X64 and did not see Lilo presented as an option.

In fact what I remembered was a vertical menu of steps to install the system, and installing from that ISO, I never saw the long menu of steps to build the system.

Does anyone know how I may select to use Lilo in place of Grub2 during installation? Thanks!

---

### Post by oldfred on 2011-10-19
I do not think Ubuntu offers any choices on install. You can install anything after the fact. 

We often install just the lilo boot loader as it uses the boot flag to know what partition to boot, to repair Windows boot from a Ubuntu disk.

Not sure how to install the rest of lilo??
Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by mdlueck on 2011-10-22
Thank you oldfred for the suggestions. I was able to clean load 10.04.3 x64 from the LiveCD onto my machine, as usual no POST once loaded.

Then I took the drive to the P4/945 based system, installed Lilo, got that configured. I needed to update /etc/fstab back to using /dev devices and not referring to partitions by their UUID. Then it still wanted to put Lilo on the partition, not on the drive. So hand tweaked /etc/lilo.conf just a bit, and was successful with Lilo.

Next I purged off the two Grub packages.

Finally I took the drive back to my computer... and still will not POST with the 10.04 drive in it.

Any suggestions of what to try next?

---

### Post by mdlueck on 2011-10-23
The trouble has been correctly identified and a work-around found:

An associate I work with was able to correctly identify the trouble with loads of Lucid, Oneiric, and the latest Debian. Turns out there is a HDD geometry incompatibility with these newer distros.

The work-around that masked the situation was to partition the blank drive with Ubuntu 9.04, then reboot to 10.04.3, specify the mount points for the existing partitions, and thus arrive at success.

In my mind, it is absolutely unacceptable for a modern Linux distro to mess up the HDD geometry / partitioning such that at system will no longer POST properly! I ended up RMA'ing a perfectly good / new HDD back to the manufacturer!! Not cool!!! :-x

Reclassifying this report against fdisk and not grub2

---

### Post by oldfred on 2011-10-24
The old gparted (using parted not fdisk) started partitions at sector 63 and tried to use cylinders as the default even though cylinders have not been used since drives when over 8GB and LBA became the internal method of accessing a drive.

Newer partition tools start partitions at sector 2048 for better compatibility with 4K drives, SSDs and other newer systems. Vista was first with sector 2048 start with Windows even before Linux.

So does your system not work with sector 2048 starting partitions? Or is it something else?

---

### Post by mdlueck on 2011-10-24
> **oldfred said:**
> So does your system not work with sector 2048 starting partitions? Or is it something else?

I have no idea. The Intel 945 based board is obviously older technology than a Intel G33 based system. The older board would boot the drive loaded on the newer board just fine.

I just thought of... does the Ubuntu 10.04 LiveCD installer even use fdisk to build the partitions, or does the bug really belong logged to some other project?

---

### Post by oldfred on 2011-10-24
I thought it was the same as gparted or parted which is different than fdisk but I am not sure.

---

### Post by nutznboltz on 2012-01-17
> **mdlueck said:**
> I logged my troubles here...

"Ubuntu Lucid prevents system POST once installed"
[https://bugs.launchpad.net/bugs/874698](https://bugs.launchpad.net/bugs/874698)

Dear Michael Lueck,

Canonical Ltd. does not maintain packages in the "Universe" repository.

The gnu-fdisk package arrives in Ubuntu via a Debian Import "di" process also.

Despite the fact that you are using Ubuntu, the best place to file bug reports for gnu-fdisk is with Debian not Ubuntu.

You also made the mistake of using the launchpad web site to open your bug report.  Ubuntu bug reports should be opened using (at least) the ubuntu-bug command line tool.

I hope this clears up some of your misconceptions about how Ubuntu bug reporting actually works since how it appears to work is wildly out-of-sync with how it actually works.

Sincerely,
nutznboltz
Not affiliated with Canonical Ltd., Ubuntu or Debian

---

