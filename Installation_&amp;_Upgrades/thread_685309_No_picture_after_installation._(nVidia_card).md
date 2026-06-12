---
title: "No picture after installation. (nVidia card)"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by prelude on 2008-02-02
hi

I've been trying to get ubuntu installed on my machine but I've been experiencing some problems and I'm hoping someone here could help me out here.

lets start with my hardware.
Asus A8R32-MVP Deluxe mainboard
Opteron 185 CPU
4GB ram
Nvidia 8800 GTX 768MB
2 PATA HD's
5 SATA HD's
1 SSD - Main Windows disk. (Addonics Quad-CF card with two CF chips. it's basically a SiL0680 controller card with CF slots instead of PATA connectors)


I Installed Ubuntu from the 7.10 AMD64 alternate cd and installed the OS on a spare SATA drive I had but booting from it turned out to be a problem. what happens is that when I try to boot is a s follows.

after grub loads I get a very brief glimpse of the kernel loading saying something like "keeping kernel alive and a whole bunch of numbers" and then my screen goes black. I can see the HDD busy light is flashing and after a little while I get a click sound through my speakers so something is happening. its just that I can't see anything on my screen. the keyboard works and ctrl-alt-del reboots my system.

I've tried to boot the OS using the failsafe. that works and I can see the OS booting and I get the console. From searching the forums here I figured I'd try this command I found
```
 dpkg-reconfigure xserver-xorg
```
and I set the graphics driver to VESA and rebooted.

what happens then is the usual black screen immediately after boot but after a while my screen flashes and then I get a "NO SIGNAL" message from my screen and it powers down.

manually editing the original xorg.conf file and replacing the driver "nv" with "vesa" didn't help either so, I'm at a total loss here and I don't know what to do.


PS. the live CD produces the same black screen.


Solved:
After some extensive searching on the net I found a solution on a SuSE linux forum which was remarkably simple..

It turns out that with some LCD panels the kernel fails to initialize the graphics correctly (or something like that) and adding ```
vga=normal
``` to the boot commands takes care of that.

I'm typing this on my new installation of Ubuntu ):P

---

### Post by eeyore76 on 2008-02-02
Hi

I have the same problem, but with different hardware.
The Live CD doesnt start the system correctly. I had to use the alternative text installer. But when the system is installed and reboots: nothing but black screen. I have tried the same things as you described: setting to reconfigure X, set to VESA etc...
I also tried to install Fedora Core, with basically the same result.

Searching forums and the Internet yields a lot of threads and discussion about this problem, but I have found no remedy.


So, this is a SERIOUS problem. Things like this makes people stick with M$ ...
Can someone at least try to pinpoint WHAT is the problem. My myself is far to inexperienced with Linux to find out.


I have tried 
- Ubuntu 7.10
- Ubuntu x64 7.10
- Ubuntu x64 7.10 alternative
(And, yes, I have checked the discs for defects...)

My hardware:
AMD Athlon 64 3500+
ATI X800GTO
1GByte RAM
MSI K8N NEO-F (nForce4)
(Tried several monitors, old VGA flat panel and new DVI flat panel)

---

