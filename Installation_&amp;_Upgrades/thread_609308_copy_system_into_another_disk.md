---
title: "copy system into another disk"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by fm1234 on 2007-11-10
Hi,

I have two hard disks (of different sizes) in my system and the first (master ide) has bad sectors and I would like to move everything to the second disk (a slave ide, now empty but partitioned into ext3 and linux swap).

I guess I could do a cp -r (using sudo) from the first disk to the second and then make the second disk become the master ide. I'm not sure about possible open files. Would it help to boot only into shell mode (no X)? how?

What about the boot? how/when to install grub in the second system?

Do I have to do something else? (in old times with FDISK one would have to make the first partition active, but maybe this was just a DOS/Win thingy).

TIA,
Fernando

---

### Post by weblordpepe on 2007-11-10
Bump.

I would like to know this too. I beleive you would have to mark the new partition as active/boot, and install GRUB to the new disk, and tell it where the / partition is, and where swap is.

But I would like to hear from someone who knows what they're talking about (e.g. not me).
I think?

---

### Post by logos34 on 2007-11-11
You could:

Boot from the live cd an use the **dd command** to copy root partition over (root can't be mounted).  Then while you're still [on the live cd reinstall grub]("http://ubuntuforums.org/showthread.php?t=224351") (to the slave mbr) pointing to the new root partition on that drive, like weblordpepe suggested above.  

Edit /boot/grub/menu.lst and /etc/fstab to reflect any change in the partition #'s.  (If the layout is exactly the same except for the disk size and you will be taking out the bad disk and putting the slave as master, then you probably don't have to edit anything.  The uuid's will be the same--I'm certain about that)

Your primary slave drive is either hdb or sdb (depending on whether the libata storage driver chooses to see it as a scsi device--my Maxtor IDE's still show up as 'hda' and 'hdb').  So for example if your root partition on the master (bad) drive is hda2 and you want to copy it to hdb1, then:
> 
[sudo dd if=/dev/hda2 of=/dev/hdb1 bs=4096 conv=notrunc,noerror]("http://www.brunolinux.com/02-The_Terminal/The_dd_command.html")

That's how I'd do it (I think).  Either that or just back up /home and /var (where all your deb pkgs are stored) and then reinstall. Reinstalling might actually be a better idea come to think of it--maybe you have data corruption. 

I'd be interested in what others recommend for situations like this.

---

### Post by fm1234 on 2007-11-11
This is what I've done (*):
- boot with livecd
- mount both disks
- copy from 1st to 2nd disk (with cp -rp) 
- switch off computer
- switch disks (master <-> slave)
- boot again with livecd
- follow the procedure linked above to setup grub in the (now) master disk
- mount master disk
- get uuid of the master disk using ls -l /dev/disk/by-uuid
- sudo vi /boot/grub/menu.lst
- replace old id with master's id

(*) actually it was not so neat (e.g., I forgot to use cp -p to perserve file ownership).
I used cp instead of dd because partitions were very different and I was using only 10Gb of a disk of 150Gb, and I wanted to read only the blocks used by the files. Luckily, none of the bad sectors was affecting the files (no errors while cp).
The uuids are not the same and since I didn't change it the first time, Ubuntu would not boot.

Thanks for the help,
Fernando

---

