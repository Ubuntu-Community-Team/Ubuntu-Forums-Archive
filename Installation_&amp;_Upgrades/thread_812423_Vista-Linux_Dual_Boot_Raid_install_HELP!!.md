---
title: "Vista-Linux Dual Boot Raid install HELP!!"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by Trade on 2008-05-29
this is the first time I'm installing ubuntu.   I've always used windows and I'm accustom to installing drivers etc.

I'm currently running a 32bit vista install on an asus mobo.  It is configured in a Raid 0 array with two 250G hitachi HDD.  The array uses the onboad nvidia raid device/controller.

I would like to make a smaller partition say 100G for Ubuntu 8.04.  I however need to as mentioned run this in a raid 0 array.  Now my problem is I have found info on installing using a raid 0 linix software/raid, and info on setting up a dual boot.

Now here is where the help comes in.  Can somebody point me to a very noobified-detailed step by step guide to help me get this install done.  As stated I'm very very new to working in linux and I'm struggling here.  I keep seeing alot of command line code for the raid install and that is where I get lost.  Again I'm just learing this OS.

Thnx

---

### Post by tritonofg on 2008-05-30
Try looking at the FAKE RAID howto.
Search FAKE RAID howto in Ubuntu search.

Most Mobo's that claim they have onboard RAID actually have fake raid (hardware + driver needed to work in windows or other OS).

I know that you will need DMRAID

BEWARE!!!!!! Instructions require use of Terminal (Command Line).
Back up your data and give it a whirl....BTW I run a RAID o w/ winxp and have not yet been able to install AND boot to Ubuntu in RAID 0.

BTW...if you mess up something pop in the vista os cd and go to recovery console...
then run "FIXMBR" to get back into windoes should your MBR be altered to the point where you cannot boot vista.

---

