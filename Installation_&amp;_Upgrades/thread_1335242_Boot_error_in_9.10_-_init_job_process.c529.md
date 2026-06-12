---
title: "Boot error in 9.10 - init: job_process.c:529:"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by Mark Hulme on 2009-11-23
Upgraded to 9.10 Karmic Koala without major incident.  Now the system will not boot except from the liveCD.   Errors shown below:

[B]init:  job_process.c:529: unhandled error from job_process_spawn: Permission denied.
failed to spawn mountall_shell main process[/B]

The upgraded Ubuntu install is on its own partition on a SATA drive.  In an attempt to fix the problem, I installed 9.10 on an older ide drive, but the boot error is the same.

A couple of folks had a similar error on the spamish adn hungarian forums, but I can't see a solution, even with google translate:

[LIST]
[*] [www.ubuntu-es.org/?q=node/122563](www.ubuntu-es.org/?q=node/122563)
[*] ubuntu.hu/node/13833
[/LIST]
 The last few process I worked on prior to this error were:

[LIST=1]
[*]Fixed the difficulty withpulseaudio and ICE1712 soundcard:[URL="https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442"] https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442

[/URL]
[*]Installed Spideroak backup [https://spideroak.com/](https://spideroak.com/)
[/LIST]

I will post the /var/log/syslog below if that helps.

Thanks in advance.

---

### Post by Mark Hulme on 2009-11-23
As indicated above, here is the var/log/syslog.

Thanks again.

---

### Post by alfplayer on 2009-11-23
From syslog:

```
EXT3-fs warning: mounting fs with errors, running e2fsck is recommended
```

I suggest you run a file system check.

---

### Post by Mark Hulme on 2009-11-24
Thanks - I previously ran a filesystem check on the drive using Gparted from the live ubuntu CD, it fixed a few errors but seemed to make no difference to this boot issue.

After the upgrade to Karmic, the system would run out of memory after about 10 minutes of inactivity, forcing me to restart.  The drive was apparently mounting read only.  Tried to fix this in the fstab, but this boot error overtook me in that process.  Would this repeated restarting have led to corruption of the filesystem?

I have run another e2fsck on both drives, but the errors are the same: 

[B]init: Failed to spawn udevmonitor main process:  unable to execute:  Permission denied
init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied.
init: Failed to spawn udevtrigger main process: unable to execute: Permission denied
[/B][B]init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied.
[/B][B]init: Failed to spawn udev-finish main process: unable to execute: Permission denied
[/B][B]init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied.
[/B][B]init: Failed to spawn networking main process: unable to execute: Permission denied
[/B]***  (tries and fails to mount hard drives)[B]init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied.
[/B][B]init: Failed to spawn mountall post-stop process: unable to execute: Permission denied
[/B][B]init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied.
[/B][B]init: Failed to spawn mountall-shell main process: unable to execute: Permission denied
[/B]**init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied.**
**init: Failed to spawn mountall-shell post-stop process: unable to execute: Permission denied**
Grub loads fine, and I can chose any of 4 kernels, but all have similar init errors to those listed above.The realtime (rt) kernel gives these errors:[B]

udevadm trigger is not permitted while udev is unconfigured.
udevadm settle is not permitted while udev is unconfigured.
svgalib: Cannot open  /dev/mem.
Gave up waiting for root device.  Common problems:
 - Boot args (cat  /proc/cmdline)
    - Check rootdelay= (did the system wait long enough?)
    - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modulees; ls/dev)
Alert!/dev/disk/by-uuid/1sf-----etc does not exit.  Dropping to a shell!

[/B]Thanks!

---

### Post by alfplayer on 2009-11-24
I'd try to fix the file system using a live cd. If succesful, change back fstab to what it should be, and try to boot the system. If the system still hangs after a period, I'd try to find out why it happens, because that may be the cause of the file system errors.

---

### Post by psaxl on 2009-11-26
I've just had the exact same problem on Ubuntu 9.10 ! But have installed previously pysdm and then IMPOSSIBLE to boot anymore. I tried to check file system but nothing goes up. :mad:

---

### Post by andrewkirk on 2009-12-01
I've just had the same error too in a system upgraded to 9.10 a couple of weeks ago. I've tried booting in recovery mode and in all available earlier versions of the kernel with the same result. I've checked the fstab and it's unchanged since several months ago and also looks just as it should be. Just in case I commented out the fstab entries that automount all partitions except the ubuntu OS partition, but still no dice.

Help please!

PS out of five computers in our house dual booting Windows and XP, I have so far upgraded two of them to 9.10 and both have been disasters, while 9.04 continues to run rock-solid. I'm thinking of addressing this latest problem by doing a clean reinstall of 9.04. I hope this isn't an indication that 9.10 is Ubuntu's Vista ;)

---

### Post by Apewall on 2009-12-21
I am getting this as well after a normal reboot of the machine, there is nothing wrong with the filesystem of any of the drives. and they work on a separate installation.

All I did was make an init.d script and now the OS does not load:/

---

### Post by kos.rock on 2009-12-26
I had the same problem after i installed windows 7, reinstated grub2 and tried to set permissions for other file systems using Storage Device Manager.

That apart, the solution to this is to some how reach the fstab file (say by booting into Live CD and navigating to the linux file system on your hard disk)and change the boot options for the linux.

My fstab looked like this

# / was on /dev/sda6 during installation
UUID=26bdffc8-3d74-40e5-b440-2e254b83f651  /              ext4         user,users<other options i dont remember>                   0  1   

Changed it to 

# / was on /dev/sda6 during installation
UUID=26bdffc8-3d74-40e5-b440-2e254b83f651  /              ext4         **relatime,errors=remount-ro**                   0  1  

Another thing i'd like to mention is that i did reinstate grub and ran update-grub. If simply changing fsttab does not work, do try this step as well.

---

### Post by Martin McFly on 2010-02-13
I have the same problem. All I did was that I added few programs to startup list - Krusader and Audacious2.

---

### Post by EMABrad on 2010-04-04
Same problem.  Help!

---

### Post by eternalnewbee on 2010-04-16
Same problem here.

In addition I got this:

[ 129.7101151] Ext4-fs error (device sda3): _ext4_get_inode_loc:
unable to read inode block inode - 32578, block 3093
AppArmor profiles failed to load


Is it possible that the Harddisk is really failing?
I get system freezes, and the system often gets very slow. This has been going on for several weeks now . . .

---

### Post by eternalnewbee on 2010-04-25
ok.

In my case the hard disk failed. So no bugs.

---

