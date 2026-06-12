---
title: "Mounting ISO to cdrom as repository?"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by Anubisxian on 2008-04-15
I've read numerous threads today on mounting isos to directories and using them as cdroms. My question is (and I'm at work, so I can't test it right now) if I mount my Ubuntu 7.10 installer DVD iso image to my cdrom device, can I _then _use that as a software repository for Synaptic package manager? :confused:

The main reason is that I disliked having to insert my install DVD whenever I updated something - I wound up disabling the cdrom as a repository source. However, I'm trying to limit my bandwidth consumed by adding packages from the repos when they're on my DVD. I have the entire contents of the Live DVD in the iso _anyway_.

---

### Post by Anubisxian on 2008-04-15
Ugh... my face is red as I type this. No sooner as I returned home and checked the forums for a reply, I find [this.]("http://ubuntuforums.org/showthread.php?t=743943&highlight=mount+iso+cdrom") Somehow I didn't find it before posting like a total n00b. :mad:

Basically, you install gmountiso, (which is a nifty little prog in its own right), mount the iso image file to some directory of your choosing, then type this at the command line:

> sudo synaptic --add-cdrom /media/iso/

assuming that /media/iso is a valid directory you've created yourself.

Thanks zvacet, for those tips. All credit given to you, my man. Much love!

---

