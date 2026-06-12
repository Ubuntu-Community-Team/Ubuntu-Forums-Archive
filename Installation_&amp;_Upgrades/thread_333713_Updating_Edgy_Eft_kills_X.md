---
title: "Updating Edgy Eft kills X"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by greatgoo on 2007-01-07
I downloaded the iso for Edgy Eft and burned a live install CD.  I installed this on an old no name clone with Intel chips and a ATI video card.  All went well untill I updated the system.  One of the 90 updates crashed Xwindows.  I was able to reconfigure to a vesa driver and get it back up, but the respose was slow.

I wiped and reinstalled, did it all again and crashed windows again.  Then I put in a bug report.  

[https://launchpad.net/ubuntu/+bug/78100](https://launchpad.net/ubuntu/+bug/78100)

And as 17 other things have been going on I have been rebuilding and crashing the system.  I have it down to the following files being the suspects.

linux-headers-2.6.17-10
linux-headers-2.6.17-10-generic
linux-image-2.6.17-10-generic
linux-restricted-modules-2.6.17-10-generic
linux-restricted-modules-common

Can anyone give me some input on which of them may be the problem?  I noticed another thread where an upgrade to Edgy failed and the user had to kill the xwindows server to get the upgrade to work.  Might these be better loaded from the command line?

The video card in question is ..  from xorg.conf

Section "Device"
 Identifier "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
 Driver "ati"
 BusID "PCI:1:0:0"
EndSection

Section "Monitor"
 Identifier "DELL 1501FP"
 Option "DPMS"
EndSection

David Davis
Toledo, OR 97391

---

### Post by hal10000 on 2007-01-08
> Section "Device"
Identifier "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
Driver "ati"
BusID "PCI:1:0:0"
EndSection

If you installed the linux-restricted-modules-2.6.17-10-generic package, then your Driver for ATI graphic cards is "fglrx". So you should change the Driver entry in your xorg.conf from
```

Driver "ati"

to

Driver "fglrx"

```
Do this with [COLOR="Red"]sudo gedit /etc/X11/xorg.conf[/COLOR] (or any other editor you like)
The fglrx driver offers you 3D hardware acceleration for your graphic card if it works.

---

### Post by greatgoo on 2007-01-08
> **hal10000 said:**
> If you installed the linux-restricted-modules-2.6.17-10-generic package, then your Driver for ATI graphic cards is "fglrx". So you should change the Driver entry in your xorg.conf from
```

Driver "ati"

to

Driver "fglrx"

```
Do this with [COLOR="Red"]sudo gedit /etc/X11/xorg.conf[/COLOR] (or any other editor you like)
The fglrx driver offers you 3D hardware acceleration for your graphic card if it works.

Nope.  Crashed the X server it did.  I am up with the vesa driver and have seen the various threads on the fglrx issue.  I will research those and look for the fix.

David Davis
Toledo, OR 97391

---

