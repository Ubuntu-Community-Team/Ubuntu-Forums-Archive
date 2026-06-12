---
title: "Trying to set up RAID 1 Ubuntu 10.01 Server during Install"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by luapyeltrah on 2010-05-24
hi -- I'm doing a clean install (booting from a install CD) using Ubuntu Server 10.04.  I have two SATA hard drives that I'd like to mirror using RAID 1, so I configured my hard drives for RAID using this web page as a guide:

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

I have partitioned my disk into one physical partition (a 100mb /boot partition) and 6 logical partitions (2 gb, 5 gb, 5 gb, 7.9 gb, 200 gb, 280 gb) -- the HDDs are 500gb apiece.  So 7 partitions.  I had no problems setting up RAID and finishing the Ubuntu installation.  However, when I rebooted after completing the Ubuntu installation, GRUB2 never loaded, and I was instead presented with a message that there was a degraded disk.

I ran cat /proc/mdstat and got this output:

md4 : inactive md6p8[0](S)
  7713728 blocks

md2 : inactive md6p6[0](S)
  4881344 blocks

md3 : inactive md6p7[0](S)
  4881344 blocks

md0 : inactive md6p1[0](S)
  96192 blocks

md1 : inactive md6p5[0](S)
  1951680 blocks

md5 : inactive md6p9[0](S)
  195311552 blocks

md6 : active raid1 sda[0] sdb[1]
  273543104 blocks [2/2] [UU]
  (resync data shown here)

I'm not really sure what is happening.  Did I try configuring RAID with too many partitions?  I tried running the command mdadm --assemble --auto=yes --scan, and was able to start all of the inactive md's, but only 1 drive out of 2 started.  If I reboot after this, I come back to the same issue as above -- most of the md's are inactive.

Might anyone know what's up?

thanks!

---

### Post by intel on 2010-05-24
> **luapyeltrah said:**
>  md6 : active raid1 sda[0] sdb[1]


 Tells me that your entire disk has been allocated to only md6

 it really should read
md6 : active raid1 sda3[0] sdb3[1]

 i.e some partition number allocated for md

 In your case the entire disk is allocated when you don't mention [1-n] part in sd[a-z][1-n]

 Here's my suggestion,
do the setup again....

 /boot on 1st primary partition unencrypted ~200MB
swap on 2nd primary partition encrypted RAID1 (2X RAM) for hibernate)
/ on 3rd primary partition encrypted RAID1 ~10GB (4GB installed + some space)

 4th primary partition into extended partition

 in the extended partition :-

 /tmp 5th partition  ~ 10GB encrypted RAID1 (even RAID0) as it's recreated   (note:- if you have enough RAM, you could setup /tmp as a ramdisk for faster fs)

 /home 6th partition rest of disk space RAID1 use ecryptfs

 Note: you may also set a separate partition for your installed apps

 I would also suggest a small /home and a separate partition for your big media files. As fsck eats time before you are allowed to login. Also remember to set internal checksum like so
# mdadm -G /dev/sda7 -binternal

 so that fsck goes lightening fast.

  -intel

---

### Post by luapyeltrah on 2010-05-25
hi - thanks for the note.  I actually did try installing RAID using 3 primary partitions and then the remainder logicals, but that didn't work either -- same type of issue.  I don't need to use encrypted partitions.

One thing I've started to notice is that sometimes when I'm configuring RAID in the Ubuntu installer, some of the md partitions are missing the "Software RAID" annotation, and instead have "Unknown".

Do you know of instances that would cause a HDD to be assigned to just one md partition, as you suggest that this could be the cause since md6 says it's using sda[0] and sda[1] instead of sda#[0] and sda#[1], where # would be the partition #.

I wonder if the Ubuntu installer is doing something incorrectly behind the scenes..

---

### Post by phroggelator on 2010-05-25
I have almost exactly the same problem. I put in two brand new disks - ran the alternative installer, partitioned the disks as I wanted (3 physical partitions, 3 logical) and built the md devices. I swapped over to the busybox terminal the second time I tried this and verified that the 6 md devices were assembled correctly and that the UUID's of the devices matched what was in mdadm.conf. Now I admit I was assuming that this mdadm.conf was the one that goes into the initrd file and that therefore it would have the correct UUID's all around.

However.

When I attempt to boot the newly installed system directly, it bombs when it tries to assemble the MD devices. When I check the mdadm.conf it's using in the initrd it has entirely incorrect UUID's and mdstat reports that the MD's are attempting to use md5p[1-5] as part of the mirror. Unfortunately it also thinks they are the sizes of the partitions they should be referring to and as such they add up to more space than is actually in md5 in total. This makes me think that whatever portion of the installer that is assembling the mdadm.conf that goes into the initrd is borked and generating a bad file.

I also note that when I restarted after the first attemtped install, although the partitioning of the actual disks was still correct, the md device info was quite wrong (I had to completely wipe both disks for the second install attempt to clear this). This may be down to me attempting a mdadm -A --scan to see if mdadm can get the correct data - it didn't, but it did try to rebuild stuff so this may be why the md devices were borked when I retried the install disk.

Has anyone actually done a successful RAID-1 install on Lucid Lynx?

---

### Post by luapyeltrah on 2010-05-25
> **phroggelator said:**
> 

I also note that when I restarted after the first attemtped install, although the partitioning of the actual disks was still correct, the md device info was quite wrong (I had to completely wipe both disks for the second install attempt to clear this). This may be down to me attempting a mdadm -A --scan to see if mdadm can get the correct data - it didn't, but it did try to rebuild stuff so this may be why the md devices were borked when I retried the install disk.

Has anyone actually done a successful RAID-1 install on Lucid Lynx?


Interesting -- I've re-tried the installer 3 times in total, and at one point the lowest md was md2, when there should've been a md0 somewhere.  I also ran into weird things such as when I pair, for example, sda3 and sdb3, it appears to work, and when I go on to create another md, the partition list is showing sda3 and sdb3 again, even though I just paired them!

I am not yet well versed in working directly with mdadm.  Did you happen to devise a workaround, perhaps by manually editing mdadm.conf?

---

### Post by phroggelator on 2010-05-25
> **luapyeltrah said:**
> Interesting -- I've re-tried the installer 3 times in total, and at one point the lowest md was md2, when there should've been a md0 somewhere.

I suspect parted reads the partition tables and then (assuming it sees them allocated as type RAID) it tries to read the RAID info from the disk partitions. Once it has this it will only create new MD's with numbers above the highest it found. So if it finds md2 then the next md it creates will be md3 even if md0 and/or md1 are missing.

>   I also ran into weird things such as when I pair, for example, sda3 and sdb3, it appears to work, and when I go on to create another md, the partition list is showing sda3 and sdb3 again, even though I just paired them!


I haven't seen this behaviour from parted. What I see is that once basic disk partitioning is done, I select the RAID option and move to "create an MD", I choose two devices with no spares and select the partitions for the device and it just works. What you describe sounds quite wrong - the only thing that leaps to mind is that perhaps the type of the raw partitions hasn't been set to "raid" correctly. Perhaps investigate this from the busybox shell the installer gives you on "alt+2" with one of the other partitioning tools if they are available (cfdisk, even fdisk - though cfdisk would be better).

> 
I am not yet well versed in working directly with mdadm.  Did you happen to devise a workaround, perhaps by manually editing mdadm.conf?

I try to stay the hell out of mdadm.conf if I can. Even under Debian it never worked right for me. My previous install on the old disks was a debian/testing setup and I had a custom kernel with the MD stuff compiled in. This worked just fine, but the debian kernels never booted as I could never seem to get the mdadm.conf correct (it all looked fine by every example I could find and the man page, but even so...)

What I really, really do not want to have to do, is go old school for the RAID build. Installing normally on one disk, then building a broken mirror on the other, copying the installed data to the mirror then boot off that in a degraded mode and redo the first disk and assemble that into the broken mirror...... Too much like hard work and a bad flash back to working for an ISP for my taste.

---

### Post by phroggelator on 2010-05-25
OK, now I have had a bit more of a play around. In fact the mdadm.conf file is completely correct. If I use mdadm --manage -S /dev/md? to stop and destroy each broken md device, then use mdadm -A -u <UUID> /dev/md[0-5] where I grab the UUID's from the mdadm.conf, each md device assembles correctly (true it complains about settinghte user and group, but I can ignore that for now). 

Thus it seems like whatever the initrd file is doing (or the dmraid kernel module?) it's completely ignoring the mdadm.conf and trying to do it's own thing (and getting it horribly wrong). I'm going to mount up some of the newly assmbled md devices and check their content to make sure they are OK (I expect they will be) and report back further.

---

### Post by phroggelator on 2010-05-25
Indeed, it appears o be pretty much what I thought. The newly, manually  rebuilt md device mount perfectly and their content is as expected (ie the freshly installed Lucid). The problem appears to lie in what happens inside initramfs. It *looks* like a script is run inside /scripts/init-premount called (strangely enough) mdadm. This script essentially runs the command mdadm --misc --scan --detail and this command returns a non-zero exit code (and obviously totally screws the md assembly).

I just don't know why. If anyone has any insght as to why this fails so badly I'd like to hear it. Otherwise I guess I'm going to have to rebuild the initramfs with a mdadm command that doesn't use --scan - hope fully the tools required are part of the default install (and therefore I can just mount the installed partitions on the disk and go direct) and I wont have to use the rescue boot on the CD.

---

### Post by phroggelator on 2010-05-25
More information: It looks like I jumped the gun in blaming /scripts/init-premount/mdadm. The problem has already happened by this point (removing quiet and nosplash is very informative). According to the boot log, the wonky RAID stuff is already inplace before the mdadm --misc --scan --detail ever gets run. So it looks like either the "raid" or "dmraid" module is at fault. 

I'm done for tonight, but I'll poke about more as time permits. Any good ideas are welcome.

---

### Post by darkod on 2010-05-25
As far as I know (and I know little about raid), for software raid you need to create /boot outside the array. In other words, not a raid member.

Are you guys doing that?

I agree it makes little sense, because if the disk where /boot is goes down, you are left without a way to boot. But there must be a way to sort it out later.

For a start, can you try with /boot on one of the disks and not included in the array?

Recently in a VB I did an install with the alternate cd, not the server cd, to play around with software raid, and it worked straight away with /boot outside the array. But it was only a quick test so I didn't bother to find a way how to protect he system if that disk goes down.

PS. The rule about /boot outside the array seems to apply only for raid0, so it shouldn't be needed for raid1.

---

### Post by luapyeltrah on 2010-05-25
> **phroggelator said:**
> More information: It looks like I jumped the gun in blaming /scripts/init-premount/mdadm. The problem has already happened by this point (removing quiet and nosplash is very informative). According to the boot log, the wonky RAID stuff is already inplace before the mdadm --misc --scan --detail ever gets run. So it looks like either the "raid" or "dmraid" module is at fault. 

I'm done for tonight, but I'll poke about more as time permits. Any good ideas are welcome.


I decided to do a rescue boot off the Ubuntu install CD, and when I went to the busybox shell, I looked at the boot logs, and it appears that all the md partitions were successfully mounted!  If I do cat /proc/mdstat, it shows all the md partitions as active, although one of the partitions was missing (not being shown).  So this is in contrast to trying to boot the server and only one md partition (the last one) being successfully activated, while all the other md partitions seem to be getting linked to the active md as spares, even though I never specified any spare drives.

Certainly sounds like something is misconfigured somewhere...

---

### Post by phroggelator on 2010-05-25
I'd have expected the rescue CD to work as this is the kernel/initrd that it was assembled under in the first place. The issue is the kernel modules that go into the initrd installed on the disk. One of them is trying to work stuff out itself and getting it horribly wrong - which is why in my case it tries to tell me that md5 is in fact composed of sda and sdb as a whole, rather than sda7 and sdb7. When I tried my last boot after removing the quiet/splash options from the commandline in grub I did notice that whatever module is causing the issue keeps trying add new devices (composed of md5p[0...n]) until it runs out of space on the device. 

It looks like my next step will be to boot from the rescue CD and try to rebuild initrd so it only loads the raid1 module (or at least loads it first) in case one of the other raid personalities is grabbing stuff first (raid10 I'm looking at you in particular...). I tried this from the mounted disk partitions after I recovered the correct MD devices, but of course all the library paths were wrong (no real surprise, but it was worth a shot) and I suspect initramfs wont like it if I mount them over it's own equivalent directories.

---

### Post by luapyeltrah on 2010-05-26
I am essentially having the same problem you describe -- the last md partition (md6 in my case) is the only active one, and all the other md partitions get md6p[0..n] assigned to them, as you describe -- those are "spare drives"...

You understand the boot process better than I do.  I did a quick google search on "ubuntu initramfs raid 1" and saw a couple older threads (not on 10.04) regarding a failure to boot that seemed to be related to things being out of sync during the boot.  Do you think putting in a delay during the boot (as these guys did) would help?

[http://ubuntuforums.org/showthread.php?t=1163519](http://ubuntuforums.org/showthread.php?t=1163519)

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/79204](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/79204)

---

### Post by phroggelator on 2010-05-26
> **luapyeltrah said:**
> I am essentially having the same problem you describe -- the last md partition (md6 in my case) is the only active one, and all the other md partitions get md6p[0..n] assigned to them, as you describe -- those are "spare drives"...

You understand the boot process better than I do.  I did a quick google search on "ubuntu initramfs raid 1" and saw a couple older threads (not on 10.04) regarding a failure to boot that seemed to be related to things being out of sync during the boot.  Do you think putting in a delay during the boot (as these guys did) would help?

[http://ubuntuforums.org/showthread.php?t=1163519](http://ubuntuforums.org/showthread.php?t=1163519)

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/79204](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/79204)

I be keen to try this as it's a lot less fiddling around than what I was planning to do. I'll let you know.

I'd be less trusting of the launchpad URL, as that issue is quite old now and looks to have been partially fixed by an update, but the one for the these forums is a lot more recent and is what I will be trying.

---

### Post by phroggelator on 2010-05-26
After a bit more reading I skipped the rootdelay option as this is required when it takes the kernel a little too long assembling the root md device and it tries to mount before it's ready. In our case this isn't what is happening. The MD devices *are* ready, they're just wrong.

I did however successfully manually boot the system once I had the correct MD device established - of course then a video driver issue hangs my system, but at least it booted. What I did was, after is drops into the initramfs shell, remove the broken devices with mdadm --manage -S /dev/md[0..n] commands (obviously you need to remove the highest device last as this is a dependency for the other devices. Then run mdadm -A --scan to assemble the device correctly. mount the root device on /root. Then umount /sys and umount /proc. Finally run "exec switch_root /root /sbin/init". 

This will cause the initramfs shell to chroot to /root (where the proper root device is now mounted) and then run /sbin/init which will complete the boot sequence. Of course, this only really proves that the system is otherwise correctly installed and doesn't really fix the issue. Because of the video driver issue I'm stuck booting into the rescue CD to try and rebuild the initramfs file so it doesn't load the dodgy module, or if it has to, it rebuilds the devices correctly.

---

### Post by luapyeltrah on 2010-05-27
I hope you get this figured out -- I had to move on to an alternative non-RAID backup strategy -- I'd try RAID with another distro, but I'm not the one who's deciding what distro to use (this is for my job).

---

### Post by phroggelator on 2010-06-28
Solved! Well for me at any rate. It seems that the tools surrounding the MD stuff in Ubuntu are less than perfect and there are several threads here and there across many years that indicate this. There appear to be two main things people are saying that might fix the issue. Unfortunately they didn't for me but the solution is still related. All changes are in the mdadm.conf.

First is setting HOMEHOST in mdadm.conf. Apparently the hostname is used in setting the UUID, which is fine, except that while the system is still running from inside the initramfs, the hostname is not set and thus it doesn't recognize the UUID's as something it should auto-assemble. I set it HOMEHOST to "" as was recommended and reassembled the initramfs, but this did not result in a clean reboot.

Second is changing the auto option on the CREATE line in the mdadm.conf to "md" rather than "yes". Again after rebuilding the initramfs and rebooting there was no impact.

However at this point I reviewed the content of /proc/partitions (as used by the initramfs) and noticed that /dev/sda came up first. Given that the default DEVICE setting in the mdadm.conf tells it to scan /proc/partitions and assemble stuff based on what it finds there and /dev/sda is listed first and the borked result was that it assembled /dev/sda and/dev/sdb into a MD device with subpartitions....

I reset the DEVICE line to have the value "/dev/sda? /dev/sdb?" and it then booted normally. Whether or not the earlier two changes are required I'm unsure as I left the earlier two changes in place.

---

