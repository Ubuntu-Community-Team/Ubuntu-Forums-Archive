---
title: "Trouble installing grub on RAID array"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by parsim on 2011-02-03
I'm trying to switch to a new RAID5 array but can't get it to boot. My disks:
[list=1][*]/dev/sda: new RAID member
[*]/dev/sdb: Windows disk
[*]/dev/sdc: new RAID member
[*]/dev/sdd: old disk, currently using /dev/sdd3 as /
[/list]

The RAID array is /dev/md0, which is comprised of /dev/sda1 and /dev/sdc1. I have copied the contents of /dev/sdd3 to /dev/md0, and can mount /dev/md0 and chroot into it. I did this:

```
sudo mount /dev/md0 /mnt/raid
sudo mount --bind /dev /mnt/raid/dev
sudo mount --bind /proc /mnt/raid/proc
sudo mount --bind /sys /mnt/raid/sys
sudo chroot /mnt/raid
update-grub
grub-install /dev/sda
```

This completes with no errors, and /boot/grub/grub.cfg looks correct *[EDIT: No it doesn't. It has root='(md/0)' instead of root='(md0)']*. For example, here's the first entry:

```
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
	recordfail
	insmod raid
	insmod raid5rec
	insmod mdraid
	insmod part_msdos
	insmod part_msdos
	insmod ext2
	set root='(md/0)'
	search --no-floppy --fs-uuid --set a928b10f-bc3a-43ea-a4e2-49b073a8375d
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=a928b10f-bc3a-43ea-a4e
2-49b073a8375d ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
```

The UUID a928b10f-bc3a-43ea-a4e2-49b073a8375d is /dev/md0.

However, when I try to boot from /dev/sda, I get:

```
error: file not found
grub rescue>
```

---

### Post by YesWeCan on 2011-02-03
I may be wrong but I don't think Grub supports any RAID level other than 1. So I think you need to make a separate boot partition. As you are using two drives you could make a RAID 1 for Grub so you can boot off either HD.

---

### Post by parsim on 2011-02-03
I think that's the case for legacy grub. I should have said I'm using grub-pc, which does support RAID5 (and was working fine on a test array I built earlier).

---

### Post by psusi on 2011-02-03
Type set at the rescue prompt and see what root is set to.  Also check what drives ls detects.

---

### Post by YesWeCan on 2011-02-03
Yes you are right. I picked up some out of date info from somewhere. Just out of interest, would grub-install /dev/md0 also work?

---

### Post by parsim on 2011-02-03
> **psusi said:**
> Type set at the rescue prompt and see what root is set to.  Also check what drives ls detects.

Thanks! Here's the output:
```
grub rescue> set
prefix = (md/0)/boot/grub
root = md/0
grub rescue> ls
(md/0) (hd0) (hd0,msdos2) (hd0,msdos1) (hd1) (hd1,msdos3) (hd1,msdos2) (hd1,msdos1) (hd2) (hd2,msdos1) (hd3) (hd3,msdos2) (hd3,msdos1)
```
So I'm very interested to see an extra slash in "md/0". My array is /dev/md0, not /dev/md/0.

Re: the output of "set", /dev/sda and /dev/sdc have two partitions each (main + swap) while /dev/sdd has three partitions and /dev/sdb has whatever Windows does (one?).

---

### Post by psusi on 2011-02-03
The naming is kind of odd.  What do you get from ls (hd/0)/boot/grub?

---

### Post by parsim on 2011-02-03
Thanks again for the help.

Not much from that command:
```
> ls (hd/0)/boot/grub
error: no such disk
```

I thought maybe that was a typo so tried some variations.
```
> ls (hd0)/boot/grub
error: unknown filesystem
> ls (hd0,0)/boot/grub
error: no such partition
> ls (md/0)/boot/grub

error: file not found
> ls (md0)/boot/grub
error: no such disk
> ls (hd1,msdos3)/boot/grub
<long list of files from /dev/sdd3>
> ls (md/0)/

```
That last command just produced a blank line.

---

### Post by YesWeCan on 2011-02-04
```
brian@bU10:/media$ sudo mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sdb /dev/sdc missing
mdadm: array /dev/md0 started.
brian@U10:/media$ sudo grub-install /dev/md0
Installation finished. No error reported.
```
Says it works.

---

### Post by psusi on 2011-02-04
Oops, I meant md, not hd.  Can you run the boot info script and post the results?

---

### Post by parsim on 2011-02-04
> **psusi said:**
> Can you run the boot info script and post the results?

Here it is. Again, it looks like grub is searching for md/0 instead of md0 for some reason. But I have no idea why, or how to fix it.

---

### Post by parsim on 2011-02-04
Some more investigation. I chroot'ed into /dev/md0 and ran **grub-mkconfig**, which again produced output including the line:
```
  set root='(md/0)'
```
It seems that this is coming from **grub-probe**:
```
# grub-probe -v /
grub-probe: info: cannot open `/boot/grub/device.map'.
grub-probe: info: changing current directory to /dev.
grub-probe: info: changing current directory to vboxusb.
grub-probe: info: changing current directory to 002.
grub-probe: info: changing current directory to 004.
grub-probe: info: changing current directory to snd.
grub-probe: info: changing current directory to by-path.
grub-probe: info: changing current directory to cpu.
grub-probe: info: changing current directory to shm.
grub-probe: info: the size of hd0 is 976773168.
grub-probe: info: the size of hd0 is 976773168.
grub-probe: info: the size of hd0 is 976773168.
grub-probe: info: the size of hd0 is 976773168.
grub-probe: info: the size of hd1 is 156312576.
grub-probe: info: the size of hd1 is 156312576.
grub-probe: info: the size of hd1 is 156312576.
grub-probe: info: the size of hd2 is 976773168.
grub-probe: info: the size of hd2 is 976773168.
grub-probe: info: the size of hd2 is 976773168.
grub-probe: info: the size of hd2 is 976773168.
grub-probe: info: the size of hd3 is 976773168.
grub-probe: info: the size of hd3 is 976773168.
grub-probe: info: the size of hd3 is 976773168.
grub-probe: info: the size of hd3 is 976773168.
grub-probe: info: the size of hd3 is 976773168.
grub-probe: info: the size of hd0 is 976773168.
grub-probe: info: the size of hd0 is 976773168.
grub-probe: info: the size of hd0 is 976773168.
grub-probe: info: the size of hd0 is 976773168.
grub-probe: info: the size of hd1 is 156312576.
grub-probe: info: the size of hd1 is 156312576.
grub-probe: info: the size of hd1 is 156312576.
grub-probe: info: the size of hd2 is 976773168.
grub-probe: info: the size of hd2 is 976773168.
grub-probe: info: the size of hd2 is 976773168.
grub-probe: info: the size of hd2 is 976773168.
grub-probe: info: the size of hd3 is 976773168.
grub-probe: info: the size of hd3 is 976773168.
grub-probe: info: the size of hd3 is 976773168.
grub-probe: info: the size of hd3 is 976773168.
grub-probe: info: the size of hd3 is 976773168.
**grub-probe: info: opening md/0.**
ext2
```
It somehow thinks the device is md/0 instead of md0, despite this:
```
# mount
rootfs on / type rootfs (rw)
none on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
none on /proc type proc (rw,nosuid,nodev,noexec,relatime)
none on /dev type devtmpfs (rw,relatime,size=2021324k,nr_inodes=505331,mode=755)
none on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/disk/by-uuid/416ac6b2-d0d5-4479-8737-79344b2c2518 on / type ext4 (rw,relatime,barrier=1,data=ordered)
none on /sys/kernel/debug type debugfs (rw,relatime)
none on /sys/kernel/security type securityfs (rw,relatime)
none on /dev/shm type tmpfs (rw,nosuid,nodev,relatime)
none on /var/run type tmpfs (rw,nosuid,relatime,mode=755)
none on /var/lock type tmpfs (rw,nosuid,nodev,noexec,relatime)
none on /proc/fs/vmblock/mountPoint type vmblock (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)
gvfs-fuse-daemon on /home/max/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
**/dev/md0 on / type ext4 **(rw,relatime,barrier=1,stripe=256,data=ordered)
none on /dev type devtmpfs (rw,relatime,size=2021324k,nr_inodes=505331,mode=755)
none on /proc type proc (rw,nosuid,nodev,noexec,relatime)
none on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
```

I find that "ext2" from grub-probe suspicious, too, because the filesystem is ext4.

---

### Post by parsim on 2011-02-04
> **YesWeCan said:**
> ```
brian@bU10:/media$ sudo mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sdb /dev/sdc missing
mdadm: array /dev/md0 started.
brian@U10:/media$ sudo grub-install /dev/md0
Installation finished. No error reported.
```
Says it works.

I get this (from within chroot):
```
# grub-install /dev/md0 
/usr/sbin/grub-setup: error: can't open /dev/md/0: No such file or directory.
```

---

### Post by psusi on 2011-02-04
Grub does not differentiate between ext[234]; they are the same FS just with different optional features enabled.

At the rescue prompt, if you type ls by itself, it shows (md/0)?  But ls (md/0)/ shows no results?

I do notice that your raid partitions are tagged as Linux instead of raid.  That might be the problem.

---

### Post by YesWeCan on 2011-02-05
I can do this successfully, or something similar anyhow.

In Ubuntu 10.10 32-bit running in VirtualBox.
I created two 20GB virtual disks: sdb, sdc
I created a single partition on each, ext4
'sudo mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sdb /dev/sdc missing'
'sudo mkfs.ext4 /dev/md0'
'sudo mkdir /media/raid'
'sudo mount /dev/md0 /media/raid'

then I copied my root fs to the raid
'sudo rsync -var --exclude=/media --exclude=/dev / /media/raid'

then I did your exact commands in post #1 to chroot to it, then
'update-grub'

then looked at /dev/grub/grub.cfg and it looks correct,
```
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 0eff2efe-45fa-4e13-87fe-a379f5c6abed
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=0eff2efe-45fa-4e13-87fe-a379f5c6abed ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}

```

I don't think I can try to boot it because I am in VB so I didn't bother with grub-install.
I am curious as to what exact steps you used.
BTW what is the partition structure on your raid drives? Do you have more than one partition on each?
How did you copy your root fs to the raid?

One thought I had is that the mdadm install might not have been copied properly. Wild guess. But you could reinstall mdadm in the chroot context and then update-grub again and see if that corrects the problem.

---

### Post by parsim on 2011-02-05
> **psusi said:**
> At the rescue prompt, if you type ls by itself, it shows (md/0)?  But ls (md/0)/ shows no results?
That's correct. "ls (/md/0)/" produces a blank line and nothing else.

---

### Post by parsim on 2011-02-05
> **YesWeCan said:**
> 'sudo mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sdb /dev/sdc missing'
'sudo mkfs.ext4 /dev/md0'
'sudo mkdir /media/raid'
'sudo mount /dev/md0 /media/raid'

then I copied my root fs to the raid
'sudo rsync -var --exclude=/media --exclude=/dev / /media/raid'

then I did your exact commands in post #1 to chroot to it, then
'update-grub'

then looked at /dev/grub/grub.cfg and it looks correct,
Yep, and that's what I did, too, both this time and the last time, when I successfully built an array. This time I think I accidentally formatted the filesystem ext3 first then went back and redid it as ext4, but otherwise that's what I've done. The exact command for copying data is:
```
sudo nice ionice -c3 rsync --verbose --archive --delete --update --one-file-system --human-readable --progress / /mnt/raid/
```

> BTW what is the partition structure on your raid drives? Do you have more than one partition on each?
See attached RESULTS.txt.gz above. The two RAID drives each have a swap partition.

> One thought I had is that the mdadm install might not have been copied properly. Wild guess. But you could reinstall mdadm in the chroot context and then update-grub again and see if that corrects the problem.
It didn't correct the problem, but it produced a warning:
```
# sudo apt-get install --reinstall mdadm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/240kB of archives.
After this operation, 0B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 341271 files and directories currently installed.)
Preparing to replace mdadm 2.6.7.1-1ubuntu16 (using .../mdadm_2.6.7.1-1ubuntu16_amd64.deb) ...
Unpacking replacement mdadm ...
Processing triggers for ureadahead ...
Processing triggers for doc-base ...
Processing 2 removed 1 changed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Setting up mdadm (2.6.7.1-1ubuntu16) ...
[B]Generating array device nodes... /var/lib/dpkg/info/mdadm.postinst: 170: /dev/MAKEDEV: not found
failed.[/B]
 Removing any system startup links for /etc/init.d/mdadm-raid ...
update-initramfs: deferring update (trigger activated)
update-rc.d: warning: mdadm start runlevel arguments (2 3 4 5) do not match LSB Default-Start values (S)
update-rc.d: warning: mdadm stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (0 6)
runlevel:/var/run/utmp: No such file or directory
 * Starting MD monitoring service mdadm --monitor                        [ OK ] 
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-25-generic
mdadm: md device /dev/md127 does not appear to be active.
```
From my Googling, though, that's harmless. More interestingly, the new /etc/mdadm/mdadm.conf it produced has an md/0 in it!
```
# cat /etc/mdadm/mdadm.conf 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/0 level=raid5 metadata=1.2 num-devices=3 UUID=98ab8ad1:23e4df2e:d8bb3605:b9be0e1f name=eve:0
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=c45843d4:a0418d21:00706633:8bce23f2

# This file was auto-generated on Sun, 06 Feb 2011 09:11:09 +1100
# by mkconf $Id$
```
So I took a look at /proc/mdstat:

# cat /proc/mdstat 
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : inactive sdd1[2](S)
      204804544 blocks
       
md0 : active raid5 sda1[0] sdc1[1]
      968576000 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [UU_]
      
unused devices: <none>
```
That "md127" on /dev/sdd1 is a leftover from my old RAID array. I don't know why it's md127 and not md/0 but it seems to be the same thing:

```
 # mdadm --examine /dev/sda1 /dev/sdc1 /dev/sdd1 | egrep 'UUID|/dev'
/dev/sda1:
     Array UUID : 98ab8ad1:23e4df2e:d8bb3605:b9be0e1f
    Device UUID : 56b64914:fa4f68bf:a9dbe8f9:68e1b477
/dev/sdc1:
     Array UUID : 98ab8ad1:23e4df2e:d8bb3605:b9be0e1f
    Device UUID : 3af9a379:9b51803a:4e261ec4:3aa28cdd
/dev/sdd1:
           UUID : c45843d4:a0418d21:00706633:8bce23f2 (local to host eve)
```

I think I will destroy /dev/sdd1 (which is useless anyway), reinstall mdadm, and see if that helps.

---

### Post by psusi on 2011-02-05
Now you seem to have two different arrays, one of which is using format 1.2, which grub can not work with.

---

### Post by parsim on 2011-02-05
> **parsim said:**
> I think I will destroy /dev/sdd1 (which is useless anyway), reinstall mdadm, and see if that helps.

After that, /etc/mdadm/mdadm.conf dropped the line for the old array, leaving just the existing one... but it's still mapped to wrong device:
```
# cat /etc/mdadm/mdadm.conf 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/0 level=raid5 metadata=1.2 num-devices=3 UUID=98ab8ad1:23e4df2e:d8bb3605:b9be0e1f name=eve:0

# This file was auto-generated on Sun, 06 Feb 2011 10:02:34 +1100
# by mkconf $Id$
```

I tried manually editing that to "/dev/md0" but it makes no difference: grub still sets root to "md/0". Which doesn't exist.

```
# ls -l /dev/md*
brw-rw---- 1 root disk 9, 0 2011-02-06 09:45 /dev/md0
```

---

### Post by psusi on 2011-02-05
I don't think the version of grub in Ubuntu supports metadata format 1.2.

---

### Post by parsim on 2011-02-05
> **psusi said:**
> Now you seem to have two different arrays, one of which is using format 1.2, which grub can not work with.

I don't think that's been the case since grub-1.98+20100720-1 ([link](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=492897)).

I read some information [here](http://linux.derkeiler.com/Mailing-Lists/Debian/2011-01/msg01115.html) that got me thinking my new RAID member superblocks needed to be updated. So I did this:

```
sudo mdadm --stop /dev/md0
sudo mdadm --assemble /dev/md0 --update=super-minor /dev/sda1 /dev/sdc1
$ sudo mount /dev/md0 /mnt/raid
$ sudo mount --bind /dev /mnt/raid/dev
$ sudo mount --bind /dev/pts /mnt/raid/dev/pts
$ sudo mount --bind /proc /mnt/raid/proc
$ sudo mount --bind /sys /mnt/raid/sys
$ sudo chroot /mnt/raid
# mdadm --detail --scan
ARRAY /dev/md0 level=raid5 num-devices=3 metadata=01.02 name=eve:0 UUID=98ab8ad1:23e4df2e:d8bb3605:b9be0e1f
```
Yay! No more md/0!

However, grub STILL thinks there's a /dev/md/0 somewhere. :(
```
# dpkg-reconfigure mdadm
runlevel:/var/run/utmp: No such file or directory
 * Stopping MD monitoring service mdadm --monitor                               No /sbin/mdadm found running; none killed.
                                                                         [ OK ]
Generating array device nodes... /var/lib/dpkg/info/mdadm.postinst: 170: /dev/MAKEDEV: not found
failed.
 Removing any system startup links for /etc/init.d/mdadm-raid ...
update-initramfs: Generating /boot/initrd.img-2.6.35-25-generic
update-rc.d: warning: mdadm start runlevel arguments (2 3 4 5) do not match LSB Default-Start values (S)
update-rc.d: warning: mdadm stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (0 6)
runlevel:/var/run/utmp: No such file or directory
 * Starting MD monitoring service mdadm --monitor                        [ OK ] 

# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sdb1
done

# grep 'set root=' /boot/grub/grub.cfg 
set root='(md/0)'
	set root='(md/0)'
	set root='(md/0)'
	set root='(md/0)'
	set root='(md/0)'
	set root='(md/0)'
	set root='(md/0)'
	set root='(md/0)'
	set root='(md/0)'
	set root='(md/0)'
	set root='(md/0)'
	set root='(md/0)'
	set root='(md/0)'
	set root='(hd1,msdos1)'

```

---

### Post by YesWeCan on 2011-02-05
Some progress of sorts! Well, you might do worse than to start from scratch and erase both drives completely so as to remove any raid ghosts. Like use disk utility to create new partition tables and a new ext4 partition on each.

And, of course, disable any mobo RAID stuff in the bios.

BTW, I have a RAID10 and I installed Ubuntu on it on an LVM partition. I created a SWAP partition in LVM. I reckoned in the unlikely event that a disk failed while the OS was using swap space it would ensure the system carried on without crashing. If the swap space is outside the RAID then I presume a sudden loss of swap data will cause the OS to have a crisis. I mention this in case you want to make a raid then LVM before you copy your OS over.

Also, make sure there is no raid superblock stuff on any other disks.

---

### Post by parsim on 2011-02-05
Yes, given I had it working earlier on a different array, I suspect I could fix this by wiping everything, zeroing superblocks, and starting again. But I don't really want to copy all that data again, and I feel like it should be fixable, dammit.

I've even tracked down the line of code in grub that's causing me grief. I just don't understand it:

[http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/maverick/grub2/maverick/view/head:/disk/raid.c#L584](http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/maverick/grub2/maverick/view/head:/disk/raid.c#L584)

I might file a bug against that and see where it gets me.

Really appreciate the help, thank you both.

---

### Post by psusi on 2011-02-05
It looks to me like it is using md/0 instead of md0 because it is 1.x format.

---

