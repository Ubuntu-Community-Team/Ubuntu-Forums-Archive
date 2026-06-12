---
title: "Another dual boot post"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by elightbo on 2007-06-26
I have a Vista 32-bit Home Premium OEM upgrade that I installed using a clean install from Windows MCE.  I have a SATA RAID 0 setup with vista on partition 2, and I would like Ubuntu to be on partition 1.  This is an intel controller (975x chipset).  I used the Ubuntu 7.04 live CD, and started up GParted, but it does not recognize my Windows partition.   Both sda and sdb show "unallocated".  Is this a problem with Ubuntu not having the proper drivers for the RAID controller?   I don't want to risk installing Ubuntu on partition 2 and have it ruin my MBR for Vista, so i thought I would post.

I hope that this hasn't been address already, but I've googled for a while and can't seem to find an answer.   Thanks for the help in advance.

---

### Post by elightbo on 2007-06-26
I should probably add that it is the 64-bit 7.04 version.

---

### Post by Pumalite on 2007-06-26
Check this:

[http://ubuntuforums.org/showthread.php?t=473962&page=2](http://ubuntuforums.org/showthread.php?t=473962&page=2)

---

### Post by elightbo on 2007-06-26
I read the link, and will be following the instructions on there.  Thank you.  I'm still not really sure why Ubuntu didn't recognize Vista on the other partition.   How do I know which drive to install Ubuntu on since they are both the same size, and both are unrecognized?  When in Windows, E is the open drive, and F contains Vista..

---

### Post by Pumalite on 2007-06-26
Look; first of all I would get rid of Raid arrays if you want to run Ubuntu. Raid 0: minimal performance improvement. You probably have a FakeRaid, that is, software Raid. It can be disabled in BIOS. I tried 12 times to install 7.04 in a C2Duo. D975XBX, XFXNVIDIAGeForce 7800GT Raid 0 about a month ago. I gave up. It's better to work with independent drives and give Ubuntu an entire drive. Your chances of success are much better.

---

### Post by elightbo on 2007-06-28
I did get Ubuntu dual-booting with Vista successfully.  The problem was that I was using a "fake-raid" and Ubuntu doesn't recognize this through the installation manager.  It sees them as individual drives.  But, after much googling, I found a solution, and followed the excellent instructions here:
[https://help.ubuntu.com/community/FakeRaidHowto#head-7918ab0def192cdf40484077136a40241732c669](https://help.ubuntu.com/community/FakeRaidHowto#head-7918ab0def192cdf40484077136a40241732c669)

I do have some problems with the install, but I thought it would be best to post those in a different topic:
[http://ubuntuforums.org/showthread.php?t=486625](http://ubuntuforums.org/showthread.php?t=486625)

~eirc

---

### Post by Pumalite on 2007-06-28
Glad you made it work. I appreciate the link too.

---

