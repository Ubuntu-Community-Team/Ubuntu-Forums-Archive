---
title: "No hair left - green install"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by vmweenie on 2008-03-10
Tale of woe follows below. First the facts maam, just the facts. 

Buiilt new system: Asus M2A-VM (with HDMI but not "model HDMI")AMD 690G chipset, AMD 64 X2 4400+, Pioneer SATA  CD/DVD R/W on SATA 0, Maxtor IDE 500G on IDE.   

My working system is HP Digital Entertainment Center under XP. Target system has yet to have a successfuil OS install. 

Haven't done Linux in years, but I was a 4.3 BSD guru way back in *cough* *cough* and played with Red Hat in 19*hrmph*chrp*.   Burned my CD images this past week. 

Mobo, case, chip,HD, CD/DVD new out of the box (all bought as components).   Tried Ubunto 7.10 OEM install, safe graphics mode install, etc etc.  At some (seemingly random) point it just hangs. Need to hard power cycle.   Tried Fedora 8 LiveCD install.  Everything just hangs at some point.  Though in both cases, I CAN run from the CD just fine! 

I'm installing 32 bit systems, not 64 bit.  I CAN boot RescueCD and get a system runnning,  I CAN make partitions (parted), file systems (mkfs), etc.  But no install works. AND... If I run aida and after the first CPU test, it says "...DETECTING..."  Forever.  OTOH, memtest works fine.  Various utils work fine. 

Removed 802.11 adaptor, have bare bones system.  Updated BIOS to latest (burned freedos bootable CD - fun!)  Still no go.  Both Ubuntu and Fedora just hang after a bit.  I did notice last time there were some "pixel artifacts" - like a spray of bad pixels across the screen when Fedora halted. 

What else can I say?  (Aside from HELP PLEASE!eleven!!tyone!!   :-)  

Found some references to needing kernel 2.6.20+, and references to problems with ATI grfaix. They seem to be older, fixed(?) bugs. 

Thanks for any help.  
Peter 



The promised TALE of WOE: 

Bought everything at Fry's.  First chip OR mobo bricked the other.  Well, not bricked exactly. First POST okay.  System runs for a bit.  Then crashes. Hmm....memory ptroblem? Run memtest, it crashes. Okay, let's get a new 1G stick. Hmmm, old stick checks out okay. Fine, I'll fight the traffic (I-5 has a 10 mile long traffic jam) to go home and and bring the mobo and chip back.  First look says everything OK.  Oops, second POST show a problem.  Etc Etc Etc finally we figure both chip and mobo are hosed.  Much anguish ensues.   I leave with new mobo, new chip (after laying out quite a few more $$$ than I had originally as THAT chip no longer available).  

Back to square one.  That was two days ago.  I STILL haven't been able to get an OS onto this pig.  

Oh - I forgot:  I had donated some old parts (cases, mobos, systems, etc.) to FreeGeek when I decided to just go ahead and buy new everything.  OOPS!  Left the new 500G drive in a donated machine.  There went a day just trying to recover that. 

ARGHARHGGRZHAHGARHGH.

---

### Post by chewearn on 2008-03-11
I read your post carefully; I didn't find a mention of whether you tested the LiveCD burn, via the "Check CD for defects" option of the boot menu.

I thought I would mention it, just so to get it out of the way.

---

### Post by vmweenie on 2008-03-12
Thanks for the response.  I got distracted from this project for a few days but here I am again.  (lLike a bad penny) 

I had in fact run the CD check, it was ok.  My bad for not saying so.   I found some other people with problems (at Asus forum) but nothing there helped so I'm alone in the wilderness again. 

I managed to put XP (v 2002) on the machine and it's fine (as far as XP can be 'fine') and have two HDs to play around with.  I'm now ruling out flaky hardware.  

So I've been doing attempt after attempt trying to nail down exact sysmptoms.  Each time I carefully watch the "install" (whether Ubuntu 7.10 or Fedora) , I notice some odd things on screen:
1. A "shadow" bar near the yellow-gold yo-yo thing in the center.  Doesn't always appear and exact position varies.
2. What looks like an off-color, compressed and tiled version of the Asus BIOS splash  screen across the top of ther screen  Hard to tell on this, it's very brief and only occupies the top 70 or so lines.  
3. That Matrix effect, random columns of randomly distributed (usually green ) pixels "splashed" across the screen.   Again, don't always get it, and the color varies. 
4. In every case, end result is same: system lockup requiring power cycle.  

It's the darned irreproducibility that I can't stand!   When debugging new boards we call that sort of thing "a loose disconnection."  :rolleyes:

In any case, I now have an OS (on an old 20G disk) and net connectivity to the machine.  What's the best way to go from here?  I'm not averse to building various flavors (different drivers, etc)

Does Cygwin let me cross build to Linux/x86 on a Win machine? (used it before but always for Win/x86 target) 

Let me guess: I'm making it much too complicated, aren't I?

---

### Post by Shazaam on 2008-03-12
Two questions-
1. Are you using on-board graphics or a dedicated Video card?
2. Where did you get your version of Ubuntu?

If all else fails try the "alternate desktop cd" version.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

(under the green Start Download button)

---

### Post by vmweenie on 2008-03-12
1.  On-board ATI X1250 video 
2. Got it from that URL.  Last week.  


I'm going to try the alternate CD now.   I'll keep you posted.

Thanks! 

> **Shazaam said:**
> Two questions-
1. Are you using on-board graphics or a dedicated Video card?
2. Where did you get your version of Ubuntu?

If all else fails try the "alternate desktop cd" version.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

(under the green Start Download button)

---

### Post by egalvan on 2008-03-13
> I managed to put XP ... it's fine (as far as XP can be 'fine') .... I'm now ruling out flaky hardware.

Don't let a "good" Windows install fool you.

I have had bad cables and bad RAM cause Linux installs to :confused:  :mad:

while Windows 2k and XP both just  :)  :lolflag:

---

### Post by vmweenie on 2008-03-13
Yes, you're right; I may have been premature.   I had started thinking that XP, especially  6 year old disk, isn't going to exercise the hardware, not much.  Youv'e confirmed it for me, thanks. 

Tried OEM install from the alternate CD.  Made great progress, halfway through "copying OpenOffice" or whatever, don't recall the exact message, dead in the water again.  

Let's see: I put the 500G IDE Maxtor in an external USB housing but installed Win to an old 20 GB IDE disk on IDE 0.  That would seem to rule out a bad IDE cable, right?  Could there be something flaky with the Maxtor disk?  Seems very odd but I dunno.  (I've been doing embedded work, microcontrollers mostly for  the last fifteen years - I hardly know what'a "hard disk" is) 

I'll run memtest (again) ...okay, 5 passes seems good.  It aint RAM.  It aint a bad IDE cable.  Now trying install in text mode.... 

Thanks to all for your pointers.  I'll post results later. 


> **egalvan said:**
> Don't let a "good" Windows install fool you.

I have had bad cables and bad RAM cause Linux installs to :confused:  :mad:

while Windows 2k and XP both just  :)  :lolflag:

---

### Post by vmweenie on 2008-03-13
Ubuntu 7.10 64 bit system running. [falls to knees and gasps] 

boot flags(gleaned from various archives and places) that other people have reported success with: 
'irqpoll pci=nomsi noapic acpi=off nomce" 

I'll play around and figure out what proper subset, if any, is actually needed.   I'll start a new thread on this board/chip combo when/if I figure that out.  

Thanks to all.

---

### Post by rfruth on 2008-03-13
It must have been asked / answered b4 but live CD ok -  So hardware or software problem (hard to tell I know) leave at BIOS screen (or live CD = better) all night if need be, rock solid :confused:

---

### Post by egalvan on 2008-03-14
> **vmweenie said:**
> ... isn't going to exercise the hardware, not much.  Youv'e confirmed it for me, thanks.  

Actually, I think it´s more a function of Windows not KNOWING or CARING if the bits don´t come out right.
 After all, if Windows DIDN´T stress the hardware, then VISTA would fly. :)


> **vmweenie said:**
> 
... 500G IDE Maxtor .... old 20 GB IDE ...  rule out a bad IDE cable, right?


OK, since you don´t seem to *  hardly  know what a hard disk*  is :-k , maybe you haven´t meet the right cable.
Are you using a 40-wire or 80-wire?  (n.b. I said WIRE not PIN. All IDE cables are 40PIN)
Older drives (up to ATA33 used 40pin-40wire cables, and they were happy...
Newer drives, ATA66 and up, won´t work reliably with these older cables, and many  throttle down  to ATA33 or ATA16 speed to keep errors to a minimum.
 They NEED 40pin-80wire cables. Make sure you use them. 


> **vmweenie said:**
>   Could there be something flaky with the Maxtor disk?  Seems very odd but I dunno.  *- I hardly know what'a "hard disk" *is :-k  ) 

Just ´cause it´s new, don´t mean it´s GOOD and new. Run diags on it, save headaches later on.


> **vmweenie said:**
> 
I'll run memtest (again) ...okay, 5 passes seems good.  It aint RAM.  It aint a bad IDE cable.  Now trying install in text mode.... 

Thanks to all for your pointers.  I'll post results later.

I run a new RAM set-up AT LEAST over-night (12-hours), and for my home server, I always run the mobo/RAM a week.
 Of course, that setup gets updated only every year or two...and that´s just me.
Most folks don´t need that extreme.

Get memtest running, then go jogging or movies or dinner or shopping.... 

And keep us up updated....please. The Ubunut community needs this info.
:popcorn:

---

### Post by vmweenie on 2008-03-14
> It must have been asked / answered b4 but live CD ok - So hardware or software problem (hard to tell I know) leave at BIOS screen (or live CD = better) all night if need be, rock solid  

I think you mean just see if it can keep doing nothing all night without crashing?   I did let Win run overnight.   And yes, checked the CD - it was ok.  But I've got everything working now. Sort of.  


> **egalvan said:**
> Actually, I think it´s more a function of Windows not KNOWING or CARING if the bits don´t come out right.
 After all, if Windows DIDN´T stress the hardware, then VISTA would fly. :)  

Now now, be nice. 
> 
OK, since you don´t seem to *  hardly  know what a hard disk*  is :-k , maybe you haven´t meet the right cable.
Are you using a 40-wire or 80-wire?  (n.b. I said WIRE not PIN. All IDE cables are 40PIN)
Older drives (up to ATA33 used 40pin-40wire cables, and they were happy...
Newer drives, ATA66 and up, won´t work reliably with these older cables, and many  throttle down  to ATA33 or ATA16 speed to keep errors to a minimum.
 They NEED 40pin-80wire cables. Make sure you use them. 
 
Yep, 80 wire cable.  Being an engineer, I noticed the difference between the cable Maxtor included and the old one I pulled out of a parts drawer and googled it. Right you are. 

>  Just ´cause it´s new, don´t mean it´s GOOD and new. Run diags on it, save headaches later on. 

That's a great idea. Is there a sticky somewhere on how to bring up a green machine or how to test new hardware before committing it to your system?   There ought to be.  A tool kit or guide at least. I'd be happy to contribute to one. 

Anyway, I did try to do diagnostics on the system by running 'aida' from rescueCD but it kept crashing.  There doesn't seem to be much detailed info about aida so I finally gave that up.  Which gets me thinking about another project that might be really really useful....  

> And keep us updated....please. The Ubunut community needs this info.
:popcorn:

I'm happy to - makes me feel useful. :cool:  So now I'm running (mostly - working on bringing up a Realtek WiFi card) and spent some more time researching.   There seems to be a lot written about ACPI problems so I'll focus on that first.   Maybe try booting the LiveCD with various params then  "installing."  This may take a while -----

---

### Post by vmweenie on 2008-03-17
Okay.  After spending (and when I say 'spending' I mean wasting) two days trying to get my WiF working (ndiswrapper, loading modules, blacklisting,etc...)  I finally figured out I had mistyped my network name. :mad: Thank you sir may I have another. 


Minimal subset of boot params that works without fail is acpi=off.  Fedora 8 and Gutsy Gibbon both work with acpi=off on this Asus board.   I suspect that's why I have to manually power off?  I'll look into the other options <noirq ht strict>  and experiment.  

Film at eleven.

---

### Post by egalvan on 2008-03-17
> **vmweenie said:**
> Okay.  (and when I say 'spending' I mean wasting) two days trying   I finally figured out .....

*FINALLY FIGURING IT OUT*  means the time *_was not wasted.._*.. mis-directed, mis-guided, mis-intended maybe, but not wasted. This is a valuable learning experience, and please don't ask *me* how I know about mis-spelled words/commands...:lolflag:

> **vmweenie said:**
> 
Minimal subset of boot params that *_works without fail is acpi=off_*.  Fedora 8 and Gutsy Gibbon both work with acpi=off on this Asus board.   I suspect that's why I have to manually power off?  I'll look into the other options <noirq ht strict>  and experiment.  

Film at eleven.

SEE??? You have attained great wisdom, Little Padawan. Experimentation is the spice of life.


And i case I didn't mention it before, verify your motherboard is using the latest BIOS. apci (& related) problems may disappear with an updated BIOS.

---

### Post by vmweenie on 2008-03-18
> **egalvan said:**
> mis-directed, mis-guided, mis-intended maybe, but not wasted. This is a valuable learning experience, and please don't ask *me* how I know about mis-spelled words/commands...:lolflag: 

Yeah, that's an old war story we old warriors have told many times.  Usually it's in the form of a question: "*How many times* have you spent two days trying to debug what turned out to be a typo?  And *how many times* did you **look right at it **before realizing it?"  ](*,)

> And i case I didn't mention it before, verify your motherboard is using the latest BIOS. apci (& related) problems may disappear with an updated BIOS.

Good point.  I'm using the latest _stable_ BIOS which, for the M2A-VM (and other Asus boards) is rev. 1603.  There is a rev. 1604 but as of last week it wasn't marked as stable. Have run across a LOT of people with ACPI problems, not just on the Asus boards.  So many it makes me think disabling ACPI maybe ought to be the default.  

Anyway, I'm still experimenting....

---

### Post by Green Tree Python on 2008-03-18
VM:

I have been researching all the different version of Ubuntu, including Kbuntu. I would try Ubuntu 7.04 (Feisty Fawn). Also, if you have any other questions theirs a site you can try [www.tuxfiles.com](www.tuxfiles.com), as well as this site. If you have any other question you can find me here.

Good luck,

GTP

---

