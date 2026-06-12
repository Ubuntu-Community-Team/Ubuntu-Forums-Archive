---
title: "dual boot uefi win10 problem"
date: 2016-11-02
forum: Installation &amp; Upgrades
---

### Post by cosphi on 2016-11-02
Hi everyone, I understand this is a common problem but with every post I read comments say every situation is case specific.

today I've bought an Acer Aspire E15 laptop and I am trying my best to install Ubuntu 16.10 next to my windows 10. Unfortunately I need windows for a few things so I have to dual boot.

I brought the partition size back to 250Gb, created a 40Gb root sda5, 8Gb swap and 500Gb data partition. installed Ubuntu with root swap and uefi defined, but do not get grub at boot, to choose which os to run.

I use Ubuntu but my knowledge does not go far.

it is an E15 757 Acer Aspire, i3, 4Gb RAM, 1TB uefi

Any help you guys could give me, I would greatly appreciate it! Thank you in advance!

Remco.

---

### Post by oldfred on 2016-11-02
See link in my signature for general UEFI install.
But Acer has a unique requirement for setting UEFI password and enabling "trust" on Ubuntu/grub .efi boot files from UEFI.
Also make sure you have newest UEFI from Acer. Some older thread mention downgrading UEFI, but newer ones say to upgrade and that works.

       Acer Trust Settings - details:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757
[/URL]
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062)
One of several with more details on trust:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335) 

[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]
[/URL]

---

### Post by cosphi on 2016-11-02
thank you very much! i am sure the answer must be in here!

Thank You!

---

