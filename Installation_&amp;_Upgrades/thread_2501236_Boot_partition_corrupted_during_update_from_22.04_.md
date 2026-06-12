---
title: "Boot partition corrupted during update from 22.04 to 24.04."
date: 2024-09-28
forum: Installation &amp; Upgrades
---

### Post by chribonn on 2024-09-28
I have Plex media server running on an hp laptop running Ubuntu server. Today I logged in using putty and discovered there was a version upgrade. 

The command which I do not recall had do-something-something.  Long story short is that I had to leave and when I returned the putty session had terminated and I could not reconnect. 

On the laptop itself I had a white screen indicating that something went wrong (white screen of death?) and the machine will not boot. 

Is there a way I could recover? 
Thanks

---

### Post by TheFu on 2024-09-28
Did you make a backup of the system before you started?  
Here's a reasonable guide for how-to, [https://www.cyberciti.biz/faq/how-to-upgrade-from-ubuntu-22-04-lts-to-ubuntu-24-04-lts/](https://www.cyberciti.biz/faq/how-to-upgrade-from-ubuntu-22-04-lts-to-ubuntu-24-04-lts/)

However, I think they left out verifying that you have sufficient free storage available, especially in /boot/ if /boot is a separate partition.  Running out of space where new kernels get placed, which is in /boot/, is difficult to recover from, so it is best to avoid it by ensuring there's about 300MB free there.  300MB should be more than enough.

If you don't have enough space in /boot/, keep reading. Otherwise, everything below here won't help you.

For example, my /boot/ contains these files today:
```
$ ls -F /boot/
config-5.15.0-121-generic  initrd.img-5.15.0-121-generic  System.map-[COLOR="#FF0000"]5.15.0-56[/COLOR]-generic
config-5.15.0-122-generic  initrd.img-5.15.0-122-generic  vmlinuz@
config-[COLOR="#FF0000"]5.15.0-56[/COLOR]-generic   initrd.img-[COLOR="#FF0000"]5.15.0-56[/COLOR]-generic   vmlinuz-5.15.0-121-generic
efi/                       initrd.img.old@                vmlinuz-5.15.0-122-generic
grub/                      System.map-5.15.0-121-generic  vmlinuz-[COLOR="#FF0000"]5.15.0-56[/COLOR]-generic
initrd.img@                System.map-5.15.0-122-generic  vmlinuz.old@
```
If you look closely, you'll see there are 3 kernels, each a different version, there.  Only 2 really are needed - the last one installed and the one that worked before it.

To see the space used in the /boot/ partition (or ZFS pool, called bpool, OR LVM LV /boot/), use
```
$ df -Th /boot/
Filesystem               Type  Size  Used Avail Use% Mounted on
bpool/BOOT/ubuntu_d0wbmk zfs   1.8G  [COLOR="#FF0000"]385M[/COLOR]  1.4G  22% /boot
```
So, with ZFS, looks like the installation created the bpool to be 1.8GB in size, but only 385MB is used for those 3 kernels.  I should clean up one of the kernels, do that referencing my files above, we can see that kernel 5.15.0-56 needs to go.
The kernel files themselves are:
```
$ ll vmlinuz-5.15.0-*
-rw------- 1 root root 11699080 Aug  9 04:16 vmlinuz-5.15.0-121-generic
-rw------- 1 root root 11700328 Aug 29 08:47 vmlinuz-5.15.0-122-generic
-rw-r--r-- 1 root root 11551392 Dec 17  2022 vmlinuz-[COLOR="#FF0000"]5.15.0-56[/COLOR]-generic
```

```
$ sudo apt remove --purge linux-image-[COLOR="#FF0000"]5.15.0-56[/COLOR]-generic
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  linux-image-5.15.0-56-generic* linux-modules-5.15.0-56-generic*
  linux-modules-extra-5.15.0-56-generic*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 482 MB disk space will be freed.
Do you want to continue? [Y/n] y
....
Purging configuration files for linux-modules-extra-5.15.0-56-generic (5.15.0-56.62) ...
Purging configuration files for linux-modules-5.15.0-56-generic (5.15.0-56.62) ...
Purging configuration files for linux-image-5.15.0-56-generic (5.15.0-56.62) ...
rmdir: failed to remove '/lib/modules/5.15.0-56-generic': Directory not empty

```
So, the linux-image-5.15.0-56-generic is gone as is the vmlinux.... version for it.  Trust me.

Cleaning up the modules that are specific to the kernel failed.  Let's see of **apt autoremove** will address that.  Nope, it failed.  While I'm here, I also see that the linux-headers-5.15.0-56 linux-headers-5.15.0-56-generic packages need to be removed. They aren't useful without the kernel anyways.  
```
sudo apt purge linux-headers-5.15.0-56 linux-headers-5.15.0-56-generic
```
Removed them.
```
$ df -Th  /boot/
Filesystem               Type  Size  Used Avail Use% Mounted on
bpool/BOOT/ubuntu_d0wbmk zfs   1.8G  [COLOR="#FF0000"]257M[/COLOR]  1.5G  15% /boot
```
That's a little better.

It is possible that other file systems are full too.  I think for an upgrade, having 5GB free for / is a reasonable amount for a server.  It is probably less, but better safe, right?

The bad things about backups is that we only know we need them AFTER there's a problem. OS upgrades are one of those high-risk tasks. Basically, an OS upgrade is like replacing the engine in your car. If something doesn't fit, that car won't start or move.  Think of backups like having a tow truck available, standing by, just in case it is needed.

---

### Post by chribonn on 2024-09-29
I have a backup and this was a single purpose machine so I am not that bothered.  I had done a YouTube series on how to setup PMS on ubuntu server so the notes exists if I need to start from scratch :razz:.

My question is whether there is a utility I can use to attempt recovery before heading for the restore route.

---

### Post by chribonn on 2024-09-29
I downloaded the Boot-Repair utility and would like to share with the community maybe it can help others.  The utility uploaded what it discovered/did to : [https://paste.ubuntu.com/p/Vyb8cBK6N2/](https://paste.ubuntu.com/p/Vyb8cBK6N2/). After I booted this is the message I got:

[IMG]https://imgur.com/a/wNtrUGC[/IMG][IMG]https://i.imgur.com/DC9wnbF.jpeg[/IMG]

I think the restore route is the most efficient in my case.

---

### Post by TheFu on 2024-09-29
If it were me, looking at a file system/disk issue, I'd boot from an Ubuntu ISO with a GUI, the go into _Try Ubuntu_ mode and run an fsck on all file system on all storage.  

If that didn't work, other errors would certainly be shown that could be followed.  Most likely the storage device is failing, so I'd use **smartctl** to run a "short" SMART test if the storage were SATA connected.  For NVMe connected storage, I'd use the **nvme** command to see the storage problems.  Both of those tools would likely need to be installed into the "Try Ubuntu" environment.

If SMART data from the storage device(s) show issues, you'll want to look up any non-zero "raw values" on the internet for the true meaning, then I'd decide if the storage is dead or dying.

Only after seeing a clean SMART report would a bother restoring from backups.  If the disk/storage is dying, it doesn't make sense to restore until that has been swapped out.

BTW, I can't see the paste. Sorry. I'm going by the kernel panic image only and that sda2 can't be mounted.  If you wanted to try and mount the correct root= manually, you'll need to know the device.  Lots more information is needed to know what what is. It is probably inside the pastebin that I can't see, so wait for someone else to respond.

---

### Post by oldfred on 2024-09-29
You can ignore the Boot-Repair issue on line 51 on efi variables cannot be set.
We are seeing more of this, not sure yet why.
But you have a valid UEFI boot entry that boots to valid grub.cfg in ESP, so you should be past grub or grub is not an issue.

Or running e2fsck on all ext4 partitions and review of smartdata as suggested by TheFu.

You show many mounts using cifs
//192.168.16.253/Movies	/mnt/pms-movies	cifs	credentials=/etc/win-credentials2,,uid=1000,gid=1000

I see two ,, after credentials2 on most and one comma on one entry. 

TheFu or others may have suggestions on network mount parameters as they know them better.

---

### Post by chribonn on 2024-09-29
Sorry I decided to go with the backup.  I'm back up.  What I can report is that I did all the updates and this time round it worked perfectly.

The only different thing I did  is that the first time round I did the updates through putty from a remote connection. This time round the updates were done from the console.

More than happy to try anything out if it can help others.

---

