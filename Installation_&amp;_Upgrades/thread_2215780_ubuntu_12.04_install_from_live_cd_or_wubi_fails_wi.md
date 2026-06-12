---
title: "ubuntu 12.04 install from live cd or wubi fails with Windows 7 BIOS machine"
date: 2014-04-08
forum: Installation &amp; Upgrades
---

### Post by Anon_Ymous on 2014-04-08
My pc is an HP Pavilion Slimline S5000. I checked the setupact.log to assure I boot in BIOS and not UEFI. I won't try an older version or different distro until I get some enlightenment here, including about lilo instead of grub.

A couple years ago, I had a dual boot running fine on this machine, did the install when I first got it, but don't remember if it was from an exe or live cd. Anyway, it was one or two versions ago of ubuntu. 

My Windows 7 this past winter got some very tenacious malware, so to save me time and trouble, I just used the restore factory default from my D drive. I let the installation wipe out my ext4 and swap partitions, figuring I would want to install the latest version of ubuntu anyway.

My HD then consisted of a 100mb SYSTEM primary partition, a very large C drive primary with Windows 7 and the boot, and a D drive where the OS recovery is, which is also primary.

First I tried the easy install from the ubuntu live cd, in which I could choose alongside my existing Windows 7. Upon restart, I never saw any GRUB loader, and ubuntu froze at login. I used the live cd and tried the lilo fix, the ms-sys, and boot-repair. I did not know enough about the kernel to run liloconfig 8 and after trying to find the steps how to do it for over an hour, installing and running ms-sys and getting error messages about not being able to read something, I gave up and ran boot-repair. Boot-repair told me a wubi was broken, which did not make sense to me because I wasn't installing via an exe. However, upon restart, I was able to boot the pc and it went directly to Windows 7, no loader, no ubuntu, but the disk manager showed me the ext4 and swap were still there and healthy.

So then I decided to try the wubi exe installation. Maybe I should not have done this, but first I went ahead and created free space out of the existing ext4.  I don't remember what happened to the swap, but when I was done, I had a partition with a lot of free space waiting for ubuntu.

Then I ran the windows installer from ubuntu. This time, I did get a loader. I was able to choose Windows 7 and boot it no problem, but the ubuntu boot would freeze at the log in screen, that cute little bongo stuck on about thirty beats, and then just solid brown.

I left the solid brown there for about 30 minutes, and finally somehow Windows stepped in and asked me if I wanted to attempt to repair. I chose that, but I got the message that it was unsuccessful and did I want to try the system restore to an earlier point. I did that and was told the restore was unsuccessful. I restarted, booted Windows 7 from the loader, deleted the ext4 partition, extended the C partition, and on log off was told a system restore was successful. That message applied to changes that took place before I extended the C partition. Silly Windows.

I did write those addresses from boot-repair to use them later, but I thought I would post here first. 

I think ubuntu rocks, have been able to use WINE on an old acer netbook I had converted to ubuntu, etc. I need Windows 7 for some proprietary software that won't run on WINE, but otherwise I routinely use ubuntu and don't mind learning to use the terminal as I go.

---

### Post by oldfred on 2014-04-08
12.04 is the last version that will have wubi. All new systems are UEFI with gpt partitioning and wubi does not work on gpt partitioned drives.

Better to have full install, but you need the 4th partition to be an extended partition, so you can have Ubuntu in logical partitions in the extended partition. Most Windows 7 installs use all 4 partitions.

         My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by Anon_Ymous on 2014-04-08
I see, so because I already have THREE (according to disk manager in windows) partitions (not 4) I can't have the ext4 AND the swap? I will check out all links given, but I thought the four partition problem didn't apply to me because my machine has BIOS, not UEFI and I found only three partitions. Thanks! Will close as solved after I review linked sources and I will report back how I will have succeeded.

---

### Post by oldfred on 2014-04-08
You use the last primary partition as an extended partition. The extended partition then is a container for as many logical partitions as you want or need. Only Windows needs a primary to boot from, Ubuntu will boot from an ext4 logical partition just fine.
Often a good idea to shrink Windows a bit more and use a shared NTFS data partition for any data you may want in both systems. I put Firefox & Thunderbird profiles in shared NTFS partition.
Use Windows partition tools to shrink Windows NTFS partition and reboot immediately so it can run chkdsk. Then either install into unallocated space with available primary partition and installer will create two logical partitions one / (root) and the other swap.
If you want other partitions like shared NTFS or /home you should then partition in advance with gparted, but still have to use something else or manual install to choose which partition is / , if swap exists it seems to find that automatically.


It is with the new UEFI with gpt partitioning where there are no primary, extended or logical partitions, or in effect all partitions are primary.

---

