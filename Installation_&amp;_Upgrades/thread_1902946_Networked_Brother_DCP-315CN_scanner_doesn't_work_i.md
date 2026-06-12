---
title: "Networked Brother DCP-315CN scanner doesn't work in Oneiric"
date: 2012-01-01
forum: Installation &amp; Upgrades
---

### Post by Eksilius on 2012-01-01
I have a networked Brother DCP-315CN printer/scanner that I've been using with Ubuntu since version 7.10. Each new version has required its own tricks but so far, I've always been able to make the machine work - until now with v11.10.

Printing is no problem and has just become easier with the years, not even requiring drivers from the Brother web pages but the scanning function now leaves me without a clue as to what to do. I've downloaded and installed brscan2 (which hasn't been updated by Brother since 2009) and other related drivers just as with earlier Ubuntu versions. I have also applied the tip about copying a number of files from /usr/lib64 to /usr/lib but to no use.

brsaneconfig 2 -q tells me that I've correctly configured and registered the scanner, and dpkg -l tells me that the drivers are installed but still, no scanner application detects it.

scanimage -L, scanimage -T, sane-find-scanner, and brsaneconfig2 -d all state that there is no scanner device connected, which I find very strange since the two computers in the house still running v11.04 see the scanner, and I can anyway print on the device even from Oneiric.

Any piece of advice that can put me on a forward-moving track would be extremely warmly appreciated.

---

### Post by dandnsmith on 2012-01-01
Networked - is that 'having own IP address and built-in server' or 'attached to another PC on the network'?

---

### Post by Eksilius on 2012-01-01
Derek.

It's on my LAN having its own static IP adress. It's not attached to any other computer but directly to the router via an Ethernet cable.

---

### Post by dandnsmith on 2012-01-02
That clarifies the matters for me, and suggests that some of the oddities and the ways round you found may have a bearing on your problem.
My personal opinion is that the problem will be found in the OS and dependent software and its interaction with things like the sane version software and the scanner built-in software.

I'm afraid that I've never managed to resolve my scanner over-the-local-network problems some years ago, so I don't have a good base to get you further

---

### Post by Eksilius on 2012-01-03
I tried to connect the DCP-315CN directly to the computer via USB and now, sane-find-scanner detects it. However, scanimage -Q still doesn't, and Simple Scan can't find any device either.

---

### Post by Eksilius on 2012-01-10
I've been playing around with VirtualBox on two different computers, testing both 32-bit and 64-bit versions of Ubuntu. So far, the conclusion is that this problem is specific to the 64-bit version of 11.10. 32-bit or earlier versions of Ubuntu work fine with the scanner.

As to the reason for the problem, I'm no wiser, however.

---

### Post by kurt18947 on 2012-01-10
Is this relevant to your Brother scanner problem?  This appears to be an Ubuntu 11.10 problem,  there was someone with another brand scanner with the same problem and the same fix.

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101)

---

### Post by Eksilius on 2012-01-11
That's the thing: I've followed that tip already but it still doesn't work. I haven't been able to find any other tips, neither on the Brother web pages nor elsewhere. But I'll keep looking. Does anybody know any other forums where it might be worthwhile throwing out the question?

---

### Post by Eksilius on 2012-01-30
More playing with VirtualBox. Scanning works with 64-bit Fedora 16 (recent kernel) and Debian 6 (old kernel), but so far not with Ubuntu-based Mint 12. So the problem seems to be kind of ubuntuish up to now. Going to try OPENSuse as well.

---

### Post by lkraemer on 2012-01-31
Eksilius,
Check out the info at:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10)
to see if the Ubuntu 11.10 or Debian 6 or Debian 5 information will get it working.

lk

---

### Post by Eksilius on 2012-01-31
Thanks a lot for the tip lkraemer. I've already tested all the Ubuntu-related tips on the Brother website but I'll check if the Debian workarounds are of any use and get back.

Does anybody have any idea if the default firewall/iptables settings have changed with v11.10?

---

### Post by Eksilius on 2012-03-08
It finally works!

I evidently made a mistake when first following the tip on the Brother web pages copying a number of library files from /usr/lib64 to /usr/lib. I discovered this by accident when playing with the Ubuntu 12.04 beta 1 in a VM. Since that version is an LTS, I now know that Ubuntu will support scanning with my DCP-315CN for longer than the hardware is likely to last... :popcorn:

---

