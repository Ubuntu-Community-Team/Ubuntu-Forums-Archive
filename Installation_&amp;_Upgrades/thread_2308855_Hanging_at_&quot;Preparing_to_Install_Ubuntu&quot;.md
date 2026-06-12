---
title: "Hanging at &quot;Preparing to Install Ubuntu&quot; screen"
date: 2016-01-06
forum: Installation &amp; Upgrades
---

### Post by nickTaylor1181 on 2016-01-06
Hi all.


I'm attempting to install ubuntu 15.04 from a USB alongside windows 8 on a new lenovo laptop.

I managed to get it installed once (created space using diskmgmt.msc) in windows... but wound up with serious bluetooth issues... tried to upgrade to 15.10 and wound up with a system that could not get to the desktop at all.

So I've attempted to reinstall ubuntu.

I used diskmgmt.msc to format the partition where ubuntu was last time (I've tried both exFAT and NFTS).... it says "Healthy (Primary petition)"

When I try to run the install from the USB though, it gets as far as the  "Preparing to Install Ubuntu" screen, then hangs.

I've spent about 4 hours scouring google for possible fixes, and nothing is working.


Any ideas?

---

### Post by kc1di on 2016-01-06
What video card is in use?

---

### Post by nickTaylor1181 on 2016-01-06
Under Adaptor Information it says

Intel(R) HD Graphics Family
Internal
Intel(R) HD Graphics 4000
Intel Video BIOS

Does that tell you which video card is in use?

---

### Post by westie457 on 2016-01-06
> [COLOR=#000000]I used diskmgmt.msc to format the partition where ubuntu was last time (I've tried both exFAT and NFTS).... it says "Healthy (Primary petition)"[/COLOR][COLOR=#000000]

After shrinking a partition to make space for any Linux OS the new partition/free space must be left unformatted.

Then use the 'something else' option in the Installer to set the partitions for use with Linux.
[/COLOR]
Windows tools cannot create 'ext' format partitions and Linux/Ubuntu will not install to any FAT or NTFS partition.

---

### Post by nickTaylor1181 on 2016-01-06
So what do I actually need to do to get the partition in the format that's needed?

I've tried deleting it, then (right-clicking) and creating a "new simple volume" witout formatting it

I've tried shrinking it, then leaving it as "Unallocated".

When I try to install ubuntu, it still hangs at the "preparing" screen, with both of the above.

(edit: It never gets to the "something else" option. It hangs before then)

---

### Post by kc1di on 2016-01-06
Try this when the live DVD/usb just begins to boot press the tab key.  
That will bring you to a window and at the bottom you'll find a number of Fkey options
press F6 and select nomodeset from the dropdown menu, press esc. and hit enter.
see if it will install now.

---

### Post by westie457 on 2016-01-06
All you should need to do is shrink a partition and NOT create a 'new simple volume'. Leave the free space as 'unallocated'

Reboot Windows so it can run a 'chkdsk' to check the main -Windows- partition is correct. You might need to do this twice. When Windows is happy and running okay then reboot the Ubuntu USB into 'Try' mode.

Start 'Gparted' to confirm that you have 'unallocated' space on the hard drive.
Now if you want you can create the necessary partitions for Ubuntu or you can now close Gparted and clicl on 'Install Ubuntu'

At the 'How to install' screen select 'Something Else' and in the new window highlight the 'Free space' and click 'New' at the lower left.

In the next window make one partition about 2Gib in size, In the 'Use as' box select 'Swap', click OK and agree to the prompts and wait while the partition is created. Does not take long.
Highlight the free space again and click New. This partition can use all of the space, 'Create EXT4 partition', tick the box to format, in the 'Use as' box select "/", click as above then Continue/Install Now'.  If you missed out the step to create the root "/" partition you get a warning.

Let us know how it goes.

---

### Post by mörgæs on 2016-01-06
Better to install 15.10 than trying to upgrade, especially for an Intel HD.

---

### Post by westie457 on 2016-01-06
@ kc1di
I have a Lenovo with the same graphics card and 'nomodeset' does not do anything. I think the issue is in the partitioning and trying to install to non EXT partitions.

---

### Post by nickTaylor1181 on 2016-01-06
Does it matter if I'm using that UEFI system?

because if try to boot from power-up, it goes to the grub menu.

To boot using the USB, I need to get into windows first, then (if you click restart with shift down) it gives options, one of which is "Use a device", then there's "EFI USB Device"...

... which appears to be what you need to do to boot from the USB stick.

From there it loads the usual install menu with options for "try", "install" etc.

I've tried hitting tab all the way through that process... it doesn't load any windows with fkey options.

---

### Post by westie457 on 2016-01-06
> **mörgæs said:**
> Better to install 15.10 than trying to upgrade, especially for an Intel HD.

^^ +1

15.04 has about three weeks of active life before support ends.

---

### Post by nickTaylor1181 on 2016-01-06
Yus... that's the advice I got a while back after I'd successfully installed 15.04... but bluetooth wouldn't work.

Then I attempted to upgrade to 15.10 - that didn't help. Then I tried something else... and after that I couldn't get into the desktop at all. Some sort of show-stopping display error.

The reason I'm using 15.04, is that it was the last system that actually worked... albeit without bluetooth, which is the main thing that I need this PC for. 

This whole experience has severely shaken my confidence. I have been using Ubuntu for about 10 years (I've even got my elderly parents using ubuntu)... but I've totally hit a brick wall with this one. I really don't know what to do from here. Get a whole new hard-drive?

---

### Post by mörgæs on 2016-01-06
Do you have a thread dealing with the bluetooth problem in 15.10?

---

### Post by yancek on 2016-01-06
If you are using GPT partitioning, then you must install windows in UEFI.  If you have windows installed using UEFI then you must install Ubuntu using UEFI or one or both systems will fail to boot.  More info on that at the Ubuntu documentation site below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Did you do an md5 checksum on the downloaded iso before putting it on the flash drive?  What software did you use to put it on the flash drive?  Have you tried booting the flash drive on another computer to see if it boots, eliminating that as the source of the problem.

As suggested above, leave the formatting for a Linux partition to Linux software.  You can use GParted which is on the Ubuntu installation medium.  All you will see of a Linux partition from windows is "Healthy drive".  If you install any Linux system on a windows formatted partition, it won't work.  The opposite is also obviously true.  So having unallocated space is the best way to go.

I would suggest you download and run the boot repair software from the site below and burn it to a CD.  Boot the computer with it and select the option to "Create BootInfo Summary" and do not try to make any repairs.  This will provide detailed information and if you post a link to it here, someone should be able to advise you on what to try.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by nickTaylor1181 on 2016-01-06
Okay... minor bizarritude.

I gave up at about midnight... left it where it was hanging... on the "preparing to install" page...

... and when I came back about 9 hours later, there was this splash-screen with a load of text saying "do you want to write your changes to disk", to which I replied "ok then", and the install went ahead as it should, and after a reboot and a self-inflicted disk-check, it's all there, AND bluetooth now works. 

So it seems that the "hanging" situation was just the system grinding through a hell of a lot of bits/bytes... I don't know how long the whole thing took. Based on how long it was sitting around in that state before though, I'd say hours.


So with appropriate touching of wood... that all appears to be as it should be. 


Thank you for your help everyone. Although the solution kindof came out of left-field, it means a hell of a lot to have people to talk to. I'm extremely grateful.

---

### Post by peter_l2 on 2016-05-29
I was experiencing the same problem with Ubuntu GNOME 16.04 being installed beside a Windows 10 installation (guid partition table) and UEFI (secure boot enabled) and these steps succeeded:
- Remove any partitions that are not necessary (IE: Ones created from previous installs)
- UEFI boot the installation media
- Proceed _without_ downloading updates and _without_ installing proprietary decoders

---

