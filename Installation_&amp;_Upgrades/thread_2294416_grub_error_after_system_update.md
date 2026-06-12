---
title: "grub error after system update"
date: 2015-09-11
forum: Installation &amp; Upgrades
---

### Post by sara-feizbakhsh on 2015-09-11
Hi,

Ubuntu crashed while installing some software updates. Now I get a series of "syntax error", "cannot find command", "incorrect command"

I tried to run Ubuntu from USB, but it does not boot (or even install Ubuntu) from USB. Only blank screen

Thanks

---

### Post by oldfred on 2015-09-11
You need to get live installer working from USB, you may have to download it again if it got corrupted.
You may just need to cold boot to get USB to boot. Some systems need full shutdown, if laptop remove battery and hold power switch to drain left over power. Then reboot and go into UEFI/BIOS. You may have to turn on settings to allow boot from USB.

If just a blank screen it may be the video. Do you have AMD or nVidia. Then you need nomodeset or other boot parameters.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
      
 [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)
     

After a crash you usually have to run fsck.
       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

And if in the middle of an update you need to boot to command line if possible using recovery mode, or if it will not boot at all, then chroot into system and run repairs. If you have good backups then you can reinstall.

Have you checked drive to make sure it does not have issues?
In Disks, icon in upper right is Smart Data which can tell if drive is still good.

---

### Post by sara-feizbakhsh on 2015-09-15
Thanks for the response! It was worse than this. None of commands in the threads worked for me. It finally got fixed by turning the secure boot off and on again. (!)

As for the grub error, root partition had gone out of space, so the new kernel version had crashed. got easily fixed with some re-partitioning.

---

