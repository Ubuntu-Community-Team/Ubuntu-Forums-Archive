---
title: "How to uninstall Ubuntu versions on multi-Ubuntu computers?"
date: 2011-12-11
forum: Installation &amp; Upgrades
---

### Post by beaucoder on 2011-12-11
Hello - I wish this were a _cheery_ hello.

Multiple computers, desktop & laptop. 
Various Ubuntu versions on them. _No_ Windoze on any of them. 

How to uninstall selected Linux and Ubuntu versions:
  Lucid Lynx
  Linux Mint
  Oneiric Ocelot

How to do this regardless of which partition it is in?

(An aside: Windoze has a simple uninstall. Why not Ubuntu?? Much reading, studying, backing-up, Gparted attempts and GRUB2 edit efforts have been made. No clear answer anywhere.)

Here's hoping I missed a thread or site. (Even better, maybe a utility?)

Thanks,

Ken Wagner 
Sugar Creek, Missouri
Where Ubuntu is sweet....mostly.

---

### Post by bulldog on 2011-12-11
Backup your data if you don't have a separate /home.
If done,just format the partition which you don't want to use anymore.

This action can be done with gparted.
You have to know of course on which partition any ubuntu is installed.

On the other hand,I have never seen an un-installer for the windows os.

---

### Post by CryptAck on 2011-12-11
> **beaucoder said:**
> 
How to uninstall selected Linux and Ubuntu versions:
  Lucid Lynx
  Linux Mint
  Oneiric Ocelot

How to do this regardless of which partition it is in?


Are you trying to free the space or completely remove the partitions? I'm not certain I understand what you mean by "uninstall" selected versions. If you have multiple versions installed (dual booting) and you want to remove the others, you can simply format the extra partitions.

> **beaucoder said:**
> 
(An aside: Windoze has a simple uninstall. Why not Ubuntu?? Much reading, studying, backing-up, Gparted attempts and GRUB2 edit efforts have been made. No clear answer anywhere.)


What uninstall are you referring to? That may help me in understanding what actions you are attempting to perform.

Thanks!

---

### Post by dandnsmith on 2011-12-11
I too am having a problem with what is being said/wanted.

Windows doesn't have a simple uninstall which removes the whole package - only certain application packages. The equivalent for Ubuntu would be apt-get or Synaptic Package Manager.

With the latest grub, you can remove the other Ubuntu releases by formatting the partitions - then run the grub update, and it will rescan and provide a new boot menu leaving out the ones you've removed.

NB make sure you aren't removing/formatting the partition where the grub stuff is.

---

### Post by critin on 2011-12-11
> How to do this regardless of which partition it is in?If you're talking about multiple versions (separate partitions) on several computers, I simply go to Disk Utility, choose the version I want to uninstall and choose Format Volume.  That erases the os and leaves the partition intact for a new OS.

It may not be the 'correct' way, but it works for me and I don't have to partition again.  It then shows as New Volume.

---

### Post by oldfred on 2011-12-11
Your MBR only boots to one install, if that is the one you are keeping then you have no issues, just reformat as suggested above.

But if the install you are deleting is the one in the MBR you need to boot into the one you want to keep and reinstall grub from it. Or else you will have to use LiveCD or another install to reinstall grub2's boot loader to the MBR.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub


If you have more than one drive:
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by beaucoder on 2011-12-11
Hi Guyz,

To make things a little clearer....

Here is what has happened. 

  Computrer #1:  Lucid on sda. Linux Mint on sdb1. I formatted the Linux Mint then no boot from sda. Ran a boot update on this dual-boot from my Lucid install USB. Still no boot. 
  Re-installed Linux Mint, boot is fine and both Lucid and Mint work just fine.

  Computer #2: Lucid on sda, Oneiric on sdb. Waiting on how to proceed. 

Am studying the GRUB2 stuff in help.ubuntu. It looks like the format of the sdb partition is doable. But what if I want to keep the Oneiric on Computer#2 as the main boot? Should I remove sda's Lucid and then make Oneiric the boot drive? Can I then resize the Oneiric partition to use the old sda space or make it all sda? 

Thanks,

Ken Wagner

---

### Post by dandnsmith on 2011-12-11
You can tell the oneiric install (advanced tab, several screens in - watch for it carefully) to put the bootloader on sda, if I recall correctly.
The grub2 setup will then create a boot menu with oneiric as default.

---

### Post by beaucoder on 2011-12-11
> **dandnsmith said:**
> You can tell the oneiric install (advanced tab, several screens in - watch for it carefully) to put the bootloader on sda, if I recall correctly.
The grub2 setup will then create a boot menu with oneiric as default.
Hi dandnsmith -

This advanced tab - is it part of the install setup where the partitions are selected and we can set which one is to be the boot? If so, this Oneiric install would be unnecessary because Oneiric on sdb partition is the one I may choose to keep. 

Or is this an advanced tab in Gparted?  Does Gparted allow me to move the bootloader? (And do I have to? If Lucid in sda is removed, must the bootloader be on sda?) Not clear to me at this point. 

Thanks,

Ken Wagner

---

### Post by Cookieh on 2011-12-11
Thanks. Had to unistall my multiboot computer ubuntu os, and couldnt want to unistall all of partitions...Thanx :P

---

### Post by dandnsmith on 2011-12-12
> **beaucoder said:**
> Hi dandnsmith -

This advanced tab - is it part of the install setup where the partitions are selected and we can set which one is to be the boot? If so, this Oneiric install would be unnecessary because Oneiric on sdb partition is the one I may choose to keep. 

Or is this an advanced tab in Gparted?  Does Gparted allow me to move the bootloader? (And do I have to? If Lucid in sda is removed, must the bootloader be on sda?) Not clear to me at this point. 

Thanks,

Ken Wagner


Ken - it's part of the install setup, cannot remember exactly how far in. Thus, if you want to retain the current installation of Oneiric on sdb, then you could, from inside your Oneiric or from a LiveCD, install grub, specifying where you want the bootloader to reside.

It's nothing to do with gparted operations.

HTH

---

### Post by beaucoder on 2011-12-12
Hi Guyz,

First attempt:
  1. I formatted the sdb Linux Mint partition, 2nd partition. (1st is Lucid)
  2. When I rebooted I got to **grub rescue>**
  3. sudo update-grub does not work here. I did not expect it would.
  4. I could only boot from a live USB. So I did a live Lucid boot.
  5. Trying to run 'sudo update-grub' from partion 1, sda, on HDD1 fails because no device is mounted. (I tried to mount the HDD 1 of 2, not the USB.)
  5. Could not 'sudo mount /dev/sda'. This, too, failed with a message that it could not be found. (Although, /proc/partitions showed 'sda')
  6. Thus I could not update or reconfigure the grub on the first partition of HDD1 which is the normal MBR on this system. 
  7. I then used RescaTux, a utility to restore linux boot records and grub configurations. This went without a glitch.
      a. Reconfigured GRUB
      b. Ran the Update-Grub. 
      c. Reboot ran as expected.
      d. Rebooted from USB and deleted the sbd partition. It then reallocated to sda. 
      e. Rebooted from MBR on HDD1 and all is now running well. 

  8. Why did the 'sudo update-grub' fail on the sda partition on HDD1?
      a. Could not find or mount /dev/sda.
      b. What other commands would do so?

Thanks,

Ken

---

### Post by beaucoder on 2011-12-12
> **dandnsmith said:**
> Ken - it's part of the install setup, cannot remember exactly how far in. Thus, if you want to retain the current installation of Oneiric on sdb, then you could, from inside your Oneiric or from a LiveCD, install grub, specifying where you want the bootloader to reside.

It's nothing to do with gparted operations.

HTH

Hi Dan,

Yes, I remember the partition-configure page of the Live USB install. And that I can flag the partition as the boot. I will use that on my other computer, a laptop. 

Yet, after formatting the sdb Linux Mint partition, I could not reboot. Only got to grub-rescue. Not aware of any grub-fix command at the grub-rescue command line. Is there one? 

From a Live Lucid USB I used xterm and cd'd to HDD1 of the 2 hard drives. Then to the sda partition of HDD1. 'sudo update-grub' could not find sda. sudo mount /dev/sda would not mount it. 

Could not proceed at this point. 

But, I found a utility called RescaTux which will reconfigure the grub and update it. 

BUT!!!  I would really prefer to know how to do this from within a Live USB after the 2nd unwanted Linux partition is either formatted or deleted. 

Thanks,

Ken

---

### Post by oldfred on 2011-12-12
Some links to instructions on reinstall grub from grub rescue or grub>. But if Ubuntu has install issues then grub may not boot it and the other methods may be required like you did.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Two repair or boot methods:
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by beaucoder on 2011-12-13
Aha!!  Some excellent progress.

If I boot normally from the hard drive using Lucid in /dev/sda and then do the following:
 
  1. Use Gparted to delete the 2nd Linux Mint partion (sdb)
  2. Resize the first partition to gain the space from the deleted (sdb) Linux Mint partition.
  3. Execute:   (while remaining in current Lucid session.)
      a. sudo grub-install /dev/sda
      b. sudo update-grub
  4. Rebooting

...then the system will reboot as a single Linux install with the full space on the first hard drive restored to the first (Lucid) partition. 

Works nicely. 

It will be a week or two before I work on doing the reverse on my laptop, namely, keeping the 2nd partition with Oneiric and deleting the first partition with Lucid and adding the space from the deleted Lucid partition to the Oneiric partition. 

What I hope to do here is just delete the Lucid partition and then mark the 2nd Oneiric partition as boot, which I believe it already is. 

I will report back on this effort when it is attempted. 

Thanks for all your help and suggestions. The GRUB2, grub-rescue and boot repair references have greatly enlightened me. (Or so it seems. This boot business is slowly beginning to make sense even though it does seem somehow rather obtuse.)

Ken

---

