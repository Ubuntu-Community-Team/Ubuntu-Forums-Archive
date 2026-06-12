---
title: "About to Install 14.04 Trusty Tahr Over 12.04 LTS Need Advice"
date: 2014-08-16
forum: Installation &amp; Upgrades
---

### Post by LaughingHorse on 2014-08-16
I have been running 12.04 LTS for some time now, and am ready to install 14.04.1 Trusty Tahr.

I'm running a dual boot system
SDA -Winblows
SDB - Ubuntu

My Ubuntu hard drive is configured this way:

(Primary) New Partition #1 NTFS 100 GiB
(Primary) New Partition #2 ext4 30 Gib (for Ubuntu Root)
(Extended) New Partition #3 Extended 1.69 TB
(Logical) New Partition #4 Linux Swap 16 Gib (My Computer has 16 GB RAM)
(Logical) New Partition #5 ext 4 (My Home)

Yes, I will be backing up my data before doing a fresh install of 14.04,

Here is my question:

If I do a fresh install over 12.04 is there anything I need to worry about?
Any tips from anyone who has done this before.
It will be my first time doing an install this way.

Thank you in advance for your help and insight!

---

### Post by ajgreeny on 2014-08-16
To give us more info can we see the output of ```
sudo fdisk -l
``` from your current 12.04 install, as it is not yet clear on which disk those partition reside; I assume sdb?

As you have two disks did you leave the windows bootmanager on the windows drive and put grub on the second drive where your ubuntu is sitting. That would have been the best way to do it, but if you didn't, it may now be a bit too late to change, depending on which version of windows it is and whether or not you have the windows install DVD.

Whatever your situation I would strongly recommend that you use the "Something Else" option for partitioning when you get to that stage as there is a bug in the installer of 14.04 which can wipe out a whole disk, ie all partitions on the disk, if you ask it to replace a current OS.

---

### Post by LaughingHorse on 2014-08-16
Thank you for your reply ajgreeny!

Right now I do have a WD Passport plugged in as I am backing up files.

Yes I left the windows bootmanager on the windows drive and put grub on the second drive where ubuntu is

The windows version is 7
I only use it when there is a specific thing that will not work with Ubuntu. 
Like for instance when I upgrade my Samsung mp3 player os. etc.

Here is the output:

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd7329376

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848    48383999    24088576   1b  Hidden W95 FAT32
/dev/sda3        48384000  1611192319   781404160    7  HPFS/NTFS/exFAT
/dev/sda4      1611192366  3907024064  1147915849+   7  HPFS/NTFS/exFAT
Partition 4 does not start on physical sector boundary.

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00010172

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      503807      250880   83  Linux
/dev/sdb2          505854  3907028991  1953261569    5  Extended
/dev/sdb5          505856    64503807    31998976   82  Linux swap / Solaris
/dev/sdb6        64505856   264503295    99998720   83  Linux
/dev/sdb7       264505344  3907028991  1821261824   83  Linux

Disk /dev/sdg: 1000.2 GB, 1000170586112 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953458176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00023f15

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1            2048  1953458175   976728064    7  HPFS/NTFS/exFAT


I don't understand what you mean "use the "Something Else" option for partitioning when you get to that stage"
The drive is already partitioned. Do I need to do tht again?

---

### Post by grahammechanical on 2014-08-16
Something to watch out for is the fact that the installer will put grub into the MBR/UEFI of sda by default. If the Ubuntu disk is sdb then you will need to re-direct the installer to put Grub into sdb.

See the third image in this link - Installation Type. Note the bottom option - Something else.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Regards.

---

### Post by LaughingHorse on 2014-08-16
Thank You grahammechanical

Since the disc with Ubuntu is already partitioned, do I need to re-partition it?
If so, wouldn't that wipe out the data I currently have on it?

Regards!

---

### Post by ajgreeny on 2014-08-16
We need to know before you do anything else which partition out of sdb6 and sdb7 is your current /home, so show us the output of command **mount** from your current OS.

Now start the installation and when you are in the "Something Else" page you will see all your partitions listed for both drives.

Ignore the Win7 drive sda completely and select your root partition for ubuntu, which I think is sdb1, and choose to Change (or is it Edit, I can't remember). Now choose to use it as an ext4 with mountpoint / (root), and select to format the partition in the tick-box.
You can ignore the swap partition as it will be found by the new OS, but from the other two, sdb6 and sdb7, your old /home should be selected, and then choose to use as ext4, but make sure your /home is again given mountpoint /home and, most important, that the format tick-box **is not selected**.  You can ignore the other of those two partitions and we'll deal with mounting it at boot, if that is what you want, after the installation.

---

### Post by LaughingHorse on 2014-08-16
Thank you for your reply ajgreeny

What command do I enter in terminal to display the output command of mount?

---

### Post by ajgreeny on 2014-08-16
> **LaughingHorse said:**
> Thank you for your reply ajgreeny

What command do I enter in terminal to display the output command of mount?
Just ```
mount
```

I also forgot to tell you to make sure that in the box at the bottom of the Something Else page, you put the bootloader files in /dev/sdb, note just /dev/sdb, **not** in a partition such as /dev/sdb1.

---

### Post by LaughingHorse on 2014-08-16
Thank you for your reply ajgreeny

/dev/sdb6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdb1 on /boot type ext2 (rw)
/dev/sdb7 on /home type ext4 (rw)
gvfs-fuse-daemon on /home/allen/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=allen)
/dev/sdg1 on /media/My Passport type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

---

### Post by kansasnoob on 2014-08-16
Beware this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by yancek on 2014-08-16
The 'Something Else' option referred to above is one of the installation options which used to be referred to as 'Manual' or 'Expert' and is what you should use as you already have partitions and this gives you much more control.  The other standard options are 'Install Alongside' and 'Erase Disk' which you don't want.  Your mount output shows that your Ubuntu install is on sdb6 which is where you want to install the new Ubuntu.  What you need to worry about is that you have no problems with the installation so make sure you keep the installation medium in case you have problems.

---

### Post by LaughingHorse on 2014-08-17
kansasnoob Thank You.

---

### Post by ajgreeny on 2014-08-17
I managed to get confused and got your partitions wrong in post #6, as I did not realise that for some reason you have an ext2 boot partition at sdb1 of about 250MB, a huge swap partition of approx 32GB, a root partition of around 100GB and finally /home of approx 1.8TB.

Does that sound correct?

Can I ask why you have a separate /boot partition?
 It is not normally necessary for a desktop system and can cause problems when you have a large number of kernels which are not removed as new ones appear in updates; the boot partition can quite easily fill up stopping any further kernel updates.

It will be very helpful if you could get a screenshot of a gparted window, showing sdb, as it will give us a lot more detail of disk and partition layout, and as you are now re-installing I would recommend that you get rid of the /boot partition and just use root, /home and swap, but I suggest that 32GB for swap is overkill, and unless you really must hibernate the system, I would suggest 2 - 4 GB for swap.  Getting Ubuntu out of hibernation is hardly any quicker than a cold boot so I think it is pointless on a desktop system, though could be of use on a laptop.

Sorry for the confusion; it was that /boot partition that did it, and I did not look closely enough at the sizes showing.
For future posts when copying code from terminal output lease put the text in code-tags (see my signature for how to do that),as it makes it a lot easier to read.  As an example here is the fdisk output that you showed for /dev/sdb,this time in code tags: much easier to read isn't it?
```
Device      Boot     Start         End      Blocks   Id  System
/dev/sdb1      *     2048      503807      250880   83  Linux
/dev/sdb2          505854  3907028991  1953261569    5  Extended
/dev/sdb5          505856    64503807    31998976   82  Linux swap / Solaris
/dev/sdb6        64505856   264503295    99998720   83  Linux
/dev/sdb7       264505344  3907028991  1821261824   83  Linux
```

---

### Post by LaughingHorse on 2014-08-17
ajgreeny Thank You!

"Can I ask why you have a separate /boot partition?"
Probably misunderstanding on my part.

From past thread when I first installed 12.04
"For the Total space you want for Ubuntu - my standard suggestion:
Ubuntu's standard install is just / (root) & swap, but it is better to add another
partition for /home if allocating over 30GB.:
Ubuntu partitions - smaller root only where hard drive space is limited and if total
less than about 30GB just use / not separate /home.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3) format"

I do a lot of multimedia editing (video and sound) so I have a need for a big swap.

My system does have 16Gig of Ram, and from time to time I still do run out of memory.


It is a lot easier to read and understand with the tags :)
I will do my best to keep this in mind and use in future.

How do I get a screen shot in gparted window?

I have not yet started install.
 Can I open gaprted while Ubuntu is active, and use screenshot?

Regards!

---

### Post by oldfred on 2014-08-17
You can use gparted to only view your current install, but it can be used on other drive. You just cannot change the mounted partitions which you are running gparted from. So I always install it in my working install to edit other drives or view my drive, but if changing working partition have to use live installer. Best though to use Windows to edit its own partitions.

Screenshot is standard so if Unity just click on top icon to open dash and type in the line screenshot. If a menu system like gnome-terminal it is in applications, accessories. Attach to a post from the Advanced editor with the paperclip icon in top edit panel.

Have you installed a lot of applications. And then exported a list of all installed apps to make it easy to reinstall. While settings for all apps will remain in /home if not reformatted, the actual app will not be reinstalled.
       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

---

### Post by LaughingHorse on 2014-08-17
Thank You oldfred!

You are the one who helped me when I originally installed 12.04 and set up partitions!
Anyway, here is a screenshot of gparted for sdb

[IMG]http://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAA YAAAJICAYAAADsAf4NAAAABHNCSVQICAgIfAhkiAAAIABJREFUeF7snQdgXNWV/r pkmY06l2WZBX3XgBjMMUYTA8QIGRTIH3JLsmG9La72c1mNyHJ/pMQkgABUsjSAphAbFNtigsY3Ltl2ZKt3vv0/zn3zZNGoxnNqFqyzzXDzLxy77m/d9/offece69hka3U7wcn r/2n/qsbVM7Ap Dt2jb5f9CQAgIASEgBITAxBH49i/ BcbELDgcDiQmJsJmsyE Ph5msxkmk2niDJGShIAQEAJCQAgIgTElYGYJHlDmSo7rklwX6yLHx5S3ZCYEhIAQEAJCYMQEenudMJh6lBA3Go0qH6/XO D7iDOXE4WAEBACQkAICIEzRsDMolwX5CzCNaE UJaLOD9j10cKFgJCQAgIASHQR6CruxsGdMFgMFCnul JcpfLpbzlulAXXEJACAgBISAEhMDUI2D2Bcly/iM/QKSr75xEmk 9SysWCwEhIASEwNlGoKOTRLnXCp/PB4/HA6fTCavVKsL8bLvQUh8hIASEgBA45whQKLsPvoAgZ5H 6z//5zkHQSosBISAEBACQmBqEvCS2T2a6dKHPjUvoVgtBISAEBACQoAImFmUsyC//8//oYBccfMnpigYw7jZPX45j5vJ/RlPaeMngE/MRQjImFEN88BxJzvuBQyzwoMOn/QGDrJYNggBIXAuE5gCPUDjaOI4Zn0uN6qgugvhMWkIUxTj Jo9vrmPxXVToewsyi 57naVn9vlHIt8JQ8hIASEgBAQAkJACAgBISAEhIAQEAJCIAYChpefedS/6trbYjhUDhECQkAICAEhIASEgBAQAkJACAgBISAExpqAmTP0 31jna/kJwSEgBAQAkJACAgBISAEhIAQEAJCQAjEQMDQ1dE2ooB7nsGdZ4T10VIt/Nk3CcW90WCEwWiAkZaRMZvMankZSUJACAgBISAEhIAQEAJCQAgIASEgBCYTAVrHfPjeco/bDbfHjZ7WRjhb6oCWWvidvTDExQOpOYhLzUZCckbM9XT2dMHV26PGt3voZbbGwUIva3wC4hLsY5OPzQ6L2QKzxRJzfiM 0O F18MdFkaYrNQhMOKMxvjEQXZRhwp3rtCyOwZzHEzGMS7vbMtuEL zrYJSHyEgBISAEBACQkAICAEhIATOBAFDR1tzzB5z9oy7XS50NFbDVXkA6a4exNscMCfQK84Gj7Mbnp4O9HZ3oMmaAGvhXNjTciLWq6erA90d7UhOS4cjJR1WEvYWixVutwsuEvodrU1oa26CzZGEBLtjTPKxO5JJ9FvHwHvuh5fq6vL4SdTaqQMhIMBJvLlbjmH/vuOo68nG8ssWIi1uLMV5hHIj0gnsGGTXAqQYOnFq3x5U1HQgadlqLMqynV3inJcBpE4HCpmg6x0NUJT9g/iN9XWNUr7sFgJCQAgIASEgBISAEBACQuCsJTAsj7nL6URrTQUsFXtQlJoLQ7wd/t4u JtqSEz3ApZ48nbHw5GUgUTyE9ce3o624kVIzikaBLCzvRVuEt9FM fBRKHmXo8LbvKa95JYN1HYuclsQnp2PlIyclBVfhBerweJSSljkk9SSpoS5yNP5GnuacCeR36Ah3b3In7xP L7n16C5Hgasu/pQcfBp/Hgn8qBtCsxY8UcpFrHyhUdudxoutMfatcFs5DoPowXHnwMB72JWFG4AvMz4mActYINosoeZupk8bq9NNQh0P9jMMHIkQtWC5XlI1zUmeMN7hsywMDXnzpozOZRcPO70NvShMaGdlimlSLLxkMZRnHFQ/mN6XUduV1yphAQAkJACAgBISAEhIAQEAJTn4DZ74vNYe4hYdzRWAPL8d3IzSyg8PXT8DWdVt5IGsjdR4JD4/0 L4xp cjNmIaa47vQaYkb4DlnT7mPwuFLZi2kkHgnerq6 kmSOR6vG6TmABLuHM7Ox1Uc3ovuzo4BnvOR5tPZ3oaklFQY2faRJL8H7o7j2HqQOiNgw7wLi2HnOHBiqevPfiA0uV6MjKOaMlS5UU4eZFe444n9mNnqo6iHluN477WX8fYHh1DV6qISDYhPnYbSBRfj6usuRoG5Gm/c/1Osqwhaos/iQHbRbCy9ZC0uXVSAxLgRXCPi5Kp/B/f/259RgUys/eZ3cG2RY1TRAIP4jSWrcNdCtgkBISAEhIAQEAJCQAgIASFwzhCIyWPO0l2NKz/8LgqSUoGqA/A1nNBEuZEEaZAwJ2VHAtUHX3sDDF1tyMwsQtWR92C/4HoVPs7h8B3kySybtxguV6/ympMcVMD7ugjog 7cdPX0wB/nR35xGY4f3IMEG/nixyIfux1WGsc kuT3utBZ/g4Os9a0LyBvsw3skXY6w43XZ7HO23k8N3mP1dhz krMjGbdK0z7nD3w8GEmGltv1cSo303j7ilUHkYLLHE0Nj603CIbDOQZdve4uU9AJYORvM0UDUBz3rHK1jzW3vB2aWfo/6cQ d5OeIm8QY3FH0X4PQljZ917eOIXj2JHa3ApfvJiV2H/e4dx0dUr4Te60dnWL8rZZp 7A3XH3sP6Y7tQftu38LlL8mGlOnoJjt4 VB1prgCjVkk6h/ZTHbltBSDQG9W9r2jyzFPdPEYrcdTrNdT1CJwYhd9I5mcYyFy CQEhIASEgBAQAkJACAgBISAEABLmfXI4Ig8vCe3epmqkkNgxttbDe qgEuVtvS609zhRkJlOipBUFeV1uqkFCRYT0mzx8NNxJgptTyUh1UPedVtmPniit7SsHCWieMK3/jTQDu2bUpfqOJ4ELi0rl5zoXTSu3R42n0d//xCJ/SDva1DuX7j7nwfmQyHUPJ59 IkEnbsdR7ccAfn04Vi4Avnecmz6wzN4bdcpdPqsSE7pl4Rsv59Cun3d9dj/6l/x4lt7UdPlhyWlGEuv/DBuvKgEdn8Dtv3y3/FEhR/xS76If71rAeyGHpx66b9x38YGIPcmfPura5BtGljutHg3Gt5/EU//jToJGqneBisceUtx6xc ikVpFvjajmDzXyPZFdQRgk7s tN/YkdLBzymZEw//zrcftOFyHfQWPxhAyI vY3Y9fTjmig35uLC227DZfOnIdnsQltNOY615qHMQZ0P3CcTSJlXfxtfvyob6DiGVx96AC fcuPIpvdQf54dHX/7DZ54rwqtvdzBEIe0kmVYc8vNWFHsgNF5Gtueexbv7K/A6eZuaqF0RM4qfPbTFNWhUgM2/vir2Mgfc2/Gd75GHBOM8A9xPRzcMULXzNM6FDrtHvnYAR8iYEhIAQEAJCQAgIASEgBISAEIhIICaPOXte3aePI42ErPfkYXKfk6uYPOUtXT1Y9 5e3HzePBRkpKC6uR3PvrsP1y2fT Oq2f1JXsvaciQULUA7nY MfPR0diK3sJg88Oxu1oSN n84kUNZ6MLQ43bCkZyKmsoKxJNID5cPj0v/8j3fHFTZB39zf19ZwfnYaVK5YSceN91 GFuPeujUZCxabsOuP9yHdeo79XTEedHWOlCY 5ytOPLs/8NDW1roCBNsiSZ0t1Zg 9O/RLv1u/jM UmYsZyEZEUlesv3os45G9NNrSjfT6KcUtZiGqduIY92a1C55 fD3Lwdjz/2OkjPw jIoOvTg9Y2F IsBvhctdj22P1D2qUyD6ReEuVmHgvvasOJrX/BA54kfOsfFsAx3PHxLGhb9mLzAb6 QMGHPotbLsymGfF5AjbqeLCnUHA5LWHH/ThB5fNHA0UQcIfFssVZJMxrgc5GdPkosqCHJgH0WImbEa7ObjQf34KnHrYg7zsfRqGnHru37EeVQm6GxUTeel8SDS3oz9xsT4LNZIAlLQEmssFP1 PwUNfjggyYPHVR YnHPOQCylchIASEgBAQAkJACAgBISAERkQgpjHmPO7Y191Ga4EbSBzWk CmgGfykBdlpuHma67Gc s3YGVpPrYdr8b1a9Zgepwb/s5WzaPY1gAzCXR/T5sSYuzRNpPAZ895VI8jiXVdvHlpeba4BBtcJNAj5kM7eNz5oMT5BIT/gHxGMvbb50b7oXdQzq7ZlCVYYt2DJ5Uod D8z30Tt82xo/v9X DfHj hmcHh0E3v40UlynNw9dfuxZo8E5q33I//eaYCBzftRsvSy5A663wUoBJV7Qewr96FAvsx7KQh/NSbgcULMii0wYO2oHLPy4ujTo9aaHPqF Kme76MizJM5Oj1wxhngKf6fWwayq4BkOxY/sV/xUfLTGh45wHc99fj6PzgdRy9cQ4Wp1gGeM391CkzAJuBJ oLmqSNO3FaKtGk8s/A7LIUGttN /kaeDpRe7wS7V4j7HllyB0QsEBtzNWJ1tr9eOtdEuWcHNlwmBOQ9dH/wH0f8dAM/p3obduFP/3iBRqzfgTlrR4UJuoVoQnsvvSvuG26hcLeSeT3vBfYkYkr/vlbuCqbJuajiedMJj889dGvR3JDdH5jNh5fr4K8CwEhIASEgBAQAkJACAgBIXBOEojNY05S2ECTsRlYoNOSaDw moU52puQb0vGhcuX4vUt23HJBctRaOqBt41FOSlXVtAkqE00Y7ufRBGNMCdN71HOca9X8ypzPg/ 9oGwIdN8 uf/8YtKVPPLShv8tO52pHyGuoJ6HsH5DN/jyeKyDQe2VKiqpS49DxntL2oiNH4GlpXQBGPkqTVRKH9/8sNZfxA1akMtNvz0G9gQbGhbLdrdfqSnzsOKomdQdbIJe/Y3YmX6ezjJhWRdgCWZPL68eUC5OSS zZkLMS9lM7a0VuLZH30P2xZehMuvvAJLC2xwNx0f2q5AR4VmCuVl5tnQrUiftxy5JMxPeRvVhG2LkqgugbAFv7cTBx78Lh4 2B8RYJ73j/jBZ cpj7RKKl9 6YkvGo8Pp389J7D dw9gN0Xdl9z1I/zT3P6jGjb8D745AEw85l1JfKkWe59/DE 9dQLU8oISzbru7h93ru8wmGg8vpk6Q4JHSVAFDHRhtNEWvhiuhw 2WPipekkSAkJACAgBISAEhIAQEAJCQAiMjkBMY8xZmPloAjJ3bzON4aUvJLa1tadoSbRTVdh2oAqrzluGd3fuRvacAuQn28gqFmQk6EkoeXq74bfROHQWSDQ2ndcp58m6 BgW5l 69xua0A pC4voro42ioinvKhYPk/NAh8hHyUJuUxWYIGkBDl95o6A0Hx0L3pIsUN8pXDyln3YphRzBpYvy4a5NVCWzwO16lc4pdYn4FKxYNVipAfpdoO9FCkUeg5TCuauLIXxZDkadmzFdsdxNV46d8USpLMubwwplxnYy3DzvV9G7isbsGnLYVTveRWP79mD6n/5GtboanoIu0JNVZqaj1cEKH/iGBsj7jjRsZHIT6Zl7uhrNxpx8FgbrsqzqhnRQ8vTzwh NyekIWf6HCy7dA1WzkpBz54H8TiJcrcpHxdcuwrF1mpsfvZN1FBm4fLrt5fsVxmTbRyxoRuorpEuqCNcD qk6OuNiMhP6ywKVwfZJgSEgBAQAkJACAgBISAEhIAQGA6BmDzmSuLYE9HTUQ rOY685tqsXTWdvXjxcDWuvXQVChIMyEu/DOteewPXzcqlicMSyA4Oq6bx4CzkaTZ1mkJchbH3dHdQjkYSyhQST2HOvKa5kd5ZCOpikIWUj2d3Z2FN77y0WU93pzo/Uj5cHp8Tmg9v5wnsQvMZtsecxk 37NuKKiaceR6WZNGYZnMZjZk gFrXIWz6oA4lF2YN4m9JLyUZfxB16IIznSYuu3gaEowUUt3ZjE5rOlIovJpIwTH3Msy1lmNfw2a8zMPLjaW4dEkaTBTG3hRSLs867vd0odNQgAtvvhsXXluFl3/ MzqvnjzuTbhyeTS7wsha8oifeOctzbsfNw0lqRT zeXohxoSMOfzP8PPgk/lThAet92vzGFMXYCVxevwTIUPp9Y9gnW2j2LNwnwK9tc6SQYBYpyByd9Un4VS1Pw/D5rrmtQke8hdiSsvXYFU9xEcfJGEefg5/uhAzV6DxYYEzszbhqp6itjINVOYP3U5UDRD1OthpvaSEZ3fsNsP10OSEBACQkAICAEhIASEgBAQAkIghEBMY8x5pq649Hy0NdUgIz6RlkKjEcQkyKzxNlxz6cXI99Fs3nWtyKJJtm5YfSksvMY5jcVWHnM6vt1qR3x6Huk3A2y0TFlHSwscKenkAXcrQa5eHGqsvLTqNHqRKGdhHnhZaT3r9pZm2KmDIFI fN6Dv/tNwFOq1ZQFo5mW/ Ll3jiv4HyGPUbYS2Hm29TAb2SfvwQ0pBvGjPNx7bLX8cj7nTjyzI/wrRfiYaXQ/eDEx1yz5A08trMLR57/Kb73vBlmgwcevxXzP/8f NRsmsGeT7DPxKXLHNi3VRsnH79gNeYl0QzinoZB5bLt7sqX8PNfvIOexFSkxFOnQSNnYkJqFi0FF4Nd/TZ2Ytuvv4 dcMKp3OUG5KGmXUtxKVkbpYwbWlz8Y0nHfHh7H3f5/G4d7TePvxn9Ir5JgIX1VWff8zIamoAAnUpdFz6mn8/CfbkZXQi qIopzOJS7qdGsuFhQYceiEGwf/8H18N94Md/wFuOdbt9JEhdGvRyzXNSqbCHWUzUJACAgBISAEhIAQEAJCQAgIgWACMXnMyd0MW04hTtHM6klxNI6axpX7OlqQEmdFqquFPL9tWp5tzci208RvFvKG93popvA09CTnwEVrmSfnFrA/GwkkzJsb6mh2bgedYyBxTmPGSY0bjXQ8TxIWSJog1zyxJpOZlkmjdb5p4riE9PSI dz1mS ota0HhbKTUmturKfx38H5ZNAkYcoXG2OisO7GXdDmJcvDBYvSYVQh0TbM/ci9 HT689i4dT9Od/TCRfWKS8rCtNmaZ9xvSMT8j34Vn8lap4451c6i3AhbeiGJe44K0NcZt6LossuRu/UF8lqnY WamSRKiVrYcskZ7E9Adno8ymmJusZO0sOJuZi/8gbcskjzTUe1i8Lny YVoL68Bk1dJMqJRFx6GZZcfgOuX5EdqF MeEIOM2asxKe/mYUtL7 KbXvLUdepzVoPaxKy8mdgQSZ5sEOzDjNm21p6Cz5zgxfPvbEHp srcYLPsTqQNW0WcnnZs5A8uENHbTOkYvnHP4navzyPrcdbqf14YKOeFA8L95iuRwzXNShKILQq8l0ICAEhIASEgBAQAkJACAgBIRArAUNN5bFQbRP2XPZod9ZWoqNiP/KO7oChrY5mam8PeyxvNNqT4U/KxOnZFyKtbAGJovy Yztp3HhHaxuS0jNVCLSHJ3RjcU6TyumJxarm7TarcPf2xlqk0PEJtIa5nkaTT1wcheSTBz3mROHaDRv/B/e9TG7pabfgu/9yMS2W1o/OEJgQTxvXrOWqvP5B4m3wMVqY/kAruJOCwvopCz F vuGLJejDfSx1Fym1pExdJmBaARll9aJYQwakx8uj5gZDTpQy18NLQjeR2Wr60tb9bryuuFqjH6YNJgbHRQmD8VrwPlam qvnjbUQS9mcL6Dr8fgY4L5hTFWNgkBISAEhIAQEAJCQAgIASEgBIZJIDaPOWXq9fjgIK 5z9WLSprQLaNiJxJqK Dn5ctoxnZSuWptc4ORhHRcAroypqGxZBmS6Rx7ei7l0K 6HLR OHurWxtqkeCg5bTIk 0jr7yXxlLriQURizaX00lj21uR6HDAZgtMKhc4aKT5xMfHU2fA8LzlRl8dPtihYsVRsGI iXKt40C3N5bxxrEcw/npM9azcB66XGIWvGS6bkzQe7QyWZ8Po3siTAlDb4rmVO6va R8otVhqDy8JPgjpWj58nmxHBMpf9kuBISAEBACQkAICAEhIASEgBCIhUBsY8wDOfE47eSCGbAkpaElJQttFXuQVFsOa0czLYnmhNcSBxeFr7fnlMJXvBAZWXmwp2ZQ6PAAf6nKLTk1HWZrHHnOW0nT00ze5ME2kkDXJ3/z0XrZHhLlRpokLSUjQ40tD dQHW4 NhoXz/WIbbbxQMWpk8BbuwPvN9N3QzEunJvM6jmsPbFAj/mYM1VuzAbKgUJACAgBISAEhIAQEAJCQAgIASEwWgKGU8cPhtO7Q ZrNltJRBvQ0ViH9uY6OLu74KH1yc0krOMo1DwpLRuO9GwVgh4tsUDu6uhAV2cHemkcOc czufFxyfQRPAO2MlTHjxmPFJ UfNJctBKYN5hesqDSjPQDOwW6jgg/7KHlm3jFdwmJJ2pciekclKIEBACQkAICAEhIASEgBAQAkJACBiqyg MSGKyWDaZzSrcXI0ND MVP N4A OQeSy5l8axD8tLfsaNFwOEgBAQAkJACAgBISAEhIAQEAJC4FwgEPMY81AYamyyK/L43dDj5bsQEAJCQAgIASEgBISAEBACQkAICAEhMJjAsMaYDz5dtggBISAEhIAQEAJCQAgIASEgBISAEBACoyEwYo/5aAqVc4WAEBACQkAICAEhIASEgBAQAkJACAgBjQAJ8xENMRd QkAICAEhIASEgBAQAkJACAgBISAEhMAYEDDTjGhjkI1kIQSEgBAQAkJACAgBISAEhIAQEAJCQAiMhED09cxGkqucIwSEgBAQAkJACAgBISAEhIAQEAJCQAjERECEeUyY5CAhIASEgBAQAkJACAgBISAEhIAQEALjQ0CE fhwlVyFgBAQAkJACAgBISAEhIAQEAJCQAjERECEeUyY5CAhIASEgBAQAkJACAgBISAEhIAQEALjQ CcEuZGQxfKt7yO104Y4BsfnhFzPZNlRzRKdgiBc4iAydCJfeufxv/t8sJ7DtVbqioEhIAQEAJCQAgIASEw QlMemFugAstlcdwtMWI0c4fb6YH852vvoFt1d5R5zXcSxtatslXgxd 8gP8 wtNcBqMGMt6Dse2UDuGc 5UPvZsr3ek9hRa71iPm8rXWrfdZOxFxQd7cLjJO Edc2cDP6mDEBACQkAICAEhIASEwPgRMMeStcHdgN2bN GVdw/iRIubTrEgKa8Uiy 5HjcuS4XN2I29f/hf/GZPd192FkcOyhaswJorl2FmYiylhD/GamzC of/gJPX/Se cQFgCn/YhG41m3rw3i9/hEdODC425 Yf4FsrjVHttMQ7kJaTi9wMO6xmE6zesa3nwUf/HQ cWomvfu96TDe4Bhhqqt Ab9 3A6Vf jHuLuseYAfcEx1LMJghC6iB7cmAuNQ8lM5ZgosvPR/z0wzUkTG6FMr/TNR7cD3pzhrn ya03pHaXehxZ4KPfoX77jfLF3Df3cWI9/JvkJZMFX/EFx9w4uM//AouiOuM2ijOfOuOaqIcIASEgBAQAkJACAgBIXAOEogqzI2uSrxw/0PYWJOG auvw6dL02FxtqO qhyn3TZYLWYYfH70tJEoz1mLL318Lmw F9pqDmHzi8/jV/vq8E/fvBGzrZ4R452MD9Nedt/nXo0v/cNs2HSVSJ5vW3YGjP7mqHV1eZNx9T3fwlVeD7o72wGKXRjLes67fA4sv34fW6pvwPT8YHNcOLV1N9oS5uHyYiNcHsdAO6JaPv4HGAyB9pR7FfGdiwRvD5qry7HzrQ14cMsWXPiZe/CR2eaonR9DWTqI/1AHj9O vnpO4H0zqN4R2t2g48aJQazZqvvNHykAfSzvnFgtkuOEgBAQAkJACAgBISAEhMDYERhamPudOPXykyTKc3DDd7 DDxUAXjd5X kh2bxyFcxmK9pbGpQbW4WZJxZgemE bH4fTKWlWFrixdf 6028cepmzCl1of3dJ/DT5w imR241nTMufRmfGzNdCQb/TAaunF44zo8994xVLXyATbMu/O7uGehVtnqZ76Pf3lG zzr7p/hn0u6YfC24eAbL GZzQdR12uEo2Ap1n74elySb9I8qu4m7H75RTz3zjE0uU1IKSyCmZxqQ1d6GHDt0zC9aBoSfMGCoQMeduhFKdvkb8RzxPStRd/F99fGIy5QbLh6DsOivkPjSy/Ggvh92LW1Grfclol4uiacLL46vPFBJxzLLkOBoQcm30A7LHRMJK6rpxtw8i//jR XX4rvfGs1cmmYgRVV P33HkTtLT/EV5fSdaSW4Nn/KO79YxxeOPjcR0dY5qT/ZCxdfm96NsxixcfMWleP2XP8Qf/vgkZn7vU1huc0W09YpiA8r/ CP8tPIKfOcbl5CtfFF8cO58GF97Ohlf/vEtqAjir rt68Txt9fjqdf34lSXH6akYlz5 btxXbYzYjl9bW2ENZ3oYrZadjanehx2l8OnD0zfV45o29OE39cPa8RVj9oQ/hihKL6iQxGbuw 7mn8PzuU6jr4HvYAHv Yqy97WZclj/6KIdYEEdqu3ydQhPbu/f5Z8jeStS0s71mpBYvxRU3XItVBSbuK5MkBISAEBACQkAICAEhIAQmhMCQGtVC46A3bm1H/NKPYU2uBz0dXX1GuZw9YQ30ejxwU6ip2 VEnMFKQe8m4goWVE vw1 FjetUix dC0bwP 8MIf8FTxv OzM0gEGZyo2HkAddnX4 67ypDk6wUKkums06qc9Cvuxj0Xp8NMXum4tHigtxmnNjyCX29Lx/WfuBdLUjuw54U/4ZkHgezv3YrZ5jac Nvv8fC2eKy45VO4c5oFLUfewbOVYyjMyS6urycotFYZ6OqWwKNBiUBtXT2T88YNDBQ2xwm/Jx5dJEfPDBJlTe/A YaXKqoz2n38Ou7hSsuqwEJneL5qkPtsPfG5nr92/D3KXTYXz3EE65rkSularaUo5yyrr9QA2cy/KQ4O9B7f4a PNvGMK62Hf1tyeosfiXfuRKrP/XF/H6QSeWLnWiJlIbYFvPpzq vxvHe6gTIcFNnT/cxqphLLocRVY3ygfU24Xa1x/Fzzd6sPymO3F7iQOetk6KgEigSrZFZsJtzdIfWh17zQYeOWH3DZkaU7sLPY466WpeeQS/eBVYcevncMc0Pyrffg5P/ a3cH31X3B9jpfuVRdOHzqO1vz60Mq1AAAgAElEQVQb8U9ri2DtrcUHLz2LZx80IY84zRotJ/KYe7z86veQ 5QrPZCGartU/sIQbc72Vh08hmay94t3FSLOWY 9r/8Nz/yyCt3f BKuyRx5lM9I24GcJwSEgBAQAkJACAgBIXBuEhhSmKO7DtXkSMpdUAxDbwwCUT04kzDv7UJH40ls/dsbaDQUYW0R YPpodmQOh1zk/hh14/iq25G1dYf4c0jHXDPoHHWait54QoWYc70JFgNBhiNpPgCw6Pj0vKRnhIIX/a0w g5geffasOcT30bNywywUdu6uI7b8D7316HrbV3YEF2BV7Y1oFpH/4qPrU6FX63E5ZSO3lE9 PwWF3rYw/j6/cGZRa3HPf F4lg1/4Rlx1az0jBu9Gq4HEbMGPNhUjbsglvnvBhRilr8F4cf cAerKuwMVZlLOm1QdkZRmKa80dWFK4CIV4FrtO 7C82IeO44fRQoLZd2I3GvzTUYIafHC0F9mXzotm4rD3 8nr73cUYho1lsOV7TAsrIncBsjWpUXLUGp8HDuo5 DC RQt4K3FlnIfiu6g8HgXRXoEJbOb2tNr9cj90Pfxuasz4evtgdHESs4Jf8fQbW12wSiF QTeN5Ggh7a70OPMLmLwRiNyiM9dqzMoIsSJBbP Ea7K/8JLG0/i8jsLkRI4yTZtAWYVJyHOVIR52S3Y8x9bsLPZjFnZo RU/ii /fVQy/j7NLVxyLZLvwkLp4c7l2Jz8hdQRE8y/eZMx JF9Fv3vR/j1Y1VuOzj UgY0wEm4cuXrUJACAgBISAEhIAQEAJCYEhhbtRjOQ3koaJwYj0ZDF60bHoYP9k5B//81bUk1ALe85AHZ1P6HNz4pU/iIocTXqcb9TtfxNMv78SRmlb0mhJgIdFtcXlgIGEXnDwULq8P247Td1H5XhUjriVjG4Wfkves7eGv4wsDzqY82zzwxVM4rT8J581Mg6urTR1hMI5SGISUA/IKf NT8ynoPmCTNQmp3AdRP4qyQ oZWmSs3/2Ujz99OS7LfQXrNh1BBw0tSHdX4uU9Lky/9SKkevqjHwbkGY1rWQnOy3Pj77vq4KEQ5vKdzSi44UZYNr6DA60GlJiOY19bGpYuTKVsaez8GCdvn7fUD0NH1ZBtwFVSjEtKDXh06zF0zi D6dQHOOQpwu1z7TD46wda1laBKhpvv2xeJlwdWntR0e ULFGYgIZ4jCpN5H0TKT479P4KPa79BE55k7BsbgbcXdp19fvjsWB2Itbtoc4Z6pLRhTmzUPcw8UuwZSOVOoRae0c7XR9lStE299IcFglBWfUc/j/8/PkA/SjXKUyASt9l4wgfTj6fHctn2fHK4cNoNRRTBAhF7kgSAkJACAgBISAEhIAQEALjTGBoYZ6YjXRyGp442gjnvGRQAHlf8vV2oqOtCyqSVH9Q5gfnT8xDojUejrQsZDgscHV3wOXshal5K 5/ZBOMl3wUX7yzmB7W6/DyAw/j/RFWkBzq5GGPx7LP3osPF/EIWC2xyLemJJEI4zGtfnrQHqnPOQbDErKRk5mOeF9/yKuPQvyNxgkoOwbzXF47Lrl6Bp5/7FXs75mN5cdIPGMmPrc0mWLwKYw9TIrG1e1yY l5WXh603tovGEWtp9KxnmfWA777pfwGkU/rDLtQV3yAizNoIYRiHYIU8yIN/lbj6OS8k2fTsMauPNhiDbgc3qwePUsGB56C0d7i5Gx7TDcJbdgbgJlEBKlzNeMpD7NLzY4fDkaE/Q0jbg 6sQJvG9Gaijz4eQPup84/N6o4NBAlb5evIEl I08Vpvuw74fiZFaQOfZ8jAtP2fA/YYO7hbTOgajXSeDqyZq4V4PheRzoATPycBVHkrNR81NDhACQkAICAEhIASEgBAQArERCPWLDTjLaynA6oXx6Nr2LN5r7Re/fFCQA73/HH5wziOxmmqjmbTb0UkTw7Eo5 RtrkAtinDtDStRlulAZlYm8nVX85C2mpBARTu7XAOCSk0pRcgx9KKShqDb7HFIDrySbBbEO1tgTitFnqkD /c26o7PIUsZ6U4vCTn25OsvDrceWdnh6zlSu/g8Hn btHANlsRV4tV3DuONl48jYdlazLGGnx Az4nGlXVZ5tLzkN22G5u2bcUx20LMT07EvPMzUb/1HWx pwbJy1Yiexw8jQZvM7Y9uxmN5pm4cqEDlihtwEeDqRNmXYKF1uPY/MF vLLXh3lrl8HmHuwFVfU2tuPQ4dZQzR6VyWiukTp3Au bwbbG1u7M6Xw/MZ 2Pj4miojYc6gD5vwypBknZmb00PstuD7R2q5 rN8X2VaToR0HjnbBlFOC1Amq0 BrIluEgBAQAkJACAgBISAEzjUCQ3rM3W4zlnz0o1h69FE89ZNf4eRVq7AoP5F8lF2oPBV zLl6cA7jdYzPKkY6XsOGl7YgflEaks0dqB sjwbx95lSMTPXhE1vrsPb Rcin8RZZ/pirCiajQ9dnIL71v8aj/ivxUU0WZeltwX1zkIsW0re1PgZ PDqTPzwpV/iEc/1WFXqQLz7FGpiKHOQEZE2dJ1G XET4oK8iIa4dJSWzBp22ZHquTQ7soiIZFbwdpdxGq5flYofbHwEf0MGbrx7Fsw06VskR6DPPjRXjprwpyzAxbkv4a/r2pB 9c1I8/bCvvA8ZDy9DuuRhms lU9hzOE98rHY3HdM5ymUl9Ma7 4emrOgEnu2vo33axy46At3YWlCD3zG6La6TdNw9Xl2/Oi5J2nVgPPx1TJyh3oC3tAgY3z2Obh5VQp /Pwv8Uf3ddS bDD1tMGVtwzLcqKXM6x6hTl4ou6b83MHFh6p3YUe54mjnyDPzw QfwhPF6rMjxoPa9v P5ukxc 9nFtLY4hf PQbR6GDQxb4rWdpMMCaA QzTvexeHll6MpVla1i3vv4hX0haiNM2P vc34Lm6JFz2yflUp/C/cTEbJAcKASEgBISAEBACQkAICIEYCQwpzHmcstM6G/f851fx8l//hjc2PYXtXSwUjUhIzcbsJWVI5rDPGLSjP ty3PPRVjz64hO4f5N2gtWegRk5tiGf5z0eKy6482PY9 un8ezDe2hK9RTM//B8LM41Y/7Hvo57HE/guTefxG82UJ7GRBRccDsWLs9Rs8KXfvhefM3 DJ55/Wn8hmbb5vnYEzNLcH5eApUZZuazGKH1HVazHr 9P SkjGvx/e9cPuyyI9VzafaQQQ1RLfa4/ShcvRbFrz6Bk2VrcVEaTWbWG0mWU/Q5YRmKazx1Qri8ibhoTTHqd2XLgih0R4M3zJc7Eqfx2e9K3CynQKFR9NGLvBBFsSzYa dwN2utitaUPJTNuxZf qcrMD/VC2d3F1wUuxzNVp4Er3TNKmS99Xf4Ll6DIloiLlxyOf2Yc8fX8SX7E/jrpr/gN7RcGuIyKUx/MZUXnUm4PMdi21jfN8tp2bLgFKndhR7ndvmpTX8F/xL3BJ5a/yi2E0Zb7gLc9OWPYW2OCx5uU2dYmEdru16/A5fcuhrvP/I6/rp9GRZ SLu3jOZ27NvwONa3 2BJm4ErP/dx3DSdfta6Y/hhG4uLLHkIASEgBISAEBACQkAInPMEDBUHd0ZWaQE8JpMZcTY7zBYrjSXV1hzi8aU 8oz3dnfSpGpGJCanqaM7WpsGTNKmEzaQiLLG2xBHL222aw6H96nlxrraKfTcEgd7kjZ9VGtj7YALw Um2B10Hvcj0DrZLhd6aAIq7jhIsCfBbNXs4vw8breyiUPLucx4WyIscfHKbj7ex8st0YzSPV0dI774bI9e33CZdLVTODSVMVTZFhqHH1rfcPXs6mgNV8SwtsUl2BU/rn97c4PirqdwdjC3objyuVx/ttfZ06VY8jVNSs1U2fLa9sx5pMlktsDuSOlrJ5yPum4elxLkwREZsdgaT2033uZQ7bW9pVGZFXO9qa11d2qTwUVjMtz6BrejibpveFK2hMQkZap n4Vrd GOC2XN14SvvdulhaGEY8rM4hJs6j7vaNXYjyWnpLRMdW87e7rVb0KojaG/Cdb4BMQnJKq21dV8EC/ 98/xzuLv4id3FCCetnGduE07Y1mFYrgVkeOFgBAQAkJACAgBISAEhEAEAjEJ8wjnymYhIASEwJQlYDG29Anz76 Nx8BZNKZstcRwISAEhIAQEAJCQAgIgSlIYHRx0lOwwmKyEBACQkAICAEhIASEgBAQAkJACAiByURAPOaT6WqILUJACEwYgXCh9xNWuBQkBISAEBACQkAICAEhIASCCAw5 ZuQEgJCQAicrQR4bHzofBZna12lXkJACAgBISAEhIAQEAKTm4CEsk/u6yPWCQEhIASEgBAQAkJACAgBISAEhMBZTsDQ3dkedVb2s5yBVE8ICAEhIASEgBAQAkJACAiBKUiAV2ThNVu19ylYATFZCAQISCi7NAUhIASEgBAQAkJACAgBISAEphwBIy3ZXFdbi4rj5ejqHPlSyFOu4mLwWUlAhPlZeVmlUkJACAgBISAEhIAQEAJC4CwmQJ7yhsYGHD6wHzPnzkNGZhb8fn/Ac 6nz Hrzv71CLvCnyBbhcC4EOAoD2qLgYbKn0WYjwtoyVQICAEhIASEgBAQAkJACAiB8SLAoevlRw9jxpw5iI PR3t7GwW0a4mFt/5ZyXB/kByn8zQtJPJ8vK6N5BuOQKBF0ptBNcCAMFfdRNwm/SLMw2GTbUJACAgBISAEhIAQEAJCQAhMXgIszDvaO5Camo6e7i7SNiRufLrY9sPHppMgV15J7RtLIfrCe7Ttk7d2YtnZRED3iquIDmN/x5Ae1aFFeogwP5uuudRFCAgBISAEhIAQEAJCQAicMwS8Xq8myEnhKHET8Dyqd/pnZEmuqx dSsB53i/izxlcUtEzSUB1EFHi9qiHdGgblFXceiWU/UxeIClbCAgBISAEhIAQEAJCQAgIgRER6PNE0tn8mf/xfz5NAql3Xfvwu9GgCXgVOjyiEuUkITACAkGdRkb2mHNkB4dy9EVwqMYZuzDv6OjsG5weizkms0mN9zDRbImShIAQEAJCQAgIASEgBISAEBACY0eAQ4IpLD3gLdeENn8Hep0unKquQU9PN3wkgtizPtTL5/Op/brQZxtNJiOSk5OxcMF82O32sTNbcjrnCGjRHFRtaqtqtEUgisNAHUUc0aGCOGhHzB5zzpAbZyzJ5XLRTeBDd1c34uKssFqtsZw2qmP4Zupsb0dHWztcbid8HjWyBEazEVZLHBzJSUhMSqKbzDSqcvSTW5sbkJkzDW6Xc0zym hMRmN/fUMDNR5tfE6f3TyRgWpWWlKdQEHfeTmL9PS0Catmeflx1QY5cdmlpSXjWvZoeI6rYZK5EBACQkAICAEhIATOQgJKzOiiPPCujR8HTlRW0djzVPXcn5ubC4/Hg66uLnU8PxfqyeFwqG1OpxNut7tPmMfFxaGxsRGsad5/fydWXbzyLCQoVZowAizEOZSd331atAbPkaAGX1DnklJVtD9mYa4broudcBXhwlgg9/b2IjExURXe20simd7jqYGPR2J7mpsa0dLYhASbDfEJCUhKSaabThPgPp8XLuo1a29rQ0NdHVJIHKZnZAaWUhgPi87 PL0eL7Kzs4dVUV7OYqKT3pHU2dmpRHrwD/FE2yLlCQEhIASEgBAQAkJACIwtASXMlbwhvcOihxI/p7IQT0tLU3pk9 7dKC4uRhI56DiaVwmiIDHeRhqBBbjuSOzp6VF6JisrSz0/njx5Eh63C2bzsGXT2FZWcpuyBJQgp4kIVXtVAp0dhzwBoeYx92sezdiFucqQkv4eSkZv5KpAerEIslgsqkG7XW5lAd8MY5ncdBNVnTgBE90o6Zma2PbRjeSkzgAqMFCUQVU8kXrE7PZEdHZ0oL21DQXTpyv7pmrq7e1BfW2t jHKzs5VHRITlfia8jVupwiFWBL/EI7nBBunKivpx1jzjrM93FT5B5rL5dRB17yKjgm0ebXNaDBiWmGh jxZEzPm 2qqJLb3dM0p uNFfwxphlSd/1SxX wUAkJACAgBISAEphYBTXdoopzD2vm52EkOOX7G52eoI0eOYPHixUp083fWJ xF53fexl50fk9JSVH7 RmXv9fU1CgQvI29551dPXA4EqcWHLF20hBQnUfqkT4Qtq5aKolyli9KOw/TYx5JkIerMTdqbsjcs6SLODc9rBuNbmrsYyOGOdyk4lg5bDTmI4FEqZO89Cz WKB5qZfMyzUN9EaYzRZ1AxroZaeeM 4Jqzh6DMUzyia1OOfeu4a6WurYcJHwtiGTvNR6KH49beeODrPJDP5cOL043KUYl218TTkNR3jp54yHQXzNbTYe 6OJ2MamJjXsgtsIJ24f3ImQkZ4eKN6Pbl5WY5Im7lxqqK9HL42LMlDkRwZ1OnE7n yptb2V5pQwIS0rDa2trWhubUZ2ZrbiL0kICAEhIASEgBAQAmNNQNMn7DAi7UGZ83e3x600CGuRdHr24 cQ/s4Cm/UAP19z6Dq/s2ednxn5OVXXLyzM2dOuOx35PB6r7ki0jbX5kt 5QiCgvFV7VQqdveeacgnW2MOamU3rldI84uE cwPmF4tHHpfRQGOR20gQuQICiQXxWCQuu7KiQt1o3CPWRaHKHiqju7tbfY4jwZqSmoYUCmFhT3JXYLvT2Us9Y53qHD638kSFuoEna6qrqVaefi0aAKg fUr9aHByU2 g6vWzmClUf2LHubMQDnf9h9o2nsJcv34uGu vvVyoJ2F7/Phx9eJ2yCJd3z9ZrzfbxWP3a2trqH3GIysnh8ZHpajIiIngNxouHPLV2tKiepx5wseM9Ayk09iu2jqtx3k0ecu5QkAICAEhIASEgBAIR0A9x9OjMUUE07MS/Y/ 40hdftZn3cECWx/KyENt2XFQXV2twtP5WTHcMEfeFjyvFgt1HprLeYd/ dBV/g7Wv74fLZ4wx3jbcfD1F7Fhf3tg4q8wx0TMe6hjo5Q7VJ6hNnm7UP7mS3jpg2Z4hzov1n0 Jyo3v4TNx2nyvVjPmQrHUb1q31uPjYe6RlUvft73e lFcFRUMbVjbr/DGiwxlIjlfbow5wasvOW8jdqT8laTYGfhPBapkYQW52ulieV6Anlybxb3O/Q6/ciiSR6Cb7TsvDy0NDWjnsJSLOSx9xGIBFuC6injvDJpDMlkS2pdRrpOHHLNEQDs6fdTSHbNqVPIKyjQhDFfVP5B4oY8gUkPS48Uyh7Okz7ewlK7lzUQ6empYWlwyAinCcYV1pZwG/la1lIbtdFcCRa6h7g3l 8jbss8XspoHVY/Wrgixm1bC3nHExMdmq1eD4lzGuNFbTjOOj5zS4xbRSRjISAEhIAQEAJCYGoQIDGgomXJWv3Zjp83XSzM6TmKxTnrA37e55B1dhrys0lGRgbySBvwc5fuKQ tMJ/H3nROrGu6u3siO0l8bdj94gt43f4JXHwJe95DcnM1Yfcbm3Hs4uW4YvYYhsNHKze0UsHfQ23ytOLAm5vw3pz5WLOIwvqHOjeGfc7KjXhs3S6UfvZS5XQKRRJDFhNziKsSz/78d9hX9hl849YSRB90TUMl6vZi/QstyP/GRzDXNjxSupbmdx5yERdPz8ms59iLTv/FLMyHEuXB5HRBzELcyKKREm9jgTEWwpxvqMa6eiSTZ06fnEGJWErsHfeQKKg8XoHpZaV9ZrEtaRnptD8eJ2mf1WpQ5/JkcU31DSrMxThGs7UHsxjNZ4464LHzXB/uRXFRLx Pke/oaEd1VZX6BdJEuTZGYTRlDfdcXWSHCvBTp6rYVBU2blATGlAboI4Ffucfx9raOm1boKOGx/7zJH0pNFnfqBMXHGhvel5Ol6evsyjYHu0HO3587RlmhZQopx5cvkGtJGadNIcAs FhDLyyAHcoTdbEPHkcfx51iPmoveo/US00mUp 7rTJarbYJQSEgBAQAkJACExxApo 0ULZ9YhOJ0VJOkgTKMcGaYRjx46pGdqLiopUbfmc4Je LfidveqZNJSQE4v0ttaWAfMZqR2B5Gs7gK1VZsz8ZCEJOxKhgzxAPPadEkWcso3Dk3LBJQ38HL3cyOf2rfSu28RM2ET6xzaOSkj7WvDeC1vQMes2XFMWT6wD9ae8e0 /gz/ bj26rv0GvryCJuuOYKK/9xS2vPACXt1ZhXavCY6CRVhz0w24qIAm7/O70bR/E154eTsO1JLn2uTAtIWX4OabLsL0hCC6vma8 f/uw7raCIUgH7d/61akkIM2KyVOmx3d34k9j/8aj 9phdYtQzo2IRX5pYtw2dWXY1GWFXmX3ojztj CdW9firIrs2MS0yxRWA8xYV7FqoocrRtefgVXrVmDogJ VuY2OQxhrldpKIHO /gm0D3k rG6Jz0SluFsb6cQFDWpHN1oXhq37ubeLKonexc5cYg6z8LN4pU9y8GJx lmk3ioI6 k1U950Phs7jDgGds57H2ypXTq0auh8PWkJBKuJHA5FJ9DcjpI HI0Ar 0H5aJtZyFebh2wEMWykrLhmVMc3PzsI6PdHA4DtypcabsiWRnpO0N9XVq/oX4eJ4vgUQ5dcx4qI23UXvPzcuPdNqk2N7c3Ng33wD/qHCnUgfdg3bq BqrOSUmRUXFCCEgBISAEBACQmBSEVDPo9q0Usou/u4kp0YaaQUexnjw4EHMmTNHeb21Z0VNNfNn/XlW3x78zkK loYS8szsLMw5lD3csy8X3nrgPVSZy/Cp6eRv5WfzUEJ92wLP7aH7R/Q9hnKHyjfUJuao0uht9NTtwOaTCVh692w4aIyBukTd1di1aSNe2nwUbVRKPpcfjpUyoRP7nnwYz54sxfWfuBszElqxZ8Nf8dzDNLkwealnG45j4wvvwzn/ctxxVQr8tTvx95dfwsP LHznjhno1 YOLLzts8jp4W4GD2refAIvVJXi5jsuRBYv3mVKQLYjG0l3/TMuVeWSTT5aVq JRHnOGnzm5hLEuXvR3lCBd1/bhD890IaEb9yKmQnTcenKdLy79R1UXnIzimNYFVxrO9q48tPVp7F 48vqOZnfr75yDQqLCkm4j0CYs91DJW7kWo A5inX6qnBH q8WPe1ttAEU/TgzzcbT/DG4nQW3XDHaNZFTZz7YaOJ0jraO9BI3vCMLK23S8 fPeccLsznch6cV0szjY2dKGFO9jbR5GQd7W0qRF0larADbmP1XU9 NDfTZGYUIcBseXyMncadcw8g90Bp5w/6Ceg7ezw 6DOgs5c0NHHDixTiHnose9y9tJzdWKVwP5hn0p5Y61VPY8q59yyBJrBjUa7 UFB3awuN2eZrfKryZKCNaDlyx5eJvOh2Ch1PTklVf2zOVOL22EsdRhz1wB0h3BfIHQrtdP8VFRadKbOkXCEgBISAEBACQuAcIMDPecof2zdWV3PWsRPv0KFDyM/P75uMmvUJH8/PUXZy1vExnPhZhp9d9edIfud9fAyHv7NTjI8Ju8KQrxX7362GdcYVmE6PY2rMsLsBH6x/HhveO4FWjwlJ5GAx0WheMz/f834u1NOCfa uw0vbjqLRSfbkzsfqm27EqkIDDv/5x/h99YX4yr1XIU/FNvvQsu03 NFLibjz25/EfA6fDi3X24tT29bhmdf24HQXlWBJxdwbPo1PnpcG1qBRbWK76LTOQ3/Dr/acRnWHj7IowQVrb8K1i9IRe9ymF0379qDRPhu351gCzCjaeftzWHcwBav 4WZUPPUcOpUIHqB 1LVQyVWH3cecyL7ialw8K53sn4as66vw/q/24HCjG7OnleH2r34NBnoWVv7xOdMRd IQHjt5HM3usgAz3sHsaZk8LVOYdxFM4lJYXIppeoU8Nfj7//wKO bcjW/dMA0W3aaEbPUcq6YvLp2FGY5q/ODPJ3CMJhGYEUergc1bhIxXtuOD6uswvTA6HdW2yNhTp6ux4ZVXlAZtJccwp7 TOL/mqqtQWDgtJu 7OokzDCd81M6QFNyw9V3DOT80v DvHILOPQwc4sviNJkEAYvrktJSHDl0hO5GlzqcbyaeNItDgx2BZbP0fJKTk9SSaUYOseZxIzTT4kSlJlpzvZu8iewF51BuTuoG5Qum3iK8cycEi1ja7aRjeEZ2HvsyVlxV4cNMDuogCE6NVDdOoSHuQ2XL4/3HIgWwhc3qTNgT1pAwGzvoptTacYoS5Wo8E1WGPeapadpY XBtQnXS0HinNhLvSTSbaGZ2Tl HWJhixm1TQ1MDkun 0joTaK14ikLhP25qEjiqgyQhIASEgBAQAkJACIwPAU1o83OT9o9WZiKPJ4sefi5hj/fcuXPVZ066MOcx5/yZI2z152g lkPX9e/8zlriBC3LzM RHKHLz2v6s7teH1/LfmyvsWLWVQUqjN3v68bh5x7CE7visWTt7ViSY0JbxQ68XM3CXAu59/t7cfylh/CHnam4/KZPY14ynfPac/jbo uQ8fXbULiwAKb9h1Hevhq5qRTs7e/CyX11ME5bgYJ4TY Fluuu2Yw/vXAQqVd8BHfPTqZ5qZrQnWanYcVcZiw2aYx8bhtmXX4r1qb4UbPzVWx44iG47V/CLaUUQh7LRaSyqo81wZC1GplmLluRR8aqz NfLyEh7TyGP3BGOotweRrtyEkB9uw/hMYV5N02e9Fy4iQ64qehLMWorpFB9TYEQuSJeUunF6a0TCQa9TJDMw4cyy1FlR3YH Tk1LbrO/Rr5UFPSyW2b6MJuB3zUJbMbY6ed1OK6Fq8horKdngLUiOG5OtWaM/yBhr2mY3P3PkJtVl3ZLMx2jrmw5z8LbSKZ K77mXWwk9oXDmF/nJigV0yoxTlh4/2NRwOXa sOIGSmRTWELRkUxyd46dACv1G5XWXJypxGDrf4HxRPe5AI1E/KJQivfNe/k 9uKH0d5Loom2i7NfLiVRupO2R7BsTj7kGT3EJTTmZWtcAACAASURBVOG2hR4T/H1M7BmqgJB9bW2tqieWl/vjlQX0CRP1CUf67A/UTbUU k N26fQd35xdAi35ZxxCnlvoXFVXG5qcuoA8c9LzvGEHhzi5WVvOQ234D9cPT29yKJl0iQJASEgBISAEBACQmA8CejPxNozMjlb6ZmeHQPsyGMngf6szzbowry8vBxlZdrQSz6fj FoVp4UTtMX2nM279Pns1JLptGzGq a05/IO7z/A9TEzcC1BXHaENOOw3htVxey134Wt65iby l6XZU7TiK4/Qsxc956DyMl9/rRMnNn8dVCx1Kt Td1Ia9P3sV71Y5MbNwEQqNz2FXeQdWLEuCoacKOyt9yLtmOmwqj8Hlenpa0U1dA7NLSlGYR Olafw0JzXsNQabeFZ7fopOmncZVl Qrzzks8py4K35FV7fdBRXFc HPRZl7u1EXTtFLxcnkfeXbVVmUKKTg/QLl6ZYhEvGdKy4dS2OPfJ3/OxnB7CwyIdjh1xY fEbMZNWrBt4nhv1257H rpcXHH3HNgHlBmcOUdWaEkbDhz4Eqi3bo/ixbsq/g//9p3g81Ow/GMUFcFztbHd1HmQSfP4Halvh9ufEjWigNuS6o8IvHPOfTiDOMQ8 RtnoDf YDNj/TxcgRQpX/0G0i5Kv0Dl41l8F0wvRBX1qvBxVrqJ2LNcTmuWz5ozuy9kRc9bXRgOG47UMCIZMYrtOsO d778gUbRZ4dqFH0tpcAfzVMVqaSPuDqx4pZD3S9nCe67HwmCtazCPCdZxoe4bTPLj9MQM10QbXgdujmhyCkt4O1Oe TeqLXl/ I2O309CNtnZq/zYk05iosUxNLU1qCUL I8dCPDc7r88Tzt5yB4XTcw8y226mCBCeryGNhoXok0COpS2SlxAQAkJACAgBISAEggno3k/9WZAnpOX5o/j5n8PR2dERPDE1Pz8VFhYqbzo/g/E Pm7mzJkDRDnv43P11XG0JdN6Kd g1Wa8Ldj7fh3iZ67FtDh NqOl2pqr0OhPxPwiWqlGf1bXH kDz6ru5pNooGenjmfuw7efGXg9zW00lr20BMsppP2vHxxH55JFsFTtQrk3D9fMJBHPeYQp15J/ES4rPoQND/0vqhadj5Urz8eCfLvqGIjFpgEaRLfbmISSQhteOVaFFvc82KJHbJNq9cBJ/k6z1aQ9q4Y21yDNo55lQ/er7xQV2tKAFn8GFp03C2nNB1FO4e17dxzGiqLFSNMDMv0u1G1/Cr97qQnz7/gsLs2hrgC CGFT30UIPEMHDtKPD1wb7fma9uWtxRduKUUcdYK4Ohtx/IM38MrjvwM eTduod4BWhwcFNEOT69He34PW2b/Rt2usPYF2RyzMA bURQjamr7193mQ1lEpAXCc6OcGnE3h8rqs7DzTdMbsjY6j8XuzemlpdG0KfjUcgl0g/IYdB6Lzjdgb2AcL3/mvEzmiQu5dVAIeyeNzbaRmDLSmlL97YEbjNaY1P/1xhpoKLxJ96IqlmQ7T4CnNepIjTAixlHv4HJDQ9mbW7SJ3MIJ8EgFqvD8cU6TzZ7g6qaQkOal/Hi4hbqetJPFObdJmrM 8IOl/djzeeo 1H88WNQHvvPyf3X0R4ajRLjNj0Xq7OxQQjudhDa3N 41rqw6iZycXLXEg4lmjed7i 8h3s9zPHDEQTJPVihJCAgBISAEhIAQEALjTEATUjz7m/Z85HI5 xwI2dnZ6tmZhXewjmFnQ3DYOpuo5aM5PnQvO48r52XVWL8oYU5z6vh9/cudeZv24f168lJfm4s4ev5Rz3BkBwU703H03ReYc1x/1uWoV7WdI2bjMO/Dn8SV2iDyACUqx8ETyBlQtrwIxmd34EhbKRJ3HIOnYC1mJWr5hisXpgxcctdXMOfoB3jnrXfw5G/exFuXfgqfW52vOgii26TZz6JY2ags4mG09ElN4MZ2x3AxyXYrC1Z6TuzPJ i8UBZhsvR3HcRzz yC7ep7cOtynrn9fFy85BX86vcv4m/zy/CJ2QlqZva67U/it tbsOAjn8KH5thh6LM7TKZcL01gUbWC6hJUV 3aBOpuTUZ2Voa2fBq1o8LCVHSefBjbt1bi2rIZiPe6QJqcOiDImTZkuZotqv0FHG/qavA14e/8ovbAz9GchiXMgxt1uCoHb Nj WaYXlSsvIHcCKtOVUU7Lep 7gHj8eWqLvSvmcbYTqOZ7IJTdk4OnBROy6KChQvfTE6XFxXlx2kseglNptZC/RyaV5Jt1MPhoxY BgfwTOt0x4EnseOlpfSuItVnpN0FqhSt7WgbeDxLIo3nViEQ9OIOha7OLrWOe//B2scz/f/htBG21TsGY8y132LtxzS0/mfCnlAbhvqelExjy nHi4c42BPtWsgVXWieEKON2y/dN3rS2wRffw6p4jB2tToBj3WhMHKLxYxqWn6hqKRkqCJj3tdAcwZwp4by5HvcVKZVtb0amjyRE0/4pnnLffRDYkQnrRGaQeN7JAkBISAEhIAQEAJCYCII9AlqekLmfz00ezoLb35 YgcSi/JkmouHnQv8Cn4u1D/35aEpNzW2XOkNGmLIz1u8n/PhvPsf1WlCs3270ZAwEzfm0zGByppSi5Bp2oGjR5rgKsgZFOLMx5lSCpBheB/V9fQstSgz7DH2GRdgpuVJbN25F4nHfCi9aSYcPNwc4ctVxRusyJi5Ah asQSLXnoAD23fjlOrbkFxDDYFSRBVF/XdVY DFT0wZxcihXyYwccEqjv4jUK8MxwGdDe3w0UnmANBoIMP1PILl6enswZ1rniUZrFnmo8zIC6nFLmWbTTkoIcI0LU58QoeW1 PObd/Dh aS9EJus3hCgps08vqq1/IsaHbg7/7vU70kGwzWjRnrp9C9us7gUSKZx9O2VxkOCRaWzTELsx124cjdPhYFuUeD63FTKP0Va/LKBNPiFVDawtayHPOl4oFf2NDIzIyWfD2p4LpRThy DBcJNC5i0TdUN3dOETLJqguExb2pO55TGzWKL34w6kSl5mRmaVe0RJ79nlNdhZsfJ6X7FYhxV3d4FAdXopK zGJltPE7g83W3uoBbq3fWzGdLMo58savn1NvD2htR36eyYtxVFLwpdDxtnjzR1P/EuW6EikiUm6MI1CrhJowkM98R KqpMneCAVtQeKnKD7iuS58l5304Rw7IFPTR/98n9Wi1X9EeMx8MyWO7G4vBSaPJHvG548ka fikIhbzn39vEfM0lCQAgIASEgBISAEJgIArqo5gHE7NRgZ0c8De3Tnwl5orduev7nZxkW6Pydn2fYsaBH4PIzNj9fs1bgF2/nlXE4cT78nMNOvh4a0tc3BNPTiD27mmCbeS1yaZIz3RGM FKsOT8VD25 HH/2Xo4LilNg7q1CA6/qzMMWySFlSCjDZUsceOyt/8NfcBmWT0 GxdmG u5MLFmary33ZS3EhXNt P1rG2is7nzcRYOb/XSuP0K53tZDePcYkJ2TBKu3DUdrSf/EJdLy0HROLDZ5tWfp3rpyHDpKIfvuFhzb/jrebsvApbcXI56jNGO6oBZkTU F/93jqHfOwaAJywPlsJdYZ nrPIinfvscTs28A/90QwkSHMUotb NnSgoKrFiHX2o2q91/GQXcqLi5KhMHdjA827EBn/hVYnNROTql2zTKDBY70dDgs4aRvwGNO11MNIQ0EM5C40jREwB5tiDNl112L4 VxxJLaT1stjuzYgp3dDixfngMzne mCeFO99pRnE/P55xfLGzY8Ublc3vT35XXnOULD/KnjzF7zPXGGa3cqlMn ho6j8vQx9BS3Ksy4sjRQyoLDkkvK9EmXoiWZ/D 5NQUVFVWUnZMlIN9DbScVKXq2WIhoyeuaNmMGTiwb58SEVxnFi5qJkZ1kEHZ5vVQ6O0Yj8sNtnc0n3m9dQ5R5sgAfWk3FkpxVFcOG1Y/OkqMhhekoyl7qHM5hPkkL EVIYWGuEc4bMw2a3o8vMecC5loe0ZSMZ64jb3d3OmiZtwPLOVno tfQ sdllDYjJ74j0Z QSFOHDsG3s J2wL/IeHOmhYaFz4WwjyfbGqkceSttIKBg 4tbocqbJ3uLS6HRbn2BxHoIm953jhNPjcSnnKOEBACQkAICAEhcHYT4Od57TmEQ8O1Z2EW5rycLK9fzuPG ZmFHTQ8Azs7D2zk6ODnQtYoukDSx5OzgOdJ4PhYTaBpc1FVk0OQ1zVvoeWL9eRp3o9dzTbMvpHC2IMxk9e6YM2d JTtFWzcvh6Pv81DNk2wpRVgXiZPykbJQN7ga 7CxxI34tUdf8df3iJZZ7Qhe/5VmLckIMxhxbQVS5G28y34lqxAUbymXiKV6 2sxr43t PvHVweOUpyZuPqWy mTgMuMAabjPHILpmGxINv4ok/aTY78udg7V1XYWVeLIPLdQgmpM2Zi7RNu7C7zo3CvnXJgiGF aw0TWB7XCGuufNGmP7 Jl764w7weltxaSW48NarsZor5GxGeQPpYc9reOyh4LySsPLzX8Q1WqXDFBLDJnIkJ6TSxHUH3sTjf9CON1gdyJo2H1d/4hKsKObZ6b1oPrgPjbYZuClrOGy05dJe27R5QEQsd/xct3YtsrIzYOjupKnzYkgN5JUOnd0w3GkVJ8tRkD NvGf0GM 9AJQ85A00GUmkc08R9WZxY6 rq8OsmbPDZRF1G3vMG2rr6aYyaaG03MtBFzRvGq1zl53VVy5n5KSwk4P79pN3j0PAOfxAu3W5Z8xDojyTpq3Pzc2NWmboAa3NDcjMmUbeTe4CG/vEAqj8yGH1I8Iz0fPyWS76seF3DlU sHcvLRuXQD8 iaivq8e8RYuGZcR42H/k6FEaujB9WHacIM/vTOpAGU2qOH487FreXdSJMVH2jAVP/uNy6uRJuj 8KnSKO2P4D0dnRydd89L oQsBWE10TzbW16lJD/Wl9PgXn2dFn7NgwWiQDji3rb1N/aFKTLRp4WE8/ED9NeQONh5bTu2S7q0cWrJNkhAQAkJACAgBISAEJoKA2WzBnx57GFeuvY684p3KYbBn3yEUF9MwWtIG7OhQTqyQxPqExZCuU9SwPNYS9NKEfv85fAw/jynnIs1XtXjBHMrNi9rXfovf7JyOT3/pOhSNzdQ oWaG X6myg1jylCbaI31dx/7LV5J BC fMccJGpycKgzptQ v/Mk/nb/4zix7LP44mVZMXm5uf3oHUHV1bXY9NZbqpOol57Zr1pDS8tR5DfL5jH3mHMYCd8YXlqugJdP0pIWBquLcn3sx0ivAo8hb2pspBuFQmv5xlL/oDyO1bRweyqNfY0LLI/WS2uUc4eAUhJ0w3Him1GdS7MT5NCA/smYmBGLcP6RYNHDHnK YgXTp2s/JHSBmXXoD8hkqEukWdB124YzGVss9eGGrvhESBNtTwQzom7meuRT2HrliQqaoLAXcVZehkz7Y2Gm8eOhKZ1u4vb2VlV3NayB/vEQB 6sGavE7YtnXudok9q6WsRThwHPbcDtkhOHA7Gt dQZp3vTuR76H7uxskPyEQJCQAgIASEgBITAAAL8aE/PKewv15872DvOgpxDz8OJ8nAE2QkSLfGzTt/zJIeT72uDfTaHWUc7cwz3n6lyh1sFYzIWX7kM7zz6Cl6vKMYNJTGugT7ccs7I8W7Ubt2ID3xz8dHzM4cnpJW99Kyfn4fLVq0icf42rrryCjXJMmtknlMseksMqnQsDVwPB HJqDS3Gk/wxUsV0HRrdAOxKNbFxkh58s1XQl7Ww/sPKGHAodW8fACXx2POm2mMbXDiiqp93FvBopwnXaM0g9cwZKMmaZpWVITTFKbv6qWwHAol5ogAFuyceCk4D9VDTQIXvHTDGa6LEnIUIjRUiqUdDXV 6L7p1DMaLrEH/0zYE86WWLfx/VFAUQfVVVUUQt4KI/2xyCsoUPdNuFRQWISTJOR5LDonbgvcTkaT9M6e4Hfulc7NyUNtfQ21O5p2I9DmeGw5R3UEh7nrwjz4fTT2yLlCQAgIASEgBISAEAhHQD1T8jhqdljRxyeffAo7duygiZ6bsXnzZmTRPD784qVceYw5O4fYU6kvp6Y/X7E2Yc84v3SdEvzOQ/ZOnqzEKlqGzFO/F3vb7JizKAsWLjecYeOw7UyVO5KqWPJX4dY1QKVJi2oO/xQ7kpzP8DnU1gxJpbjkpgtQRqNJh69ptNaSl5eDO26/RWlYbrh6G4pZmOsFx2LAafJac2KPbw6FlmsN24 6 gYlnDnpAnO4ePWbhCeeKplRpmZa1yeiUiJb/TdQbOuVZdt9FBZuphn1plM4OOfBE0DwTTlSe4Zr/3COj4 jMSgzZoY9JZ/E2mkSbyzOp9FnSWcPAW6LHBnB7TWa59lM4825jXBPLh/PYe2jSdoftv5IjODvfJ9kZVK0Cg3j4Enm2EvPczakpaVH/WGKVo/R2CznCgEhIASEgBAQAuciAc3pxhGkrGxYYyTTBLU8Nw4/s7DXnN917cLOQ9YRupbQo//4Oz/P6C/9GP041gq8Uk4GTSzGZZmyV Mr312tgKuyJyidqXJHVj0r8i 4Avl8Mkf4jiyTSXgWTW636HKoKbyHUS8moPQpi3B2ttE7T4yu2q2Cw0O9hxHKrj gRyNUWtI/XpgneuOeJ274BgNPtObBooWLo2UR834LzRpdSuK8nsarNzc29zm/NWGui3NGoTcHWkc9I02tXWgiD BoUgotCzVe48tjsYtn754xe2Rj9Dn/M21/LHWcSseMB8/hiFnu R3PxLbwbwAPHclMz6Y/ei3o7u1GckqK1ttHhQ/H3vG0VfIWAkJACAgBISAEzg0CfQ4E9azvRxpN0naKHIQ8ae2dd96pZmNnYc0ebxbauoechwHyhMr87KJH 7KTg7cHC3hdpLe3d2D XHru1lTUuQFXajmGBEiNKmlKAl1FePBzc0ChqiHXHFPAyw/HkLjRc0Pm3qLhJC8Jcp74jQvnPNR6yPQazQO8GntNtug3Eoep5 Xn06RvLBZa1frgPEkar /Mib32vP5yCs3mzpPX6bMwch66p3w09gyHx9l bLTZ2sPVX4VwjFOabPaMUzXHNFu F3QRHtwZp/c26 8ZGQOXJ9TvoeB3Pa8xNVAyEwJCQAgIASEgBIRAgIDmsdZC2XnTksULceDgYeU1r6o6PWaczKQnli9boo/SHbN8JaNzhAALcaoq 805cZC38qKzWg985g8xCXN wE6hCdWGk/gBvrr2NM2 3th3molmUR8LEcx5hE7UwL1bPGYkLy9PiX9dQASLA/6s95QNpy5ybGwESktLYjtwgo6abPZMULXHpJhIolq/r0ILGYv7OjRP S4EhIAQEAJCQAgIgaEI8HNJfzS5ARetXIFFC ajmdYhZ cgO9JV7GwgXFhX1ppI0iNqhyqBl1u2qBB5nlNHkhAYCQGO5tYiurnNURQq/esfd89OMa1lxiTM2QBeO3m4acki6lmaoCSCe4JASzHnNAER4Of05ZfKCwEhIASEgBCYVAT8gYnfNAGuzWNlT7QjwW5TYedKkLN4V1bTSkf0TzkZ ryUsVcnNhkfe35y5DlGQLU5iubm4aH0roW280b6Rl9YnMcszM8xdFJdISAEhIAQEAJCQAgIASEgBCYxARUly7NmKRe47pWkr0qRa2KHBZBRqWptiWXtWLV3EtdMTDubCKiwddUeNde4UQlxvf3xu7ZdhPnZdNWlLkJACAgBISAEhIAQEAJC4BwhwMsg87LMnNgT6eMlkkmn8xxTWhB7QKSzU5K2sDjSRNI5AkiqOSkIcAcSC3EVrMEx7JqTXHUN8ctP 2guOPGYT4qrJUYIASEgBISAEBACQkAICAEhEDMBFjvJScm0jGuzmo2dRbqRRLk/aF5hTYxzlsplriX9Y9CmmAuVA4XASAkEBWiodtn3XQtt5/8bujvbpVmOFLCcJwSEgBAQAkJACAgBISAEhMCEE2CveMXxcrzz1mbMnj0XaelpmqdcV O6wlEuyYB5oZ8n3Gop8JwkEKy2w7XBQJsVYX5Otg6ptBAQAkJACAgBISAEhIAQmNoEjCYzKk cwPYtb5HnvGlqV0asP cJiDA/55uAABACQkAICAEhIASEgBAQAlOTAHvOjcaxWZJ5ahIQq88WAjL529lyJaUeQkAICAEhIASEgBAQAkLgHCPg83rBL0lCYKoT6F/bfKrXROwXAkJACAgBISAEhIAQEAJCQAgIASEwBQmIMJ CF01MFgJCQAgIASEgBISAEBACQkAICIGzh4AI87PnWkpNhIAQEAJCQAgIASEgBISAEBACQmAKEhBhPgUvmpgsBISAEBACQkAICAEhIASEgBAQAmcPgbCTv/3f2ydiquFHL54 4Lj/jk M6Tw5SAgIASEgBISAEBACQkAICAEhIASEgBDQCIjHXFqCEBACQkAICAEhIASEgBAQAkJACAiBM0hAhPkZhC9FCwEhIASEgBAQAkJACAgBISAEhIAQEGEubUAICAEhIASEgBAQAkJACAgBISAEhMAZJBB2jHmoPR 7rBZxcVfikY17Q3cN X3NFz8 5P5oO1994M8DDvngnv Kdsqk37/0V9896 o06aGLgUJACAgBISAEhIAQEAJCQAgIgUlKgDWieMwn6cURs4SAEBACQkAICAEhIASEgBAQAkLg3CAgwvzcuM5SSyEgBISAEBACQkAICAEhIASEgBCYpAREmE/SCyNmCQEhIASEgBAQAkJACAgBISAEhMC5QSCmMeZjheKS3z0 ZFZvfuFjQ 4P3fnX/70gdJMaCz Z0vVf/OGwzAlXp2FlIAcLASEw5QhMtt tKQdQDBYCQkAICAEhIASEwBQiEE4jisd8Cl1AMVUICAEhIASEgBAQAkJACAgBISAEzj4CIszPvmsqNRICQkAICAEhIASEgBAQAkJACAiBKURAhPkUulhiqhAQAkJACAgBISAEhIAQEAJCQAicfQREmJ9911RqJASEgBAQAkJACAgBISAEhIAQEAJTiIAI8yl0scRUISAEhIAQEAJCQAgIASEgBISAEDj7CIgwP/uuqdRICAgBISAEhIAQEAJCQAgIASEgBKYQARHmU hiialCQAgIASEgBISAEBACQkAICAEhcPYREGF 9l1TqZEQEAJCQAgIASEgBISAEBACQkAITCECIsyn0MUSU4WAEBACQkAICAEhIASEgBAQAkLg7CMgwvzsu6ZSIyEgBISAEBACQkAICAEhIASEgBCYQgREmE hiyWmCgEhIASEgBAQAkJACAgBISAEhMDZR0CE dl3TaVGQkAICAEhIASGScCLxrfux7//5AVUusOc6qnGhvu jv94sRqeMLtHvilKuUNlHGqTtwFv/vKb P4TFXANdZ7sEwJCQAgIASEwCQmIMJ EF0VMEgJCQAgIASEwoQS8NVj3za/gvrf9sJvDlOw6gWfv yke39kGX5jdI94UrdyhMg61yVODjf/vJ3hkSyO8Q50n 4SAEBACQkAITEICIswn4UX5/ ydBWAURxfH/3dxF KBOAQLEEiCuxUvLsWKFS2l0GKFUihQpBT7cIpL8aLFChR3dwgaYhAjCUkuuftmT5LL5SzkcrG37ZG73dmZN7/3Znbe2JJIRIAIEAEiQAT0SSAj7BBWXzFB88H1Yc/TX8r6Tjft8WxU4PHAU/JpuDtWfxmnlIgAESACRIAIKBBQ1i9OkIgAESACRIAIEIESQyAdbw uwVWz5vi7nh3055frP10jz37YfqEBEjOH/VPxbM3X6L/NE52rWJQYjVNGiQARIAJEoPARoBHzwqcTkogIEAEiQASIgP4IpL/B/rXXYdFiMOraStxyUfIjbBrZEJ5m3OiyMdzrjcPx9woipb7E3gmtUM6aC2MIx8Ce ONSLJvqHocjnSzB85mE26myezLwalkN8MxaY98HkeSkYrrCBFxf2hvVHQ0kI9oW3uiwOhSyJe9aycRijjz8LWq7GonjMPdugu 2P8UnqRg8UzdUrV0XdetKPiEu97FyaxQaLtqI4WWN9cecUiICRIAIEAEioECAHHMyCSJABIgAESACJZhA qu/sfamFb4YXAd2nF8u/ICjwxqi77Jw1JHYeP/IWfW9oiRepPi1GJ4nHm 4botCwZnVecwqX/tmNEqcP4vtUwHImxRlCP2jB6cRhn3km3ihPF4PKeuzAI6o6a4kQAxXRT785Bt1H7YDNiB85evYwz239Fv3ouMOICayOTOFYgI8UBraZsxoEDWzAl5CUW9WyI0f/GQV58cUBhNA6Pn4KLpUdjQV8v0BRCKUD6QwSIABEgAgVCgJ5DBYKdEiUCRIAIEAEiUBgICPBy35 4bd0Kc2vbigUSRh7CzM1RqDznLNb9UE7iGDdwxrW1R3BGKrIw6hCmrQ5Ho7WXMLOXK7he/hqrwrDXdxLWXE1Eq3q9UctgALafisQIb3fw4y5hy8UMBM5vBEfxkEDOdNPjXiMGdmjdtDnqBlmzKfUhmYC0kUkW2K3TVEwdHgwzdqJti2oQ3KqEX2cfw8zG3eAoN09f8Gw9pu5JR5tt36EaF5gOIkAEiAARIAIFSIBGzAsQPiVNBIgAESACRKBACQheYM 6u7BpNRA1bSSSpLy8iKdCFzRoUEbilCsRMOXFOTwSCHC6rxsMpBupGfl hztIRlhYIuDSHIPq8nF1w7 IYuu5E65swunUIAxqU1oyMq0kXYvgHzCxYTyWNvBFrd7TsOVqVOY0dm1kUiImYOyJxnVLQfDoEl6nyIdIwZ1VS3DHsRfGt3ERdyzQQQSIABEgAkSgIAnQs6gg6VPaRIAIEAEiQAQKkEDa811Yf98WbQfVhNQvB1uczUarRRAKc0z zpJUJGIhrNFx4zXcv39f7vMQOzs7gc93QYtvGsLgwmocC/ Ai2uPIaX2N2jjbiCOQ2m65lXw479heHRonoCMigAAIABJREFUEqq9Xo7eIe6oNeUKPnJiaCOTCo4iLh/s/my72n26gw3b3sC1y0DUsFRxI50mAkSACBABIqBHAuSY6xE2JUUEiAARIAJEoPAQSMOznRvw0K4dBoRYZ4pl6t0AFY0icfzQk8xN0xRlNvWqjXL8BNy6z4N3xYqomPkpD08bbpUcH85fjEZrswtYum4LlvyTjqaj28FN7JcrT1ecBt8K/q3HYOWZJzgzwhk3lizEtSRAG5kUZRT/TrqP/adiYFqlPrxMskKkPt2PQ /s0bxbJZgrvZFOEgEiQASIABHQLwFaY65f3pQaESACRIAIEIHCQSD1KXZsfIJS7Vci2CpLJL5TG/w6yg91ZrZEx4xZGN7UG6Zx5/H4o1wYl3aYOtAdzee0RReDGRjSyAumH1/iQXQl9B9cC3as259n3wjfdSuFhlNGA6W wrHmDpIp4yrSTXuxG8uPAgHVPGDJdnw/cYe9V9zGDZyfr41MMuniH5zA4eMfYZ38HMeWTMTvrytg0u7mKJW5vlyI99dOIJQfgJkV6RVphcMYSQoiQASIABEgx5xsgAgQASJABIhACSSQ mQbNj1zQPu1QZDzy5lHbYXabOO3E45jMH7RcHT4LY3RMYGDXz10qWQD8aA3zw7NlpzH386j8dOKofhyFtt93dABAT0WovNAiWMOFmvN0d/Ab 0MCAZ8j/o2Es9YVbppEdewc8Yf O4d9441IzgFdsL87ZNRzZRLUAuZDOwQ0LQOXPZOQ5cWEpndQrpg3uk/MCZI3gFPwZurLwGnzvC2lNsNrgTaAGWZCBABIkAECg8BcswLjy5IEiJABIgAESACeiKQikdbtyDUsQPWV1eyyNrQBU0nbMO1CWrEMfFE xn72Ed1GJOA6Xgqmi4XQHW6lrVn41zYbNWRaZLJsAx6rD7PPqqjkFwxR63lERAt1xSOrhMBIkAEiAAR0B8BWmOuP9aUEhEgAkSACBCBwkEg5QG2bH0Jp45fQ5lfnm9CFlS6 ZYhipgIEAEiQASIgG4IkGOuG44UCxEgAkSACBCBIkMg5f4mbHvtjE79AqHPVdYFlW6RUQwJSgSIABEgAiWWAE1lL7Gqp4wTASJABIhASSVgWmMB3ogW6D37BZWu3jNKCRIBIkAEiAARyCUBGjHPJTAKTgSIABEgAkSACBABIkAEiAARIAJEQJcEyDHXJU2KiwgQASJABIgAESACRIAIEAEiQASIQC4JkGOeS2AUnAgQASJABIgAEchnAsmX8K2fKTyHnEZCPidF0RMBIkAEiAARKAwEyDEvDFogGYgAESACRIAIFBgBIRJu/IGWNoYIWvEGGSrkSHs8GxV4PPCUfBrujpXcJXiL/RNawMecC2cF/3bTcTJKIcb0UCysojweSdzBWBNhAc/yFVHe05a90Zwdwijs7uYJM7m0jey8EdJpIv56lASRCpnpNBEgAkSACBCBokKANn8rKpoiOYkAESACRIAI6JhA ocb GvuJIyfexRhLO7qauI38uyH7RcaIFEoC5SKZ2u Rv9tnuhchdvbPQV3ZrVChzkJ6D5vBxa7P8Tyb39Gq452eHh6FHzFHjY7DNzQ5c9/UTmOc9hTcG9eD4y50gxLt4yEvzE7ZWiHSu4BcD14A2Olt0CUhg hr5FSeToOLW8My5Q4vHt8Butm/IYe9cJg93QDWtjxZKHpLxEgAkSACBCBIkeAHPMipzISmAgQASJABIiALgik4fnaIRhzwAujd6zGub6DEaUmWp6pG6rWdssMIXi BD9sjULDxWcwvCzzqD ewvxF9 A67BzWjKsLSzaOXcf6LrzbzsHiW4OwKNhMci/PFKWDGqO0 FcSzLaz8/e9ULNxMwRJgyD1Dib7VMX6tlfwbHEwZKdRqjLq1KsHW 7WZm3Rwu0WnDqdw5k3acwxN1EjPV0iAkSACBABIlC4CdBU9sKtH5KOCBABIkAEiEA ETCG/w XEflgFyZ/4QHT3Aw4C6NxePwUXCw9Ggv6eoHr5U99fQYXY81Rq0MAc8q5gwe7ml0QyAvDmYsRSNdlLoSpiH1 EquXX0aGS2M08eSG2ukgAkSACBABIlB0CdCIedHVHUlOBIgAESACRCBvBHgGzH3O/SF4th5T96SjzbbvUE06nJ3 4SViYA/PUrI568w1N3MFWyaO5y9jIIC32IHP03GmE7LPWPfCgL2/oqHN5 QiT5LQzUSACBABIkAEdEqARsx1ipMiIwJEgAgQASJQ3AmwteSrluCOYy Mb MCvTYkqv Os7dv49bNqzj3z2bM7G6IdR2D8c2R98hc l7c8VP iAARIAJEoFgSyHPndbGkQpkiAkSACBABIkAElBP4dAcbtr2Ba5eBqCGZsy4OZ2jvycbLY/AqJmvSuuhTBF7FA/Ze9pLd1ZXHqP1ZK29UrlJFssYcQajboByizoVg ZLLWNCqDWy0j4lCEgEiQASIABEoVAT02tFdqHJOwhABIkAEiAARIAK5JpD6dD8OvbNH826VYC53t4lnI9S2S8al/ffYlm7cIULcld24JXRHo9oueZ/GrkRSUVoCYlNYp4CZsX5H7pXIQqeIABEgAkSACOSFAI2Y54Ue3UsEiAARIAJEoJgSyIjYhR5Ve Jy28O4vaa5dG23EO vnUAoPwAzK3KvSJM7rGpj3OhK2DStN4aV x1fuT/GipE7kFR7EUbJFqLnldWHOzh72g4WaYn48OomDq2cg40f3DFkeLB0w7m8JkD3EwEiQASIABEoGALkmBcMd0qVCBABIkAEiEChJyASibiBb7kjBW uvgScOsPbUnHDNVNUmXQE 5K/xujxHbEpxQJl207DkTXD4Ze1H9zn5ZlnhFLeZWCyaxraN5ZEwbN0Q6XaPTH/2DSMamr7WZvYfZ4wdBcRIAJEgAgQAd0TIMdc90wpRiJABIgAESACRYuAVQvsTc7mgcPApQt2RSm 5Iy9Dm15BETLVWTPqAw6zDnBPiqu5zhtgbprorP7/lwYkyqYGSrCTFl4vjM673yNzjnupxNEgAgQASJABIoHAVpjXjz0SLkgAkSACBABIkAEiAARIAJEgAgQgSJKgBzzIqo4EpsIEAEiQASIABEgAkSACBABIkAEigcBcsyLhx4pF0SACBABIkAEiAARIAJEgAgQASJQRAmQY15EFUdiEwEiQASIABEgAkSACBABIkAEiEDxIECOefHQI WCCBABIkAEiAARIAJEgAgQASJABIooAXLMi6jiSGwiQASIABEgAkSACBABIkAEiAARKB4EyDEvHnqkXBABIkAEiAARIAJEgAgQASJABIhAESVAjnkRVRyJTQSIABEgAkSACBABIkAEiAARIALFgwA55sVDj5QLIkAEiAARIAJEgAgQASJABIgAESiiBMgxL6KKI7GJABEgAkSACBABIkAEiAARIAJEoHgQIMe8eOiRckEEiAARIAJEgAgQASJABIgAESACRZQAOeZFVHEkNhEgAkSACBABIkAEiAARIAJEgAgUDwKG szGf998pdPkOo 5rCQ ZeeUBCukp5TnqZAKS2IRASKgIwJFu97SEQSKhggQASJABIgAESACJZYAjZiXWNVTxokAESACRIAIEAEiQASIABEgAkSgMBAgx7wwaIFkIAJEgAgQASJABIgAESACRIAIEIESS4Ac8xKreso4ESACRIAIEAEiQASIABEgAkSACBQGArzkxASRoiDbzr1UPKX0d896XtnOzza1VBqOThIBIkAEiAARIAJEgAgQASJABIgAESACygnQiLlyLnSWCBABIkAEiAARIAJEgAgQASJABIiAXgiQY64XzJQIESACRIAIEAEiQASIABEgAkSACBAB5QTIMVfOhc4SASJABIgAESACRIAIEAEiQASIABHQCwGla8z1kjIlQgSIABEgAkSACBABIkAEiAARIAJEgAiARszJCIgAESACRIAIEAEiQASIABEgAkSACBQgAXLMCxA JU0EiAARIAJEgAgQASJABIgAESACRIAcc7IBIkAEiAARIAJEgAgQASJABIgAESACBUiAHPMChE9JEwEiQASIABEgAkSACBABIkAEiAARMHxw8xJRIAJEgAgQASJABIgAESACRIAIEAEiQAQKiIAhl25gnWbg8QpIAkq2QAm8fnYfZXwrkf4LUAukA/3DJ b6Z04p5h8Bsuf8Y0sx658A2bP mVOK UeA7Dn/2BbHmMWOOXeIRMLimD/Kk5YESP9agsrHYKSDfISrImpirgIMnS6SBMiei6TaSGgVBMieVYCh00WSANlzkVSb3oWWOOYiEXPMRXpPnBIsJARI/wWvCNKB/nVAzPXPnFLMPwJkz/nHlmLWPwGyZ/0zpxTzjwDZc/6xLWYxix1zziVnrnkxyxplR1sCpH9tSeVfONJB/rFVFTMxV0WGzhdFAmTPRVFrJLMqAmTPqsjQ aJIgOy5KGqtYGSWTmVnJkMj5gWjgUKRKum/4NVAOtC/Doi5/plTivlHgOw5/9hSzPonQPasf aUYv4RIHvOP7bFK2bpVHbyy4uXWrXMjawzhuoLLYHlQzDSQT5A1RAlMdcAiC4XKQJkz0VKXSSsBgJkzxoA0eUiRYDsuUipqzAImzViDtr8rTAoRJ8y8CDbip955p r/4xonN wHtfcv8KIlm7I3E1QnxkpwmnpRAdFOP8FIToxLwjqlGZ ESB7zi yOow3IxY3Dx7EU/e26BxkBwMdRl3coiJ7LgYaJXvPVCLZM0NBfkKuCnXWGnN9TGUXfULEw/t4Z1kRgR7mmW4hUp9i7dhpuFJ5Ev4YWgnm2obLVVYpsCIB2b4CnFuu9eZ/irpKj8eji1dwv15nCJkNcXEV KHKfgpcsJwCfJYOckajnzP65KpoZ5pymAvZihRzTfkuTNdzq7PCJHsRloXsuQgoTxCJi/v240HrxuhYwxb8IiByQYlI9lxQ5HWYLtl7JkyyZ4aiMPoJOjR3XUeVuSs786okcYvicX7OGCy4kZSZlpGNO8rXaIJO3b5AFfs8jImmhGL7b3PxouNCVC1tJtdrbApHN3e4O5jDkJND23C6plFC4hNrWvziepnO2V Z/oUfcHzScKwIzQnDb9gK/FZPQVeZdiMXR85bVZwRIfHpUazfeAAXHr9HKgtlZFsGAQ17YXiP6rD73GEFlfajQowCOK1WB0yepGsz8fXcUNSZsBCjq1tldWKJZRXg5V8/YuxuA/RbPAftXT4XVC4zrg1XndUfCnamSVQtZNPEXFMSdF1DeUUudUZA80SA7Pkz8Ane4K x4/C3509sMCAAZplRCBC6aTR OFUZvy4fjgomnxG3ultkExK5ARDZM1Nd BJ4jexZidILyl6ViJKrU2Tvkta1qnZ2rmAWgcCa/Ia6SnyNIpCtghIx08vOHOsUCZAUx5xy904YP6QKzNM/IS7sHk7u3oRfrr/CpAXDUN1KNgU6t2JLlSPeAz4zReaNuaPdhN/QThyd/BVN4XKbPoUXe3gi9o/Ce uztCH9Vrozxg9ksxcyVc2Hhbsl5zkr6ErGVEFXWqAWxp7Hwl/W4ZZDXfQY1gcelkIkhD3FM5EVTA3k7EOLuLIHUWFnuY4nn27QqIMMfIyMQwYScXbDIXQI6A4voyxZhB/OY93 d yEPaKT0lmJ0df4ixZcdVV/5KgTNOlCg2wamWuKn65rLK8GivU4Mcs3AmTPeUSr LzK/gSU1SZ5TETudg31k 4SKpoxkT1r0Ju 7VWDOBovl3B7L3H2rMFvQIzUYhTtWKMhlcgAkqnsrAxlduKy7 IiZVUG5fzLQ yDVw5EdW8Bvp1yEgce9EW1EFO8OzwPM7bdxoc0dt3EEZVb9MOInkEoxQ3esfUl17etxPbzD/EqhhsHtUCVoXMwsbYk7rdbxqD7FgnvCt vxS/VP2Db9z/idPWZWPK1L4ylMmgMx0WREYObu9di0z/X8Zb1J1iUDkLrPgPRqZp0HVfGe5xfsxg7WKdCeDwnCw WZULQYfBgtPe3VBiJlMhUPP8VsbxyDjmn3ezNjmyd DL9W5ZGuQoVJfqXAyJMe61UV7I4xB2lgmhc2bkGW47dRvgnPqy8aqHToIFoXdYiGUdzfwOM0Kjb4Zgo7lpUMUQbXRmItDlITr84dj9qtWmLegBzzFjqkAr7aPxQ8nKuCXJf1hcmYtVu46jxcfmdDMBoP6TcHYpk5gPr04hznsp6aFetmktvLXtZeISOAM2wB25ZugfU0j3Dt1DrdfJyDdxBmB7b/ByE6MTa79YS11wFzyhMiPgLEDrMKPYOvVlhhf21bKLhVP/v4L9wydYS6IQ3RiRlbZ1VQWUh5g8bDpePHlH5jfwVU8YyUj4iB HL0XXj//D6P8E9WXFXVcOfVwh8x 1NYfrINHk6wCBTvTVI5VysYtmdHC7mXy01 VBNSXV/YMUdCZ8N4ifDPjIj5li9ESjX/5H4Zx5V3LekKlQCXygrZ1SImEoznTsvqJheTaPPI768hW84nPCz8h9KiK5wuXigbbFaW w9ktq7H934d4L2DPES8fGLIq3ZCLWyFdzUIX5xBkz2q1q629pmto52p69lcQkb2rVYS2F0uoPcvsVKXfIGmTZ/kJ6ep9SA53RhzuHtiAzYcu40UCq6kNLOBYpjyaDRuNjp4Z6u1VW3UV0nBZm7/JRlBlTyfur9yoKt/YDEbMYUhLYyN0bMTVpmJz9B/bAfYWQry/vR rdi7GKr/FmFDTGryMeDy5fAsRLl3w3TflYS1MhsjDmjlMEWIMjl Mxdgmjswx4MHMkTXQMtNh8Lnv0t aw6Xg8eZpmH0YqNt7NPp5AK9Ob8Xm2b8g9ddZ6O1nypSbiNf3niCmdDeMGe4D05RwXNuzGVvm8OGxeCQCLbieh J3cM4I0yBjyf6VZlH1GLScrjP1zxy DAHTuPTg8WHA5xwcWVMmu67ETRyx7pLxYOMvmH/WAV8O gnBpT7i1q5V2DB7DVwXjUR1yyzeRrYecMB53P73OiK9a8LZWF4XpvCp7QuDqzfxIKYzPJ2YGymMx7M7UTDy QouEfswdd1VOHQZjenVS0EUG4EEFytmY2rsR5ioXjYTia3EenTH2A5 ME18gsNrdmLDYzc0/KovxnmYIvbaX8zWF2JrJeZ0yDoTVJjPZ sA6Uj6kASeR08M8vwbC7cfxesaXcWdE8IPF7DtZCKq9hsMi63L8D4uhanYBDyRFmVBUXdiD0KdW/prJiING96nIptTdxvGrqD1YfPNmsodwqyqq1bOMkdQtL3syJq1skPbTKVZRdRuVh6KyMgPryyuk8e91g4tcLs Z2YNbMjrQw/LNwCU4a1kfD0uyxo6ksytUTJVkDn1 HlGRqavKeaaOKZV9mu5Lzglf78IfK54uGZ5xFEm6vmYalZ81Rv9co1PMwxIcHp7DjJXPMZc9JNSIW50tkz7nUrpb2qrGdK312Z7bTODHknv2CV3 TvedSNVxwsmcptNz6DYycWh StWefbpuGGQdSUKPLN jmbwtR5AWsXXOO QNpaIsDqu31M/RY0Lco2pF08zf5xqvUfWNTUtPSUpEqSEbMm3s4vuUwonh aONjxpwANjLtEYiaHpLslPWwxOv/JuDE3UikhVjBRKok8zJVEVTFB8ayXKdIvhjbucKzjGTETnxGwCLkDu6PuEEv akpnCjhJnYcjYJb17kY3saddRwAVcu7IjV0AvbtuI32E0JgLZOldABqiGUJQCXHKNyYdBYXX6ciUINzJZGk6P2bzQmX8lSVi yTS6R3Pl6KwV8tzbrFviVm/9EXPrIxhkxdZdedKP4mdp6MRaVvfkHPOpJRXp/BMbgy i cfPYJ1atmreozcG6B7wa/wrw/F2PUJTcENmqKL1o2QjVXU3FfgpV/PfjxV PcvTi0bGwPfvJLXH/Dg2c/b5gmX2ETvS0QWKky/L2ZTXr7SGRVYz8aZasoyYu5e2UEVuZspRwcIs7j5l431GtSG2LR/Qxx 7/f8OBeFNL9S6vdhf6zdSBKRQIbsedbOKJS y/hd2Yn9t79At8GGuP1sb14YN0Us2q64sJe4GV0IjJErNNLq7IgVaeYkZzexKezzpmrKitekvtzlEtZXOJouHi4vwIIZPXHW1Z/bJbWH77mQMJVrcttVp0g1Y1G2Vyy1y3ysknEz/w3u93LXWRJibuIuKywyk5cabJ4eOL1YiX30FRes9kUx8vYHu5l7BlE7iG7CCfjyqLP7O6oyExAY1mUqydKLnHOBKXlVGqP6liQPaujI72WWe9l1XeSK9J6S1oPCpPeq3y aLLdQM8b2HM2AWV6TsXwttJ2jr81np 6hQfyda8W4ha3IGTPudSolvYqq3s1Pbslz2dpnZJZtYhA9p5LvciqE6qfpdWntP7M4Td8wfyGPvCVceJsTmrT6nxI44Tb2PFPBJw6zMSYzl5iH1LoFo3dOCe X529fp4mC/YuxXpRuvlbFqzMhvWT5RjWb3mmtAaOVdDph8FozjaaErFtuiIu7caGvRfwMCwWKQbmMGYzfw39BeKGRFYiik2FrEaGfChxC1h8yMJrFy418gHeZNggJMCBOUjSVI2cUKWiFXbefIhIQTCbiq0YN5PTzgN2YB0Oydz63Mxug4LVTEGmLldYMvVfpismD64MM6kvwje2hbsRCyge/pLXVfbfqVGPEJaRgbhlI9B9WfZMGcZ Ym69xOkWX EZwb3JcPxRtyseXTqDE8f3YvbRHSj75TiM71YBVnYBaObPx/IzdxHbsAEs3t3EMwFbx1rRBqZ2bfBlhevY8ssYPKvXHK2 aIbavsxBlcqWXSrJL82yKdqKAazYKDzS4pEgEELEwTC0ghObif04IYXNJhDp7rU38jrI IT4ZMCUzSYxdqyDbrV24bfdFxDl44A9x2Pg/9UX8DRLwx02IPyJBeTkSNemLGSWM1lJy/or/y2rHCqWFVXlUl7P0nLI6o hyuoPZz57CcPnlFtF3XyObNntUYxDwXHnzF18mgsqtX1xjtj3rHpNIZ6S8lNTec20L/l6X4Sk 1ux4EAsqg bgFZstJy7qqksilg9QUcuCZA9awFMVorlbZS7Tb50s1aBj rniybbTTF/inCRDWpWYJ3JSmoNScpaiFrSg5A9y9mlenvNst6scNnbuTmf3Vl2SPaul6JWrO1ZaoEq/AY2TiM9ZPaZptaHTIt6gNcCa1Sv7soGXCVxZ7bL2G919bNedJnPiWQ65lkzZmSA2eZvAwNgZWQCSztHONmaSraYYg3ZtNd/47dFh8Fv0h/fDfKFLcJxbOH/cIld40aWsjqFpb8zdSKNWxYuS1fS9rHsfi3Dyas6s4EtvZddE8si/ssFzJJFxKZlcw/MDLbYS vXhOWzIgo0esYnh/7NneHl66OwxpzjpcBTyjiTr/i3GYKHTUR3H/lODx5zppmTmxleLsdsLXX5Bp1Rvn4btN43A5N2rsTfIXPxlZcNqjSrCIP//YsbMTVR9uZdxDvXQ9VSTHuGZdDupyWocfs0Du0/gCU//Y2DHadgahdfmMnS4P7KpSf5rk62jzlshW/ILbhIR3qGJO8Q8WHMzaoXCnX7ejh5HTDHnM1Qh7Elx88MFTq0hPOP 7BhiyVuGdbGxJp2zH5jYGEiQgrXQcDyKBvL5ehn2TT3S3LIOHCrETIE6WLZuSXysutivSjqlruuUFYkRSk712y2y0XCHWVU1x ZMmmQVRKVNC1dyJZNUEnmM 2edeDRqLgiIBW/VZVXdyV1beI9bPrfSaSEjMLgusxRkZZHTWWR6mUV7NWdlq9DyJ6Vk IZiOvv9JRUcb2ZWf x7s2URLYHjYGRxEZNVD9fJDas5jnC9uXk6mOhfPtCVi/KtUOUC0hnMwmQPTND0tJeNT0fGVS1z35jsvd8L3nF2Z5l9ZtKv0FW10raWRp9SGE6q5HZ8lnpc4zTTWabgKu31dirbDAx3/WZjwlIt6/iHk/SD/sjbuSbu8HPzw9 XmXgYsOccrkgKe8eMVfcB 07N0ZVX094so1N3Nm WuJDFk7 u wcG3ExY/PNU9kDULzZnPxHPryW4Ywdy6O0QTzu342WzIbn4kuLwp0HH2FY2h9OXLcDd06ZLNLT2WRQlKkk/FaEw/Isc/JUslHCUyR1XI0dysKV9wmv3vLgxF6BVzrz4wYHM9YiUseUjZKVqVoJpZjT TKGdbGxvQysq7RGiNlzHP3vHq5e/gDnOsFw5obFxXo1hVvVLzD4p3n4ubk1Xhw9ilBuuYQK 9FKNsW8KbMTxTDq8qTNNXEacgGFqeDaiMassHATPgxdGqJjRbYZ3tkwuLRsg/LimscY5lxZEjvm7Jc2ZYFnAQc22h/7Mhqp0qXlOcqHsrzJGKjgmkOnXHg19YdWsor1yw55foq/ZWG489rKJotPMXJ2XrJJnEKa8unTdwV9KJZXMdSsMGwvgQd/rcIpQQiG9g CHWe2UoZalUXirb6 VCwb8oWF7Fk5O741PN1NkRF6Bc8SGSQZw5S3uHYvETwXPzhwa K48yqeL5ps19ihPNxZu TuzXCkyeKXlAzlMpGd5 SSrSKR6KlE1s 5sle5ulfR7rR69itvT5G9K Ga2zJbEuxZizpO5ido8iGN7H3ghDg8ehQjbt9m1tNcGpm2rdxec7RHc6urQhBeusac5ZXrhWAfXmYvMlcZyvcoy6izDbCdfNmmXf/g4J5TsK7rCRv B0RwWKb5HEIwkt c7lU3wYOsDf3QAnTu/CId/m8BLFIM6uBhp4yUJIw2sZDpZV0bW5E37euQArjLqjIVvz/vLMduyKcEbboQGwZAJljbxkyZLVeS1/XSZkyfsrtkNt9Z8FT3IP3xR2rFMm5u4F3ApzRpBrNXRqZIdZB37HAl5nNK3oAKNP7xH20R0NG/tBfq 91Od7sfK4AGUr bLOH2OIPrLG0eHj MB1k6ZRAAAgAElEQVTzRjtX9ptLy6ws2jQqhUl71uBdhgM6hDiznW1FbFPcqzh B/DwLAVTwXvcfc225DezhRnrQRKpsh8/DbIp5k3MRWYPnK1wJyT1AvevmJmOzCWbDjJS8ZE55kamnGPO0uDZIrhnNzT Jwk1G7uwDe64dPkwNTVga20 Io31cplrUxbYTu4hIU7Yc2AdVu1n5cXHCqKIF2CbBasst1lI1HAtK/d2g0wmHCgVfLSRNSvhPMnWkMmm6sjGvISvH1fFSP68VuVVfIOkbKS PIjVbL JMu0boFTcW7yK466xmTMObnCy1lAWM3sHtZGMwkioy9XjZM8qjMIM/u2aw 3KAcyfyUfnltXgahCLR6f24sgHWzQeFAgbZr CKNXPF2iyXauq6N7CGVP3zcX8jK5oUckRRslP8U78egLdPjdUZLJYnKb6mVOjdvaqsZ2r4dkviLqisj1F9q6b4lSs7VlTu0/BT6iiwYfk2QaifbAZFmxfjLVGnVHHnYeIG2fwlqmivLh Vm2vmU1H3aitQGKRTGWXPiw4CTILuLhdrbxhbejRHmP6xGLN3xsx56Rk325jS0eUc U2huPuybovexzWCOnfH3eWbMP2RbeYo26PKl19UdtLMby24UxQtsdE/GC6EVv3LcF5ti7X3D0Qncf1x5e WTsyy5wnmSyZqXGyFgct5tl0sjho1r CrviOqNetOa6sPoENR4MR0N8Plfv hLHWW7Dj3/X4fT zDwMrlKnVC8ENfGEuWQTOWRrSedYwjzuJ/X8eRJx4DYopHP1C0HNCDzR1YtPVxboxQpnm7VDuyDo88WiLetweB y8IO4FLu37BxtjuUXvBrD2DMJXI9vBk72PRgQV9uPnrl42JXYrMw x7YgNSWpNasrH56lDTgfMMU9mezYYm7HiKS5P7LtnSwz RhKzhAsPhtz0kw8J MS6FG0MtCkLhijz5Rh8k7gGf 1ejstc0WWvoHDwqgQfa27vCAXdinMry686rhbijRfFRyYw1fUH69r7jHL7ebI18JNN5ZEJKP9XjjnVA8oAZTunsbymy tIgOhbVyF D8fZi0PyuqciOW4udaVurLYmY9oVEsCpBJgOxZG2Mw9uqIKZPMsfmvY9i96ix7CSd7fniwjqLvv0KHytzOhJqeL YabNcEft0nY5LVVmw7ugHzD3DPKENYOZdDTXdZG0kbSUt6GLJnzgK0sVeu5lXfzlX/7FffniJ7101JLMb2rKndp AnzO nyYe0Qo3BEzDAdBP2/7UQ/6YYw8HTSTyrkZvmrdZeZQVBN0orkFh4184eE1WqUQ CVObV0lHiCMREh8O5tG/h1n/KE/z54I6PYbJtTj1lcXr6NI6KB4IQcxL2YKLeHZIXsu4QZQzLJP9lzMFFrCs0P2nHcDELzdix8nnkbAz/MwwK94b9ot3fwtqycn7/gohiJHQDwaXMi6mdgrw6JfhCGJ7Z7/5J/1OGPWDD8Hs9evSUeQixxjTQIXRh1okrmoXyfmRV2DJL88AbJnsofiRIDsuThpk/JC9pwLGxDg3fmTuM93hqu9JfhJb3Dl70OItG Ioe5sn/bC5q/kImfaBJWuMS Ejpk20lMYnRAQT4MqbIYuCMfJlTNwIJwPm7KNMXRsB3ix17UVNjF1ogAWSaHUga4yV0jjIeaFVDEk1mcRIHv LGx0UyElQPZcSBVDYn0WAbLnXGBjG8eGP7mC/ZdeIeYT26mYbwG3Sk0xYmhH LG3ERVXP0BGSLrGnP0s7jnNhU2UyKCFTf GHug ey26yyujsMmoa0Mp7vnTNS9dxEfMdUGR4igsBMieC4smSA5dECB71gVFiqOwECB71k4TPCtU7/cT ygJXgIYSqeySzZqUoKATpUEAtKNzEpCVgttHkkH lcNMdc/c0ox/wiQPecfW4pZ/wTInvXPnFLMPwJkz/nHtpjFnDmV3cRM3e7FxSzXlJ0sArHR4mnUpP8CNArSgf7hE3P9M6cU848A2XP saWY9U A7Fn/zCnF/CNA9px/bIthzOJd2aMiwoth1ihLRIAIEAEiQASIABEgAkSACBABIkAECj8B8Yh5qy59C7 kJGG EHj8 DH8/f3zJW6KVDsCpAPtOOkyFDHXJU2Kq6AJkD0XtAYofV0SIHvWJU2Kq6AJkD0XtAaKVvrF7ZXQRYs SUsEiAARIAJEgAgQASJABIgAESACJZ4AOeYl3gQIABEgAkSACBABIkAEiAARIAJEgAgUJIGs16UVpBSUdp4IJCTE48Kl8wgNfY6kpCRYWFjAx8cXdWrVhbW1jdZx/3n0rtZhlQUc0DJA2Wk6RwSIABEgAkSACBABIkAEiAARIAJqCJBjrgZOUbj08uULHDpyEK1atUKjho1hbGSCNEEq3oWHYdOWjWjbuh08Pb2KQlZIRiJABIgAESACRIAIEAEiQASIQIkkoOOp7ELE396NP7eeQ2S6Ep4Z73F56zKsv/AeGUouf/4pDemqi1hRJmEcbu9ajjUnwyFQd18huJbwMQGH/zmIr/sNgIuzKyKjI/D85RNEvY8U/ 7Pzh86fAAfEz8WAmlJhM8nIGffaUXHPj8/v3QnESACRIAIEAEiQASKKYEi5GsUUw0U2mzp1jEXfsDZFUuw7Q5gaqAkz4IInNm2DceeJEGo5PJnn9KUrrqIFWXK IDLO7bi0N043cqoTobPvHb58iW0bNkK4AEnTh7Fnt278DL0BUQiEUJfPQWfz0Pz5i1w/fqVz0yhgG8TJuPt7XO4FJpY6HWRr6Tk7Rt6tE/in69qpciJQCaBlPtY2KMJusy9iSTCQgSKOgGy56KuQZJfnkB 2LM fQ1qyxUpe9apYy6MvoADD4wQ1K4KrJmzqK joNIFcxeTnuzA9180xKB9UXp3Hp8 ewJ3t9KIS4jDs fP0btXP9x7cB/WltZi9JHvw1GmjCeePH2qL1XoNp3Ux/hz/EQsvRibna0oFWH/rcHEfu3QqH591G/SAYOm78C9jzrt7tFtXvIQW4HZtyr ecgL3UoEtCKQqzIuQPixqWjP6oLeW95ANllLGLUPA7n6Qf7TaTEepaqQID0a51Z8j27NuHtaoNf49bgeK1enaLouF23iue9Z3dQG0y/GK3kupOHZ2t4sjX7Y/lYqrYEFXDy84OFiCfH6MmEsTk/tgqZysjdq1RWDJ6/EyVcpEKnIAp0u7ATUtBk02Jcw8RH2zv4GXzbm7LMxOgyeid0PVXdaqwsveL0JvRXLhvT3yNM5Z9iRPRd2uyoo VTYc0YMrm diRHdW0rq3 ZdMHzuAYR Uqy50hF77yCW/TQU3Vs3RpN G/BS7VTVvKYn4VTi7JnacgVVQD4rXR2uMc9A1IWDeGQSjNlVrLhBXD0dBZNuRvwTnNy6Eiu2XkE0y2k5PeVWPpmPbCq7ibEJGyHPQHBQMLZu34z69RqwEXQe 5 PdIEAhgYGSE4uXmMwosRbWLf4CD416ItJg1wgCj2KlWuW4Ed4YceUEFjqz/j0oHVFasjQ4iULwJaF/GhYi5sACj51xBmgKSjE8fkcp3Rddfp6Glk2QKF9 kFDyMlbFLw/NN4zBxSxKaDp O7xxfYd/CtRg3yQqbl3SGu6Gm6/JxZiDhXQxbrpWA44t3oFeNwfCTS1MYfRJLtrxiNzgi8iO3qIs9ho280GPun iRGU06iyMSaT4DMXdsdZinJeL961s4tGEzpo2IhtW2yQixKlYVnTKlFKtz6tsMGuyLH4tzs7/DgnvVMXzmStSwisDplbOx8HsB3P76GbUVR0JYx4668LVcWmHa8mrI8pMEeHtgFmadcEEjP1MF7mTPxcoQdZQZtfbMM4Ao2QRVuo9H79KmSHhwECvXzsV4y/LYMrwsxNWh6BOebpuA79ZFonL7Thg45RuUcSkDVxVeSZ7Ty8w32bOOTICiyScCKorAZ6SWEYXzBx/DNGQAAqSekSjlFY4tn4fVB28jMs0QDmXLwzCetUHkoxeE47 1v2P53st4m8yHTdnG6Dt2LLpU4uHK5I744WlXrNsyBH7im4SI2DsYXZfaY9aeuahvwxomiukKk/B47wLMWXcCT PZaIepC p9uwgz2rmJRyK0komFi7m0CEM7PMKzmAyYuFRH 6E/4JumpWEill2AsENzseS8C7pO/xF3fp2LWPk86em7lZU1UlI sU4QPipXroKQ4FpiZzwiKhx85pibmpgjJTUVlpZWepJISTIq9WuBuFNT8dXUh2ixZAO q2YJXtoLbBr6NbY4TsKmWS1Ys1VyvFrRC41XSL5XnXEYSxuFYOK2HeAbGUg6gOpXhcXdC5h49yYi0kOktqJElqJ4StG pQNs6u2TZZSNvlzcsADLdp3Dy0TAyqseuo4ciz41HSQjchwLbcKwYDn5F6A9FUUdksy5JsCz0q6MC17vwdQZ1xA05WcYLx6Pa3IpCZNjkWxQChUCKsDfVoMTm3wP23aGotSXyzC ZwDM2Jh0ZYvn6PbjFux62hajPe rv15B8mSQJJ O HfsQWfiApu3O7HqXGf81sSe1dLckYIHW1bjhrE7LAQfpI45Oy14jlVf9ceROquw/bsK0ucMO2/tg4AqVWDJ3RpUB8EOT9Fu8h3cikpnjnm2J6kkafq3kBLQ0GbQZH9eL3DqehK8 w1H1zqlWR1eEV7fPsSxgSdxNSyNOeby9scQpGoIX8EBfpUdMlmlh 3GshOxqDZ6CTqWVrQrsudCalQFKJYGe bbIGjQOATJJAwqC8H5s5hz7zWSRcwx54mQdGcZJm3hY/CfG/FlGaW9pXL5y2t68qgKlz1TW64AzbiQJq2zqewZEWdx8Kk5arYLgLgjXxiPK7 Pwq97P6DqwGmYN/8XfF3TEmnyM1lEibi1ZBQm701Bo3GLsXLpL hkfQlLxv2OywnmKN 0MgzDL LWe lWcaIEPDgTCn75JqgoHS1QTFcQugVTF/4Hy06/4H rV2HptMH4ooq9dHqgFjJJFSVMs0Gt/lMwZ85U9KsYjp3TRmLRjUTpFEIjePRchf2bf0Xfms6skikY7ZYr64 3YW9ha2OH2LgPbCf2NwgLfyt ZVq6IJ2NmvOQnp6ODx/eIybmg/6FVKtfHuwbjsEPDZKwZ Za3E1Kw6tds7DuXU18P64pHOX2KHDpMhtr1q/H vUbMDnYguWDBwOZU87lKiMJkbECGLl5w17Z3gb6z7nOUlS0b1nEau1TlIx7y0fix/Wh8Os7A7//PgO9fZ/jz3GjsOrBJ0kU2oSRJpaTv86yRxERARUEtCjjqc w5ec1SOwyE9/WspM6vlnRZSRFsfXahkiJjkJ8mvplLoLIW2wpjCkq1fdhTjl38GBVsRHK8qJx634MUjRcz76ZaQYSoxPB8 mB79ub49LqPXghHc4XRp/CqgMfETJsIGpZpLF6W8tp6UIBPoZdx4F9DyC0r44azrrrU1ehADqtUwLq2wya7C/DsBR8nYA3Zy C eHsECDq7l3EWFREdTclTk1uwrNNqC4tX417jl0x6gtX5HyEkj3r1BSKRWTq7TlbFjMS8fribuwLNUONlhUlMxrZvjn/rT6ACGE0dn3bFg0bNEWHAT9jyy1VezvlMb3sAhWq pnacsWiQOg0Ezp6uqcj/OwhPDOvhWGVxH37bIncRWw8Fgufof/DxF5lJI5xVXs8OngJt6RZ4ML8eeADAiesxODmpcQNK/8fo/Ff91U48OgTalZpgUr833DyRgw6tXEEL/E jt8XotyIQNiKuxRyppuRGMkmEFqhdo1gBJS3YM2rCpnAtJFJFtihQX/07ygZuagTXBYZT/tgw6YrGBLYBOLBFzYiXUD eGZ QkJqYvOWDejVozdsrGwRHx PpETWFDUyggGfj4SEBJiZWqBvn/7Ytn0LunfrCQcH2Th0ZjT59kW9fpNRO6QUGo35AfV6T8MvMxNgeekNgifMQlN5r5xJZ LgCV9fqQ3lkDYVr/b9hhWhZdFvdUPY66yrKUdCBXAip33LhFBnn9ZxF7F2zzt4DNyEST29xDNUQgI9kPK4HzavvYxe8xtBmzC20sTU8y8ALJRkCSOgrIynIXT7TGwT9cCy3uVgikcKTEQQpLAZWKaPMG9AF8xlTyCX4O4YPX4g6jkrjgiyvr2ECHxkzw0X66xHIs/EAWzJN66HJyBVw/V0yDk0ojTEx6bAwNoNNXr3Q8Ujq7Hpejf8XNsUz/euxy3b9ljZyAP/bhThacRH9hSzzz6LTD4ntyajVX35Ey5oM2swqhWv9Tolw57VtBk02V 6UTl0 mk4bny3GH16/ocmVdJx7VwKOs/ AXW4mYOKh5GH1uHTww5jzX8ZqP1zN/gpDLyLoyV7VqRLvzkCauxZAkiEmGOj0HHGbfE G7YNJ2NGa1eJL/DpOf57lAHbmi3xdacaKGMWj5tbf8PSMT/BYusifOmas3soT nJa6yQ2TO15ag4KRLQjRuTzqajHw6FRa02qCjxy5EWfh9vhfaoWs1JUhAVU2a/08Lv4BUb0b3565doKN14pFH3xXjOpvtFR7ORPftgtA3g4eGRG D24El6eBQ30/zRtraTpFdXSbqm5XuhT7Uk7B7ZHd/M BPHHsZmbgakjUxKxGRz710QGGCD9Ff32ZR8pSEK5KQ1m8replU7bN66EQ8fPhCPktvblYKhIXPMDYzEG8PFxLwXO hdunTDdrbbfGRUpN5k1aRfrrLmOzTG998FI 7sMbz0H4YxTR2V9NirEFmUgtDdP2H44jA0/nkOeittVai4tyicVmLfSsVWsM 0d7cQmm6P6sEuWQ1 IzfmnNtCEHoL4cyGtQmjNC06SQT0SUBFGc IPIaF2xLRelx3 CpzJli3qU296dhx Dj O3UIW34fhgovt2Di2I14nt91ONsBN4Zt62FqY8ZmszfHgMZ8nPnzON7FXMPGvdEI6N8N5SzMYM2G5pNikpVsDicHuNxI/I/NFlr352os 30KhjQ1wOFJgzHvkrJN5fSpGEpLvwTYplfhr9gIoyead6iHMkZ8GKQ8x6mDFxGhdLMsbcOzte37d O5bXN8VUe23EIhZ2TP lV1sUmNB9s6k7F2xSL8 t2XcL08E4N OYn3rOEnTI7Ce7YJp2ez9mhaoyLKVayNbmO/RXXRbfx9PuozX6esOr1sSAuzPVNbrthYf14yopMRc0HYaRx YYm6o9k0FZk00k5ckVBxF0Y5ccWXLNDgp0UY7C/fuuLB1IFNTWSv wrpUA38mQdw5UMt2B9kG/xUHoU6jpL BKXpmvqi16K9qHf5IP7ashkzhmzEX/2WY8nACmzdtSRttTKposleQcZtqlbgw QK8nl6eqFfnwG4eu0y/jv3H9LSUmHMNoTjpq 7u7kj n00mjVpjrCwMHTv2hN/7dyGTh27ws3VTVVOdXdek365lIQJeHr1Gdu4ibF9fBTnwlujS441bkpEYg32F7snYviSd2g8fTnGNsyFQ68kusJ4Sql9qxK0kNqnKnHpPBHQSEBlGWcbvl35GzeTInBzWAvsko I7Ufxxa252DevdtazyNAaHiHd8MPY67gw4TjOhPWFr3f2UXMDK2c2Xv4REQlZk9JFqR8QwRxsa1drmGi4nu1Byhp caxf2ZStXxLBHYpwvc 23E0mU2uGTYDPMbs45lfjSsTUVIYQHVTrI3d4WPr680L URULUMYu8Mwb7dDzCyllweNcKkAIWZgCb748edw 8zj8Jm1HZMaufMOq 7oXvb/ HrEb9jcbPamF3PJlvTRKht NTnOHIiCqUatYW/ZA1HTkxkzzmZ0BmtCPAtXeFXiftUQ4D1K3Scvgn/RjRCV1MT8YAd1zGZARvxYAzPzAlubPuasKhEsWOuZMxcY5qq0uvmJhdbYbdnastp1HNxD6CDEXO2KcOpI3hlVRdtKnDrfyWHsWs1eBnG4OrFN1D1dhpj10oow0/C0xc8uHp5wSvz48mmEHIFiQ 7ml1R2 Qu9rCRj92XM1Cja12UEkutPF1x6nxzeNRmDbElW7G0kz2e7NqBRymANjJJxc/ J UFzt1IgLFvVbjknAWp9BZ9nrSyskKTxs0waMAQDB86Svy3b5 vUT2wBnPU0 Dt7SN22B89eSR2zvf9vRtv377JdxE161eI2AuLMOukHQasWIWhvg w7Ne9eCMbAeAZwYL116TEpyg0XkVIvPk/jFvyAnV/WYpxzCnXSQ9TvhPJTQJq7FsxGgX7NHarBm9W9m5ei2ClRHoI3uHKzTgYeVeFK1uSqE0YqOSvKAD9JgK6JqCujPNh33g6Nm/ahE2yz9pf0IKtvXDpNherfqgG8xziiNjbK7iT7I0VOa5xk6ICUdkqBffPh7L5WtzB0n9wBk FjgisZM/2EFV/PVsjMiNF7JibWJqIl2cZebRF38CPOHf0Bdy79EIVbho6zwSWrBx iuMaptofIkEyPrIRfwMTwxxr6rWPhUIWNgKa7A8fHrNXTVmwNpLEieHs2NI3BOVMUxD 9mMOG8rQMrzg7TlcfG N4CbebDmIioPsWQUYOp0rAtzbgpilCjJE4FmUQXm29 Dry4/xUTp2lxH3HM/i HDxZbM cxWxisBy6WULUZjtmdpyKpRZsk7n3f4Fb/HvP2/YtMEfUF6uNcS3q43Bnd0xbONYTBIOQccabjBOvIPXyVmA fZ10Z tHR z5UdM4Q9C 0BXGCeH42WcN1q1qwQr1qrhWQeiWxMbjFyzCLBpgQVBNpIGiYp0BeGnse8y4FvWGWaCCFx7zt7JaekAzs/XRiaZdIkvr Hi1U wSA3D1V0rsT3SE31 DYay5VyF0WRcXVzBfQ4c2o//LV/CprYbILBadVy5ehk9uvXC6rUrMf6HSfkquib9WiRexfK5J2HdazV6VvKHweRBONlvBX47WA LOrJd9I3dEOBliH2H1mBHxc4oiyjEONRHywpJOLrsb8RUHIpWLjF49jhGkgCUp5eMLBRFnTO1 zqvvIVdi3VvZpWxuDOrlh2JoJmG3CGPkCTw8tw7q37uj5Uy2xDfO0CMO8d X8K0vLoO5zTTESAQmBjHD1ZZyNxHhmTs9it6SmwMaIBxP70vBwMgNfEIbjm44jydMfpdmGJB9fXsbu1ReQ6j0ADdmMHGHMafzcfxoe1JmH9eODYWVeGT27euPonzMwv8xItHB4jX1//IuUyqPRuSzrHTTUcF1eb8IUJHAdwebGkk4AvgMaDB KtjsT0Li9h2R5CXudkLmZAYTslZepbMhcPivZTCDhOW7ftGLPsk Ij3yCi39vwT/xjmjP9j9RNcBJJlQECWiwP6O0EATZb8KRP1YgYGQrlGVrcu//vQhnU9zQs7oj Myep8jbs6v68JKGnxBxj67hHd8HQ7xUuuVsVhvZcxG0qIIV dND7Nh0Axb fmyQTYT4l5ewa9UNCMsNRT0XZn1GfujQyY dW4B5O83Qu1I6rqxejkc2TTG3FuthVbRnTU06TekV4vpZra hRTuN2nIFa r5kXqeHXPBmxM4GmaDuhPLZx l4Jmj8rBlWGi7GMt3LsDEzdzYnRFs3KugsbeFZJoKzwpBY5Zhtv0irN43HxM3sbEDAxv4NP0WDdsyx1ycY3NU7NoB7gfXI6N1d1SVbnqjKt101lN8asNfWPyeS88QdmUbYsS0vtL3yGohE98KvjUqo9TZdZjC3hHKyexQoTGbMj0K3cureXjlh3Z0EKfM Z4zbxZ7nVoIXr9 w16fprIZqIMU5aJQq18/RGz7A0fQGgt7cZs3scOrC8Z22YehK5fhIhsRq29rj0Zjx Hq1KVYOeUCU4UjgodURjPvSFx9IUJ62nKMGSwvsiO6rdmGUdmWReg2S/qKTZV9Qxv7FJe9pZhr/jtbnzoFx9l0XEv2urSv541F30pmEmdBmzB8FfzJMdeXGZTcdFLe5K2MM2fifeh/2Ll1LaK5KVumTqhQbwgWjOwJHzbriZs LuKG0DNXWhnDt898zE6ZhUXLJ FomilK1xmA eM7orT4KanpupyqWNqJbFRbNmLOXTEt1w3jJ8ur0wDGbEQdUXH4pHQuuwGbQu8Eo9N/YsK3kvt4Zg7wrtwMIxYMQOca7PWS8tHR9yJOQIN9GVbFqIWTYPTHOvwxerd4VodF6WB0nfY9BpZjdsT6prPZs7mG8GJaaYh6FMHtygVXMzXWRPZcxG1L/ ILP8Uh uERbNz6CvHclCALN1RtNApLhneBp3jWqRG8es7F3JR5WLJ2HIYksz1B/L/AuIXfoZYNHyJFe9aQBc3pyUVQWOyZ2nIatFpyL/OunT0mqlGv WcSEODZyl74 mAQlu4Yj6p668IvqHQ/E1MhuO3v/Xvx6PHDTEl8fHzRtXN3PH78GP7 /uLzfx69mydJB7QMyNP9JfVmeR1IGJB957ct5GSe3ylS/EQg/wiQPecfW4pZ/wTInvXPnFLMPwJkz/nHtjjGnLcR87SXOHY8AnYNWqveOCQ/qBVUuvmRFz3F2aF9R3RARz2lRsnkiQDZd57w0c1EgAgQASJABIgAESACRKCoEciTY5724h ciLRHw1ZlVW8ckg9ECirdfMhKoYqSRrwLhzrIvguHHkgKIkAEiAARIAJEgAgQASKgLwJ5csyN/Udhz9lR pI1M52CSlfvGaUESyQBsu8SqXbKNBEgAkSACBABIkAEiEAJJqCD16WVYHqUdSJABIgAESACRIAIEAEiQASIABEgAnkkQI55HgHS7USACBABIkAEiAARIAJEgAgQASJABPJCQDyVPTY2Ni9x0L1FmEBCQgLpv4D1RzrQvwKIuf6ZU4r5R4DsOf/YUsz6J0D2rH/mlGL ESB7zj 2xTFmGjEvjlqlPBEBIkAEiAARIAJEgAgQASJABIhAkSFAjnmRURUJSgSIABEgAkSACBABIkAEiAARIALFkUCedmUvjkCKYvde2IEAACAASURBVJ4SEz/i5u0bePPmNZKTk2Fubo4yZTwQWLU6LC2ttM7SH9a2WodVFnBMQpyy03SOCBABIkAEiAARIAJEgAgQASJABNQQIMdcDZyicCks7C1O/3cKrVu3RovmLWFsZII0QSrehYfh7wP70KhBY7i7ly4KWSEZiQARIAJEgAgQASJABIgAESACJZKAjqeyC5Fw/xC27bmC6HQlPDNicGPPOmy/GoMMJZc//5SGdNVFrCiTMB73D6zHlrORUJYFdVHp 1piUiLOnD2FAf0HwsXZFZHREXj 8gmi3keKf3/Nzp9hTntScpK RSt66SnawefkQBdxfE66dA8RIAJEgAgQASJABIgAESACRZqAbh1zYQwub1iDPQ9EMDVQwiU9Ehf27sXp0CSIlFz 7FOa0lUXsaJMGbG4sX8Pjj9MgFDdfYXg2u3bt/DFF60BHnD8xD/Ys3sXXjwPhUgkQuirp DzeWjRoiXu3btdCKT9DBFEnxB /wquv9KxvSgTRdEOlIXRdE4XcWhKg64TASJQ/AikPsaqIZ0xcOldJBe/3FGOiAARIAJEgAgQAS0IiKeyR0dHY/LkyUhJSclxi4GBAebOnQtHR8cc1xRPCD9cw9EnRqg2qSIsmbOor0Pv6YrSEHFpJ9Zu/QfXXsUjw9AOfnU7Ycg37VFejxl/9folmjVrjpi4D3geGooObTti/6F9CA6uiY J8Yh8H87Wmnvi5L8nUTOkjr7Uobt0Up9h64xfEdp1Oap6WoDWXegOLcVEBEouARGSn /HnMnr8LHfGsxv5QBVPdSipGc4snYF/jr1BLEZBrAr2xDdhg5G67IW4Gn7HMiIwP7vhmDNK1XE/TBy1Wg4lS6D0k7Sek4Ujwtzv8eC89FIk95mYOEEn4AG LJvN9Qrbcr1x9JBBIgAESACRIAIFCMCYl Hc7rbtGmD8 fPw8/PLzN7Dx8 RKNGjbRyysEmp7 /egxPjavhp4qWemw06D9dUdI9bFtzEim1umL0V04QvTqFTVvWYjo8sPr7QFjoqcXEbfpmYmzCRsgzEBwUjIOH96N vQZsBJ3H/ucjXSCAIetY fSJxmCKUZmlrBABIvCZBDI PsfZ3ZuwYc8NfGBx KqLhznHlxb9hBWPquDrSfNRxTIKFzYuxsqpAjivGocaPC2fA3x71Bk9E55J3BysNLzaMw9rnlTFN2PborQRO8W3gEcpT9hNXYgvZfKIBPgYyZxyz68wdVgAzARJiHl7Dyf 2oV54z/AcuV3CNRjJ7A6THSNCBABIkAEiAAR0A2BzEFIbvOw06dPIyoqCra2tkhISEBGRoZ4UzGtjoz3uHL8OUwDe6GC1DMVpbKNydb/D5uP30d0mgHsfcrCMAHZRz4FUbi4dRk2HL6Bd5/4sPaui67Dh6G9Pw83Zn2NX160xaJlfeHNNWDY5PKow2Mx6E9bTFo3FbWsmAesmK4oGc8Or8DSbWcQmsAmzJs4IWTQr5jQ0kWcrlYysXBx11bhh/PP8CI2A8ZOAWjZbwT61XeDMbvGswzEtytWg29kIOmAqFUJ5g vYubDu4hKD5TKqhW1PAXidlxPSfnEZOCjcuUqCAmuJXbGI6LCwWeOuamJOVJSU2FhYZmndPJ0s0r9miPu/BwMn/MUjWYtwZDKbAQq7TV2/Tgau0qNxtJJjeAgTfjNhmHotEHyo9KErZhdh VHZbysUygjGmeXz8OWyy/wLj6V0xisPGuj8/AR6FjBSqwzrexAXRraxpEneHQzESACuiOQjojj/8Paq05oN34kHvyxFPHqIk99jfN3kuHRvT/aBbux50c5lBn0BKfHnMXNCAGCymr5HOAZw8EvQFqfpcD4P/YUee0E/ypV4cc9ULhD8BKbBn Lk8G/syntZcXPGfFh5YEKFSvCgvteNRjV7EPRZ/YD3Hufzhxz8UORDiJABIgAESACRKCYEMh0zI2MjNC/f3 sWLECJiYmeP36NYYNGwbuvDZHRvRlHA81Q/U FSTT2EXsFV7LJ KPUxZo1O8HNPQyxPt7x7A1VM4xFyXh3tqJmH3KCV2Gz0QthwRc374Ea6cthzsbkSjbwB8Gl67jXsxX8HZmi9ZZnE8uvgTfbxT8paMFiukKXuzG3JWX4NhzPH4LdoAo5h0SXO0knQHayCTNrFBgjRrdv0dvRyFendqMjfMmItVmGUZUYQ4k 8 AOeWZR0YyouPTYejiAVs9zrf28vTGW7Yru7u7O3PG3yGOTWkXCNLFSxJ44lFzHtLT0xEbG4P4 DjY2OTtdWja2EG2MBr0G1R7KEbUGoa5C7ei/uJ sPpnIbZGVMe3P9WHA4dXIInNqd1PmNDciemQBzMnc2YH6u0myDQJL28/Qoxnb4zvVBamn8JwecdarJ9uAM/VbKTLIjHPthlkqUUcuQZGNxABIpB/BAzh3nE Nnbig/fpJmZpSogtUfJivYPnL11DeJv2KGOcjg9sFlmseTlUdeaei3p8DrAR9MTIBzh25AmEdnVRxVGPDxpNnOg6ESACRIAIEAEioBMC2Z7uVatWhbe3N548eYJy5Vjjg/3W7khH1KXjeGFWA/39xX37EMVdxY5T8fDs9xu 7eQucYwr2eLpceZoSyMVxV/DtqMxCPh2Pvo0tBOPZPqO ICLQzbh2NNPqFGxMcrzF Hs3Ti0cS4FXtJjnH4khM AyrAWTxfPmW5GUjQ whI1qlRDBT9zFme5zCxoI5MssH3tHujRWjJyERzog/TQEfhr5030CagHm2xT1dPw5sgSbHzpg 4L6sBOT9PYOTmrsBGX/Qf24quefWBjZcuc73gkJSbBkHWmGPD54lkPZqYW6NunP3bv3onWrdrCzs4 k0d f9Gk36DqdqgzdARqDp H Qs/wuLaOwR Own1xV551mFi7w4vL6kNsdOiOPV2ExQgudfcIxDB1TkdBiLAORLXvv8X516lorqbDmzTW3Mc c2X4icCRCCXBNhMIq2raEN3tBnzNe5OWYORQy hXsV03L6SiraTRyBI8gCSSzyfngP3ZqNne/k8OqHZpD6orK/1UrnES8GJgIxARkoSUtJFko1 eYYwNsiAQM1vU3NTGGpdOIkzEdAvAbJn/fIuyanl6Hb/ uuvMXXqVPHoudYH24364olXMK8xEOUkfjnSIh/jnYg5XpUds09dl4s0jY0AvGXT5WP/6IcOf2RPzSiGbUQXWA3NK/Cx5OQdxDdtDOMnp3BPUBb9gxwgdt2UpGtathO6Vr6M9ROH4GmjNmjbrjXqlbURy6CNTErzbOiIgIpW2HrrMaIFzDGXzTMUpeDV4TmYtDocdcbPRRfvzAmISqPR9UlLNkW9Yf3GbH37BoYqEE6OzrC3K4VkNr2dm8ru6urKliZEsiUJQnTt2h07dm7HFy3bwKGUbJK4riXKHp8m/YpgDr59XQwdcgLfLDyND WHY0p9qW7ViKY53pw3G5Xyhj2S8CEpQys70JRGqrlm 84pBZ0hAkSg6BAQIjnqDSKFpdHwixA4h1/C3ZSXOH/sGlpXagIX2dMzP58DvgPw2 hqMBOymVBxb3Hv5DZsnvU98PMijKphrX0nQ9GBTpIWCwLJuD2/H6ZdkW1d6ItWld/gyD1VvwMwedtM1JS2H4sFAspEMSJA9lyMlFnos5LDMec2gps fbqWG75J8pcecQEnX1sgZHA5yVo47jTr eSxvlKRUM2L0dglzjmrNeZX9PEzkYPFg4m9jXgDs8AvKoO/8BhuxgTB9vhNpJUfhKBSkj10laZr4oVOM9ej5vVj2MdeH7Zg7A783X0OZvUqx5xVLWRSpTLxu9PkunNFqXh9cCbGr4lE3QlzMKx2KUlngar78 m8u3tpdOzQBXfZK9EesGmWAkEaW35gLJ6 7u7mjuj30WjWpDnCwsLQo1svbN xFS2at2JOvFM SSQXrSb9ckHZ8oLQW6FsSyTG9vkpXI5shnZuOcwyu6wa42UbGSgefAO2El8keQWeNnagKY23ebAlRdnoNxEgAoWOgCj Cpb/cQrWA1dhdEtHVr93wJfN12H0hOVY0yAYk2uy/Sry zlg5gxPLy/pc9UPFSq7I 7BWBw5 AQDawRlPW8LHT0SqGQTMEXZPr9gRrt0CQa2waGDRSrqfFT12wrepiWbGOW MBMgey7M2ilusin1gLR5NVoWiHSEnz JN5Yh KYcW/8rPYydK6OMwRHcvBbGnGmfrM1s5AgaO/vDnXcEL17z4Ny4jNIwttXboYbxLBw8cRq2N4So m0wJH658nTF0fPM4B7UASNqNEOjVSMx8cB POs8DpW1kElOvKyvKa9x e5HGHtVhHhpIXPwku79iWlrXiPkxwUYXkBOuUxACwsL1KpZh32yROYc8vi4WIS9C2PLE3xw7/5dPHrySOyc79i1HU0aNYOLi6vS7OrqpGb9ChF/ZTUWnbVFz3k/w3jlD1j3xyFUn90B7pxl8oxgziYhpHxMzfZOeY3xStemq8qHLmxT9Lm2pEooOk8EiEChIpAe wyvUixQxcNK2unKg4VXNfiY7EN4eCJ7D4klUvX8HBAJkpHEBh0NjA1VvuKtUEEkYUooAT7bcLUSe81p9uy7K9BQ/F1CYVG2Cz0BsudCr6JiJKBSxzxX RO8w7l/38EqZATKmmXdybMJQu92rvhxx8 YJeyL1lWdYZT4EGGf5MLYhqBH81KYsns6fuP3RssAJxh9isKbeA80bekv3kSOZxWADvWsMHHLarZDbSNMryadvqci3fTIC2AbvMPLxxGmbFftWy8TAQt7mLNBdm1kkkmX/OY2rt36BPPUcNw8uBH7osug68Rq4DaCR0YkTq37B7H /dDUORYvnsVKbuObwL50adgby42s5wqm7gI7OjiC /x7 iT t3wJuPfRB1arjitXL6Nn96 weu1KDBk0THcJKomJp0G/Fom3sG7pWVh2/B2d/P3AH/MV/hu5AUuO1cSvrdku sbOqFDGAEeOb8H cm3hI3qPWPtaaFJeg90okUX lDZ2oEl2Sy3sW4MYdJkIEIFCREAYex7z2H4n/2fvPsCiOPowgL93VOkgCFgpoqAgFsDeWzQaY waS2yxJ362qNEYNcYSjR17L7Gb2GKLLfZeY8WKFBWkl4PjmztAEY4mcBzy3hOfwN7uzOxvht3978zO3vP8CfOHVoaRdRW4m23D0SVr4dKnMRz0Q3Hv7 U4H2ODtm5FoS3OA3/n9Xkg7Alu3zSCflw0wgJ9cPHgDvwTVhTNxfwn7GDUoMbDolCAAhSgAAVyQSDHgbns5Ukc8zNB9WFOSBGXK3utncXEb1NMVmDtHm9M3a4YwqQDE9sKqF3aMPFuv8QI7t/OwI/my7H wGL8si1edAWYoEzdvqjVVATmygfJi6DcF5/B9vAWxDdtgwpJk96kl6 il P0lj xIkjRbaoFU4da6D2qIxyUj39noUxSI9i5O8Ps7CZMn5hYZotytfHNtD5oUzbpUijmJa49S0B87BpMEI/7vf9Yos2cJejz7h04Kb/Ln5 Tg 9lK7zF69S8xGz7z2FkpKbXp2VYv/YI3LUE/6AxprRzhPJBhlKtMKj1AYxatxqXav AGqZijgLxirNrM1Zi3fSLYjp/S1Tp4Yx6LqUybjeZUedK28xCW8qsHPyeAhTQKIGkqaoSy1SkIvpO/R46Szdj2Y/7IGY9gUHxyvhi1EB0dRQnlMg8PA IybKMrS2hc3ozpo5PLI5E3wKlneuh9 QuaOWueDsIPxSgAAUoQAEKfEoCkkunDiU4VPT4yH2S4fG6gfjusDt XT4UFdV2Cz /8v1IJg3Y7Og/h/HI5 G7kpQuXQafNWuJhw8fomzZssrlv5vk7HVqw0PfasCeFrwipKyDglf6gllimhfMemOpVQuwPat24dKCKcD2XDDrjaVWLcD2rNqFS1UL5KzHPPY5TpwIhGmNJnBUW1AudiS/8lVtWCCWNhYTwCn 8UMBClCAAhSgAAUoQAEKUIACmiWQo8A89tkxnHxlhlqNHNT6vFt 5atZVZf7pWGPd 6bMkUKUIACFKAABShAAQpQgAKZCeQoMNct2wer/uqTWR65/n1 5ZvrO8IEKUABClCAAhSgAAUoQAEKUKDQCyS ELzQMxCAAhSgAAUoQAEKUIACFKAABSiQPwIMzPPHnblSgAIUoAAFKEABClCAAhSgAAWUAsqh7Obm5uQopAImJias/3yue9aB iuA5uo3Z455J8D2nHe2TFn9AmzP6jdnjnknwPacd7afYsrsMf8Ua5X7RAEKUIACFKAABShAAQpQgAIFRoCBeYGpKhaUAhSgAAUoQAEKUIACFKAABT5FgRzNyv4pghTEfQoNDcGZc6fh4/MIERERMDQ0hIODI2rVqA0TE9Ms79LJb7tleV1VK9ZbulHVYi6jAAUoQAEKUIACFKAABShAgQwEGJhngFMQvnry5DH2HdiLFi1aoEH9htDV0UOsLAYv/XyxfuM6tGrZGmXK2BWEXWEZKUABClCAAhSgAAUoQAEKFEqBfBzKLkfI9R1YtelfBMSpsI9/jfObFmPNmdeIV/H1xy/KJN MEk5dJvlbXN/ujRVH/SDLaLs8 i40LBT7/96Lb3r2ho21LQJe ePRk/sIfB2g/L2XWL5v/x6EhYflUQkySTbOH0fnjcfU3c/yxSeT0vFrClCAAhSgAAUoQAEKUIACGiGQf4G5/A1OLVmAzTcAfS0VFjJ/nNi8GYfuR0Cu4uuPXpRZvhklnLpM8W9wfusm7Lv5NnfLmFEZUnx3/vw5NG/eApAAR44exM4d2/HE5zESEhLg8/QBpFIJmjZthsuXL2QxxVxeLf4tbp84iau 0UhQJB19G3M7N0L7mVcRkctZMTkKUIACBVaAx8YCW3UsOAUoQAEKUCC3BPJtKLv81RnsuaMDj2mVYCICS3V98iNfeeBu9Gs3G/dT7qRVByzfPAzOeh /5w8e3kfduvUQ9PYNHj56hO5de2LD5nXw8PASveQhCHjth1KlyuDY8WNimHvjj88ot7bUMoRNaTuUtjFKfE9fbqXLdChAgcIrEB Ey1u8serPk7jxMlLc6bWGW9OeGDm0FRyKJJ1c4l7h3xW/Yv72i/CLKYJStbpixA89UM1c9b3pDI/ZujHwPbUeC1f ibM bxGvY4HyDbrhHt4WqcTnqRPvhn/Ur8cfA87r2KEXWlCwv7SqjTdiAGfVkOhqmPjfJgHJ/UD1OOBSA2qWa1jGzgVLUJOvfviUZl9BX3Y/mhAAUoQAEKUOATEsinwDwegWf24q6eJ36tZKzGC4z8yTc KgwxUlt0mDoJzYslDg Q6hVFad2ctaQwMZRdT1dP9JDHw9PDE5v 2IC6deqJHnSJ E KOJkM2lpaiIzUkP5pHTt0nrkKnXO229yaAhSgwHsBiRYSIvVQqdMYfF1SH6F39mLpypkYY SMjYOcRAgci0frR2Lsxgg0HjQZ31s9xe65KzFynDE2LGiHEirOghkdsxPCr2H1/AOIqtcD4/raIMHnIJauWIDRsMPWCV4wShUxy0OvYNGg77D1qQ282vfGWLfi0I18jRcPb BRuATaivXTHBvjEPpSBOUOfTBzRFUYxIbj9bNr2Ld2AyYNfgXjzePhZczQnH8GFKAABShAgU9JQMUliRp2Lz4Qp/feg75Xb7glXcUkRD/FIe9ZWL73OgJitWHp5AztEHG9krI4Mj cXDkb3rvO40WkFKZODdFjxAi0ryjBhfFtMepBB6ze2B9llRvJ4b rHzostMC0nTNR11RcxKTOVx6Be7vmYMbqI3gQIgbM69ugzrB5mNK6uLJHN0tlEusFnZuHAW3u4mFQPPRsquKLAaPwbeOSSO4Ml0cGI1KrKFzcXFDeLPcupoyNTRAdHSVubEjh6loJXp41lMG4f6AfpCIw19czQHRMDIyMjNVQqVnIQvYIy7r1woFay/DH9y7Qiw/A0d8mYcXph3gRHC0SkMDEoR66jRyNzm4mkEZdxeS2w3C/ yas6VZKWSdxLzajd5d1cFqwDYODp6PbxP/QbMFafF/ZCJLYx1g/4BtstBqH9dOawSr1IxLp1rcprv3UDsNvfyHmPBgEJ8UNk4iLmND2f/D9diuWt7OFlmhPrw8MxlczdDFp928oe/gHfL/0ApSdX6LdVG37HX7sXwdWikKKdvbP75Ox8tQ9PAtS7JcOrFwaouPgoejobiZqix8KUCDXBKSm8Og7Eh7JCXo4QXb6FGbceobIBBGYR93C5m0 KPrlYozp4oYi4sEaV8NH6Dh6I7Y/aIXvXNIOW8rwmG3shbGbt0Kqo5V4U7muOwxvnsHYm1fhH eVdP5JKkxCBG4s/VkE5Xbo7r0E/VwNU9yIbv eIPWxMfkbEwe4VaoEI8XvHrXgafkArcffwLXAOBGYf3B2zDVOJkQBClCAAhSgQP4I5EtgHu9/CnsfGKB6fzcob/rLQ3Bh9lBMPWiIZgMmoamjDgKv7cHKBykC84RwXFswFOMP2uDrkfNRt1gIzq2ejgUjZ6PUlolwaewK7ZNnce11H5S1FRFZQijunPCB1Lk9KiT1LKTOV/ZoIybOPQnrb37GolrWSHjzHG9LWiQOs85KmZLqTB5rihq9JqCftRyPDi7HsklDEG2 AaOqimBRrBMfESieqdZG9KtAhBhYwVQ3d0Kzck7l8cL3BUqUKCGC8Zd4K4a0y2RxIliPFj3mil5zCeLi4vDmzWsEBb2BhUXR/Gll6eUqD8ejy7fw2r4fJo93RpGo5/h37UJ4j54Dh60/oUaGrVMLFvWHY1S9bvjpl5VovGYgTP chtUvq OHGY3TBuWiDDKf9OpbD2XrlYfWP1dxV9ygcbKSIvblJdyNEjddLjxGpAjMjRGFx2d9kODwLVyMtWBcpR26UHLI3lCLywAbNWTsKsCtsxvYEIvOVheHjhOgLFfv38g9iv6Be4uGM5Fg25j7AVy9GvvH56IlxOAQrkRCA HM/O7cBunyKoNqyCsvdaFnANt8L0UbGugwjKFR8JjCs0gJPkOK7dDkK8i LG24efjI/ZEmiJoPzdJz4CAcEy6BS3h0XqhCJuYMuhIBjU/wFdKqYMyrO5k3IZwvxuYM/uO5BbNEQ16wwPjtlMnKtTgAIUoAAFKKAJAvlwdo D36l9eGhQAwMrKvsBIA8 i3WHguEwYBHGdk3sGYW7Be7uPYdrSUqKdVbteYMqPyxFv6ZFlb2O5Ue/wslOy7BHRFDVKzVDRel0HL0ShK8 t4Ik/DYO35aj3OAqMFPGwWnzjQ8PQKgIuWpW84Sbs KiyeVdnWSlTMkrW9brhV5tRQ wWFDL0wnxD7pj7foL6F lEcwkCZBFi959/buY1bs9ZooA3cazE74b0wd1rHPW4 HlVR0bNq5F185fw9TYDCEhIYgIF7cAdHSgJZUiNDQURfQN0aN7L2z YyM6dewCS0urd/uoKT8Y2XuiVnWFnxeq2L7Emb5/4x fGNQol0kJpUXRYPgo1Pl6En7 JRRG557D84dpaJzUVR4fHY4oWULixHMSbUjC0q9vk4oNURYLcOpeOFpZGeLN9YsIFENk5Xf/xdPoWnCVPMOZW5Eo2boKLLWk0ClbC/XLJpavopMpfP7uib8u yJWBObJYbeRnSdq10zcr5o1nSH5 ltsWXUJnabXUeu8Cpko8msKfAICCQg6NBRtp1xXTsRpVn88prS0Vd5kjQ71R5g4ztuYvD/dSfQsIaa6wGW/UHFmSB2YZ eYHYOnu6djiY8Tei6vD4tU91xlbx7iuRg0U8qrLAw/ZrDUtfFoUTdl9djg82n9UDn1ePlPoAa5C5 WQOrzr65WPGRx78/HqX8vYlgk8bGOT4uBe/OJCLA9fyIVWQB2Q/2BeZwYjr7fB4Y1hqBCYlyOWL/beCG3QP3KxdKdFCxW9BY8Fb2/QVO/RP2pH8rqvBJdm IZ61ZuEkw/cAXBLZpD77 DuBpbHgNrFkvsDVGRr75zV3Sv/C 8h3TCnWZfoX37tmjkYq4sQ1bKpLJ dWxQxc0UKy/eFkPyRWCuJ4FpncnYul sHReKZ1f xorpCzB2hA7WrOoDxxw8Z24ihrJ/3qI1Nmxah8rulVHMyhoW5kURKYa3K4ay29raIjAwAPHxcrFvHfGHmEG Q/vOsC5mrbLomrBQx7IsrCCepwxX9Q69tCWUWjbE/77fh86/HMJr15GY0dgqqfcrApd/boMR/yZPnVQFv 7 Lt36llp6oJF9LDaKURbRtUrj5kk/OIrXzen9sR9nX8pQXusSLr6xFs/wlxAD02Pw4thKzF97BDeevkKUmLhJzAcFHbcMyqzvgHpVTLD1ynX4y0RgnoN6T6vAJRQo7AISmNUaj5VL/OB79xg2LvkFfX/WwdrJjROHgWeLJ4vH7IRo OycgKHzfdHwZ298XTbtkHgxdEt5Y1AcjlN9YvFg bcYfsoDs5YPhkua75NWLzcEi8Z5wED0mEcFP8O1/auwfFw/YNZqjK5hysdiUrPydw0RSH3 LYcvKz/B7mvJ5 PUv4vz84H5qJN0TaghO8FiUCBJgO2ZTUF9AmoPzGW x7H/sRFqfyeGGSbvZ1JPQoJc VIt1R/lV4ao9 M8MRQ45QWQBPqW5spXg3m1qQzpL3tw4U0NWOy9gFjXoaglhiUrPirz1XdE13m7UOf8XmzZuAFT q/Dlp7eWNDHRQS2icXIsEyqSyquxURhxTDyFA8TJq6pbYLSXh0xasRlnPnhME749oCjfc56zcuUsUPP7r1x8dJ5nPz3JGJjY6ArJoRTDF8vUbwEXr1 hSaNmsLX1xedOnTBlm2b8VXbDihuWzy90ufrcomWtrjYTEB80tWs6JxGvCw sddbVcnkoXhw8aGY3kl43zuIf/1aon1JhWkROPebg7ntZInbapnCycwRddKpbwNta9RsWBLeu4/i0ZvqOPrIEnVpJQAAIABJREFUEg2 bwSTs uw68JLfKZ9DM8t6qChmLFP9mgFRk/cAmnr/ Hn0RVQNOEZdk6YhOOqypdymaJRJciVzYMfClAgdwWkRrYoW1HxrzLcTJ6i7eT1 Me/AdoaW4v 8jD4h8a/yzAh5g38xZyYJrYm6d4MVq6c3jFbBOWPd4zFoAUv0XCyN0bUT74h OE aZvbw0Ycju5ef4HoVlYweF8CxEW8RUhwROKxLj0KA1s4ODomnSud4eZeCsE3 mP3jjsYUqPmR9x0SC8jLqdAbgqkPv8aw9ooGg1Cks/HqX8X5 fE50xysxBMiwK5JMD2nEuQTCYLAmoOzGXwPXYAT41r438uhu Kp2tbGXbau3Hx7HPEuDq9mzQtZfl1bSuilHQ3HjyWwLa5ncp1zKt3QE29cdi5/zDMz8ej2tjaKKqMy1Xnq0xfaoDSNUWwXKMlms3tgSHbt Jut59QOQtlUukb/Rj/XgmFrqO78oIs7Uf0oCgDM/EMeNovP2qJsbExGjVsIv6939zP3w/B4rnyPfv gr29A27dvom79 8qg/NtO7bgi1ZfomTJUh VX3Y3SpCLYDS7GynW11IMPwWO3/dDdIIddNKAyRF8Zh6mHTVH7yUzoTt3ABZP3YXqCzqilI5UTCTnjmoOqTNWXd9Vi igZINmKLnqT za44/bRjXRt6QN9BsVx8IDe/CX9DGK1h8FB3FPKFLMjvwczmJG5taorhi7Gm8Iu8zm1xMTF169GQLtMhVhzd7y1JXC3ymQuwKKOTYghs6KO3w6NlXEa8zW4NJpMRrGy1U8apKA8Dsn8EBuhRYVLdI8X562IKmP2WL7q4swcsFj1P55OUamE5Qr0pEYueHLmgYYd2QZ9nabi452qnrV0 aY3pIEWSTCRKejlp7iBiY/FNBUAdXn39RXHKl/19S9YbkKuwDbc2FvAercf/UG5rIX Ofv52Jo9yg4v 86gNS8pnjPdwkMXDcC4 T90baaeJ1M A08E6 kTf5ILWqjl3h2fPjG0Zgg7YsvqtiKV8744clbe7RoXRGK18dKTKqgYyNTDFkxDzBthjkeSUP90slX5nccu88Djk7WKCLzx6VHYYCRJYzEBD5ZKVNy2cKfXMLZi1EwjPHFxe1L8UdAGXSf6gnFRPCiqx6H1x9GRJnyKCkedg97ch47lp9BjH1v1Ff27ObNx9bGFop/isB8kfcCaInXplWpXBUXLp5H545dsXzlUowZNS5vMk9OVcsIlmJYxKsLR3D aSnUyW4nvU5J1GtYAms2/IaZGwaipbMp5C/uQ0zWr/zIQy/Ce ZRmHRdLiZWEpO3je Loz2XYPreOpjXNnFm/ZQ7mFF9K9bTKdkILcuswrLVb2DduR/K6IqL3zrNYOst6hTW6DzWUXlDSFKiAmywBX s3gvzZk4wlwbAN0VbTc7z9cm1WGvXDG7WCXh8cBlWPi K1iO9EttFyoLxZwpQ4OMFov7D1vVXYFi rHhuPAEhT85h 7IrkJcbgDo24hSn44ouHexxcNUU/FZqCJpZPsPu3/9BtOt3aOekB3nQcfzUaxLu1JqFNWM8YRyXyTE7/iUOLv4TQRUGoIVNEB7eC0osu1QPRUuXgaV4fOndR2qGWsNGoP71KWIk1rfipm871HOxFkPT3 Lmo/DM9zn0Ea5fNRbnpyiEBNzH2T834u8QK3wh5jRhB2PmfFyDAhSgAAUoUJAE1BqYy54fwUFfU9Qe65xiSJ/gkhjAdeBizDWbD 9tczB2g0ws1IFpiUpoaG Y2KMhMYbH8MX41WIelovXVY1dL4YliuHJDo2HoX4rEZgr1Q1QoUMblNi7BvEtO8E9aYKc9PKNe3MPx9ZuwfzXivy0Ye5UH4Mn9UBZZY9mFsokNYZjNVcUPbUaE/6XWGZL8VqsQWL2 E7OSVOAyaPx2ucktm1amfRqrWJwqdMfc4Z0gUPexeVKDcUnOfieMWuaeJ2aF549ey5en6amB7m0i OzAe1xYtpOzNveAF7DsnspqYuyPWdgXOivWLrqZxxXPMKtLXrRy3nAxTwejzb/jgNoibldyyVOuGbXHiPa78aApYtxtuFk1E2c9e dRcb1LVYTNwKatnfBstnBaNrcXrz/WHyKN0BLh6VYHN8GrewTu7p1nXpi6vdvMHPtHIzanTg8Vs 0OFxLG33QiyXVfYuzq3/G iC5eI1eFbT/aTQGJM3U/65Q/IECFMiRgDzqLV79dwDrNj1FiOLP0bA43BsMxYJB7VFGeYzVhWP33/Br9DTM8x6Hg7H6KFmrN34b0xYlxRlQMVlcgmIYU/KwnsyO2RHPcfFxAuJivTG8X8qiW6Hjis0Y sGjVuI0Zd0Mk9ZZYdeKNWII mwcVg6p14KhVWlUrVsp7UzuyiS1xDD7YtA5vgo/DEvMQ1LEEvauTTB4Tm 0q5b4xo UufNnClCAAhSgAAUKtoDk0qlDCdXqNFXDXsjwcGlXfLPXAwu3joF7dmO0jy5hfuX70QXOkw3//GsX7t77713aDg6O6NCuE 7du4fy5csrl5/8tluO8q63dGOOtv9kNk7vncTp7GDKOkhnFS7OZQGa5zIok8tXAbbnfOVn5rkswPacy6BMLl8F2J7zlb/AZa6 HvPYJzh02B/m9VqivNqCclEf ZWvhjWFNl 0RRu01bBSsTgUoAAFKEABClCAAhSgAAUooLbAPPbx3zgSIF6J1sLp3Xue1cGfX/mqY99yOw/2eOe2KNOjAAUoQAEKUIACFKAABSiQuYDaAnPd8kOx89TQzEuUy2vkV765vBtMriAJ6Dii/9ZT6F QysyyUoACFKAABShAAQpQgAL5JsA3ruQbPTOmAAUoQAEKUIACFKAABShAAQqIt4IRgQIUoAAFKEABClCAAhSgAAUoQIH8E1AOZQ8ODs6/EjDnfBUIDQ1l/edrDQCsA/VXAM3Vb84c806A7TnvbJmy gXYntVvzhzzToDtOe9sP8WU2WP KdYq94kCFKAABShAAQpQgAIUoAAFCowAA/MCU1UsKAUoQAEKUIACFKAABShAAQp8igJqm5X9U8TTlH0KDw/D1etX8Pz5M0RGRsLAwAClSpVGFfeqMDIyznIxu49flOV1Va24/pfBqhZzGQUoQAEKUIACFKAABShAAQpkIMDAPAOcgvCVr 8LHD95DC1btkSzps2hq6OHWFkMXvr54s89u9GgXkOUKFGyIOwKy0gBClCAAhSgAAUoQAEKUKBQCuTjUHY5Qm/vw adF/AqToV9fBCu7FyNPy4GIV7F1x /KJN8M0o4dZnkIbi9Zw02ngqAql3IKKnc C48IhwnTh1D7159YGNti4BX/nj05D4CXwcof/9GLD8hgvaIyIjcyI5p5JtADtpsvpWZGVOAAhSgAAUoQAEKUIACWRXIv8BcHoTza1dg550E6GupKG5cAM7s2oXjPhFIUPH1Ry/KLN MEk5dpvhgXPlrJw7/Fwp5Rtvl0XfXr1/DZ5 1BCTA4SN/Y eO7Xj8yAcJCQnwefoAUqkEzZo1x61b1/OoBHmcbEIU/G5fwOWnudwG8rjYuZ58TtpsrheGCVKAArkuEHMPy/q3Q5 FNxGZ64kzQQqoWYDtWc3gzC5PBdie85SXiX8okG9D2eVvLuHgfR1UHlcBRiKwVNcnv/KF6FMPuXsMO3cfwtkbD/G6aGfM 70TSuWgBp4 e4ImTZoi6O0bPPLxQZtWbfHXvt3w9KyOsPAQBLz2E8 al8HRf46iulctdRHnXj4xD7FpylT4dPCGexlDqKaKQ Dx2Rgx5zRMenpjXrsS6ayXe8VSd0r512bVvafMjwIfJxD/9hq2LVyGXRdeIEpiAvs67fDtgDaoYJx471ngBG9PbGo5TJF22NOUv7oaxuqjzj3 L6n2uw e zuOMfBehZwaV Jwzq2xRl9CWI892OYQPX4YWKolb8YRN rWWU5puEqKc4tW0jdh 7godvYsX3ujAr7YLqLXvhmxaOMJAaoFjJUihZLOk4lxCCMzP/hzmnX0GxtuKjZVgMDm718GWPjqhTUl9xP5afT1ogAZGP/sKM8asR1nMFfmthiXc9KXGvcWHjfCzfcw0Bsfoo7vkVBg7rCHdT1X0tGbV/u1dsz590M9KAnUuIeIgDK5dgy7H7CI7XgrlTfXQc0A8tnQxTHceydj2XaXrZ/Pvg8VkDGgmL8E5AdayT50DxeH3xEB7oVsaPFYzUeIGRT/kmRMNn11RM2PwKzqKHu v/eqB4sRKwVjVSIBv2iknf9HT1RA95PDw9PLF3/1 oW6ee6EGXiP kiJPJoK2lhaioT7UPRo63F5dg/MKrkGXDrWCtmk9ttmAhsbSFWSBOzKcxeRI2hTfAwCnD4Si7jR0LVmHCdAN4T26OYuI4K48OR4zUGq1/GIWGlonBi1TPAiV1VMBJxQZRuqjQZijaF9dD2L3DWLdpIaYYlcXiXg7QsWqEUTMrIvrdUC4Z/A7Nw9yTxVDLTj9NgglhN7Dyhx/x1/NiqNq6K4a5WEM3Kgh PnfwJFICbUWErVMKX06ciy Tt06QISxABOVlumHiQDcUkUUg6MUtHNmyHbPGvIHR0u9RRZ13tNPsFRfkpUB82COc2rEea3dewRuRkeMHmcXiybafMXVHJOp Mwb9iz7HgWWbMOkXI3hPawUbFVd1GbV/LbbnvKxKpi1uMp6b9yOW3K2Eb8b9hkpGgTizbj6WTpTBetlIeBgn32LM4vVcpunJsvX3weMzm6imCag4hKuhiPHibu/hR9Cv0hUuhol/lAkxYhKzNYuw4fBtvIrVgoWDE7RD8WHvpywQZzctxtr9V/AySgoT 9roMGggvigvwZVp3 Dnx60wb3EP2CsvtuQI3D8CfVeZYdzqiaih ONPnW9CJB7uX4KFm0/AJ1RcZekVg1ffqfihuY0y3yyVSaz39tIyjDr9EI D46FbzA3New5Gz7rFRZ I4iPuet9ZjWk7JPh67gK0KJG6e bjvRUzrkdHR4kbG1K4ulaCl2cNZTDuH gHqQjM9fUMEB0TA0PDtD04H59rNrdMt84M8Pb0DAya8QANpi1Af1dx5zT2GbaP/g7bi36HheMawDIpq drB KrtYm/pOyRkvnuw4w51 A fCR0VkzBjWwWrUCsnrrNFohCs5AUUJ A7MUx/P1QH3Un90cLdwORcVkMGXwLvaf iRN jdGhpDbkUW8RJTVHORcnlDXNpK9ZYgz3boPgnrwLlR0Qd/EcFvzni6gEB jqWsDe2eLdDsb578XqEyFw7f8rWhZPdUoV55jb634TQXkpdJg5C187G6S4Ed36PZLsCdYPGoajnrPFkHanpHOH Nq4NFwqVIChYk13T1S28EH3X /g1us4EZiruqugPnfmlFcCcfA/vAgrLxZD6zFDcOf3hQhJmVXUPeza8xTmLWZgaFsX6ItrDGeDp g3eQf2PG6Gfk5przEybP9sz3lVkUxXIRDzDKdvRKJ0p15o7VlcXFuXQ6m 93F8 Clc9ZeJwDyxvWb5ei6z9LSz8ffB4zPbqAYKqB73lMcFjX91Hod9iqBqc5fEYewJ4nVf3mPx /5gVOw6Cj9NGo0uVQ0hS/lweUIEbq0ci1/3x6DWoF/w26 j8LnJZayc5I3LYQYoW688tAIu41ZQ0lRxIs37Z59AWrYuyif1LKTOV/ZkB2YuPQfDz8dg pzf8Ouor9G4gnnizYCslCnJSS4zQbVO/8OECSPQuVwg9swai2U3kp6Llgfj3IZDCBTPCe8d/zW bNMePb6fiR23QnL8XLpdGXu8ELOym5maI1gMZ3/p9xy fi8QEREhAvQ40Wsuhl3GxSE4OAghIW/zuFZVJJ9hnUlgXnMABteIxL65m/BfZCye752LTf5VMWBgXVimGE1QrPWPmDN/PubPX4DvKysuvMUn9jF2zNyIiNZj0dfD7P0QPxXFKMiLUrfZgrwvLDsF8kJAHhWCKBSBmWFyUCxBkZIVYA1//BeQOBA8PvINIiXaiH7zGmGx2Zi1JD4Cvhf34sBTfbg3LIek 8jvd0P03lxeswF3LVujT6NiSDMIKvIO/jz FkVqfYO25VMG5dmUED3o4f7XcejAfcjN3VDJKn/uqWez1Fz9owS0UaLtb1i36Ad0rGr1/iZNUlqyV7dwN1wP5auXEUG54iOBUblacJC8wa27wSony81y 2d7/qga40YZCGibw070svieuwQ/5eE4Dm/w/BBuXgbp10czE713OZpJetvw8enzOoOH6VXwL5cHYXz5CcO4zHRaqhV3llPwAS3l7E1mMhKNNzOoZ9lfSMcEUzPDgsAu0kmYSQS9h8MAhuw35D9/rmyl4Hx8FvcLb/ehx6EIVqFRrCWToPp26 xefWRSGJuIfjd Vw6O0KE2UHSdp84yNeIQxGqFapMlzKKi6ayr2rh6yUKXlli5qd0bllYi HZxXRu IzGFu2XUV3tzowjX6Csw/iYVq1ITp/XgnFi4Ti5s4FWDVhOgyWTEWLHIxnr1TJHX/t2YVuXbrD1NhMBN8hiAiPgLaODrSkUoSGhqKIviF6dO FHTu2oWWLVjA3f9/T825n8 iHzOrMo6o5ag0YjOqDZuG3uWEwvPQSVYaNQ92UUbkom55FCdjZpXx2PBZPd83FroS2mNHeUVycPMyjPcjvZNO22fwuEfOngKYJ6BavDCfdgzix8xSaD22IUvqxCPJ7g2gRosTGKYLwBMiiJTDRe4DF3/fBIhE F6v8JfoN7Ybq6Qa4CXh7fBx6zbmtvIFqWut7jGlinWb iriXR7HxrBweI7 AQ9qOSsQFP4ZvDFCiih0MMumoV l661d0 SLlN8XQZFx3uKa5Q6Byay4sqAJixFt6zSU LADhMEYxk/eXbxLR6y2mJ8CNwDDR6q1T3SDKevtney6oDUaDy61dAp8P/wY3J6zAkAHnUKdCHK5fiEGr8YPhobw4z b1XCbpxT7P t8Hj88a3G4KcdHUH5iLmc3PHnkKg2p9UC4xLkdswD28TBBBmqtVmguf5LqJDbiDF/HxCP69J9r8/mGN6QRFA1Uqo6mLFAuO3kBI44bQvX8Mt2RO6OVhmXiSUpGvvtNX6OB6HmvG9seDBp jVeuWqONkqixDVsqkst1oW8GtgjE2XbuHV7I6MI56DcVcPyXrN0ddd2PlJg4DLS Vn4 8JrNGud iSqMlWVC43EEPX6dRti/ca1YveroJiVNSzMiyJSDG9XDGW3tbVFYGAA4uPl6NChE7Zu wOfNf8clkWTB4mrTDbXFmZWZwkwgNSiNgb0P4Jv5x7HG dBmFA3qb4yKEX8qxNYtisCTX5qAzvFxXDy7EgZbFMgv1LRZgvkfrDQFMhDAYlpdQwa8Tmm/T4PQzrPS8xJORbMGG5Gij5sEZRXH4Plm8SPcWHwvfkPNixYiV9 0sb8ud0SjyFpyie28fwev88KgP D09ixdi7 95sOFoyuC4t348zEs74H9 KJST1865l4szhNMuINGYpbAxLxhowPA61Y GwYhYnn3PHTnN5wSi8Kc yN6d9VRhF5HKLfvsCto5uxYdr/gJ/mYWg1k3SDtzTl4IJCLJDV9s/2XIgbSR7uuhyRgc8RIC J p95wdrvHG6KDqvThy6hZcVGsArO7vVcxumZZWdPeHzOjhbXVZOA2gPzOP8zOPrMEF79xLDA5J0UFyUScfmSIM9giKH4ShHI1Rg Fd3L6qXgkYgeVVPlZGdVPnOFdO4hXA3ygNnhq4h17guPoolXUSrz1bPDV7 sQfXLh7BbvGpszoit LPTDEzrWk4EtlkoU3qVpHx3WuKVlkRLVxnoRwZHiTvZxsqbBBJ9S9iIx779Xkcoh52lGf6YXroqlpcoURJtxfD4m KVaHfE8CCZLBY6OrrK4eslipfAq9ev0KRRU/j6 qJzx674Y smNGvaQgTxxVSklsuLMqszRXbikQGfaz4ithZej47hfEATtE79nOYHxRI9WVcP4GZkIG6O6Yg9Kb8Tz6J3vjURa3/yeN 2cnmX1JmcyjarzgIwLwoUCAFtWNb8FnOq98Lb10GI1TFE1JGxGLrJHFVLpDxXiJ3RNha9120weMANXJx6Emf9O8GutOrToNTQGvblFf/c4GL8Ar1mb8O/gbXwhU3SETv2Cf45 RrmtZuhbNo535RyWmalYS2Sf3D7JaKbFhUD7t9/4iNDEBoSCWWnfnqBeRFrlLGzSzqelYWLawm8vTMCB/beR59qn8ZxrkA0MQ0qpJZRMTHOLwyBYUmP7YmyJcQGIzACMCqWeI2RbnEzav9sz my8YuPF0gIuQDv34/BpM8yfNfcSlzvtsGXTVfjux 8saJeNQwIyd71XMbpeWK0Tdb/Pnh8/vh65ZZ5J6DmZ8zj4Hf6KJ4beaFJuaRnhcW 6Vq7opTWW1y95Jtu56eudXmUkETi8TMJrEuVEq8BS/5XUgzhSuwVMavaGtV0/8PeI8ex94oc7q09kRiXq85XySopghIe4kJt2hL8 rkZHu35Cw/F0MOslElltUQ/w/mbYdC1E884isdnJAYl4CRGj/teeYjwpPsO8SFP4BMiRTE7c TG9D2GhoaoUb0WOrTrhK6duyv/3/bL9ihfzhmxsbGwt3cQ/4/B3ft3lcH5kaMH4e/vp7L4ubkw8zqTI TCcsw7ZYYus2ajZ5n7WP37PvjGJZVCogMD0SMeHRaT4nl8Ccxq/4DFixZhUfK/30ejgSlQ7IuJmD3YVdyRQ GbTZT2H3uA8UyG0BqR7MitnCLOosVm97DpP67VBF5URv4iaw8licXjSsomDKG7XxkMW/v3kse3kBl4KMUaVOaaQK/98lIDFywWceRRB2Qjxy9TznQ3sSZJGIEMlo6Wp/svNqqNDnohQCOmKCWWejGNy78FQ8rqH4JCDi/hn4JBSFm7N5Fm70q27/bM9sZnkhEBf8EE jDVGqdPJNIwkM7SrDQS8GAX6RMMnm9VzG6YVDmo2/Dx6f86LGmWZOBVR3FeQ01fS2l73Ev/ 8hLHXYDil6DqQmHrg69a2GL31J0yT90BLd2vohP8HX/EK2eSPxMwLnUWPw4QdkzFd jWauxWDTlQgnoeURuPm5ZWTyEmM3dCmjjHGblwuRjE2wOTKSUP90sk3LuAMxATvsHOwgr6YPfzak3DA0EK8U1aklYUyJZct8vl1XLoWBYMYP1zduw67X4kZeMdWhvItELp2 Oxze xZ741Ff mjvXMcrm5Yg4fGdTGxmll2Lg3TU1W53MrSCop//xw/ikXeC6AlXptWpXJVXLh4Hl06dcPylUvRv 9Aldvm1sLM6sww/BpWLzwFo7az8VX5spAO74aTQ9ZiwaHqmNpSzIyvaw2XUlo4cHgj/irXCg4JrxFsUQONXIqh5LvhFqK04qaDsXjnkJ65LUpYfiLv902nzeZW3TAdCnw6AuLNF/6P8VTcbHx84xT27T6Dl2XaY0qfyomTi8b548S244gsWRbFTaQIf3EZe9dfRGzpLqhlK2ZsDz6NWWLuknueP2H ULFNzAP8ue0GDMvaw8ogAWHPL4vj903IHXuiuqL7W/lJQOjDa/CXlEH3UumF5WI1iSk8 w1EzTtzsFK8PeJhu89Rw6mYGJoegrtPRBdnZp wJ7h90wj6cdEIC/TBxYM78E9YUTQXc5qk00mfWYr8vqALFCmPtq1L49jmOfAu3hv1i/ri76X/Isa5H1rZ66Ztz/EZt/9EDrbngt4sNLX8OtZV4G62DUeXrIVLn8Zw0A/Fvb X43yMDdq6FYWuoW6G13MJ4vg8M XxOZP0tIsUzfDv4wMnHp81tdkU6nKpNTCXvTyJY34mqD7M6YMhfYpea2cx8dsUkxVYu8cbU7crukx1YGJbAbVLGyb2DEiM4P7tDPxovhzrDyzGL9vEMC4tE5Sp2xe1morAXDm6sAjKffEZbA9vQXzTNqiQNEFOevkq7ryd3vInVgQp3oKtBVOHWug9qmPSJD5ZKJPUCHbuzjA7uwnTJyaW2aJcbXwzrQ/avBvbqINSbSdiYswirNg0CSOjxPNeZRti0NRvUS1xVro8bYDJwfeyFd7idWpeePbsOYyM1PT6tAzrzB6Bu5bgHzTGlHaOiT1OpVphUOsDGLVuNS6Ju6g1xGzztQYNxrUZK7Fu kUxDNUSVXo4o56Lca6MNMhT Bwmnl6bzWGy3JwCn6BAFO4sHY3JV7Rh5VgRXr0mY9Jn7rDSTeoRl0cj6Ok5/LVjk3K D hZolz1Hpjc50uUEUOWFE8eJT4Jnkgjjw7Bm/tHsW3nC4QqRgsb2KBi7b6Y1qsVxJvXkj6xeP0gEDCrBesiGfe8a1k1wKgFRbF/4xYxBH0JTiiHIGvBwLIE3KpXgLni3JX6KS4xg7yxtSV0Tm/G1PGJWUr0LVDauR56T 6CVu7i9ZLJReH/C5mALuw6TML4mHlYvnYajsXqo7hnF0wa2hLiPlOa9oxM2n8iHttzIWtE6tvdIhXRd r30Fm6Gct 3Kcc5WEgJuz8YtRAdHVUMWOmipKlPD4jC ll9PeROnken1OL8Pf8FpBcOnUowaGihxrKIcPjdQPx3WF3/Lp8KCqq7XZ/fuWrBtJsZHH0n8N45PN 9vLSpcvgs2Yt8fDhQ5QtW1aZUvfxi7KRYtpV1/8yOO1CLslUIGUdJK7MNpspWg5XSGuewwS5OQXyUYDtOR/xmXWuC7A95zopE8xHAbbnfMQvgFmrr8c89jlOnAiEaY0mcFRbUC5qJL/y1bDG0FhMAKf4x08BEGCbLQCVxCJSgAIUoAAFKEABClAg9wTUFpjHPjuGk6/MUKuRg1qfjcuvfHOvitSXEnu81WedUU5ssxnp8DsKUIACFKAABShAAQp8egJqC8x1y/bBqr/6qF0wv/JV 44yw09GgG32k6lK7ggFKEABClCAAhSgAAWyJKDm16VlqUz0JisjAAAgAElEQVRciQIUoAAFKEABClCAAhSgAAUoUGgEGJgXmqrmjlKAAhSgAAUoQAEKUIACFKCAJgooh7Kbm5trYtlYJjUImJiYsP7V4JxRFqyDjHTy5jua540rU80fAbbn/HFnrnkjwPacN65MNX8E2J7zx72g5soe84Jacyw3BShAAQpQgAIUoAAFKEABCnwSAgzMP4lq5E5QgAIUoAAFKEABClCAAhSgQEEVUNus7AUVqCCUOzQ0BGfOnYaPzyNERETA0NAQDg6OqFWjNkxMTLO8C60GTc3yuqpW3Lv4R1WLuYwCFKAABShAAQpQgAIUoAAFMhBgYJ4BTkH46smTx9h3YC9atGiBBvUbQldHD7GyGLz088X6jevQqmVrlCljVxB2hWWkAAUoQAEKUIACFKAABShQKAXycSi7HCHXd2DVpn8REKfCPv41zm9ajDVnXiNexdcfvyiTfDNKOHWZ5G9xfbs3Vhz1gyyj7fLou9CwUOz/ey6dkbNta2CHjlj0dP7iPwdYDy915i b79exAWHpZHJWCy6hFI0WZj3 Lq1oVYevhlvrQ59ewvc6EABShAAQpQgAIUoEDhEsi/wFz BqeWLMDmG4C lgp0mT9ObN6MQ/cjIFfx9UcvyizfjBJOXab4Nzi/dRP23Xybu2XMqAwpvjt//hyaN28BSIAjRw9i547teOLzGAkJCfB5 gBSqQRNmzbD5csXspiihq0mj8SL6//inE94vvhqjEbKNos3uLh9C/6 HVK4TTSmclgQCuSCQPRtzO3cCO1nXkVELiTHJCiQrwJsz/nKz8xzWYDtOZdBmVxGAvk2lF3 6gz23NGBx7RKMBGBpbo 6s5X9mw9vum2DE9V7KD7lP1Y2MBYxTdZW/Tg4X3UrVsPQW/f4OGjR jetSc2bF4HDw8v0UsegoDXfihVqgyOHT8mhrk3zlqimrRWzD2sGjMW97tvwhoHI6i iySD36Ep HbKMZgMEOt1K4V8a9R5ZPdhm32VR7kwWQoUFgE5Iu5vx4RhixA6YBuWfVlM5bElS8fuuFf4d8WvmL/9IvxiiqBUra4Y8UMPVDNPcbSKf4mtvTthgU96vs4YvWUsbErbobSNUeLxSx6M45P6YcqxAMQmbaZlZAOnqk3QuX9PNCqjr7gfy0 BF1B9/ooPuoj1M dh8 mniJSawqlhN3w/vBMqmaY C6rePn0W1evLA3ejX7vZuJ9yQ6sOWL55GJz10qYmj/TBP tX4o D53HvVYxYQRcW9pVQp 1ADPqyHAy1DNme07JxSZYEsnZ8RkIMfE tx8KVf Ksz1vE61igfAPF30l7uBqn/DvJJD0en7NUK1xJfQL5FMPEI/DMXtzV88SvlYzVeIGh/ny1bVpgkndlRCUkV6oML/ZMw7QjNmhQVj9HNR0mhrLr6eqJHvJ4eHp4YtMfG1C3Tj3Rgy4R/0kRJ5NBW0sLkZGfah MHEFn5uC7GRfeXbzmCFQjN07dZhmYa2Q1sVAFQiA 5D6OblqKJZsuQPGXVC6DUmd 7I7Fo/UjMXZjBBoPmozvrZ5i99yVGDnOGBsWtEOJ5LOr1BINx86DQ7hi7FcsfDb9hAX/eWD4xHYorSMWaRnD3soBRWeuQud35YlD6EsRlDv0wcwRVWEQG47Xz65h39oNmDT4FYw3j4eXMUPzDKqvAHyVzvlL9gxbRo/EyrDmGPH7eJST3cCm6Qvx/QRDbPz9C9i G2GYzvbp7nn668dHhSFGaosOUyehebHEDKR6RVFaN21i8tArWDToO2x9agOv9r0x1q04dCNf48XDG3gULoG2olnq2KEz23NaPC7JUCA7x eE8GtYPf8Aour1wLi NkjwOYilKxZgNOywdYIXjEQ7zFJ6PD5nWCf8Uv0C ROYxwfi9N570PfqDTfFX4/4JEQ/xSHvWVi 9zoCYrVh6eQM7RBxfE9pIvPDyZWz4b3rPF5ESmHq1BA9RoxA 4oSXBjfFqMedMDqjf1RVrmRHP67 qHDQgtM2zkTdU0Vf6Wp8pVH4N6uOZix ggehIiLJn0b1Bk2D1NaF1f2WmSpTGK9oHPzMKDNXTwMioeeTVV8MWAUvm1cEoobzRJdS5R1tXy3F3G O7D4SDAqf7cAbUt sHcp9zRLPxsbmyA6Okrc2JDC1bUSvDxrKINx/0A/SEVgrq9ngOiYGBgZfXyvfJYKktFK6daZId4em4huE/9DswVr8X1lI0hiH2P9gG w0Woc1k9rBqukdJ8u6YqGSxJ/STnKQPZsJyZOuQSPCT9Bd/4YXMqoHAX1u9RtNmk htd/j0e7v14hRCaFiUNddBs5Gp3dTBJ7/kQv3tm1c7B4 794Eg4Y29VBhyEj0L26ZWJvXHwAjv42Ccv/fQDft4reDi0UrdQaXRvo4vLew7joEwyZfgnU6DYGP/aognedNOnWpbHKHseCSs5yf6oCMvjum4kFp23QYfJo3Jg6E8EZ7Gqmx 7IK9i8zQdFv1yMMV3cUAQJcDV8hI6jN2L7g1b4ziWpq1GiCyvnqknHs2joHRXLn9iiQlWP972RskdY1rEXDtRahjd1GeO5QfEwe4VaoEI8XPHrXgafkArcffwLXAOBGY5 z8kZwF/58/Aumdv2TPDuLPe0XQeM53 NLDUBTOGaNGXUP7sVtx5EULdC TWO/pbZ/e3mS0vjwyGJFaReHi5oLyZhnc8EmIwI2lP4ug3A7dvZegn6thio6V9u zVrTnbmzP6dUFl6sSyObx2dgLYzdvhVRHK7EN1nWH4c0zGHvzKvzjvEQckMX0eHxWVRlclo8CqcdFqaUo8f6nsPeBAaq3doPypr88BBdmD8XUXW/g3mcSZv32M76pboTYd73MYp2EcFxbMBTjd0Wjwcj5WLrwZ3xlcg4LRs7G VADODd2hbbfWVx7nTRVXEIo7pzwgdS5ESok9SykzlfmsxET556E0Vc/Y9HyZVgohg5 VskiaShhFsqUpCWPNUWNXhMwY8ZE9Kzgh22ThmDelXBxmZbqIyaLO e9HLfEELGhn9mKcChnn3JO5fHC9wXMTM0RLIazv/R7Dl /F8pXpsXJ4kSvuQRxcXF48 Y1goLe5Cyzj9k6wzqTwKL cIyqF4Gdv6zEzYhYPN0 DatfVsf/RjaGVQocm/a/YsWaNVizZi3GeyouVMQn5iE2/rQC4e1/wbAa5p9sYJi6zSZXg659cwyePBuzpw1HE 0z8B49BxfCRItLiMQt7yEYvcYHZXtMwezZU/C14yOsGjkUy 5EJW4uD8ejy7fwxrEnpv4 D7MnfQOnx7uxYOF5mH42DL/Mno7RLfRwYeVELLkVnbhNhnWZpqV/TGvhNhTIYwEdlO6yDH9tmIoe1a2hm0H8kaYgKo7dsoBruBWmj4p1HURQrvhIYFyhAZwkr3DtdlDuTloqlyHM9zL27L4DuUVVVLPOn3vqaVy44OMEMjh/xUe9RRQMYG6UXMcSGNq5wRYvcdMv6cGGDLZXWaBM1o PCBRzG2gj lUgQmIzmNUn4ga2HAqCQf1B6FIxZVCuMtf0F7I9p29TaL/J7vFZAq3koFxhFh BgGAZdIrbw0J5/Zjd9HIAz/acAzxumlogH87ucfA7tQ8PDWpgYEVlPwDkwWex7lAwHAYswtiuSc8Iu1vg7t5zuJZUYsU6q/a8QZUflqJf06LKQKz86Fc42WkZ9tyNQvVKzVBROh1HrwThq8 tIAm/jcO35Sg3uArMlLcf0uYbHx6AUBijZjVPuDkrTjIu73yyUqbklS3r9UKvtom9HLU8nRD/oDvWrr A/lUaIeXN5zjf/VhxMh41f qIsiqe23qXeRZ/8PKqjg0b16Jr569hamyGkJAQRISL06uODrSkUoSGhqKIviF6dO FzX9sRKeOXWBpmdwPncVMcrBaxnUWiZpeRdFg CjU XoSfv4lFEbnnsPzh2lonDIqF/nrWZaBo2PKZ8fFcNA/fsHmhM5Y/HU56ONuDkqpyZumbbPJpTUpXw N6iS2ucrFXuDfvgfwj08MvEqfxcqdL1G6z3qM62KnHHHiVaU0ou J QdWnkfX3xrALCkRIzsP1PBQpOEG65eHcW5dGTRp0wReBmKFijq4cHAErl0WbxyoZA tDP/ FHWZdMNEkzlZNgqIkUTZiceTwVQdu ND/REmzh82Ju9PoxI9S4jHxHHZL1SccXJ 8xXXxqNF3ZTVZoPPp/VD5aSRZqzQgiiQ8flLt4SnGEnxFw5v/gdfjGkOuyKxeP3ilQjW4xATp7gJmvH2aUUyWz8BsmgxAlH/Lmb1bo ZIkC38eyE78b0QR3rD0dlyN48xHNxr7aUV1kYfswfEttz2urhkvcCH3l8Fj01eLp7Opb4OKHn8vqwSO5y/Oj0slgpbM9ZhOJq2RFQf2AeJ4aj7/eBYY0hqJAYlyPW7zZeyC1Qv3KxxN5qFXsQ63cDT0Xvb9DUL1F/6ocr6LwSPYHiGetWbhJMP3AFwS2aQ/g7gaWx4DaxZL7JlWkac1d0r/wvvId0wp1mX6F9 7Zo5GKuLENWyqSimOImnQ2quJli5cXbYki CMzfBeDiecS/duCRWVMMr2WRKz28JmIoctWmPDpnWo7F4ZxaysYWFeFJFieLtiKLutrS0CAwMQHy8X 9YRf4gZ5Du07wzrYtYqi57bCzOrMzkMIbVsiP99vw dfzmE164jMaOxVaYjCeIDDmHu5nC0/K0THBW itHYn JHRZtVtZvaVo6whHgGNTwOsS vwSfOAvU8bd4/BqJTXATnZlh99hr8YkVgnmacjA7MSpgC0UF4GyMu/AzEFZeOOYqbADffRilnf4/P5O9PWZeqCsdlFCjwArl/7M4ySbkhWDTOAwaiRyYq Bmu7V F5eP6AbNWY3QNU/7NZRlSc1bM7PwlNa DURPaYewv09Djs2mJBVceXE1RxVgbmW2fek8zX18C0zqTsXW/2DIuFM u/I0V0xdg7AgdrFnVB44fPGeeoBwJKC4vUn1i8WD5txh ygOzlg GS5rvk1Zne04Nx99zKpAQDZ dEzB0vi8a/uyNr3Oj1yurZWJ7zqoU18uGgNoDc5nvcex/bITa31VIfG5OUdikO68J8gyGxCq/MkS9H ehX/mU3c0S6FuKoczi1WBebSpD sseXHhTAxZ7xYRgrkNRyyrxDKEyX31HdJ23C3XO78WWjRswpf86bOnpjQV9XERgm6iYYZnSgxavK1NMwPZB10zMIxw4EoiiDVqhfOK4x/S2ztbyMmXs0LN7b1y8dB4n/z2J2NgY6IoJ4RTD10sUL4FXr1 hSaOm8PX1RacOXbBl22Z81bYDitsWz1Y H7VyZnWmSFQeigcXH4o AOF17yD 9WuJ9hk ey8msLnwJ65G OPqwGbYnrJg4ln0z67NxO5ZNd 3rY8quGZspLLNqiiaRKotLtATEJ/Bn4 KzT5YpKWrLWogWqShvOwS/2lDTwwHU7R/ZbJZqcvMMuH3FCiIAukcu7WMrUV/eRj8Q5Men1L8mcS8gb Ya9PE1iTdm8zZIjCwhYOjY9LxzBlu7qUQfKM/du 4gyE1Po3jXLY8CvzKWTt/WdX/HivqDkBQwGvE6Bkjat9g9FxVFNVL6SDodHbOf1nLL6mPBNA2QWmvjhg14jLO/HAYJ3x7wNH fa 5trk9bMSvd6 /QHQrKzHgPvmTgLiItwgJjsj4PMT2XOBbsEbtgAjKH 8Yi0ELXqLhZG MqJ95x06ulp/tOVc5mViigJoDczEZw7EDeGpcG/9zeT/0Vde2Muy0d Pi2eeIcXV6P/FNilrSta2IUtLdePBYAtvmdirXMa/eATX1xmHn/sMwPx PamNro6gyLledrzJ5qQFK1xQnohot0WxuDwzZvhV3u/2Eylkok8pGFP0Y/14Jha6ju/IElvyRvfgXZ1 bwLORvRh6nbsfY2NjNGrYRPx7n66fvx CxXPle/b9BXt7B9y6fRN3799VBufbdmzBF62 RMmSpXK3IKlSy7zO5Ag Mw/Tjpqj95KZ0J07AIun7kL1BR0hrj9EcKgDQ3EPJjokOsU7u6WwaDgZG9xi3j/DH uD9SN wo1mMzGjU UUFwt5unt5nHgGbTaDnHWLV4a9 Fu6eskfsoqJQ9khe4kLV99Cx94dtorej6QJ5DJIJs1Xmddlmk24gAKfhEB6x24dmyritTxrcOm0D6K9XMVxPQHhd07ggdwKLSpaZDry52NwEmSRCBOPGWvpKW7G8VPwBLJx/pLqw8K2JGJf/IVx65/CtMkweJlrwSBb579s5PcOU9yMVd6IFW93SQUsMXLDlzUNMO7IMuztNhcd7XL2TB7bc8FrwZpTYnG8vboIIxc8Ru2fl2OkuoNyFRBszypQuCjbAuoNzGUv8M/fz8WwqVFwfn rFVLzmuIdmiUwcN0IjJP3R9tq4vUb4TfwLPL9/kgtaqOXeHZ8 MbRmCDtiy q2IpXdPjhyVt7tGhdEYrXFkpMqqBjI1MMWTFPjPpqhjkeSUP90slX5nccu88Djk7WKCLzx6VHYYCRJYxET2FWypRcuvAnl3D2YhQMY3xxcftS/BFQBt2nekIxEXziR463dy/hpdQB/e1yOyxXXee2NrZQ/FME5ou8F0BLvDatSuWquHDxPDp37IrlK5dizKhxqjfOpaWZ1Zlh EV4zzwKk67LxUQy5aE1vi O9lyC6XvrYF5bMTO bnG42Wlj974V2FqhHZwQiCDLumjuaosy727xi8LGRMNURwI9i5IoXazIp3HBmk6bzaxqpGY10fer4hi44gf8qjcALRyBB/sWY/WLEujyY40UbTKzlD78PrO6/OC1odlLmmtTQCME5EHH8VOvSbhTaxbWjPFMnJhU3BJM99ht4IouHexxcNUU/FZqCJpZPsPu3/9BtOt3aOeUs4DlHUjoI1y/aizOT1EICbiPs39uxN8hVvhCzGmSiwOvNMK/sBRCyyiz85d477LvI/i89MXDK0ewY8sJ Np/jd HeiS2yUy2h2jHE1K240zWl8p8cXj9YUSUKY S4jmnsCfnsWP5GcTY90b91KPXpGaoNWwE6l fIkYWfis6Mdqhnou1eNTiLW4 Eq8AyezD9pyZEL9PRyDN8Vnuh4OL/0RQBXGdYxOEh/eCEreU6qFo6TKw1Et9WymdhHOymO05J3rcNh0BtQbmsudHcNDXFLXHOn/YqykxgOvAxZhrNh/e2 Zg7AaZKK4OTEtUQkN7w8SeB4kxPIYvxq8W87B8928Yu14MH9QyhUPjYajfSgTmyh00QIUObVBi7xrEt wE96QJctLLN 7NPRxbuwXzXyvy04a5U30MntQDZZXPVGWhTFJjOFZzRdFTqzHhf4lltnRpKIbVDEUn55QBeCwC7/oDZvVhW0QNB4sUlZ0cfM YNU28Ts0Lz549F69PSxnVplg5t3/MsM7Kwn/z7ziAlpjbVTGBm/jYtceI9rsxYOlinBW9AnXNLNBgxEhcnLgQSyecEU3CCp79XdHE9dN/tjK9NptpFSn/lhZipsFsLFozAYfFsFoj8bq0b2aNQI KRdL0gGSaXvIKGdZl8t9fllPjihTQSIEERVfhB4 EZHTs1oVj99/wa/Q0zPMeh4Ox ihZqzd G9MWJXN8ZtUSw GLQef4KvwwLJFKUsQS9q5NMHhOb7SrJl4vqZGCLFTOBaJwQ4weG31BB9ZO7qg9cA5mt/GAdTZeI5C2HWdQKnk0XvucxLZNK/FKMV LfjG41OmPOUO6wOHDud UiWhZN8OkdVbYtWKNeKRiNg4rH XQgqFVaVStWylpRuzU bE9pxbh79kX KBdRz/HxcfiEYpYbwwX0268/1ih44rNGPrBI6/ZzyvjLdieM/bhtzkRkFw6dSihWp2mOUkji9vK8HBpV3yz1wMLt46Bu9pu9 dXvllkUdNqf/61C3fv/fcuNwcHR3Ro1wn37t1D fLllctbDZqao9LsXfxjjrYvrBunrINEA7bZvG4Lac3zOkemT4G8E2B7zjtbpqx AbZn9Zszx7wTYHvOO9tPMeUc39fPMkrsExw67A/zei1zdfKzTPPPr3wzLZh6V2jzRVu0QVv1ZsrcPk6Abfbj3LgVBShAAQpQgAIUoAAFCqiA2gLz2Md/40iAeCVaC6dcn/wsI/v8yjejMmnqd zx1oyaYZvVjHpgKShAAQpQgAIUoAAFKKAuAbUF5rrlh2LnqaHq2q93 eRXvmrfUWb4yQiwzX4yVckdoQAFKEABClCAAhSgQJYE MaVLDFxJQpQgAIUoAAFKEABClCAAhSgQN4IMDDPG1emSgEKUIACFKAABShAAQpQgAIUyJKAGmdlz1J5uBIFKEABClCAAhSgAAUoQAEKUKBQCbDHvFBVN3eWAhSgAAUoQAEKUIACFKAABTRNgIG5ptUIy0MBClCAAhSgAAUoQAEKUIAChUqAgXmhqm7uLAUoQAEKUIACFKAABShAAQpomgADc02rEZaHAhSgAAUoQAEKUIACFKAABQqVAAPzQlXd3FkKUIACFKAABShAAQpQgAIU0DQBBuaaViMsDwUoQAEKUIACFKAABShAAQoUKgEG5oWqurmzFKAABShAAQpQgAIUoAAFKKBpAgzMNa1GWB4KUIACFKAABShAAQpQgAIUKFQCDMwLVXVzZylAAQpQgAIUoAAFKEABClBA0wQYmGtajbA8FKAABShAAQpQgAIUoAAFKFCoBBiYF6rq5s5SgAIUoAAFKEABClCAAhSggKYJMDDXtBpheShAAQpQgAIUoAAFKEABClCgUAkwMC9U1c2dpQAFKEABClCAAhSgAAUoQAFNE2Bgrmk1wvJQgAIUoAAFKEABClCAAhSgQKESYGBeqKqbO0sBClCAAhSgAAUoQAEKUIACmibAwFzTaoTloQAFKEABClCAAhSgAAUoQIFCJcDAvFBVN3eWAhSgAAUoQAEKUIACFKAABTRNgIG5ptUIy0MBClCAAhSgAAUoQAEKUIAChUqAgXmhqm7uLAUoQAEKUIACFKAABShAAQpomgADc02rEZaHAhSgAAUoQAEKUIACFKAABQqVAAPzQlXd3FkKUIACFKAABShAAQpQgAIU0DQBBuaaViMsDwUoQAEKUIACFKAABShAAQoUKgEG5oWqurmzFKAABShAAQpQgAIUoAAFKKBpAgzMNa1GWB4KUIACFKAABShAAQpQgAIUKFQCDMwLVXVzZylAAQpQgAIUoAAFKEABClBA0wQYmGtajbA8FKAABShAAQpQgAIUoAAFKFCoBBiYF6rq5s5SgAIUoAAFKEABClCAAhSggKYJMDDXtBpheShAAQpQgAIUoAAFKEABClCgUAkwMC9U1c2dpQAFKEABClCAAhSgAAUoQAFNE2Bgrmk1wvJQgAIUoAAFKEABClCAAhSgQKESYGBeqKqbO0sBClCAAhSgAAUoQAEKUIACmibAwFzTaoTloQAFKEABClCAAhSgAAUoQIFCJcDAvFBVN3eWAhSgAAUoQAEKUIACFKAABTRNgIG5ptUIy0MBClCAAhSgAAUoQAEKUIAChUqAgXmhqm7uLAUoQAEKUIACFKAABShAAQpomgADc02rEZaHAhSgAAUoQAEKUIACFKAABQqVAAPzQlXd3FkKUIACFKAABShAAQpQgAIU0DQBBuaaViMsDwUoQAEKUIACFKAABShAAQoUKgEG5oWqurmzFKAABShAAQpQgAIUoAAFKKBpAgzMNa1GWB4KUIACFKAABShAAQpQgAIUKFQCDMwLVXVzZylAAQpQgAIUoAAFKEABClBA0wQYmGtajbA8FKAABShAAQpQgAIUoAAFKFCoBBiYF6rq5s5SgAIUoAAFKEABClCAAhSggKYJMDDXtBpheShAAQpQgAIUoAAFKEABClCgUAkwMC9U1c2dpQAFKEABClCAAhSgAAUoQAFNE2Bgrmk1wvJQgAIUoAAFKEABClCAAhSgQKESYGBeqKqbO0sBClCAAhSgAAUoQAEKUIACmibAwFzTaoTloQAFKEABClCAAhSgAAUoQIFCJcDAvFBVN3eWAhSgAAUoQAEKUIACFKAABTRNgIG5ptUIy0MBClCAAhSgAAUoQAEKUIAChUqAgXmhqm7uLAUoQAEKUIACFKAABShAAQpomgADc02rEZaHAhSgAAUoQAEKUIACFKAABQqVAAPzQlXd3FkKUIACFKAABShAAQpQgAIU0DQBBub/b 9eg6wgzDMAf8tVdhEBASMKKmgJXrCAl0yS/kgT01xQqWNtTK1NrBMdTWocpqNtMomBVJuLkzTGzMTES6uoAWoTUWOSpmaCNYlFhZiC0UQRqiJXg9xhd3sWEHYRZY3U ez37DjDLBzOeb/n9c/L2YVsjchDgAABAgQIECBAgAABAqUEDPNSdTuWAAECBAgQIECAAAECBLIJGObZGpGHAAECBAgQIECAAAECBEoJGOal6nYsAQIECBAgQIAAAQIECGQTMMyzNSIPAQIECBAgQIAAAQIECJQSMMxL1e1YAgQIECBAgAABAgQIEMgmYJhna0QeAgQIECBAgAABAgQIECglYJiXqtuxBAgQIECAAAECBAgQIJBNwDDP1og8BAgQIECAAAECBAgQIFBKwDAvVbdjCRAgQIAAAQIECBAgQCCbgGGerRF5CBAgQIAAAQIECBAgQKCUgGFeqm7HEiBAgAABAgQIECBAgEA2AcM8WyPyECBAgAABAgQIECBAgEApAcO8VN2OJUCAAAECBAgQIECAAIFsAoZ5tkbkIUCAAAECBAgQIECAAIFSAoZ5qbodS4AAAQIECBAgQIAAAQLZBAzzbI3IQ4AAAQIECBAgQIAAAQKlBAzzUnU7lgABAgQIECBAgAABAgSyCRjm2RqRhwABAgQIECBAgAABAgRKCRjmpep2LAECBAgQIECAAAECBAhkEzDMszUiD18v1PkAABaFSURBVAECBAgQIECAAAECBAiUEjDMS9XtWAIECBAgQIAAAQIECBDIJmCYZ2tEHgIECBAgQIAAAQIECBAoJWCYl6rbsQQIECBAgAABAgQIECCQTcAwz9aIPAQIECBAgAABAgQIECBQSsAwL1W3YwkQIECAAAECBAgQIEAgm4Bhnq0ReQgQIECAAAECBAgQIECglIBhXqpuxxIgQIAAAQIECBAgQIBANgHDPFsj8hAgQIAAAQIECBAgQIBAKQHDvFTdjiVAgAABAgQIECBAgACBbAKGebZG5CFAgAABAgQIECBAgACBUgKGeam6HUuAAAECBAgQIECAAAEC2QQM82yNyEOAAAECBAgQIECAAAECpQQM81J1O5YAAQIECBAgQIAAAQIEsgkY5tkakYcAAQIECBAgQIAAAQIESgkY5qXqdiwBAgQIECBAgAABAgQIZBMwzLM1Ig8BAgQIECBAgAABAgQIlBIwzEvV7VgCBAgQIECAAAECBAgQyCZgmGdrRB4CBAgQIECAAAECBAgQKCVgmJeq27EECBAgQIAAAQIECBAgkE3AMM/WiDwECBAgQIAAAQIECBAgUErAMC9Vt2MJECBAgAABAgQIECBAIJuAYZ6tEXkIECBAgAABAgQIECBAoJSAYV6qbscSIECAAAECBAgQIECAQDYBwzxbI/IQIECAAAECBAgQIECAQCkBw7xU3Y4lQIAAAQIECBAgQIAAgWwChnm2RuQhQIAAAQIECBAgQIAAgVIChnmpuh1LgAABAgQIECBAgAABAtkEDPNsjchDgAABAgQIECBAgAABAqUEDPNSdTuWAAECBAgQIECAAAECBLIJGObZGpGHAAECBAgQIECAAAECBEoJGOal6nYsAQIECBAgQIAAAQIECGQTMMyzNSIPAQIECBAgQIAAAQIECJQSMMxL1e1YAgQIECBAgAABAgQIEMgmYJhna0QeAgQIECBAgAABAgQIECglYJiXqtuxBAgQIECAAAECBAgQIJBNwDDP1og8BAgQIECAAAECBAgQIFBKwDAvVbdjCRAgQIAAAQIECBAgQCCbgGGerRF5CBAgQIAAAQIECBAgQKCUgGFeqm7HEiBAgAABAgQIECBAgEA2AcM8WyPyECBAgAABAgQIECBAgEApAcO8VN2OJUCAAAECBAgQIECAAIFsAoZ5tkbkIUCAAAECBAgQIECAAIFSAoZ5qbodS4AAAQIECBAgQIAAAQLZBAzzbI3IQ4AAAQIECBAgQIAAAQKlBAzzUnU7lgABAgQIECBAgAABAgSyCRjm2RqRhwABAgQIECBAgAABAgRKCRjmpep2LAECBAgQIECAAAECBAhkEzDMszUiDwECBAgQIECAAAECBAiUEjDMS9XtWAIECBAgQIAAAQIECBDIJmCYZ2tEHgIECBAgQIAAAQIECBAoJWCYl6rbsQQIECBAgAABAgQIECCQTcAwz9aIPAQIECBAgAABAgQIECBQSsAwL1W3YwkQIECAAAECBAgQIEAgm4Bhnq0ReQgQIECAAAECBAgQIECglIBhXqpuxxIgQIAAAQIECBAgQIBANgHDPFsj8hAgQIAAAQIECBAgQIBAKQHDvFTdjiVAgAABAgQIECBAgACBbAKGebZG5CFAgAABAgQIECBAgACBUgKGeam6HUuAAAECBAgQIECAAAEC2QQM82yNyEOAAAECBAgQIECAAAECpQQM81J1O5YAAQIECBAgQIAAAQIEsgkY5tkakYcAAQIECBAgQIAAAQIESgkY5qXqdiwBAgQIECBAgAABAgQIZBMwzLM1I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 OuiZ OFNs LKq1viq5/9kzho57rd9yHesGfsfUicetmVceob9oIJX4hBwlJEIkCAAAECBAgQIECgssCuYb7hiZj9/SUx6JQr4sJJfxD7Nb4IfEzzkrj4C7PjnkXvio O7tPVqfHu iN33Bg33/tQ/M 6iJZDJ8YH/vK8OOP4QdvfjW5dGT 78dr4zn89Gc/ bnPj9/aKwUe LT74F fEB8cOiJ3vwW9ZHg/OvCGm/2h PLehR x/ Mlxxl fFx84qiWaWl Ih267Lm5/YGE8vWpT4zlaYtwFV8XfvWtgPP/9L8e0234ZKzueuu/QOPaUc PisyfGgZ3 AOGZW6fE2bdujz320m/F5yasjNumXB4/mTAtrvnI6Nh20V7vWBH/ef3XY8bcRfHcmo4Xa4r I06M088/P04b0z a2jfEkz 8Ib4564F46sXGF843spxw7qdiyruHdX1Xfp947CVLI137pmdjzvRvx 33PRYrtvSMQYePil4vdujv NiyuKtB696fMxo9PDr7X KWex6Mp9a0RfRsjqEjxsZ7LvxE/Onhu/1/8dLr JEAAQIECBAgQIAAAQIEuiWwa6 tXBiPr sTR50wojHKOz6aouXIk KIpl/Egid F62jh 4amo3v4f719Klx1T0R72i8u/5XjX8z/emf3Bq3XDUtNn3 yjjnyMYztK2LRb98LFaOOCsuvXBU7Ldpacz/wYy4 XNPxborPx8fGtW3sSLXx4Kbp8WX5wyJyed/Ok488MWYN u6 Od/vCEO/qePx4S a LxB fF0recGZ 84K0xoK3xfdIjBzZy9IwDjn5vfGTK5Bjc0hYr5t8Z1828Jq476mtx ckDGsm3fwx935SY8scduZui39B Lwfp1h3rY/GvHo9VHXec1rhj43Mx945bYvoXe8bIr308jl1xZ3zlxrkx5MxLYuqEA6N99dJY85YDXv6l8vvE49WzjG9eF/Ovnxpfn9Mcf/ThT8Q7R/aKlQvuixmLOg3z3RUapq923/jmTfHE7VNj2uyNMfHMC KsMQOj/fkH4vpv3x8LVm81zHf39DkBAgQIECBAgAABAgReo8DOYd724vJYG/1j6P673nJu6jMohjZHPL9sbeNv9N41zNvXPBIzfrAshp/1pbho0iHRu/Gix48dHpuevCy O3N nHb5yTFgR5DmQ4 LieM73p0eF PHj4qmKZ Ju2b9Kib97cRoaTzPzB vjmMunBpnv2PgtkE96mOr48G/uT1 /NuNMeHo7U/SPPL4OOH4He9w73jelsMmxMmHbf/kqMP2j8U/vSz /dFlsbkxzBuTf9tHn8HD47CRB 8ayVt2/MKOH17THSMad2zLMC6OGbo8Hv77n8bPlmyOo9tWNtxaYvyxx8WYUf0aN4zu iK7fbZPPF4hyx8e9EjcMWdNjPjwZ OiU3fc/dYD4rf3zYsFr5oqovmVnnP4/Jhx79IYdvo/xKVnHrHtqwzaDlkR/xr37 UZ/TIBAgQIECBAgAABAgQIdEeg61/ 1p3f0XjM5mULY0nrwDjpuCHbRvm2j97DYtwxA2Lmw4/Fsi2NYf7S29adn7PviDjp6P5x938/Fsu3Tozey34dz7S2xgvXXhR/fm3nBzbe4V21sevfqN7llzfH0p/PipvueCAWPrMqNja tLpP46vMe43Z2vVJ9vLZ73tH70EjY3Csj1XrWqPvsZNi8ti5Mf2KT8Zv3vneeP/7T4m3jx7w8nfM95RlH3h0zrJ5 RPxXPvAeNvYA7v3 nvK1FFlp/u2NLpevGVATJg4fPuX/r/C7/HTBAgQIECAAAECBAgQIPD7Cewc5j36D2m8X742lq9tfA/xjo/2zS/E8vUR/Yf1f11Dr0u0jm8ub2/v K/xY8d//eKkiz8dHzqi8/cqN0XfwR1fkt745ug9fGxZ/L246qt3R493nxeXfuzIGNT bNz7lWvi53t47P/JT/Xs2fge fbYJtV3ZJz mW/EifP I 763p1xzae G3edcUVc8Wejo9 e/nBi90Cv16NzlsbrNXXkauvyj8Tt/op7/7zTc7a3bW3c2SN69ejOMXt/ao8gQIAAAQIECBAgQIAAga4C/wuIJvjmjtnAOQAAAABJRU5ErkJggg==[/IMG][ATTACH=CONFIG]255550[/ATTACH]

---

### Post by LaughingHorse on 2014-08-17
null

---

### Post by oldfred on 2014-08-17
As ajgreeny suggests, I do not recommend a separate /boot for new users, normally. It may be required with some server or server type installs using LVM or RAID or full drive encryption. You do have to regularly maintain it or remove old kernels so it does not fill up and create major issues. Otherwise it is ok.

Some examples of the Something Else installs. Most very similar:
       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

---

### Post by LaughingHorse on 2014-08-17
Thank You oldfred!

I did a bunch of reading of those links.

I liked the first link you gave the best.

Anyway...

I think I've got it. However, I still have a couple of questions.
I've never done an installation over the old one

1. Based on my set up, I would be installing into sdb6, and just leave the boot alone. Is that correct?
2. I'm not clear if I need to manually adjust the partitions, or if the installation will leave them as they are.
3. Since Grub is already installed, I will not have to do anything about it.

Regarding a separate /boot, it has filled up in the past and I just delete older kernels. That's not a problem.

I am wanting to install over the older version rather than update, as I understand this will give me a cleaner/better functioning installation.

---

### Post by oldfred on 2014-08-17
Attached are a couple of screen shots from my over installs of older versions. I only used / so do not have the added mount of /boot with formatting and mounting of /home withOUT formatting.

You push the change button, not + or -. But then it says edit partition.

---

### Post by ajgreeny on 2014-08-17
Yes, that dedoimedo link is exceptionally helpful, I agree, and you seem to have managed to understand what is about to happen, except for the separate /boot partition.


[LIST=1]
[*]Yes, you must use sdb6 as your new root partition, and you can either choose to format it, which is what I always do, or not format and just install over the old, which seems more likely to cause problems to me, but then I've never done it that way, so who am I to say. If you want to keep the /boot partition you will also need to select that in the something else list, and choose /boot as the mountpoint, ext4 as the filesystem, and select to format it, which will remove all the old kernels, and start clean again. If you do not do this the /boot partition will remain on disk but will not be used for booting the system.
[*]There is no real need to modify the partition sizes unless you want to.  If you do, bear in mind that it will possibly take a very long time to resize, so don't wonder what it happening and cancel the operation as that will totally corrupt the partitions, and possibly the whole disk.
[*]No, there is no need to do anything with grub except choose to put it on /dev/sdb, leaving the windows bootloader files on /dev/sda.  This will allow you to set sdb as the boot priority device and thus go to grub, where you can choose to boot either OS.
[/LIST]
I hope this clarifies matters for you, but if you still have questions, I'm here and will keep following this thread.

---

### Post by LaughingHorse on 2014-08-17
So would I be better off removing the boot partition?
If so, how would I do that without disrupting  my data (though I do have a backup)

---

### Post by oldfred on 2014-08-17
You just would reinstall without using/mounting it. New install then would have an updated /boot inside of / (root). 

But not particularly easy to re-arrange partitions to recover space, since first partition. It is small so I might just leave it?

A few BIOS also want to see a boot flag on a primary partition or you cannot boot at all. Grub does not use boot flag, it is a Windows (and Lilo) way to boot. So leave sdb1 with boot flag.

---

### Post by LaughingHorse on 2014-08-17
Thank you ajgreeny and oldfred,

ajgreeny, your reply came in just as I was writing my reply.

With both you and oldfred advising to ignore the boot partition on sdb, I will do that.
And thank you for the tip on reformatting.

My sda drive is exclusively windows.
sdb drive is exclusively ubuntu.

When I first installed 12.04 on this computer I set sdb as the boot priority device. Had some problems at first finding sdb and had to go into the bios to tell it to go there first. But such is life :p

Once I finish up what I am doing now, I will backup Firefox, and Thunderbird.
Run the back-ups earlier in the thread for the packages I'm using and do the install.

A side question, I was using Ubuntu Studio till I installed 12.04. I would like to go back to using that, is there anything I need to be aware of if i do? I know it will remove some packages and install other ones in their place.

---

### Post by oldfred on 2014-08-17
Do not know about Studio, but there is a sticky at the top of the sub-forum for it.

[http://ubuntuforums.org/showthread.php?t=1124138](http://ubuntuforums.org/showthread.php?t=1124138)

---

### Post by LaughingHorse on 2014-08-17
So I started the install.
I wanted to put the system into sdb6

How do I correct this?

---

### Post by oldfred on 2014-08-17
Please review post #20.

You have to scroll down to sdb6 and click the change button. Screen shots should show similar as to what you will see. You have to choose a partition, select change, select mount as  / (root), select ext4, check box for format and then it should work. Same for /home or any other system partitions. If existing swap it will be found automatically.
Any other partitions may have to be mounted via fstab after install.

---

### Post by LaughingHorse on 2014-08-18
Thank You oldfred,

Sorry I was not clear in my question above. When I saw that I kind of freaked. I thought it would automatically create space for root, and I would just approve (like in #20, and the URL's you had provided above). Instead it looks like I need to allocate space.

So do I need to allocate space for the boot, or will the install automatically do that for me?

If I have to allocate space:

1. How much should I give it?
2. Would that then start moving things around on my sdb6 [root] and sbd7 [data]?

---

### Post by oldfred on 2014-08-18
If you are ok with existing sizes of partitions, you do not have to make any changes.
You just click on change button, but have to choose which partition will be / (root) etc.

It is manual install and does not know which partition is which.

The auto install options just create / & swap but then those are always new partitions into space you create or is existing. And with the bug on reinstall erasing everything, you really have to use Something Else to manually choose partitions.

---

### Post by LaughingHorse on 2014-08-18
Thank You oldfred!

I think I have it now.
I will be doing the installation in about 5 hrs, because I know it will take time to update all the packages I have.

I appreciate your patience.

---

### Post by LaughingHorse on 2014-08-18
The install went smoothly after following your instructions oldfred.

Now I have a new problem...

Grub started. My selections for Ubuntu are:

3.2.0-67- generic
3.2.0-67- generic (recovery mode)

The windows system shows up as well booting from sda as expected.

I start Ubuntu from grub and after about a minute I get the following:

Gave up waiting for root device

Common problems:
- Boot args C cat /proc/cmdline
     - Check rootdelay= (did the system wait long enough?)
     - Check root = (did the system wait for the right device?)
- Missing modules (cat/proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/c4253cdc-59d9-4f18-8197-9cbf1780qef does not exist!

BusyBox v1.18.5 (Ubuntu 1:1.18.5 - 1ubuntu4.1) built-in shell
(ash)

Enter 'help' for a list of built-in commands
(initramfs)

---

### Post by LaughingHorse on 2014-08-18
some screen shots that may also give some insight

---

### Post by oldfred on 2014-08-18
Kernel 3.2 are from original 12.04 not 14.04 which should be version 3.13.
So did you not install?

Or is grub looking in the wrong place or old boot partition. Did you use it again or not?

---

### Post by LaughingHorse on 2014-08-18
I installed 14.04 and created a new boot in sd6 (journal4 just like discussed). So I guess Grub is looking in the old boot.
How can I check to see what version of Grub is loading?

---

### Post by oldfred on 2014-08-18
Post the link that the BootInfo report creates.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by LaughingHorse on 2014-08-18
Boot summary

[http://paste.ubuntu.com/8084010/](http://paste.ubuntu.com/8084010/)

---

### Post by oldfred on 2014-08-18
It looks like the grub in the MBR, still looks to the boot partition which now does not go anywhere.
And you installed grub to sdb6 when it should be installed to sdb not sdb6.

Do not run auto fix in Boot-Repair as it will install grub to every MBR, you want to keep Windows boot loader in sda.
But you can use Boot-Repairs advanced mode, choose Ubuntu and choose sdb as correct location for grub2's boot loader.

---

### Post by LaughingHorse on 2014-08-18
I want to verify the Boot repair settings are correct so here are screen grabs of the options. There is nothing in "MBR Options"

---

### Post by LaughingHorse on 2014-08-18
Re reading your instructions oldfred, and I see inGTUB Location I did not tick the "Place GRUB into:" and change it to sdb. I did make that changeon the setting, but have not done anything else yet.

TO clarify, I do not tick the "Separate/boot partition" nox. Is that correct?

---

### Post by oldfred on 2014-08-18
Your second post with just grub going into sdb is the correct one. 
The earlier one also has the install grub to every MBR which you do not want.
Only if major issues, should you need the full uninstall & reinstall of grub.
And your old /boot is not used now, so no you do not want to check separate /boot.

---

### Post by LaughingHorse on 2014-08-19
Thank you oldfred!

I did it, and can now boot up.

However, there is a new issue.

Since I was able to do the update and get it working, should I open a new thread for the new issue?

Also, I have a related question to that uissue regarding partitioning.

---

### Post by oldfred on 2014-08-19
Title should reflect issue, so if not install issue then a new thread is appropriate. Then users that may know about that issue will respond. Plus when a thread gets longer additional users that may be able to help stop looking.

How you partition is often related to install (we often suggest many alternatives, but each user has his own needs). Or is it mounting the partitions which probably should then be separate.

If install issues are resolved then change to solved.

---

### Post by LaughingHorse on 2014-08-19
Well, the install made some changes that brought up an issue. So I guess I will continue here.

Before the install, if I remember correctly I had 
/
allen (which had all my folders, and packages)

After the install, the folder allen is still there, however none of the packiages are in the new installation, even after I used the code in the link to upgrade them.

Here are a bunch of screen shots so you can see what I am talking about.[ATTACH=CONFIG]255643[/ATTACH][ATTACH=CONFIG]255642[/ATTACH][ATTACH=CONFIG]255641[/ATTACH][ATTACH=CONFIG]255640[/ATTACH][ATTACH=CONFIG]255639[/ATTACH]

I do have a couple more screen captures I will post in a reply right below, as I think I readhed the limit on this post.

---

### Post by LaughingHorse on 2014-08-19
More. These are the last two

---

### Post by oldfred on 2014-08-19
When you installed did you include the mount of /home like the mount of / (root), but NOT choose the format box?
If not your /home is not used. We can manually add it or reinstall but being sure to include /home.

The 237MB partition is your old /boot. And the 1.9TB looks like a data partition or external drive. And of course you Windows 7 partition is Windows.
I like to label every partition so I know what they are, but then I have a lot. I usually try to remember to label when I create partitions with gparted, but when I forget or change use I use Disks(14.04) or Disk Utility(12.04) and find the change label button.

You can add to fstab mounts of your data partitions, and I often suggest auto mounting your Windows system partition but in Read Only mode. Auto mount by Nautilus is read/write and too much writing directly into Windows can cause issues.

Instead of posting screen shots please use terminal and post terminal output. If longer output use code tags, which are easy to add with # in advanced editor's edit panel at top.

Shows partitions:
sudo parted -l
Shows mounted partitions, if you first click on it with Nautilus file browser it will be included
df -h
Shows mounted partitions, auto mounts by Nautilus will be in /media/$USER where $USER is your name.
mount
Shows the partitions you are mounting
cat /etc/fstab

This one also includes the labels.
       sudo blkid -c /dev/null -o list

This is only about half of mine:
```
fred@trusty-DT:~$ sudo blkid -c /dev/null -o list
[sudo] password for fred: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs    WinXP    (not mounted)  04B05B70B05B6768
/dev/sda2  ext3    backup   (not mounted)  13a684e4-2849-4566-9528-21cd07028a9a
/dev/sda4  vfat    SHARE    (not mounted)  46CD-C9B2
/dev/sdb2  ext4    Maverick (not mounted)  0eea4e95-ea0a-4745-80d4-57bf2bbc9d69
/dev/sdb3  swap             (not mounted)  00c4e383-cf30-4b54-9a9f-d46953e3966e
/dev/sdb4  ext4    MavData  (not mounted)  431ba9e5-c72c-41c2-ba82-d8ee052336ff
/dev/sdc1  ext3    grub     (not mounted)  9e16ad9c-c5f8-4b5a-b2b3-20dfc71a422f
/dev/sdc2  ntfs    Shared   /mnt/shared    44332FD360AA9657
/dev/sdc4  ext2    bios_gpt (not mounted)  bbda6045-bb8a-4666-8bd4-04b3945ca581
/dev/sdc5  ext4    trusty   (not mounted)  e94b3a65-6707-408c-b7e2-3ff205344aad
/dev/sdc6  ext3    Data     /mnt/data      a55e6335-616f-4b10-9923-e963559f2b05

```

I have been using Disk Utility in 12.04, I see with Disks they have hidden the edit partition under a tiny set of gears just above the size info nearer the bottom of what it shows. It also has some other settings which I have not used or used much.

---

### Post by LaughingHorse on 2014-08-19
Thank You oldfred!

I'm not sure if when I installed I included the mount of / but did not choose to format. I set it up several times, and kept running into questions, so when I finally did the install I might have missed that.

The 1.9TB is a partition, and that is where my old home "allen" is residing.

Ourput of sudo parted -l

```

Model: ATA ST2000DL003-9VT1 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  106MB   105MB   primary  ntfs         boot
 2      106MB   24.8GB  24.7GB  primary  ntfs         hidden
 3      24.8GB  825GB   800GB   primary  ntfs
 4      825GB   2000GB  1175GB  primary  ntfs


Model: ATA WDC WD2002FAEX-0 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  258MB   257MB   primary   ext2            boot
 2      259MB   2000GB  2000GB  extended
 5      259MB   33.0GB  32.8GB  logical   linux-swap(v1)
 6      33.0GB  135GB   102GB   logical   ext4
 7      135GB   2000GB  1865GB  logical   ext4

```

And sudo blkid -c /dev/null -o list


device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
```

/dev/sda1  ntfs    System Reserved (not mounted) 685215E95215BD2E
/dev/sda2  ntfs    Recovery (not mounted)  3830174630170A90
/dev/sda3  ntfs    WIN7     /media/allen/WIN7 F452D79B52D760C2
/dev/sda4  ntfs    DATA     /media/allen/DATA 0A4401CD4934F92B
/dev/sdb1  ext2             /media/allen/2de4798b-f414-4ddb-9d47-e4c5942073cf 2de4798b-f414-4ddb-9d47-e4c5942073cf
/dev/sdb5  swap             <swap>         7ae87800-384c-4c00-aba2-04351705bb89
/dev/sdb6  ext4             /              c7e088d0-0e86-47e6-bf6b-0474fe5f0cf3
/dev/sdb7  ext4             /media/allen/e7d4d342-963b-46e1-b3c8-7f0a97277e37 e7d4d342-963b-46e1-b3c8-7f0a97277e37

```

I really don't care about automatically mounting windows. I don't use it for anything unless absolutely necessary (some myopic website or application demands it)

When I do need to access any data on the drive, I just click on the drive in Nautilus.

I would like to label every partition.

I have no problem doing a reinstall, which would probably be best because that way I will learn how to do it properly and include the /home

---

### Post by oldfred on 2014-08-19
When you reinstall just be sure to choose the  same partition for / (root) or your sdb6, then also choose /home or your sdb7 but DO NOT check the format box. It will auto find swap. As before choosing a /boot partition is optional (your sdb1), I usually suggest that you do not want it.
And make sure you choose to install grub2 boot loader to sdb. That combo box is the bottom of the partition chooser screen.

But NTFS data partition cannot be mounted during install, and we must manually add to fstab after you reboot into install.

See my posts in #20 for example of overwriting an existing / with a new / install. I do not have /home, but that would be otherwise the same except NOT checking format box. Note on my screen shot it still shows sda as default for grub boot loader as I have not changed it to new MBR yet.

---

### Post by LaughingHorse on 2014-08-19
When I installed last time I did install in sdb6.
I don't recall an option to choose my home.

---

### Post by oldfred on 2014-08-19
Its manual install, you have to tell it you want to use a /home.
Just like you clicked on sdb6 and choose /, click on sdb7, click change and choose /home, but do not check format.
You had to do similar with original install as /boot would also be the same. Click on partition, click on change and choose what mount point it will be.
Minimum is / (root). But best to have swap and if swap exists it will auto find it. But you can add many other system partitions as separate folders. Usually with standard desktop just / and swap often /home are all that is required.

---

### Post by LaughingHorse on 2014-08-19
Thank You oldfred.

Finally, finally, finally after 5 reinstalls it is finally working properly.

Now for the second to last issue.

In post 15 you gave me instructions on how to make a backup of all installed apps to make it easy to reinstall.
I made the list.
It is in my home/allen directory
file name: my-packages

I ran the code you gave me
```

sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

```

But those packages were not re-installed into my system.

Do I need to copy the file someplace else?

---

### Post by oldfred on 2014-08-19
Did it give an error on dselect? You may have to install that.
sudo apt-get install dselect

And file must be in path you run it from. Which should just be your /home. 

Not sure you should see /home/allen unless /home not mounted correctly?
But if you click on computer in left panel, then on /home, it should show allen. But once you click on allen ti only shows Home at the top of Nautilus.

In terminal it should look like this.
fred@trusty-DT:~$ 

the tilde or ~ is a shortcut for /home/fred.

And this shows my file:
fred@trusty-DT:~$ ls -l my*
-rw-rw-r-- 1 fred fred 51919 Apr 24 16:57 my-packagestrusty.txt

---

### Post by LaughingHorse on 2014-08-19
I did not get an error on dselect

"if  you click on computer in left panel, then on /home, it should show  allen. But once you click on allen ti only shows Home at the top of  Nautilus."
Yes, that is what is happening

Yes, in my terminal it shows:
allen@allen-CM6870

Do I need to add the .txt to the file?

I have tried:
allen@allen-CM6870:~$ sudo dpkg --set-selections < allen/my-packages
bash: allen/my-packages: No such file or directory


allen@allen-CM6870:~$ sudo dpkg --set-selections < home/allen/my-packages
bash: home/allen/my-packages: No such file or directory

allen@allen-CM6870:~$ sudo dpkg --set-selections < home/my-packages
bash: home/my-packages: No such file or directory

Then I ran:
allen@allen-CM6870:~$  ls -l my-*
-rw-rw-r-- 1 allen allen 51778 Aug 19 17:55 my-packages

I'm not sure where do tell teh command to get it.

As you can tell, I suck at commands.

---

### Post by oldfred on 2014-08-19
When you are here, you do not need to add path to file if file is as shown in /home.
allen@allen-CM6870:~$

 sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

---

### Post by LaughingHorse on 2014-08-20
I tried, but it did not work.
Then I looked at the packages that were backed up. None of the packages I installed were backed up e.g. audacity, inkscape, xara, openshot, gimp... etc.
So I guess when I thought I was backing up I really did not.

Looking at what you gave me, and how I mis-understood I know I entered
dpkg --get-selections > ~/my-packages

When I guess it should have been 
dpkg --get-selections > my-packages

As I was in:
allen@allen-CM6870

My mistake.

So I will to mark this thread as closed.

I do need to open a new one due to my desktop acting up after changing wallpaper to Forever.

---

### Post by oldfred on 2014-08-20
Actually these are the same. ~/ is /home and if you run the second one when in home it will default to that. If you were in some other directory then it would be there.

Looking at what you gave me, and how I mis-understood I know I entered
dpkg --get-selections > ~/my-packages

When I guess it should have been 
dpkg --get-selections > my-packages

Did you look at the my-packages file. It is just a text file and may have a 1000 entries. But most are dependencies and apps already installed that would not be reinstalled.

If you know package names, not necessarily the application name, you can install from command line. 
Otherwise I prefer synaptic.

# is comment, do not copy comments
       apt-get update #resync package index
apt-get upgrade #newest versions of all current packages, update must be run first
# one user posted this as what he installs
sudo apt-get install ubuntu-restricted-extras non-free-codecs p7zip-rar acroread gimp inkscape blender smplayer vlc libdvdcss2 libdvdread4 faac faad audacious rubyripper cd-discid aacplusenc gtkpod lame cdrdao aacgain flac mp3gain normalizenze-audio vorbisgain arista soundconverter gnome-sushi exfalso winff devede openshot audacity cheese synaptic gconf-editor lsb-core

---

### Post by LaughingHorse on 2014-08-20
Hi oldfred,

Yes, I looked at the my-packages file that was generated. That's how I knew (too late) it did not collect the other packages.

Before I wrote my previous post, I deleted the old one, and tested to see what would happen when I did the command
dpkg --get-selections > my-packages

I opened the newly created file, and saw the packages there that I installed some by command line and some by synaptic.
Personally I prefer synaptic unless the package is not listed there.

Those are some really good packages.

I use a lot of those, as well as Spotify

Thank you very much for your kind help.
You have been awesome!

---

