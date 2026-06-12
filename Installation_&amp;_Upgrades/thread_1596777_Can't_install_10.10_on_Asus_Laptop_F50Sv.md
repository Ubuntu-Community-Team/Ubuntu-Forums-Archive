---
title: "Can't install 10.10 on Asus Laptop F50Sv"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by lottomotto on 2010-10-14
Hello,

I used this laptop since 8.4.

When first 10.10 beta arrived I decided to upgrade as usual. all seemed to go well. At reboot the computer was hanging after grub, with a blinking cursor on top left. Then was turning off and had getting into a weird hung mode. Was not possible to start it over. The only solution was unplug, take battery off and wait for a minute.

Now with the official 10.10 I decided to install it over.

But the live CD start right after the first screen. Again with the blinking cursor and angs the machine again.

Windows works perfectly as well as all Ubuntu, including 10.4

---

### Post by lottomotto on 2010-10-14
I forgot... I installed, with the same CD (which is actually a DVD cause I run out of CDs) on my VM in MAC OSX SNow Leopard.

thanks a lot

---

### Post by lottomotto on 2010-10-16
It install and stars with Apci=off, any solution?

---

### Post by bigpup on 2010-10-16
10.10 CD, either 32-bit or 64-bit, does not install on Sony CW laptop. I get initial splash of purple screen, but then all black while optical drive works hard for a few minutes. Nothing ever comes back on. Have to restart with power switch. (This is meant to be fresh install on new SSD. I have had 10.04 installed since RC days; the only thing not working is bluetooth. Nvidia graphics drivers are very useful, but were not needed for 10.04 basic installation.)

---

### Post by lottomotto on 2010-10-18
Ok.

so I installed with Acpi=off (options F6). NOw to start I can do the same. "e" for options and I add acpi=off to Grub2.
The problem is that acpi functions are really usefull and the laptop is unusable without it...

any hope that future kernel will fix the problem?

---

### Post by PollekePol on 2010-10-18
If you do CTRL+ALT+F7, you probably see the message 'Checking Battery State'?

---

### Post by lottomotto on 2010-10-18
> **PollekePol said:**
> If you do CTRL+ALT+F7, you probably see the message 'Checking Battery State'?

nothing happens with ctrl+alt+f7

---

### Post by PollekePol on 2010-10-18
Mmm, funny. Tried it just now again myself. This time mine did not respond to the CTRL+ALT+F7 (or F1 etc) at all either :-) Just the blank screen with a cursor in the top left corner.

But after rebooting it responded to the CTRL+ALT again, so I could select the tty where F7 normally gives you the GUI. But like you, it is stuck and won't load the GUI (the last message is the 'Checking Battery Status'). The 10.04->10.10 migration must have f*d up the configuration required for the GUI to come up, e.g. loading the wrong graphics driver or something? Mine is an onboard intel graphics card.

Had no problems with 10.04. I have this problem since the upgrade to 10.10, a black screen with just a blinking cursor on start up - like you and many others.

---

### Post by PollekePol on 2010-10-25
> **PollekePol said:**
> Mmm, funny. Tried it just now again myself. This time mine did not respond to the CTRL+ALT+F7 (or F1 etc) at all either :-) Just the blank screen with a cursor in the top left corner.
 
But after rebooting it responded to the CTRL+ALT again, so I could select the tty where F7 normally gives you the GUI. But like you, it is stuck and won't load the GUI (the last message is the 'Checking Battery Status'). The 10.04->10.10 migration must have f*d up the configuration required for the GUI to come up, e.g. loading the wrong graphics driver or something? Mine is an onboard intel graphics card.
 
Had no problems with 10.04. I have this problem since the upgrade to 10.10, a black screen with just a blinking cursor on start up - like you and many others.
 
Have moved to Linux Mint.

---

### Post by t1m3 on 2010-11-30
i'e got the same computer as you.
instead of booting with the 'acpi=off' command, i used 'nolapic'.
i works out better, i get the control back.. like brightness, battery, and a smooth shutdown.
and now i can see my battery percentage!
i forget what the nolapic command does exactly, i think it restricted the processors or something..

now everything is perfect!

---

