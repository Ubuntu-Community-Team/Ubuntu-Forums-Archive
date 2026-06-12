---
title: "raid configuration in ubunut 12.04 lts"
date: 2012-09-29
forum: Installation &amp; Upgrades
---

### Post by kkannan on 2012-09-29
Dear all,

i am trying to install ubuntu 12.04 server in intel server.
but its not detecting the raid controller .
Raid controller is intel embedded raid 11 technology. that is LSI 1064e card.
Can u send the driver for this raid card.

pls help me to proceed further.

With thanks&regards,

Kannan.k

---

### Post by darkod on 2012-09-29
If by embedded you mean onboard (not a dedicated raid controller), you are better off using ubuntu software raid, it will work better than onboard raid.

If possible disable raid in BIOS and set the sata mode to AHCI, or enter the raid configuration and find an option to show the disks as single disks.

After that start the ubuntu server installer, use the manual partitioning and configure software raid.

Alternatively, if you want to use the card visit the Intel website to get the correct driver. I am not sure it's an Intel card since you mention LSI and that is a separate company making raid cards which has nothing to do with Intel. They have their own website [www.lsi.com](www.lsi.com) and there you can find drivers if needed.

---

### Post by kkannan on 2012-12-04
Dear Mr.Darkod,

In intel motherboard, ther are using LSI controller for raid functionality . i searched both intel and LSi website but i cant get the driver for that.

i search the lsi website they gave drivers for RHEL 5&6 , solaris 10 & windows os's .then how do i take for ubuntu pls help me to proceed further

may i know how to configure raid in the time of ubuntu installation . can u send the procedure for that .

With thanks&regards,

kannan.k

---

