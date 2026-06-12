---
title: "Ubuntu 14.04 on Raid 0 (fakeraid)"
date: 2014-11-05
forum: Installation &amp; Upgrades
---

### Post by aquablue25 on 2014-11-05
Sup guys,

what is the proper way to install Ubuntu 14.04 64-bit on a fakeraid (Raid 0) array consisting of two 320 GB HDDs?

Last time I tried, I let the installer do "its thing" and the only thing I got were "???" during the installation. Next time I chose LVM to eliminate the "???" during the installation, but a Grub error message appeared when the installation was finishing and getting ready to reboot. I think the installer didn't know where to put the Grub loader on.

When booting off a Live-USB, I can tell that "dmraid" is installed at default.

I read reports that booting via a Live medium + using Gparted to manually create a swap, home and / partition and then installing Ubuntu on / should do the trick, but I have yet to try this method. I already have Windows 8.1 running and I would like to make keep losses at a minimum this time around. :-)

Thanks!

---

### Post by oldfred on 2014-11-05
When they eliminated the alternative installer for RAID & LVM, they said later they would include that in the Desktop. I see LVM is not in Desktop, but not RAID. It did not used to even recognize your partitions and caused all sorts of issues, but grub still does not install correctly, so not fully implemented yet.

 Elimination of Alternative installer for 12.10 and no RAID support directly for Desktop.
[http://ubuntuforums.org/showthread.php?t=2049021](http://ubuntuforums.org/showthread.php?t=2049021)

Note that most LVM installs are full drive install, erasing everything else on drive.

You have to install grub to root of RAID.

 Does not recommend "fakeRAID"
[http://aryklein.wordpress.com/2013/10/28/a-quick-guide-to-linux-software-raid/](http://aryklein.wordpress.com/2013/10/28/a-quick-guide-to-linux-software-raid/)
[https://raid.wiki.kernel.org/index.php/DDF_Fake_RAID](https://raid.wiki.kernel.org/index.php/DDF_Fake_RAID)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
"fakeRaid" with nVidia, note p1 is partition, without p1 is root of RAID volume
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0

 How to install Ubuntu 14.04 in software RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126)

Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by aquablue25 on 2014-11-13
Hello there, 

thanks for posting all of that useful information. It helped understand the subject a lot.

Even though there is a lot of info on the subject, it does seem a bit complicated.

I have a question though: I noticed that the disk management utility in Ubuntu has the option to create a software-raid via a GUI by combining two or more drivers together.

[IMG]http://s14.directupload.net/images/141113/obxfcz3z.png[/IMG]

After selecting the drives I want to use for the array, it says the following in the lower left corner: "create RAID" and when I click on it, I get the option to create a Raid 0-10 array. 

My question now is: Can I do this on the fly, even though I have Ubuntu installed on one of the two drives or do I have to merge the two drivers together by booting via a live-medium and installing Ubuntu afterwards?

Thanks,
Aqua

---

### Post by oldfred on 2014-11-13
I still do not know much about RAID as there are so many types.
Linux RAID is often suggested as it can easily be moved from one system to another where hardware RAID requires the specific brand/model hardware to work. 
FakeRAID or BIOS RAID I think is compatible with Windows but Linux RAID is not. 

[https://raid.wiki.kernel.org/index.php/Linux_Raid](https://raid.wiki.kernel.org/index.php/Linux_Raid)
[http://en.wikipedia.org/wiki/Mdadm](http://en.wikipedia.org/wiki/Mdadm)

---

### Post by nerdtron on 2014-11-13
> My question now is: Can I do this on the fly, even though I have Ubuntu  installed on one of the two drives 
Nope. 

Theoretically, you can create two partition for each drive and then create a RAID for those two partitions. But why bother? On RAID 0, when 1 drives fails, your data is toasted.

> or do I have to merge the two drivers  together by booting via a live-medium and installing Ubuntu afterwards?
I haven't configured raid on GUI yet so no idea on that. But what I think is that you have to have an OS installed when you are installing software raid. Since you are going to configure the drives. 


BTW, thanks for oldfred for the link on software RAID in Ubuntu. It will help on my research.

---

### Post by Greg_C on 2015-09-19
I just started playing with Ubuntu and the experience has taught me much. I discovered something pertinent to this discussion through my endeavours and I would like to share them in the hopes that I can save some people some headaches. I will admit that I'm very green when it comes to Linux, and from what I've seen the information I've learned will not help everyone. That being said; FOR A CLEAN INSTALL (Might have some bugs especially after updating. See bottom for details.)

Hardware. Make certain it's good if at all possible. If you have an install of Ubuntu or another distro, use it to verify that your known working installation is not throwing any suspicious errors. Example: Mine was throwing WRITE DMA EXT errors while the two IDE drives I just raided were plugged into the motherboard's IDE port. Turns out - I either have a damaged port or a damaged IDE controller chip/chipset, or further motherboard damage. That led me to install a FastTrak100 to test them. Discovered the drives were good (no WRITE DMA EXT on install), and proceeded to fail at getting Ubuntu to install and boot on the raided devices.

If your fakeRAID is like mine, you've got a BIOS option that pops up "(Ctrl + F to enter Cleverly named RAID BIOS option editor)", so step 1 is to set up your raid in that, as was stated previously in this thread. I chose RAID-0, though this would probably work for others with careful adjustment. Choose your drives, perform whatever other naming and/or configurations you want, save, and reboot.

Step two, the Live CD. Let it boot, but do NOT install, or you're in for a world of headache.

Go through the menu and/or search for GParted. Under no circumstances should you allow the Ubuntu installer to format or resize your RAID device, nor should you (with GParted or the installer) attempt to do ANYTHING to whatever drives are in your array (mine are /dev/sda and /dev/sdb). Do not format them, do not mount them. Just ignore them. If you manage to access them you will break your array (maybe not if mirror, but my raid 0 certainly). Look for "/dev/mapper/incredibly_longandobnoxiousoutputifyouhavetotypeit", or whatever yours is called. It may be /dev/md0 or similar. This will list any and all partitions on your RAID. If partitioned, choose to create a new partition table. Otherwise you need to create a new partition table. The goal is to have swap separate as a primary partition, and all other partitions should be logical inside an extended partition that is the size of the rest of your array, or the rest of the space you wish to have for this installation. My structure was 200MiB unused before the first partition (primary, swap), second was (extended), third was (logical, ext2, / ), fourth was (logical, ext4, /home), fifth was (logical, ext4, /linux-shared). My setup is only for reference, choose whatever you like, but it seems that everything needs to be logical partitions in an extended partition, except for swap. If you leave swap logical, it doesn't mount. If everything else is primary, it doesn't mount everything.

After making all the changes, make sure you've applied them. Let GParted work its magic, and now you're ready to run the installer. When it asks how you want to install, choose "do something else" and it should bring up the installer's disk editor. ***DO NOT FORMAT OR RESIZE YOUR DISKS HERE!!!! If you must format or resize your disks at this stage, quit the installer and use GParted to adjust your RAID. It also might be a good idea to open the installer to this point and quit it once or twice to make sure it gets your updated array partitioning scheme. *Note: Sometimes the installer will demand to format the swap partition. I do not believe this harms the installation any. If it does, you may need to format the array and "destroy" it, then try again.

DO NOT FORMAT AT THIS STAGE: Select the partition that matches the size and/or formatting of /, select it, and choose "Change". Keep the current filesystem if it matches or make sure to match the selection with the existing format displayed, choose to mount the partition as /, untick format if it's ticked, and apply. Do the same for all your other partitions except for swap and/or any areas to be left "untouched." Select the root of your array for the boot loader (the same as the empty device in GParted, or the shortest of your really long named array name. Once this is done, choose "Install now."

If everything's gone as planned, the installer will hum along and install everything. I don't know whether or not it helps or hurts to try to install with updates on or off. I did it with them on.

Once the installer is complete, DO NOT REBOOT. Select "Continue Trying" and reopen or go back to GParted. If it was opened, make sure to refresh the devices.
Select your device, select your / partition, right click, go to Manage Flags and select "boot." Apply the change if GParted doesn't do it automatically, and exit GParted.

Reboot.

You should now be able to boot Ubuntu from your device. Keep in mind that you must never fiddle with the drives in your array in RAID-0. So if your open Disks or GParted or anything else, steer clear of those devices.

I sincerely hope this helps. I've spent a week working on getting my RAID to boot and I'm willing to destroy it and test this install method to make sure it's viable and not just a lucky fluke.

**Update: I have not attempted to destroy and recreate my raid yet.  However, I did verify that Ubuntu 14.04 is booting from my array from an  install off of a desktop live cd (actually, I used UNetbootin and  installed the live cd onto my Windows10 Tech Preview hard disk. I have  no reason to believe that this would not work from a generic live cd or  usb stick containing the same media. However, I do get a conflict after  updating. 

Oxymoron kernel: [   15.300459] systemd-udevd[708]:  conflicting device node '/dev/mapper/pdc_iaihdhfc2' found, link to  '/dev/dm-2' will not be created). It is repeated for all partitions  involving the raid array.

This seems to be a conflict, or rather, some kind of "race" between udevd and dmraid. And I haven't been able to find a successful fix yet. I've tried changing fstab to use /dev/dm-X, and to use the UUID's. Nothing works. They fight. I will post more if I can learn anything more.

---

### Post by crazyshoez on 2015-09-20
> **Greg_C said:**
> 
Go through the menu and/or search for GParted. Under no circumstances should you allow the Ubuntu installer to format or resize your RAID device, nor should you (with GParted or the installer) attempt to do ANYTHING to whatever drives are in your array (mine are /dev/sda and /dev/sdb). Do not format them, do not mount them. Just ignore them. If you manage to access them you will break your array (maybe not if mirror, but my raid 0 certainly). Look for "/dev/mapper/incredibly_longandobnoxiousoutputifyouhavetotypeit", or whatever yours is called. It may be /dev/md0 or similar. This will list any and all partitions on your RAID. If partitioned, choose to create a new partition table. Otherwise you need to create a new partition table. The goal is to have swap separate as a primary partition, and all other partitions should be logical inside an extended partition that is the size of the rest of your array, or the rest of the space you wish to have for this installation. My structure was 200MiB unused before the first partition (primary, swap), second was (extended), third was (logical, ext2, / ), fourth was (logical, ext4, /home), fifth was (logical, ext4, /linux-shared). My setup is only for reference, choose whatever you like, but it seems that everything needs to be logical partitions in an extended partition, except for swap. If you leave swap logical, it doesn't mount. If everything else is primary, it doesn't mount everything.

After making all the changes, make sure you've applied them. Let GParted work its magic, and now you're ready to run the installer. When it asks how you want to install, choose "do something else" and it should bring up the installer's disk editor. ***DO NOT FORMAT OR RESIZE YOUR DISKS HERE!!!! If you must format or resize your disks at this stage, quit the installer and use GParted to adjust your RAID. It also might be a good idea to open the installer to this point and quit it once or twice to make sure it gets your updated array partitioning scheme.


How much space did you allocate for each of your partitions and how big is your drive?

---

### Post by Greg_C on 2015-09-22
> **crazyshoez said:**
> How much space did you allocate for each of your partitions and how big is your drive?

Together the array combines to 320GB. In GParted it's 298.02GiB. I will attempt to upload a snapshot of GParted.

---

