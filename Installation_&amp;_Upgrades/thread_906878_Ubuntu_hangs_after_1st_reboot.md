---
title: "Ubuntu hangs after 1st reboot"
date: 2008-08-31
forum: Installation &amp; Upgrades
---

### Post by shane3 on 2008-08-31
I installed 8.04 Desktop edition, and was prompted to reboot.  The reboot hangs with the message 'Starting up ...'.

I had a lot of trouble with the installation and my graphics card.  I finally had to install it in 'Safe Mode', otherwise I could not get the visual installer to come up (black screen).  I'm guessing this is the same problem I'm having now when rebooting after the initial installation. Any help would be greatly appreciated.

---

### Post by manishtech on 2008-09-02
Please tell us what graphics card you have, if you cant find out exactly, please post the output of this
```
lspci | grep -i graphics
```

---

### Post by shane3 on 2008-09-03
Thanks for the reply!  I've got a 1GHZ AMD with 256MB memory, and an S3 Trio64V+ PCI video card. 

I've tried to install Ubuntu 8.04 Desktop with both the Live and Alternative.  Both end up with with the same result, which is the installation goes without error but when asked to reboot the BIOs runs, grub loads, then 'Starting up...' displays on a black screen and hangs.  There is no hard disk activity.  I've let it reboot for several hours without changing.  

I've also tried to tack on the 'vga=771' (and other values) parameter by editing the kernel.  What's weird is upon boot I'm told that this isn't a valid value.  Instead values from 0,1,2,n are listed as valid with values like (80,25).  Not what I expected according to the documentation. 

Another strange thing is that I booted into command line mode to see if I could fiddle with the xorg.conf file.  I thought it would be in /etc/X11 directory, but none existed.  Maybe it's somewhere else, but I'm a linux novice and didn't take the time to figure out how to search for it.  

Any help you could provide would be great.

---

### Post by manishtech on 2008-09-04
While booting through the liveCD, try adding **noapic** option to the boot options, press F6 before pressing enter on any option.

---

### Post by shane3 on 2008-09-07
Adding 'noapic' did not resolve the issue.

---

