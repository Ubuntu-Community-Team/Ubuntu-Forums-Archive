---
title: "ubuntu 12.04 New instalation sata hdd"
date: 2013-02-10
forum: Installation &amp; Upgrades
---

### Post by dobromir.mitkov on 2013-02-10
Hello,

how to install an ubuntu. on a blank sata hdd. first install. do i need windows on it to format them? the problem comes from the fact that it can not recognize the hdd.

help please.

---

### Post by Bashing-om on 2013-02-10
dobromir.mitkov; Hi !

Try this --- as it is a new hard drive perhaps not having an existent partition table is the problem.

Boot up with the liveCD: -> try ubuntu 
At the desk top: launcher (left side of screen) -> ubuntu button (top icon) = the dash
in the dash insert the term GParted (ubuntu partiton editor);
click on the GParted icon to start the utility;
select the drive from the upper right - only one drive ? will be "sda"-;
choose "device" in GParted's task bar -> new -> format -> "msdos" [this is not microsoft dos] if you are happy with the older partitioning scheme of 4 primary partitions;
Close out GParted and click on "install ubuntu" icon on the desk top. Carefully follow the install wizards prompts to install ubuntu. -Remember your username and PASSWORD as they are vital to administer your system.

[INDENT][INDENT][INDENT]just try'n to help

[/INDENT][/INDENT][/INDENT]

---

### Post by fantab on 2013-02-11
If the Blank Sata HDD is new and more than 2TB than you are better off using GPT table instead of MSDOS.

---

### Post by dobromir.mitkov on 2013-02-11
I was able to install it. And at the moment Ubuntu is updating. Thank's for the support. ):P I was using Ubunto 12.04 for 3 weeks now and  Ubuntu 10 for 2 years and I didn't know about the partitioning software.

Greetings.

---

### Post by Bucky Ball on 2013-02-11
*Thread moved to **Installation & Upgrades**.*

Please perform the suggestion to Help Others in my signature if this is solved. ;)

---

