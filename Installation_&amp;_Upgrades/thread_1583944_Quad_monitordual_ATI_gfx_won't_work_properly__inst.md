---
title: "Quad monitor/dual ATI gfx won't work properly / install properly"
date: 2010-09-28
forum: Installation &amp; Upgrades
---

### Post by kalleth on 2010-09-28
I have a reasonably demanding set of system specifications:

[LIST]
[*]Core i7 920 @ 3.0ghz
[*]12gig ram
[*]Quad Monitors
[*]..powered by an ATI Radeon 5870 and an ATI 3400, not running in crossfire but running as seperate graphics cards
[/LIST]

It's the latter - two seperate graphics cards driving four monitors - that seems to be the issue with not just ubuntu but any linux distributions.

I checksummed all the images I downloaded.

None of the liveDVD's - first ubuntu, but also mint, fedora and suse - I tried would work. All hung.

The Ubuntu liveDVD got into the loading splash screen (~6 grey pips turning red), then the screen went black and the PC hung. Keyboard not responsive and machine not responding to ping. I assume this is about the point that X would start.

I managed, using the x64 ubuntu alternate install dvd, to install and get to a console. Attempting to start gdm/x would hang the machine.

I then manually downloaded (using wget) the ATI drivers from ati.amd.com and installed them from the command line. After doing this, I could get into a gnome desktop and configure my graphics card using the Catalyst Control Centre.

However, I could only manage a single graphics card - my 5800 - through this interface. I couldn't find anywhere that mentioned or let me configure more than 2 monitors - the ones that weren't connected to the 5870 but were connected to the 3400.

The graphics adapters were correctly detected by lspci.

I'm not in a position this week to investigate further, but I wondered if anyone could offer suggestions for things to try over the weekend when I attempt to install ubuntu again? I know it's more than likely an issue with ATI's proprietary drivers, but the non-proprietary ones X tried to use to start off with (whatever they were) it seems were what were causing X to crash.

---

### Post by Buntolo on 2011-01-27
The Linux graphic server, X, doesn't support multiple graphic card (only pure Crossfire/Sli, with 2 quite identical cards).

So you cannot use monitors attached to 3400.

[This guy](http://phoronix.com/forums/showthread.php?27922-2x-ATI-5670-amp-3-Monitors-How&highlight=eyefinity) have chosen eyefinity to use 3 monitors.

---

