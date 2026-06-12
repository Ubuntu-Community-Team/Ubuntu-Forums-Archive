---
title: "Alert /dev/disk/by-uuid...does not exist"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by novice buntu on 2008-11-19
Hi,

Ubuntu 8.10 on Dell Precision T5400 with SAS HDD.

This is my first attempt at installing ubuntu and I have hit a problem. I installed from CD (3 times now) and created new partitions. Grub was installed on /dev/sda1 (/boot). When I boot I get the error:

ALERT! /dev/disk/by-uuid/3.. does not exist. Dropping to a shell.


The link exists and I can mount /dev/sda2.

ls -l 
lrwxrwxrwx /dev/disk/by-uuid/3... -> ../../sda2

The cmdline looks correct.
 
cat /proc/cmdline:
root=UUID=3....8

If I select the recovery mode, the scsi module load and there are messages that 
 sda: sda1 sda2 sda3
Driver 'sr' needs updating - please use bus_type
[sda] Write protect off ..

However I end up with the same error.

I could use some help now as I am not sure what else to try. I don't know where the rootdelay is set.

---

### Post by caljohnsmith on 2008-11-19
How about when you get the Grub menu on start up, select the first Ubuntu kernel entry, press "e" to edit it, select the "kernel" line, press "e" to edit it, and at the end of the kernel line add "rootdelay=130" similar to:
```
kernel	/boot/vmlinuz-2.6.27-7-generic root=UUID=d0b10c15-66ed-4d1c-b7f6-c1fc131636f7 ro quiet splash [COLOR="Red"]rootdelay=130[/COLOR]
```
Press enter to save the change, then "b" to boot. Let me know if that makes any difference. :)

---

### Post by novice buntu on 2008-11-19
Wow, Thanx. That's done it. 

I'm trying to get an better idea of the cause and recovery of this.

rootdelay=nn is a command passed to the kernel (not grub) to say wait nn before accessing the partition, Is that correct? I guess I can trail and error to find out the minimum delay I can use.

Thanx again. Much appreciated.

---

### Post by caljohnsmith on 2008-11-19
> **novice buntu said:**
> Wow, Thanx. That's done it. 

I'm trying to get an better idea of the cause and recovery of this.

rootdelay=nn is a command passed to the kernel (not grub) to say wait nn before accessing the partition, Is that correct? I guess I can trail and error to find out the minimum delay I can use.

Thanx again. Much appreciated.
Glad that worked for you; it is a kernel parameter and not Grub parameter as you say, but other than that, I don't know any more of the technical details about it since I haven't bothered to research it. What happened is I saw another thread recently where someone had the same type of problem as you, and that's how they fixed it; so I'm just passing it along. If you have the time though, it would be great if you could file a bug at bugs.launchpad.net and alert them so maybe they can get to the root cause of the problem, and of course let them know your workaround. Anyway, cheers and have fun with Ubuntu. :)

---

### Post by chadsmith729 on 2009-01-23
I know resurecting old threads are really bad to do.  However, I just ran across this issue with Kubuntu 8.10.  I installed Java 6 and Eclipse.  Right after I restarted this problem came up, almost exactly.  So I used this trick that cal said and it worked perfectly!  Now I am back up and running and cal ... you freaking rock!

First post on the forums, I know I'm a total N00B.  My new years resolution was to become completely open source.  So far, I have it completely down except for Photoshop.  Just can't break the habit but I'm working on getting better with Gimp.

Take care,
Chad

---

### Post by n0manarmy on 2009-05-04
> **caljohnsmith said:**
> How about when you get the Grub menu on start up, select the first Ubuntu kernel entry, press "e" to edit it, select the "kernel" line, press "e" to edit it, and at the end of the kernel line add "rootdelay=130" similar to:
```
kernel	/boot/vmlinuz-2.6.27-7-generic root=UUID=d0b10c15-66ed-4d1c-b7f6-c1fc131636f7 ro quiet splash [COLOR="Red"]rootdelay=130[/COLOR]
```
Press enter to save the change, then "b" to boot. Let me know if that makes any difference. :)

This also worked for me. I fresh install of Jaunty on a Dell Power Edge 6600 failed until I added the delay in like you suggested. I'll toast to you tonight good sir!

---

### Post by j1n3l0 on 2009-05-14
Hi,

I have run into a similar issue. I just installed ubuntu 8.10 on an old Dell Desktop 2 days ago. That worked more or less okay. I then chose to upgrade to 9.04. Twice it froze during the upgrade process -- at around file 720 of 1019 or something -- so I decided to install the updates instead. It suceeded in downloding and installing the files and a restart was requested. However, since I restarted the system I get the above error:

```
ALERT! /dev/disk/by-uuid/3.. does not exist. Dropping to a shell.
```

I've tried the recommendations but I get no joy. I did notice that there does not seem to be a kernel in my file where I specify the root delay!

```
<no kernel info>... root=UUID=d0b10c15-66ed-4d1c-b7f6-c1fc131636f7 ro quiet splash rootdelay=130
```

This is a part of Ubuntu I never thought I'd see so I'm comfortably out of my depth here! Any help would be appreciated.

Thank you.

---

### Post by moodah on 2013-01-13
Just solving incase someone needs in the future..

The problem is the UUID is not correct within menu.lst.

1) type 'blkid' and write down the UUID of your main partition.
2) type 'reboot'
3) hit escape at the boot menu when booting up.
4) press 'e' to edit on the default boot up kernel.
5) update the UUID in here to reflect the correct one.
6) hit enter to save.
7) hit 'b' to boot from it

Ubuntu should boot.

IMPORTANT:

8) go into /boot/grub/menu.lst and update all the UUID's in there to reflect the correct ID. Else you'll have to repeat steps 1-7 above every boot.

---

