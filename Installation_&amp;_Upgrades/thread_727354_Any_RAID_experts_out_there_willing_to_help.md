---
title: "Any RAID experts out there willing to help?"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by SighKick on 2008-03-17
I have had **RAID 1** running fine on a Win2K3 Server [**ASUS P4C800** with **Promise PDC20378** controller chipset and **MBFastTrak378 BIOS** & Fastbuild Utility and software drivers].

My problem is trying to install a **minimal linux OS** and configure this OS to use the **2 x SATA 120Gb drives in RAID 1** configuration.  The minimal OS will be used to host **VMware Server**.  I have already managed to create a VMware Server using Debian Etch and have only just discovered **Ubuntu JeOS** which is just the ticket [this current VMware server does not use RAID and it needs to be replaced by this more fault tolerant RAID 1 server].

Is there anyone who is prepared to give **BASIC** instructions to assist me getting **RAID 1** set up on this ASUS Powered Server [P4 3.0Ghz with 4Gb RAM]?

I have found a couple of guides to help me with my quest but they may as well be written in a foreign language [one is a Japanese guy whose command of the English language makes it even harder to try and follow].  In any event, these two guides talk about configuring the Kernel & compiling and **dmraid** and **fakeraid** and it's hard to extract the bits that are relevant to my situation.

Is there anyone who is prepared to **write a tutorial** to do this using **Ubuntu JeOS** please?  I understand that I need Software RAID and it must be possible to do this without booting to a PATA [IDE] drive first as was one suggestion that I didn't fully understand.

---

