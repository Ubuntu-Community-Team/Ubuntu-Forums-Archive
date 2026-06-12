---
title: "hangs on startup after wireless setup"
date: 2006-04-30
forum: Installation &amp; Upgrades
---

### Post by kludge on 2006-04-30
I have a new install of breezy badger on a Sony VAIO PCG-K45 laptop, that began to hang on startup after I set up wireless networking.  If I follow the console via ctl-alt-1, it seems to get through the entire process okay, until the X desktop login screen starts.  At that point, the console goes away and doesn't come back. ](*,)  I've already re-installed once just to chase this ghost. 

The wireless network uses 128 bit WEP security, and sets up okay.  Everything works, until I reboot.  Before wireless is set up, the "network" notification fails during boot, and the ntp clock setting fails too.  Once the network is setup, the networking passes, and the clock setting passes, but the desktop fails!  ARRGH!!!

Does anyone have any ideas?  Services I could turn off or something?

---

### Post by antiwyrd on 2006-04-30
when i installed ubuntu on my comp it wouldn't detect the wireless and only worked when i plugged it in using the wried connection. See what happens if you plug it in

---

### Post by kludge on 2006-04-30
It detects the wireless just fine, and boots as long as it isn't configured.  The problem only occurs once the wireless is configured. 

On the Sony, I can disable the wireless with a mechanical switch.  When I do that, it boots correctly. But that's because the kernel can't detect the wireless card anymore.  Turning the switch back on doesn't seem to engage PnP so it detects. :(

---

### Post by Mustard on 2006-04-30
Have you had a look through your logs in the /var/log/ folder to see what you can find that might be related to the issue?

---

### Post by kludge on 2006-04-30
Nope, haven't checked /var/log yet.  However, I'm starting to think I won't find my answer there.  I have determined that the wireless network works correctly in recovery mode - I can ssh out to the 'net from the root prompt.  And I have determined that the graphical login works IF the wireless is physically turned off.  So it's probably some sort of interaction between the existence of wireless access and the graphical sequence.  At that point, I'm reading through init scripts looking for bugs. :evil: 

Next, I'm off to plug it in to the wired network, set that up, and see if it has similar problems.  That'll tell me whether it's a network issue or a wireless-specific issue.

This is making me very cranky.

---

### Post by Mustard on 2006-04-30
I'm wondering whether you might find some IRQ allocation problems if you look through the logs.  If that is the issue then you might try booting with a few special kernel parameters to try to overcome this.

---

### Post by kludge on 2006-04-30
Any suggestions on what kernel parameters might resolve this?  I suppose an IRQ conflict makes sense.  That would explain WHEN it blows up, that is, when gdm starts.

---

### Post by Mustard on 2006-05-02
Well you could try pci=routeirq or even irqpoll.  On a desktop machine I would suggest noapic and nolapic, but I don't know whether thats a practical solution for a laptop.  I think you would need to establish whether it was an IRQ issue from reading over the logs though.  I'd look through the syslog and kern.log files.  I'm not exactly sure which ones are going to contain relevant information.

---

### Post by az on 2006-05-02
Are you using ndiswrapper?  Does your card now have a native linux driver?  Are they in conflict - did you blacklist the linux driver?

---

### Post by kludge on 2006-05-02
I've tried the ATI binary driver, but it either blows up on configuration errors, or causes a kernel panic. I've also tried the whole gamut of IRQ-related kernel options - irqpoll, noacpi, etc, every combination I could find.  Nothing works so far.  

Since it's a new installation, I'm going to start from scratch tonight with the 6.0.6 beta and see if that doesn't resolve the problem.  And if that doesn't work, I'll try another distro and see if that works instead - although I'm not counting on it, as it seems very much a kernel problem, which isn't necessarily an Ubuntu kernel problem. 

Y'know, I've been using Linux off and on since installing SLS back in '94, and I think this is the most painful install I've ever had.

---

