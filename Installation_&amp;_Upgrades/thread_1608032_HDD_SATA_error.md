---
title: "HDD SATA error"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by adriankoooo on 2010-10-28
Setup: Asrock A330ION
HDD: Samsung HD154UI 1.5TB

Sometimes the problem lock my system. :(

Here is the kern.log:

[http://pastebin.com/U7d0Jf7g](http://pastebin.com/U7d0Jf7g)

What can be the problem?

I tried to change the sata cable, the PSU, but not helped.

---

### Post by sikander3786 on 2010-10-28
How many Sata controllers are there on your motherboard? If more than one, try with the other one and hopefully it should be solved. Linux doesn't like some newer controllers yet.

---

### Post by adriankoooo on 2010-10-28
I have only one, what is on the mobo.

nVidia chipset

---

### Post by darkhelmetchris on 2010-10-28
I experienced something  similar recently, if not exactly the same problem you're having.

I see in your log that the SATA link rate is fluctuating between 1.5 Gbps and 3.0 Gbps.  This is probably either that you have a faulty cable, or that the controller on your hard disk is faulty or not designed to operate at one of these speeds.

The first and least expensive thing would be to try another SATA cable.  You could be experiencing interference or the cable may actually be faulty.  Try a shielded cable - you can get one that has transparent plastic, and you should see foil-covered cable inside the cable sheathing.

When I had this problem, it was a bad SATA controller.  I flashed the controller on the SATA card with a new firmware (using FreeDOS and the manufacturer's firmware update). Since you say yours is on the mainboard, I would then suggest flashing your BIOS as this might help Ubuntu more clearly identify your hardware.  I would also suggest, if you have the option, to try a SATA daughter card and see if your problem remains or goes away.  If the problem persists, you probably have a faulty hard disk controller, and if it goes away, you probably have a faulty mainboard SATA controller.

---

### Post by adriankoooo on 2010-10-28
Thank you for the reply, darkhelmetchris.

1, I already tried 4 cable, not helped :(
2, I tried all sata plug on the mobo, not helped

Samsung.com:

EcoGreen F2 
Capacity: 1.5 TB 
[B]Interface: SATA 3.0 Gbps 
[/B]Buffer memory: 32 MB

Is there exist any LOW PROFILE PCI Sata controller (I have mini-itx case, it is a HTPC)?

I have latest BIOS installed.

---

### Post by darkhelmetchris on 2010-10-28
> **adriankoooo said:**
> Thank you for the reply, darkhelmetchris.

1, I already tried 4 cable, not helped :(
2, I tried all sata plug on the mobo, not helped

Samsung.com:

EcoGreen F2 
Capacity: 1.5 TB 
[B]Interface: SATA 3.0 Gbps 
[/B]Buffer memory: 32 MB

Is there exist any LOW PROFILE PCI Sata controller (I have mini-itx case, it is a HTPC)?

I have latest BIOS installed.

Sorry to hear about your on-going troubles.  Yes, there should be low-priced SATA controllers around.  The last one I picked up was about $30 cdn.  It was a SATA raid controller, but they usually work well even if you're not using them for raid.  Linux usually understands them and enumerates the drive as single.  I find it very handy to have one spare SATA raid card around, for data recovery and backups when an older PC doesn't have SATA on-board.  It's a cheap way to get fast data transfer on older systems.

I have one machine here that is Mini-ITX also, and the case is nice and small, so I understand your need for space.  The cards are usually very short, so it *should fit, just be a little picky when you buy your card; check the size in the store and decide if it's going to fit your case.

Something else comes to mind.  Before you spend your cash, since it's Linux anyway, see if you can pop the drive into another machine.  As I suggested before, this would tell you if you're leaving the problem on the original mainboard, or taking the problem with you on the hard disk's controller.

And.. as much as I really DO hate to suggest it - you *could pick up and external hard disk case and go USB.  (Perhaps get one that maybe has USB and eSATA on it).  For a HTPC, it might even be convenient to have the drive external.  Just a thought, and I know it's icky, so please don't shoot me for the suggestion.

Also, you might try forcing the mainboard SATA controller to run at 1.5 Gbps - you'll probably still get acceptable happy performance.  I am a little unsure how to do that, but I know it's possible - perhaps with hdparm?  I will look into that.

---

### Post by darkhelmetchris on 2010-10-28
Okay, some searching got me this result.  I have NOT tested it myself, but it looks like the way to go.

Add the following to your boot options:
libata.force=1.5

If you add that to your kernel parameters in your grub config, that should force your controller to stay in 1.5 Gbps mode, and not fluctuate.

---

### Post by adriankoooo on 2010-10-29
Thanks for trying to help me, but the problem was the BIOS. I flashed back the older one, and it is looks now OK, no error message.

Asrock A330ION BIOS 1.40 is not linux compatible (<-for Google)

I contacted with Asrock support team.
:guitar:

---

### Post by darkhelmetchris on 2010-10-29
Hey, that's good news.  I'm glad to hear you got it worked out.

---

