---
title: "Cleaning up partitions after reinstal"
date: 2013-08-23
forum: Installation &amp; Upgrades
---

### Post by hanlie-pretorius on 2013-08-23
Hi,

I had to reinstall Ubuntu 12.04 after some system problems and let the installer install over my old installation without interfering. Curiously, it warned me that I would lose all my previous information, but now I see that me previous Home partition is still alive and using up 5GB of the 20GB that I have available for Linux on my dual boot machine.

fdisk -l gives:

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *      206848    30926847    15360000    7  HPFS/NTFS/exFAT
/dev/sda2        30926848   584179711   276626432    7  HPFS/NTFS/exFAT
/dev/sda3       584181758   625141759    20480001    5  Extended
/dev/sda5       599805952   615428095     7811072   82  Linux swap / Solaris
/dev/sda6       615430144   625141759     4855808   83  Linux
/dev/sda7       584181760   599805951     7812096   83  Linux


sda5 and sda 7 (7.5GB each) are my the partitions where linux is currently installed and sda6 contains my previous Home folder.

Could I merge sda6 and sda7 and so create more space for my new installation?

I would prefer something like that to having to do another reinstall and manually edit the partitions during installations.

---

### Post by TheFu on 2013-08-24
Wouldn't it be easier to just mount the /home in the new installs /etc/fstab?  
Having the OS+Apps split from the /home is a best practice for a good reason. You are experiencing that right now.

However, if you want to merge the storage in sda6/7, you can delete sda7 (losing all that data), use a boot gparted disc and extend sda6 into the freed space.  If you don't want to lose anyhting in sda7, back it up first.

BTW, it looks to me like you have 7.5G total that is shared by both those partitions.  To me, it seems you have lots of opportunities to improve the partition layout, if you so choose and can backup almost the entire drive.  That way, you could expand sda3 to include your Windows data partition, which will give you much more flexibility with the logical partition storage available.

Lastly, if you can post with the "code" tags, things like the partition table output will line up nicer. It is in the "Adv Reply" toolbar.

---

### Post by hanlie-pretorius on 2013-08-24
Thanks for the reply.

I see now that my previous post wasn't clear.

The new install has created a Home folder on sda7 and my previous Home folder is on sda6. sda5 is 7.5GB and so is sda7. sda6 is 5GB.

So perhaps I should just reinstall again an intervene in tne installation process to tell Ubuntu that sda6 is my home folder; then I can split root and swap across the remaining 15 GB. Or is there another way to reassign your Home folder?

---

### Post by TheFu on 2013-08-25
> **hanlie-pretorius said:**
> Thanks for the reply.

I see now that my previous post wasn't clear.

The new install has created a Home folder on sda7 and my previous Home folder is on sda6. sda5 is 7.5GB and so is sda7. sda6 is 5GB.

So perhaps I should just reinstall again an intervene in tne installation process to tell Ubuntu that sda6 is my home folder; then I can split root and swap across the remaining 15 GB. Or is there another way to reassign your Home folder?

sda5 is marked as a swap partition, you couldn't have installed anything there.

If you get any of the partitions wrong, you might make the system unable to boot. Be very careful and very clear.  I'll assume you are 100% correct in your words and that sda6 really is your HOME and not anything else. If that isn't true, this can be bad.  If you want to check, please post the output of 
```
cat /etc/fstab
```
and
```
df -k
``` here.

You can mount any partition (with a supported file system type) almost anywhere you like in Linux using the fstab. The file format is easy to understand and fully documented in the man page. $ **man fstab** will display that.  Most people like to look at examples and google has thousands of those. You want a line like this inside yours:
```
/dev/sda6 /home         ext4    defaults      0       2
```
After you make the change, run
```
sudo mount -a
```
to get it mounted.  Any files/directories stored under the old /home will be hidden as long as that new mount exists, so you might want to move your HOME directory files in the new storage somewhere else if you can't live without those or don't want to waste the space.  Might be easiest to use a temporary mount for sda6 ... /mnt, then move the files from your HOME over, then mount sda6 under /home. Your choice.

Long term, you probably want to go with a UUID-based mount in the fstab, but get it working this way first.

---

### Post by hanlie-pretorius on 2013-08-26
Thanks.

Here's the output you asked for:

```
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=a953f291-c379-4b7b-b08d-8d4a05249ce5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=72bef3c5-c558-4781-b448-10d0ffe44d8e none            swap    sw              0       0

```
and
```
$ df -k
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda7        7786712 3299036   4097072  45% /
udev             2036592       4   2036588   1% /dev
tmpfs             817552     888    816664   1% /run
none                5120       4      5116   1% /run/lock
none             2043876     108   2043768   1% /run/shm

```

---

### Post by TheFu on 2013-08-26
Well, sda6 is the only place where you might have other Linux stuff. Mount it and see what is there.

---

