---
title: "Cannot boot Ubuntu 10.0 desktop or server"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by erik777 on 2011-04-08
I currently dual boot Vista and Fedora on one drive, and have tried 5 times to install Ubuntu 10.0 64-bit on another drive.  

I used desktop CD and put /boot on 1 GB /dev/sdc1 ext4 and root on 100 GB /dev/sdc2 ext4.  It installs fine, but when you go to boot, and you pick it from the GRUB menu, it times out and says it cannot find /dev/ with the ID.  Because GRUB runs you can conclude that it never has a problem finding /dev/sdc1.  

When I boot into Fedora, I can mount and access both partitions without a problem.  I've run e2fsck -ccv on /dev/sdc2 over and over again with no issues whatsoever, unmounted, of course.  

I then created a new logical group and used /dev/sdc3, inside of which I put a 100 GB logical volume.  I installed root onto it using the Server 10.10 64-bit CD.  No problems with installation.  GRUB came up with all the new options, but again, when I selected to boot into either the new server install or the old desktop install, it timed out and dropped into a useless command line that was non-responsive to keystrokes.  The now the /dev name is the /dev/mapper/lg_raptor/lv_uroot logical volume that it says does not exist.  

Again, I boot into Fedora, able to access all these partitions, including the new logical volume, without any problems.  I can mount them, view all their files, and open them. Fedora reports that the file systems are clean.  
 
Why can't Ubuntu's GRUB see the Ubuntu partitions when I select them from the menu despite being able to boot into Fedora and Vista when I select them from the same menu, and Fedora able to mount and access these partitions without a problem and a clean bill of health from e2fsck?

---

### Post by mikewhatever on 2011-04-08
Can you post the output of the [bootinfo script]("http://bootinfoscript.sourceforge.net/"). That should gather all the needed info to troubleshoot the problem.

---

### Post by erik777 on 2011-04-08
"Your file of 22.4 KB bytes exceeds the forum's limit of 19.5 KB for this filetype."

So, removed some menuitems of older kernel versions in the attached bootinfo script output file since I only pick the latest version when booting.

---

### Post by mikewhatever on 2011-04-08
You can just post the ouput as is into the text box, with the [noparse]```

```[/noparse] tags wrapped around:

[noparse]```
[/noparse]

...text here

[noparse]
```[/noparse]

...or you could have compressed the text file.


Anyway, I'm no expert, but four HDDs with bootloaders on the MBR of each... are you booting from /dev/sdc at all when trying to load Ubuntu?

---

### Post by erik777 on 2011-04-08
Yes, I have the BIOS boot from sdc and then I let Ubuntu take over the MBR on sdc.  That results in GRUB 2, which is what we're looking at.  I have no problem booting into Fedora or Vista from the sdc MBR that uses the GRUB 2 created from these installs (the last of which was the server install using the LVM at sdc4.)  

sda also has an MBR with GRUB 1 created by Fedora.  But, I don't let Ubuntu use it, and only have the BIOS boot sdc when I'm working with Ubuntu.  

I don't ever use the MBR on sdb, which just has an NTFS partition that I use for data.  sdd is a drive I'm not using.  You can pretend that sdd doesn't exist for all intents and purposes.

---

### Post by erik777 on 2011-04-08
I just noticed, based on the Boot Info Summary that the serer install did replace the MBR on /dev/sda because it says Grub 2 is there when it was supposed to be Grub .97"

```

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for (,msdos1)/grub.

```

Someone needs to fix the Server installer so you can pick the MBR.  The dialog said it will install on the first drive.  In contrast, the Desktop's GUI installer gives you a dropdown.  

I'm using sdc's MBR, which was created by the Desktop install.  Both MBRs use /dev/sdc1 as /boot.

---

### Post by Dutch70 on 2011-04-08
Maybe you're booting from the wrong Grub2. See if this helps any.
[[COLOR="Red"]https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD[/COLOR]]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by erik777 on 2011-04-08
@Dutch70

I'm definitely booting from /dev/sdc1/grub/grub.cfg.  When I mount this using Fedora and edit it to create new menuitems to try to resolve this, the changes show up upon the next boot.  I know I'm using the /dev/sdc MBR because that is what I have selected in the BIOS.  Prior to the Server install overwriting my /dev/sda MBR against my wishes last night, I switched between sda and sdc using the BIOS many times, toggling between Fedora's GRUB 0.97 on sda and Ubuntu's GRUB 2 on sdc.  

(I know that you would never want to touch the menu.cfg in Grub 2 IF you were able to run the OS where a grub-install would overwrite it.  Until I can boot Ubuntu, this doesn't matter.)

---

### Post by erik777 on 2011-04-08
I looked back at when I was able to install Ubuntu successfully, and asked myself what was different.  I realized that for unsuccessful installs, I didn't check the box to reformat the /boot partition. I didn't think it was necessary since it had a working ext4 filesystem, and it would copy all the new files it needed, overwriting old files.  In fact, this is one partition that  faithfully worked and always had the new files from the new install.  

But, when I tried installing server on /dev/sdc2, letting it format the /dev/sdc1 partition, it worked.  While I doubt it needed to be formatted, per se.  This did let it install on a file system that had no left over files on it.  Then, when I installed Desktop on the LVM on /dev/sdc4, again letting it reformat the /dev/sdc1 root partition, it worked again.  I'm now typing this into the Desktop install.  

I can't prove that letting it erase the root partition before installing is why it worked. I'm certainly going to pray that I don't have to re-install again.  But, if this is what permitted it to work, then the theory I have is that even though it overwrites all the files you need if you don't reformat, perhaps GRUB 2 does some logic based on some checking so that, if you don't reformat or erase the files from a previous install, it can cause it to find info from previous installs and use it, creating unpredictable circumstances.

---

### Post by MAFoElffen on 2011-04-09
This one may help: [http://ubuntuforums.org/showthread.php?t=1529658](http://ubuntuforums.org/showthread.php?t=1529658)
This was when I was having problems getting my main multi-boot up.  

One thing i noticed on the new installs and the partitioning menus... There is an obscure "box: there that now asks if you want to keep the data in the partition.  On my clean installs, I always partition "manually" for my ext4 and swap, format them (unchecking that check-box), then do the install.

How are your drives laid out (drive, partitions and OSes) with what OS'es?  

A suggestion/recommendation on server/desktop... Because I do allot of testing, I used to install separate desktop versions and desktop versions.  Now for my own use on machine that are going to be server with some "users," I install server, then a desktop package (ubuntu-desktop, kubuntu-desktop or xubuntu-desktop) after the main install and re-add a custom Grub2 menu entry to get the tty text console back as a boot entry.

On boxes that people are going to use as a desktop, with some server services, I now install desktop and the services packages. 

The diffrences there between the two basically are in how the kernel is configured and how is schedules tasks....

To help with mbr's of diffrent disks... my test boxes all have disks that are all individually bootable, but tied together and organised with the primary disk's grub2 menu. On overwritten mbr's. the testdisk utility in the above thread came in handy in repairing those.

---

### Post by erik777 on 2011-04-09
Thanks, MAFoElffen!  I thought I was pushing it with tri-boot, LOL:

> 
For tranlation perposes to this script-
 sda1 is Vista
 sda2 is OpenSolaris
 sdb1 is WIN7
 sdb5 is Ubuntu
 sdc1 is WinServer 2003
 sdc2 is just Data with a NTFS file system.
Good point about the kernel scheduler.  I forgot about that.  This is  purely used for desktop, so I'll probably be happier with the desktop  kernel.  In fact, the primary reason I needed Ubunutu is Boxee.  :)  I  found that boxee doesn't run well in a VM.  It works.  It just isn't  pleasant to navigate because it can be laggy.  

I've reduced Windows to just games, Netflix, and a few Windows only apps I rarely use.  

I wasn't sure how to toss a desktop on the server.  I was thinking along  the lines of xinit, but that's just probably my old school thinking. Next time I'll reference your post. 

Just curious, why do you have both Vista and Win 7?  Does Vista have a niche, like a legacy app that 7 won't run?

---

### Post by Dutch70 on 2011-04-09
> I thought I was pushing it with tri-boot, LOL:

:lolflag:

Have a look at my disk, this is just one of them. The other has vista & Maverick.
So, I currently have 10 OS's.
I've traded the ntfs partition in for ext4 as of yesterday.

---

