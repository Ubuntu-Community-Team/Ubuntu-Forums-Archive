---
title: "Acer Aspire 5920g dual boot Vista/Hardy"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by Matt_300tdi90 on 2008-08-26
Hi this is my first post here but have been using ubuntu and this forum for help for a while.

I have just ordered an Acer Aspire 5920g laptop which comes pre-installed with Vista and i want to dual boot it with Vista and Hardy. From the information i can find online, the hdd comes with 4 partitions, the main Vista install drive, a Data drive, a Recovery drive and an Acer Arcade drive. I would like to keep the last two partitions as they are. 

What would be the best way of going about this without screwing up the Vista install?

Delete the Data partition to make way for the Ubuntu partitions?

Resize the Vista partition to make space for the ubuntu partitions, leaving the data partition as it is?

Or another method?

Also I have an external drive that i will be using for backups with the laptop that is currently empty, it is 250Gb the same as the hdd in the laptop. I was thinking of making a clone of the laptop hdd first in case anything goes wrong. Would Clonezilla be good software to make the clone and would it successfully restore the original drive if something goes wrong? Is there better freeware software to do this job?

Why can't the manufacturers just give us a OEM OS cd and key! :mad: It would make everything so much easier. 

Sorry for all the questions!

Cheers

Matt

---

### Post by Pumalite on 2008-08-26
Clonezilla is fine. So is partimage. Shrink Vista's partition with Vista's partitioner allocating free space for Ubuntu. I think you should use the Alternate CD and partition  Manually.

---

### Post by reg4c on 2008-10-06
AH, unfortunately you cannot resize the Vista partition
I have the same laptop and have tried a bunch of programs to resize it but still does not work

If you do manage to make the vista partition smaller please explain so that I can do it also...
Cheers

---

### Post by Pumalite on 2008-10-06
Try disabling PageFile

---

