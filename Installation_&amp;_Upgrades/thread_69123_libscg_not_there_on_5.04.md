---
title: "libscg not there on 5.04?"
date: 2005-09-25
forum: Installation &amp; Upgrades
---

### Post by Hanspi on 2005-09-25
Dear forummers,

I installed Ubuntu 5.04 on my machine, and it doesn't seem to have libscg on it.  When I do cdrecord -scanbus, I get "Cannot open '/dev/pg*'. Cannot open SCSI driver.".

Using Knoppix 3.9, everything worked and I got a frustrating "Using libscg version 'ubuntu-0.8ubuntu1'."  I don't find this in the Synaptic Package Manager  ](*,) 

Can anyone point me towards a solution, or tell me how to get this package?

I'm running Linux humphrey 2.6.10-5-386 #1 Thu Sep 8 06:18:41 UTC 2005 i686 GNU/Linux

Slainte!
Hanspi

---

### Post by Hanspi on 2005-10-01
Finally found the solution with the help of a friend.

It seems that plugging a USB CD-Writer in requires a "modprobe sg".  This is not automatic by default.

---

