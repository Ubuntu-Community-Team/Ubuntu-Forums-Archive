---
title: "Cannot boot Ubuntu 12.10"
date: 2013-02-04
forum: Installation &amp; Upgrades
---

### Post by Dr Cod on 2013-02-04
Hi,
I have a new Lenovo Z580 laptop which came with Windows 8 preinstalled. I have been trying to dual boot with Ubuntu 12.10 with only limited success. The laptop is UEFI (not entirely sure what that means but from looking at other posts it seems important). This is the story so far:

1. I edited the BIOS options to turn OFF SecureBoot and change boot mode to Legacy (with UEFI as priority)
2. I used a live CD of GParted to make a ~450 GB partition on my hard drive
3. After this, Windows was still able to boot just fine (after some complaining and disk checking etc)
4. I was able to boot a LiveCD of the Ubuntu Secure Remix 12.10 64bit
5. I installed Ubuntu using the default options (although strangely it didn't ask me what size I wanted the Ubuntu partition to be, it just placed it in the new empty partition without warning).
6. Installation all seemed to go OK.
7. After looking at various forum posts, I ran boot-repair. This threw an error: [http://paste.ubuntu.com/1608706](http://paste.ubuntu.com/1608706)

After restarting the computer, no grub screen appears. It just boots straight into Windows 8 (after some complaining the first time round). If I access the Boot menu I can see that there is an 'ubuntu' entry. When I select this, it just boots into Windows 8.

I know very, very little about grub and booting etc. I am very much a Linux novice. Looking at the boot-repair output it seems like the problem is:

mkdir: cannot create directory `/boot/efi/EFI/ubuntu': Input/output errorBut I don't know what this means or how to solve it.

Is anyone able to offer any help?

Thanks

---

### Post by Dr Cod on 2013-02-04
Replying to myself to give more information. Here is the output from gparted in case it helps:



I seem to have a lot of partitions. Most of these came pre-installed (thanks Lenovo!) and I'm not sure what they all are. However, you can see the Linux partition (sda9) and the Windows one (sda5).

---

### Post by oldfred on 2013-02-04
Partition table looks fine. Once booting in UEFI mode you will not need bios_grub partition as that is only for BIOS boot of Ubuntu.

You installed in BIOS mode not UEFI mode. How you boot install flash drive either UEFI mode or BIOS/legacy/CSM mode is how it installs.

Not sure why Boot-Repair cannot update or install grub-efi boot files into efi partition.  There is a bug report on lock efi partitions and a use in the tread just bfore yours (only right now) had a work around.

       grub-efi fails to install with Input/output error - locked efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829)
Some find chkdsk on efi partition helps, others backup, reformat and restore as current work arounds.
Another possible work around.
[http://ubuntuforums.org/showthread.php?t=2112273](http://ubuntuforums.org/showthread.php?t=2112273)

    
I would be sure to back up efi partition, as it is not large, and do a full backup of your Windows install.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

    
       Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

    
Another user did not seem to try repairs and just reinstalled, but then chose to write over the entire drive. He then wondered where is Windows went.

---

### Post by Dr Cod on 2013-02-04
Thanks for the reply. I'll have a go at the work around and post the results here.

Quick question:
When you say 'You installed in BIOS mode not UEFI mode. How you boot install flash drive either UEFI mode or BIOS/legacy/CSM mode is how it installs.'
Will this impact anything at all? Is it better to install in UEFI mode?

Thanks

---

### Post by Dr Cod on 2013-02-04
I had a go at the workaround in this link:

[http://ubuntuforums.org/showthread.php?t=2112273](http://ubuntuforums.org/showthread.php?t=2112273)

But was not able to implement it. The problem was at this stage:

- then open a File Navigator, and go to the Drive of the partition : you can see the EFI folder, and navigate down to the file : /EFI/ubuntu/grubx64.efi

I have no /EFI/ubuntu folder, only /EFI/Boot and /EFI/Microsoft folders.

I don't know what this suggests. That installing Ubuntu in BIOS mode (accidentally) is not going to work?

---

### Post by henrx on 2013-02-04
I have a brand new samsung and it seems to be samsungs UFEI.  workareound still waiting.

---

### Post by oldfred on 2013-02-04
Boot-Repair can convert a BIOS install to UEFI. All it has to do is un-install grub-pc and install grub-efi which then adds the grub efi files into the efi partition. But we have seen some with "locked" efi partitions and do not know why. 

Other work arounds for not being able to write into efi partition were a full backup of efi partition, delete it and then recreate it. Some were able to use chkdsk and it then worked. See bug report link for more detail on work arounds posted above.
Some BIOS computers had a setting that locked MBR to prevent unauthorized updates. (Not sure how that worked either.). And sometimes that setting is not obvious, it may be a virus protection checkbox.

Boot-Repair has a work around for those systems that only boot Windows. It copies grub's efi file to the Windows partition and renames the Windows file. Then from grub menu you chain back to the renamed Windows efi file.
       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)


this install worked:
       
 Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)

    
Older install, no secure boot.
       How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)

---

### Post by Dr Cod on 2013-02-06
Quick update:

I uninstalled the Ubuntu installation that I couldn't boot into and removed the partitions from the harddrive (in an attempt to get back to a 'fresh' start). Then I used a LiveUSB, instead of the LiveCD (still using the Secure Remix). Before booting, I changed the boot order of the BIOS and put USB to the top. Previously I had been starting the computer by going to the BIOS options (using a little button next to the main power button - it's a Lenovo Z580) and manually selecting to boot from the CD. Now, with the USB stick in place, just pressing the power button I can boot straight into the LiveUSB. So far, so good.

I did a fresh install of Ubuntu (I used the default options which further partitioned my harddrive - I don't care at this point), and immediately ran Boot-Repair. Drum roll... No errors! For the first time Boot-Repair did not complain about the 'input-output' problem.

With baited breath I rebooted the machine and, again for the first time, was presented with a Grub menu. It did not immediately boot into Windows. Progress had been made.

Grub gave me 7 (!) options. Two for Ubunutu (ubunutu, and advanced ubuntu options), 4 for windows (windows, windows recovery, windows uefi recovery, and windows boot recovery) and a system recovery.

Of these, only one of ubuntu ones work (advanced) and only one windows worked (one of the recovery ones). The main windows and ubuntu option fail.

But... I can at least boot my machine into Ubunutu and Windows. It's not perfect. My Grub is clearly a mess and my hard drive is partitioned to death.

The partitioning I can sort out with GParted. I will do some research on the Grub menu before posting.

So what have I learned? If you want to dual boot a Lenovo Z580 with Windows 8 preinstalled, this is what I did (after many attempts).


[LIST]
[*]Make a LiveUSB stick of the Secure Remix (a LiveCD did not work. I don't know why)
[*]With the power off, press the little One Key Recovery button next to the main power button.
[*]Change the BIOS options so that Secure Boot is OFF and UEFI mode is set to Legacy (with UEFI as priority). Also change boot priority so that USB comes first. Save and exit.
[*]Upon exiting BIOS, the machine will probably automatically restart and try to get into Windows. If it does, power down again.
[*]Stick the LiveUSB stick in and power on. If you're lucky, you boot into 'try Ubunutu'.
[*]Install Ubuntu
[*]Before restarting, run boot-repair (I did it a couple of times to make sure
[/LIST]
Like I said, my Grub menu is quite broken, but I can at least boot into both. This is progress. I don't know why the LiveUSB stick worked when the LiveCD didn't. It may because I changed the boot order to get the USB working, instead of always manually choosing to boot the CD. I really don't know.


Even though the computer is not perfectly set up, I think this deserves a SOLVED flag.


(All written from my new Ubunutu installation - whoo!)

---

### Post by oldfred on 2013-02-06
Glad you got Ubuntu working. :)

But Boot-Repair normally creates correct grub chain load boot entries from the efi bootable files in the efi partition. Grub2's os-prober still has a bug and only creates the old BIOS chain load entries that do not work. You can turn off the os-prober until grub fixes its bug to eliminate those entries. And manually edit 25_custom to fix or delete entries you do not want.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

    
You may just want to backup entire efi partition. I think Boot-Repair does some backups and renaming of efi files but you may want to preserve those.

# Edit 25_custom entries:
       sudo cp -a /etc/grub.d/25_custom /etc/grub.d/25_custom_backup
gksudo gedit /etc/grub.d/25_custom
 # Then do:
sudo update-grub

    
# I add this line to grub configuration or turn off the execute bit on 30_os-prober
       gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executable bit
sudo chmod a-x /etc/grub.d/30_os-prober
 # Then do:
sudo update-grub

---

### Post by ankur1993 on 2013-02-06
first to delete the paritition of window drive.Simple to install ubuntu.
:P

---

### Post by oldfred on 2013-02-06
@ankur1993
With some UEFI systems that may totally brick system as you can only get to UEFI menu thru Windows menu.

---

