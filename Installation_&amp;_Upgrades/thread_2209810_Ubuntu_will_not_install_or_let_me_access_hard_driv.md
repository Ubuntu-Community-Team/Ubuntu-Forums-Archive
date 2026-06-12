---
title: "Ubuntu will not install or let me access hard drive at all"
date: 2014-03-07
forum: Installation &amp; Upgrades
---

### Post by wolf4 on 2014-03-07
So when I boot Ubuntu from my live USB and try to install it on my Windows 8 desktop, it doesn't work. I get to the part where the installer is *supposed* to say that Windows 8 is installed and give me a list of options on whether or not I want to dual boot or get rid of it entirely. Instead, after a long time waiting for it to load, it takes me straight to the screen where you choose a partition, except there isn't anything there in the table, it's just blank. At this point, if I click any buttons, the installer either freezes or crashes out.

So then I went to the "try Ubuntu first" option, went to the files tab, and tried to access the "892 GB Volume", which is where Windows 8 is, as well as where I want to put Ubuntu (I have already shrunk the Windows partition to have 100 GB of unallocated space for Ubuntu).

This is the error it gave it gave me upon attempted access:

**Unable to access "892 GB Volume"**

```
Error mounting /dev/sdb2 at /media/ubuntu/3A58AE4C58AE06AB: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,dmask=0077,fmask=0177" "/dev/sdb2" "/media/ubuntu/3A58AE4C58AE06AB"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sdb2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
```

At this point, I'd like to make clear that I have disabled fast startup, as well as secure boot. I even tried shutting down in Windows by typing "shutdown /s /t 0" in the Command Prompt. No dice.

Can anyone please help me figure out how to get Windows to just shut down and not interfere?

---

### Post by ubfan1 on 2014-03-07
Windows sometimes uses something called "Dynamic Partitions" which have to be turned off.  Also, raid should not be used.  I'd leave secure boot on until you run into a problem.  Sometimes turning it off puts you into non-UEFI mode on some machines.  If you get to the black grub menu screen (not purple), then you have securely booted, and will avoid many issues if you just proceed from there.

---

### Post by wolf4 on 2014-03-07
My partitions are not dynamic, I just checked. But I do have an SSD and 1 TB drive in RAID 0 so that may be a problem. I'd really like to keep the data, though, so is there any way around this, or at least a way to keep the data?

Also, I do boot to the black GRUB menu, even with secure boot off (which will not turn back on for some reason, but I don't think it'll be an issue).

---

### Post by Mark Phelps on 2014-03-07
Windows 8 uses a new form of hibernation by default, such that when you think you have shut it down, instead, it's hibernating -- and keeping the partitions mounted.  This prevents you from mounting them when in Ubuntu.  You have to disable Fast Startup in Windows 8.

Also, you can not install inside Windows8 as Wubi support has been dropped.

I don't know if you can install with RAID present.

---

