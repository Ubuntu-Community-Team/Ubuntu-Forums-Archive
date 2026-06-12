---
title: "dapper install with no=acpi"
date: 2006-09-15
forum: Installation &amp; Upgrades
---

### Post by heathenx on 2006-09-15
hello,

i have been using ubuntu 5.10 for some time on my compaq armada 1700. it has always worked flawlessly...very stable os. however, when i install 5.10 on my laptop i ALWAYS have to use the boot option "boot: linux noacpi acpi=off" otherwise i get about halfway into the install and my laptop shuts off.

so now i would like to install 6.06. i booted the live cd and everything works just fine. i click the install icon and i can get about 40% into the install before my laptop shuts off.

so during boot, i f6 to add some options to the options already there. i add "noacpi acpi=off" but my laptop still shuts down during the installation process. 

my question: how do i boot/install with "noacpi" and acpi=off" options? i have tried so many times last night to install 6.0.6 that my eys and ears started to bleed.:mad: 

i suppose i could fall back to 5.10 but 6.06 is so darn pretty.

---

### Post by ajgreeny on 2006-09-15
You may need to use the alternate install CD which gives you many more options for installation then the live CD.  Have a look on the ubuntu site for that version; it has a text based installer a bit like breezy's version, but as you got that up and running, dapper shouldn't be any more difficult.

---

### Post by heathenx on 2006-09-15
ahh. i wasn't aware of another install cd. i'll check it out. thank-you.

---

### Post by heathenx on 2006-09-16
well, that did the trick. i downloaded the 6.06.1 alternate cd, installed via text mode, f6, added linux acpi=off noacpi, and it took off. it was a slow install but it workded like a charm. i'm writing this post on my new 6.06 install.

thanks a ton.

btw, once i booted to the desktop, i went into the grub menu and removed "linux acpi=off noacpi" and replaced with acpi=off. i did this right after the spalsh screen option.

:D :D :D :D

---

