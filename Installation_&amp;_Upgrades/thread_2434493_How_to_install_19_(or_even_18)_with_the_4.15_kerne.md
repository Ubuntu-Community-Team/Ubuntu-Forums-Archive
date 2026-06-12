---
title: "How to install 19 (or even 18) with the 4.15 kernel?"
date: 2020-01-06
forum: Installation &amp; Upgrades
---

### Post by inappropriate on 2020-01-06
Hello and thank you in advance. To make a long story short I have a HP laptop with ACPI errors that I found only the 4.15 kernel is stable (5.0 fails to boot and 5.3 fails to shutdown). My question is, is it possible to install the version 19.04 or even 18.04 with the 4.15 kernel? I noticed the ISO images both have the 5.0 kernel. It would be ideal if I could get an iso with the 4.15 kernel. But in case I can't do that what is the best alternative? I suppose I could install the 5.0 kernel and downgrade but I want to fully test it out first before installing if that is possible.

---

### Post by Bashing-om on 2020-01-06
inappropriate; Hello

If you install 18.04.[color=green] 1 [/color] then :
> 
<ubottu> linux-image-generic (source: linux-meta): Generic Linux kernel image. In component main, is optional. 
               Version 4.15.0.74.76 (bionic), package size 2 kB, installed size 15 kB


Then again ACPI issues may have resolutions, not enough info in that respect to make a call.

[INDENT]we are all in this together[/INDENT]

---

### Post by inappropriate on 2020-01-07
Sorry bud but I'm not following you. You are saying to install the 18.04 with the 5.0 kernel and then downgrade?

---

### Post by deadflowr on 2020-01-07
> **inappropriate said:**
> Sorry bud but I'm not following you. You are saying to install the 18.04 with the 5.0 kernel and then downgrade?

No.
Just install this image
[http://old-releases.ubuntu.com/releases/18.04.1/]("http://old-releases.ubuntu.com/releases/18.04.1/")
It has the 4.15 kernel already.

More on how Ubuntu ships newer kernel stacks:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")

---

### Post by Bashing-om on 2020-01-08
inappropriate; Hey -

If you install the .1 release:
then
> 
sysop@x1804mini:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.3 LTS
Release:	18.04
Codename:	bionic

sysop@x1804mini:~$ uname -r
4.15.0-74-generic
sysop@x1804mini:


Where my system, fully updated to version  18.04.3, was initially installed as 18.04-

you will have the 4.15 kernel, supported for 5 years.

[INDENT]ubuntu -
[INDENT][INDENT]sized to fit your needs
[/INDENT][/INDENT][/INDENT]

---

