---
title: "Upgraded from 10.10 to 11.04 and now can't boot!"
date: 2011-05-17
forum: Installation &amp; Upgrades
---

### Post by oat_ on 2011-05-17
Hi, this is my first post so bear with me as I will really appreciate your help. I never really liked asking for help and always searched for solution by google but this is the first time I am stumped and cannot resolve. 
 
I upgraded from 10.10 to 11.04 via the update manager and somehow in the middle of it, the package failed. And so I carried on using the ubuntu, rebooted and now the disk is not ready and cannot mount. Press S to skip or M for manual recovery. Skip does nothing, only can use manual recovery.
 
I tried everything from the ubuntu forums & google from other people who had the same problem. The problem is my root terminal on manual recovery doesn't have networking. Only can use liveCD which I still can't connect to the internet because I use wlan0 from ndiswrapper.
 
I am a dual booter of Ubuntu 10.10 on one partition and Windows XP on other. I edited the grub to boot those. One HDD is partitioned into 2 drives so one partition holds XP and the other partition is a "translator" that holds files which both ubuntu and XP can access. (don't ask me why, I cleaned the dust off my PC recently after 3 years :P)
 
 
My outputs are:
 
 
/boot/grub/menu.lst
 
```

[FONT=Courier 10 Pitch]title       LINUX - Ubuntu 10.10 - kernel 2.6.35-28-generic[/FONT]
[FONT=Courier 10 Pitch]root        (hd1,0)[/FONT]
[FONT=Courier 10 Pitch]kernel            /boot/vmlinuz-2.6.35-28-generic root=UUID=85de06c5-cf3e-46b8-8c14-2c217be8dd9d ro vga=0x317 splash[/FONT]
[FONT=Courier 10 Pitch]initrd            /boot/initrd.img-2.6.35-28-generic[/FONT]
[FONT=Courier 10 Pitch]quiet[/FONT]
 
 
[FONT=Courier 10 Pitch]title       Windows XP Professional[/FONT]
[FONT=Courier 10 Pitch]root        (hd0,0)[/FONT]
[FONT=Courier 10 Pitch]makeactive[/FONT]
[FONT=Courier 10 Pitch]chainloader +1[/FONT]
 

```
 
 
/etc/fstab
 
```

[FONT=Courier 10 Pitch]# /etc/fstab: static file system information.[/FONT]
[FONT=Courier 10 Pitch]#[/FONT]
[FONT=Courier 10 Pitch]# <file system> <mount point>   <type>  <options>       <dump>  <pass>[/FONT]
[FONT=Courier 10 Pitch]proc            /proc           proc    defaults        0       0[/FONT]
[FONT=Courier 10 Pitch]# /dev/hdb1[/FONT]
[FONT=Courier 10 Pitch]UUID=85de06c5-cf3e-46b8-8c14-2c217be8dd9d /               ext3    defaults,errors=remount-ro 0       1[/FONT]
[FONT=Courier 10 Pitch]# /dev/hdb5[/FONT]
[FONT=Courier 10 Pitch]UUID=8f71786e-e3b6-4f5a-b1ee-ce249dd4f57c none            swap    sw              0       0[/FONT]
[FONT=Courier 10 Pitch]/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0[/FONT]
[FONT=Courier 10 Pitch]/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0[/FONT]

```
 
 
blkid
 
```

/dev/sdb1: UUID="85de06c5-cf3e-46b8-8c14-2c217be8dd9d" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb5: UUID="8f71786e-e3b6-4f5a-b1ee-ce249dd4f57c" TYPE="swap"
/dev/sda1: UUID="DE2853AE28538485" TYPE="ntfs"
/dev/sda5: LABEL="TRANSLATOR" UUID="147553BCE0BA3D91" TYPE="ntfs"

```
 
- I commented the UUIDs, that doesn't work.
- I tried remounting it, no effect.
- I fsck'ed it, no effect.
- I booted using LiveCD but cannot connect to the internet due to wireless.
- Cannot apt-get update & upgrade due to no internet.
 
That's all I remember cos I basically tried alot different ways and cannot get it to boot.
 
I am thinking of formatting the mess and start all over again but I don't really want to do that because it is a good system, just that the grub file and fstab is kinda cluttered.
 
Any idea what I should do?

---

### Post by Hedgehog1 on 2011-05-17
If you boot from the 11.04 LiveCD/LiveUSB, you may have an upgrade path offered in the 'install 11.04'.

[IMG]http://img848.imageshack.us/img848/874/upgradetonatty.png[/IMG]

**If this is not offered**, if you have your data in a separate '/home' partition you can reinstall 11.04 over your 10.10 '/' partition and be sure to not format the '/home' partition:

First, define your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Then define your '/home' partition:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

***The Hedge***

:KS

p.s. To learn how to move your '/home' into it's own partition: **_[SeparateHomePartition]("http://www.psychocats.net/ubuntu/separatehome")_**

---

### Post by oat_ on 2011-05-18
Thank you for the response!
 
Booted using Ubuntu 11.04 LiveCD but failed:
 
```

[     0.016437]  [Hardware Error] : No human readable MCE decoding support on this CPU type.
[     0.016502]  [Hardware Error] : Run the message through 'mcelog --ascii' to decode.
General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and reboot the system.
bash: /root/.bashrc: Input/output error
root@ubuntu:~#

```
 
 
Maybe I should try the Wubi installer using the Windows XP?

---

### Post by oat_ on 2011-05-25
bump.

---

### Post by oat_ on 2011-05-26
Hmm.

I waited for a week.

Any idea?

---

### Post by oat_ on 2011-05-31
I'm guessing that the silence to my thread means there isn't anyone who are willing to help me?  Or is there no ways I can fix this?

I will appreciate it if someone response to this and guide me to saving my files.

---

### Post by oat_ on 2011-06-01
Thanks.

---

### Post by bcbc on 2011-06-01
You cannot use Wubi to install over a normal install. 

You probably have a problem with your Ubuntu CD (a bad burn?). Boot from it, hit spacebar when little keyboard appears, and select to check the CD from the extended menu.
If there is a problem burn another.

---

