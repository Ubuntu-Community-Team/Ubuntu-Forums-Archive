---
title: "Startup hangs after fresh install of 11.04"
date: 2011-06-18
forum: Installation &amp; Upgrades
---

### Post by grw on 2011-06-18
Hi,

I have a brand new laptop, a Thinkpad E420 - Core i5 processor, 500GB harddrive, 4GB RAM

My problem: The computer hangs when I try to start it up. I just get a dark screen and nothing works. I have installed Ubuntu 11.04 (64 bit) several times, varying settings here and there. No luck. Once I managed to boot normally. Sometimes I have been able to boot using recovery mode (like now), but mostly recovery mode hangs too.

I tried a few things from this thread: [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535) 
But nothing worked and I don't know if I have the same problem.

Can anyone help?

I manually partitioned the harddrive: 
/boot (500MB) (I have since reinstalled things without the boot partition)
/swap (8GB)
/    (20GB)
/home - (rest of drive but with 20GB of unused space at the end. I was hoping to install a couple of different linux distros (not a Windows/linux dual boot)

Gwyn

---

### Post by MAFoElffen on 2011-06-18
> **grw said:**
> Hi,

I have a brand new laptop, a Thinkpad E420 - Core i5 processor, 500GB harddrive, 4GB RAM

My problem: The computer hangs when I try to start it up. I just get a dark screen and nothing works. I have installed Ubuntu 11.04 (64 bit) several times, varying settings here and there. No luck. Once I managed to boot normally. Sometimes I have been able to boot using recovery mode (like now), but mostly recovery mode hangs too.

I tried a few things from this thread: [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535) 
But nothing worked and I don't know if I have the same problem.

Can anyone help?

I manually partitioned the harddrive: 
/boot (500MB) (I have since reinstalled things without the boot partition)
/swap (8GB)
/    (20GB)
/home - (rest of drive but with 20GB of unused space at the end. I was hoping to install a couple of different linux distros (not a Windows/linux dual boot)

Gwyn
I'm thinking that since you visited my sticky... that you already have some info about your system.

Intel® HD graphics 3000... which had more of a problem in 10.10 than in 11.04 (newer/updated kernel and video driver support).  Please post the output of:
```

lspci -vv | grep VGA

```

---

### Post by grw on 2011-06-18
Here you go:

gwyn@gwyn-ThinkPad-E420:~$ lspci -vv | grep VGA
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
01:00.0 VGA compatible controller: ATI Technologies Inc NI Whistler [AMD Radeon HD 6600M Series] (prog-if 00 [VGA controller])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-

---

### Post by grw on 2011-06-20
bump

---

### Post by grw on 2011-06-22
Can anyone help me with this?

Over the last couple of days, I have been able to start my computer in recovery mode after trying 3 or 4 times (it hangs on start up 3 times then boots). Then I thought I'd solved my problem. I edited /etc/default/grub , uncommenting gfxmode=680x480. The computer started normally. (I then tried to get the wireless going....)

Finally, I shut down and tried to restart. The computer wouldn't boot at all. Not even in recovery mode. I gave up after 7 or 8 attempts. I am using a Knoppix live cd to write this...


gwyn

---

### Post by dino99 on 2011-06-22
how it might be installed:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

then google a little about: ubuntu+yourlaptopmodel

---

### Post by grw on 2011-06-22
When I try to startup in recovery mode, the computer often hangs at this line:

eth0: no IPv6 routers present

Or at this line:

type=1400 ..... apparmor="STATUS" operation="profile_load" name="usr/sbin/cupsd" pid=781 comm="apparmor_parser"

(copied out by hand)

Does that mean anything?

---

### Post by marquivon on 2011-07-19
Were you able to figure our a resolution to this?

---

### Post by steve11911 on 2011-07-19
You should be able to get a good install.

I'd start here:

[http://www.ubuntu.com/certification/hardware/201103-7440](http://www.ubuntu.com/certification/hardware/201103-7440)

---

