---
title: "broke boot manager trying to install, now always boots straight to windows 10"
date: 2020-03-26
forum: Installation &amp; Upgrades
---

### Post by natebot on 2020-03-26
Hello, first time poster.

I'm trying to dual boot Ubuntu 19.10 alongside Windows 10 on my Lenovo C940 Yoga. I made a mistake following [this tutorial]("https://itsfoss.com/install-ubuntu-dual-boot-mode-windows/") and seem to have broken my laptop's boot management system. 

I created the partition a la the tutorial, I shrank the C volume and then booted into the ubuntu installer, and then used the installer to create a "root" partition in the unallocated space. My mistake was that I forgot to create a "home" and "swap" partitions as well. I successfully completed the install process but when I tried to log in it just re-booted and took me to Windows, and asked me for my bit-locker key. I had to disable bitlocker because it was asking me for the recovery key on every reboot. 

I figured out my error. Turned off bitlocker. Reabsorbed the partition into the main volume using windows disk manager, and then recreated a similar partition. Now when I bring up the boot manager on restart (pressing f12) it just has "ubuntu" at the top as if ubunutu were installed, and it never shows any install media I have in the USB as an option. If I select ubuntu, it just takes me to windows.  I have disabled secure boot and disabled fast start up.

I created a recovery disk image using the Windows 7 legacy tool prior to this process. My next step is to try to reset the hard drive to the state it was before this process? I was hoping for some advice before I commit yet another two hours of my life to trying this.

---

### Post by ajgreeny on 2020-03-26
I suspect that you have installed ubuntum in legacy mode but if your computer came with Windows 10 pre-installed it would have been UEFI, therefore Ubuntu would need to be installed using UEFI as well.

See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 **[COLOR="#FF0000"]Do not run the default repair just yet[/COLOR]** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by natebot on 2020-03-28
Hey thanks for the reply!

I created a Boot-Repair disk with Rufus and booted from it, selected the "start session" option (it was the only option) and then my computer just sat for ~15 minutes with a blank screen doing nothing. I lost patience and rebooted and then posted this reply. I have no ideas on how to proceed, other than trying to recreate the Boot-Repair disk with different settings.

---

### Post by oldfred on 2020-03-28
Better to use your Ubuntu live installer and add Boot-Repair with ppa.

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by natebot on 2020-03-28
[https://paste.ubuntu.com/p/CRkktwsP6F/](https://paste.ubuntu.com/p/CRkktwsP6F/)

There it is, thanks for offering to help me make sense of it.

---

### Post by oldfred on 2020-03-28
You are showing UEFI boot of both Windows & Ubuntu as you have UEFI boot entries.
But Linux partition not shown.
You show two NVMe drives.

You also are showing RAID, I do not know RAID, so do not want to lead you astray.
Do you really have Windows RAID or is just drives are not set for AHCI? If really RAID, you should not change to AHCI, but if RAID or Intel RST then you do want to change drives to AHCI. And RAID does not seem to be entire drive, which RAID normally is and two drives with same sizes in the RAID. 

Linux desktop & then report used to not even show a drive with Intel RST or RAID. Only server installer would see RAID as it has those extra drivers.

Do not know Windows, but what does Windows see as the two drives?

---

### Post by natebot on 2020-03-29
[IMG]C:\Users\natei\OneDrive\Desktop[/IMG]

---

### Post by oldfred on 2020-03-29
You have to post screenshots or reduces size photos here.
Use Forum's Advanced mode and paperclip icon in upper panel of editor.

If you use the Forum's advanced editor, you can use the paperclip icon to attach screenshots. Post #4 1024x768 if photo
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

---

### Post by natebot on 2020-03-29
Windows just sees a 100gb unallocated partition.

---

### Post by natebot on 2020-03-29
So I assume "ubuntu" is still an option in the boot-menu because there is still a UEFI boot entry for it.

So should I run boot-repair? Or should I just go ahead and try to install again, making sure to partition the drive correctly this time (e.g. making swap and home partitions)?

---

### Post by natebot on 2020-03-29
So I ran boot-repair and then reinstalled ubunutu on a correctly formatted partition (w/ home, root, and swap). Everything went smoothly during the install, but upon restarting and hitting f12 to get into my computer's boot menu, in *still* takes to directly to Windows 10 no matter what option I pick.

I ran boot-repair again and generated another report. Don't really know what to make of it, it seems my laptop's (Lenovo C940) boot management system is extremely broken. It it time to just do a factory reset?

Here's the output from my most-recent (post re-install) boot-repair report.

[https://paste.ubuntu.com/p/jn4w5vcpWc/](https://paste.ubuntu.com/p/jn4w5vcpWc/)

---

### Post by CelticWarrior on 2020-03-29
1. A separated /home is optional; it has some advantages but not really better than a separated partition for your data (personal files). Again, it must be stressed, it's OPTIONAL, and has nothing to do with your problem.

2. A swap partition WAS needed, it no longer is. The default installation now uses only one (root) partition. Also this has nothing to do with your problem.

---

### Post by natebot on 2020-03-29
Do you mind telling me how you know it has nothing to do with my problem?

Do you know what does have to do with my problem?

I've noticed looking through the paste-bin report it seems that when it tries to test-mount the volumes every single one except for the one labeled "Microsoft Reserved" doesn't mount properly, could that be part of the problem?

---

### Post by oldfred on 2020-03-29
Report still has lots of mention of RAID & Optane on second NVMe drive. And then various gpt errors.
Ubuntu may try to boot but will try to mount all those paritions with errors. It may not work or may take a very long time to timeout if those errors otherwise do not prevent boot.
Windows will not show the Linux partitions.

What version of Ubuntu. Your system is new enough you need newest Ubuntu.
Perhaps even 20.04, which will not be released until April. It works, but you may have issues that are still being fixed. It has newer kernel & newer drivers.
You could try disabling your second NVMe drive temporarily in UEFI settings, to see if then you can boot Ubuntu.

Yours may be too new for this to apply. But UEFI update is always a good idea. And SSD firmware update is often required.
UEFI update required for USB-C port issues 2017 thru 2019 models
ThinkPad models including the ThinkPad X1 Carbon (5th Gen to 7th Gen), X1 Yoga (2nd Gen to 4th Gen), and P-series 
[https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/](https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/)

---

### Post by natebot on 2020-03-29
I've reabsorbed the ubuntu partition back into the main windows partition but my laptop's boot manager is STILL showing ubuntu as the the top choice in the boot menu. 

I don't see the point in trying to repartition and reinstall because I've already tried that. Same problem. I'm sure if I tried to reinstall ubuntu it would just keep taking me to Windows 10.

Fast start up and secure boot are disabled.

I'm completely at my wits end. It seems like my laptop's boot manager is permenantly broken.

---

### Post by oldfred on 2020-03-29
But issue is your second NVMe drive and you do not seem to be making any fixes to it.

---

### Post by natebot on 2020-03-31
I'm actually not trying to install Ubuntu anymore, I've completely removed it and I've reabsorbed the ubuntu partition back into the main partition.

But when I boot to UEFI settings, ubuntu is still shown as the top boot priority. I feel like this is a signal that the boot configuration is still "broken" and there's no point in trying to reinstall ubuntu until I fix it. Right now I'm trying to get my UEFI menu to look like it did before I attempted any of this. I *thought* completely reinstalling Windows and de-partitioning the drive would do this but obviously I was mistaking. 

I looked in my UEFI settings but couldn't find anything that disabled my second NVMe drive. Both NVMe drives are listed in the boot priority order, I could try moving them down the list but I don't see what that would accomplish.

---

### Post by oldfred on 2020-03-31
The settings on disabling a drive is not in boot options but hardware/drive settings. Different tab in UEFI.
Should be somewhat similar to third screenshot in my old post. That showed ports. My newer system shows drives in similar fashion.
[https://ubuntuforums.org/showthread.php?t=2258575&page=2](https://ubuntuforums.org/showthread.php?t=2258575&page=2)

Your ESP - efi system partition will normally have both /Microsoft & /ubuntu folders. Unless you houseclean any of those you do not want, you still have part of Ubuntu/grub boot. Do not delete ESP partition as essential for Windows boot.

And UEFI retains UEFI boot entries. You can see those:
sudo efibootmgr -v

To delete UEFI boot entries. You may want to houseclean old entries also:
# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

---

### Post by natebot on 2020-03-31
I'm looking at [this]("https://www.tenforums.com/installation-upgrade/115716-uefi-remove-unwanted-boot-entries-bios-solved-easily.html"), told me to run

bcdedit /enum firmware

in windows command prompt as admin to list all UEFI boot entries and also gives instructions on how to delete them. Seems very similar to what your proposing, just using command prompt instead of Ubuntu/bash.

My UEFI boot manager, the one I get on restart, doesn't look as "fancy" as the one in the screen shot you posted. I also don't recall seeing any options to disable drives in it but I could double check. 

Are those screens you posted of the UEFI manager one would get by restarting and botting from the recovery partition or is that something different?

---

### Post by oldfred on 2020-03-31
The screenshots are from my Asus Z97 system's UEFI. Asus allows screenshots from within UEFI and you can save to a FAT32 partition. That is f2 with the Z97 system.
Also motherboard manual shows screens but has more explanation of all the settings. If you do not have manual you should be able to download from vendor's support page for your specific system. Google gave me this.
[https://pcsupport.lenovo.com/us/en/products/laptops-and-netbooks/yoga-series/yoga-c940-14iil/documentation/doc_userguide](https://pcsupport.lenovo.com/us/en/products/laptops-and-netbooks/yoga-series/yoga-c940-14iil/documentation/doc_userguide)

I have seen some discussion where Windows BCD is sync'd with UEFI, but do not know Windows.

---

### Post by natebot on 2020-04-04
I did what you said, turned off the secure boot in the UEFI. I think maybe I didn't do that the first time, getting it confused with turning off bit-locker perhaps?\

[https://paste.ubuntu.com/p/JnQ75pgrkj/](https://paste.ubuntu.com/p/JnQ75pgrkj/)

After getting everything set up again I ran boot repair and produced the previous report. I have not checked on the status of the boot-order yet.

Looking at the boot-repair report, it looks like there are still errors coming out of the nvme drives. I looked around in my UEFI menu and I couldn't find any obvious way to disable them.

---

### Post by natebot on 2020-04-04
Update, I booted into ubuntu and out of curiosity opened gparted. The first thing it did was tell me that there was something wrong with one of my nvme drives, something about it not using all of its allocated space? I told it to fix this problem, and I ended up with a normal looking hard-drive but with two tiny unallocated sections, one is 1mb and the other is 2mb. 

I ran the boot repair report after doing this and I've noticed that those drives are no longer throwing errors the way they once were.

G-parted is showing red exclamation warnings for the Microsoft Reserved Partition and the Basic Data Partition. Googling around tells me that is *not* normal (?)

---

### Post by oldfred on 2020-04-04
Microsoft reserved is a required unformatted partition. 
Because it is unformatted gparted shows it as an error.

Standard data partitions should not show errors. If you right click on the error what does it say.

Partitions have to be aligned. Important for new 4K drives & SSD. Old drives you can ignore error.
First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). 
[https://developer.ibm.com/technologies/linux/](https://developer.ibm.com/technologies/linux/)
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

Other errors in report were from Windows fast start up being on. 
And this:
> The backup GPT table is not on the end of the device. This problem will be corrected by write.

Not sure what tool you used to partition that drive, or if you tried to image copy a smaller drive to it.
But as it says you need to do a write from various partitioning tools. Best to use gdisk with gpt partitioned drives.

repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

gpt partition table in middle of drive
sudo gdisk /dev/nvme1n1
Command (? for help):
To move backup to end of drive
 launch gdisk, then type x, then type e, then type w to save your changes

---

