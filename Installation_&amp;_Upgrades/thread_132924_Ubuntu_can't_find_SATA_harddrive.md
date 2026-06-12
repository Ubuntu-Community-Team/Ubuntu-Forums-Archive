---
title: "Ubuntu can't find SATA harddrive"
date: 2006-02-19
forum: Installation &amp; Upgrades
---

### Post by Seaman on 2006-02-19
Straight on; I'm trying to install Ubuntu-server (5.10) on my computer, however, when I come to the partioning part I can't see any of my partions (or free un-formatted space). When I later try the Ubuntu LiveCD (5.10) there isn't any SATA-drive in /dev. But I could see my SATA-drive in the Debian partion manager, unfortunately the partion manager could only "see" the first 137 GB of my 200 GB harddrive.

So, what to do? Did I maybe something wrong when I built the computer? All help is really appreciated. I'm tired of using a LiveCD for my brand new computer...

---

### Post by Seaman on 2006-02-21
Okey, it seeems like 5.10's support for SATA is quite bad. Installing Dapper Drake 6.04 Flight 4 instead got me on track, no problems with the SATA there.

---

### Post by Seaman on 2006-02-24
After four days of testing I must say that Dapper Drake Flight 4 contains lot of bugs. Before I even got an installed system I was quite familiar with several of them. However, I didn't except anything else.

Right now this is my main OS. Of course Dapper shouldn't be used for this, but I lack of alternatives. Is there any possibility that I can run stable version of Ubuntu with my SATA harddrive?;

*Seagate 200GB SATA Barracuda 7200.9 (8MB Cache / Sata)*

If not, can anyone give me the name of any other _stable_ distro with good support for SATA harddrives?

---

### Post by LordBug on 2006-02-24
1) Dapper is in beta, so expect bugs :)

2) I've found Ubuntu SATA support to work wonderfully.  I have 3 SATA drives (36GB Raptor, 2x300GB Maxtors) and they all work without issue.

3) 136GB limit is, I believe, a BIOS issue.

We might be able to help figure out the issue if we knew exact hardware specs for your system.

---

### Post by Seaman on 2006-02-24
[QUOTE=LordBug]1) Dapper is in beta, so expect bugs :)

2) I've found Ubuntu SATA support to work wonderfully.  I have 3 SATA drives (36GB Raptor, 2x300GB Maxtors) and they all work without issue.

3) 136GB limit is, I believe, a BIOS issue.

We might be able to help figure out the issue if we knew exact hardware specs for your system.[/QUOTE]
1. Yeah, I told you that I expected bugs, no shame at all on the developers.

2. Okey, that's good. Which kernel do you have? How old are your SATA-harddrives? I need some nasty data.

3. BIOS issue or not, I didn't have that particular issue. The breezy installer couldn't se my SATA-harddrive at all.

Motherboard is: *Asus - Socket 939 - ATX SiS756/965l (A8S-X) - AMD / PCI-E / Gblan (Serial ATA, RAID i0,l RAID1, and JBOD)*
Harddrive: *Seagate 200GB SATA Barracuda 7200.9 (8MB Cache / Sata) (Serial ATA-300)*

---

