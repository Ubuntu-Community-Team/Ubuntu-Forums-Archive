---
title: "Same swap partition for XP and Breezy"
date: 2005-10-17
forum: Installation &amp; Upgrades
---

### Post by Nightfall on 2005-10-17
Hello,
can I have the same swap partition shared between Windows XP and ubuntu breezy? how can I do this?

Thanx

---

### Post by rmjokers on 2005-10-17
That would not be possible.  The swap partition used by linux has to be a special type (0x82).  Meanwhile, the swap file used by windows has to be on an NTFS / FAT filesystem in an NTFS/FAT partition.  The format of the data stored in these files is totally different.

---

### Post by Adapted.Cat on 2005-10-17
The answer is yes :D

I actually did this many years ago with another distribution, and I tried a few of the steps tonight without any problem, so there's no reason why it won't work. However, you won't be able to do this in a plug-n-play manner - you have to go in and tweak things afterwards.

I should warn you that I haven't done this whole process from start to finish on Ubuntu, as it's getting late here, so please check that things work before you reboot.

First of all, when you install Ubuntu, choose no swap partition (if you think you have enough memory) or make a small swap partition that you can later delete. I have 1Gb ram, and had no problems installing Ubuntu without a swap partition, but 256Mb or even 128Mb should be enough. Ubuntu is one of the few distros that doesn't have a major hissy fit when you elect to do this, so we're already off to a good start.

So, after the install, the basic idea is as follows:

1) Find the partition that your swap file(s) is(/are) mounted on:
[INDENT]Go to the properties of "My Computer", hit the Advanced tab, Performance Options, Advanced, and then the Change button for Virtual Memory.

Select each drive in turn and see what it's set to. If you're going to try this, I'd recommend setting a custom size (rather than system managed size) where the "initial" and "maximum" are the same - this ensures a consistent swap size all the time.

Reboot if you've made changes.
[/INDENT]

2) The file you're looking for will be a hidden system file in the root of that drive called pagefile.sys

3) Boot into linux, and find that partition - make sure it's automounted at boot, and mounted read/write. If it's an NTFS partition, I don't know whether the fs support in linux is reliable enough for you (opinions anyone?). If it's a FAT32 partition, you should have no problem.

4) To initialize a swap file/partition, you run mkswap on it. This needs to be done every time you boot into linux, as you may have blasted it away by running windows. Fortunately the process is quick enough to do at boot (mainly adding the "SWAPSPACE2" signature at the front).
[INDENT]Go into /etc/init.d and grep for "swapon" - you should find "swapon -a" in mountall.sh - change it to something like this: ```
for swap in $(awk '{if ($3 == "swap") print $1}' /etc/fstab)
do
  if [ -f "${swap}" ]
  then
    mkswap "${swap}"
  fi
  swapon "${swap}"
done
```
This takes every swap file/partition in /etc/fstab, and if it's a file runs mkswap on it. Then it mounts them as swap.

There's another "swapon -a" in checkroot.sh, but that's run before filesystems are mounted (to allow fsck to run with lots of memory) so I think we just have to allow that one to fail.

To go with that, you'll need a line in /etc/fstab to register your swap file, like this:
<mountpath>/pagefile.sys none swap sw 0 2
[/INDENT]

5) Once you have this working, and you've been able to boot into both OSs without problem, you can remove your old swap partition if you made one.

Sound complicated? It is, but once it's done it should work pretty reliably. 

I have tried the "mkswap pagefile.sys" on Windows 95 and XP SP2, and it doesn't complain at all. Windows crashes often enough that it has to be used to a broken swap file.

However, this is something you're going to put into the boot sequence, so please make sure you test it thoroughly before you reboot. Particularly that code sequence for the mkswap. The same sequence can be entered interactively in your root shell, to test it. Run "swapon -s" afterwards to verify that it worked. Ubuntu doesn't have a root user, so you'll have to "sudo bash" to get a root shell to make the configuration changes and test it.

Really, the worst that will happen if it fails is that you won't have any swap. You should still get a login prompt when you boot up (if not, try the failsafe mode) so you can fix things. If this fails, what has probably happened is that your "mkswap" and "swapon" is executing before the relevant filesystem has been mounted. Just move it to lower down in the mountall.sh script if this happens.

Good luck!

---

### Post by DutchR_PW on 2005-10-19
Just make sure that you don't mkswapfs the whole windows partition! It might be safer to make a 1GB FAT32 partition with pagefile.sys on it. This way you can still have WinXP on a NTFS partition. I'm not sure about NTFS support either, but I have heard of a program that wraps around the ReactOS NTFS driver and gives full read/write possibilities. The standard NTFS driver can overwrite files, but not change the size, so it *should* be enough to 'format' the swapfile.

---

