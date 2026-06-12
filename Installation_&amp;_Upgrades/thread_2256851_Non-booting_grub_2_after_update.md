---
title: "Non-booting grub 2 after update"
date: 2014-12-15
forum: Installation &amp; Upgrades
---

### Post by simongsell on 2014-12-15
Hello everybody,

I am working with Ubuntu 14.04 installed on an old Dell Latitude Laptop. So far, due to (I suppose) a BIOS problem,  I had to boot manually from grub after each update of the kernel. I achieve it with the following commands :
```

grub> set root=(hd0,1)
grub> linux /boot/vmlinuz-3.13.0-29-generic root=/dev/sda1
grub> initrd /boot/initrd.img-3.13.0-29-generic
grub> boot

```


Each time I have to do it, I use the latest version available.
Recently, this workaround failed. I also tried to boot from an older version of the kernel but it fails anyway. It is quiet hard to describe the messages printed on the screen as I don't understand anything. However, this message has drawn my attention :
```

CPU : 0 PID :1 Comm : swapper/0 Not tainted 3.13.0-43-generic #72-Ubuntu

```

Then, the message "Call Trace :" is followed by a series of messages.

Does anyone have an idea in order to fix this ?

Thank you very by advance !

---

### Post by simongsell on 2014-12-15
After a new test, I could boot on an older version of the kernel (vmlinuz-3.13.0-40-generic instead of vmlinuz-3.13.0-43-generic), so the problem should be directly related to the latest version.

---

### Post by oldfred on 2014-12-15
Does recovery mode boot?

Did you install proprietary nVidia driver or other drivers directly from nVidia? When drivers are directly downloaded they are not registered and then the rebuild of initramfs does not happen correctly.

Just to see if install looks normal post link to summary report:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by simongsell on 2014-12-15
How could I test the recovery mode using grub commands ?

I didn't install any drivers from nVidia.

Here is my BootInfo report :
[http://paste.ubuntu.com/9531566/](http://paste.ubuntu.com/9531566/)

---

### Post by oldfred on 2014-12-15
I do not see anything unusual in report.

Recovery mode is just second line after each kernel line. May be in the sub-menu now.

You may want to house clean some older kernels, but be sure to keep one older one that you know still works.
14.04 is supposed to be deleting all but two kernels.

I prefer to use synaptic, so I can control versions I delete.
sudo apt-get install synaptic
       Determine your current kernel:
uname -a

            In synaptic search for linux-image to choose to delete old ones

    
Since a SSD, you must have AHCI on in BIOS, but please check. 
Some systems with IDE mode for drives have issues when kernels or other boot files are beyond 137GB on drive. The ext4 file system may write boot files anywhere in the / (root) partition, so they may be anywhere on drive. Then you may get random boot issues after update depending on where on drive files are written.
I do prefer to have smaller / (root) of 20 or 25GB and rest of drive for Data, or for newer users configuring rest of drive as /home is easier.

---

### Post by simongsell on 2014-12-17
OMG things are getting really bad. I deleted old kernel images, keeping only two : the new one which doesn't boot and a older one.
I tried to reboot on the new kernel (3.13.0-43-generic) but it failed again.
So I decided to keep using the old one (3.13.0-40-generic), hoping that a future update of the kernel will work better. I rebooted manually using grub2 commands and I made the change permanent with the following commands :
```

sudo update-grub
sudo grub-install /dev/sda

```

This procedure used to work well in the past.
But now it seems that I broke everything, and when I try to boot I get :
```

error : invalid arch-independent ELF magic
Entering rescue mode...
grub rescue >

```

The same message appear when I try to boot manually from grub rescue.
I have seen that this error is quiet usual for people who try to install ubuntu. But for me, everything was working pretty well until this kernel update ... 

Any help ?

Thank you,

---

### Post by oldfred on 2014-12-17
My notes have this:
 
 error: invalid arch independent ELF magic

 Often version of grub in MBR is not same as install. 
Use same version to reinstall or chroot and fully uninstall & reinstall grub.

But how you say you installed grub to MBR should not have different version of grub??
So I can only suggest the full uninstall, purge of grub and reinstall of grub.

Boot-Repair has a mode for that, I have not used it, but I think it just walks you thru the chroot & commands to uninstall grub & reinstall. 
Or you can just chroot & manually do the same.

You may be able to boot with Supergrub also.

When in chroot be sure to also move the grub folder. Not sure if Boot-Repair includes that or not.

Chroot into system and run these command.
 # uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda


 drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

      
 [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

Since you say laptop is older and drive is over 137GB, you may be having the older issue of some boot files beyond the 137GB boot limit. It really should only apply to very old BIOS, but have seen same issue with some not that old BIOS when in IDE mode, or when booting from USB drive.
Better to have smaller / (root) of 20 or 25GB and make rest of drive /home or data.

The df command included in summary report says you only have used 30GB, but ext4 randomly writes files anywhere on partition. You could shrink / to 60GB and see if then it boots. Of those I have suggested this to, only about 50% have had it work, but may be worth trying.

---

### Post by simongsell on 2014-12-19
I could boot with a live CD and I launched the recommanded repair in BootRepair. Here is the report given by BootRepaire : [http://pastebin.ubuntu.com/9564037/](http://pastebin.ubuntu.com/9564037/)
Fortunately now I can boot again, but still using the 3.13.0-40-generic kernel image. 
I agree that it would be a good idea to shrink / to 60GB.
An easier and more immediate solution. Shouldn't I just try to reinstall the 3.13.0-43-generic kernel image with synaptic ? I guess it could writen elsewhere on the partition.

---

### Post by oldfred on 2014-12-19
No harm in trying to reinstall kernel. 

You also show the flexnet issue. Grub now has work around so it does not cause any issues.
But flexnet is where Windows proprietary software with DRM writes code into the sectors just after the MBR and in same sectors as grub. It used to be a big issue as either grub overwrote flexnet and prevented users from running some Windows software that they usually paid large amounts for, or flexnet overwrote grub. But grub now finds it and writes around it.
 Adobe Photoshop, CAD/CAM, Rosetta Stone, Matlab others use flexnet.

But you do not have Windows, so then no proprietary Windows software. Is the flexnet entry left over from an old Windows install?

---

