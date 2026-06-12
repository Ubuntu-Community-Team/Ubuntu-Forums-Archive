---
title: "printing blues (hp 959c, parallel)"
date: 2005-07-25
forum: Installation &amp; Upgrades
---

### Post by arminbw on 2005-07-25
First of all: I really like Ubuntu.
At the moment I am using Kubuntu Hoary, but I think the problem I have is not KDE specific. And I am using a 64-bit version, but I think my printing problems aren't related to that ether (but who knows). The mainboard is an Asus a8n sli (nforce4 chip).

The printer is a HP Deskjet 959c, parallel port.

First question: /dev/lp0 is useable for root only. Where can I change this permanently? A chown or chmod helps just until the next reboot.

If I do a simple 'echo "test" > /dev/lp0' as root the printer starts doing something. First it waits about 30 seconds, later it prints a single letter and stops.

I changed user=lp to user=root in cupsd.conf and tried the "print test page" option in the "Control Center" gui stuff. I can choose between four different hp deskjet 959c drivers, but three of them did nothing. With the gimp-print-ijs driver the printer printed a few pages full of rubbish.

The cups error_log has't given me any hints.

Any ideas?
Thank's. 
 Armin

---

### Post by mxsteini on 2005-10-04
Hi Armin,
sorry for answering so late, but I found the thread due to my own problems...
I can answer only the first question.
goto /etc/udev/permission.rules
search for permission for your printerdevice and change them to 0666 or something like that.

bye Michael

---

