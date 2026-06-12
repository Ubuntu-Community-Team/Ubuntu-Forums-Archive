---
title: "Low graphics mode during install"
date: 2013-06-03
forum: Installation &amp; Upgrades
---

### Post by Akkaid on 2013-06-03
hey all,

I posted this before, and it didnt seem to work, so here goes again, but a few beers later...

When I try to boot after install, it gives me the 'Low graphics mode' error.  Ive searched solutions to this, but none work for me, when I try to go to terminal after failsafe mode to install drivers, it gets hung up at 'loading glx extention'.  Ive reached the end of my rope, any help would be grteat,

MSI 440DX
I7 something
ATI 630M
Too much beer for one night.

---

### Post by gordintoronto on 2013-06-03
When I Googled "MSI 440DX" (in quotes) the only result was your post. Is it a motherboard, a laptop, or something else?

ATI 630M sounds like a video adapter, (once again, Google didn't help) but what is it driving, and how is it connected? A significant portion of people complaining about low graphics mode seem to be using adapter cables with a different connector at the monitor end from what is plugged into the computer.

Are you sure it's not an Nvidia 630M? That one seems to often link to that horrid Optimus technology.

I suggest this command: sudo lshw -html > desktop/myconfig.htm

That will produce a nicely formatted description of the details of your computer, which you can browse.

---

### Post by Incarnadin on 2013-06-03
I have exactly this problem plus some others. I have a laptop with a Radeon 6400 series graphics. At this point I'm pretty sure it's got something to do with the graphics drivers. Any attempt to load unity is just fraught with errors. I tried to install new proprietary drivers but that just made the problem worse.

---

### Post by Akkaid on 2013-06-04
Sorry for the lack of detail, it was pretty late at night.  below are the exacts of my system.  Also, I cannot use any commands as I cannot get to a terminal, it gets stuck at 'loading glx extentions'.

Thanks for the help!

[TABLE="width: 100%"]
[TR]
[TD="class: main, width: 30, align: right"]x[/TD]
[TD="class: main"]MSI X460DX-291US
 * - : *
 * - Back Up Software: No Back Up Software*
 * - Battery: Smart Li-ion Battery (6-Cell)*
 * - Bluetooth: Bluetooth Included (See “Wireless Network” Section Below)*
 * - Camera: Built in 1.3Megapixel Camera*
 * - Car Adapter: No Car Adapter*
 * - Case: No Carrying Case*
 * - Dead Pixel Warranty: Standard Dead Pixel Policy*
 * - Display: 14.1" HD 16:9 "Glare Type" Super Clear Ultra Bright Glossy** LED** Screen (1366x768) (SKU - X1R201)*
 * - Exterior Finish: Standard Finish*
 * - External Display Video Adapters: No Video Adapter*
 * - External Hard Drive (Back Up): No Back Up Hard Drive*
 * - External USB Optical Drive: NO External USB Optical Drive*
 * - Floppy Drive: No Floppy Drive*
 * - Free Shipping: **FREE!! **UPS GROUND SHIPPING (Use Coupon Code "FREESHIP" in Checkout - U.S. Only, Not Available to Alaska and Hawaii)*
 * - Graphics Video Card: nVidia GT 630M 2048MB PCI-Express DDR3 DX11 with Optimus™ Technology (SKU - X3R514)*
 * - Memory Card Reader: Internal 2-in-1 Card Reader (SD/MMC)*
 * - Monitor Calibration: NO Professional Monitor Color Calibration*
 * - Optical Drive Bay: **Combo Dual Layer SuperMulti DVDRW/CDRW Drive w/ Software** (SKU - X7R451)*
 * - Optical Drive Bay Hard Drive Caddy: No Extra Optical Bay Hard Drive Caddy*
 * - Port Replicator / Dock / Adapters: No Dock/Hub/Adapter*
 * - Primary Hard Drive: 120GB Patriot Pyro SE Solid State Drive (SSD Serial-ATA III) (SKU - X5R419)*
 * - Processor: 2nd Generation Intel® Core™ i7-2670QM, 2.2-3.1GHz, (32nm, 6MB L3 cache) (SKU – X2N170)*
 * - Ram: 8GB Kingston HyperX DDR3 1600MHz CL9 Dual Channel Memory (2x4GB SODIMMS) (SKU - X4N212)*
 * - Sound Card: Sound Blaster Compatible 3D Audio - Included*
 * - Spare AC Adapter: No Spare AC Adapter*
 * - Thermal Compound: Stock OEM Thermal Compound ( IC Diamond Thermal Compound - CPU + GPU Provided** FREE** with Processor Upgrade!)*
 * - TV Tuner: No TV Tuner*
 * - Wireless Network: Bigfoot Networks Killer™ Wireless-N 1102 (2x2) (SKU - X8R051)*
 * - Wireless Network Accessories: No Network Accessory*[/TD]
[/TR]
[/TABLE]

---

### Post by gordintoronto on 2013-06-04
Can you boot from a LiveCD or LiveUSB?

At what point does the "low graphics mode" error appear?

I have no experience with Optimus technology, but I suggest it's a good term to use when you use Google to try to find the solution.

---

