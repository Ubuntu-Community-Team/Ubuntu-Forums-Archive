---
title: "CMI8788 detected in lspci but not listed in gnome not working"
date: 2010-03-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by swimfish on 2010-03-16
CMI8788 detected in lspci -v but not listed in gnome not working in lucid.

06:01.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
    Subsystem: ASUSTeK Computer Inc. Device 838e
    Flags: bus master, medium devsel, latency 32, IRQ 11
    I/O ports at ec00 [size=256]
    Capabilities: <access denied>

thanks

---

### Post by executorvs on 2010-03-16
my girlfriends c-media card showed up as a pci device but ran most of it's sound channels through the usb hub (I never did figure out if the pci detection was a bug in ubuntu) that said it wouldn't load because ubuntu (used to at least) blocks usb audio devices from grabbing the primary position at boot. you may want to check that and to see if your card is blacklisted for some reason.

I doubt it's the same problem though as each time I've had trouble with C-media devices It's required a different solution. hopefully it helps though.

---

### Post by swimfish on 2010-03-16
where might i see if my card is blacklisted ?  i don't seen see a single bug report for this chipset and lucid, and lots of reports with issues of it in previous releases.  also, what module would i be looking for at that location ?  would it be safe to unblocklist it ?  its a very common card, i had seen reports of it being functional under other distros.  its a Xonar DS PCI 7.1.  

thank you for your time

---

### Post by executorvs on 2010-03-16
I'm actually shy on time right now but will try and find the thread that pointed me to the blacklist later this evening and get back to you.

---

### Post by cariboo on 2010-03-16
You could look in /etc/modprobe.d/ to see if the card is blacklisted.

---

### Post by swimfish on 2010-03-18
i've got these.  one of them had a CMPCI blacklisted.  i commented that out to see if it'll work after reboot.  note:  it was not a cmipci

[http://pastebin.ca/1844409](http://pastebin.ca/1844409)

[http://pastebin.ca/1844405](http://pastebin.ca/1844405)

[http://pastebin.ca/1844407](http://pastebin.ca/1844407)

---

### Post by swimfish on 2010-03-18
rebooted and that did not do the trick.  

:(

---

