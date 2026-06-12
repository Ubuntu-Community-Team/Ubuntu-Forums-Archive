---
title: "dmraid prevents boot - busybox after trying to access fakeraid"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by aroddo on 2008-04-28
I made the mistake of using the "advantages" of the nvidia fakeraid feature to create a RAID-0 stripe with S-ATA harddisks.
I didn't make the mistake of using the stripe to host my OS, though.

My system looks like this:

[[IMG]http://img291.imageshack.us/img291/3735/sdant9.png[/IMG]]("http://%22http://imageshack.us")

sda is my solo disk containing windows and ubuntu:
sda1 - windows xp 64
sda2 - extended partition
sda3 - ubuntu
sda4 - linux swap
sda5 - just data storage
sda6 - windows xp

sdb and sdc are my raid drives and show up as unallocated in gparted.


So, what I did was this:

[LIST]
[*]Both windows partitions existed beforehand. I created a primary partition for linux.
[*]Installed ubuntu and configured grub. everything works fine. Windows boots and detects the fakeraid like always. Ubuntu boots but doesn't detect raid.
[*]installed dmraid using synaptic package manager
[*]reboot
[/LIST]
I landed in the BusyBox.
I typed the log from console 1 on my laptop.

CTRL+ALT+F1 console:
> 
Loading, please wait...
/dev/sdb: "sil" and "nvidia" formats discovered (using nvidia)!
kinit name_to_dev_t(/dev/disk/by-uuid/5f83b254-8255-4855-81b1-6c965ee54ea) = sda4(8,4)
kinit: trying to resume from /dev/disk/by-uuid/5f83b254-8255-4855-81b1-6c965ee54ea
kinit: No resume image, doing normal boot...
mount: Mounting /dev/disk/by-uuid/8ea78797-f5df-48a2-ae0f-66053bc0a84d on /root failed: Device or resource busy
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
Using the live-CD I mounted the ubuntu partition and took a look at the fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=8ea78797-f5df-48a2-ae0f-66053bc0a84d     /       reiserfs notail,relatime    0       1
# /dev/sda4
UUID=5f83b254-8255-4855-81b1-6c9665ee54ea   none  swap    sw                     0       0
/dev/scd0         /media/cdrom0    udf,iso9660 user,noauto,exec,utf8                    0       0

```when I look at the busybox output I see that it tries to resume from the swap partition first but doesn't find anything.
Afterwards it tries to mount sda3 - which contains ubuntu - but can't because it's busy.

Why is it busy ? What did dmraid do to make it busy ? How can I boot my system again ? 

I browsed the forums but this particular problem doesn't seem to have been solved - although there are some guides that allow installing on raid, which I don't need to.
And none of them encountered busy devices either.

Please help !

[update]
I checked the /dev/mapper directory in the busy box (I think that's the directory dmraid fills):
> 
(initframfs) ls /dev/mapper

control
nvidia_fiehaifc
nvidia_fiehaifc1
sil_agaddbgfaba
sil_agaddbgfaba1
sil_agaddbgfaba2
sil_agaddbgfaba3
sil_agaddbgfaba4
sil_agaddbgfaba5
sil_agaddbgfaba6


---

### Post by aroddo on 2008-04-28
I restored ubuntu with a backup and installed dmraid again.

```

# sudo dmraid -s
/dev/sdb: "sil" and "nvidia" formats discovered (using nvidia)!
*** Set
name   : nvidia_fiehaifc
size   : 1172229376
stride : 128
type   : stripe
status : ok
subsets: 0
devs   : 2
spares : 0
*** Set
name   : sil_agagddbgfaba
size   : 586112640
stride : 128
type   : stripe
status : ok
subsets: 0
devs   : 1
spares : 0

```I must say, I don't understand the size numbers.
My drives are 279,47 GiB large according to GParted.
the sil_agagddbgfaba set is size 586.112.640 , which sounds right.
The nvidia_fiehaifc is size 1.172.229.376, which doesn't make any sense (apart from being twice as big as the other one).

I'll try to deactivate the raids just to find out if I can boot or not.

```
# sudo dmraid -an
```

[update]
Doesn't make a difference. 
dmraid still screws the system just like before.

---

### Post by aroddo on 2008-04-28
Hmm... I just found out something interesting:

dmraid seems to map even drives that ain't stuffed into a raid, causing any attempts to mount them to fail:
[I]
BusyBox[/I]:
> 
# mkdir sda1
# mount -t ntfs-3g /dev/sda1 /sda1
mount: Mounting /dev/sda1 on /sda1 failed: Device or resource busy

# mkdir sda3
# mount -t reiserfs /dev/sda3 /sda3
mount: Mounting /dev/sda3 on /sda3 failed: Device or resource busy


So I  checked out the /dev/mapper entries again:
> sil_agaddbgfaba
sil_agaddbgfaba1
sil_agaddbgfaba2
sil_agaddbgfaba3
sil_agaddbgfaba4
sil_agaddbgfaba5
sil_agaddbgfaba6 			 		
hmm... enumerated just like the sda device ... maybe ?

> 
# mount -t ntfs-3g /dev/mapper/sil_agaddbgfaba1 /sda1
# mount -t reiserfs /dev/mapper/sil_agaddbgfaba3 /sda3
 

and tada, i got my drives back.

I'm still stuck in the busybox, however, so I have to find out what to edit so that linux mounts the mapped drives and not the, er, real ones.

I'll try fstab first.

---

### Post by aroddo on 2008-04-28
so much for that: fstab get's completely ignored.

Who knows more about it ? Where does linux look for the partitions it has to mount ?

---

### Post by aroddo on 2008-04-28
**[SIZE=4]Success ! [/SIZE]**

well, in a sense.


First of all, I created a method to fix my system after every botched try at dmraid. I had to, because restoring a backup using partimage took was fast ... but even that takes too long if you have to do it all the time.

What I did was duplicating a save initrd (whatever that is) and creating a new grub entry for it. That way I could keep and boot my save configuration while ruining the other one.

(my edit in ***bold italic***)
> 
# cd /boot
 # sudo cp initrd.img-2.6.24-16-genericinitrd.img-2.6.24-16-generic.save
Then I had to modify the /boot/grub/menu.lst:
```

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=8ea78797-f5df-48a2-ae0f-66053bc0a84d ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

[I][B]title        Ubuntu 8.04, kernel 2.6.24-16-generic.save
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=8ea78797-f5df-48a2-ae0f-66053bc0a84d ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic.save
quiet[/B][/I]

```And when I booted the save configuration after yet another botched attempt I noticed that GParted shows the mapped raid drive in it's device list !

So i try to mount it
```

# sudo mkdir /media/raid
# sudo mount -t ntfs-3g /dev/mapper/nvidia_fiehaifc1 /media/raid

```And bingo, RAID online !

A quick "aptitude show dmraid" shows that dmraid is installed. But any evil changes dmraid did to my system have been purged.

It's not a solution but it's a workaround.


[LIST=1]
[*]duplicate your ***initrd.img***
[*]create a grub entry for the duplicate ***initrd.img***
[*]install dmraid
[*]reboot the duplicated initrd
[*]rename the ruined initrd (the one you didn't boot) to /boot/initrd.img-2.6.24-16-generic.dmraided
[*]rename the duplicated initrd (the one you're using now) back
[*]manually mount the raid or put it in fstab
[*]you can now remove the *save*-entry in /boot/grub/menu.lst
[/LIST]
Works just fine.

But since I'm not sure what dmraid actually did in the initrd I can't say how save this is.
I'd reeeeaaaaaaaally like some competent feedback saying it's all fine.

---

### Post by Anthill on 2008-04-28
It's really too bad that you're on your own here, replying to yourself... I've got exactly the same problem and haven't found a solution yet.

I wonder if editing the GRUB boot string

```
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=8ea78797-f5df-48a2-ae0f-66053bc0a84d
```

to read

```
kernel        /boot/vmlinuz-2.6.24-16-generic root=/dev/mapper/nvidia_fiehaifc1
```

would do anything?

---

### Post by Anthill on 2008-04-28
Reporting in:  Yes, it seems like installing dmraid tools causes problems when trying to access drives through either /dev/sdaX or /dev/disk/by-uuid/foofoofoo.  I suppose dmraid has attached itself to those paths, hence the 'device or resource busy' error messages.

The solution for me, was to:

1) when the boot fails and dumps you to busybox after failing to mount the root partition, fix things up by mounting /dev/mapper/nvidia_efeddfba1 (for my NVIDIA raid drive) to /root then do the same for /dev/mapper/foo to /home and so forth.

2) type 'exit', busybox should quit and resume booting the kernel

3) once booted up, edit /boot/grub/menu.lst and change the references to root=by-UUID=foofoofoo to the appropriate root=/dev/mapper/foo

4) grub-install to your appropriate drive (can't use /dev/mapper addresses though!  grr!)

5) edit /etc/fstab to remove references to disk UUIDs and replace with corresponding /dev/mapper/foo addresses

6) curse linux developers

7) reboot, cross fingers.

---

### Post by aroddo on 2008-04-29
looks like we have found a method to escape the busybox in case you failed to backup first. :)

---

### Post by dalbuschat on 2008-06-06
I'm experiencing the same problem.
I have four SATA discs, two of them are stand-alone and two are striped with nvidia fake-raid.
I installed Ubuntu on sda3 and it works perfectly. But a single ```
sudo apt-get install dmraid
``` messes up the initrd. As aroddo pointed out, the initrd fails to mount sda3 to / because it is "busy". I could not find out why it is busy.
I simply solved the problem by booting the older Kernel. 2.6.24-18 is now broken thanks to dmraid, but 2.6.24-17 boots fine, I guess because the corresponding initrd has not been altered. I even have dmraid modules loaded and the raid mounts fine.
But I'd like to have this problem pinned down and fixed. I dunno where to look for the cause of the problem, because I'm not too familiar with initrds.

Thanks for sharing your experience and providing fixes, aroddo, this is **HIGHLY** appreciated.

Regards,
Daniel Albuschat

---

### Post by EagleDM on 2008-07-15
I just filled a bug in Launchpad with what you guys are experiencing.

I could easily reproduce the bug just installing Ubuntu over a single HDD (in a Matrix RAID enviroment) and then installing dmraid (aptitud install dmraid)

After boot, my kernel no longer boots and "device busy" is present.


If you want you can check launchpad and join me in trying to "fix" or find a solution to this annoying bug.

[https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/245842](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/245842)

---

### Post by psusi on 2008-07-18
It looks like your non raid boot disk actually IS part of a ( broken ) raid.  Based on what you show so far, it looks like dmraid has detected two different raid sets, one of which appears to be a stripe set that only contains one disk.  To confirm, post the output of dmraid -n.  If sda is NOT supposed to be part of a raid set, then have dmraid strip the metadata from it by running dmraid -E -r /dev/sda.

---

### Post by EagleDM on 2008-07-19
Are you sure?

What you say is pretty interesting, except for the fact that the disk was actually taken out of the PC, their partitions had being removed and the disk blanked and then I re-utilized the disk again.

The disk was previously on a NVRAID stripe,  does the NVRAID information gets deleted when I delete the whole partitions on the disk?

if that's not the case, how can I do it?

I believe maybe you found out the problem, I will do what you recommend, THANK YOU!

Will post results.

---

### Post by EagleDM on 2008-07-19
Success !

Thank you very much !!

I could never found on my own, not until I put dmraid -n

That NVIDIA RAID was pretty evident once I put dmmraid -n, deleting metadata totally fixed it!

---

### Post by specter9mm on 2008-07-26
Thank you so much.  It looks like dmraid screwed initrd, though I couldn't find exactly how it did.  Took me forever to find your thread, but it was fixed in minutes.  You, sir, are awsome!

---

### Post by MacLux on 2008-10-07
Hi,

I'm stuck with the same problem. Just to make sure, I don't mess up the whole hdd - when I delete metadata with "dmraid -E -r /dev/sdb", can I then still use the partitions on the disk without restoring a partition image or something like that?

Do I have to (and CAN I) tell the BIOS to boot from that one non-RAID disk (instead the raid controller), to be able to boot from grub?

Best,
Mac

---

