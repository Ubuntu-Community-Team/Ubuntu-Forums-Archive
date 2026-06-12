---
title: "Fresh Lucid install boots with flashing cursor"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by apropos on 2010-05-01
I have a machine with Windows 2003 server installed in a pair of mirrored SATA on Intel fakeraid.  Added a new drive and installed from Ubuntu 10.04 LTS AMD64 DVD into the new drive ended with a flashing cursor after POST.  I then tried installing from an Ubuntu 10.04 LTS i386 Desktop CD using ext3 instead of ext4 and ended up the same.

Fakeraid was on /dev/sda and /dev/sdb.  Ubuntu 10.04 was installed on /dev/sdc and boot loader installed in /dev/sda.  There were no grub menu after POST, just a flashing cursor at the lower left of the screen.  The Windows 2003 was just being used as file server, so I'm booted into live cd, mounted the fakeraid from /dev/mapper and shared folders from the mount.

What should I try now?

edit: resolved by installing grub into raid drive in /dev/mapper instead of /dev/sda

---

### Post by elnur on 2010-05-01
Got the same problem, but still can't find a solution after 5 hours of searching.

---

### Post by elnur on 2010-05-01
Anyone who has the same problem please leave a note here so that we and others know how many of us are affected by this problem.

---

### Post by Axellink on 2010-05-01
I'm having the same issue.  After a successful installation, i was able to configure everything.  Restarted the machine, chose the OS within GRUB, then the flashing cursor just appears on he top left hand corner.  

I am using the netbook remix on my Toshiba NB200 netbook.  Gonna wait a while to see if someone comes with a resolution.

---

### Post by elnur on 2010-05-01
> **Axellink said:**
> I'm having the same issue.  After a successful installation, i was able to configure everything.  Restarted the machine, chose the OS within GRUB, then the flashing cursor just appears on he top left hand corner.  

I am using the netbook remix on my Toshiba NB200 netbook.  Gonna wait a while to see if someone comes with a resolution.

Heh, one more Toshiba guy. Welcome to this thread: [http://ubuntuforums.org/showthread.php?t=1466337](http://ubuntuforums.org/showthread.php?t=1466337).

---

### Post by apropos on 2010-05-01
> **Axellink said:**
> I'm having the same issue.  After a successful installation, i was able to configure everything.  Restarted the machine, chose the OS within GRUB, then the flashing cursor just appears on he top left hand corner.  

I am using the netbook remix on my Toshiba NB200 netbook.  Gonna wait a while to see if someone comes with a resolution.

My problem was there's not even a grub menu to pick from.  After POST I see a menu for the raid config flash for less than a sec then just a flashing cursor on the lower left with no hard drive activity.  Live CD/DVD works fine so I'm thinking it's not a video problem like others have and have solved.

---

### Post by bnuytten on 2010-05-01
AFAIK, the flashing cursor upon boot signifies that grub is not installed on the master boot record of your hard drive. In my case, the alternate installer failed to install grub and I had to install it manually. To make matters more complicated, my root filesystem is a logical volume on the fakeraid device.

For you information, my fakeraid device identifies as /dev/mapper/nvidia_bddfahce and consists of the hard disks /dev/sda and /dev/sdb.

These are the steps I went trough:
[LIST=1]
[*]partitioning:
/dev/mapper/nvidia_bddfahce1 as /boot
/dev/mapper/nvidia_bddfahce6 as physical volume
volume group "vglinux" using only /dev/mapper/nvidia_bddfahce6
8G logical volume "lvlucid" inside the volume group "vglinux"
[*]further following the setup, including installing the base system
[*]installing the grub boot loader (one of the last steps) fails with the following error message: "Executing grub-install /dev/sda failed"
This fails because grub should be installed on the fakeraid device, not on one of the disks of the fakeraid device.
[LIST]
[*]I switched to a shell by pressing alt+F2 and install grub in the master boot record of my fakeraid device:
```
mount -t proc none /target/proc
sh -c "chroot /target /bin/bash"
grub-install /dev/mapper/nvidia_bddfahce
```
[*] Switch back to the installer (alt+F1) and choose "continue without installing boot loader".
[/LIST]
[*] reboot the machine and all I got on boot was the grub command line looking like this: "grub >" followed by a flashing cursor. So at this point, grub has been loaded from the master boot record but it doesn't know what to do.
[LIST]
[*]tell grub to load the linux kernel
```
linux /vmlinuz{press tab}
```
[*]tell grub where the initial ramdisk image is
```
initrd /initrd{press tab}
```
[*]boot the kernel and the initial ramdisk
```
boot
```
[/LIST]
[*]the kernel loaded but I was dropped to the initramfs shell.
[LIST]
[*]mount the root file system and /boot file system. Also include the special filesystems like proc and dev.
```
mkdir /target
mount /dev/mapper/vglinux-lvlucid /target
mount /dev/mapper/nvidia_bddfahce1 /target/boot
mount -t proc none /target/proc
mount --bind /dev /target/dev

```
[*]change root to /target and execute a shell in it
```
chroot /target /bin/bash
```
[*]write a new initial ramdisk to /boot/. I called it "test" in stead of initrd.img-2.6.32-21-generic.
```
mkinitramfs -r /dev/mapper/vglinux-lvlucid -o /boot/test
```
[*]press ctrl+alt+del to reboot the machine
[/LIST]
[*]you will again have to specify the commands in grub manually (similar to step 4). But in stead of using the intial ramdisk generated by the installer, use the "test" initial ramdisk.
[LIST]
[*]tell grub to load the linux kernel
```
linux /vmlinuz{press tab}
```
[*]tell grub where the initial ramdisk image is
```
initrd /test 
```
[*]boot the kernel and initial ramdisk
```
boot
```
[/LIST]
[/LIST]

You only have to do this last step when booting the next time. Setting it in the menu.lst file of grub will make the machine boot automatically. Still figuring out that one. Feel free to add comments and experiences.

---

### Post by bnuytten on 2010-05-01
When finally booted, I checked out the /etc/fstab file. It looked like this:
```
cat /etc/fstab 
# UNCONFIGURED FSTAB FOR BASE SYSTEM

```

So I added a line to mount the /boot filesystem.
```

/dev/mapper/nvidia_bddfahce1	/boot	ext2	defaults	0	0

```
And then mounted it:
```

sudo mount /boot

```

---

### Post by bnuytten on 2010-05-01
And this is what I did to tell grub to tell it to boot.
```

# install grub2
sudo aptitude install grub-pc
# check your version of grub: v1.98 is actually grub2
grub-install -v
# install and configure grub
sudo update-grub2
# remove the temporary initial ramdisk we create earlier
sudo rm /boot/test

```
More information on [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by apropos on 2010-05-01
[quote=bnuytten]mount -t proc none /target/proc
sh -c "chroot /target /bin/bash"
grub-install /dev/mapper/nvidia_bddfahce[/quote]

So the grub needs to be installed in the raid instead of /dev/sda?  I'll give that a try, thanks.

---

### Post by bnuytten on 2010-05-02
> **apropos said:**
> So the grub needs to be installed in the raid instead of /dev/sda?  I'll give that a try, thanks.

Correct. Good luck!

---

### Post by apropos on 2010-05-07
Problem fixed by installing grub2 into the raid drive on /dev/mapper/  There were some warnings for memory leaks but it's now able to boot into both Windows and Ubuntu.

---

