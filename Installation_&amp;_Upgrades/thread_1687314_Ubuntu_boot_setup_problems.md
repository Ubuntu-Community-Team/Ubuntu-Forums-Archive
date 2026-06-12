---
title: "Ubuntu boot setup problems"
date: 2011-02-13
forum: Installation &amp; Upgrades
---

### Post by hillmelvin73@gmail.com on 2011-02-13
I did a Tar backup of my Ubuntu10.10 system to a tar file about 3 Gigs in all. I have a 500 Gig SATA internal Hardrive that I format/partition with ext4 488Gigs and about 12Gigs for swap. I extracted the Tarball to the 500Gig drive like the instructions said, But I can't get the system to boot. These are the problems I have with the setup. When I type find/boot/grub/stage1 I get (Error 27: unreconized command). Also when I type root(hd0) or (hd0,1) or (sda) or (sdb1) I get (Error 23 while parsing number) or  (Error 17 cannot mount selected partition). So find/boot/grub/stage1 and root (?) and setup (?) get me nothing at all. I did a DDresue to the other drive and that works great.Please help.

Melvin,

---

### Post by d.atanasov on 2011-02-13
Do you have a live CD of Ubuntu 10.10? If you have you can try to search through the folders where did you put you grub2 or even your partitions. How did you "untar" you backup ?

---

### Post by hillmelvin73@gmail.com on 2011-02-13
Yes I have the Live CD and I still get the same error message with it. I extracted the TAR file with this command in the root directory of the ext4 partition.

Code:
tar xvpfz ubuntu10_backup.tgz -C /

Then I re-created the directories that I didn't include in the tarball

mkdir proc
mkdir lost+found
mkdir mnt
mkdir sys

I have done this several times now. Excluding the directories and including the directories with a system that won't boot. I've been trying a little something different everytime with about the same results. I could continue to use ddrescue but it copies the whole disk 500Gigs and takes a while. Tar seems to work fine as far as copying files, it just the boot thing that I need to get straight.

---

### Post by oldfred on 2011-02-14
It sounds like the instructions you are following are for grub legacy and you have grub2. If everything else is ok, you should just have to reinstall grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

If you want to see if everything is there.
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by hillmelvin73@gmail.com on 2011-02-15
Well it seems like I at least got the machine to booting. I tried the first two methods and the one that actually booted was  ****METHOD 3 - CHROOT. But now I run into this before login. There is a red circle with this:

Could not update
ICEauthority file/var/lib/gdm/.ICEauthority

With a close button on the right side just below.

I click close and then I get this two.

Another red circle and this message:

There is a problem with the configuration server. 
(/usr/libgconf2-4/gconf-sanity-check-2 exited with status 256)

and then just this.

Melvin-desktop.

No password prompt and nothing but a shutdown/restart option. This has been quite a project so far trying different things. Now I'm beginning to wonder about my tar backups. I have like 3 different ones and I guess the others will give me the same thing when I try them.

---

### Post by oldfred on 2011-02-16
Another thread with similar issue:

[http://ubuntuforums.org/showthread.php?t=1021106](http://ubuntuforums.org/showthread.php?t=1021106)

This is from moving /home which may be similar?
Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

I think you just reinforced my plan of recovery. I just backup /home which only has my user settings and is about 1GB. I have all my data in other partitions that I separately backup. I would then just reinstall. One install from a USB, took 9 minutes to already set up partitions. Updates, linking to data files, & my updates of installed apps made a total of about 1 hours to a working mostly configured system.

---

### Post by hillmelvin73@gmail.com on 2011-03-02
Well after a long absent from the ubuntu system. I took one of my backups and ddrescues it to another drive and then I started back on working on the tar situation again. I found that if I go.

Code:
sudo tar pcvzf   thetarfile.tgz    --exclude=/thetarfile.tgz  from the root directory of the linux system with the p in the first position I didn't have the permission problems when I booted the system after installing grub 2. Everything worked fine. So I got this to create my system backup:

Code:
sudo tar pcvzf   thetarfile.tgz    --exclude=/thetarfile.tgz /

And then I have this to extract in the root directory of the first partition on the other drive.

Code:
tar pxvfz   thetarfile.tgz   -C /

After this I use this to install grub 2.

**METHOD 3 - CHROOT**

  This method of installation uses the *chroot* command to gain access to the broken system's files. Once the chroot command is issued, the LiveCD treats the broken system's / as its own. Commands run in a chroot environment will affect the broken systems filesystems and not those of the LiveCD.  
 
[LIST=1]
[*]Boot to the LiveCD Desktop (Ubuntu     9.10 or later). Please note that **the Live CD must be the     same as the system you are fixing - either 32-bit or 64-bit**     (if not then the chroot will fail).
[*]Open a terminal - *Applications,     Accessories, Terminal*.
[*]Determine your normal system partition     - (the switch is a lowercase "L")      
     sudo fdisk -l
[LIST]
[*]If you aren't sure, run          
         df -Th.         Look for the correct disk size and ext3 or ext4 format.
[/LIST]
     
[*]Mount your     normal system partition:
[LIST]
[*]Substitute the correct partition:         sda1, sdb5, etc.
[/LIST]
     sudo mount /dev/sdXX /mnt     # Example: sudo mount /dev/sda1 /mnt         
     
[*]*Only if you have a separate boot     partition*:
[LIST]
[*]sdYY is         the /boot partition designation (for example sdb3)
[*]sudo mount /dev/sdYY /mnt/boot
[/LIST]
     
[*]Mount the critical virtual     filesystems:      
          sudo mount --bind /dev  /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
[*]Chroot into your normal system device:         
     sudo chroot /mnt
[*]If there is no /boot/grub/grub.cfg or     it's not correct, create one using      
     update-grub
[*]Reinstall     GRUB 2:
[LIST]
[*]Substitute the correct device - sda,         sdb, etc. Do *not* specify a partition number.
[/LIST]
     grub-install /dev/sdX         
     
[*]Verify the     install (use the correct device, for example *sda*. Do *not*     specify a partition): sudo grub-install --recheck /dev/sdX
[*]Exit *chroot*:     **[SIZE=2]CTRL-D[/SIZE]** on keyboard
[*]Unmount virtual filesystems:      
          sudo umount /mnt/dev/pts
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt/sys
[LIST]
[*]If you mounted a separate /boot         partition:          
         sudo umount /mnt/boot
[/LIST]
     
[*]Unmount the LiveCD's /usr directory:      
     sudo umount /mnt/usr
[*]Unmount last device:      
     sudo umount /mnt
[*]Reboot.      
     sudo reboot
[/LIST]
 **Post-Restoration Commands**

  Once the user can boot to a working system, try to determine why the system failed to boot. The following commands may prove useful in locating and/or fixing the problem.  
 
[LIST]
[*]To refresh the available devices and     settings in */boot/grub/grub.cfg*
[LIST]
[*]sudo update-grub
[/LIST]
     To look for the     bootloader location.      
     
[LIST]
[*]grub-probe -t device /boot/grub
[/LIST]
     To install GRUB 2 to the sd*X*     partition's MBR (sda, sdb, etc.)      
     
[LIST]
[*]sudo grub-install /dev/sdX
[/LIST]
     To recheck the     installation. (sda, sdb, etc.)      
     
[LIST]
[*]sudo grub-install --recheck /dev/sdX
[/LIST]
 
[/LIST]
 This is so far the only method that has worked for me. Now I have several backups to learn from and to play with and try things. I'm very new to linux and just love it.

---

