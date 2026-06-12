---
title: "Question about bays and the number of devices that can be added"
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by ClientAlive on 2011-06-27
Other o/s because I plan to turn that machine into a Xen server.

Unfortunately I don't have much exper building computers/ hardware. What I'm wondering is whether the number of devices (like hard drives and optical drives, etc) is a function of what the mobo can support; or, if the bays are there and the cable has enough plugs I can just go for it.

Specifically I'm trying to have 3 disks and one optical drive. The machine happens to have been a media center version desktop so it has this like 9 in 1 card reader thing in it but I don't think it uses that flat cable for data transfer anyhow. It looks to be connected differently.

Any help would be greatly appreciated. Thank you.

---

### Post by dabl on 2011-06-27
Your motherboard and the chipset on it are the limiting factor on how many storage devices can be installed on it, subject of course to some physical place to sit them (in a case, hopefully).

If the motherboard was designed after about 2002, then it has a SATA interface, and some number of SATA connectors.  These are about 3/4 of an inch long, and "L" shaped. The number of SATA connectors is the limit on how many SATA devices you can connect -- once device per connector.

Until recent times most motherboards also had a IDE controller and interface -- usually a single connector.  This is a 40-pin "ribbon" cable connector, with a notch in the middle of one side.  The IDE interface can support two devices, commonly referred as "master" and "slave".  So if you have an IDE connector, you can have two IDE devices on the IDE ribbon cable (which needs two connectors installed on it, of course).

Hope that helps.

---

### Post by ClientAlive on 2011-06-27
> **dabl said:**
> Your motherboard and the chipset on it are the limiting factor on how many storage devices can be installed on it, subject of course to some physical place to sit them (in a case, hopefully).

If the motherboard was designed after about 2002, then it has a SATA interface, and some number of SATA connectors.  These are about 3/4 of an inch long, and "L" shaped. The number of SATA connectors is the limit on how many SATA devices you can connect -- once device per connector.

Until recent times most motherboards also had a IDE controller and interface -- usually a single connector.  This is a 40-pin "ribbon" cable connector, with a notch in the middle of one side.  The IDE interface can support two devices, commonly referred as "master" and "slave".  So if you have an IDE connector, you can have two IDE devices on the IDE ribbon cable (which needs two connectors installed on it, of course).

Hope that helps.


Yes, it does. Thank you. It's mostly older hardware but is a mixture of stuff from diff machines. All hard drives are ide and I think the optical drive is too. Sounds to me like I'm only gonna get 2 drives and the optical unless I go with external optical and use all 3 ide connections for the drives? I wonder if the mobo would allow something like that? Does it care what type of ide drive/ expect you to have one of them be an optical drive or something other than a hard drive??

Thanks
------------------------

I have 3 old computers sitting here in my living room with a combined total of=lots of stuff! I'm trying to figure out the best combination that will max me out on resources for what I have available. One is an old Gateway from like 1999. It's case is clearly different, it has more bays and drives already installed (like 4 of them) but it's processor is an old pentium II (uggg!). The one I have operational is an hp media center computer that's from like 2005. It's processor is an AMD 3400+ (oh the glory!!) - but it's case is a smaller case and it doesn't seem to support that number of drives. I have 3 ide drives: one is 100 gig, one is 80 gig, and the other is just under 20 gig. The 80 gig is a Western Digital Caviar. So that's like 200 gig - if I could find a way to make use of it all. Otherwise, I guess I'm down to 180 gig with the top two drive sizes.

But in it all, there's a completely different reason I wanted to have 3 drives in one machine. From what I can gather, running a Xen server involves several components (usually done by having multiple servers, each performing different functions within the system). Since I only have one working machine (or the parts to make one). I thought I could use each drive as though it were a separate server. To configure things that way I mean. One for a ticket server, one for Xen and one for content - somthing like that. Still learning about the whole Xen/ Server/ Configuration thing.
------------------------

Edit 2:

Can't I just find an ide cable that has 4 plugs on it and use that one?

---

### Post by tgalati4 on 2011-06-27
IDE cables can only support 2 hard disks (or CD/DVD devices) at a time.  Your card reader is probably connected to an internal USB port (4 wires).  You can buy SATA with IDE PCI cards cheaply and that will allow you to hook up additional IDE and SATA drives.

If you are going to run multiple virtual machines under Xen, then you will need lots of RAM--perhaps more than your old machine can handle.

---

### Post by ClientAlive on 2011-06-27
> **tgalati4 said:**
> IDE cables can only support 2 hard disks (or CD/DVD devices) at a time.  Your card reader is probably connected to an internal USB port (4 wires).  You can buy SATA with IDE PCI cards cheaply and that will allow you to hook up additional IDE and SATA drives.

If you are going to run multiple virtual machines under Xen, then you will need lots of RAM--perhaps more than your old machine can handle.


Ok. Thanks.

---

### Post by oldfred on 2011-06-28
You also need to check power supply. Often prebuilt brand name systems put in the smallest power supply they could to save money. I put a newer video card in and in just a few months blew the whole thing up. Power supply was border line & video card drew a lot of power and this was 4 or more years ago. Now the new devices draw even more power.

Do not mix 40 conductor IDE cables that need master/slave jumpers on the hard drive and the newer 80 conductor cable select IDE where the jumper on the drive is set to cable select. Most CD/DVD that were IDE used just the 40 conductor cable.

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by ClientAlive on 2011-06-28
> **oldfred said:**
> You also need to check power supply. Often prebuilt brand name systems put in the smallest power supply they could to save money. I put a newer video card in and in just a few months blew the whole thing up. Power supply was border line & video card drew a lot of power and this was 4 or more years ago. Now the new devices draw even more power.

Do not mix 40 conductor IDE cables that need master/slave jumpers on the hard drive and the newer 80 conductor cable select IDE where the jumper on the drive is set to cable select. Most CD/DVD that were IDE used just the 40 conductor cable.

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

Well . . . I wasn't really thinking about it anymore but now you've really got me thinking about a lot of things:

1> I was reading that wiki article at the first link and it talked about there being more than one ATA on the mobo - so I got to looking inside the case and on my mobo. Well, there is two, errr . . . ATA? slots on there. And there's two ribbon type cables connected (both slots are used/ taken). But here's the thing. One cable has a grand total of 3 plugs = the plug connected to the mobo, a plug in the middle of the cable and a plug at the other end (currently attached to one of those drives). The other cable only has a plug at either end. One attached to the mobo and one to this thing with . . . audio jacks and <sneering> usb slots. So anyway, I have a whole box full of cables sitting right next to me, including these ribbon type. Why not just swap out that one with only two plugs for another three plug cable? Viola! Now I have a grand total of four plugs between the two cables. Lol. I mean, why not. It would work right? Just pluger on in??

Truthfully though, that was part of my initial question. What the limiting factor is. Whether the mobo actually has to be able to recognize x number of devices or whether the mobo has nothing to do with it and you just plug in as much stuff as you can and that you can power.

2> I don't know how to tell whether its the 40 or 80 type cable. I'm sure I can google something if I had to though. *Edit: I'll keep looking at the links you gave - I'm sure that info is in one of them - sorry.

3> You mention something about jumpers but it sounded like it was in a different context than I'm used to. The only jumpers I knew of had to do with setting the drive as primary or secondary, not to do with the type of cable being used. Is there more than one place where jumpers are used? Where are these other jumpers you're talking about? On the mobo or something?

4> I don't know how to tell what the limits of the power supply are or how to figure it out. I do know there are extra, unused plugs on the cable though. Just that, that prob doesn't automatically mean the power supply can handle all the devices. (In other words, prob not the best way to gauge something like that - just because there's another plug there).
--------------------------

Edit:

Oh!! That's what those other, black plugs are - serial ATA. I have some of those in there too.

---

### Post by oldfred on 2011-06-28
Most IDE motherboard had two IDE channels. So one plug is primary and the other is secondary. Usually the first hard drive was on the primary and the CD drive was on the secondary. Then a second hard drive was a slave on the primary. Jumpers on drive are master, slave, cable select, and some may have a master with slave jumper.

Newer motherboards with SATA often only have one IDE connector for a CD/DVD drive. 

Links show examples. I tried using a cable from a CD drive in cable select and of course those were only 40 conductor.

I always had trouble with those little jumpers and now cannot even see them. As some as I could I started buying SATA drives and will not look back.:)

The power supply will have a label but you might have to remove it to see its wattage. I do not have links but several vendors had calculators for power. Video card again is the major issue. One power supply I bough had 3 16 amp sections, but video card wanted 20 amps. I was not sure it then it was large enough or not so I just went with a different model that was only slightly larger but had the 20 amps available.

---

### Post by ClientAlive on 2011-06-28
Well the PS looks like it says 300W but then there's other, finer details; and, now, we're getting into an area I have no clue about (electrical). The drives (1) and (2) seem to have two differing pieces of information both seen to say the same thing, and it's in volts. The third one (3) I can't find anything about power usage on it. Now I don't understand how electrical calculations work; and, to be honest, I have enough stuff I'm studying. I hope that doesn't sound bad, just there are some things I just wish someone who already knows would just help me with and not make me take a week to learn a figure out if they can just look at it and tell in two seconds.

So then you have other components that eat power too? Like maybe a NIC and a sound card and a video card. And how would I find out about them? I'd have to google the model and brand to try find a spec sheet?

Truthfully, I never thought it would get this complex. I had just planned to plug it all in and fire the sucker up - until you said something about, what was it, "burn the whole thing down"? Well I sure wouldn't want that. Just this is something I really don't find too thrilling - dealing with calculating power supplies and power usage. I just want to get on with using the thing.

Sorry, kinda bad attitude I guess - just kinda killed the thrill having to think of all this junk. I know it's important though. I can tell. I get that.
==============================

Edit:

There's a fourth drive sitting here too. It's prob at least 11 yrs old maybe 12 and it doesn't seem to say anything useful on it at all. I mean, there's a label, just doesn't tell you anything you'd want to know - like the size of the drive, for instance.

---

### Post by oldfred on 2011-06-28
Just plug all your planned devices into one of these if less than 300 watts you should be ok:

[http://educations.newegg.com/tool/psucalc/index.html](http://educations.newegg.com/tool/psucalc/index.html)

[http://www.antec.outervision.com/](http://www.antec.outervision.com/)

Google has many others under computer power supply calculators.:)

I find they seem somewhat low and I like to allow for future growth so I add a lot 50% or more. You can test sensitivity of choices by changing to a smaller or larger one to see how much more it changes total.

I really hated old drives like that. You have to have saved the instructions that came with the drive until Internet came along. Then you can look drive up to find jumper settings or other info.

---

### Post by ClientAlive on 2011-06-28
Right on, thanks. That psu calc thing tells me I need a larger power supply but I'm not sure I'm giving it totally accurate details. I'll have to run these tools I have to get the details they need and be sure.

So what it it that burns up if you over-load the psu? Just the psu itself, or can it damage components?

---

### Post by dabl on 2011-06-28
> **ClientAlive said:**
> 

So then you have other components that eat power too? Like maybe a NIC and a sound card and a video card. 

The CPU, GPU (video), memory, and drives are your main consumers of power -- you can safely disregard the other onboard components.  A 300 watt PSU should handle your AMD CPU and the the other modules of similar vintage.  Just don't try putting a fancy new graphics card into that rig.

If it were me, I would use the big old Gateway case, put the HP motherboard with the AMD CPU in it, and spend $50 for 3X the hard drive space that you are presently looking at:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136358](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136358)

You could use the MAXTOR IDE drive for backups, although that particular model runs hot and tends to die young.

[http://www.youtube.com/watch?v=tC7fkmymX6s](http://www.youtube.com/watch?v=tC7fkmymX6s)

You didn't say how much memory the HP motherboard has on it -- hopefully at least 2GB.

---

### Post by ClientAlive on 2011-06-28
> **dabl said:**
> The CPU, GPU (video), memory, and drives are your main consumers of power -- you can safely disregard the other onboard components.  A 300 watt PSU should handle your AMD CPU and the the other modules of similar vintage.  Just don't try putting a fancy new graphics card into that rig.

If it were me, I would use the big old Gateway case, put the HP motherboard with the AMD CPU in it, and spend $50 for 3X the hard drive space that you are presently looking at:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136358](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136358)

You could use the MAXTOR IDE drive for backups, although that particular model runs hot and tends to die young.

[http://www.youtube.com/watch?v=tC7fkmymX6s](http://www.youtube.com/watch?v=tC7fkmymX6s)

You didn't say how much memory the HP motherboard has on it -- hopefully at least 2GB.

I know drives are cheap these days but what I have is what I could beg or scrounge togethter. If it weren't for that I would have nothing at all. That 80 gig WD drive came out of an old computer (like from 1999) someone gave me because I posted on craigslist asking. It's embarrassing. I'm severely under employed and barely make ends meet so when I see people talking about $50 here and $100 there like it's just monopoly money it just kills me. This is why I spend every minute of my free time reading, practicing, learning about every computer technology thing I can get my hands on - that I think may make money. Maybe if I learn how to implement servers I can dig up some work and pull myself out of this hole. Maybe if I learn about cloud platforms and Xen servers I can pull myself out. Maybe if I . . . 

I'm sorry man, you didn't know. It's just very difficult for me to deal with right now. Nothing personal, ok?

Ram? it uses old ddr 533 mhz. It has two sticks of 256mb now and there are 4 slots on the board. I think, the board will support up to 4 gig - I think (or was it 2 gig). Someone I met on one of the forums, thank God, promised to send me a little extra ram for the thing (a gig) but I'm not sure if it will be 4x256 or 2x512 if it's the latter I'll end up with 1.5 gig total if it's the former I'll end up with 1 gig total.

I think the only card it has is a sound card. Ev else is on board. Well, I guess my room mate is an IBM certified engineer or something like that (I didn't know it until today). He looked at what I'm trying to do and assures me I'm fine - that the psu will handle it. I'm gonna roll with his advice. The two calculators I've used tell me I need 350/ 400W though - but I don't think I'm giving the correct info in them (either because it doesn't have a selection for my old, old components or because I don't know). So, yeah, I think I'll be golden.

Thanks for the great knowledge you've shared. You have no idea how much I appreciate it. Next time should be a cinch now.

Jake
:)

---

### Post by dabl on 2011-06-28
> **ClientAlive said:**
> 

I'm sorry man, you didn't know. It's just very difficult for me to deal with right now. Nothing personal, ok?



It's OK. I've been blessed, and I don't always remember how hard others must struggle.

For learning purposes, those old IDE drives are fine, and probably you can get it performing well enough with 1GB of memory to do your experimental setups with servers and Xen.  As soon as you can figure out a way to back up any important data that you put on it, you need to do that.  It might run fine for a few years, but it might not, so ....

For example, Ubuntu One gives you 2GB of storage space for free.  ;)

Good luck with it!  :guitar:

---

### Post by ClientAlive on 2011-06-28
> **dabl said:**
> 
Good luck with it!  :guitar:



Thanks dabl

---

