---
title: "GRUB Can't Boot - Missing Device Files"
date: 2013-04-10
forum: Installation &amp; Upgrades
---

### Post by conte_matthew on 2013-04-10
I was installing a software library using apt-get and all of a sudden I   see it tampering with my /boot directory. I canceled the installation   but somehow it deleted all the sda device files from the /dev directory.   When I try to boot now, all of my OSs are listed but when I selected   Ubuntu, I get an error saying that it cannot find the device and I   should try to boot manually. I can't do that though because the device   files are gone.  I've followed the advice from these questions:

  [http://ubuntuforums.org/showthread.php?t=1769391](http://ubuntuforums.org/showthread.php?t=1769391)
  [Boot error > no such device: grub rescue]("http://askubuntu.com/questions/143667/boot-error-no-such-device-grub-rescue")

  But I think my situation is different. My partitions are intact; I   was able to mount my Ubuntu partition while running the Live CD and all   the data is there. How can I restore the device files?

-- Extra Info --
  Here's the output from BootInfo script:
  
============================= Boot Info Summary: ===============================   
=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at  sector 1 of      the same hard drive for core.img. core.img is at this  location and looks      for (,msdos6)/boot/grub on this drive.  

sda1: __________________________________________________  ________________________ 
     File system:       ntfs     Boot sector type:  Windows Vista/7:  NTFS     Boot sector info:  No errors found in the Boot Parameter Block.      Operating System:  Windows Vista     Boot files:        /bootmgr  /boot/bcd /Windows/System32/winload.exe

  sda2: __________________________________________________   ________________________      File system:       ntfs     Boot sector  type:  Windows Vista/7: NTFS     Boot sector info:  No errors found in  the Boot Parameter Block.     Operating System:       Boot files:         /bootmgr 

 sda3: __________________________________________________   ________________________      File system:       Extended Partition      Boot sector type:  Unknown     Boot sector info:   

sda5: __________________________________________________   ________________________      File system:       swap     Boot sector  type:  -     Boot sector info:

   sda6: __________________________________________________   ________________________      File system:       ext3     Boot sector  type:  -     Boot sector info:      Operating System:  Ubuntu 11.10      Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img   

I also tried to run grub-install on the mounted partition as suggested by one of the posts I linked to but I got this error
  
ubuntu@ubuntu:~/tmp$ sudo grub-install --root-directory=/home/ubuntu/tmp  /dev/sda6 /usr/sbin/grub-setup: warn: Attempting to install GRUB to a  partitionless disk or to a partition.  This is a BAD idea.. 
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be  installed in this setup by using blocklists.  However, blocklists are  UNRELIABLE and their use is discouraged..
 /usr/sbin/grub-setup: error: will not proceed with blocklists.

---

### Post by conte_matthew on 2013-04-11
Here is the full output from Boot-Repair:

[http://paste.ubuntu.com/5698675/](http://paste.ubuntu.com/5698675/)

---

### Post by darkod on 2013-04-11
You have at least one kernel in /boot, the 3.0.0-12 kernel. Have you tried booting it?

It should be in the grub2 boot menu in Previous Linux Versions.

If you can manage to boot that, you can run this to update all packages including the kernels:
```
sudo apt-get dist-upgrade
```

It's bery strange that installing SW would delete your kernels.

---

### Post by conte_matthew on 2013-04-11
I managed to repair grub using Boot-Repair. Now I can actually boot into Ubuntu but I get a black screen before the login and can't do anything. The first time, it did the disk check before going to a blank screen. (No terminal prompt, just completely blank.) I know there's a thousand things that could cause the blck screen but is there a way I can at least get a terminal?

---

### Post by grahammechanical on 2013-04-11
Can you boot into recovery mode? If there is not a recovery mode option or if it fails to boot, do this:

Select Ubuntu at the Grub menu and press E. That will put Grub in Edit mode. Now search for the line that has > initrd.lz quiet splash and change it to > initrd.lz recovery and then press F10 to boot.

In Recovery mode you can try Resume. That sometimes gets us to a desktop. But to get a command prompt with read and write access to the file system you need to do a bit of messing around.

1) Select Failsafex. That will run with the file system in read/write mode. But back out of failsafex at the next screen
2) Select Root. That will drop you to a root shell prompt. Normally, this will be in read only mode. which prevents updating the system. But as we have gone into Failsafex and backed out of it you will find that you have the file system in read/write and can run commands that change what is on the disk.

Regards.

---

### Post by conte_matthew on 2013-04-11
I was able to get access to recovery mode and eventually, was able to boot Ubuntu but only into a terminal. What can I do from here to fix the boot issue so that I can boot into the desktop? So far I've tried changing "quiet splash" to "nomodeset" as suggested in many places but I still get a blank screen.

---

### Post by darkod on 2013-04-12
That's a very difficult question since it seems your problem is not only missing kernels. If it was only a missing kernel, the 3.0.0-12 should have booted fine.

Once in the root shell you can try remounting the root partition as RW (the recovery mode by default mounts it as read-only), and try the dist-upgrade suggested above. After that's done, reboot and see how it goes.

The command to remount root as RW once you are in the root shell is:
```
mount -o rw,remount /
```

---

