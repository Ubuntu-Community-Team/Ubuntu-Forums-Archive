---
title: "[SOLVED] problem with cd drive during installation"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by greifla on 2008-07-18
Hello,
i try to install the latest xubuntu-version.
Installation freeze after step hw-detection an cd searching.
In syslog I found messages, that there are errors reading from cd.
I wonder, there are messages as: 'Attached scsi CD-Rom sr0', because I have no SCSI-Controler. CD drive is ATAPI (IDE1 Master).
The Mainboard is ASROCK P4I45PE.

---

### Post by Pumalite on 2008-07-18
Burn a new CD and try again.
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by alfalfa31 on 2008-07-18
> **greifla said:**
> 
I wonder, there are messages as: 'Attached scsi CD-Rom sr0', because I have no SCSI-Controler. CD drive is ATAPI (IDE1 Master).
The Mainboard is ASROCK P4I45PE.

Don't worry about the sr0 thing, as the system is going to assign just about everything block a SCSI dev name.

Is there a slave on that channel?  If so, is it a hard drive?

If not, check to see if the drive is set to "Cable Select" or "Master."

Whichever it is, change it to the opposite and try again.

---

### Post by greifla on 2008-07-18
I have tried it with the Desktop Edition and with the alternate Version. The error is the same.

---

### Post by Pumalite on 2008-07-18
What are the options you have in BIOS for CD Drive?

---

### Post by greifla on 2008-07-18
> **alfalfa31 said:**
> Don't worry about the sr0 thing, as the system is going to assign just about everything block a SCSI dev name.

Is there a slave on that channel?  If so, is it a hard drive?

If not, check to see if the drive is set to "Cable Select" or "Master."

Whichever it is, change it to the opposite and try again.
There are two devices in my PC. HD at IDE0 Master. DVD at IDE1 Master. Both Slaves are not connected.
I have switched DVD Device from Master to Cable Select, but its the same error.

---

### Post by nrdlevans on 2008-07-18
While I do not believe this is your problem, I have found that burning at slower rates sometimes helps "bad media" burn properly.  

This is partially why I like buying a pre-burned media when I switch OS's

---

### Post by greifla on 2008-07-18
> **Pumalite said:**
> What are the options you have in BIOS for CD Drive?
I found no special options for CD in BIOS.
...
Secondary IDE Master: DVD-RW
Boot Priority: 1. CD/DVD
...
The device is LG GSA-4167B

---

### Post by Pumalite on 2008-07-18
Did you burn a new CD as per suggestions?

---

### Post by greifla on 2008-07-18
...yes, I did burn a cd with lower speed. But without success.

---

### Post by greifla on 2008-07-18
How is it possible to deactivate DMA ?

---

### Post by alfalfa31 on 2008-07-18
OK...  

I'd suggest breaking down the hardware you have.  We already know the optical drive, what about the motherboard?

You also say that there are "errors" without specifying what they are.  Can you give as close to full text on the errors as possible?

---

### Post by greifla on 2008-07-19
Here is a part of syslog as attachment...

---

### Post by greifla on 2008-07-19
The problem is fixed.
I connected CD drive from IDE1 Master to IDE0 Slave.
Now it works.

Many, many thanks for your help!

---

