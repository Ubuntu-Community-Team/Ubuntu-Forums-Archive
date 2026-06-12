---
title: "No boot in 10.04 after kernel 2.6.32-33"
date: 2011-07-19
forum: Installation &amp; Upgrades
---

### Post by climbe2 on 2011-07-19
Hello, rather new to linux ubuntu, ran into this problem:

Running Ubuntu 10.04 as 2nd OS to Windows on a separate partition.  running an AMD 32bit.  After upgrading to kernel 2.6.32-33, Ubuntu will not load.  Recieved the error: 

Gave up waiting for root device. common problems:
-root args (cat /proc/cmdline)
  -check rootdelay=
  -root=
-missing modules (cat /proc/modules; ls /dev)

Down further, it says:

Alert:
/dev/disk/by-uuid/e3df952c-d462-4292-bab6-4965da1d567c does not exist.  Dropping to a shell. 

Then Busybox v.1.13.3 (built in shell) is executed, and I am left with:

(initramfs) 

I am not sure what has happened here... never seen this before, but I am not sure how to get around it.  I have tried loading earlier kernels, but to no avail...same general error messages.  Was it the kernel upgrade that did it...or something else? I am not too familiar with command-line interface...any suggestions? Thank you all!

CMB

---

### Post by mikewhatever on 2011-07-19
Something seems to be wrong with the root partition. It could be the partition table corruption or even a disk failure. Try booting from a Live CD and check if the Ubuntu partition is accessible.

---

### Post by climbe2 on 2011-07-20
Is a Live CD the installation source disk?  If so, I put it in, rebooted and got the following message:

Generating locales...
   en_US.UTF-8... done
Generation complete.
Using CD-ROM mount point /cdrom/
Identifying.. [blah blah...char...num...char...num...]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes, and 1 signatures
Found label 'Ubuntu 10.04.1 LTS _Lucid Lynx_ Release i386 (20100816.1)'
This disc is called:
Ubuntu 10.04.1 LTS _Lucid Lynx_ Release i386 (20100816.1)'
Copying package lists...gpgv: Signature made Mon Aug 16 2010 UTC using DSA key ID [blah]
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>
Reading package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - release i386 (20100816.1)]/ lucid main restricted
Repeat this process for the rest of the CDs in your set.
W: Skipping nonexistent file /cdrom/dists/lucid/main/binary-i386/Packages
W: Skipping nonexistent file /cdrom/dists/lucid/restricted/binary-i386/Packages
stdin: error 0
Killed

It repeats this message many times, and doesn't ask for any user input.  I should also mention that I am able to boot up Windows on the other partition.  Hope this helps, thanks

CMB

---

### Post by jramshu on 2011-07-20
Boot it up, after it drops to busybox give it about 60 seconds, then just type "exit", without the quotes. See what happens. Mine did this a while back and it seems it needed a short delay for bios to id the drive.

---

### Post by climbe2 on 2011-07-20
After waiting a minute or two and typing 'exit' I received the following:

/init: line 271: can't open /root/dev/console: no such file
[99.422757] Kernel panic - not syncing: Attempted to kill init!
[99.422823] Pid: 1, comm: init Tainted: G    D     2.65.32-33-generic #70-Ubuntu
[99.422895] Call Trace:
[99.422958]   [<c05895ee>] ? printk+0x1d/0x1f
[99.423018]   [<c0589524>] panic+0x48/0xf5
[99.423080]   [<c014f9ad>] forget_original_parent+0x2bd/0x2c0
[99.423142]   [<c014f9c3>] exit_notify+0x13/0x170
[99.423203]   [<c01512d9>] do_exit +0x189/0x310
[99.423263]   [<c015149e>] do _group_exit+0x3e/0xa0
[99.423323]   [<c0151518>] sys_exit_group+0x18/0x20
[99.423385   [<c01033ec>] syscall_call+0x7/0xb

---

### Post by climbe2 on 2011-07-20
Update:  downloaded new 10.04 iso, made a liveUSB.  when booting from new liveUSB, now get the error: 

/init: line 7: can't open /dev/sr0: No medium found 
Unable to open '/dev/sda'
stdin: error 0
Killed

Why can't I even boot from a USB or CD?

---

### Post by mikewhatever on 2011-07-22
Looks a lot like a hardware problem, perhaps the SATA controller or something.

---

