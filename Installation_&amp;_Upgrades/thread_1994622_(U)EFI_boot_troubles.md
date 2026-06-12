---
title: "(U)EFI boot troubles"
date: 2012-06-03
forum: Installation &amp; Upgrades
---

### Post by Axxon95 on 2012-06-03
I just came back from having a good run with Linux Mint 13 x86_64 with EFI booting, but it all the sudden isn't working... so I came back to Ubuntu for another round.

Since I have gotten my new hardware, I've been having issues with almost Every Linux distro I threw at it. The only Ubuntu that works perfectly(not in UEFI) is 10.4, but it's a little older, and I'm a person for modern stuff.

Hardware:
Asus P8H61-M LE/CSM (latest Asus/Intel UEFI bios)
i5 2500 + Intel HD Graphics(you'll see)
EVGA NVIDIA GTX 460
Measly little 40GB I had around

Ubuntu 12.4 x86_64(via LiveUSB)
The whole issue is about the video(not drivers, just video in general), keeping me from booting.
First, I can't boot into EFI mode, I just get rebooted and it doesn't continue.
Second, I attempt normal boot, and get no video and stops booting.
I then try normal booting in compatibility, and see the reason it has no video.
I get conflict similar to stating "EFI Intel VGA vs nouveau" and that's when it stops booting and locks up.
(The only alternative is to boot using Only my onboard graphics, and installing the Ubuntu-X NVIDIA proprietary drivers, and it still results in bugs in the future, because of having switched from Intel graphics to NVIDIA. I get minor bugs. Ubuntu-X has yet to fail on me.)

Does anyone know what I should attempt to do next?
I've heard Linux Kernel 3.3 supports EFI bootloaders by default, or something to that extent. Anyone know when Ubuntu plans to use it in an ISO?

I've been trying for a week or 2 now and have had little success.

(Figuring that it is a booting/installation issue, I put it here rather than Hardware, so if I posted this in the incorrect forum, sorry.)

---

### Post by Paddy Landau on 2012-06-03
I'm sorry I can't solve your problem. However, have you considered disabling UEFI in the BIOS? At this stage, UEFI is pretty new and the problems (at least regards Ubuntu) have not been ironed out yet.

---

### Post by oldfred on 2012-06-03
I do not know how to add nomodeset for a nVidia card with UEFI boot.

All that have installed UEFI have partitioned in advance and then loaded USB or CD with UEFI in efi mode to install. But then video can still be the issue.

This is how to add nomodeset with BIOS boot. It may be possible to format with gpt partitioning  with both efi partition and bios_grub. Install in BIOS mode and then once nVidia is working reinstall grub in efi mode.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

GUIDE: (U)EFI installation Also full install post *52 superfreak
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)
Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)

Someone posted this on relabeling entry:
> Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 


If you only have 40GB, I would not have a separate /home.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
If gpt(not MBR) partitioning include these first - all partitions with gpt are primary
    250 MB efi FAT32
    1 MB bios_grub  no format 
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

---

### Post by Axxon95 on 2012-06-03
> **Paddy Landau said:**
> I'm sorry I can't solve your problem. However, have you considered disabling UEFI in the BIOS? At this stage, UEFI is pretty new and the problems (at least regards Ubuntu) have not been ironed out yet.

I have tried, and It disables all USB ports. My MB only has 1 PS/2 port and it serves to be used as a mouse, or keyboard(so I think), and I can only have 1 plugged in at a time.

---

### Post by Axxon95 on 2012-06-03
> **oldfred said:**
> I do not know how to add nomodeset for a nVidia card with UEFI boot.

All that have installed UEFI have partitioned in advance and then loaded USB or CD with UEFI in efi mode to install. But then video can still be the issue.

This is how to add nomodeset with BIOS boot. It may be possible to format with gpt partitioning  with both efi partition and bios_grub. Install in BIOS mode and then once nVidia is working reinstall grub in efi mode.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

GUIDE: (U)EFI installation Also full install post *52 superfreak
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)
Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)

Someone posted this on relabeling entry:


If you only have 40GB, I would not have a separate /home.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
If gpt(not MBR) partitioning include these first - all partitions with gpt are primary
    250 MB efi FAT32
    1 MB bios_grub  no format 
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical


I'll try that again when I get the chance.
For some reason, I believe when going into Legacy mode on my MB, it disabled USB. I have yet to install a DVD drive into my computer, I use an External USB DVD drive(power cord and USB cord is shared between that and my 1TB storage which are 1 on top of the other).
I guess since a new gparted is out(even on that, I get the same EFI Intel VGA vs nouveau, but EFI booting does work), and I have a little more knowledge, I'll try again and hopefully succeed.

---

### Post by oldfred on 2012-06-03
You had boot files in the efi partition. Does the shift key work to give you the grub menu. There was a bug on shift key not working.  But if you can get to grub menu then you can add the nomodeset.

You should be able to boot liveCD/USB versions from USB flash drives in BIOS or UEFI mode.

I am not sure vendor's all have resolved their own issues with the new UEFI as it does a lot more than BIOS used to. I would make sure you have the latest revision.

---

### Post by Axxon95 on 2012-06-03
Sorry for the delayed posts, busy.
Now that I have time, I just downloaded and are about to install the latest BIOS for my MB then try the tut. you showed. Will report back.

Edit: I have just installed the latest bios with system stability updates, maybe that will help as well.

---

### Post by Axxon95 on 2012-06-03
Some success!
After downloading the LATEST Asus UEFI bios for my MB, it booted into UEFI mode with no problem.

There still is a bug with the EFI VGA vs NVIDIA. I had to set it up to run only on the iGPU, I just hope it doesn't mess me up in the future(like it did last time).

I'll first try a normal install, if that doesn't go right I'll try the tut. you showed.

Edit: I'm guessing once I test the 2 installs(if the first one fails) and if I succeed post back and mark as solved.

I'll still report the bug of EFI Intel vs NVIDIA(which causes in a lock-up). Sorta don't know where to, but I'll look around.



I have Ubuntu 12.04 (almost)perfectly installed in UEFI mode! Now to attempt to iron out these Intel iGPU bugs...

---

