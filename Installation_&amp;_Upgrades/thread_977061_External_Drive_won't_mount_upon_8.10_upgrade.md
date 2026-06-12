---
title: "External Drive won't mount upon 8.10 upgrade"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by ms defector on 2008-11-09
I was hoping my first post to the forums wouldn't be asking for help, but maybe that was naive of me.  I've been trying to immerse myself in Linux methodology since my fairly recent divorce from microsoft vista (windows...whatever).

That being said, I reluctantly concede that I just can't find an answer yet to my issue with my external drive (WD My Book, formatted to NFTS).  The problem is either the device, or how Ubuntu 8.10 interacts with it since its official release.  I know this because I've been using 8.04 since April and upgraded to 8.10 during the beta and had no problem with the drive mounting up.  After rebooting one day last week, the external drive light just started blinking and I now receive this message:
"Error org.freedesktop.DBus.Error.NoReply"

Here's the long message:
"Unable to mount External_1
  DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."


The drive works fine if I use the 8.04 liveCD, but not the 8.10 liveCD. I even reinstalled 8.04 and voila! the drive works fine.  I immediately upgrade to 8.10, reboot after completion and the drive no longer works again.

The system seems to know that the drive is there as it recognizes the partitions, it just can't access them.

I'm not sure if I should report this as a bug or what. (Heck, I'm not even sure this is the right support category)

Thanks all!

MSD

---

### Post by taurus on 2008-11-09
Can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by ms defector on 2008-11-09
Thanks for the reply.

Here's what I've got:

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00027f4c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25496   204796588+   7  HPFS/NTFS
/dev/sda2           25497       25618      979965   82  Linux swap / Solaris
/dev/sda3           25619       48641   184932247+  83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x81c281c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24322   195358720    7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14593   117218241    7  HPFS/NTFS

---

### Post by echovolutionx on 2008-11-09
:confused::confused::confused:

---

### Post by taurus on 2008-11-09
I assume you want to mount /dev/sdc1 then.

```
sudo mkdir /media/sdc1
sudo mount -t ntfs-3g /dev/sdc1 /media/sdc1
df -h
```

Any error when you run those command, especially the second one?

---

### Post by ms defector on 2008-11-09
Sorry, I'm not really sure what you just suggested.  (Sometimes I suprise myself, how little I know)

All I want is for them to be accessible.  In Hardy, I could click on the icon and they would mount.  Now with Intrepid, I get nothing.  In fact, I am unable to mount any of the other NTFS drives until I turn the external drive off.  Then it everything appears to go back to business as usual.

---

### Post by ms defector on 2008-11-09
In response to commands...

desktop@desktop:~$ sudo mkdir /media/sdc1
mkdir: cannot create directory `/media/sdc1': File exists
desktop@desktop:~$ sudo mount -t ntfs-3g /dev/sdc1 /media/sdc1
fuse: mount failed: Device or resource busy
desktop@desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             175G  3.3G  163G   2% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  124K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.8M  1.5G   1% /dev
tmpfs                 1.5G  336K  1.5G   1% /dev/shm
lrm                   1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sdb1             187G   94G   93G  51% /media/Vista
/dev/sdc1             112G  104G  8.5G  93% /media/DOCUMENTS
/dev/sdc1             112G  104G  8.5G  93% /media/sdc1

---

### Post by taurus on 2008-11-09
Just run those three commands from a terminal and see what happens.

---

### Post by taurus on 2008-11-09
> **ms defector said:**
> In response to commands...

desktop@desktop:~$ sudo mkdir /media/sdc1
mkdir: cannot create directory `/media/sdc1': File exists
desktop@desktop:~$ sudo mount -t ntfs-3g /dev/sdc1 /media/sdc1
fuse: mount failed: Device or resource busy
desktop@desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             175G  3.3G  163G   2% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  124K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.8M  1.5G   1% /dev
tmpfs                 1.5G  336K  1.5G   1% /dev/shm
lrm                   1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sdb1             187G   94G   93G  51% /media/Vista
**[COLOR="Blue"]/dev/sdc1             112G  104G  8.5G  93% /media/DOCUMENTS[/COLOR]**
/dev/sdc1             112G  104G  8.5G  93% /media/sdc1

Looks like /dev/sdc1 is already mounted to /media/DOCUMENTS.

---

### Post by ms defector on 2008-11-09
The volumes I have labeled: "Vista" "Documents" are both internal drives.  The partition (though I don't see it there) labeled "XP" is my dual boot partition on the same drive as my linux ext3 partition. 

The ones that don't show up should be labeled: "My audio" "Videos" "External_1"

It seems like they were never mounted as sdc1.

I have to load the 8.04 liveCD to know for sure, but it seems like ssd, or sdd were more like it.  I don't know if that makes sense.

---

### Post by taurus on 2008-11-09
Sounds like the device name is changing.  Therefore, you need to use the UUID instead if /dev/sdxx to mount your external drive.

You can look it up to see the UUID by running this command from a terminal.

```
sudo blkid
```

---

### Post by ms defector on 2008-11-09
Believe it or not, the terminal froze up after entering the command until I turned off the external drive, then it immediately spat this out:

 desktop@desktop:~$ sudo blkid
[sudo] password for desktop: 
/dev/sda1: UUID="B0D0AD0BD0ACD93C" LABEL="XP" TYPE="ntfs" 
/dev/sda2: TYPE="swap" UUID="1fee8190-75ef-44a6-b5dd-3f87fb92edb4" 
/dev/sda3: UUID="584bb8d0-71be-43f0-b097-0104651242f5" TYPE="ext3" 
/dev/sdb1: UUID="56B842F8B842D5E1" LABEL="Vista" TYPE="ntfs" 
/dev/sdc1: UUID="B47487ED7487B0A2" LABEL="DOCUMENTS" TYPE="ntfs" 
/dev/sdd5: UUID="08F8C250F8C23BA6" LABEL="My Audio" TYPE="ntfs" 
/dev/sdd6: UUID="D4F4C01BF4BFFE2C" LABEL="Videos" TYPE="ntfs

---

### Post by ms defector on 2008-11-12
Hello all,

I guess this thread has stalled out a bit, but I really need to figure this one out.  I'm determined to stay with this Linux distro, but I've got to figure a way to keep my media up and running for the rest of the family or have the confidence that any future expansion won't end up in some inexplicable meltdown.  I'm still searching and if I find the answer somewhere else, I'll post it here.

But to recap:

-Western Digital MyBook 250 external drive with 3 partitions formatted to NTFS...

   ...recognized, mounted and worked perfectly with clean install of Ubuntu 8.04 Hardy Heron with updates.
   ...upon immediate upgrade to Ubuntu 8.10 Intrepid Ibex, partitions will not mount and drive light simply blinks.

Should I report this as a bug?  There were no hardware or software changes to the system aside from updates and the upgrade, all done from within Update Manager.

Thanks...really.

---

### Post by vanadium on 2008-11-12
In the output of "sudo fdisk -l" you gave earlier, only your system disk has three partitions. Next to your system disk sda, there is sdb and sdc, each with one ntfs formatted partition.

The output of "df -h" shows that both the partitions on sdb and sdc are mounted and thus accessible. sdb1 is accessible through the directory /media/vista, sdc1 is mounted twice (that is possible in linux), one on /media/DOCUMENTS and once on /media/sdc1.

From the output you posted, you really do not have a problem.

---

### Post by ms defector on 2008-11-12
Thanks for the reply.  

To tell you the truth, I don't know why those three external drive partitions don't show up.  I'm really confused.  However the output of "sudo blkid" seems to show that they do exist. I really don't know what that means, though.

I'm kinda searching in the dark.  I'm so desperate that I'm searching in all my system logs, though it's totally greek to me and may have nothing to do with anything.

-----Ignore below.  I closed Nautilus Browser reopened it and the other partitions became accessible.  Still no luck with the External drive---------------


Here's another twist:  While the external drive is on, but on the blink, I can't access any of the other drives (except the filesystem), even though they appear to be mounted.  

I get this error message: "Unable to mount location  Internal error: No mount object for mounted volume"

  Once I manually turn off the drive, everything else comes back online.

---

### Post by ms defector on 2008-11-12
The thing I can't figure is what was it that changed from 8.04 to 8.10 that would cause this issue to surface?  

If I go back to 8.04, it will work again...but I don't like to give up or go back. (chutes and ladders...not my favorite game)

---

### Post by ms defector on 2008-11-12
I've been playing with this thing and decided to select a different kernel in the grub menu.

When I load kernel 2.6.24-21 everything works as it should.

If I restart and load kernel 2.6.27-7 the external drive goes haywire again.

Back to 2.6.24-21...copasetic.

Any ideas?

---

### Post by vanadium on 2008-11-12
Indeed, there is a drive sdd that showed up in your "sudo blkid". However, it did not show up in the output of "sudo fdisk -l" which indicates that it was not connected at that time. Then someone referred to sdc1 while that was not the problem drive. Sorry, but this thread is not quite clear and it is easy to get confused.

Anyway, it is not uncommon that things go astray with a new kernel (up to the point where your computer won't boot). Usually, this gets fixed with a subsequent update. I advise you indeed to stick with your older kernel and await a next update (if that conforts you, I am currently running an older version as well because of an issue with the newest one).

---

### Post by Berduchwal on 2008-11-13
Hi
I have similar issue!
I use network attached share and use smb to connect to, but after upgrade when I try to connect it connects for 1second and then disconnects.
What is more strange is that I can connect via ftp but can not access all folders!
It worked find under 8.04

---

### Post by ms defector on 2008-11-14
Well gang, as it stands now, I have gone back to Hardy.  There are some Intrepid features I really would have enjoyed using, but I'm sure things will work out.  I'm still going to keep searching and try to get a little deeper into understanding the system.  Maybe this thread won't be dead, but for now, I guess we're at an impasse.


Jaunty or bust!

---

### Post by chipmaker on 2008-11-24
> **ms defector said:**
> I've been playing with this thing and decided to select a different kernel in the grub menu.

When I load kernel 2.6.24-21 everything works as it should.

If I restart and load kernel 2.6.27-7 the external drive goes haywire again.

Back to 2.6.24-21...copasetic.

Any ideas?

I think this is the same problem happening to my Windows drives!

I first started running Ubuntu 8.10 two weeks ago, using a bootable USB disk created from 8.10 LiveCD. After running a fresh install on USB, I am able to access my Windows drives normally. However, when I did an update on the from Update Manager, my Windows drives were having problems being mounted. So I made a fresh USB-bootable disk and didn't run an update. My Windows drive can now mount properly. I think I'll wait for the next kernel updates before I run Update Manager.

---

