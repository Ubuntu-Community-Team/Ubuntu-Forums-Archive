---
title: "Shuttle XPC SS51G version 1, SUPER slow problems booting, installing, and using"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by LazerTag on 2007-05-21
Hi, I'm new to the forums as a poster, but been reading for quite some time.

I've recently hit a huge snag on an old box I have that I decided to go all Ubuntu with.  First the machine specs

Shuttle XPC SS51G version 1 (latest BIOS firmware)
P4 3Ghz Northwood
1 gig Crucial PC3200
ATI 9800 Pro AGP
120gig Maxtor IDE
DVD-ROM drive


Problem I am running into, when booting from the Ubuntu 7.04 LIVE or alt x86 the system is really slow to bootup.  I mean literally 10 to 20 minutes (I never clocked it).  I was able to do a full install (took nearly a whole day, no kidding) without making any changes (hardware wise or boot arguments) and everything seems to work fine just freaking slow as can be.  And it's not like the video is hindering it (you know you usually can kind of tell when it's that).  It's almost like my nice little P4 system is at best running like a PII of some sort.

I've tested the RAM and HD.  I 've tried replacing the RAM with two other sets I have (another 1gig Crucial set and an off brand set of 512meg).  I've also dropped another DVD-ROM, CD-ROM and 80gig Hd in just to make sure it wasn't any of those.  I tried using an older Nvidia 256 AGP card and ATI PCI card in the box as well.  No matter what so far it acts the same way.

I've also gone as far as futzing around with turning off and unplugging all unneeded devices, LPT port, COM ports, USB ports and removed devices, turned off floppy and second IDE.  I also tried putting the DVD drive and HD each on thier own IDE controller at one point.  Same speed issue.

I've also tried all sorts of settings in the BIOS with no luck.

The odd part of all this is I can do an install XP Pro in 40 minutes or less (pretty normal) and my original 80gig HD is already installed with XP Pro at this point and running totally normal in that system.  Been that way for many months.

I'm at a loss on this one.  Not an expert per say, but I work in the industry and usually if I don't know it doesn't take to much searching forums or Googling to find the answer.  This one has me baffled.  I do have three items I plan to try tonight.

1) Turn off the NIC interface and try without it.

2) I am using a wireless kb and mouse setup, however it's the type that plugs in to the PS2 ports and requires no additional software.  However now a co-worker has me wondering if this could be it.

3) Download OpenSuse 10.2 and see if it's effected in the same fashion.

Any suggestions are welcome.  All the searches I've done only turn up other peeps using this same rig without an issue.  Maybe they used an alternate kernel?? or something??


Thanks for reading!

LazerTag

---

### Post by LazerTag on 2007-05-22
So this morning I tried some other items

1) unplugging the NIC (I don't see any BIOS selection to actually disable that)
2) a wired keyboard
3) tried adjusting various BIOS settings related to interrupts for all PCI bus components
4) Open SUSE 10.2

All with no change, even Open SUSE!!!  So then I ran off and grabbed an old Knoppix 3.7 CD I had laying around and it booted pretty quick for the most part.  I think I'm on to something, but not sure what?  I tried Ubuntu 6.10 and Fedora Core 5, both slow.

Does any of this make sense at all?

I'm tearing my hair out trying to figure this one out.  I so want to get Ubuntu running on this system.

As always any help is appreciated.

Thanks!

LazerTag

---

### Post by LazerTag on 2007-05-31
I'm still looking for some help on this.  In the meantime I have installed Windows MCE 2005 that I bought with a hardware purchase.  It installed and is flying like normal on this same Shuttle XPC.  Heck even getting my stupid ATI HDTV card working went fine.  This is beyond aggravating.

Can anyone recommend other Ubuntu/Linux forums I might try posting this on?


Thanks

---

