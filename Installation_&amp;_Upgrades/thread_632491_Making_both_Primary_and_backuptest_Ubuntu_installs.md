---
title: "Making both Primary and backup/test Ubuntu installs?"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by NineseveN on 2007-12-05
I haven't really seen this asked here specifically, I hope I didn't miss it when I did a search. 

Anyway, I've been running Ubuntu long enough that I think it's time to nuke my Windows XP install and run Ubuntu exclusively (I can always use Vmware or WINE etc.. if I need Windows that badly), and I wanted to get some feedback on how I plan to do this all in case I'm missing something. 


On my Desktop, I have a 40gb HD and an 80gb HD on IDE channel one with a CD burner and a DVD burner on IDE channel 2.

Currently, my XP install is on the 40gb HDD and my Ubuntu install is on the 80gb HDD. Here's what I plan to do, let me know if it makes sense or if I need to consider something I haven't already.


HD1 40gb
Primary Ubuntu = 15gb
Backup/test Ubuntu = 15gb
1 Swap for both installs to use = 3.5gb
/home for backup/test Ubuntu = 6.5gb (well, rounding down to whatever is left over)

HD2 80gb
Home for Primary Ubuntu = 80gb


Does this make any sense? Each install will have 2 users (myself and my SO). The backup/test install is to be for testing upgrades (or even new distros) or, in an emergency, to provide a stable way to get back into the PC should my Primary install become corrupted/damaged or broken.

For example, when the next release of Ubuntu comes out, I would upgrade the backup/test partition with it to make sure it's stable, if it is, then at some point I will upgrade the primary. If it's not stable, I can still use the primary Ubuntu install while I wait for fixes for the new version.

As a second example, both primary and backup/test are running the same stable version (in between releases), a change I have made or something I have installed has rendered the primary install unusable, I could at least boot into the backup/test partition and use my PC and try to fix what's wrong from the outside (or at least backup whatever I needed to on an external drive before I begin working on fixing the issue).

Does this make sense?


If it does, then I will also follow through with doing the same for my HP laptop (using Feisty instead of Gutsy due to stability issues right now), though it has only one 120gb HD so it'll be a little simpler. It has Vista on it, so no matter what, it's gonna get nuked in some way, shape or form. 

HDD1
Primary Ubuntu = 15gb
Primary /home = 80gb
Backup/test Ubuntu = 15gb
1 Swap for both installs to use = 3.5gb
/home for backup/test Ubuntu = 6.5gb (well, rounding down to whatever is left over)


Thanks for whatever thoughts you may have. If this works out, I'll finally be 100% free of Windows. So far, I'm loving Ubuntu and *nix in general. :)

---

### Post by jasmuz on 2007-12-05
It seems all well.. but 3.5 Gb of swap is ludacris!
There is no need for so much swap!!!

---

### Post by NineseveN on 2007-12-05
> **jasmuz said:**
> It seems all well.. but 3.5 Gb of swap is ludacris!
There is no need for so much swap!!!

I thought it was a bit much myself, but that was a reccomendation from another Ubuntu user (didn't really get the reason). I currently have 1.5 times my RAM as swap on that machine (2gb RAM = 3gb swap)...which still seems to be a bit much to be honest, but it's been that way since I initially set it up.

Thanks.

---

