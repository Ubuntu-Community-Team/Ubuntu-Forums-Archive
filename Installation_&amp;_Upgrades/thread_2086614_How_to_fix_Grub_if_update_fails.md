---
title: "How to fix Grub if update fails"
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by Dragonbite on 2012-11-21
I have a family desktop computer which is running Ubuntu 10.04.0 and I am looking to carve out a partition (~10GB +/-) to install 12.04 onto. Version 10.04 will sit in its partition only as a fallback in case 12.04 doesn't work.  In the future then I'll use 12.04 and install an update version over the 10.04 partition.

Anyway, since this is my family computer I don't want there to be a long down-time.  I thought if I get answers/advice here then if the poop hits the fan, I'll be able to recover without starting to research from scratch.

[LIST=1]
[*]So if in installing 12.04, something goes wrong and the computer won't boot up, how would I fix the Grub and MBR to use the old 10.04 again?
[*]Once 12.04 is set up (users to their /home directory, programs installed, etc.) I want to set Grub to not show (preferred) or only show for 0 seconds before immediately booting the 12.04 version.
[*]Ubuntu 10.04 is 32bit and I am putting 64bit Ubuntu 12.04. Will this difference cause any problems?
[/LIST]

Like I said, I am hoping to gather what to do if things go wrong to quickly revert me back to where I was previously.  I already know to backup all of my /home files (which is on a separate partition) and plan on not installing all of the programs I installed previously when I was "trying" them, or thought I would do something with it and never did.

Normally I don't worry about this with my laptop because if it breaks I am the only one messed up but this is the family one and they (at least my son) may string me up if I break it :lolflag:

Thanks.  

I'm also interested if you have tried anything similar, and your experiences.  I usually don't have problems with Ubuntu so I am hopeful that this will go just as smoothly as the previous times.

Thanks

---

### Post by oldfred on 2012-11-21
I agree with the install to another partition when you have or can make some space on the hard drive.
I did the same when upgrading from 32 bit to 64bit but that was back from 9.04 to 9.10. :) And I just added a new 640GB drive so I had lots of room to experiment.

I used to burn multiple repair CDs to fix or setup system. I would have Boot-Repair, Supergrub, Ubuntu (of course), knoppix, gparted and/or partedmagic. But after updating every 6 months and burning stacks of updated CDs a couple of times I changed to directly booting all the ISO from one Flash drive with grub2's loopmount. I still do one CD in case flash fails, but now have a couple of flash drives one with older versions. And also now can boot ISO and install from one hard drive to another which is really fast.

[http://partedmagic.com/](http://partedmagic.com/)
 [http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

    [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
    
And if you just want to use command line.
       How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

            Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

The change from 10.04 to 12.04 is large. Often proprietary video drivers are an issue as now kernel has something to do with video and Unity is huge change, unless you install fall-back or gnome-panel.

My backup procedure is to do a new clean install, so I try to backup what I need of my data, but not system.
       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by gordintoronto on 2012-11-21
1. Make a boot-repair CD.
2. I don't like the idea of completely hiding Grub. Make it a two-second option. (Google can tell you how to do it.)
3. Going to 64-bit should not cause problems. I suggest using Unetbootin to make a bootable flash drive (with persistence, if possible) so you can try a more recent Ubuntu without modifying your hard drive.
4. Backup, backup, backup! Backup onto an external drive, onto DVDs and onto Ubuntu One and/or Dropbox.

---

### Post by zvacet on 2012-11-22
Instead of Unetbootin you can use [Multisystem.]("http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/") Very good tool. :)

---

### Post by grahammechanical on 2012-11-22
Yes, it is possible for an install to fail for some reason. So, installing into another partition is sensible. I do it all the time. I have at present 2 x 12.04, 1 x 12.10 and 1 x 13.04.

Remember this: The last Ubuntu to be installed will put its version of Grub into the MBR (Master Boot Record) of the hard disk. So, the 12.04 Ubuntu will be in control of the boot menu.

You should still get a Grub menu. If not pressing Esc repeatedly as the boot process moves from POST (Power On Startup Tests) to running the Grub Configuration file should bring up a Grub menu.

The Grub menu should give you 10.04 as an option. Pressing E will put the Grub menu in Edit mode. It will also stop the count down timer. Doing that will give you time to study the menu. Pressing Esc will back out of edit mode.

If you want to put 10.04 back into control of the Grub menu then load 10.04, open a terminal and run these two commands.

```
sudo update-grub
```

That will tell the 10.04 Grub to re-examine the hard drive for operating systems and kernels and re-write its configuration file.

```
sudo grub-install /dev/sda
```

That will install the 10.04 grub into the MBR of the first hard disk, if sda is the hard disk that you want Grub to be installed into.

Now reboot.

Regards.

---

### Post by Dragonbite on 2012-12-30
Well all of this is basically moot at this time.  I tried adding a partition to install 12.04 and found out all of my primary partition slots are all 4 occupied!

I know that I can or need to move some partitions to an extended partition (like the /home and related file partitions) but I don't think I am going to bother since I don't have a large enough hard drive I can move all of the files over so I could re-partition part of the drive.

So I took an external hard drive (only 60 GB) and cloned /dev/hda2 (the / directory) onto it.  I am planning on installing 12.04 OVER the current 10.04 installation and if that fails for whatever reason I can re-clone from the external drive back into /dev/hda2 where it came from.

Strange thing is even when the drive is mounted, I can navigate the 2nd partition on the external drive (I was going to copy the /home directory there) but not the 1rst, nor can I boot to the USB drive directly (the boot flag is set, but it seems to hang while trying to boot up).

Ultimately, though, I will probably overwrite 10.04 with 12.04 and if anything goes wrong... I'll install 12.04 in the partition 10.04 once resided.  So ultimately nothing is lost, but the cloned image is my "insurance". :)

---

### Post by oldfred on 2012-12-31
If it is a clone it will have same UUID, so if you have both drives plugged in, you may get into one drive one time and the other drive another time. Or have lots of issues. Just do not leave external plugged in. 

It would be possible to convert cloned partition to be bootable, but you would have to change UUID, edit fstab with new UUIDs & reinstall grub2. But if just for backup, then it is not worth reconfiguring.

---

### Post by ronparent on 2012-12-31
+1 oldfred. I have cloned and ended up with a duplicate uuid. You end up with a system with split personality and you may never know on which install any changes or updates are made with both in play. 

As an alternative I now prefer to simply copy the contents of the clone source to the target source. You do have to to this from a live cd and you have to edit the /etc/fstab file on the target to change the uuid's referenced to those of the target partition(s). You can then update-grub on the source to boot into the target, unplug the source and then install-grub to on the target to make it bootable. It sounds complicate but is actually fast and simple. Best of luck to all for the New Year.

---

### Post by Dragonbite on 2013-01-14
Yesterday I did my installation of 12.04 over the 10.04 I had previously cloned (realized I had all 4 primary partition slots occupied and can not set up an alternating / partition for versions).

Everything went pretty well, running a clean install.  Was surprised when I re-connected the users all of their settings pulled through without incident (Thunderbird, Firefox, etc.). So now I only have a few programs to still install.

Only snag I ran across was my /home/SHARE partition. I first set it up over 2 years ago so I didn't think about it before upgrading.

I had it set that members of the "parents" group could rwx permissiona while everybody else can read-only and when somebody from the "parents" group save a file there it is saved under the "parents" group.  Thus I can access what my wife saves there and vice-verse while the kids can read-only.

I got it working with the help of this thread [[COLOR="Blue"]_default folder permissions_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1633728")

Unfortunately I am not remembering everything I did, as "umask=002" in /etc/fstab fails to mount the partition, and files saved are under our default group, not "parents".

---

