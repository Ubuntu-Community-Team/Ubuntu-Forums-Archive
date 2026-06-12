---
title: "Lubuntu Precise 64 won't install grub on usb external HD - other distros work fine"
date: 2013-01-08
forum: Installation &amp; Upgrades
---

### Post by Dreamer Fithp Apprentice on 2013-01-08
When I try to install Lubuntu 64 bit Precise to a usb external HD, either from remastersys made backups of tweaked systems that no longer live on my internal drives or from the Lubuntu Precise standard installation cd it fails at the last step, installing grub. It offers to retry and lets me select from sdx or sdx1 to try in. Either way, no matter how many times I retry it fails the same way. I had the same experience installing to either of 3 different usb external drives, one Toshiba, and 2 Western Digitals. I don't have an internal HD partition to try this with.

But if I install from a remastersys made backup of a Karmic system or from a PClinuxOS live/installer cd, selecting, in the latter case, grub graphical boot manager, it works fine. I know in the past I had no trouble installing Lucid to usb external HDs including the one of the ones Precise can't put grub on.

So, is this likely to be because the grub version in Precise is such a space hog it won't fit on the external drive's mbr? Did the change from grub "legacy" to grub "2" (I use quotes since there ARE official version numbers and if I remember correctly both are < 1) take place in between Lucid and Precise? Right now I'm posting from the PClinuxOS system installed to the usb external HD and the grub version is 0.97-27pclos2011. I did update the system after installing it so it is possible that might not be the version that was first installed.

If that is the likely cause can anyone suggest a way around it? I tried making a bootable thumb drive from a Lubuntu Precise CD, trying each of several sets of instructions found here and elsewhere, and trying different thumb drives as well. It seems to work, and there are no error messages but the resulting thumbs don't boot despite being enabled in the bios. I mention this not to drag in another issue but some of the ways to get around the problem I thought of involved booting from a thumb. Assuming Grub "2" is the problem, could I install some other boot loader to the usb drive while booted from a live disk?

Or am I on the wrong track alltogether? Is there some other property that Karmic, Lucid, and PCLinuxOS (all 32 bit) installers share that the Precise 64 bit installer doesn't? I HAVE installed the 64 bit Precise on internal HDs on this same machine with no problems in the past but that isn't an option right now. I DON'T recall trying to install it (or anything post Lucid) on an external drive before. Maybe Precise just doesn't like external drives?

---

### Post by oldfred on 2013-01-08
I do have grub2 installed on my flash drives, but I use gpt partitioning and have to have a separate bios_grub partition for core.img.

When you formatted flash is there space from MBR to first partition? First partition used to start at sector 63 and all new systems now use sector 2048 which gives lots of room for core.img. Grub not only uses MBR but adds a lot of code with core.img in the space right after the MBR. Grub legacy had its early boot stage in the same location but it was smaller.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by sudodus on 2013-01-08
I've done it with Lubuntu 12.04 non-pae (the default 32-bit version). I installed a system via USB 2 and this system is an 'installed' portable system, that works well.

I have installed Lubuntu 12.04 64-bit to an internal drive, but not to an external one. I'm surprised that it does not work for you.

Did you try (from the Lubuntu install CD drive) to use some of the tips of this link?

[https://help.ubuntu.com/community/Grub2/Installing]("https://help.ubuntu.com/community/Grub2/Installing")

*Edit*: I make the partition(s) with ***gparted***, and it makes it start at sector 2048 (leaving 1 MB), as recommended by oldfred.

---

### Post by Dreamer Fithp Apprentice on 2013-01-08
Thanks guys. Several ideas here worth pursuing. I'll back up this PClinuxOS system and retry the Lubuntu Precise tonight or tomorrow and let you know.

---

### Post by Dreamer Fithp Apprentice on 2013-01-11
I reinstalled a lubuntu to the same partition, wiping out my working pclos. Still won't boot. Installed and ran boot-repair from the live disk. Results:

[http://paste.ubuntu.com/1519280/](http://paste.ubuntu.com/1519280/)

Still won't boot. I emphasize, I have no trouble installing Karmic, Lucid, or Pclos to this partition.

---

### Post by sudodus on 2013-01-11
I see the following which is different from the normal layout of new hard disk drives:

```
Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500074283008 bytes
255 heads, 63 sectors/track, 60797 cylinders, total 976707584 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *            [COLOR="Red"] 63[/COLOR]    41,945,714    41,945,652  83 Linux
```
It is an old layout. The new layout, that is used by for example gparted, is that the first partition starts at sector 2048 (leaving 512*2048 = 1 MB for boot purposes at the beginning of the drive). Maybe this is causing problems with the new Ubuntu (and Lubuntu).

Probably oldfred can find more ...

---

### Post by oldfred on 2013-01-11
How large is your core.img? I believe the copy in /boot/grub is the same as the one written into the sectors after the MBR.

My core.img is now 26048 (26kB in Nautilus) which means it needs 51 sectors of 512 bytes so it fits between 0 & 63. 
But perhaps something is making it larger for you?

---

### Post by Dreamer Fithp Apprentice on 2013-01-11
Thanks again, guys.

Sudodus, I've already tried creating that partition with more unused space before it.  I think I gave it a couple of miB but I may misremember and it might have been on one of the other 2 drives I tried to make bootable so I'll try it again.  I think what is there now is what the Lubuntu installer in manual partitioning mode defaulted to.

Oldfred, ls -l gives me

/boot/grub/core.img
 -rw-r--r-- 1 root root 26052

Pcmanfm calls that 26.1 KB.  I suppose it's possible 4 bytes might push it over the limit.

Anyway, I'll try again leaving a pot full of unallocated space and let y'all know.

---

### Post by Dreamer Fithp Apprentice on 2013-01-12
I deleted the partition and replaced it with gparted, leaving 10 mb of unallocated space before it.  When gparted finished it had adjusted that to 7.8 mb.  Anyway, plenty I should think. Same story. Installation goes fine up to grub installation and then fails.

I'm going to try to figure out how to install grub legacy or LILO.  I'm not that familiar with chroot but if I understand it correctly ```
chroot /sdx1
``` should put me in an environment where changes I make to the system will be made to the system installed in sdx1, not to the gvfs system of the live disk. From there I'll try to install grub legacy. If that doesn't work I'll look around for something I can boot with to install a bootloader, preferably not grub "2". Doing it that way will mean I have to wipe out the Lubuntu so I can install something that works so I'll have my cd drive free to burn a disk. A pity I can't make it do the old A/B shuffle like we used to do when we needed 2 floppy drives and only had 1.

---

### Post by sudodus on 2013-01-12
Have you checked if there is some hardware error on the drive, for example some bad sector near the head of the disk space, that does not work properly to read/write?

As a starting point, check the S.M.A.R.T. status

---

### Post by Dreamer Fithp Apprentice on 2013-01-12
Thanks for the suggestion.

gsmartcontrol 0.8.6 summarizes as "passed". But I do see "read failure". Not sure what LBA means but if that figure is bytes I think it corresponds to about half a gb.

Hard to imagine this as a disk failure problem though since I have the same problem with either of 3 usb external hard drives, one of which is new, AND since I have installed Karmic and PClinuxOS repeatedly to this same drive with no problems in the past couple of days and have installed various versions of Lucid and, I think, Maverick, to it in the past. I can't SWEAR I've installed a 64 bit system to it but I think I have. Seems to me this is almost certainly a problem specific to Precise, and probably grub "2". The installer suggests installing a boot loader later after failing to do so and I think that is probably the right approach but so far I have not succeeded. I've burned a boot-repair bootable CD and I will look for anything else in the way of a bootable CD iso that may can do this. Trying to repair it with a bootable CD, unless it is one I already have is a major PITA because I have to wipe out the Precise and install something that works to burn the CD, so I want to have all of the likely candidates burned before I try that again.


General SMART Values:
Offline data collection status:  (0x80)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 121)    The previous self-test completed having
                    the read element of the test failed.
Total time to complete Offline 
data collection:         (14280) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 141) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x7035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       37
  3 Spin_Up_Time            0x0027   152   148   021    Pre-fail  Always       -       3383
  4 Start_Stop_Count        0x0032   096   096   000    Old_age   Always       -       4116
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -       5785
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1014
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       249
193 Load_Cycle_Count        0x0032   046   046   000    Old_age   Always       -       462573
194 Temperature_Celsius     0x0022   115   104   000    Old_age   Always       -       32
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       3
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%      5785         512899424
# 2  Short offline       Completed: read failure       90%      5785         512899424

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

---

### Post by YannBuntu on 2013-01-12
hi

> =================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:512:msdos:WD My Passport 0730;
1:**32.3kB**:21.5GB:21.5GB:ext4::boot;


Please use Gparted to increase the free space which is at the start of your disk (before sda1) from 32KB to 1MB.

Then run Boot-Repair and tell us the new URL that w ill appear.

---

### Post by sudodus on 2013-01-13
> **Dreamer Fithp Apprentice said:**
> Thanks for the suggestion.

gsmartcontrol 0.8.6 summarizes as "passed". But I do see "read failure". Not sure what LBA means but if that figure is bytes I think it corresponds to about half a gb.

This link describes a similar situation
"In this example, the disk is failing self-tests at Logical Block Address LBA = 0x016561e9 = 23421417. The LBA counts sectors in units of 512 bytes, and starts at zero."

[[COLOR="Red"]http://smartmontools.sourceforge.net/badblockhowto.html[/COLOR]]("http://smartmontools.sourceforge.net/badblockhowto.html")
Maybe you can read the details and try to understand more about it.

But there is also
```
SMART Error Log Version: 1
No Errors Logged
```
in the output, and since you have tested also other drives, I agree, there is probably some other error with precise.

Could it be that you have some hardware, that is causing problems when trying to find and/or load a driver for it? Sometimes the installation fails because of the graphics or wifi chip/card.

In such cases it's worth trying to disable wifi (if possible with a switch or in the BOIS menu system). And if you have a graphics card and at the same time built-in graphics on the motherboard, unplug the graphics card.

It is also worth testing with various boot options. If you have no other idea, start with ***nomodeset***, and test them, one or more at the same time.

[[COLOR="Red"]https://help.ubuntu.com/community/BootOptions[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

---

### Post by Dreamer Fithp Apprentice on 2013-03-11
Thanks, Sudodus. Sorry for losing track of this thread.

 No, I couldn't find any hardware fault.

I find I can install Oneiric 32 bit with no problem on either the first or second partition of the same drive and can then upgrade to precise successfully. After upgrading I can remaster the system with Remastersys and then I can reinstall a 32 bit Precise with no problem. I have not yet tried doing this with the 64 bit version though. When I do, I'll post the result. I mention this for the benefit of anyone who finds their way to this thread in the meantime because they have similar problems.

So in summary, at the moment I've established:
On this hardware installation of several older 64 bit systems works normally.
64 bit Precise installation fails.
32 bit Oneiric installation works normally and can be upgraded on the hard drive to Precise which can then be used to remaster a CD from which 32 bit Precise installs normally.

I'll try again with the 64 bit Precise when I have a chance and post the result.

---

### Post by sudodus on 2013-03-12
I'm glad that it works with Remastersys :-)

It may be worth trying Xubuntu 12.04.2 LTS, which is well debugged and polished compared to the earlier downloadable iso files. Unfortunately Lubuntu has no LTS, so today you should try Lubuntu 12.10 rather than 12.04.

---

### Post by Dreamer Fithp Apprentice on 2013-04-17
Thanks for the patience and thinking, lads. I'm still not sure what caused all this. Nor what fixed it. But in case it can help anyone with similar problems, here is the update:

Fiddled around with several things on this partition. I was using a 32 bit Lubuntu Precise, installed as Oneiric and upgraded on the HD, for a while with only minor problems. Mainly a recurrent problem with the graphical login wanting to add all sorts of non-human users to my login choices. Not more than a minor annoyance but it might tell somebody something. Anyway, one day I decided to try to make the @##@!!@@###!! default size 0.001 fonts used by grub "2" into something readable by earthlings, and read up on it a bit. Wasn't the same technique I had successfully used in the past but it seemed simple enough. I was supposed to uncomment one line in a grub config file to change the screen resolution from whatever the monitor defaults to to a lower value. I made sure the new value was supported by the monitor. Absolutely. And then I removed that one little "#" and darned if didn't not only make both the bootable partitions I have on this drive unbootable it somehow also made it impossible to install ANYTHING, or at least any of the half dozen or more things I tried to EITHER partition. After trying a lot of stuff that didn't work, I removed both partitions (sda1 and sda2 for me, and physically the 1st and second partitions) that had supposed-to-be-bootable systems and replaced them with 2 of about equal size, whereas before they were more asymmetric. So now they are about 30 GiB each as opposed to about 20 and 40 before. Then I reinstalled the system I had not been having any problem with on one of them from a Remastersys backup and - drum roll- installed Lubuntu Precise, 64 bit, from the same installation CD that had failed me before on the other and now it worked fine. And has been for a couple of weeks (guessing) now. Not sure why this should be. It seems to me when I adjusted the size of the partition I was installing to earlier I was rewriting the MBR, so it can't be the mere fact or rewriting the MBR that did the trick. But I did SUBSTANTIALLY change the size of the partitions whereas before I had made only small changes in size. Also the system that had given me problems before had been on the smaller partition, around 20 GiB. I would have thought that was plenty big, but maybe I'm wrong. Or maybe there was some flaky part of the drive that was in a crucial area and resizing the partition by 10 miB or so wasn't enough of a change to put it in some more harmless area but resizing by 10 giB was. Or maybe the God of Electrons is just through being p'd off at me. Must have been that mosquito I ritually sacrificed with a tiny obsidian knife on an alter made from an old 64 k ram chip.

---

### Post by Dreamer Fithp Apprentice on 2013-04-18
I'd mark this solved or, failing that, edit the title to show [solved], but neither the thread tools nor the edit function will work for me right now.

---

### Post by sudodus on 2013-04-18
Thanks for sharing :-)

There might be a bad sector on the HDD, that is not used now. You have checked with the S.M.A.R.T. information, but did you check the file system? Anyway, it is hard to find the problem now, that it's gone.

You can find how to make this thread SOLVED at this link

[[COLOR=#ff0000]http://ubuntuforums.org/showthread.php?t=2121377[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2121377")

---

### Post by Dreamer Fithp Apprentice on 2013-04-19
Thanks again. But, sorry, those directions don't work if the initial post is too old because the edit function locks out after a time. Makes sense when edit is being used for the normal purposes. It'll just have to wait until the normal [solved] function is fixed. I'll be glad to send the admins a copy of the incantations I used on the mosquito if they think it would help. But they'll have to supply their own sacraficial insect. Or maybe I should say "bug".

---

