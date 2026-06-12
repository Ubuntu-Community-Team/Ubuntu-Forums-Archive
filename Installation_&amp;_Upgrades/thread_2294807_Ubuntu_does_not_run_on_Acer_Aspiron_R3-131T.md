---
title: "Ubuntu does not run on Acer Aspiron R3-131T"
date: 2015-09-13
forum: Installation &amp; Upgrades
---

### Post by elvisblanco1993 on 2015-09-13
Here is the thing. I just bought this Aspiron R3-131T( the cheaper one) and i tried to install ubuntu on it. I already deactivated UEFI boot on BIOS. It loads the Grub menu, but when it starts loading the OS the screen gets white and stays there forever. Any help this would be appreciated. :)

---

### Post by Bucky Ball on 2015-09-13
*Thread moved to **Installation and Upgrades**.*

Welcome. More detail, please. Is this going to be a dual-boot with Windows? Which version of Ubuntu are you using? Have you installed Ubuntu or you are running a Live session from install media? If the latter, when you boot from the install media, USB or disk, and you get to the screen 'Install Ubuntu' 'Try Ubuntu', hit F6 and choose 'nomodeset'. Continue. Any luck? 

Any other info you can think of. Check the third link in my signature for some hints. :)

---

### Post by elvisblanco1993 on 2015-09-13
I am trying to make a stand alone install of Ubuntu 15.04 (I don't want Windows on my hardware :P ) . I am using a USB stick. Already tried with 'nomodeset' option, but still does not work. Now I am trying Elementary 0.3.1 and this work just fine for now. :)

---

### Post by fokkedekker on 2015-12-08
Did you use any special boot parameters to boot the live disk. Mine won't boot without noapic, and even then it won't show the desktop, tty1 is working however. All other linux distro's do not work without noapic and acpi=off.

Thanks.

---

