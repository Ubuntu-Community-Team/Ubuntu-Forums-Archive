---
title: "beginner preseed installation question"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by hfturner on 2008-08-07
Greetings. I am new to Ubuntu and trying to figure out how to do automated installation, but I can't seem to get started. My network based preseed.cfg file is never accessed. I have tried
to specify the location in my dhcpd configuration and on the command/boot line. When the install window comes up and asks the first question (language) I can use the function keys to get to a standard commandline window. From there I see that my network interface is indeed up and using the expected information from my dhcpd server. But looking at /var/log/casper.log (I think that was it), it looks like it initially failed to configure eth0, then failed to fetch my preseed.cfg file, gave up on the preseed bit, and then at some later point did successfully get eth0 configured:

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
--20:07:43-- [url]http://172.n.n.n/full/path/to/preseed.cfg = > /tmp/preseed.cfg
Connecting to 172.n.n.n:80 failed: Network is unreachable


If anybody can provide any hints as to what I might be doing wrong, or where else I can look for clues I would really appreciate it.

Stuck for now:

--hft

---

### Post by Pumalite on 2008-08-07
This might help:
[https://help.ubuntu.com/7.04/installation-guide/i386/preseed-using.html](https://help.ubuntu.com/7.04/installation-guide/i386/preseed-using.html)
[http://www.debuntu.org/how-to-unattended-ubuntu-network-install-preseed-p5](http://www.debuntu.org/how-to-unattended-ubuntu-network-install-preseed-p5)
[http://ubuntuforums.org/showthread.php?t=3900](http://ubuntuforums.org/showthread.php?t=3900)

---

### Post by hfturner on 2008-08-08
Thanks. I had read the first two, actually on the first one, a 8.04 version, which is what I am trying to figure out how to load.  I had not seen the last link. But that thread is dated 2004 and contains:

>> So does Ubuntu support preseeded installation?

> no! 

If that is accurate, it would seem to contradict most of what I have read in the "B. Automating the installation using preseeding" section of the current version of the "Ubuntu Installation Guide". It tells you to configure your dhcp server with something like 'filename "http://172.n.n.n/compsys/SW_Repos/Ubuntu/x86_64/preseed.cfg";' or to append the boot option "auto url=http://172.n.n.n/compsys/SW_Repos/Ubuntu/x86_64/preseed.cfg" neither of which seems to be working for me, because, it seems, it tries to fetch the preseed.cfg file BEFORE it has successfully brought eth0 up.

Still stuck.
--hft

---

### Post by hfturner on 2008-08-18
Well, for the record, I wasn't too far off on what I was trying.
I finally tried to preseed on some different/older hardware and
it worked fine, at least as far as accessing my preseed.cfg file.
I still have a lot I don't grok about how to actually use much of
what is in the preseed file (like I can find no evidence that it
ever tried to use my "preseed/late_command"). But my main problem
is still that can't seem to use network based preseeding on the
bulk of the new hardware that I was hoping to do automated Ubuntu
installs on. If I just do a normal install from the LiveCD it does
bring the ethernet up eventually, just not until after it tries 
and fails to load the network based preseed file. I suppose that,
once I finally figure out what I want in my preseed file, I could
figure out how to put it on some media and thus avoid the network
part of this problem. But in the environment in which I work, media
handling restrictions make this a much less attractive option.
I would really like to figure out how to do network preseeding
on my new batch of workstation hardware. Thanks for any suggestions.

--hft

---

