---
title: "Dell Power Edge Problems SAS 6iR Raid"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by pvs4 on 2008-01-11
We just purchased a Dell Power Edge 2950 with dual quad core xeon processors.  Also included with the server is a SAS 6iR or SAS 6/iR intergrated RAID controller.  Running RAID I with two SATA 250 Gb drives.

Dell does indeed have a Linux driver for this RAID card for Red Hat 5 Enterprise and this driver is avaliable on Dell's support web site.

Is there anyone else out there that is running Ubuntu on a box using SAS 6iR RAID controller,

or

does anyone know of any drivers that will work with Ubuntu?

Thank you

Kobie

---

### Post by slyi on 2008-01-14
Any luck with this Kobie? We have a similar problem on exact same system.. 

thanks

Levent

---

### Post by ceagan on 2008-01-21
Have you guys tried the 6.06.2 LTS release? I saw it announced today and it is supposed to fix this issue. [http://www.ubuntu.com/news/lts-6.06.2](http://www.ubuntu.com/news/lts-6.06.2)

---

### Post by pvs4 on 2008-01-23
Howdy all:

Update - no solution as of yet.

I will be downloading the Ubuntu 6.06.2 LTS Server and attempting to load this OS on my server.  I will let everyone know.

One thing that did happen was I tried to load Ubuntu 7.10 and I tried to use the megaraid drivers and it locked up the machine and I lost the CD Rom, I had to pull the CMOS jumpers and reset the CMOS to get the CD Rom back.

Will keep everyone informed.

The SAS 6/ir card is made by LSI and I can tell you that as long as this is a DELL card LSI is not going to provide any support except directly to DELL.  LSI will also not tell me what card in their current line is the same card as the SAS 6/ir - they say they are under contract with DELL and cannot provide any information.

We shall see about Ubuntu 6.06 LTS

Kobie

---

### Post by tgalati4 on 2008-01-23
How much for this server?

---

### Post by ceagan on 2008-01-23
I configured a PowerEdge 1950 III to be $1,995.67 after $857.33 Dell Small Business 30% off. You can save some money by going to a different PowerEdge version, but it comes at the expense of upgradability. This server has an extra processor slot for a second quad-core and 4 more memory slots.

Processor: Quad Core Intel® Xeon® E5410, 2x6MB Cache, 2.33GHz, 1333MHz FSB
Memory: 4GB 667MHz (4x1GB), Dual Ranked DIMMs
Hard Drives: 2 250GB 7.2K RPM Serial ATA 3Gbps 3.5-in HotPlug Hard Drives
RAID Controller: PERC6i SAS RAID Controller, 2x4 Connectors, Int, PCIe, 256MB Cache

---

### Post by neemers on 2008-01-24
> **pvs4 said:**
> Howdy all:

Update - no solution as of yet.

I will be downloading the Ubuntu 6.06.2 LTS Server and attempting to load this OS on my server.  I will let everyone know.

One thing that did happen was I tried to load Ubuntu 7.10 and I tried to use the megaraid drivers and it locked up the machine and I lost the CD Rom, I had to pull the CMOS jumpers and reset the CMOS to get the CD Rom back.

Will keep everyone informed.

The SAS 6/ir card is made by LSI and I can tell you that as long as this is a DELL card LSI is not going to provide any support except directly to DELL.  LSI will also not tell me what card in their current line is the same card as the SAS 6/ir - they say they are under contract with DELL and cannot provide any information.

We shall see about Ubuntu 6.06 LTS

Kobie

Did you get 6.06.2 installed on your Dell?  I was not able to....

I just got a PowerEdge 1950 with this SAS controller in it and had the same problem when installing Ubuntu 7.10.  During the install it said I had no drives to install Ubuntu on.  So I tried to install 6.06.2 and it hangs at loading Kernel screen and never actually brings me to the installer.  So I tried 7.04 and what do you know it installed just fine.  Everything is running fine.  I also did a distro-update to 7.10 and what do you know, fails to find drives and craps out when I try to load that Kernel.  So I'm telling it to load the 7.04 Kernel now.....  What a headache.......  I would love to get 6.06.2 running because this is going to be a production mail server......

---

### Post by neemers on 2008-01-25
Kobie,

Were you able to get Ubuntu 6.06.2 to install on your systems?  My boss bought 2 more of these systems with the SAS cards in them, so I have 3 servers with no OS that I wish I could load Ubuntu 6.06 on!

Thank you!
-Arron

---

### Post by neemers on 2008-01-29
BUMP!  Any ideas of what I can do to get 6.06.2 LTS to load?????  I thought 6.06 was supported? :)

---

### Post by pvs4 on 2008-02-19
Status update, we have not found a ubuntu solution to this problem.
CentOS loads up just fine and works great.

We are maintaining a test bed with the SAS 6iR Raid card and still testing Ubuntu - hopefully we will find a solution soon.

Take care

Kobie

---

### Post by frost on 2008-03-06
> **pvs4 said:**
> Status update, we have not found a ubuntu solution to this problem.
CentOS loads up just fine and works great.

We are maintaining a test bed with the SAS 6iR Raid card and still testing Ubuntu - hopefully we will find a solution soon.

Take care

Kobie

I think this patch can help: [http://bugzilla.kernel.org/show_bug.cgi?id=9909](http://bugzilla.kernel.org/show_bug.cgi?id=9909)


Best regards

---

### Post by meese7en on 2008-04-27
I have R200 with SAS 6iR on it, and I successfully installed Hardy 8.04. Does it mean ubuntu recognize this raid card ? How can I configure it ? 
I'm new with the raid thing.

---

