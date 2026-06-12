---
title: "Ubuntu 64 bit hangs on install, only see splash screen"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by krohn on 2010-10-08
I can not get ubuntu to install on my workstation.  I have the 64-bit cd (am currently trying the 32-bit cd with similar results) and it won't install.  I get to the ubuntu splash screen with the 5 dots underneath it and it looks like it's trying to run for several minutes.  After the several minutes, the screen simply goes black and I can't do anything.  Any advice?  Thanks in advance.

---

### Post by Rubi1200 on 2010-10-08
Which version are you trying to install and what graphics card do you have?

---

### Post by krohn on 2010-10-08
> **Rubi1200 said:**
> Which version are you trying to install and what graphics card do you have?

I am trying to install the newest Ubuntu desktop 64-bit edition, 10.04.  My video card is an ATI Firepro v3800.

Interestingly, when I use wubi to install ubuntu, it works fine and I have no problems.  However, I don't want to go this route and would rather have linux installed without windows.

---

### Post by Rubi1200 on 2010-10-08
Well, I cannot imagine the video card being the source of the problem.

Did you burn at the lowest possible speed? Perhaps also try another fresh CD.

Do you have, or once have, a RAID setup?

---

### Post by krohn on 2010-10-08
> **Rubi1200 said:**
> Well, I cannot imagine the video card being the source of the problem.

Did you burn at the lowest possible speed? Perhaps also try another fresh CD.

Do you have, or once have, a RAID setup?

Just burned another fresh CD at the lowest speed and it still gives me the same problem.  Also ran the checksum to be sure the ISO was downloaded correctly.  

I've never had a RAID setup on this machine.

---

### Post by krohn on 2010-10-08
> **krohn said:**
> Just burned another fresh CD at the lowest speed and it still gives me the same problem.  Also ran the checksum to be sure the ISO was downloaded correctly.  

I've never had a RAID setup on this machine.

Forgot about this attempt.  I once installed Ubuntu Server 10.04 64-bit and it installed just fine.  When I tried to install "ubuntu-desktop", it crashed on reboot.

---

### Post by Rubi1200 on 2010-10-08
Ok, so let's try this anyway.

Pop in the CD and start things. When you see the little stick figure press Enter to select live mode and language and then immediately after that press F6 followed by Esc.

What you should see is this:

> **file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**Move the cursor backwards and remove quiet splash and type in xforcevesa. The line will then look like this:

> **file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz xforcevesa --**Then press Enter to boot and let's see if it works.

You may also want to look here:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

---

### Post by krohn on 2010-10-08
> **Rubi1200 said:**
> Ok, so let's try this anyway.

Pop in the CD and start things. When you see the little stick figure press Enter to select live mode and language and then immediately after that press F6 followed by Esc.

What you should see is this:

Move the cursor backwards and remove quiet splash and type in xforcevesa. The line will then look like this:

Then press Enter to boot and let's see if it works.

You may also want to look here:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

Gave it a try, it was working on things and eventually gave a green screen for a while and then a black screen.  I'll check out those links and see if any of them work for me.

---

### Post by Rubi1200 on 2010-10-08
The only other thing I can suggest is to either try 9.10 or wait just a little longer until 10.10 comes out and see if the issues are resolved with a new kernel.

Good luck!

---

