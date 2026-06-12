---
title: "Mostly painless upgrade and backup path"
date: 2011-12-03
forum: Installation &amp; Upgrades
---

### Post by jeff.sadowski on 2011-12-03
When I built my home server system, a little over a year ago, I included 2 disks. I was originally going to raid it, but I held of. I had plans in my head how I wanted to use the second disk. A couple of weeks ago I implemented the ideas that had been developing in my head when I started running out of space in some of my partitions. My idea was to rsync all the partitions nightly to the second disk. Why? (you might ask.) Simple it backs things up. But that's not all. I also created a fully operational second disk following I will describe more about this as I'm loving it more and more. 

So first I partitioned my second disk exactly how I wanted it. Then I formatted and labelled my partitions, because labels just made a lot more sense to me then disk UUID, that my fstab file originally had in it. I also labelled my old disk with similar labels with the exception of appending 0's to my old disk's partition label's and 1's to my second disks label's
example my first disk contains partitions with labels usr0,boot0,root0,home0,... and my second disk contains labels usr1,boot1,root1,home1. Then I created directories in my root that mirrored where the original stuff was mounted. I created /1 /usr1 /boot1 /home1 and /current (a second mounting point for the real root partition) and created noauto boot entries in /etc/fstab that mounts my second disks partitions and the second mount point for the real root partition. "noauto" so that they don't mount on startup.
Reasoning: When a disk is not even mounted there is no reason it should spin up. So I'm hopping that it gives me a better chance that my second disk will stay powered off until needed. Then I created a script that mounts and rsyncs the partitions (for the root partition it rsyncs from the /current mounting instead of / so it doesn't copy all the udev stuff and proc stuff or any other mounted partitions), then does a small amount of sed editing of swapping disk labels on two files /etc/fstab and /boot/extlinux.conf then unmounts them. I used extlinux because it was easier than figuring out the stuff that all those grub scripts did to create grub config files. I could have used grub but grub has changed too much for me. I use to edit grub config files but things have changed since those days.
I had to use extlinux to make /boot and /boot1 bootable and I copied the mbr.bin that came with syslinux over grub and made /boot and /boot1 cosponsoring partitions with the boot flags. I set my script to run nightly and wala even if one disk dies the other is ready to take its place.
Disadvantages of right now: When I upgrade the kernel I need to manually edit the /boot/extlinux.conf file. I'll script that as well when I get around to it.
Advantages over raiding: Second disk is left offline until needed. If something goes wrong on my primary disk I can easily select to boot off my second disk and repair it.
Other Disadvantage: is databases should be shutdown while doing an rsync on it.

So now I can try an upgrade and if it fails just boot off my second disk and bam I'm back up.
Another advantage is that backup partitions don't need to be the same size. Its easy to upgrade disks or even downgrade disks.

---

### Post by oldtimer7777 on 2011-12-03
I use Remastersys to backup my existing system just the way I want it to  be. Then I use Startup Disc Creator to create a live USB Flash Drive  containing my entire backup.  From that point on I use my NAS ethernet  file server to store all my data that I need.  I do weekly backups of my  entire system with Remastersys Backup and use Startup Disc Creator to  make a new USB Live Stick each time. Completely automatic.  Plus I can  take my system and boot it from any PC I want, and still have all my  settings and everything.  I can access my NAS file server remotely via  my VPN router to access larger files over the internet that I need from  anywhere in the world.  I can install my backup to any other computers  for extended periods of time, if need be. My system is on my keychain  everywhere I go just in case.  It can reinstall my system in less than  20 minutes on a newer PC without missing a beat. Extremely flexible,  portable, and backed up. 

> **jeff.sadowski said:**
> When I built my home server system, a little over a year ago, I included 2 disks. I was originally going to raid it, but I held of. I had plans in my head how I wanted to use the second disk. A couple of weeks ago I implemented the ideas that had been developing in my head when I started running out of space in some of my partitions. My idea was to rsync all the partitions nightly to the second disk. Why? (you might ask.) Simple it backs things up. But that's not all. I also created a fully operational second disk following I will describe more about this as I'm loving it more and more. 

So first I partitioned my second disk exactly how I wanted it. Then I formatted and labelled my partitions, because labels just made a lot more sense to me then disk UUID, that my fstab file originally had in it. I also labelled my old disk with similar labels with the exception of appending 0's to my old disk's partition label's and 1's to my second disks label's
example my first disk contains partitions with labels usr0,boot0,root0,home0,... and my second disk contains labels usr1,boot1,root1,home1. Then I created directories in my root that mirrored where the original stuff was mounted. I created /1 /usr1 /boot1 /home1 and /current (a second mounting point for the real root partition) and created noauto boot entries in /etc/fstab that mounts my second disks partitions and the second mount point for the real root partition. "noauto" so that they don't mount on startup.
Reasoning: When a disk is not even mounted there is no reason it should spin up. So I'm hopping that it gives me a better chance that my second disk will stay powered off until needed. Then I created a script that mounts and rsyncs the partitions (for the root partition it rsyncs from the /current mounting instead of / so it doesn't copy all the udev stuff and proc stuff or any other mounted partitions), then does a small amount of sed editing of swapping disk labels on two files /etc/fstab and /boot/extlinux.conf then unmounts them. I used extlinux because it was easier than figuring out the stuff that all those grub scripts did to create grub config files. I could have used grub but grub has changed too much for me. I use to edit grub config files but things have changed since those days.
I had to use extlinux to make /boot and /boot1 bootable and I copied the mbr.bin that came with syslinux over grub and made /boot and /boot1 cosponsoring partitions with the boot flags. I set my script to run nightly and wala even if one disk dies the other is ready to take its place.
Disadvantages of right now: When I upgrade the kernel I need to manually edit the /boot/extlinux.conf file. I'll script that as well when I get around to it.
Advantages over raiding: Second disk is left offline until needed. If something goes wrong on my primary disk I can easily select to boot off my second disk and repair it.
Other Disadvantage: is databases should be shutdown while doing an rsync on it.

So now I can try an upgrade and if it fails just boot off my second disk and bam I'm back up.
Another advantage is that backup partitions don't need to be the same size. Its easy to upgrade disks or even downgrade disks.

---

### Post by oldtimer7777 on 2011-12-03
:popcorn:
> **jeff.sadowski said:**
> When I built my home server system, a little over a year ago, I included 2 disks. I was originally going to raid it, but I held of. I had plans in my head how I wanted to use the second disk. A couple of weeks ago I implemented the ideas that had been developing in my head when I started running out of space in some of my partitions. My idea was to rsync all the partitions nightly to the second disk. Why? (you might ask.) Simple it backs things up. But that's not all. I also created a fully operational second disk following I will describe more about this as I'm loving it more and more. 

So first I partitioned my second disk exactly how I wanted it. Then I formatted and labelled my partitions, because labels just made a lot more sense to me then disk UUID, that my fstab file originally had in it. I also labelled my old disk with similar labels with the exception of appending 0's to my old disk's partition label's and 1's to my second disks label's
example my first disk contains partitions with labels usr0,boot0,root0,home0,... and my second disk contains labels usr1,boot1,root1,home1. Then I created directories in my root that mirrored where the original stuff was mounted. I created /1 /usr1 /boot1 /home1 and /current (a second mounting point for the real root partition) and created noauto boot entries in /etc/fstab that mounts my second disks partitions and the second mount point for the real root partition. "noauto" so that they don't mount on startup.
Reasoning: When a disk is not even mounted there is no reason it should spin up. So I'm hopping that it gives me a better chance that my second disk will stay powered off until needed. Then I created a script that mounts and rsyncs the partitions (for the root partition it rsyncs from the /current mounting instead of / so it doesn't copy all the udev stuff and proc stuff or any other mounted partitions), then does a small amount of sed editing of swapping disk labels on two files /etc/fstab and /boot/extlinux.conf then unmounts them. I used extlinux because it was easier than figuring out the stuff that all those grub scripts did to create grub config files. I could have used grub but grub has changed too much for me. I use to edit grub config files but things have changed since those days.
I had to use extlinux to make /boot and /boot1 bootable and I copied the mbr.bin that came with syslinux over grub and made /boot and /boot1 cosponsoring partitions with the boot flags. I set my script to run nightly and wala even if one disk dies the other is ready to take its place.
Disadvantages of right now: When I upgrade the kernel I need to manually edit the /boot/extlinux.conf file. I'll script that as well when I get around to it.
Advantages over raiding: Second disk is left offline until needed. If something goes wrong on my primary disk I can easily select to boot off my second disk and repair it.
Other Disadvantage: is databases should be shutdown while doing an rsync on it.

So now I can try an upgrade and if it fails just boot off my second disk and bam I'm back up.
Another advantage is that backup partitions don't need to be the same size. Its easy to upgrade disks or even downgrade disks.

---

