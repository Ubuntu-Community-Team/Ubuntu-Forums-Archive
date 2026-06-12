---
title: "Intrepid install via alt CD leaves me with a grub prompt"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by Tonohono on 2008-11-14
Right.

My upgrade from Hardy to Intrepid was shaky, so I decided to do a clean install of Intrepid via the alternate CD.
First off, the install was extremely slow and would hang constantly for two to three minutes... Hitting Alt+F4 revealed the spamming of
```
buffer I/O error on device sr0 logical block xxxx
```
I let it be, for I saw no other errors.

Once my lengthy install is completed and reboot, I'm presented with a grub prompt. No menu whatsoever. "Hrm, perhaps I screwed up my partitioning schemes and forgot a bootable flag." So I try to install... two more times.

Figuring I couldn't have made the same mistake three times, I attempted an install with the Hardy 8.04.1 alternate CD. Installation was fast and went without a hitch. I reboot, and am happy to find a grub menu and working OS.

Another thing worth noting is the Hardy install detected my other OS and asked if I would like to add it to my grub menu, or something along those lines. The Intrepid install did no such thing.

Is there perhaps something new with the Intrepid install which I'm unfamiliar with, leading to this grub (and less importantly, buffer I/O) issue?

Thanks for the help!

---

### Post by littlebat on 2008-11-14
Maybe, there is some error when you burn Intrepid CD, re-download ISO file and install it from ISO file in harddisk directly. There is some useful information about how to install Ubuntu from Altertive CD image file here: [http://www.learndiary.com/en/2008/11/install-ubuntu-on-old-computer.htm](http://www.learndiary.com/en/2008/11/install-ubuntu-on-old-computer.htm) 
Change "hardy" into "intrepid" in the download link of "vmlinuz" or "initrd.img" for your Ubuntu 8.10.

---

### Post by kamni on 2009-02-06
I can't speak to the I/O problem, but I've had a similar problem with getting the grub prompt when doing a fresh install of Intrepid on two of my machines.  Did you try to install GRUB somewhere other than (hd0), like I did?

My Ubuntu is installed in a logical partition (hda5), and I use a different bootloader to access my other operating systems.  Hence, I installed GRUB only in hda5.

First I booted into Knoppix (5.1.1) to take a look at the install.  First, I went into the GRUB prompt and tried the following:

```
grub> root (hd0,4)
     Filesystem type is ext2fs, partition type 0x83
```

This is a good sign.  It means that GRUB and I both agree that my install is in hda5.  Sometimes the BIOS numbers the hard drives differently.  Next stop, trying to reinstall:

```
grub> setup (hd0,4)
     Checking if "/boot/grub/stage1" exists...no
     Checking if "/grub/stage1" exists...no

Error 2: bad file or directory type
```

I checked hda5, and /boot/grub/stage1 did exist.  I ran a file system check, and everything was fine.  So I did some research, and [here's what I think may have happened]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/207001"):  more recent versions of Ubuntu format an ext3 partition with 256-byte sized inodes, instead of 128 bytes.  GRUB can't handle this, and it seems that the GRUB used in the Intrepid install CD (or at least the one I have) hasn't been patched to accommodate the new size.

**How I fixed the problem:**

1) I booted back into Knoppix, and using qtparted, reformatted the partition as ext3 again.  

2) I restarted the Ubuntu installation CD, and when I got to the partitioning part of the install, I chose "Manual".

3) I clicked on hda5, chose "Edit Partition".  I told it to use the partition as ext3, I set the mount point as "/", but I left the format partition checkbox unchecked.

4) When I tried to go the next step, it gave me a warning about overwriting my files because I didn't format hda5.  I ignored it and chose "Continue".

5) In the "Advanced" configuration at the end, I told it to install in hda5.

The files installed, and when I rebooted everything worked as expected.  Hope this helps!

---

