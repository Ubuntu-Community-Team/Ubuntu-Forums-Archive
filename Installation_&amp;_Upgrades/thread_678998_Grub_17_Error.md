---
title: "Grub 17 Error"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by boyb on 2008-01-26
Hi,

I've looked on the forums, and there are a lot of posts on this error but I can't seem to find something to fix what I've done.

I've been running a dual boot with windows/ubuntu for a while now (~1 year), so I know a bit about ubuntu, but still, I'd appreciate it if the responses were pretty basic :)

Anyway, my ubuntu has been having problems for a while so I went to reinstall it,  I first copied all important information from ubuntu over to my windows partition and then tried to format and install the partition of ubuntu.  In the process I managed to create a third partition, for swap (512mb), which I don't remember ever doing before, but I read somewhere that you're supposed to to install.  Anyway, when it was installing there was a problem (which I forget now) and I restarted my computer and received the error "Grub 1.5 Error 17".  I cannot boot anything but the live ubuntu cd.  I do not have a floppy drive on my computer too (which I read may be necessary to reinstall grub).

I'm really worried because I didn't backup my windows information for a while and I have a ton of photo's, school projects, and various other important information on it.

Nonetheless, I'll tell you what I have done so far.

"sudo fdisk -l" yields:

[I]Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf3fbff7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8172    65641558+   7  HPFS/NTFS
/dev/sda2            8173        8234      498015    5  Extended
/dev/sda3            8235        9729    12008587+  83  Linux[/I]

The last time I used windows I simply put it into hibernate, so I cannot mount it.

"sudo ntfsfix /dev/sda1" yields:
[I]
Mounting volume... Error opening partition device: Permission denied.
Failed to startup volume: Permission denied.
FAILED
Attempting to correct errors... Error opening partition device: Permission denied.
FAILED
Failed to startup volume: Permission denied.
Volume is corrupt. You should run chkdsk.[/I]

Finally, under the grub menu, this is the result of looking for grub:

[I]grub> find /boot/grub/stage1

Error 15: File not found[/I]

If I really messed this up beyond repair then I'd like to at least be able to copy the windows partition to my external hard drive (which yes, I should have been backing up on anyway...).

I also have my original windows xp cd too if that helps.

Thanks in advance for all the help, I know you guys are usually really good, and I really need this fixed.

Cheers,
Boyd

---

### Post by Pumalite on 2008-01-26
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)
You can boot either OS or fix your Windows MBR with Super Grub: 
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by boyb on 2008-01-26
Thanks for the reply, but my computer BIOS does not recognized usb's, I don't have a floppy drive, and the cd rom drive I have the live cd running in.  Is there another way to reinstall this grub thing?

I read somewhere that putting in the windows disk may be able to repair the MBR, I will try that if I can find my windows cd.

In the meantime does it matter that the linux partition may be either empty or not complete?

I can't seem to reinstall ubuntu because it see's my HD as one without a partition, and I really can't afford to write over the windows partition.

Thanks,
Boyd

---

### Post by Pumalite on 2008-01-26
If you want to try to reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

