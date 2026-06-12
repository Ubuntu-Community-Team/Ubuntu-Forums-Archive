---
title: "GRUB2 initiates but does not boot."
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sephoroth on 2009-10-16
Today for some reason my installation of GRUB2 randomly failed (after a Windows 7 crash).  As soon as the "GRUB Loading..." text appears the computer restarts.  Is there any way I could go about re-installing/repairing GRUB2 without a system-wide reformat?

Thanks in advance for any help.

---

### Post by mabovo on 2009-10-16
Have you tried "sudo update-grub2" ?

---

### Post by Sephoroth on 2009-10-16
> **mabovo said:**
> Have you tried "sudo update-grub2" ?

Would that work from a LiveCD or...?

---

### Post by kansasnoob on 2009-10-16
> **Sephoroth said:**
> Today for some reason my installation of GRUB2 randomly failed (after a Windows 7 crash).  As soon as the "GRUB Loading..." text appears the computer restarts.  Is there any way I could go about re-installing/repairing GRUB2 without a system-wide reformat?

Thanks in advance for any help.

It sounds like you can't even get into your *buntu so look here:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

In your case after mounting and chrooting try running "update-grub", no sudo needed while in a chroot.

---

### Post by kansasnoob on 2009-10-16
Do you know what partition to mount?

---

### Post by Sephoroth on 2009-10-16
EDIT:

Ignore what I typed earlier.  I'm an idiot ;).

After chroot'ing to the partition and running update-grub2 I get:

grub-probe: error: cannot find a device for /.

---

### Post by kansasnoob on 2009-10-16
> **Sephoroth said:**
> Sorry but I've never used chroot before (though I know what it does).  After mounting the partition to "/media/disk" and performing "sudo chroot /media/disk" (or any other directory for that matter), I keep getting:  "chroot: cannot run command `/bin/bash': No such file or directory"

Boot your live CD and from the "live" desktop go to terminal and post the output from terminal of:

```
sudo fdisk -l
```

---

### Post by Sephoroth on 2009-10-16
> **kansasnoob said:**
> Boot your live CD and from the "live" desktop go to terminal and post the output from terminal of:

```
sudo fdisk -l
```

I already realized what I did wrong.  Re-read my old post :D.

> **Sephoroth said:**
> EDIT:

Ignore what I typed earlier.  I'm an idiot ;).

After chroot'ing to the partition and running update-grub2 I get:

grub-probe: error: cannot find a device for /.

---

### Post by kansasnoob on 2009-10-16
> **Sephoroth said:**
> EDIT:

Ignore what I typed earlier.  I'm an idiot ;).

After chroot'ing to the partition and running update-grub2 I get:

grub-probe: error: cannot find a device for /.

I'll bet you were in the wrong partition, hopefully we didn't hose anything. What partition # did you use?

---

### Post by kansasnoob on 2009-10-16
We still need to see what your partition table looks like no matter what. The command 'fdisk -l' is the first step in that direction.

---

### Post by Sephoroth on 2009-10-16
I was originally (when I received the /bin/bash error) but I should now be chroot'ed into the correct partition (I only have 1 Linux partition excluding swap).  I am chroot'ed to /media/disk (corresponding to /dev/sda6) which I confirmed via Nautilus to be my Linux install.

EDIT:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      104391   de  Dell Utility
/dev/sda2            1972       35715   271043472    7  HPFS/NTFS
/dev/sda3   *       35715       48644   103856128    7  HPFS/NTFS
/dev/sda4           48645       60801    97651102+   5  Extended
/dev/sda5           60316       60801     3903763+  82  Linux swap / Solaris
/dev/sda6           48645       60315    93747244+  83  Linux

Partition table entries are not in disk order
```

---

### Post by kansasnoob on 2009-10-16
OK, while still chrooted into that partition run:

```
df -H
```

and:

```
grub-install -v
```

Just to gather info!

---

### Post by Sephoroth on 2009-10-16
```
root@ubuntu:/# df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda6               95G    47G    44G  52% /
none                    95G    47G    44G  52% /sys
udev                    95G    47G    44G  52% /dev
none                    95G    47G    44G  52% /dev/pts
none                    95G    47G    44G  52% /dev/shm
none                    95G    47G    44G  52% /var/run
none                    95G    47G    44G  52% /var/lock
none                    95G    47G    44G  52% /lib/init/rw
df: `/proc/sys/fs/binfmt_misc': No such file or directory
```

```
root@ubuntu:/# grub-install -v
grub-install (GNU GRUB 1.97~beta3)
```

Note that I am doing this from a Jaunty Jackelope LiveCD (which has GRUB2/grub-pc from Synaptic).

---

### Post by kansasnoob on 2009-10-16
That looks fine. What happens now if you run:

```
update-grub
```

---

### Post by Sephoroth on 2009-10-16
The same thing as earlier.

```
grub-probe: error: cannot find a device for /.
```

---

### Post by petteriIII on 2009-10-16
> **Sephoroth said:**
> The same thing as earlier.

```
grub-probe: error: cannot find a device for /.
```

I am sorry if I am jumping the gun. That error comes because the devices are different in your Karmic. Correct procedure would be:

sudo mount <Partition for Karmic, sda6 maybe> /mnt
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt
update-grub2

---

### Post by Sephoroth on 2009-10-16
> **petteriIII said:**
> I am sorry if I am jumping the gun. That error comes because the devices are different in your Karmic. Correct procedure would be:

sudo mount <Partition for Karmic, sda6 maybe> /mnt
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt
update-grub2

Thanks, you were right :D.

```
root@ubuntu:/# update-grub2
Generating grub.cfg ...
Found Debian background: Icebuntu_darkwood-Resized.tga
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found linux image: /boot/vmlinuz-2.6.31-13-generic
Found initrd image: /boot/initrd.img-2.6.31-13-generic
Found linux image: /boot/vmlinuz-2.6.31-12-generic
Found initrd image: /boot/initrd.img-2.6.31-12-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```


However, it seems like update-grub2 didn't work anyway.  The same problem still occurs.

EDIT:  Running "install-grub /dev/sda" and then running "update-grub2" solved the issue.  Thanks for all of your help everyone!

---

### Post by Sephoroth on 2009-10-17
Hmmm...the same problem happened again...right after a random Windows 7 crash and hard reboot.  The same fix worked again but I'm not sure why a Windows 7 crash on an NTFS partition should effect my ext4 partition (which it can't even read).

EDIT:  It may have had something to do with my system BIOS.  If any Studio XPS 13 users experience this, I suggest updating to A11.

---

