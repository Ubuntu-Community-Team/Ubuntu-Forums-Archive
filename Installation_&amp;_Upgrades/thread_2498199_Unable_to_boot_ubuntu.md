---
title: "Unable to boot ubuntu"
date: 2024-06-03
forum: Installation &amp; Upgrades
---

### Post by pedrokpaiva on 2024-06-03
Hi, I have a dual boot windows(nvme0n1p3)+ Ubuntu(nvme0n1p5) in my ssd. I was trying to increase my Ubuntu partition size (50Gb to 69Gb) using gparted in an usb stick. The process ran for about 5 hours then reported an error. When I exited, I noticed I was only able to access windows. I also noticed that the partition size for Ubuntu has increased to 69Gb, although I’m unable to access it. I was able to peak at the partition through grub and it seems like the directories are ok, but I’m unable to read from it. I’ll leave the pastebin from boot-recovery here for some info.
If anything else is needed, please let me know.
Thanks in advance,
Pedro

paste.ubuntu.com/p/grvKW3Jkhx/

---

### Post by currentshaft on 2024-06-03
I would boot to Ubuntu on a USB drive and attempt to mount and "fsck" the volumes in question, as well as check the grub configuration file.

---

### Post by Rubi1200 on 2024-06-04
I hope you have really good backups of your Ubuntu partition (and Windows).

It is **not **recommended to run fsck on mounted volumes or partitions as this could cause further data loss or other unforeseen issues.

If you had a standard Ubuntu install with an ext4 filesystem it is better to use e2fsck to check the volume:
```
sudo e2fsck -f -p /dev/nvme0n1p5

```

If there are errors, stop and report them here.

Make sure the volume is unmounted before you start. If you can "see" your files I would first try and save them to an external drive or USB before running the command above.

---

### Post by pedrokpaiva on 2024-06-04
Ok thanks, to check if my volume is unmounted I can run “lsblk -f” and check if the mountpoint column of the volume (and all its partitions) is empty, right? It seems to be already unmounted from the get-go.
And another question, does this have a risk of corrupting my windows partition? The contents of the windows partition are way more important than the ones on my inaccessible Ubuntu, so if there’s any risk to that I’d rather just deleting this Ubuntu partition and moving on.

---

### Post by Rubi1200 on 2024-06-04
Yes, make sure the Ubuntu partition is unmounted.

The e2fsck command above will only point at your Ubuntu partition, nothing else. It was written to only check ext filesystem types.

See here for more:
[https://linux.die.net/man/8/e2fsck](https://linux.die.net/man/8/e2fsck)

As I said, if it reports errors let us know what they are and maybe there is a chance to fix them.

If the check completes without any errors, then reboot and keep your fingers crossed it worked.

---

### Post by pedrokpaiva on 2024-06-04
I just ran it, here is the output it gave me:

Super block has an invalid journal (inode8).
Cleared.
*** journal has been deleted ***

Super block has_journal flag is clear, but a journal is present.
Cleared.
Journal inode is not in use, but contains data. Cleared.
Inode 262145 has the casefold flag set but is not a directory.

UNEXPECTED INCONSISTENCY; run fsck manually. (i.e., without -a or -p options)

---

### Post by Rubi1200 on 2024-06-04
Unfortunately, that does not look good.

I would give it one more shot and run without any parameters like this:
```
sudo e2fsck /dev/nvme0n1p5
```

Perhaps it will give you some kind of idea what is wrong by giving some other error information.

But based on the results and your previous pastebin report it does not look so good.

---

### Post by pedrokpaiva on 2024-06-04
Ok thanks for the help. I will just wipe it then. Deleting the Ubuntu partition through windows’ disk management is ok? Can I delete the swap partition as well?

---

### Post by Rubi1200 on 2024-06-04
Sorry to have been the bearer of bad news.

As to your question: I am consulting with another more experienced user called **oldfred** about that.

Please wait until one of us replies before doing anything.

---

### Post by pedrokpaiva on 2024-06-04
No problem. I appreciate the help!
Ok, I’ll wait for your reply before doing anything.

---

### Post by oldfred on 2024-06-04
Generally better to use Linux tools for Linux and Windows tools for Windows.
But you probably can delete partitions with Windows if you know how.

You say Windows data is critical, you then do have good backups of your Windows data, just in case.
Its a lot easier to restore a system than it is to attempt to recovery a broken system.

Bit concerned that gparted took so long. It only takes a long time if moving data. But expanding a partition into unallocated space is almost immediate.

I would make sure Windows is backed up and run Smart Status to see if drive has any issues. Windows does not always show issue until it totally crashes.

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
In Disks alias gnome-disks you can click on icon in upper right corner and see Smart Status
[https://www.smartmontools.org/wiki/Howto_ReadSmartctlReports_ATA_542.1](https://www.smartmontools.org/wiki/Howto_ReadSmartctlReports_ATA_542.1)
If not Ubuntu but other flavor, you can install it.
sudo apt-get update -y
sudo apt-get install -y gnome-disk-utility
Smart Data 
[https://ubuntuforums.org/showthread.php?t=2445397&p=13965854#post13965854](https://ubuntuforums.org/showthread.php?t=2445397&p=13965854#post13965854)
sudo apt-get install smartmontools

---

