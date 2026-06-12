---
title: "Ubuntu server install hangs &quot;Retrieving files/Cleaning up&quot;"
date: 2013-10-02
forum: Installation &amp; Upgrades
---

### Post by headers on 2013-10-02
Dell 710 server.  Previously ran Ubuntu just fine. Trying to install any ubuntu server, preferably LTS.

The failures:

[LIST]
[*]CD install of Ubuntu server 12.04 LTS, install hangs on various "retrieving files" steps later in the install and does not complete. Sometimes see bad mirror problem (I did not change any mirror info during process).
[*]CD install of Ubuntu server 13.04, same as above.
[*]PXE based install of Ubuntu server 13.04,  hangs very quickly, presumably when "retrieving files".
[*]CD install of Ubuntu server 12.04 LTS, machine has NO NETWORK.  Hangs on the "Cleaning up" step at the very end.  Upon attempted boot we see no bootloader installed.
[*]CD install of Ubuntu server 13.04, machine has NO NETWORK, same as above.
[/LIST]


An unfortunate success:
[LIST]
[*]PXE install of Centos6, works fine first time.
[/LIST]

I want ubuntu, not Centos. 

One hint from a friend is problems with IPv6 on ubuntu mirrors.  We cannot isolate or confirm that though.

Thanks in advance for any help.

---

### Post by TheFu on 2013-10-02
During install, unplug the network cable.
I found that if the internet wasn't accessable, but networking was enabled, the installer kept trying over and over and over and over and over ... every request had to time out.  Much easier to unplug the cable, do the install, secure the services, plug in the cable and setup networking.

I usually disable ipv6 too - if you aren't actively using it, it is a security risk.

---

### Post by headers on 2013-10-02
This is what I did to force a "NO NETWORK" installs, 4th and 5th cases,  and it failed on the "cleaning up" step at the end of install.

How do I disable IPV6 during install?

---

### Post by TheFu on 2013-10-02
Don't know how during an install - use a blacklist post-install, but you probably already know that.
Is all the hardware "supported" by Ubuntu?  I've seen older HP servers DL380, etc. not work ... ever since 10.04.
I don't know what a "710" box is.  Is it a T or an R model?
Can you boot into a liveCD desktop and run lshw to see all the recognized hardware?

[http://www.ubuntu.com/certification/hardware/200910-4539/](http://www.ubuntu.com/certification/hardware/200910-4539/) is for 10.04 for the R710
[http://www.ubuntu.com/certification/hardware/200905-2781/](http://www.ubuntu.com/certification/hardware/200905-2781/) is for 12.04  for the R710, so that should be good news.

Besides that, I got nuthin'.

---

### Post by headers on 2013-10-02
OK, the issue is mostly solved. 

We have IPv6  running in our network and the installer was setting that up and using it.  This happens so fast during the install  sequence that there is no way to hit the cancel button as it flashed past.  When it would reach out later using IPv6 at certain points during the install it would nebulously fail.   I do not  know why the "Cleaning up..." stage failed previously.


FIX:  I used  macbook to hook up to local outside network wifi. I shared the connection out through the ethernet port and the server was hooked up to the ethernet port. This way, a)  IPv6 stuff may just not work the same, different network, b) it worked slow enough for me to hit cancel while it was trying.   After that everything worked normally.   After install I disabled IPv6 on the complete install.

---

