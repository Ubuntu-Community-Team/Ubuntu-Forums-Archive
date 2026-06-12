---
title: "Booting Ubunutu from Grub Rescue?"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by apolix on 2007-09-06
I have just installed Ubuntu 7.4 , I made the mistake of choosing "continue without a bootloader" because grub and lilo failed to install.. I have xp on another partition and it fails to load now. 
When i start my machine I get the grub rescue command prompt.

How can I boot to Ubuntu from this prompt? and can I install grub once I boot to Ubuntu ?

---

### Post by merlinus on 2007-09-06
Try this. Boot from live cd.  Open a terminal and enter:

```

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

```

Substitute results from find for (hdx,y) and setup (hdx).

If this does not work, post results of:

```

sudo fdisk -l

```

-merlin

---

### Post by logos34 on 2007-09-06
Edit2: You might want to reinstall, apolix, if you cannot easily fix the problem with the commands merlinus posted above.  It's the fastest and simplest solution.  (In which case disregard the rest of my convoluted reply.)

If 'find /boot/grub/stage1' fails, then the grub files were likely never put in the appropriate folders during installation. Unless I'm completely mistaken, the 'continue without a bootloader' message means the debian installer never ran 'grub-install', in which case there isn't a stage1 file to (re)install to the mbr.  The files have to be copied from the /usr/lib/grub/i386-pc directory where they are stored, and a menu.lst generated from the kernel and initrd images in /boot.

Go to Places>Home Folder>double click on the root partition in the left side pane.  It will mount at '/media/disk'.  

Then in a terminal type:

**cd /media/disk/boot**

**sudo mkdir grub**

**cd**

**sudo grub-install /dev/hda** (or sda) (-->this copies files in /usr/lib/grub/i386-pc to /boot/grub and writes stage1 to the mbr)

**sudo update-grub** (-->this creates a menu.lst)

Post your new menu.lst.  You may need to edit the options and run update-grub again.

Edit: You may have to chroot into the environment for grub-install to work:

> sudo mount --bind /dev /media/disk/dev
sudo chroot /media/disk
sudo grub-install /dev/hda

or

> sudo chroot /media/disk /bin/bash
sudo grub-install /dev/hda


An easier way is to run grub-install from the Alternate CD (which is the way I've run it in the past):

'Using the Ubuntu Alternate/Install CD' 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28cd%29%7C%28grub-install%29%7C%28live%29](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28cd%29%7C%28grub-install%29%7C%28live%29)

---

### Post by merlinus on 2007-09-06
Brilliant stuff, logos34!

-merlin

---

### Post by logos34 on 2007-09-07
I have to admit I've only run grub-install in the recovery mode shell on the Alternate CD (which puts you into the root environment automatically)...It's so easy to do it that way or from within the mounted root partition...But from the live cd I think you have to actually chroot, isn't that right merlinus?  Someone please correct me if this is wrong.

---

### Post by apolix on 2007-09-07
Ok, I tried the first method with no results.. So I just decided to format the drive and freshly install ubuntu by itsself.

I set it up with 40gb as the primary partition ext3 and a 1gb swap file
when I get to install grub boot loader it says "[!!] Install the GRUB boot loader on a hard disk
Installation step failed"

same thing for Lilo and Grub 2

This is really frustrating, does anyone know what the issue is here?

---

### Post by logos34 on 2007-09-07
did you do all the things listed here:
[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)
?  (i.e. verify md5sum, 1-4x burn, cd integrity check)

could be data corruption somewhere.  doesn;t take much to screw up install

---

### Post by Herman on 2007-09-07
Hello  apolix,
You should get yourself a free [Super Grub Disk]("http://geocities.com/supergrubdisk/"), they are only a small download, and they sure save a lot of anxiety and frustration. You'll at least be able to use it to boot either Windows or Ubuntu and any other OSes you may have too. You should be able to install GRUB to MBR with it too, and also do quite a few other boot loader related operations.  Here's another page about Super Grub Disk, [Super GRUB Disk Page]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")        When normal booters won't work, you need **Super Grub** Disk! 

Super Grub Disk can even boot Ubuntu when there is no Grub in it at all, you need to do a direct kernel boot, ('English Super Grub Disk Menu'-->'Gnu/Linux'-->'Boot Gnu/Linux Directly'...)

logos34 already gave you the right commands for installing Grub in your Ubuntu install, those will work fine once you have Ubuntu booted, except you can disregard the chrooting part, you won't need that with Ubuntu booted.

If Super Grub Disk can't install GRUB to MBR for you, try checking your CMOS (or BIOS), and make sure you don't have any features turned on in there that might prevent anything from writing to your MBR.  Here's a link about that, [BIOS Page]("http://www.users.bigpond.net.au/hermanzone/p1.htm"), and in particular, this part, [    Turn off MBR antivirus or write protect]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Turn_off_MBR_antivirus_or_write_protect"). I do realize that your BIOS will likely be different from mine of course, but that page should remind you of a few things to look for in there. Sometimes that solves problems with stubborn MBRs.

If you still have any trouble then please boot the Ubuntu LiveCD again and post the output of 'sudo fdisk -lu' here please, that's often a big help with solving problems like this, ```
sudo fdisk -lu
```Above all, never give up, you are probably only one or two steps away from  success!

Regards, Herman :)

---

