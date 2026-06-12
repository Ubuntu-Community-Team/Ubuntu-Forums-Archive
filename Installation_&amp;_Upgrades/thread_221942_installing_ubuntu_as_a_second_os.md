---
title: "installing ubuntu as a second os"
date: 2006-07-24
forum: Installation &amp; Upgrades
---

### Post by pjs_flyer on 2006-07-24
Hi

I'm currently running suse on my laptop and want to install ubuntu as a dual boot.  At the moment I've got (something like):
hda1 - reiserfs - suse 10.1
hda3 - reiserfs - "important stuff" (mounted as /home in suse)
hda4 - reiserfs - nothing on it at the mo
hda5 - swap

I want to install ubuntu on hda4 to play around with it.  When I go through the setup for ubuntu, it picks up all of the partitions and what they're formatted as, and leaves me to start moving stuff around in dropdown boxes so that I'm just left with:

hda4 - reiserfs - primary partition
hda5 - swap

...and the option to format either of them left unchecked.  Then on the last screen before accepting the changes it comes up with a warning saying something to the effect that all partitions will be zapped, even the ones if I've removed - and this is where I bottle the installation and decide suse is fine for now.  Will ubuntu really mess around with these other partitions or am I misreading the warning? Or is there another way to make sure ubuntu only gets installed on hda4?

Cheers

P.

---

### Post by richbarna on 2006-07-24
It's a standard message that says all selected partitions will be formated, just go ahead with the install. You will get ubuntu on hda4 and it will share the swap on hda5. Just make sure that you have UNCHECKED the partitions that are already formatted/contain Suse.

---

