---
title: "Clean install does not like my partitioning?"
date: 2006-08-06
forum: Installation &amp; Upgrades
---

### Post by B()X_BREAKER on 2006-08-06
No dual boot, only ext3 /boot /var /home /swap all primary partitions on primary master ide with /boot set to active. Two other reiserfs drives on secondary ide untouched during install. After installing Kubuntu several times without any issues I reboot to get this ...

root (hd0,0)
 filesystem type is reiserfs, partition type 0x83
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro splash
Error 15: File not found

 I dont know why it is showing reiserfs or why it cant find what it is looking for. I checked, and everything is where it should be. Do I need to add a /boot partition or change some of these to extended? Someone said it is a grub problem, but I dont think so.
 After fighting for 2 days I need some help. I am doing this to learn more about linux partitions so using auto partition is out of the question.

---

### Post by Herman on 2006-08-06
Hello, B()X_BREAKER,
> No dual boot, only ext3 /boot /var /home /swap all primary partitions > Do I need to add a /boot partition or change some of these to extended?  Hmmm, can you post the output of the following command here please? ```
sudo fdisk -lu
``` You shouldn't really bother with all those seperate partitions unless you have some special reasons for needing them. One single '/' (root) partition and a swap area should be fine for just about anyone. It makes for a much tidier install and it's simpler and easier to manage. Seperate partitions used to be needed for the old 8.0 GB hard drive size limit, or for before journalling filesystems and UPSes where invented, or for sharing a big old mainframe server with a few hundred users in a university or something. :D (just being helpful, do as you like). :D Even seperate /home partitions are obsolete now that we have GParted LiveCD and can make a complete operating system and software backup copy of the whole partition that only takes up about 2.5 GB of hard drive space and can be updated or re-installed in ten minutes.

In your GRUB entries, you would need to put the partition number where the Linux kernel lives (your /boot partition) after the 'root' command.
For example,```
root (hd0,[COLOR=Red]x[/COLOR])
``` Where '[COLOR=Red]x[/COLOR]' is the partition number for your partition where the Linux kernel is.

Then, after the kernel command, you need to put in the name of the the 'root' partition containing /sbin/init.
For example.```
kernel /vmlinuz root=/dev/hda[COLOR=RoyalBlue]y[/COLOR]
``` Where '[COLOR=RoyalBlue]y[/COLOR]' is the number of the root partition.

Are you trying to boot from grub's [Command Line Interface ?]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")
If not, you should try it.  You should be able to use Grub's Command Line interface to find everything and solve any booting problems if the operating system is bootable.

All the best, Regards, Herman :D

---

### Post by B()X_BREAKER on 2006-08-06
Ok, I made a mistake. The first partition is /root (not /boot) so do I need a /boot partition to make it work?  As far as I know root (hd0,0) and root=/dev/hda1 are both right. Here is the fdisk -lu without the other disks in the system, just the os drive.

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63     8209214     4104576   83  Linux
/dev/hda2         8209215    12225464     2008125   83  Linux
/dev/hda3        12225465    38025854    12900195   83  Linux
/dev/hda4        38025855    39102209      538177+  82  Linux swap / Solaris

So in general my combination of /root /var /home /swap doesnt work. What is a working combination? Should I change /root to /boot or is there another problem elswhere?

---

### Post by Herman on 2006-08-06
B()X_BREAKER, Alright, I'm glad we got that cleared up. 

You don't need a seperate /boot partition unless you decide to use a special filesystem for root that Grub doesn't like being installed on.

Probably you have either a partition table problem or a minor Grub hiccup and that's why it isn't booting.

You could try booting from Grub's Command Line and see if you can get it to boot that way, For how to do that, [Click Here]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").

If you can't even boot from Grub's command line then it's probably unbootable and the best thing to do would be just to wipe that install and try again. (I presume you have no data in it yet anyway).

Try to stick to 'Parted based partitioners and aviod mixing different brands of partitioners.  They may be similar, but they may not exactly follow the same rules, so a fault left by a previous partitioner can trip the current partitioner up. At least that's how it seems to me. Ubuntu is compatible with 'Parted based partitioners.

I hope that helps, Regards, Herman :D

EDIT, I forgot to say that that combination of partitions should work okay, and also, thanks for posting your fdisk output, I analysed it, and that looks fine to me too.

---

### Post by B()X_BREAKER on 2006-08-06
Thank you! The link you provided helped me find and fix the problem, I am saving that page for later reference. For some reason find vmlinuz returned (hd2,0) :-k  instead of(hd0,0) but I fixed that thaks to you.:-D

---

### Post by Herman on 2006-08-07
B()X_BREAKER =D> Great work, congratulations and thanks for sticking with me. Regards, Herman :D

---

