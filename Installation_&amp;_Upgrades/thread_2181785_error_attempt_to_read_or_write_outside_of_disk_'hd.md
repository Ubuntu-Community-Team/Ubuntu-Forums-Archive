---
title: "error: attempt to read or write outside of disk 'hd0'"
date: 2013-10-19
forum: Installation &amp; Upgrades
---

### Post by danielsender on 2013-10-19
Hi,

I have a Dell laptop model Precision M50 with dual boot XP and kubuntu. Today I decided to upgrade from 13.04 to 13.10. The upgrade went apparently fine, but at the end when I restarted the machine I got a right Grub menu, but when I hit the selection I get:

```
Loading Linux 3.11.0.-12-generic
error: attempt to read or write outside of disk 'hd0'
Loading initial ramdisk ...
error: you need to load the kernel first.
Press any key to continue...

```

However, when I clicked on an older kernel it booted ok - is anything missing here?

Thanks.

---

### Post by heir4c on 2013-10-19
Remove the kernel version 3.11.0-12 
Install first synaptic, that easier to see al the installed packages. Look for that kernelversion. Take your time to do that. You need to look for linux-image and linux-headers.
Do a grub update and restart.
Than you do a update & upgrade via the update manager.

Edit: I see now you use Kubuntu, so I don't now if synaptic is used by Kubuntu or if there is a other program for that in Kubuntu.

---

### Post by danielsender on 2013-10-19
> **heir4c said:**
> Remove the kernel version 3.11.0-12 
Install first synaptic, that easier to see al the installed packages. Look for that kernelversion. Take your time to do that. You need to look for linux-image and linux-headers.
Do a grub update and restart.
Than you do a update & upgrade via the update manager.

Edit: I see now you use Kubuntu, so I don't now if synaptic is used by Kubuntu or if there is a other program for that in Kubuntu.

prior to reading the reply I ran "update-initramfs -u -k all" and now all the past kernel versions give me the same problem, in other words I cannot boot the machine, what can I do?

Thanks.

---

### Post by heir4c on 2013-10-19
Can you boot in the recovery mode (modus?) ?

---

### Post by danielsender on 2013-10-20
> **heir4c said:**
> Can you boot in the recovery mode (modus?) ?

Things are getting worse: No, I could not boot in recovery mode, so I used a "boot-repair" disk and clicked on "recommended repair" and after finishing I rebooted and the grub menu didn't come out, it went directly to boot XP as if there wasn't any linux installed. I repeated the same procedure again with the same result. On the other hand, this "boot-repair" disk mounts the linux disk without problem and all the files seem to be there. Furthermore, at the end I unmounted the linux system and ran 'e2fsck /dev/sdb1" and the response was that the system is clean.

---

### Post by heir4c on 2013-10-20
I think it messed up with that commando. I never used that before so I don't now what it do. And I don't now how to solve that. Maybe with a grub renewing/install from live-dvd/usb. Or do a new install of 13.10.Boot up with a live-dvd/usb of Ubuntu 13.10. Backup your files first. 
Than do a new install of Ubuntu.
Try it first out in the live session.

---

### Post by danielsender on 2013-10-20
> **heir4c said:**
> I think it messed up with that commando. I never used that before so I don't now what it do. And I don't now how to solve that. Maybe with a grub renewing/install from live-dvd/usb. Or do a new install of 13.10.Boot up with a live-dvd/usb of Ubuntu 13.10. Backup your files first. 
Than do a new install of Ubuntu.
Try it first out in the live session.

Using a live CD and after chroot I re-installed grub ('grub-install /dev/sdb') and then I got the list again, so I tried booting 3.11.0-12 giving me again the same problem (reading/writing outside of disk hd0), so I went back to the previous kernel and I was able to boot the machine. However is now in low-resolution and I can't figure out how to fix this. Also, using synaptic I re-installed 3.11.0-12 with all the related packages, e.g. headers, etc., but when I attempted to boot that kernel I got back the same problem. I don't care staying with the old kernel, but I have to figure out how to get the full resolution again (1600x1200), that is not appearing in the display settings GUI. I noticed that the size of the file for 3.11.0-12 is significantly bigger that all the previous kernels, I wonder if this has to do with the problem.

---

### Post by heir4c on 2013-10-20
Can you post here a screenshot of gParted from the live-dvd/usb so we can see how your partitions are set?

---

### Post by danielsender on 2013-10-20
> **heir4c said:**
> Can you post here a screenshot of gParted from the live-dvd/usb so we can see how your partitions are set?

This is the result for 'sudo fdisk -l'

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5f658c0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625137344   312568641    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006d1ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   300511889   150255913+  83  Linux
/dev/sdb2       300511951   312576704     6032377    5  Extended
/dev/sdb5       300511953   312576704     6032376   82  Linux swap / Solaris
```

Ubuntu is on sdb, XP on sda

---

### Post by SeijiSensei on 2013-10-20
hd0 is the equivalent of /dev/sda, but your Linux installation is on /dev/sdb which grub calls hd1.

Do you still get the menu of kernel choices if you boot from the hard drive?  If so, you can try editing the commands to boot by going to Advanced, selecting the entry for the new kernel with the cursor, and hitting "e" to edit.  Try replacing the entry for "hd0" in the "set root=" line with "hd1" and continuing the boot with F10.  If that works, you can make the change permanent like this.

Reboot and follow the same approach above but choose the "recovery mode" kernel instead.  Choose "root shell" from the options when they are presented to you.  Next run "mount -o remount,rw /" to make the filesystem writable.  Now go to /boot/grub and run "chmod u+rw grub.cfg" so you can edit the file.  Replace the "hd0" with "hd1" in the "set root=" line and save the file.  Then use "chmod u-w grub.cfg" to make it read-only again.  Now try rebooting and see if it uses the right hard drive.

---

### Post by danielsender on 2013-10-21
> **SeijiSensei said:**
> hd0 is the equivalent of /dev/sda, but your Linux installation is on /dev/sdb which grub calls hd1.

Do you still get the menu of kernel choices if you boot from the hard drive?  If so, you can try editing the commands to boot by going to Advanced, selecting the entry for the new kernel with the cursor, and hitting "e" to edit.  Try replacing the entry for "hd0" in the "set root=" line with "hd1" and continuing the boot with F10.  If that works, you can make the change permanent like this.

Reboot and follow the same approach above but choose the "recovery mode" kernel instead.  Choose "root shell" from the options when they are presented to you.  Next run "mount -o remount,rw /" to make the filesystem writable.  Now go to /boot/grub and run "chmod u+rw grub.cfg" so you can edit the file.  Replace the "hd0" with "hd1" in the "set root=" line and save the file.  Then use "chmod u-w grub.cfg" to make it read-only again.  Now try rebooting and see if it uses the right hard drive.

Yes, after re-installing grub I can now boot from the hard drive and get the kernel choices. However, after hitting "e" I see that the line in question already shows: "set root='hd1,msdos1'", so that doesn't seem to be the problem, unless there is something fishy with the msdos1 word. Again, if a boot another kernel, it boots alright, however only in low graphics mode that I cannot change with the "Display" GUI.

---

### Post by heir4c on 2013-10-21
That 160GB HD, is that a USB HD? If it is a usb Hard Drive, read this topic. Maybe you can find something that you can use.
[http://ubuntuforums.org/showthread.php?t=2173056](http://ubuntuforums.org/showthread.php?t=2173056)

---

### Post by danielsender on 2013-10-21
> **heir4c said:**
> That 160GB HD, is that a USB HD? If it is a usb Hard Drive, read this topic. Maybe you can find something that you can use.
[http://ubuntuforums.org/showthread.php?t=2173056](http://ubuntuforums.org/showthread.php?t=2173056)

No, is not an USB HD, is a regular PCI disk. I was wondering if the size of the initrd.img's have anything to do with the issue. All the older ones have sizes around 20MB, while the one in question is 24MB.

---

### Post by heir4c on 2013-10-21
It's strange, I installed today a mini.iso on my second HD (intern) and have grub installed on the second HD because I want to boot via the BIOS-menu and than choose the second HD to boot. But It messed up or something like that because when I try to boot from the second HD and choose the first Ubuntu in the list than he start up my old Ubuntu and not the mini.iso. Then when I boot up from the first HD and choose the first Ubuntu he can't find the Drive. (the second for booting the mini.iso install I guess) He gives a UUID number (I think the second HD UUID I don't check it) and then he stop. So it's the same, just without the message of the read or write outside of disk. So he first install the grub not to the sdb but on the sda and then he can't find the second HD. Very strange. (first HD 250GB and second 160GB)
I used the BIOS boot for the install above the UEFI boot (for booting the usb to install the mini.iso). (motherboard 2years old). :frown: ](*,) :-k

---

### Post by danielsender on 2013-10-21
> **heir4c said:**
> It's strange, I installed today a mini.iso on my second HD (intern) and have grub installed on the second HD because I want to boot via the BIOS-menu and than choose the second HD to boot. But It messed up or something like that because when I try to boot from the second HD and choose the first Ubuntu in the list than he start up my old Ubuntu and not the mini.iso. Then when I boot up from the first HD and choose the first Ubuntu he can't find the Drive. (the second for booting the mini.iso install I guess) He gives a UUID number (I think the second HD UUID I don't check it) and then he stop. So it's the same, just without the message of the read or write outside of disk. So he first install the grub not to the sdb but on the sda and then he can't find the second HD. Very strange. (first HD 250GB and second 160GB)
I used the BIOS boot for the install above the UEFI boot (for booting the usb to install the mini.iso). (motherboard 2years old). :frown: ](*,) :-k

I have two disks: the first one sda (hd0?) is fixed and the second one sdb (hd1?) is removable but not USB. I have Ubuntu and grub installed in the removable because in the first one I have XP and I want to be able to replace the removable with a DVD burning drive (the main optical drive does not burn DVDs) and burn using windows, so in my BIOS the booting order is first the removable and if that is not there then the fixed one. This arrangement has been working fine for quite a few years, is just this kernel that is giving me problems. I wonder if there is something "hardwired" in the kernel that assumes that system is installed in hd0.

---

### Post by heir4c on 2013-10-21
Yes, I think the same. I have also kernel 3.11 on the mini.iso. So, tomorrow I will install the mini.iso of 12.04 (or 13.04) instead of 13.10, than I can see if it boot up with the right settings (install on sdb5 and grub on sdb).

---

### Post by heir4c on 2013-10-22
I install the mini.iso 13.04 (because the  12.04 has an error in the iso) 
I install the grub on the sdb and it would not work. I made a mistake. I saw on the partitionmanager (text based) that the installing was on sdd 5 instead of sdb5, because I had 2 usb plugged in. So when I installed grub on the sdb it go wrong. 
So, I reinstalled the mini.iso of 13.10 on sdd5 and grub on sdd and it work now. 

Normally when grub is installed he do that by default on the first HD in the computer. You reinstalled grub on the sdb so it can't be a mistake like I did.

Strange problem. Weird is that he mentioned hd0, because that is your first HD (sda). And no Ubuntu or grub is on that one.
Can you remove the new kernel (when you boot up with a previous kernel)? 
Maybe you can remove the first HD (320GB) and boot up from the 160GB HD.

---

### Post by oldfred on 2013-10-22
From grub or BIOS the boot drive is always hd0. So if directly booting sdb, the the entry of hd0 would be correct. If booting from grub in sda as hd0 then hd1 would be correct.

---

### Post by danielsender on 2013-10-22
> **oldfred said:**
> From grub or BIOS the boot drive is always hd0. So if directly booting sdb, the the entry of hd0 would be correct. If booting from grub in sda as hd0 then hd1 would be correct.

This makes sense, otherwise all other kernels in the grub list would be wrongly specified, that incidentally have all the same parameters as the one giving the problem. I think is something in the kernel that is broken.

---

### Post by danielsender on 2013-10-24
> **danielsender said:**
> This makes sense, otherwise all other kernels in the grub list would be wrongly specified, that incidentally have all the same parameters as the one giving the problem. I think is something in the kernel that is broken.

Somehow old remains of proprietary nvidia drivers were the culprit for this behaviour. I removed all these nvidia* packages and re-installed the nouveau driver and I can now boot that kernel. In any case the nvidia driver that would work with my machine is not longer supported by ubuntu (96.x.x).

As I showed in another posting ( [http://ubuntuforums.org/showthread.php?t=2182856&p=12824848#post12824848](http://ubuntuforums.org/showthread.php?t=2182856&p=12824848#post12824848) ) the low resolution problem still remains, and it seems to be due to some error shown in the Xorg.0.log file that I attached in that posting. 
```
[    39.159] (EE) [drm] KMS not enabled
```

I wonder what this message means.

---

### Post by danielsender on 2013-10-30
> **danielsender said:**
> Somehow old remains of proprietary nvidia drivers were the culprit for this behaviour. I removed all these nvidia* packages and re-installed the nouveau driver and I can now boot that kernel. In any case the nvidia driver that would work with my machine is not longer supported by ubuntu (96.x.x).

As I showed in another posting ( [http://ubuntuforums.org/showthread.php?t=2182856&p=12824848#post12824848](http://ubuntuforums.org/showthread.php?t=2182856&p=12824848#post12824848) ) the low resolution problem still remains, and it seems to be due to some error shown in the Xorg.0.log file that I attached in that posting. 
```
[    39.159] (EE) [drm] KMS not enabled
```

I wonder what this message means.

I found the problem. The removal/purge of the nvidia proprietary drivers didn't remove the blacklisting file: /etc/modprobe.d/nvidia-installer-disable-nouveau.conf that contains:
```
# generated by nvidia-installer
blacklist nouveau
options nouveau modeset=0
```

After removing this file, the graphics went back to normal.

I hope this helps someone else.

Cheers,

Daniel

---

### Post by JurajH on 2013-11-09
Found a clue here:
[http://ubuntuforums.org/showthread.php?t=2107351](http://ubuntuforums.org/showthread.php?t=2107351)

What I did:
sudo mv /initrd.img /initrd.img.bak
sudo dpkg --configure -a
sudo apt-get install --reinstall linux-image-3.11.0-13-generic

After reboot I was able to boot system with 3.11.0-13 kernel. Let us know, if it works

---

### Post by danielsender on 2014-05-16
> **JurajH said:**
> Found a clue here:
[http://ubuntuforums.org/showthread.php?t=2107351](http://ubuntuforums.org/showthread.php?t=2107351)

What I did:
sudo mv /initrd.img /initrd.img.bak
sudo dpkg --configure -a
sudo apt-get install --reinstall linux-image-3.11.0-13-generic

After reboot I was able to boot system with 3.11.0-13 kernel. Let us know, if it works

The problem recurred on my system after upgrading to 14.04, however this time it wasn't due to blacklisting of the driver. I applied the solution you posted and worked really well. Thanks.

---

