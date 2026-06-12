---
title: "issue with old bios"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by bachurch on 2008-10-10
Hi,
i am trying to install ubuntu-8.04.1-server-i386.iso onto an old dell P2 400 Mhz machine. When the cd spins up I get:

[0.000000] acpi: bios age (1999)fails cutoff (2000)
acpi force is required to enable acpi

After a minute i get an error 16 and then the cd boots.
I run through the setup until it gets to the HD detect and it cannot find the HD. I have tried multiple drives including a winME that was in the machine and works.

Do I have to update the bios or can I work around it?

I'm a newbie but I'm trying.

Thanks

---

### Post by cariboo on 2008-10-10
I've install the server and several other distributions on older computers. Usually when the computer can't detect the hard drive it is either due to a cable or jumper problem. Make sure the drive is detected in the bios. Most bios of that age will autodetect the hard drive.

Just as an example I currently have Ubuntu server installed on a 400Mhz eMachine, Dragonfly BSD on a Compaq 350Mhz and DSL on an AST P75.

Jim

---

### Post by bachurch on 2008-10-10
Thanks Jim,
The bios does see the drive (the several I have tried).
Is the error #16 significant?

I agree with the jumper/cable issues. I've see plenty of those.

Brian

---

### Post by louieb on 2008-10-10
> **bachurch said:**
> Hi, I get:
[0.000000] acpi: bios age (1999)fails cutoff (2000)
acpi force is required to enable acpi

whitebox P2-400, 384MB ram. (built in 1997)  Message is normal when Ubuntu starts up. Guess it just some type information message. 

I had to flash the BIOS to get it to use a drive larger that 30GB. But for my board the newest BIOS available was dated 1999. So I still get it. Other that I have to press the power button after shutdown,  to get it to turn off. Does not seem to have any other problems.     

The installer not seeing the drive is odd. I guess you've already checked the jumpers and cable. Might check BIOS and see if the drive detect is set to **auto** and the mode is set to **LBA**. 

Sorry but don't know if the error #16 is significant. Can't recall  seeing it.

---

### Post by bachurch on 2008-10-12
I solved my issue. I had the hd as master on the primary ide and the cd as master on the secondary ide. I made the cd slave on the primary and it found the hd.

Thanks for the help.

Brian

---

