---
title: "Boot problem after upgrade to Ubuntu 15.10"
date: 2015-10-21
forum: Installation &amp; Upgrades
---

### Post by yang6 on 2015-10-21
Hi All,
After I update to Ubuntu 15.10 with kernel 4.2.0-16-generic, I have boot problem.
When I try to use boot-repair, and I always first got grub boot menu but hang in "Switching clocksource" or directly jump to "No video mode activated, [COLOR=#6A6A6A][FONT=arial]**invalid video mode**[/FONT][/COLOR][COLOR=#545454][FONT=arial] specification '[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**text**[/FONT][/COLOR][COLOR=#545454][FONT=arial]'. "[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**booting in blind mode**[/FONT][/COLOR][COLOR=#545454][FONT=arial]".[/FONT][/COLOR]
My pc has a nvidia gfx 970 card. And it seems I also messup with my grub.

Is there a way to reinstall grub and not reinstall Ubuntu?

I have no problem to boot from livecd. So I wonder how I can fix it?
Currently I can first boot into livecd, and Ctrl+Alt+F1 to switch to terminal and mount the root system.

Thanks for any suggestions. I already stucked on this problem for two days.

Yang

---

### Post by james_moore2 on 2015-10-21
(Sorry for any bad answers kinda new to Linux (***_use to be_*** a Windows fan.)) I don't think there is a way. Maybe you can boot from the livecd, and try to reinstall GRUB.
Again sorry for any bad answers.

---

### Post by oldfred on 2015-10-21
Can you boot with nomodeset?

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

      
 Ubuntu Launches Its "Fresh" Proprietary Driver PPA
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

   # Shows standard repository versions
ubuntu-drivers devices
sudo apt-add-repository ppa:graphics-drivers/ppa
# should show newest versions available in addition
ubuntu-drivers devices
sudo apt-get update && sudo apt-get install nvidia-3xx
# I usually use nvidia-3xx-updates, where 3xx is newest available, if older card do not install newest version, check correct legacy version from nVidia.
# While you're at it upgrade libvdpau & nvidia-settings

---

### Post by yang6 on 2015-10-21
I did reinstall of nvidia drivers and using boot-repair. Now it did show Grub menu.
But after a long pause (around 3 minutes) in "Switching to clocksource tsc",
Then it shows 
findfs: unable to resolve 'LABEL=writable'
done.
ext4
[ ] initrd:: mounting /dev/mapper/ubuntu-vg-root
[ ] EXT4-fs (dm-0) couldn't mount as ext3 due to feature incompatiablity
[ ] EXT4-fs (dm-0) couldn't mount as ext2 due to feature incompatiablity
[ ] EXT4-fs (dm-0) mounted filesystem with ordered data mode. Opts....
cannot find 'writable' partition

 Then it enters into busybox.

The boot-repair has bootinfo here [http://paste.ubuntu.com/12891093](http://paste.ubuntu.com/12891093)

---

### Post by oldfred on 2015-10-21
You have a variety of drives all different.
You have gpt partitioned drives & MBR(msdos) partitioned drives.
And you have UEFI and LVM on sdc.

I do not know LVM as that is an advanced logical partitioning  which for some has advantages.
       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)

I suggest for long term planning to use gpt partitioning and probably UEFI. I started converting to gpt with every new drive when UEFI first started, but booting in BIOS mode. That made my conversion to UEFI a bit easier as I already had and understood gpt partitioning.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

   UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by yang6 on 2015-10-22
I install ubuntu on a samsung ssd, and windows on 1T HDD, another ssd is empty.
I want to restore ubuntu since I don't want to reinstall all stuff I installed on the disk.

I really hope someone can help me out.

Thanks

---

### Post by oldfred on 2015-10-22
If you turn on UEFI and turn off CSM/Legacy/BIOS can you boot ubuntu entry in UEFI?
And can you turn off UEFI and turn on CSM and boot Windows from drive that is sdb. It shows Vista? Is that correct?

The grub installed to the MBR of sdc, should not now work for BIOS boot, as grub has been reinstalled to boot in UEFI mode from ESP on sdc.

---

### Post by yang6 on 2015-10-23
If I set to legacy boot, I can boot into window 10.
If I set to UEFI boot, it will show grub menu, I can only boot into busybox.

I can use livecd to boot into Ubuntu and chroot to mound LVM partition. But I don't know why uefi boot cannot boot into ubuntu.

[ATTACH=CONFIG]265116[/ATTACH]

---

### Post by oldfred on 2015-10-23
Have you tried recovery mode, or one of the older kernels?

Do not know enough about LVM specific issues to really help.

---

### Post by yang6 on 2015-10-23
Solved. I use live cd and choose to install Ubuntu. 
When select install partition stage, ubuntu will show the partitions already created. [B]Don't Format
[/B]
Chose mount point for each partition, and then select continue. The grub installer will be reinstalled correctly.
After it, it still have some issues, but at least I can boot into text mode and fix all other issues.

---

