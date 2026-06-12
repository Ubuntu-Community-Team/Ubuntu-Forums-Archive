---
title: "Clean install of 11.04 next to Win 7"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by Miraijin on 2011-06-15
So I've been trying to install 11.04 x64 on the same drive as Windows 7. The install seemed to go fine until it tried to install grub over the Windows 7 bootloader. My first try at this, I just told it to try again, and it seemed to install fine. It then rebooted and came up with the grub bootloader as expected. However, when it attempted to boot into 11.04, it gives me an error that says "unknown filesystem". It does however boot into Windows 7 fine.

While I was writing this up, I went into my BIOS to make sure that my SSD was set to be the primary boot drive and it was not. Changed the SSD to primary boot priority and away it went. For some reason, with the my other hard drive as the primary boot drive, it wouldn't boot to Ubuntu, but would behave just fine when going into Windows. Very strange behavior.

I rebooted the computer again to make sure that the boot priorities fixed the problem and the default background came up halfway, like a corrupted .jpg file, so I forced a shutdown. Now I'm back to what I started with. I've been rebooting to see if I can reproduce the good startup, but to no avail. Also, when grub is loaded, it either gives me a purple or black background. Is this normal? It seems to alternate randomly.

**TL;DR**
I get one of three errors when trying to boot into 11.04 from a clean install next to a fresh Windows 7 install.
"error: unknown filesystem"
"error: hd1 out of disk"
"error: you need to load the kernel first"
I also see a kernel panic every now and again.

I've got a bootable flash drive with 11.04 on it and that's what I've been trying to install from.

Ideas?

Edit:
I've been looking more into this issue, and from what I've uncovered in the forums is that the new grub bootloader that comes with Natty has some issues. I found the procedure for a downgrade of grub to the Maverick version, but I have not come across a 64-bit procedure. This downgrade has worked from what I've read so far.

---

### Post by rothux.j on 2011-06-15
Well keep at it, trying to fix it...
Just a thought... No chance of using Wubi from inside windows? I mean, if its going onto the same drive surely it doesn't make much difference...

---

### Post by Miraijin on 2011-06-15
I didn't see any reason to use Wubi if I was doing a clean install next to a vanilla Win7 install. However, it is something I haven't tried. I may try it at some point during this process. We'll see.

---

### Post by rothux.j on 2011-06-15
Personally, I prefer to do adjacent installs - what you are attempting...
But if GRUB is being unstable right now, then perhaps you should consider it. I've used it before and it really wasn't so bad... in fact I didn't notice any difference.

Have a read on wubi reviews and see what other people think.

---

### Post by Miraijin on 2011-06-15
Now that I actually understand what Wubi does, I'd definitely like for it to be an adjacent install. I can appreciate Wubi for what it is, but I'm not looking to try Ubuntu as is Wubi's primary design purpose. Thanks for the suggestion, but no thanks on actual implementation.

Kinda seems like the complete inverse of Wine.

---

### Post by rothux.j on 2011-06-16
Have a look at finding a version of grub that is fixed, and see about inserting it into the iso before you put it on your flash drive.
This one really doesn't make much sense to me...

When you installed ubuntu, did you choose ext4 in the partitioner? You might have to suck it up and drop to ext3, at least for a test. Might help - never know.
I'll continue to think for a while...

---

### Post by Miraijin on 2011-06-16
Alright, I'm trying your suggestion of installing on an ext3 filesystem.

Everything installs fine until it reaches the bootloader install. I get an error that says "Executing 'grub-install /dev/sda1' failed."

Grub is trying to install to the Windows 7 bootloader partition which is 100MB in size. This partition also happens to be on a completely separate hard drive from the OSes. Does that make any difference?

Since I couldn't get Natty's grub install to work, I tried the procedure listed here for the x64 grub downgrade to Maverick.
[http://ubuntuforums.org/showthread.php?t=1749902]("http://ubuntuforums.org/showthread.php?t=1749902")
It worked up until I had to select install devices. Before the debconf windows come up I noticed that it is asking if the device is mounted after it fails. I tried to make sure that they weren't, but I'm no expert here.

---

### Post by YesWeCan on 2011-06-18
> **Miraijin said:**
> Alright, I'm trying your suggestion of installing on an ext3 filesystem.

Everything installs fine until it reaches the bootloader install. I get an error that says "Executing 'grub-install /dev/sda1' failed."

Grub is trying to install to the Windows 7 bootloader partition which is 100MB in size. This partition also happens to be on a completely separate hard drive from the OSes. Does that make any difference?

Since I couldn't get Natty's grub install to work, I tried the procedure listed here for the x64 grub downgrade to Maverick.
[http://ubuntuforums.org/showthread.php?t=1749902]("http://ubuntuforums.org/showthread.php?t=1749902")
It worked up until I had to select install devices. Before the debconf windows come up I noticed that it is asking if the device is mounted after it fails. I tried to make sure that they weren't, but I'm no expert here.
Hang on. You are going down blind alleys. :)
You should not need to change Grub version. You don't need to install to ext3.

You have at least 2 problems (which are easy to encounter).
1) First, you need Grub installed to the disk that Ubuntu is on. It sounds like sda is your Windows disk. Find out which disk is Ubuntu and install to that, eg: sdb.
2) Second, it is trying to install to a partition (sda1) instead of the MBR of the disk, which would be sda. But make it sdb or whatever the Ubuntu disk is called.

You probably want to install Ubuntu again in order to use ext4.

FYI here is how to install Grub without installing Ubuntu again:
Boot your USB and run 'sudo fdisk -l' to see what your disks are called. Identify the one with your new Ubuntu on it. Note the disk name, eg: sdb, and the linux partition number, eg: sdb1. Then do:
sudo mount /dev/sdb1 /mnt'
sudo grub-install --boot-directory=/mnt/boot /dev/sdb

This should put a Grub loader in the MBR and you should now be able to boot your Ubuntu disk and get into Ubuntu. At this point, you should tell Grub to scan your drives and add menu entries for other OSs like Windows: sudo update-grub.

---

