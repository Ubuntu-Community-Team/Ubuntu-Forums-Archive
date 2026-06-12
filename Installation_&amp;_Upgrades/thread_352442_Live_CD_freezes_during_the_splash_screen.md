---
title: "Live CD freezes during the splash screen"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by 6StringSamurai on 2007-02-03
I'm really interested in trying out Ubuntu so I tried the Live CD.

I selected the right option from the menu and it seemed like it was starting out right.

A splash screen with the Ubuntu logo came up with a little progress bar, a lot like the one I get with Windows XP.  After a few minutes, the progress bar stops and the screen locks up. 

The first that happened I rebooted after a few minutes, the second time I left it that way for an hour to see if it worked itself out. 

No luck!

What next?

Thanks!

---

### Post by housam on 2007-02-03
Could be a RAM problem. What about your pc specs? What version of ubuntu you try to install?

---

### Post by 6StringSamurai on 2007-02-03
My specs are pretty good, 2.9GHZ with 2GB of RAM.

I'm trying the Live CD of 6.10

---

### Post by rsambuca on 2007-02-03
Depending on what chipsets you have on your motherboard, you might have to add some boot options prior to starting the live CD.  At the main screen, press F6 to edit boot options.

You will see a bunch of commands prior to  a couple of dashes "--"

Before the dashes, you should try the following (I am guessing here since you didn't give us enough info on your rig)

ide=nodma  (make sure you leave a space before the -- at the end

try rebooting.  If that doesn't work, try again using:

irqpoll pci=noacpi noapic nolapic acpi=off (just stick all of these in at once and see what happens when you boot, if that doesn't work, try different combos of them, sorry)

---

### Post by 6StringSamurai on 2007-02-04
Ok, sorry for not giving more information before.

My computer started life as an E Machines T6520, here are some detailed specs:

[http://reviews.cnet.com/eMachines_T6520_Media_Center_PC/4507-3118_7-31466280.html](http://reviews.cnet.com/eMachines_T6520_Media_Center_PC/4507-3118_7-31466280.html)

It's running Windows XP.  I've made some modifications.  I now have 2 gigs of RAM, a very high end sound card for with built in functions for recording and mixing audio and a PCI card with 3 fire wire ports.

The onboard video sucks, I haven't had the need to replace it but I'm considering getting an nVidia card because I've heard they work better with Linux.

My ultimate goal is to dual boot XP and Ubuntu/Beryl, using Windows for my music work and Linux for everything else.  I'll use a separate hard drive for Ubuntu instead of a partition.

Given what I have, is that possible?

Thank you for your trouble shooting steps, rsambuca, I tried them but they didn't help.

I also tried the 6.10 Alternate .iso.  It froze up but I did get an error message this time. It was something like this:

PCI Can not allocate resource region 3 of device 0000: 0000.00
irq 193 no one cared (try irq poll)

(I did try irq poll as part of the above advice but no luck!)

Any ideas?  Thanks!

---

### Post by 6StringSamurai on 2007-02-04
Oh, I also tried DSL-N and I was able to boot a Live CD of that with no problems.

I do prefer Ubuntu though! :)

---

### Post by 6StringSamurai on 2007-02-04
Any ideas on what I can try next?

Thanks!

---

### Post by rsambuca on 2007-02-04
I'm not sure what else you can try.  i don't have a eMachines PC, but mine is a very similar off the shelf unit from Cisnet.  Virtually the same specs and motherboard, etc.  I just had to use the ide=nodma option to boot (as I have to to boot from any CD).  Only thing I can think of is to remove your firewire and sound cards for boot up, and try with the above boot option.

---

### Post by 6StringSamurai on 2007-02-06
I was playing with this again and I was able to boot into the desktop using ide=nodma!

The problem is, either it froze up right after the desktop came up or my usb keyboard and mouse weren't working...

Thank you so much for helping me with this... what next?

---

### Post by rsambuca on 2007-02-07
Well, at least we got it booting up!  

Can you boot up in recovery mode?  If so, try entering this in the command line:```
sudo dpkg-reconfigure xserver-xorg
```

I would try and stick to the default options on most settings, but really go through the keyboard and mouse options carefully.

Give that a whirl and see what happens.

---

