---
title: "No Disk Space Error after 11.04 Live Installation on 8GB USB Stick"
date: 2011-09-01
forum: Installation &amp; Upgrades
---

### Post by chizeng on 2011-09-01
Hi all,

I had recently installed Ubuntu 11.04 on a USB stick (Pendrive) via Live. After installation, I ran a apt-get update and upgrade. I then tried to install vim, but an error in terminal noted that I had no disk space left. 

I took a look at Disk Analyzer, and it noted that I had just used 1.3GB out of 8GB. Thus, why am I getting this error of lacking disk space, and what can I do to fix it? I am unable to install anything.

Thanks a lot!

---

### Post by bryanl on 2011-09-01
use tune2fs to look at the reserved space. the default is 5% which'd be almost half a G on an 8 GB drive. check the man pages to see what it can tell you about how the partition is being used, too.

Also check for swap space - do you have a swap allocated? (if more than 2 GB of RAM you can probably get by without, maybe)

also note that installing things requires downloading the deb and unpacking and that can sometimes be a bit much with a squeeze on. I am using 8.5 GB for the root partition (including a 4 GB swap file) so it seems you should be able to install quite a bit of stuff.

---

### Post by varunendra on 2011-09-02
> **chizeng said:**
> Hi all,

I had recently installed Ubuntu 11.04 on a USB stick (Pendrive) via Live. After installation, I ran a apt-get update and upgrade. I then tried to install vim, but an error in terminal noted that I had no disk space left. 

I took a look at Disk Analyzer, and it noted that I had just used 1.3GB out of 8GB. Thus, why am I getting this error of lacking disk space, and what can I do to fix it? I am unable to install anything.

Thanks a lot!
Did you perform a normal installation (just like it goes on hard disk) or is it a 'persistent live' installation (a Live USB)?

If it is a live usb, the size of available disk space seen by the OS is equal to the size of "casper-rw" file on the USB drive. It's maximum size limit is 4GB (the limit of file size on a FAT partition). If you don't set it to the max. limit while creating the live usb, it gets set to 128 MB by default. This casper-rw file is actually the virtual file system in which your changes, installations etc. are stored, and is seen as the entire 'filesystem' itself when you are in the live session.

If it is a normal installation, I think we'll need more details about your setup, like partitions, their size, mount-points etc. whatever you can tell.

---

