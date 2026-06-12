---
title: "Saving last successfully booted kernel"
date: 2008-06-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Raptor45 on 2008-06-25
Caught [this]("https://lists.ubuntu.com/archives/ubuntu-devel/2008-June/025662.html") on the mailing lists earlier:

[QUOTE=Ben Collins]Just wanted to point people at this:

[https://wiki.ubuntu.com/KernelTeam/removing-old-kernels](https://wiki.ubuntu.com/KernelTeam/removing-old-kernels)

It's the first step in the road to getting rid of old kernels.[/QUOTE]

Thought it was worth sharing, as this is one of the bigger annoyances in Ubuntu, in my opinion.

---

### Post by ronacc on 2008-06-25
I NEVER remove any of my kernels until a couple of months after final release in fact I keep the last working one in grub.

---

### Post by uBeer on 2008-06-26
> **ronacc said:**
> I NEVER remove any of my kernels until a couple of months after final release in fact I keep the last working one in grub.

If it is going to work like the specification then your last working kernel that is actually used will always be kept around. This is about removing unused old kernels and having an automatic entry for the last successfully booted kernel.

Sounds like a good idea to me, though I usually clean up my menu.lst a lot so there ain't to much choices.

This could be a problem for businesses/companies as well. At my university you have 2 options at boot time: Windows XP and Suse 10.1 (I hope they will update to 11.0 this summer as 10.1 is EOL) and I can understand that you wouldn't want another option with "The last successful boot"...

---

### Post by plun on 2008-06-26
> **ronacc said:**
> I NEVER remove any of my kernels until a couple of months after final release in fact I keep the last working one in grub.

Yup... even more important during development.

I always have 2 kernels installed and removes
others from time to time.

Synaptic > and a search for linux-image

For "stable" software I cannot see a problem with
Ben Collins suggestion and for development
or advanced users this function must be easily disabled.

:)

---

### Post by ronacc on 2008-06-26
> **uBeer said:**
> If it is going to work like the specification then your last working kernel that is actually used will always be kept around. This is about removing unused old kernels and having an automatic entry for the last successfully booted kernel.

Sounds like a good idea to me, though I usually clean up my menu.lst a lot so there ain't to much choices.

This could be a problem for businesses/companies as well. At my university you have 2 options at boot time: Windows XP and Suse 10.1 (I hope they will update to 11.0 this summer as 10.1 is EOL) and I can understand that you wouldn't want another option with "The last successful boot"...

for a work box yes pruning menu.lst is a good idea , my test box gurb is a kluged up multi,multi boot which starts with opensuse 11.0's grub and if I choose to boot Ubuntu transfers control to gutsy's grub from which I can choose gutsy (gnome) hardy (kde or gnome ) intrepid (gnome) with 2 kernels each . plus the occasional odd install thatlooks like it might be fun to play with :lolflag:

---

### Post by ShirishAg75 on 2008-06-26
I'm trying to know how it will work or if somebody has got friendly-recovery working. 

I'm using grub 1.96 which means after purging whichever kernels I don't want grub does it own stuff automatically after the uninstall (some hook)

It will be worth seeing how friendly friendly-recovery is with grub2 ;)

I haven't seen a grub entry in grub.conf and hence dunno what is to entered in menu.lst to invoke the recovery menu.

---

### Post by soccerboy on 2008-06-26
> **ShirishAg75 said:**
> I'm trying to know how it will work or if somebody has got friendly-recovery working. 

I'm using grub 1.96 which means after purging whichever kernels I don't want grub does it own stuff automatically after the uninstall (some hook)

It will be worth seeing how friendly friendly-recovery is with grub2 ;)

I haven't seen a grub entry in grub.conf and hence dunno what is to entered in menu.lst to invoke the recovery menu.

As I understand from the blueprints, cleanup-cruft is going to be highly configurable on what you want it to cleanup so if you don't want to cleanup kernels on a dev. install, you can turn it off.  I am excited b/c I have accumulated tons of config files for programs I tried out and then removed using apt-get remove instead of apt-get purge.  (I don't want to go hunting for the files)

---

### Post by uBeer on 2008-06-27
> **ronacc said:**
> for a work box yes pruning menu.lst is a good idea , my test box gurb is a kluged up multi,multi boot which starts with opensuse 11.0's grub and if I choose to boot Ubuntu transfers control to gutsy's grub from which I can choose gutsy (gnome) hardy (kde or gnome ) intrepid (gnome) with 2 kernels each . plus the occasional odd install thatlooks like it might be fun to play with :lolflag:

Haha, I don't think this program will be of any use to you :popcorn:

---

### Post by ccw on 2008-06-27
> **Raptor45 said:**
> Caught [this]("https://lists.ubuntu.com/archives/ubuntu-devel/2008-June/025662.html") on the mailing lists earlier:

Thought it was worth sharing, as this is one of the bigger annoyances in Ubuntu, in my opinion.

I'd rather just manage my kernels manually. If anything, just take out the hidemenu option in grub by default, so people are aware of what they might be accumalating.

---

