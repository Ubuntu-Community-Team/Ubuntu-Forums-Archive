---
title: "Resolution problem; Gutsy + GeForce 7200 GS (EVGA) + Mitsubishi WS-65813"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by MykeBuntu on 2008-03-18
Resolution problem; Gutsy + GeForce 7200 GS (EVGA) + Mitsubishi WS-65813 (rear projection hdtv circa 2004)

And thanks in advance if you actually drill through this novel and offer some advice; I am starting to think "I cannot get there from here".

Suffering a bit from information overload here; what direction should I take this? I've been completely unable to find any official source indicating the TVs "modeline" specs... but am not starting to think it could be an nvidia issue.

My background: Wintel, BuntuBeginner

Machine purpose: Run MythBuntu with an HdHomerun box, primarily for HD DVR functionality, but will use for other "HT" purposes as well.

Part of my problem is not so much a lack of information; but conflicting current and archival information and so many recommendations... I'm not quite sure how to narrow down my troubleshooting efforts. I start reading through a discussion of nvidia config and find out it's a *very* old doc that is may no longer be accurate.

I've been noodling with this since December(!) and got disgusted and walked away from it for a month or so; but I'd *really* like to finish this project....

I connect to the Mitsubishi via DVI but cannot get anything but 640x480 or sometimes 720x480 resolution. The card can certainly handle it; I was able to connect up to my ANCIENT Sony CPD-1304 and put it up to IIRC 1024x768, but I'd really rather watch HD on a 65" screen than a 14" screen. Call me crazy.

I've tried support from Mits but the only semi-useful information I can get from them is:
* don't connect a PC to DVI (consensus agrees this is lawyer-speak for: don't bug us if you try)
* the DB15 connector only supports 640x480
* the highest resolution (for DVI) is 1080i
* no info available for horizontal/vert refresh ranges
* YES, the DVI connection DOES support EIA-861 (which to me implied it uses EDID-- aka "plug and play")
* The DVI does send EDID info out (!) per technical support-- 2nd tier (crazy discussion from me to phone support person to engineer ("he doesn't talk to customers") and back again)

I don't seem to be getting EDID info from the TV; I used DDCPROBE (and several others) and I don't get info and it invariable "safe modes" me down to 640x480...

I've been hesitant to muck around with horizontal/vert refresh rates-- but finally tried some and NONE ever come back as "valid"-- and it always defaults down to 640x480 (or 720x480 some times)...

I guess I still haven't figured out the proper way to "officially and completely" tell the video card to ignore EDID and to do what I tell it to-- probably to my benefit, actually....

I have been pursuing this as a problem with the TV-- it not sending properly formed/recognized/valid EDID info out to the video card, but recently, taking another swing at this, I've found discussions about the "edid problem with nvidia cards"...

Could my whole problem be with the nvidia card? Would I have better results with a different vendors card? Could it be that it's not an "official" nvidia card, but an EVGA? (I didn't THINK that would matter but at this point...I suppose I should be turning over all the stones)

Is there another card I should try? At this point I am willing to give it a shot if there's a reasonable chance I may get decent resolution out of it.

Some quotes from a Mitsu doc found online (and from owners manual) are:
V23 models are compliant with HDCP and EIA861 standards for standard, extended and high definition (480i,480p,1080i) video. The DVI input is not intended for use with personal computers or devices outputting video signals with computer resolutions....1080i HDTV with a pixel rate of 1920x1080 @ 30hz can be supported by a DVI interface operating in single-link mode...The V23 can display either of two scanning formats, 480p or 1080i. The horizontal scanning frequency for 480p is 31.5 khz, and 1080i is 33.75 khz...Conventional 480i TV signals have a scanning rate of 15.75 khz. For these signals, line doubling circuitry changes the signal format from 480i to 480p.

---

### Post by ohzopants on 2008-03-20
I just set up my tv as a secondary monitor on an nvidia 7900 card.  nvidia-settings worked beautifully for me.

For a while the resolution the TV was displaying was off (1024x768 ) even if the computer was reporting 1360x768.  Then I figured out that I had to go into the TV's setup menu and select the proper resolution.

I would try nvidia-settings and exploring your TV's menus.

---

### Post by MykeBuntu on 2008-03-23
WHOOHOO AND (pardon in advance to any I offend with the next) OMFG I cannot believe I messed with this for so long!!!

Now...any of you old hands will please not make TOO much fun of me, but I finally figured out the problem that has been vexing me since December. The prior post got me to fiddle around in my TVs "hidden" menus... while I found a setting referencing 1080i for DVI-- it was just parms for when you are using it-- not a tool that allowed you to say "Hey-- DVi-- I want you to come up as 1080i".... I pored over the message boards and googled the planet again to see if I could pick up any other clues. I did find a few comments that were NOT the answer.

Also-- I noticed BETA Heron was out...

For the hell of it... and since it's useless at 640x480 any way... I went for it. I installed Heron over Gutsy. On a LARK I went into the PC's BIOS config again... first time in months. And decided that I'd try setting "YES" to "Does the OS support PNP"

Bang

I yelled into the phone when DVI came up at 1080i (sorry Scott)

So I cannot say for certain whether Heron or PNP=Y was the ultimate answer, but here I am trying to read my screen because I am now at 1920 x1080

It's TIME to order that HDHOMERUN

(one final question if anyone has an easy answer (tho I will continue with my search for the answer in the archives) ; my Xorg.0.log says: "NVIDIA(0): DPI set to (75,75); computed from built-in default"... Can I make all my fonts a LITTLE bit bigger by overriding that setting? If so-- how?
(Answer to self: (did some more fiddling; adjusted font sizes in uhh...2 places... it's not perfect but at least I don't have to zoom in on text to read it now))

---

### Post by amoore on 2008-03-23
I have a wt-42315 Mitsubishi TV and I have been trying to hook up my dvi to it. I never could get it to work! How do you get to the hidden menu? I realy whish I could get this to work!

---

### Post by MykeBuntu on 2008-03-24
**I don't think the TV "hidden" settings had anything to do** with fixing my resolution, as I indicated above. If you DO want to fiddle with them use extreme caution. I messed with my width/height settings to allow me to see the top and bottom bars in 'Buntu. While I succeeded at that, my geometry is far from optimal and there is a lot of chromatic aberration along the perimeter areas of the display. I may pay somebody to come out and optimize the set (with the proviso that I must not lose the ability to see top/bottom buntu bars) but that's big bucks and so I may live with it.

Poke around online for the system maintenance codes for your set- you should probably be able to find them. But again-- BE CAREFUL if you mess with them. One of the first things I accidentally did was a settings reset; I had to re create all my setup on the TV.

I believe that either the upgrade to Heron (beta) or resetting the PC BIOS as indicated was the solution. If I had to bet, my guess would be the BIOS change was the fix. However it's easy enough for you to check assuming you DON'T want to run a beta OS; make the BIOS change and reboot; if that IS the answer you should see the higher resolution.

I think if you've made changes in your xconf file you have to do something (reset it) to tell the OS it can do it's automatic stuff again, otherwise OS assumes you made a change and you want to keep it.

*IMPORTANT DISCLAIMER I am a Buntu beginner so do not take my word. My lack of specificness above is because while I did take notes when fiddling, I do not have them handy and I do not remember the exact details.*

---

### Post by amoore on 2008-03-24
I just upgeaded to hardy, set my bios to PNP = yes, installed the new Nvidia driver and now my resulution at 1920x1080 works!

---

### Post by MykeBuntu on 2008-03-24
Coolskeez...

Now you only have to worry about OVERSCAN 

Did you try just PNP=Y before the software update? I *am* curious if that would'a fixed it... gut feeling is yes.

---

