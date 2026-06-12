---
title: "[SOLVED] Ubuntu 8.04.1 install problem on HP 6715s"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by use_R on 2008-07-24
A problem occurs when trying to install Ubuntu 8.04.1 (version:ubuntu-8.04.1-desktop-amd64.iso) on notebook HP Compaq 6715s - in the phase of partitioning screen turns to black and notebook stops to respond. The same happens with alternate CD install (version:ubuntu-8.04.1-alternate-amd64.iso) too.

Does anybody know solution? Tnx, use_R.

---

### Post by use_R on 2008-07-26
I solved a problem of installing above mentioned version (ubuntu-8.04.1-desktop-amd64.iso) by selecting the following issues:
noapic
nolapic
acpi=off
on the installation start (two times pressed F6, then selecet noapic, nolapic, acpi=off, then esc, then select "Install Ubuntu").

But, now there is a prbolem on boot-won't boot.

Has anybody a tip? Tnx.

---

### Post by Pumalite on 2008-07-26
Double post:
[http://ubuntuforums.org/showthread.php?t=871120](http://ubuntuforums.org/showthread.php?t=871120)

---

### Post by use_R on 2008-07-28
That's the way it is. :-({|= :-) Thanks.

---

