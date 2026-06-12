---
title: "Unable to install GRUB onto / partition."
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by ch_123 on 2008-06-23
Hi all,

I got myself a new laptop (a Thinkpad T61), which in order to preserve its special startup recovery tools requires me to install GRUB onto the Linux partition as opposed to onto the MBR as is usual. Yesterday, I was able to do this successfully with OpenSuse 11. However, when I wanted to put Ubuntu on, I was unable to do this.

At the last stage of the setup, I went into "Advanced Options", and set GRUB to be installed onto "/dev/sda4" (my / partition) and then installed. Towards the end of the installation process (around 97%) I got a "Fatal error" telling me that GRUB was unable to install to this device. I tried replicating this in the terminal by typing "sudo grub-install /dev/sda4" and was told:

"Could not find device for /boot: Not found or not a block device."

Any help folks?

Thanks :)

EDIT:
In case it is relevant, here's my partition scheme -
/dev/sda1 - 120GB, NTFS, Windows XP
/dev/sda4 - 25GB, JFS, Ubuntu
/dev/sda3 - 256MB, Swap Partition
/dev/sda2 - 6GB, FAT32, Recovery Partition

---

### Post by logos34 on 2008-06-23
I've never gotten a fatal error installing to jfs, so I doubt that's at issue.

What does 

sudo fdisk -l

show?

---

### Post by ch_123 on 2008-06-23
Hi,

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       15386   123588013+   7  HPFS/NTFS
/dev/sda2           18582       19457     7030800   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3           18550       18581      257040   82  Linux swap / Solaris
/dev/sda4   *       15387       18549    25406797+  83  Linux

Partition table entries are not in disk order
```

What really bugs me was that OpenSuse was able to do the same thing (or so it seems) yesterday, but Ubuntu cant...

---

### Post by logos34 on 2008-06-23
According to fdisk, root is ext3

run a filesystem check:
[B]
sudo fsck /dev/sda4[/B]

then try reinstalling grub from the live cd.  Click on it to mount--it should do so at '/media/disk'.

**sudo ****grub-install --root-directory=/media/disk /dev/sda4**

---

### Post by ch_123 on 2008-06-24
Hello again;

Clicking on the CD Drive icon in Places gives me an error telling me that there is no media in the CD Drive (even though there is). I tried substituting / for /media/disk as the live CD seemed to be mounted as the root filesystem. However, this gave me an error saying that /dev/sda4 was not a block device. The fsck worked fine without errors.

EDIT: I tried manually mounting both CD and the /dev/sda4 partition. So, sub in "/mnt/cd" for "/media/disk" and "/mnt/disk" for "/dev/sda4". Using your command, I tried it again, but it told me that "/mnt/cd" was read only, so I figured the order was wrong, so I swapped the order for disk and CD. This however gave me an error saying that the "Format of install_device not recognized"... God, I had less hassle installing Slackware on my PC ;P

---

### Post by logos34 on 2008-06-24
> **ch_123 said:**
> Clicking on the CD Drive icon in Places 

no, you click on the root volume/partition

> The fsck worked fine without errors.

at least we can rule that out

Either click to mount root, or do this in terminal:

sudo mkdir /media/sda4

sudo mount -t ext3 /dev/sda4 /media/sda4

sudo grub-install --root-directory=/media/sda4 /dev/sda4

---

### Post by ch_123 on 2008-06-24
Well, I tried that command, and it installed GRUB :) Problem was that it only installed half of it. So when I booted, I would get the GRUB console. To get around this, I installed Ubuntu into a VM on my desktop and copied over the GRUB folder. This was grand, but then Ubuntu just froze up mid loading with some random errors. The great irony of this was that I use Arch on my PC, and I decided to use Ubuntu because I thought it would be less hassle with a laptop and all the complications a laptop brings. However, Im installing Arch now and its working quite alright. Thank you for your assistance though mate xD

---

### Post by logos34 on 2008-06-24
> **ch_123 said:**
> Well, I tried that command, and it installed GRUB :) Problem was that it only installed half of it. So when I booted, I would get the GRUB console. To get around this, I installed Ubuntu into a VM on my desktop and copied over the GRUB folder. This was grand, but then Ubuntu just froze up mid loading with some random errors.

There must be some problem with your menu.lst, then, or something else in grub folder.

anyway, have fun with arch (played around with it a little.  considering you have to install from scratch, its not all that difficult to get up and running)

---

### Post by SeePU on 2008-06-24
> **ch_123 said:**
> Hi all,

I got myself a new laptop (a Thinkpad T61), which in order to preserve its special startup recovery tools requires me to install GRUB onto the Linux partition as opposed to onto the MBR as is usual. Yesterday, I was able to do this successfully with OpenSuse 11. However, when I wanted to put Ubuntu on, I was unable to do this.

At the last stage of the setup, I went into "Advanced Options", and set GRUB to be installed onto "/dev/sda4" (my / partition) and then installed. Towards the end of the installation process (around 97%) I got a "Fatal error" telling me that GRUB was unable to install to this device. I tried replicating this in the terminal by typing "sudo grub-install /dev/sda4" and was told:

"Could not find device for /boot: Not found or not a block device."

Any help folks?

Thanks :)

EDIT:
In case it is relevant, here's my partition scheme -
/dev/sda1 - 120GB, NTFS, Windows XP
/dev/sda4 - 25GB, JFS, Ubuntu
/dev/sda3 - 256MB, Swap Partition
/dev/sda2 - 6GB, FAT32, Recovery Partition

Maybe there is still something wrong in the syntax?  That is, something in your /boot/grub info?  I would check your /boot/grub/menu.lst and try to confirm whether the info in there is correct.   

I just had to fiddle with mine and with a dual boot even.

---

### Post by kitchenguy on 2008-06-25
Just an idea, but if Open Suse did it ok, why not install Ubuntu first, then open Suse and use the Grub from Open Suse?  
 
When setting up my triple boot - Ubuntu, Mandriva, XP, I found that Ubuntu would recognise Windows and incorporate it into Grub, but the menu.lst entry did not work - however it ignores Mandriva.  While Mandriva worked fine with windows, but ignored Ubuntu. So, I loaded XP, then loaded Ubuntu, copied the menu.lst entries for Ubuntu from it's files, then loaded Mandriva and added the Ubuntu entries to the Mandriva menu.lst - (I also liked the Mandriva graphical boot loader a bit more but don't tell anyone!).  I'm now going to add 64-Bit Ubuntu, so I'll have a quad boot and if I could get PC Los to deal with my SATA2 disks it'd be there too.
 
It's probably because I am still a bit new, but I found it really annoying how Hardy, Gutsy and Mandriva completely ignored eachother...maybe Linux snobbery between them?

---

### Post by logos34 on 2008-06-25
> **kitchenguy said:**
> ...I found that Ubuntu would recognise Windows and incorporate it into Grub, but the menu.lst entry did not work - however it ignores Mandriva. 

just curious, which ubuntu did you install at this stage--gutsy or hardy?

---

### Post by kitchenguy on 2008-07-24
Sorry for the late reply, I've been a little drunk lately...it was Hardy and the 32 bit version that I installed.  
 
Interestingly, I found that the 64 Bit version of all the distros I use now all saw each other (maybe just a quirk of my rig).  I now use Hardy 64 and openSUSE 64 (same as Mandriva, it has a much nicer boot loader)

---

