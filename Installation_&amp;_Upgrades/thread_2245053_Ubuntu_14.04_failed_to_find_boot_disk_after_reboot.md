---
title: "Ubuntu 14.04 failed to find boot disk after reboot."
date: 2014-09-20
forum: Installation &amp; Upgrades
---

### Post by Eric_Battenberg on 2014-09-20
After rebooting my machine running Ubuntu 14.04, the bootloader (or whatever) fails to find the boot partition and I end up in an initramfs prompt (and am unable to type for some reason; usb keyboard issue?).  Besides recently installing smbfs (or mount.cifs) in order to mount samba shares, I don't think there were any significant upgrades of the kernel or bootloader that would've caused this.  

I tried running boot-repair recommended, but it didn't fix the problem.  My BootInfoURL is [http://paste.ubuntu.com/8390690/](http://paste.ubuntu.com/8390690/)

This is what I end up with:

Gave up waiting for root device. Common problem:
  - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system for the right device?)
  - Missing modules (cat /proc/modules; ls/dev)
ALERT!  /dev/disk/by_uuid/96aec9a6-de12-4c34-9190-b86e14653c70 does not exist. Dropping to a shell!


Any help would be greatly appreciated.

Thanks!
Eric

---

### Post by Eric_Battenberg on 2014-09-20
I have since booted from a Live CD, mounted my disks and backed up important files using scp.  So the disks are still mountable and they still exist.  Not sure why the bootloader is failing to find them.

---

### Post by oldfred on 2014-09-21
Best to see details:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Is this a newer UEFI system or BIOS boot system?
What mode is hard drive in AHCI or something else like IDE, RAID etc. Usually better with AHCI.

Another possibility:

  SOLUTION: Alert! /dev/disk/by-uuid/ ...<your UUID>.... does not exist 
[http://ubuntuforums.org/showthread.php?t=1127779](http://ubuntuforums.org/showthread.php?t=1127779)
[http://ubuntuforums.org/showthread.php?t=1565714](http://ubuntuforums.org/showthread.php?t=1565714)
"If the &#8220;apt-get upgrade&#8221; does not successfully complete then a flag is set and update-initramfs does not get to run, hence grub gets all messed up. You should be able to boot using the old kernel and then run the sudo update-initramfs &#8211;u -k command. Then run sudo dpkg &#8211;reconfigure. That should clear the upgrade flags and fix any broken packages."


 Gave up Waiting for Root Device? Change from UUID to sdaY
[http://ubuntuforums.org/showpost.php?p=10058668&postcount=2](http://ubuntuforums.org/showpost.php?p=10058668&postcount=2)

---

### Post by Mrnumber3isme on 2014-09-21
I had the exact same issue, but with no luck. I ended up installing Lubuntu instead, then simply downloaded the unity interface. works like a charm now.

---

### Post by Eric_Battenberg on 2014-09-21
Thanks for the thread links, @oldfred.  I'll investigate all of them.  

In the meantime, in my first post, I provided a BootInfo paste link.  Here it is again:  [http://paste.ubuntu.com/8390690/](http://paste.ubuntu.com/8390690/)

---

### Post by Eric_Battenberg on 2014-09-21
@oldfred,  Regarding the solutions where you boot into the old kernel.  I don't have an old kernel. :(  I get stuck at initramfs with a recovery kernel boot as well.  

And I can't type anything at the Busybox prompt.  Could this be a USB keyboard issue?  The keyboard works fine in the grub menu.

---

### Post by oldfred on 2014-09-21
I think keyboard issue is that drivers have not loaded. 

Boot-Repair has a chroot uninstall and reinstall grub2. I might try that. 
And if that by itself does not work, when in chroot add the extra commands while in the chroot to update initramfs.

---

### Post by Eric_Battenberg on 2014-09-22
Purging and reinstalling grub didn't work, so then I tried to update-initramfs from within chroot (by booting using LiveCD).  update-initramfs complained that it couldn't find /lib/modules/[my-kernel], so then I tried to install the linux-image for my kernel version. 

I had to mount/bind a bunch of stuff to get apt-get to work, specifically: dev, sys, proc, and then I had to copy /etc/resolv.conf to the chroot.  

After trying to install the linux-image again, it successfully rebuilt the image and I was able to boot!  

However, I still can't type anything to login, so I guess the usb drivers weren't loaded into the initramfs.  How do I go about making sure all the previous drivers are loaded into it?

---

### Post by oldfred on 2014-09-22
Some UEFI/BIOS have to have USB keyboard enabled. I might check that first.

---

### Post by Eric_Battenberg on 2014-09-22
It looks like all USB options involving ports and boot support are enabled in the BIOS.  How could I have failed to pull in the appropriate drivers when I ran update-initramfs.  As I recall, I couldn't type in BusyBox when the machine was previously failing to find the boot disk.

---

### Post by oldfred on 2014-09-22
Found this also:
 update-initramfs with keyboard drivers.
[http://ubuntuforums.org/showthread.php?t=2201983](http://ubuntuforums.org/showthread.php?t=2201983)

---

### Post by Eric_Battenberg on 2014-09-22
So I tried manually adding ohci_pci to /etc/initramfs-tools/modules and doing update-initramfs.  That didn't allow me to type.  Then I decided to manually install the kernel "sudo apt-get install linux-image-generic",  and now my keyboard works after rebooting.  Hooray!  

So the specific steps I took to solve my problem (that actually worked) were:
1. Burn LiveCD (actually made a bootable USB)
2. Boot from Live CD
3. Open terminal and mount everything. (My boot partition is /dev/sda2 and my home partition is /dev/sda3.)
```

sudo mount /dev/sda2 /mnt
sudo mount /dev/sda3 /mnt/home 
sudo mount -o bind /sys /mnt/sys
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

```
4. chroot
```

sudo chroot /mnt

```
5.  Install current kernel image, which updated my initramfs as well
```

sudo apt-get install linux-image-generic

```
6. Reboot

It doesn't seem like the boot-repair of grub was necessary.  And while doing update-initramfs with my current kernel (after manually installing the kernel image of my existing kernel) allowed me to boot, it was installing the new kernel that fixed my keyboard issue.  FYI, I was on kernel version 3.13.0-24-generic, and now am on 3.13.0-35-generic

---

### Post by milla974 on 2015-02-19
Hello, I have the exact same problem here and I would like to try this solution. But I don't know how to find my home partition and my boot partition ? I only have a linux partition and a linux swap.

---

### Post by sotiris2 on 2015-02-19
If you don't have a home partition that means it's included in your root partition as a folder. Ignore the 2nd line about home in Eric's instruction and do the rest. Just make sure you put the correct name of your ROOT partition instead of sda2 in the first line. All the other commands don't need adjustments

---

### Post by milla974 on 2015-02-19
It just tried this solution, but it only says "/mnt/sys does not exist". The same thing happens with dev.
So I couldn't go any further.

---

### Post by sotiris2 on 2015-02-19
Did you mount root partition first? Your root partition really should have sys, dev, proc directories and it should be mount at /mnt so mnt/dev should exist.

---

