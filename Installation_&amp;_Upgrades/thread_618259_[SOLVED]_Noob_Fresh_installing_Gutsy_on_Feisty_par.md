---
title: "[SOLVED] Noob: Fresh installing Gutsy on Feisty partition"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by supergrover1981 on 2007-11-20
Hi gang,

I'm a newb-in-awe who's been messing about with Feisty (alongside a windows partition) for the past week. The experience was fantastic and  I was looking forwad to sinking into the operating system properly. For reasons best left unmentioned (relating to some excessive newbie tinkering), I'd now like to do a fresh install of Gutsy on my Feisty partition - there's nothing important inside feisty, so data/program/settings loss is not a problem.

I'd assumed it would be a case of loading the Live install CD, but I can't seem to get around GRUB. The CD boots from the windows partition, but only goes to a "BusyBox V1.13" prompt if I choose "Linux" from the windows boot manager. The feisty partition doesn't seem to recognise boot at all, just loads up my regular Feisty. I've double-checked that the boot sequence reads CD drive first.

I can access Feisty in recovery console, but cannot log into the GUI due to some truly bizarre keyboard remapping. If anyone has any ideas on how to install to the Feisty partition, I'd be most appreciative. I guess it's a boot manager thing (or misconfigured install CD?), but I'm pretty newbish on this sorta problem.

Finally, many thanks for a stunningly helpful online forum - despite this being my first post, these forums have been an awesome help to me during my past week of newbie Ubuntu tinkering.

Cheers,
          - SG

---

### Post by Pumalite on 2007-11-20
'For reasons best left unmentioned (relating to some excessive newbie tinkering)'
Could you explain this better since it might have repercussions in your current problems?

---

### Post by supergrover1981 on 2007-11-20
*grin*

Hi Puma - many thanks for the quick response.

I decided to try the "hands dirty" approach with my first Linux install. I went in and recklessly modified anything that seemed curiously interesting, with the expectation that I would re-install after a week and start behaving myself. I didn't touch anything particularly powerful - mostly just display related stuff (xorg.conf is in a shambles). I didn't touch anything GRUB or startup-related. 

It's worth mentioning that about 30 seconds after posting my first post, I managed to get back into Feisty (the keyboard had been remapped to dvorak), and sans a few 3d-related xorg.conf errors, everything is functional. Nonetheless, the main problem still stands: I'd love to do a fresh install, mostly so that I can be confident any future conflicts were not caused by this first week of curious tinkering...but I can't seem to load the install cd.

Thanks again,
            - SG

---

### Post by supergrover1981 on 2007-11-20
I am so sinceely sorry (and embarrassed) guys - it turned out to be a faulty CD after all. I reburnt the ISO and it worked fine.

Apologies for the time-wasting, I'll try to check more thoroughly before posting again. Many thanks for the help anyway. :-)

---

### Post by Pumalite on 2007-11-20
You are welcome. Good luck. Glad you got it working!

---

