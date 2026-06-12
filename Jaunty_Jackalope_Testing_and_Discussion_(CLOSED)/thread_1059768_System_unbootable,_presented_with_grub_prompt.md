---
title: "System unbootable, presented with grub prompt"
date: 2009-02-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by LadFromWales85 on 2009-02-04
Hey all,
I recently upgraded to Jaunty a couple of weeks ago, and converted my ext3 system partition to ext4.  I have managed to successfully boot into the system several times since the change.
I performed a routine reboot, and was given an error 24 by grub when attempting to boot into the latest kernel.  Booted from a recent Ubuntu cd and ran fsck which found a few errors which it corrected.

Since doing this, grub is no longer presenting me with a menu at all, just a prompt.

After running
```
sudo mount -t ext4 /dev/sda2 /mnt/sda2
sudo mount -t proc none /mnt/sda2/proc
sudo mount -o bind /dev/mnt/sda2/dev
sudo chroot /mnt/sda2 /bin/bash

```

I ran grub to attempt to reset it up and this was the output
```
root@ubuntu:/# sudo grub
sudo: unable to resolve host ubuntu
Probing devices to guess BIOS drives. This may take a long time.
Unknown partition table signature

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd0,1)
root (hd0,1)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,1)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> exit
exit

Error 27: Unrecognized command
grub> quit
quit

root@ubuntu:/# sudo update-grub
sudo: unable to resolve host ubuntu
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-6-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

But looking at /boot/grub/menu.lst it appears as though it hasn't been changed, still containing boot entries for older kernels which I have removed previously and have been reflected in bootups.

Having used linux consistantly over the past three years, I have never had to recover an unbootable system, so I'm a bit lost at the moment! :(

Anyone have any ideas to get my system booting happily again?

Thanks in advance for any advise :D

---

### Post by regala on 2009-02-04
> **LadFromWales85 said:**
> Hey all,
Anyone have any ideas to get my system booting happily again?

Thanks in advance for any advise :D

Just to let you know, Grub exists in two "versions":
- legacy: 0.97 cannot and will never be able to read ext4 partitions, thus to boot any kernel on such filesystems.
- grub2: 1.9* can boot ext4 filesystems since a few weeks now, but is still considered experimental by some distributors. The focus on ext4 will surely improve the code base and stability.

Now the questions are: what version of grub did you run on your system and did you have a /boot partition separated from / (I guess you don't)

I think you "upgraded" to ext4 while you were using grub legacy, which renders it the / unreadable by grub at boot.
You can try to get a bootable usb disk (key, dongle, whatever) with grub2 on it (or a grub2 floppy disk).

the important point is: you absolutely need grub2 to be able to read whatever is on an Ext4 filesystem.

---

### Post by LadFromWales85 on 2009-02-04
After converting my system filesystem to ext4, I have booted from it two or three times fine, so the current version of grub appears to be able to work from ext4 fine.

I've never messed around with grub, so at a guess I have the standard grub version that comes packaged with Jaunty

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/314350](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/314350) It would appear as though the packaged grub does support booting from ext4 filesystems.

You are correct in saying that I don't have a /boot partition.  When the next reinstall comes I will make it a separate ext2 partition, which should avoid this occurrence again!

Why is grub setup not writing anything to menu.lst when it claims that it is after chrooting my mounted system partition.

I'll download a grub2 cd boot image and give that a go, but as the system has been booting fine since the filesystem conversion, something else is probably wrong?

---

### Post by autocrosser on 2009-02-04
Grub was patched by Colin to support ext4 partitions--what happened is that the "new" grub did not update update-grub--there are a couple of threads about this & I'm not up to speed this morning to advise you about it--There is a answer WITHOUT using a separate /boot partition.

OK--I just pulled up the old bug report--look thru it for answers & post to it if that won't solve your problem-----

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/316872](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/316872)

---

### Post by autocrosser on 2009-02-04
I'm sorry regala--that is wrong information--grub was patched to use ext4.


> **regala said:**
> Just to let you know, Grub exists in two "versions":
- legacy: 0.97 cannot and will never be able to read ext4 partitions, thus to boot any kernel on such filesystems.
- grub2: 1.9* can boot ext4 filesystems since a few weeks now, but is still considered experimental by some distributors. The focus on ext4 will surely improve the code base and stability.

Now the questions are: what version of grub did you run on your system and did you have a /boot partition separated from / (I guess you don't)

I think you "upgraded" to ext4 while you were using grub legacy, which renders it the / unreadable by grub at boot.
You can try to get a bootable usb disk (key, dongle, whatever) with grub2 on it (or a grub2 floppy disk).

the important point is: you absolutely need grub2 to be able to read whatever is on an Ext4 filesystem.

---

### Post by plun on 2009-02-04
> **autocrosser said:**
> I'm sorry regala--that is wrong information--grub was patched to use ext4.

Yup, correct.

Grub2 bugs seems to be unchanged and all bugs remains, both Ubuntu and Debian and I don't trust it for a mixed PC.


The challenge in this thread with grub is a bit strange....latest kernels has been missed for me  (meny.lst writings)

---

### Post by LadFromWales85 on 2009-02-04
I decided to take the easy route and backup and reinstall, and at the same time doing some much needed partition changes, bigger linux partition, less NTFS storage as I have a large LVM for storage now :)

Just going to tackle the install now!

Cheers for your advise though guys :)

---

### Post by regala on 2009-02-06
> **autocrosser said:**
> I'm sorry regala--that is wrong information--grub was patched to use ext4.

yeah, in Ubuntu. not upstream. because grub 0.97 is a mess, wrt ext{2,3,4}, and it will never be patched that way upstream. Upstream only develops grub2, that's what I meant. I guess I prefer "official" versions :)

([http://www.gnu.org/software/grub/grub-legacy.en.html](http://www.gnu.org/software/grub/grub-legacy.en.html))

---

### Post by autocrosser on 2009-02-06
You are in the testing forum for Ubuntu & as such, we use the official d/l's from Ubuntu--I know that upstream is not supporting grub with ext4, but as of Alpha 3 we were--so advising someone that ext4 is not supported by grub was a wrong statement--We as here to support anyone that wants to test with as much correct information as possible.

I, for one--am impatent for grub2---but its not stable enough for me to use & I was one of the people that asked the developers to patch grub so testing for ext4 could begin---ext4 is very important to the next couple of releases & I felt that it needed wide testing ASAP.

---

