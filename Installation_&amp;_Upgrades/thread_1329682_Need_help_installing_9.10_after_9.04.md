---
title: "Need help installing 9.10 after 9.04"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by archp2009 on 2009-11-17
Hello,

I have had trouble not being able to get back into Ubuntu after attempting the automatic upgrade from inside 9.04.  I have decided to download and burn the 9.10 cd and to attempt a fresh install.  I have 8 operating systems on 5 drives so this is a bit complicated.  Parted Magic indicated my main Ubuntu folder is on sda6.  I also notice a swap on sda3 and an apparently unallocated partition sda5 and sda4 is indicated as an extended volume.  Grub indicates my Ubuntu is on (hd0,4). I presume that's the same as sda5? I tried to install using manual partitioning because after choosing sda6 for my home partition it came back indicating that it was going to format 4 different partitions including three swap parttions and a new partition sda7.  I decided to quit because I wasn't sure what all this meant.  Is there a simpler way to go about this, e.g. should I delete the existing ext3 partitions first? Would you please explain the SCSI numbering system which the manual partitioner uses to list the partitions prior to beginning the formatting process. I want to be sure I don,t erase other operating systems or data.   Thank you in advance for any comments or assistance.

---

### Post by Vermind on 2009-11-17
If you install Ubuntu via the Wubi windows installer for Ubuntu,
it will be much simpler, as you do not need a separate partition for Ubuntu. If You use windows on the same machine and don't mind the windows bootloader, you could do that.

If you wish to install into a separate partition, with manual partitioning, you should be able to see which partitions have what on them.
sda6 means the 6th partition of your first BIOS hard disk. While on the Ubuntu livecd, you should be able to browse all your partitions in the file manager, and find out which is which. You can mount things in the file manager by just clicking the partitions on your Desktop, in Places, or in a file manager window. The terminal command [FONT="Fixedsys"]mount[/FONT] gives you a list of what has been mounted and where. Its output looks like this:
```
/dev/sdb1 on /boot type ext2 (rw,relatime)
```
I hope this helps you identify which partition you want to use.

In manual partitioning, you need to at least choose a root partition. It will be formatted, and mounted (used) as "/". You should make sure that no format operations are done to other partitions. You can configure accessing windows partitions later, they need not be on the manual partitioning window. You only need a root and a swap partition.

---

### Post by archp2009 on 2009-11-17
Thank you for the reply.  I was impatient and decided to go ahead before receiving your reply and delete the old partitions, but the Ubuntu 9.10 did install ok.  I installed it directly from the 9.10 cd without bothering to ask the Ubuntu to load itself from the disk.   The only problem was that it identified my Mandriva it did not boot. Linux Mint and OpenSuse and both booted as did my 4 Windows installations. I guess 7 out of 8 is not bad. I don't know the simplest way to fix that 1 out of 8 (Mandriva) that is currently giving a file not found error.  I have the menu.lst on Mint that used to work that I could look at, but it's likely that the disk numbering sequence will be changed now because, for some reason unknown to me, Ubuntu automatically created two or three swap partitions instead of one.

---

### Post by archp2009 on 2009-11-18
I am bewildered with the new grub2 in Ubuntu 9.10 as discussed  at [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2) This is way over my head. What do I do in place of sudo gedit /boot/grub /menu.lst? Is it now impossible to fix boot entries created by Ubuntu 9.10 that aren't working? How can I simply comment out those lines that I don't want to see?  Will Ubuntu 9.10 be correctly listed among my other operating systems if I simply reinstall Linux Mint?

---

### Post by audiomick on 2009-11-18
It is possible to edit the grub 2 files, although I don't know how.
There has been a lot of traffic on this forum, and in general help, on this subject. If you do a bit of looking, you should be able to find what you are after.

---

### Post by archp2009 on 2009-11-19
The best I could find was [http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)
This makes it clear that navigating grub2 is a maze.  I used sudo gedit /etc/grub.d/40_custom to attempt to add lines to grub.  None of the lines was considered valid, however, and all it did was add a few minutes of error messages  before my bootloader would load.  I think (hope) I have it back to the way it was now.  If not, I'm going to go back and reinstall 9.04 and/or Mint (Gloria)  before this distro really gets me in a mess.

---

### Post by archp2009 on 2009-11-21
I am back to 9.04.  I did a fair amount of reading on Grub2 before downgrading but was unable to use the 40_custom file in the way it was explained.  As long as Grub2 remains the way it is, I will not be upgrading any of my Linux distros to include Grub2.

---

