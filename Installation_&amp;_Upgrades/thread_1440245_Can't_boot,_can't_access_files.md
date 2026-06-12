---
title: "Can't boot, can't access files"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by Digital Ninja on 2010-03-27
Power in my house went down while I was working on my computer and now I cannot boot anymore. It comes to a screen where it says
```
error: unknown filesystem
grub rescue >
```
I found some articles saying I should boot to live Ubuntu and mount my disk from there. It doesn't work because it says: 
```
mount: wrong fs type, bad option, bad superblock on /dev/sda1(...)
```
So I found two more articles offering to fix that, one is installing smbfs through apt-get, another one is installing nfs-common through aptitude, both of which failed to help my case.

All of the articles I found were meant to help people who dual boot with XP which is not my case. I only use Ubuntu so I'm starting to think there's a whole different solution for my case. What are the chances that my hard drive is damaged and how can I check that? 

To conclude my question, I want to point out that fixing my installation is not neccessary. I was going to install 10.4 BETA anyway. I just want a way to get to my files cause I didn't get the chance to backup some of my work before this happened.

Thanks.

---

### Post by mikewhatever on 2010-03-27
Try running a file system check from the live cd.

sudo fsck -y /dev/sda1

Once done, you should be able to both mount the file system and boot the existing installation.

---

### Post by Digital Ninja on 2010-03-27
> **mikewhatever said:**
> Try running a file system check from the live cd.

sudo fsck -y /dev/sda1

Once done, you should be able to both mount the file system and boot the existing installation.

That was the weirdest thing I have ever seen Ubuntu do, but it didn't work..

First he outputted like hundrets of seemingly random 6-digit numbers, then he said he found inodes with multiply-claimed blocks, then he tried to "clone" them (wtf) and then he started outputting a bunch of "y"'s for like 2-3 minutes until i finally stopped him and restarted. Upon booting to live cd again, I entered the same command once more and he reported everything was fine, so I restarted to my real installation and got to the same grub error message, as if he never did nothing... 

Any other ideas? :(

---

### Post by mr clark25 on 2010-03-27
I found some articles saying I should boot to live Ubuntu and mount my disk from there. It doesn't work because it says: 
```
mount: wrong fs type, bad option, bad superblock on /dev/sda1(...)
```i would run the "check disk for errors". looks like the disk is bad.

once you get into the live environment, you should be able to remove grub and then reinstall it. judging from your last post, it looks like you can boot from a live usb/cd.

let us know if you get into the live environment. that's the first step.

the next step: removing/reinstalling grub (if you can boot from the live cd)

try this:
replace "sda6" with your linux partition.
```

sudo bash
mkdir -p /mnt/temp/boot
mount /dev/sda6 /mnt/temp/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
grub-install --recheck /dev/sda
update-grub

```
you may need to remove the "--recheck" in the second to last command.

you may need to remove the old brug first, but im not sure.

---

### Post by RJARRRPCGP on 2010-03-27
Looks like the file system used was probably ext2. 

A journaling file system rarely has corruption like that.

---

### Post by Digital Ninja on 2010-03-27
> **mr clark25 said:**
> ...
Booting to Ubuntu live works well from CD.

I can't get the mount command to work cause he says that he "can't find /dev/sda2 in /etc/fstab or /etc/mtab", the same thing goes for sda1 or sda3 or sda*n*.. When I go to /dev in Nautilus, there are sda, sda1, sda2 and sda5 files, all of which, including all of the other files in /dev, are 0 bytes large. Files in /bin, on the other hand, "seem" to be ok. Does that mean what I think it means? :( 


> **RJARRRPCGP said:**
> Looks like the file system used was probably ext2. 

A journaling file system rarely has corruption like that.
That's next to impossible. I'm no advanced user so I always leave everything to default, and, if I'm not mistaken, 9.04's default filesystem is ext4, isn't it?

---

