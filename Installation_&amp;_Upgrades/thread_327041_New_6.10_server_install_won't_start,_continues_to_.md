---
title: "New 6.10 server install won't start, continues to reboot"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by brownserver on 2006-12-28
I just installed Ubuntu using the 6.10 server disc. The install didn't seem to have any problems. I completely wiped out the hard drive and this is the only OS installed now.

However, when I try to boot the machine, it goes through Grub, shows a message that it is starting, then the machine reboots. This process continues. I tried booting in recovery mode, but the same thing occurred.

The box I installed on is pretty old, probably at least 8 years. It's got 64M of RAM, so not a lot, but I'm not getting any error messages, just a reboot.

---

### Post by garton on 2007-01-14
Same problem here, but with Ubutnu 6.06.1 server. Constant reboots, no kernel messages at all. Did you find a solution to this?

---

### Post by icefaerie on 2007-01-14
I've had this same problem with my server, but despite filing a bug report with a dozen or so confirmations it's not been fixed AFAIK.  Apparently the server install CD can cause that endless reboot cycle on older motherboards.  What worked for me was doing a server install from the 6.06 alternate CD.

---

### Post by cliveb on 2007-03-27
> **icefaerie said:**
> What worked for me was doing a server install from the 6.06 alternate CD.
The same is happening to me (old Gigabyte GA-5AA motherboard).

Can I ask: what is the "alternate" CD? I can see it on the download sites, but can't find a description of what it actually is. (I'm a Linux newbie, in case it isn't obvious).

---

### Post by confused57 on 2007-03-27
> **cliveb said:**
> The same is happening to me (old Gigabyte GA-5AA motherboard).

Can I ask: what is the "alternate" CD? I can see it on the download sites, but can't find a description of what it actually is. (I'm a Linux newbie, in case it isn't obvious).

The Alternate cd has a text based installer(same as the server install cd), some excellent screenshots here:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

You can choose "Command Line" install for installing the server...a full install would end up the same as if you installed with the desktop live cd.

You might want to read this thread also:
[http://www.ubuntuforums.org/showthread.php?t=290903&page=2](http://www.ubuntuforums.org/showthread.php?t=290903&page=2)

---

### Post by cliveb on 2007-03-27
> **confused57 said:**
> 
You might want to read this thread also:
[http://www.ubuntuforums.org/showthread.php?t=290903&page=2](http://www.ubuntuforums.org/showthread.php?t=290903&page=2)
Thanks very much for the advice. That other thread has the info I need.

---

