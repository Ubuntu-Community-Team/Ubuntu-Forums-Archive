---
title: "Moving to new hard drive"
date: 2006-09-18
forum: Installation &amp; Upgrades
---

### Post by mixmaster on 2006-09-18
I have just aquired a new, larger, hard drive.  I would like to move my existing linux setup from its present drive to the new drive and resize the partitions in the process.  Failing that, I'll settle for just moving everything and sorting out the partition problem later.

At the end of this process I would like the new drive to be the default boot device (ie so that I can remove the original drive if I choose to).

Any suggestions as to the best way to go about this?  I can't afford to render the system unbootable/inaccessible so I'm not willing just to experiment off my own bat.

I am not a noob, but neither do I claim to be a guru, if that makes any difference to the detail of the instructions offered.

Thanks!

---

### Post by kidders on 2006-09-18
Hi there,

I guess the big question is whether you can afford to take your system down for a little while. If you can, I would suggest the following:

[LIST=1]
[*]Shut down your X server, all network services and other applications, until virtually nothing is running.
[*]Use **lsof** to check that the list of open files is quite small.
[*]Start copying with **cp**.
[*]Install grub on your new disk & shut down.
[*]Physically swap your hard drives.
[*]Boot your PC, remembering to double-check your BIOS's boot order.
[/LIST]

I suggested copying with "cp", but that's not your only possible approach. You *could* use "dd" to do a byte-for-byte copy of an entire disk, including its partition scheme ... but since you want to resize them anyway, that would just create hassle. A manual copy may be low-tech, but it will work! (Provided of course you use the **-dpR** switches!)

The one assumption I'm making here is that your new disk uses the same I/O bus as the old one ... ie you're not switching from an IDE interface to an SATA one. If you *are*, you'll need to tweak your /etc/fstab to reflect device name changes.

May I suggest that you consider spreading your Linux across both disks? It might boost your I/O performance a little :-) If you *do* choose to do that, do it in two steps. What I mean is, make sure your copied OS works for a few hours before you erase the original copy.

Post back if you need more explicit help, or if there's a particular problem you're afraid of falling victim to :-)

---

### Post by mixmaster on 2006-09-18
Thanks for the suggestions.  Eventually I decided that since basic Ubuntu install is fairly simple, it was easier to reinstall on the new drive and then migrate.

Just in case anyone else wants to do something similar, this is the procedure I used.

Unplug SATA1 and plug the new drive in there.

Install Ubuntu on SATA1:
2 Gb ext2 /boot
20 Gb ext3 /root
<Remainder> : Unused partition
6Gb swap (at end)

I then plugged my old drive into SATA2 /home/<mylogin>, /opt/* and a few other directories to the old drive.  This has given me most of the functionality I had before the move.  I'm now using LVM to create mountable filesystems to replace my home directory and various /opt sections.  Once everything is working to my satisfaction I will remove the original Ubuntu partitions and the fossil windoze partition from the original drive.

I eventually did it this way because I had about 6 different window managers plus a load of unwanted rubbish on the older driver and on reflection it seemed better to start with a clean install.  However, your comment about using both drives made me think and it would seem sensible to put the swap partition on the drive which doesn't have all the most commonly used apps.

---

