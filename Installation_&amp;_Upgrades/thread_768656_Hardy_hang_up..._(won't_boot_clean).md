---
title: "Hardy hang up... (won't boot clean)"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Nathan Otis on 2008-04-26
It looks like after a couple flawless upgrades with Ubuntu, my luck has run out. I updated yesterday and now my system hangs on startup. The boot errors out and all I can see on the screen at this point says:

fsck 1.40.8 (13-Mar-2008 )
fsck.ext3:No such file or directory while trying to open /dev/hdb1
dev/hdb1:
The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem, (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock: e2fsck -b 8193 <device>

fsck died with exit status 8

*File system check faild
A log is being saved in /var/log/fsck/checkfs if that location is writable.
*A maintenance shell will now be started.
CONTROL-D will terminate this shell and resume boot
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found.
root@otis-desktop:~#

I press Control D and it does start up, but what is this error? It seems I need to run file system check on ext2, but I'm at a loss as to how.

Thanks in advance for any assistance,
n.

---

### Post by mymiasma on 2008-04-27
I had the same problem. After trying a Knoppix rescue disk I found there was no apparent problem with my drive. I finally worked around the problem by restoring fstab from an earlier backed up version. The problem is that now the os seems to think that all my drives are scsi and mounts them from /dev/sdaX rather than /dev/hdaX. Everything seems to work but I'd rather get them back to normal to make sure it doesn't break things. I know it doesn't make much sense that fstab could cause the system to think there is a bad superblock, but it worked for me.

One more note, I seem to be forced to use UUID numbers in fstab rather than /dev/hdaX. If anyone can deduce the root cause from this I'd sure like to hear about it.

MyMiasma

---

