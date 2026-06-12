---
title: "Ready to Repartion and Reformat"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by GadeTerbob on 2010-01-05
After installing 9.1 from a live disk, installation appeared normal on signature notebook. Ran updates using Synaptics. Updates completed without error. Removed live disk and rebooted. Error follows:

```
udevadm trigger is not permitted while udev is unconfigured.
udevadm settle is not permitted while udev is unconfigured.
svgalib: Cannot open /dev/mem.
Gave up waiting for root device. Common problems:
<<<<<<<<<<<<snip>>>>>>>>>>>>>>>>>>>
ALERT! /dev/disk/by-uuid/a88c5eca-3a57-4c29-90d5-964165883cb7 does not exist. Dropping to a shell!
```

The to exit from shell produces same error. Booting from the live disk ends in either black screen or what looks like wallpaper, both without clickable icon.

I'm ready to repartion and reformat and re-install but don't know how. Thanks in Advance!!

---

### Post by lmarmisa on 2010-01-05
Apparently the partition with UUID a88c5eca-3a57-4c29-90d5-964165883cb7 is not found.

Type these commands on the dropped shell:

```

fdisk -l
blkid

```

If you do not have root privileges, repeat both commands preceded with "sudo ".

Check if this UUID is shown by the blkid command and try to identify its type of partition (Linux, swap).

Best regards,

Luis

---

### Post by GadeTerbob on 2010-01-05
Thanks,

Neither of those commands are available in the built in shell: BusyBox v1.13.3

According to online doc at [http://www.busybox.net/downloads/BusyBox.html](http://www.busybox.net/downloads/BusyBox.html) they SHOULD be there, but typing the command at the prompt causes /bin/sh: fdisk: not found. 

Typing help also indicates neither function in the command list.

---

### Post by lmarmisa on 2010-01-05
Start your system with an Ubuntu Live CD, open a terminal a type theses two commands:

```

sudo fdisk -l
sudo blkid

```

Could you post the outputs of these commands?.

I have a doubt with your first comment: [I]Ran updates using Synaptics. Updates completed without error. Removed live disk and rebooted. 

[/I]The installation requires a system restart after the installation process is finished. So, I think that it is better to update your system when the system starts again after the installation of Ubuntu. I do not know if your early update is the origin of your problems.

Best regards,

Luis

---

### Post by GadeTerbob on 2010-01-05
I don't recall a post install reboot, so that's probably where I screwed up. Previous attempts to boot from live cd "making no changes to computer" has resulted in either black screen or wallpaper screen.

Trying immediately.

---

### Post by GadeTerbob on 2010-01-05
Live disk boot ended with wallpaper screen and inactive mouse cursor. While looking for a keyboard shortcut to open a command prompt, screen went black and can't be awakened by Cntrl, Shift, or Alt keys.

Thanks again for your time and attention. I'll pick this up again in about 10 hours.

---

### Post by lmarmisa on 2010-01-05
Check if your CD Live is damaged with the option "*Check disk for defects*".

I think that the hardware of your Acer TravelMate 2300 should be not a problem for installing Ubuntu 9.10.

Best regards,

Luis

---

### Post by GadeTerbob on 2010-01-06
fdisk -l output:

```
   Device   Boot       Start      End      Blocks       Id   System
/dev/sda1    *             1      4659    37423386      83   Linux
/dev/sda2               4660      4864     1646662*      5   Extended
/dev/sda5               4660      4864     1646631      82   Linux swap / Solaris
```

blkid output:

```
/dev/sda1: UUID="a88c5eca-3a57-4c29-90d5-964165883cb7" Type="ext4"
/dev/sda5: UUID="fb08452a-80e6-4f30-a3dd-8a496564a090" Type="swap"
```

---

### Post by GadeTerbob on 2010-01-06
lmarmisa,

Using the info you gave me, I've repartitioned, reformatted and reinstalled. Rebooted after install!! Running synaptics updates as I type this.

I knew this install might be difficult because of the bare minimum hardware.

Thank You! I couldn't have done it alone!!

---

### Post by aprochaska on 2010-02-01
I'm dealing with the same error.  I have a dual-boot config with partitions ubuntu 9.10, XP Pro, swap, and shared (data).  I reinstalled ubuntu into the existing ext3 partition and still get the error.

When you say "repartitioned, reformatted, reinstalled" that's a little frightening, but perhaps that's required.  I hope I could reformat only the ubuntu partition and could leave the rest of the disk intact.  ??

I have several 100 GB free on the disk.  Perhaps I should just create a new 20G partition for ubuntu and have a clean fresh install there.  Then later on I can figure out how to reclaim the other, broken ubuntu partition.

Thoughts?

---

### Post by GadeTerbob on 2010-02-01
I choose to go the whole hog route only because it gave me the opportunity to change to fat32 and remove an undesired factory partition.

My problem was finally determined to be hardware related. The hard disk crapped itself the very next day!

Good luck!!

---

### Post by aprochaska on 2010-02-02
I was able to get ubuntu to start by selecting the second choice in the bootloader menu (v16 instead of v17).  I thought I had done this before and it failed, but this time it worked.

:p

After getting onto the desktop, Update Manager had 214 updates to retrieve and install.  Took 2-3 hours.  The kicker was at the end when it asked whether to update GRUB (bootloader) with the one in the package or keep the local version which had been modified.  I chose to go with the package and it completed.    I suspect that this dialog was up when my wife found it yesterday, and she cancelled and restarted.  I can understand how things would be messed up if the process were aborted there.

Interesting.....during the installation it asked me if I wanted to preserve the four profiles it found (we four users).  I said "yes" to all of them.  Then when it came up, I was the only user created.  When I went in to create the other 3 users, it wouldn't let me point to an existing location to be their home directory.  It had to be a new directory which it would create.  I tried going in afterward and redefining it to be the original home dir (that part of the file system was intact), but that screwed it up.  On logging in again for those users' accounts, the system wasn't able to create some files in a hidden directory (.mumble).  I think this is still soluable (make the directory permissions match and then redefine to the preexisting dir), but I haven't gone there yet.

Anyway, we're running again.  Now I just have to work with users who don't remember where they stored their files, but don't understand directory structures or search, and expect them to "just be there".  (sigh)  You gotta love clients.....

Anyway, thanks for help from the folks in this thread.  Be well.

---

