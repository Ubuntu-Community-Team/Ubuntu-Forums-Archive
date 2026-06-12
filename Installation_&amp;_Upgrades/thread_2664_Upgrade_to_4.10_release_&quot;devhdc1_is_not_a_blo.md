---
title: "Upgrade to 4.10 release: &quot;/dev/hdc1 is not a block device&quot;"
date: 2004-10-30
forum: Installation &amp; Upgrades
---

### Post by oik on 2004-10-30
I am trying to upgrade to the 4.10 release. I have used apt-get to get the ubuntu and ubuntu-desktop packages - that's fine.

When I apt-get install linux-686, it tells me that /dev/hdc1 is not a block device, which is a lie. (Ubuntu is installed on /dev/hdc1).

Can someone give me an idea of where I should start looking?

Cheers, Oik.
------------------


root@cat ~ # apt-get install linux-686
Reading Package Lists... Done
Building Dependency Tree... Done
linux-686 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
7 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up linux-image-2.6.8.1-3-686 (2.6.8.1-16) ...
/usr/sbin/mkinitrd: device /dev/hdc1 is not a block device
Failed to create initrd image.
dpkg: error processing linux-image-2.6.8.1-3-686 (--configure):
 subprocess post-installation script returned error exit status 2
...

---

### Post by butters on 2004-10-30
Is /dev/hdc1 mounted?  i.e. is this a separate /boot partition?

---

### Post by oik on 2004-10-30
Hmmm,

It seems the problem is with the linux-image package (whatever that is); apt-get upgrade won't work at all now (see below). I deleted linux-image* from /var/cache/apt in the vain hope that it might fix the problem, but it didn't.

/dev/hdc1 is the root partition, by the way.

Oik.

root@cat /var/cache/apt/archives # apt-get upgrade
Reading Package Lists... Done
Building Dependency Tree... Done
The following packages have been kept back:
  mplayer-586
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
7 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up linux-image-2.6.8.1-3-686 (2.6.8.1-16) ...
/usr/sbin/mkinitrd: device /dev/hdc1 is not a block device
Failed to create initrd image.
dpkg: error processing linux-image-2.6.8.1-3-686 (--configure):
...

---

### Post by oik on 2004-10-30
OK, more info... it's something to do with udev, I think.

The root partition is on the secondary master IDE channel, i.e. /dev/hdc1.

[FONT=Courier New]root@cat /usr/bin # df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hdc1            157076776  28844540 120253156  20% /
tmpfs                   160460         0    160460   0% /dev/shm
root@cat /usr/bin #[/FONT]

BUT... /dev/hdc1 no longer exists.... /dev/hdc has been replaced by /dev/hda!!!!! Is this udev's doing? Note there is only one hard disk in the machine.

[FONT=Courier New]root@cat /usr/bin # ls -l /dev/hdc*
ls: /dev/hdc*: No such file or directory
root@cat /usr/bin # ls -l /dev/hda*
brw-rw----    1 root     disk       3,   0 2004-10-30 09:28 /dev/hda
brw-rw----    1 root     disk       3,   1 2004-10-30 09:28 /dev/hda1
brw-rw----    1 root     disk       3,   2 2004-10-30 09:28 /dev/hda2
brw-rw----    1 root     disk       3,   5 2004-10-30 09:28 /dev/hda5
root@cat /usr/bin #[/FONT]

Now I am totally out of my depth!

Oik.

---

### Post by rebroad on 2005-03-23
I'm trying to upgrade my linux image, and I'm getting:

Setting up linux-image-2.6.10-5-686 (2.6.10-29) ...
/usr/sbin/mkinitrd: device /dev/hda3 is not a block device
Failed to create initrd image.
dpkg: error processing linux-image-2.6.10-5-686 (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.10-5-686
E: Sub-process /usr/bin/dpkg returned an error code (1)

I suspect the reason is that my root partition was hda3 when I installed ubuntu, but since then I rearranged my partitions, rewrote the MBR and updated grub's menu.lst, but obviously a reference to "hda3" still exists somewhere. My root partition is now a logical partition, /dev/hda7, (it was a primary parition /dev/hda3).

I've done a "find / -print | xargs grep -c hda3" type of thing to try to find any files containing the phrase hda3, but found none!

Anyone know how I can inform ubuntu to use /dev/hda7 instead of /dev/hda3 for the kernel upgrade please?

If I don't find a solution soon, I'm going to have to convert my ext3 partition back to a primary partition again - which will change it back to hda3, but I'd rather not do that as that will cause other issues!

Thanks to anyone who can help.

Ed

---

### Post by rebroad on 2005-03-23
Ah. found it. I needed to edit /etc/fstab

Even though my system was booting fine with fstab being wrong, it's obviously used by the scripts that upgrade the kernel. 

Maybe it would be better if these scripts found the name of the device for the root partition from elsewhere (not sure where) - and then even offered to update my /etc/fstab with the correct info for me!

Anyway, the apt-get upgrade seems to have worked now. I'm off to reboot!

---

