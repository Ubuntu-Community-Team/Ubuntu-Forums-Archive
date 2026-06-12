---
title: "Weird grub error and conflicting version"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by aaronp on 2010-10-17
Hi all,

I upgraded to Maverick from Lucid last week and the upgrade went well, except for a grub problem (xputs error - due to multiple drives apparently) which was easily fixed using a livecd to reconfigure grub.

Anyway, ever since then I'm getting some grub errors every time the PC starts up, but then it successfully loads into the desktop anyway.
If I switch to tty1 the errors are still there. Weird thing here is when I login I get two welcome banners, 1 saying Ubuntu 10.10 and the other saying Ubuntu 10.04. And always telling me a system restart is required.

Just want to find out what the grub and CIFS errors are (and why they don't prevent the system from starting anyway) and also wondering what's going on with the two version numbers coming up + system restart advice.

Here's the output:

```
GRUB loading.
syntax error
Incorrect command
syntax error
error: file not found
   [Linux-bzImage, setup=0x3400, size=0x413e50]
   [Initrd, addr=0x2f5b3000, size=0xa44e18]
[   20.601751] CIFS VFS: Error connecting to socket. Aborting operation
[   20.601817] CIFS VFS: cifs_mount failed w/return code = -101

mountall: Disconnected from Plymouth

Ubuntu 10.10 apbh tty1

apbh login: aaron
Password:
Last login: Mon Oct 18 10:48:39 EST 2010 on tty1
Linux apbh 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:24:00 UTC 2010 i686 GN
U/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

*** System restart required ***
No mail.
aaron@apbh:~$ 
```

thanks
Aaron

---

### Post by efflandt on 2010-10-17
Looks like something may not have totally completed, and did not properly update your motd.  Check contents of /etc/motd and /etc/update-motd.d

---

### Post by PhilLord on 2010-10-24
Think I am getting the same problem. 

I also had a hosed machine after upgrade to maverick (an RC version in my case). I also have two hard drives (home on one, system on other). I also recovered using a Live CD (9.10 in my case, as it was the only bootable thing I had). 

On booting from powerup, I generally get the "syntax error" message. I have to force reboot, with ctrl-alt-delete. Second time around it boots, although hangs at grub menu. 

I don't get the dual splash screen though. 

Phil

---

### Post by efflandt on 2010-10-24
For the dual version login, try removing /etc/motd.tail (that is where the Lucid part comes from).

Have you done **sudo update-grub** once you were able to boot from Ubuntu from the drive?  Do you actually know which grub on which drive is booting your system?  Maybe there is some lag spinning up if it is not the primary drive on that channel.

Booting a USB hard drive I occasionally get Drive not ready mounting / ... which seems kind of silly when it found its way from grub to splash screen in that partition on that drive, but if I wait a few seconds, it continues.

---

### Post by BC20100 on 2010-10-28
Had A problem Much Like this one I updated from 10.4 to 10.10 when the update finished it was all well.
Asked me to restart do i restarted and then i got this error "Devise not found : (a large number) underneath is Grub rescue.
I have windows 7 installed next to Ubuntu and that error doesn't let me open both :confused::confused: What Now ?

---

