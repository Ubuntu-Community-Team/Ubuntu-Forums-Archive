---
title: "LiveUSB install problem"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by dwabra on 2007-06-15
I'm trying to install Edgy on a 1 Gb USB drive (PNY Attache).  The install goes mostly per instruction ([https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)) with one small glitch.  The glitch is that when I try to umount the USB stick just before installing syslinux it says "Device busy, can't umount".  So, I checked which processes were running on /dev/sda1 using 'lsof +d /mount/edgy' and killed them.  The processes I killed were innocuous - one 'su' process I think and another I don't remember right now. After this I could umount the usb stick. Then I ran syslinux and rebooted.  

It got all the way in to Ubuntu up to the final screens (i.e. it loaded the kernel and showed the ubuntu screen with the growing orange progress bar) and then froze for a minute or so.  Then it failed with a text screen saying: 

"BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash) 
Enter 'help' for a list of built-in commands. 

/bin/sh: can't access tty; job control turned off 
(initramfs)"

I can execute simple commands from this prompt but haven't a clue about what to do to repair this!  

Any ideas appreciated!  
Thanks- 
David

---

