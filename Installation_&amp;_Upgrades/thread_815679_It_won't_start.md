---
title: "It won't start"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by Instrument on 2008-06-01
I've tried using wubi *and* burning the iso image to a Cd.. both ways, when trying to start ubuntu, the orange bar goes across a few times, then stops. I've tried waiting overnight for the thing to go across, nothing happened. It just sat there. Derp.


How do I fix this? I really want to try out ubuntu.


My specs:
2.93 GHz celeron d processor
nvidia geforce 6200 [pci]
2x 80gb hard drives
WinXP Home edition sp2

Any and all help appreciated!

Edit: I also want to keep winblows after the install, dual boot, etc.

---

### Post by Pumalite on 2008-06-01
Burn a new CD. Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum, burn at 4x on good quality CD-R. Try again.

---

### Post by kewe86 on 2008-06-02
What version are you trying to use?

I tried using 8.04 hardy heron but my system which runs a windows xp service pack 3 failed to work with it.

I went lower and tried 7.10 gutsy and the same thing happened.

I did a last try and went with 7.04 fiesty fawn and it worked. I was able to boot from Live CD and install.

I dont know why is like this, I am new to ubuntu as well. Hope this helps.

Good luck.

---

### Post by sprightlyone on 2008-06-02
hi 
  i had a similiar experience &found i had to d/load the alt. cd & install that .
 this article :[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)    @community help was the next thing i tried from the point "For Installed Systems That Need Adjustment" this allowed me to see where my load stalled  
 i then edited the kernel line which then took me a little further 
i then realised i had a AMD 64 system which then needed a anothr edit to the kernel line 
 i tried this "irqpoll pci=noacpi no lapic acpi=off " was suggested for amd64 systems this let me log-in  i then opened up aterminal window &loaded my menu.lst &made the changes permanent 
 i then had it dual booting to ubuntu or windows  until my wife decidedto try my ubuntu (but that is another story )

iam very new as well but this is what worked for me may be it will help you 
lyle

---

### Post by Pumalite on 2008-06-02
If that were the case; here there is something to try:
Boot parameters
                                                                                                                                                                                                                                                                                                                                                                                                                                    [http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
Try the most common ones first:
noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off vga=0x317 vga=791 vga=788
To be tried alone or in different combinations until you hit the right one.

---

