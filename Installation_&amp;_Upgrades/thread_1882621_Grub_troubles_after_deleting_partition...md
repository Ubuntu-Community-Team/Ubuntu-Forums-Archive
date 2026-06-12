---
title: "Grub troubles after deleting partition.."
date: 2011-11-17
forum: Installation &amp; Upgrades
---

### Post by jonnyboysmithy on 2011-11-17
I had ubuntu 11.04 and 11.10 installed on my laptop. After restoring my home folder I proceeded to delete the partition with 11.10 on it (I decided to keep 11.04).
After deleting the partition and rebooting my pc, I'm left with a grub rescue> prompt.
I have tried all the tutorials I could find, I have tried boot-repair but that didn't fix it.
atm I'm running from a liveusb with ubuntu 11.04 on it, [COLOR="Black"]**Im stumped.**[/COLOR]
```
 sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3ea65017

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1212     9732631    7  HPFS/NTFS
/dev/sda2            1212        7296    48871425    5  Extended
/dev/sda5            7042        7296     2043904   82  Linux swap / Solaris
/dev/sda6            1212        6069    39016122+  83  Linux
/dev/sda7   *        6070        7041     7807558+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 2065 MB, 2065694720 bytes
64 heads, 62 sectors/track, 1016 cylinders
Units = cylinders of 3968 * 512 = 2031616 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b6e2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1016     2015713    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 
```
EDIT: sda1 is windows xp 
sda2 extended
sda5 swap
sda6 home
sda7 has the 11.04 system on it

---

### Post by jonnyboysmithy on 2011-11-17
```
ubuntu@ubuntu:~$ sudo mount dev/sda7 /media/mountpoint
mount: special device dev/sda7 does not exist
ubuntu@ubuntu:~$ sudo mount dev/sda7 /media/mountpoint

```this is where I'm stuck at. (the directory /media/mountpoint exists)

---

### Post by darkod on 2011-11-17
You're missing one more /.

sudo mount /dev/sda7 /mnt (no need to create anything for temporary fix, /mnt exists by default)
sudo grub-install --root-directory=/mnt /dev/sda

It always has / at the start.

I guess you are sure sda7 is your root since you are using that command.

Another thing I noted is that the boot flag is on sda7 while it probably should be on sda1, the XP partition. On the other hand grub might boot XP successfully even without a boot flag. For windows bootloader it should be on sda1.

---

### Post by jonnyboysmithy on 2011-11-17
> **darkod said:**
> You're missing one more /.

sudo mount /dev/sda7 /mnt (no need to create anything for temporary fix, /mnt exists by default)
sudo grub-install --root-directory=/mnt /dev/sda

It always has / at the start.

I guess you are sure sda7 is your root since you are using that command.

Another thing I noted is that the boot flag is on sda7 while it probably should be on sda1, the XP partition. On the other hand grub might boot XP successfully even without a boot flag. For windows bootloader it should be on sda1.Thanks! that worked. I manualy changed the boot flag, I've changed it back now.

---

### Post by jonnyboysmithy on 2011-11-17
[http://paste.ubuntu.com/741581/](http://paste.ubuntu.com/741581/) probably a case of purging and reinstalling grub... (if i can manage that :/)
EDIT: boot-repair couldn't fix my grub so I'll try manually when I've got time.

---

### Post by darkod on 2011-11-17
You have no boot files or kernel files on sda7. Are you sure you deleted the correct partition? there doesn't seem to be an ubuntu installation present.

---

### Post by jonnyboysmithy on 2011-11-17
> **darkod said:**
> You have no boot files or kernel files on sda7. Are you sure you deleted the correct partition? there doesn't seem to be an ubuntu installation present.Oh...:shock::-\"

EDIT:Okay I'm sure I kept the right partititon, I installed some themes manually on the 11.04 partition and they are there.
I can't make much of the log/report, what do you suggest I do?

EDIT2: Heres a list of the files under /boot/

/media/ffdb517d-a8fc-483a-80c0-8775fb906c4e/boot/grub
/media/ffdb517d-a8fc-483a-80c0-8775fb906c4e/boot/abi-2.6.38-8-generic
/media/ffdb517d-a8fc-483a-80c0-8775fb906c4e/boot/abi-2.6.38-12-generic
/media/ffdb517d-a8fc-483a-80c0-8775fb906c4e/boot/config-2.6.38-8-generic
/media/ffdb517d-a8fc-483a-80c0-8775fb906c4e/boot/config-2.6.38-12-generic
/media/ffdb517d-a8fc-483a-80c0-8775fb906c4e/boot/initrd.img-2.6.38-8-generic
/media/ffdb517d-a8fc-483a-80c0-8775fb906c4e/boot/initrd.img-2.6.38-12-generic
/media/ffdb517d-a8fc-483a-80c0-8775fb906c4e/boot/memtest86+.bin
/media/ffdb517d-a8fc-483a-80c0-8775fb906c4e/boot/memtest86+_multiboot.bin
/media/ffdb517d-a8fc-483a-80c0-8775fb906c4e/boot/System.map-2.6.38-8-generic
/media/ffdb517d-a8fc-483a-80c0-8775fb906c4e/boot/System.map-2.6.38-12-generic
/media/ffdb517d-a8fc-483a-80c0-8775fb906c4e/boot/vmcoreinfo-2.6.38-8-generic
/media/ffdb517d-a8fc-483a-80c0-8775fb906c4e/boot/vmcoreinfo-2.6.38-12-generic
/media/ffdb517d-a8fc-483a-80c0-8775fb906c4e/boot/vmlinuz-2.6.38-8-generic
/media/ffdb517d-a8fc-483a-80c0-8775fb906c4e/boot/vmlinuz-2.6.38-12-generic

---

### Post by darkod on 2011-11-17
Uhhh, I've never done this, but I can give it a shot. If sda7 is surely the root partition, we can try entering it from live mode with chroot and trying to install the kernel and grub files. I know recreating grub files works, but installing a kernel is a different thing.

First to enter as chroot:

```
sudo mount /dev/sda7 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
```Now you should be inside as if the installation was running and not live mode. Trying to install the kernel and recreate grub files:

```
apt-get install linux-image (not sure if you need a number or it picks it up itself)
grub-mkconfig
update-grub
```Note: In the second group of commands you don't need to use sudo because entering with chroot you are already the root user.

Hopefully if that worked, exit the chroot and unmount and reboot:

```
exit
sudo umount /mnt/proc
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt
```Out of all this, it's actually the command about installing the kernel I'm not sure about. Try googling also if it gives you any ideas. The rest is surely working.

EDIT after yout EDIT2. Looks like the kernel files are there, not sure why aren't they showing up. Try the above commands without the apt-get install to see if recreating the grub files will do the trick.

---

### Post by jonnyboysmithy on 2011-11-17
Thank you very much for the help!
All the commands ran smoothly. 

I rebooted and grub tells me it cannot find "the" partition, something is probably still directing it to the deleted partition.
EDIT: it did fetch some archives and configure the kernel.

---

### Post by darkod on 2011-11-17
Grub on the MBR might still be looking for the old one. We should have run the command to reinstall on the MBR just in case. Do it again from live mode as before:

```

sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```

And after that (without rebooting), run the script again and post the link as you did previously. Lets look at it again after those commands.

---

### Post by westie457 on 2011-11-17
A bit late for you now as darkod has done all the hard work. Something for you to read just in case. [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by jonnyboysmithy on 2011-11-17
```
root@ubuntu:/# grub-install --root-directory=/mnt /dev/sda
/dev/sda8: Not found or not a block device.
root@ubuntu:/# grub-install --root-directory=/mnt /dev/sda1
/dev/sda8: Not found or not a block device.
root@ubuntu:/# grub-install --root-directory=/mnt /dev/sda
/dev/sda8: Not found or not a block device.
root@ubuntu:/# 

```dev/sda8? it doesn't exist. I think we've found the problem?
EDIT:btw I purged then installed and mkconfig and updated grub.

---

### Post by darkod on 2011-11-17
Hold on, are you trying this from the chroot or just from live mode? Because it makes a difference. And why it is asking for sda8, you did mount sda7 at /mnt right?

From live mode WITHOUT entering the chroot as previously just do in terminal:

```

sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Or from chroot it's enough only:

grub-install /dev/sda

because you are already inside the "root partition".

---

### Post by jonnyboysmithy on 2011-11-17
> **darkod said:**
> Hold on, are you trying this from the chroot or just from live mode? Because it makes a difference. And why it is asking for sda8, you did mount sda7 at /mnt right?

From live mode WITHOUT entering the chroot as previously just do in terminal:

```

sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```Or from chroot it's enough only:

grub-install /dev/sda

because you are already inside the "root partition".
yes I did that inside the chroot without the sudo.
As for the /dev/sda8 thats the partition I deleted.

this is the result
```
ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt
mount: /dev/sda7 already mounted or /mnt busy
mount: according to mtab, /dev/sda7 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# grub-install /dev/sda
/dev/sda8: Not found or not a block device.

``` Thats my question, why is it asking for /dev/sda8?

---

### Post by darkod on 2011-11-17
If you look into sda7 in /etc/fstab do you have an entry for example:
/dev/sda8 / ext4 .....

The only idea I have is if the entry in fstab is looking for /dev/sda8 specifically.

But if I understood correctly the partition you deleted was from another installation, 11.10, not this 11.04. So it shouldn't look for it.

Run the bootinfoscript again, it's best to see the new situation after all these changes.

---

### Post by jonnyboysmithy on 2011-11-17
[http://paste.ubuntu.com/741768/](http://paste.ubuntu.com/741768/)
EDIT: Shall I edit fstab?

---

### Post by darkod on 2011-11-17
It's looking for sda8 because 11.04 was on sda8 and now somehow is on sda7. It still has references to sda8 all over it.

I'm not sure why the update-grub command didn't adjust this.

You could try entering chroot again, but if you still haven't exited it I recommend shutting everything down and entering the chroot again. Then from inside the chroot run the update-grub.

Also, in sda7 you have /boot/grub/menu.lst which is not used since 9.10. I would delete that because it also exists /boot/grub/grub.cfg which should be used (even though right now it's not 100% correct). Why would the menu.lst be there, did you maybe upgrade version by version since 9.04? In that case the menu.lst might remain there.

Try entering the chroot again and running:

update-grub
grub-install /dev/sda

---

### Post by darkod on 2011-11-17
> **jonnyboysmithy said:**
> [http://paste.ubuntu.com/741768/](http://paste.ubuntu.com/741768/)
EDIT: Shall I edit fstab?

No, leave it alone for now. It does say that / was on /dev/sda8 when installed but the UUID is correct and is from /dev/sda7. No need for editing, it should work fine with the UUID.

---

### Post by jonnyboysmithy on 2011-11-17
No this was first installed from fresh with xp then 11.04 then 11.10 EDIT: (actually I'm not sure on the order)
Running in chroot after a reboot:
```
root@ubuntu:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.38-12-generic
Found kernel: /boot/vmlinuz-2.6.38-8-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```
EDIT2: I just ran this inside of chroot, no mention of /dev/sda8 ...interesting...
 ```
root@ubuntu:/# grub-install --root-directory=/mnt /dev/sda
The file /mnt/boot/grub/stage1 not read correctly.
```

---

### Post by darkod on 2011-11-17
You seem to have a mix of grub and grub2 but that's a smaller problem if we get this thing to boot correctly.

Does it boot now?

And how would grub1 get there, ubuntu last time used it in 9.04.

EDIT: I think you used that boot-repair cd and that might install grub1. This is exactly why I don't like "external" tools. They advertise them as easy fix, and if you don't know what they will do, they can get you into more trouble. Now that you have a mix of grub1 and grub2 it's a hell to get it out.

EDIT2: I'm trying to find some link in my bookmarks about removing grub1 in situations like this, but I can't. You have to depend on google or someone else jumping in.

---

### Post by darkod on 2011-11-17
OK, it's getting very late in my timezone. :)

But, if you feel like adventure, the only idea I have to resolve this mixup of grub1 and grub2 is to completely remove them both and install grub2.

You already know entering chroot but lets repeat it (DO THIS FROM FRESHLY BOOTED LIVE MODE, DO NOT HAVE ANYTHING MOUNTED):

```

sudo mount /dev/sda7 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
```

Lets remove grub1&2:

```
apt-get --purge remove grub grub-pc grub-common
```

Install grub2:

```
apt-get install grub-pc
```

Not sure if it's needed but lets run the mkconfig again:

```
grub-mkconfig
update-grub
grub-install /dev/sda
```

That should be it more or less. Exit the chroot and unmount everything, and reboot:

```
exit
sudo umount /mnt/proc
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt
```

---

### Post by westie457 on 2011-11-17
Is this of any help? [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by jonnyboysmithy on 2011-11-17
I'll try that :) thank you very much for the help and goodnight! EDIT: Goodnight to darkod that is.

---

### Post by jonnyboysmithy on 2011-11-17
> **westie457 said:**
> Is this of any help? [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
Yup, I'll keep that handy:)

---

### Post by jonnyboysmithy on 2011-11-17
Solved!!!!!:D:D:D):P

---

