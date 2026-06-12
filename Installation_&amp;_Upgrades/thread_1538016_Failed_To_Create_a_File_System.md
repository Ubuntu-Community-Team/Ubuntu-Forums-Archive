---
title: "Failed To Create a File System"
date: 2010-07-24
forum: Installation &amp; Upgrades
---

### Post by joek71 on 2010-07-24
HI guys

When I am doing a fresh install and it tries to create partition i get this error:

Failed to Create a file system
The ext4 file system creation in partition #6 of Serial ATA Raid nvidia_cjtiagcb(stripe) failed.

How can I fix this.

Thank you

---

### Post by Rubi1200 on 2010-07-24
> **joek71 said:**
> HI guys

When I am doing a fresh install and it tries to create partition i get this error:

Failed to Create a file system
The ext4 file system creation in partition #6 of Serial ATA Raid nvidia_cjtiagcb(stripe) failed.

How can I fix this.

Thank you
Is this a RAID setup?

I have heard there can be problems.

Check this out and see if it brings you further:
[https://wiki.ubuntu.com/ReliableRaid](https://wiki.ubuntu.com/ReliableRaid)
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

I think you may need the Alternate CD.

Hope this helps.

---

### Post by joek71 on 2010-07-24
Yes this is a raid setp 0 on mt dfi expert mobo nvidia motherboard, with nvidia raid

---

### Post by joek71 on 2010-07-24
I had no problem with 9.10 but with 10.4 is a problem, thought 10.4 was improved.

---

### Post by ronparent on 2010-07-24
A problem exists with 10.04 in that gparted won't recognize a raid. I posted a bug report ([https://bugs.launchpad.net/bugs/600729](https://bugs.launchpad.net/bugs/600729)) and received a response that suggested a quick fix. The problem occurs because 10.04 was distributed without a package called kpartx  which is needed by gparted to read a raid. The solution is to open the 10.04 install from a live cd session, use synaptics to install kpartx for the session, and continue on to run a normal installation within the session. You may run into a glitch writing the grub boot loader to the raid but this can be fixed if needed.

---

### Post by CyberCam on 2010-07-24
I had this issue as well... trying to install 10.04 64bit server edition on a brand new server, with nVidia raid 1 (mirror) that has 2 1TB WD SATA HDD's.

After messing around with it for hours, I gave up and installed 9.10. It works like a charm! I just don't have time to mess around with this issue at the moment, this server has to be up and running by Monday!

I'll check back here by the time 10.10 comes out to see if the issue is fixed.

**[COLOR="Red"]UPDATE:[/COLOR]**
I threw caution to the wind and decided to do a dist-upgrade after my fresh install of 9.10 server... the machine is now running 10.04 server as smooth as silk. It takes up a bit more time but it's an easy workaround! At least now I have the nVidia raid 1 working beautifully!

---

### Post by ronparent on 2010-07-25
Unless the developer gets around to it, the situation still exists on 10.10 Alpha 2.

---

