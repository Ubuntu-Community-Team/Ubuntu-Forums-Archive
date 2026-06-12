---
title: "Corrupt master boot record or Grub?"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by tomreid on 2010-11-27
Hi

I have a very frustrating problem that I seem unable to resolve.

I think I managed to corrupt my master boot record, or have a very intractable problem with Grub.

I'm not sure how I did this, but my desktop will boot Ubuntu fine from a USB, but every time I try to install it, the install seems to go fine, but when I finish the install and the machine tries to boot the OS from it's hard drive, it does not work. The monitor does not get a signal and it just goes to sleep.

I tried posting here to resolve the problem before, tried everything on this thread: [http://ubuntuforums.org/showthread.php?t=1572607](http://ubuntuforums.org/showthread.php?t=1572607)

But nothing worked. 

I have even tried running the system from a USB, running a "shred" command for the hard drive and then reinstalling  - my theory was that the shred command would destroy all the data on the hard drive anyway, and allow a "clean" install from whatever was corrupt on it, but no luck - when I installed Ubuntu on the hard drive, same problem.

I'm not clear where the problem lies now, I'm assuming there is something up with it's master boot record, but there are no partitions on it's hard drive and I started with a completely blank, unformatted drive.

Most frustrating.

Any help gratefully received. 

cheers

---

### Post by efflandt on 2010-11-27
My first thought was that maybe your BIOS was set to protect the mbr.  But that would not be the case unless you specifically set that after installing 9.10, because boot info script shows it as grub2.

One time when I accidentally formatted a floppy for Mac instead of DOS from the shell, I could not DOS format it until I wrote zeros to the beginning of the disk.  So maybe try writing 1 MB of zeros to the beginning of the drive just in case something is mixed up in the mbr or partition table.

**[COLOR=Red]WARNING:[/COLOR]****This will remove MBR and partition table from /dev/sda**

```
dd if=/dev/zero of=dev/sda count=2K
```Then use gparted on live/install iso to create "MSDOS partition table" and whatever partitions you want and reinstall.

I just did that for a USB stick when I was not sure if an iso that I had earlier dd'd directly to it would interfere with trying to partition it normally (works fine).

What brand of drive is it?  wdc.com has DataLifeguard software that can boot from CD or floppy to test Western Digital drives.  Seagate might also have a bootable version of their SeaTools to check Seagate or Maxtor drives.

---

### Post by oldfred on 2010-11-27
If it is the monitor going to sleep it may be the video driver. I install from USB and could tell the install was still working as USB was still flashing but monitor was asleep. After use nomodeset I installed and it went to sleep on first boot. 

On first boot after install, press e on getting the GRUB bootloader. Hold shift from BIOS boot if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

---

