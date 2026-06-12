---
title: "Ubuntu on USB stick not recognized"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by ibonig on 2008-06-20
hello
couldn't find an answer in the forum, hope you can help
(sorry about my english)

I set up newest Ubuntu on an usb thumb stick like explanied in that manual:
[http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)


that worked without problems, but by booting my notebook or desktop over different USB ports I get the message "pendrive without operating system"

Than I set up the stick with Windows option, but it's still the same :(

How can I test or check where the problem is?

any help will be appreciated

Chris

---

### Post by Pumalite on 2008-06-20
How large is your pen drive? You can install 8.04 directly to it as if it were a hard drive.

---

### Post by ibonig on 2008-06-20
hi

1GB , for a compleat install I would need 4GB?

---

### Post by Pumalite on 2008-06-20
You can make it with 4 GB. Best is 8 GB

---

### Post by ibonig on 2008-06-20
hmmm, bought already two x 1GB for that customer, would be to expensive anyway, because it will be used by beginners only for surfing more securely in a doctors office.

Do you have an idea, why Ubuntu can't be recognized and where I can find another way to get it on the stick?

---

### Post by Pumalite on 2008-06-20
I have a few links I can give you:

[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)


[http://www.ryancloke.com/ubuntu-804-hardy-heron-live-usb-how-to/](http://www.ryancloke.com/ubuntu-804-hardy-heron-live-usb-how-to/)


New:
[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/#more-372](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/#more-372)

---

### Post by Carondimonio on 2008-06-20
The problem is most probably due to the fact that, at boot time, the BIOS hasn't recognised the pendrive yet.
Check in the BIOS settings whether the "enable USB legacy support" and "enable USB keyboard" options (or something similar) are ON.
Even then, it can happen that the USB device sometimes is not recognised. I have the same issue with a Gutsy Server installation I did on a CF card. The solution, in my case, is as follows:
- Boot the PC WITHOUT the pendrive in (but with the "Boot from USB" option enabled)
- When the default start-up screen pops up (the one which offers you the possibility to enter the BIOS settings), insert the pendrive. It should then boot.

---

### Post by ibonig on 2008-06-20
thanks for the links, quite helpfull ! it seems to be more easy to make a compleat install on 4GB and thouse stick prices are resonable low. 
I changed the order.

that one here I will try anyway
[http://www.ryancloke.com/ubuntu-804-hardy-heron-live-usb-how-to/](http://www.ryancloke.com/ubuntu-804-hardy-heron-live-usb-how-to/)

might take a while :)

---

### Post by ibonig on 2008-06-20
hi Carondimonio

it says "no operating system on pen drive" so I assume that usb port might pork properly
USB emulation enabled - that might be the one

In bootmenu I only find an usb storage device when I plugged in the stick.
Without stick it runs through

---

### Post by Carondimonio on 2008-06-20
> **ibonig said:**
> hi Carondimonio

it says "no operating system on pen drive" so I assume that usb port might pork properly
but I will try that

Well, in my case it usually says "No Operating System Found". It's just a BIOS message, a line on a black screen. When I re-boot and insert the stick during booting, it works.

If I understood correctly, your PC doesn't see a Windows-bootable pendrive either, right? There's the hint...

---

### Post by ibonig on 2008-06-20
that message "no operation on pen drive" is that quick, no chance to ctrl alt del reboot. Anyway the port seems to be ok.
I don't know about Windos bootable, but backtrack for example on another stick works well.
Thats why I am sure, its more Ubuntu on that stick thats causing the problem.

---

