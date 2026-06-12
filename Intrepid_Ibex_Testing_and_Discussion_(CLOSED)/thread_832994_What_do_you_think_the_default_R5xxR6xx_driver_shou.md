---
title: "What do you think the default R5xx/R6xx driver should be?"
date: 2008-06-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Game_boy on 2008-06-18
There are three drivers for ATI Radeon R500 and R600 based cards cards with 3D support on Ubuntu.

--

fglrx is the binary, officially supported driver which is suggested by Ubuntu to users on first boot (as a restricted driver).

ati/radeon is the open-source default Ubuntu driver. The Hardy version doesn't support 3D on R5xx/R6xx. It is independently maintained by the community.

radeonhd is the newest driver. It is developed by people who work outside but are paid by AMD, as well as developers from the the community. It shares the 3D component with ati/radeon but has different features in most other areas.

--

Now that all three drivers have 3D support (which is continually improving), which of ati/radeon and radeonhd should be the default for R5xx and R6xx cards in Ubuntu, and should fglrx continue to be suggested by the Restricted Drivers Manager if both of the open-source drivers support 3D and Compiz stably by the time Intrepid freezes?

---

### Post by Eclipse. on 2008-06-18
If 3d open source support is stable then I would presume it will be chosen over propriety.

I dont really know what state the three drivers are in however.Never use ATI in my life and dont plan too.:P

---

### Post by eeclark on 2008-06-18
current fglrx driver is not working for me in Intrepid. Using the xorg-driver-fglrx from the repo.  Giving me a white screen.
With that being said...back to the question...
I think the criteria should be whichever one supports the widest range of cards.

---

### Post by gradedcheese on 2008-06-18
I have been using radeonhd from git and it works well enough.  There are occasional issues like cursor corruption but they seem to be rarer now (or have been fixed).  It definitely doesn't crash anymore.  I'll take a proper open source driver like this one without 3D over the fglrx blob any day, however radeonhd currently doesn't do any power management so the chipset's fan is likely to be on all the time, etc.  Until power management is implemented, it's probably not safe to have this as the default driver.  Then again, it beats just using vesa-fb and not getting any 2D acceleration.

---

### Post by syxbit on 2008-06-18
agreed. I won't use ATI until the RadeonHD driver is mature, stable, and works with all Radeon cards

---

### Post by Amaranth on 2008-06-18
I don't really see the point of the RadeonHD driver. The radeon driver gets support for new cards faster thanks to their use of AtomBIOS and has the codebase for the older cards to draw on for the newer cards. For example, the r500 cards are very similar to the r300 and r400 cards so it is much less work to get support for them. This is why the radeon driver supports compiz and everything with the r500 and (last time I checked) the RadeonHD driver almost had glxgears working.

---

### Post by Game_boy on 2008-06-19
> **Amaranth said:**
> I don't really see the point of the RadeonHD driver. The radeon driver gets support for new cards faster thanks to their use of AtomBIOS and has the codebase for the older cards to draw on for the newer cards. For example, the r500 cards are very similar to the r300 and r400 cards so it is much less work to get support for them. This is why the radeon driver supports compiz and everything with the r500 and (last time I checked) the RadeonHD driver almost had glxgears working.

It's partially AMD funded, unlike ati/radeon.

---

### Post by Amaranth on 2008-06-19
One of the radeon developers works for AMD...

---

### Post by NLS___87 on 2008-06-28
> **Amaranth said:**
> I don't really see the point of the RadeonHD driver. The radeon driver gets support for new cards faster thanks to their use of AtomBIOS and has the codebase for the older cards to draw on for the newer cards. For example, the r500 cards are very similar to the r300 and r400 cards so it is much less work to get support for them. This is why the radeon driver supports compiz and everything with the r500 and (last time I checked) the RadeonHD driver almost had glxgears working.

You would if you had an RV670 before others drivers supported it.

In fact, [FONT="Courier New"]radeonhd [/FONT]was the only driver supporting RV670 back then, long way before [FONT="Courier New"]fglrx[/FONT].

I think [FONT="Courier New"]radeonhd [/FONT]should be the default, as it's free enough to debian pick it and because DRI is in the way.

[FONT="Courier New"]radeonhd[/FONT] is a first-quality driver.

---

### Post by Amaranth on 2008-06-28
Yet the radeon driver has proven its worth by being the first to support r500 3d and supporting new ATI cards the day they are released.

The radeon driver supports everything the radeonhd driver does plus support for older cards, r500 3d, and quick support (at least for 2d) for new cards.

I really see no reason to use the radeonhd driver, it just has no use.

---

### Post by Sand Lee on 2008-06-28
For those of you who do not know the difference between the two, see this Phoronix article: [AtomBIOS Radeon vs. RadeonHD Drivers?]("http://www.phoronix.com/scan.php?page=news_item&px=NjMwOA")

From what I gather, the main difference is that the radeon driver uses AtomBIOS and bytecode to add support for new hardware. Radeonhd developers argue that such software is dangerous as it flashes the gfx's ROM and that ATI is against it. 

Radeonhd developers believe that using register information is the best way to go about the situation and that a new codebase would be more "hackable" and maintainable in the future. Radeonhd devs are supported by ATI and Novell, while radeon devs are backed by Red Hat.

I apologize if I made any mistake in the above information, but reading from both sides, I'd have to put my support behind the radeonhd developers. =D>

---

### Post by Amaranth on 2008-06-28
No, you do _not_ flash the ROM and the fglrx driver actually uses AtomBIOS, as does their windows driver. At this point I would say the AMD folks want Novell to use the register info directly because they want the driver to suck and fail.

However, that doesn't really fit since one of the main radeon developers works for AMD now.

So almost everything you said was wrong. :)

I have seen nothing to suggest the code already in the radeon driver is holding back development there but plenty of examples of it helping (r500 3d, rs690 3d).

---

### Post by Sand Lee on 2008-06-28
From a radeonhd developer's blog on the subject:> At no point do AtomBIOS functions come close to fitting the definition of script, at least not as we get them. It might start life as "scripts", but what we get is the bytecode, stuck into the ROM of our graphics cards or our mainboard.

The tools to generate this bytecode can now of course be written, but such tools are currently not available, nor is anybody planning on writing them. There are also no tools to replace functions in our existing vga BIOS images, or tools to generate brand new images. But none of this matters as ATI doesn't want us to flash our graphics cards ROMs in the first place."
If that doesn't mean radeon's implementation of AtomBIOS flashes the hardware, then what does it mean?
Also I would imagine nothing wrong with fglrx using AtomBIOS as they are the ones how make the cards - and I don't believe the AtomBIOS is configured the same way in both drivers.

> **Amaranth said:**
> 
So almost everything you said was wrong. :)


I'd hardly consider *possibly* getting one fact out of four points misconstrued as "almost everything."

---

### Post by Amaranth on 2008-06-29
They don't flash the BIOS, they use the AtomBIOS "scripts/bytecode" already there. Also, the radeon driver is backed by AMD and Red Hat. Also, the code in the radeon driver has proven to be useful, not a burden.

By the way, I'm pretty sure 2d acceleration in radeonhd actually came from the radeon driver. Just something to think about...

---

### Post by Sand Lee on 2008-06-29
> **Amaranth said:**
> They don't flash the BIOS, they use the AtomBIOS "scripts/bytecode" already there. 

OK. Though, it still seems that such code is dangerous, [from libv's blog]("http://libv.livejournal.com/15571.html?thread=74963#t74963"):
> It's only when I started working on embedded hardware I realized how unnecessary such proprietary bytecode layer is. suspending peripherals from their drivers is really simple to do, much more so than trying to get buggy vendor-provided bytecode to execute correctly in a enviroinment it was not meant to be run in (hw vendor only tests windows).  

> **Amaranth said:**
> Also, the radeon driver is backed by AMD and Red Hat.

I've read that an radeon developer works for ATI, but not the entire company backing the driver itself. But I guess if we can say that a company is backing a driver as result of the company's developer working on it, then it would be fair to say that the radeon driver is backed by ATI as people would say the radeon driver is backed by Red Hat. It would appear as a wasted effort for AMD to "back" the radeon driver and hire radeonhd developers that believe the radeon driver is going about the situation the wrong way.[URL="http://lists.opensuse.org/radeonhd/2008-01/msg00203.html"] An OpenSuse Mailinglist thread on the subject.
[/URL]

> **Amaranth said:**
> Also, the code in the radeon driver has proven to be useful, not a burden.

By the way, I'm pretty sure 2d acceleration in radeonhd actually came from the radeon driver. Just something to think about...

I never said radeon driver code was worthless, and yes radeonhd does reuse 2D code from radeon.. 
> 
I am working on integrating r5xx 2D acceleration and drm support from
-ati into radeonhd. Doing this in a clean and modular fashion is proving
more work than originally expected, but the result is starting to look
real nice and really hackable.

But don't forget radeon used radeonhd code as well:
> 
The R5xx and R6xx support in radeon is purely a private project of two
people, redhat's Dave Airlie and ATIs Alex Deucher. This started in
november, and copied a lot of radeonhd code.

---

### Post by Amaranth on 2008-07-01
Again, you have two drivers:[list]
[*]one supports every radeon from r100 to r600, one supports only r500 and r600
[*]one supports basic 2d on new cards within days, one takes up to months
[*]one is quickly gaining support for 2d and 3d acceleration on r500 and r600, one is still working on 2d acceleration and has a little 3d support
[*]one uses the same setup as the fglrx and windows drivers that are well tested, the other tries to manually do all of this work and most likely has diferences that are less tested
[*]one has developers from AMD and RedHat, the other has developers from Novell paid by AMD (although this point is worthless anyway, who cares what company is behind it if it works?)
[/list]

I'm not going to post in this thread anymore, people seem to be clinging to the RadeonHD driver because it's shiny and new and hyped and not for any technical reason.

---

### Post by Sand Lee on 2008-07-04
Looks like the radeonHD driver is going to use [AtomBIOS.]("http://www.phoronix.com/scan.php?page=article&item=radeonhd_atombios&num=1") With more cooperation, it seems users won't have to manually choose a default driver after all... 
Hopefully things will end up like Compiz and Beryl - yay for cooperation!!\\:D/

---

### Post by zoodayz on 2008-07-04
I would say anyone that has the largest support.  And that dont include RadeonHD.  I have a Ati 3200HD Chip that is no where on that list. here [http://wiki.x.org/wiki/radeonhd#head-cc89624fd96105127892119323e209b3d80e137d]("http://wiki.x.org/wiki/radeonhd#head-cc89624fd96105127892119323e209b3d80e137d") 
In less I missed something here? so from my stand point there would go a default install ubuntu for my spider platform.  Oh forgott to say now that fglrx is open now right?  Then I would say fglrx.  just my 2 cents.  Oh wait from wiki fglrx "It contains free open source as well as proprietary and closed source" Is that true I thougt it went open? No?  well if thats the case I dont see that being a default install. No? I know this is not Fedora but Ubutu but have I missed much in that last few years?  Sorry to hijack. ZoodayZ

---

