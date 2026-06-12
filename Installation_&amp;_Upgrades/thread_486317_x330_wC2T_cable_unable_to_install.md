---
title: "x330 w/C2T cable unable to install"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by jtombre on 2007-06-27
I have an IBM x330 with the C2T cable. The C2T allows multiple x330 systems to be daisy chained to a single VGA, with ps2 keyboard and mouse. 

The systems boots fine with 6.10 and 7.04. I received the initial flashscreen that prompts for the Install to Disk. I click return and it starts the install. However, after I hit return on the Install to Disk, they keyboard mapping gets all messed up and I can not continue the install. ie, when I hit return on English for language, it dumps me to the 'm' listing. My return has been mapped to an M.  I tried to play with the initial keyboard map at the flashscreen F3 or F4 I think. No matter what option I select, I am not able to continue.

I am using a standard 101-IBM PS2 keybaord.

I have tried to unplug the keyboard and plug it back in. That solved my issue with Red Hat installation. Suse installs good. Debian installed ok as I remember.

I am going to try the 7.04 alternate but am not too optimistic.

Thanks! Jay

---

### Post by jtombre on 2007-06-27
I have tried the alternate CD, but keep receiving an error that the CD is corrupt. /cdrom/dists/feisty/main/binary-i386/Packages.gz failed the disk check. However the md5 sig on the CD is the same as I get from an md5sum on the Packages.gz file.   I am downloading the 6.10-alternate to see if I have any better luck.  --J

---

### Post by jtombre on 2007-06-28
the 6.10 alt distro rolled back to the keyboard map problem. If anyone has any suggestions, they would be appreciated.  --J

---

### Post by coresus on 2007-07-24
I had the same issue.  I could not install Feisty from the desktop disk, the server disk, or an alternate cd.  I ended up doing manual upgrades from a Dapper server install disk.

---

### Post by toyoder on 2007-08-09
Me too... ubuntu 704 server
x330 install hangs at 21% -  libc6-udeb 
install cd passes media check on two other cd-rom drives in different machines
tried various boot options but all resulted with install hanging at the same point

---

### Post by gwhit918 on 2007-08-23
I'm getting the exact same behavior on an IBM x232... Ubuntu Server 7.04 hangs at 21% in the install at libc6-udeb every time.  

This bug report [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/23085](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/23085) deals with the issue... it's related to CD drive hardware incompatability, and it looks like they've closed the bug.  I guess we're suppposed to either a) know how to flash our drive's firmware to a later version, or b) install a new drive.

---

### Post by gwhit918 on 2007-08-24
UPDATE: 6.06 LTS Server installed just fine.  Go figure!  Took about 30 minutes to complete the "Install a LAMP server" option.  This meets my needs, so I'll just hope that the issue gets resolved for those still waiting.

---

