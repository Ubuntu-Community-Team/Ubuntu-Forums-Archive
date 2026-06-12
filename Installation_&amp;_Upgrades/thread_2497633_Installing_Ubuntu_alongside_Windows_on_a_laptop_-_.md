---
title: "Installing Ubuntu alongside Windows on a laptop - original recovery configuration"
date: 2024-05-13
forum: Installation &amp; Upgrades
---

### Post by baskak on 2024-05-13
Hi,
I'd like to install Ubuntu alongside Windows on a HP Pavilion x360. I wonder if my original boot configuration, allowing for recovery and reverting to like-new state (OOBE) will be irrecoverably overwritten/destroyed?
Thanks in advance.

---

### Post by Rubi1200 on 2024-05-13
What version of Windows is currently installed? What version of Ubuntu do you want to install? Do you have backups of all important data?

---

### Post by yancek on 2024-05-13
I would not expect that to happen without a user choosing to do so. There are generally several install options and the only one I would expect to overwrite everything is the 'Erase Disk and install Ubuntu' option.   At least if I am understanding what you mean by the 'like-new state'.  If by that you mean returning to the state it came from the factory using the windows recovery partition, you should be able to access through the BIOS.  This recovery option will obviously overwrite everything on the disk to return it to the factory state so you need backups.  Backups should/may be able to be done when starting the recovery process but much safer to do beforehand. 

If that is not what you meant then clarify what you mean by 'original boot configuration'.

---

### Post by baskak on 2024-05-13
Thanks for the replies! By "original boot configuration" I mean the one that allows for access to recovery partition via a key on startup or via restart in a Windows recovery mode in order to revert to "factory state" (OOBE - Out-Of-Box Experience).
Don't worry about the backups, I'm on it.
Currently it's Windows 10 Home 22H2, I want to install current Ubuntu (24.04).

---

### Post by ubfan1 on 2024-05-13
The changes to "revert" are to delete the Ubuntu partition and expand the windows partition, delete the EFI's partition EFI/ubuntu directory, and reset the EFI/Boot/bootx64.efi to the windows boot manager (EFI/Microsoft/bootmgfw.efi, but it may have been renamed to bak... something in the Boot dir). Not sure how your nvram gets reset, might be automatic without the actual grub files deleted from EFI/ubuntu. I've never done this, but have been messing around with EFI for years.

---

### Post by baskak on 2024-05-13
I see, so it will be overwritten and needs some fiddling after all.

---

### Post by oldfred on 2024-05-13
I had to return my Dell for a new motherboard. I think they did not update UEFI with old Microsoft product key.
My Kubuntu install worked without issue, but Windows would not boot. Tried every repair and normal Windows install, but nothing worked. Backup would not install either.

Downloaded from Dell an image restore. Not all vendors allow download like that. But Dell image restored Windows to just like new. And that restored partition table totally erasing my Kubuntu install. But Dell laptop Kubuntu install was essentially a copy of my install on desktop, so nothing really lost.
Debating reinstalling to Dell as I have a larger external SSD with a full install (and is copy of desktop). It works just as good for everything I use system for, so will probably just rely on external drive and let Windows have internal drive.

---

### Post by yancek on 2024-05-13
If you run the command:  sudo fdisk -l it will LIST the partitions on the drive and if you have windows installed, there should be several partitions.   One (the largest) would be the filesystem partition and you should also have Microsoft reserved and a Windows recovery environment partition.  I don't use windows so am not really sure what the small 'reserved' partition does but I'm quite sure you will need the recovery partition (usually around 500MB) if you want to go back to factory settings so don't delete or format that partition.  The other members posting here probably have a lot more experience and knowledge about windows.

---

### Post by baskak on 2024-05-16
Here it is, hope it helps solving the riddle somehow:[ATTACH=CONFIG]293779[/ATTACH]

---

### Post by baskak on 2024-05-27
I'd be happy to get a clear solution...

---

### Post by yancek on 2024-05-27
The image in your last post shows you have a very large partition on  which windows is installed (/dev/sda3) so I would suggest you use  windows Disk Management tool to shrink it to create unallocated space on  which to install Ubuntu.  After doing this, reboot windows to test and  run chkdsk before beginning the Ubuntu install to the newly created free  space.  It also shows an EFI partition so when you boot the Ubuntu installer, make sure you select to boot in EFI mode in the BIOS options.  I would suggest you read through some of the links posted above so you have a basic understanding of the install procedure.

---

### Post by MAFoElffen on 2024-05-27
Here's another log to throw in the fire... Microsoft has a big bug right now with one of their updates, where what they thought was enough for the size of the originally installed Win PE recovery partition was too small. And a specific update breaks the machine, filling that partition to 100%.

They do not have a hot-fix for that. Nor have they figured out a way to handle that by an amended update process. 

The correction has to be done "manually", by shrinking their root partition, deleting the old Recovery partition, adding a new one that is over the minimum new size required, then reapplying the update to re-populate that partition... I have to note that their own GUI tools can't handle that, and has to be done via booted from Win PE so nothing is mounted, and is all done in commandline.

When I do that for customers, I also grow the original size of the EFI partition, so it is over what was originally created. So I give 750MB to 1G as EFI. 500MB is their new minimum for the recovery partition after that... Where I give it 7500MB to 1G. Doing the math, and starting by shrinking the Win Root, by that much from the left before starting that. 

Just thought I would throw that out

---

### Post by baskak on 2024-07-05
Hello, kind reminder, I'd be happy to learn how to solve this.

---

### Post by baskak on 2024-07-05
[-------------]

---

### Post by baskak on 2024-07-05
> **yancek said:**
> The image in your last post shows you have a very large partition on  which windows is installed (/dev/sda3) so I would suggest you use  windows Disk Management tool to shrink it to create unallocated space on  which to install Ubuntu.  After doing this, reboot windows to test and  run chkdsk before beginning the Ubuntu install to the newly created free  space.  It also shows an EFI partition so when you boot the Ubuntu installer, make sure you select to boot in EFI mode in the BIOS options.  I would suggest you read through some of the links posted above so you have a basic understanding of the install procedure.

Hi thanks, but I don't know how to relate to this in the context of my original question.

---

### Post by tea for one on 2024-07-05
> **baskak said:**
> I'd like to install Ubuntu alongside Windows on a HP Pavilion x360. I wonder if my original boot configuration, allowing for recovery and reverting to like-new state (OOBE) will be irrecoverably overwritten/destroyed?

yancek's reply in post 11 is correct.
If you install correctly, the original recovery partitions will not be affected.

Anyway, another perspective.

If you dual boot Windows and Ubuntu on the same disk and, then, have cause to use the built-in Windows recovery, you will lose your Ubuntu OS.
Also, depending on the reason for using Windows recovery, you may or may not repair your Windows OS.
You will need to be completely confident that the Windows recovery will always return your PC to the original state (i.e. out of the box experience).

Having gleaned that Windows is your priority OS, have you considered installing Ubuntu to a separate bootable external disk with its own ESP?

---

### Post by yancek on 2024-07-05
If you want to install Ubuntu and still keep the currently installed windows OS, you need to first shrink the largest windows partition which in your case is shown as /dev/sda3.  Do this with windows Disk Management tool and reboot windows and run chkdsk from windows to verify there were no problems.  Do this before trying to install Ubuntu to the unallocated space you created  from windows earlier.  I would also suggest that you go through some tutorials on installing in dual boot with windows UEFI.  Your original question would have been better answered at some windows forum.

---

### Post by baskak on 2024-09-01
Hello,
Let me revive this (unanswered) question.
I guess there's a bit of a misunderstanding. I *do* know how to install Ubuntu alongside Windows.
What I don't know is how to do it without destroying original (factory, OOBE) Windows recovery configuration/ability.
PS. Regarding Windows forum, I don't know if they bother with installing other OSes alongside. But may indeed be worth a try.
Regards,

---

### Post by tea for one on 2024-09-01
> **baskak said:**
> What I don't know is how to do it without destroying original (factory, OOBE) Windows recovery configuration/ability.
Posts 11 and 17 from yancek answered your question.

You start by using Windows tools to shrink the sda3 partition and rebooting to run chkdsk.
Then, if you have doubts, check that the Windows recovery partition is still present before proceeding.

---

### Post by yancek on 2024-09-01
>  What I don't know is how to do it without destroying original (factory, OOBE) Windows recovery configuration/ability.

I don't know how much more clear we can be.  If you don't specifically tell the Ubuntu installer to delete/format or overwrite it then it won't.  If you install Ubuntu with the "Erase Disk and install Ubuntu" option, it will overwrite all the windows partitions.  Why would you think your Ubuntu installer would overwrite that partition?

---

