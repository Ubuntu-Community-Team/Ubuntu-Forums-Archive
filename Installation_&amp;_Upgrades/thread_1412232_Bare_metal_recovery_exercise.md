---
title: "Bare metal recovery exercise"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by rustybutt on 2010-02-20
I'm going through the exercise of doing a bare metal recovery just to figure out how to do it BEFORE I have to do it.

Back in my Solaris days, we'd boot a machine off of CD, make a new file system on the new raw drive, restore the files from a level 0 dump tape (dump/restore), then install a boot block on /dev/c0t0d0, which in Solaris speak is akin to /dev/sda

I'm guessing there's something similar here.  To do the exercise, I'm using VMware Workstation VM's.   Instead of booting from CD, I'm booting from iso images, but using VM's shouldn't make any difference.

In my test case, my subject Ubuntu 910 VM had everything on one file system.  I did a level 0 dump.  I built a new VM with the same size virtual drive (not that it really mattered), as well as other identical specs (memory, peripheral devices, etc).  I booted the new VM off of the Ubuntu 910 install iso, partitioned the virtual drive the same as the original VM, made a file system on OS partition and restored to it.  Everything looks good.  

But now I'm stumped.  Haven't got a bloody clue as to what to do next.  I assume there's some sort of grub install, but fiddle-farting around with grub-install doesn't do it.

Suggestions?

Thanks!

Russ

---

### Post by falconindy on 2010-02-20
I essentially just did this tonight as an exercise on a VM, as im considering upgrading my live rig to Grub2... You'll need to mount up the newly dumped-to drive somewhere handy, and then the command you're looking for is something along the lines of:

```
grub-install --root-directory=/mnt /dev/sda --recheck
```
...Assuming that you've mounted the drive on /mnt and it's /dev/sda that you've restored to.

---

### Post by rustybutt on 2010-02-20
Just gave it a go.  I have the VM booted off the install iso.  But it barfed on me same as before:


root@ubuntu:~# grub-install --root-directory=/mnt --no-floppy --recheck /dev/sda1
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly

---

### Post by rustybutt on 2010-02-21
Oops...  tried it again, and this time specified /dev/sda

Much better...  almost...

root@ubuntu:~# grub-install --root-directory=/mnt --no-floppy --recheck /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sda
(hd1)   /dev/sdb


But when I boot to the virtual drive, I get grub and a selection of kernels to boot from, but when I accept the latest kernel, the boot fails with:


error:  no such device: 8dcddc9a-8aea-a9ae-c5f24245ef84

Press any key to continue...


Once I press the "any" key (heh...) it takes me back to the kernel selection menu.  So I tried editing the boot commands and lo and behold, there's a "search" command, which I eliminated and it booted farther, but then went to an initramfs shell prompt.

Further digging shows that /boot/grub/grub.cfg specifies the uuid to be that hex number above.  Because I deleted the search command in the boot command sequence, the VM started to boot.  I got the little splash screen with the Ubuntu logo, then it dropped to the shell I mentioned.  Now the error reads:

ALERT!  /dev/disk/by-uuid/8dcddc9a-8aea-a9ae-c5f24245ef84 does not exist...


At this point, I'm in a shell, but the / file system is not /dev/sda1, but is instead the file system in memory.  Clearly there's some uuid thingy that's not been done which needs to be done.  Gotta dig some more.

Ideas?

---

### Post by rustybutt on 2010-02-21
So it turns out that grub-install fails to deal with the uuid of the boot partition.  I tried to manually edit (yeah.  I know.  You're not supposed to manually edit it...)  /boot/grub/grub.cfg to reflect the actual uuid of the boot partition.  The booting process got farther along, but failed to fully complete and left the VM at a blank green screen.

So I restored the grub.cfg to what grub-install had done and instead altered the uuid of the boot partition with tune2fs.

tune2fs -U 8dcddc9a-8aea-a9ae-c5f24245ef84 /dev/sda1

That did the trick and the VM properly boots up!  Huzzah!

---

### Post by rustybutt on 2010-02-22
I've worked my way through the whole drill and figured it would be a good thing to post it here.   I used good old dump/restore to backup and restore my data.  It's not part of the default Ubuntu install, nor is it part of the Ubuntu Live CD, so you'll have to install it, but that's no biggie.

Here's the full exercise of dump/restore/bare metal recovery:

First I used dump to backup the boot partition of my original VM.

dump 0ujf [email]backup@ellington:/backups/VM_root_level0.dmp[/email] /dev/sda1

Explanation of options and command structure

Options:

0 - level 0 - dump the whole file system
u - update the /etc/dumpdates file
j - compress the dump
f - the following token is the dump file

ellington:/backups/VM_root_level0.dmp

ellington is my desktop host
/backups  is the directory where I put dump files
VM_root_level0.dmp  is the name of the dump file
backup is a UNIX user on ellington where my VM is defined ~backup/.rhosts

/dev/sda1 is the device name of the file system on the VM that I am backing up.

I then built a new VM similar to the original VM.

- same amount of memory
- same size virtual drive

Once I've booted the new VM into the Ubuntu Live environment I did:

1.  Open up a terminal and become root with:

    sudo su -

2.  Partition the virtual drive identical to the original VM

In my case, the boot partition is on /dev/sda1 and swap is on /dev/sda5.

root@ubuntu:~# fdisk /dev/sda

The number of cylinders for this disk is set to 1044.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xddb86ebc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         993     7976241   83  Linux
/dev/sda2             994        1044      409657+   5  Extended
/dev/sda5             994        1044      409626   82  Linux swap / Solaris


3.  Make the boot partition file system

     mkfs -t ext2 /dev/sda1

4.  blkid -u filesystem,other /dev/sda1

        make note of the UUID

5.  Configure networking to be have the same static IP address that
    the original VM had.

    route add default gw <gateway IP addr>

6.  Edit /etc/apt/sources.list to include the rest of the Ubuntu distribution

apt-get update

7.  apt-get install dump

8.  mount /dev/sda1 /mnt

9.  cd /mnt

10.  restore rlf [email]backup@ellington:/backups/VM_root_level0.dmp[/email]

11. grub-install --root-directory=/mnt --no-floppy --recheck /dev/sda

12.  Here's the tricky part.  grub-install fails to properly set the
     UUID for boot partition, so you have to manually change the boot
     partition UUID to match that which grub-install wants.  Instead
     of grub getting the UUID from the /dev/sda device, it gets it
     from the original /etc/fstab.

     You'll also need to make /dev/sda5 into a swap partition with a UUID
     to match what is in /etc/fstab.

From my /mnt/etc/fstab file:
=========================
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=8dcddc9a-8aea-4535-a9ae-c5f24245ef84 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f22c079b-b7de-4a31-9bd1-434cc9c49b98 none            swap    sw              0       0


UUID for the boot partition:
============================
The UUID for /dev/sda1 needs to be 8dcddc9a-8aea-4535-a9ae-c5f24245ef84

Notice that it is different from what you saw from the earlier blkid command.

Change the boot partition UUID with:

tune2fs -U <new UUID>  /dev/sda1

Re-run the blkid command as above to verify that the UUID has been updated.


UUID for the swap partition:
============================
The UUID for /dev/sda5 (swap) needs to be f22c079b-b7de-4a31-9bd1-434cc9c49b98

mkswap -U f22c079b-b7de-4a31-9bd1-434cc9c49b98 /dev/sda5




Example:
root@ubuntu:~# blkid -u filesystem,other /dev/sda1
/dev/sda1: UUID="ea104168-502b-4f92-a678-1351e49cf96d" TYPE="ext2"
root@ubuntu:~# tune2fs -U 8dcddc9a-8aea-4535-a9ae-c5f24245ef84 /dev/sda1
tune2fs 1.41.9 (22-Aug-2009)
root@ubuntu:~# blkid -u filesystem,other /dev/sda1
/dev/sda1: UUID="8dcddc9a-8aea-4535-a9ae-c5f24245ef84" TYPE="ext2"
root@ubuntu:~# mkswap -U f22c079b-b7de-4a31-9bd1-434cc9c49b98 /dev/sda5


reboot

---

### Post by barinov2000 on 2011-01-03
Anyone aware of Mondo Rescue package? It's pretty amazing what it does.  It doeas bare metal backup and does it on a live system, too.
[URL="http://www.mondorescue.org/"]
http://www.mondorescue.org/[/URL]

Good luck!

P.S. Don't use the one in standard repositories. Get the latest binaries from the site and try it.

[IMG]http://www.mondorescue.org/images/screenshots.png[/IMG]
[]("http://www.mondorescue.org/images/screenshots.png")

---

