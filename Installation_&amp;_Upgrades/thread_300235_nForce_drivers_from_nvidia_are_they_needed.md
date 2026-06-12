---
title: "nForce drivers from nvidia: are they needed?"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by kcy29581 on 2006-11-15
Hi all,

[B]Are the nForce drivers available from nvidia needed on a system with an nForce chipset? Is there any gain in using them?
[/B]
Link to the drivers:[http://www.nvidia.co.uk/object/linux_display_ia32_1.0-9629_uk.html](http://www.nvidia.co.uk/object/linux_display_ia32_1.0-9629_uk.html)

Obvioulsy we have to use the nvidia graphics drivers from nvidia to get the maximum benefit for their graphics cards, so it would be safe to say the same would apply for the chipset, i guess.

Please do not treat this as a support thread: a simple question is asked.

---

### Post by Dr. Nick on 2006-11-15
If you are referring to nForce 2 then I believe the answer is no. I had a nforce 2 and had to use nvidias drivers to get the lan card to work several years back, but I believe that the necessary sound and lan drivers are now built into the kernel so they are not needed.
 
If you are referring to nforce 3 or 4 then I dont know.

---

### Post by kcy29581 on 2006-11-15
> **Dr. Nick said:**
> If you are referring to nForce 2 then I believe the answer is no. I had a nforce 2 and had to use nvidias drivers to get the lan card to work several years back, but I believe that the necessary sound and lan drivers are now built into the kernel so they are not needed.
 
If you are referring to nforce 3 or 4 then I dont know.I was actually looking for an answer regarding all nforce chipsets, as I did not know that there was a difference (for needed drivers)

I am mainly asking about nforce 4 though, as that's the one I'm using at work.

Thanks for the reply. Anyone else with solid info?

---

### Post by bulldog on 2006-11-15
Is everything working for you?

If yes,you don't need the drivers.

If you do not install your mobo drivers in Windows,most likely some things aren't working properly.

---

### Post by xinix on 2006-11-15
I don't have any problems with out these drivers on an nforce4 chipset.

It's possible they may be included already.
> All of the following drivers are open-source and are included in most popular Linux distributions. In most cases, the Linux installer will select the appropriate driver for the detected nForce hardware.

---

### Post by drphilngood on 2006-11-15
> **kcy29581 said:**
> ...I am mainly asking about nforce 4 though, as that's the one I'm using at work...

I use one of those and didn't need any.

---

### Post by kcy29581 on 2006-11-16
> **xinix said:**
> I don't have any problems with out these drivers on an nforce4 chipset.

It's possible they may be included already.
see, my problem with this is that "no visible problems" does not immediately rule out any future/current non-visible problems.

Also, nvidia's quote just makes things worse; how does one find out whether or not his distribution includes the latest drivers?

---

### Post by kcy29581 on 2006-11-18
bumping because seriously, things like this deserve a full answer.

---

### Post by the ev on 2006-11-18
> **bulldog said:**
> Is everything working for you?

If yes,you don't need the drivers.

If you do not install your mobo drivers in Windows,most likely some things aren't working properly.

I'm also interested in a full answer to this, having nForce4.  If by work you mean "I get sound", then yes: but only on two channels.  My center, woofer, and surround speakers are all dead silent.  So I wouldn't say the open source drivers included in distros "works".  [This]("http://www.ubuntuforums.org/showthread.php?t=253725&highlight=nforce") guide doesn't seem to work with nForce4, and I've yet to find any other surround solution.  :(

---

### Post by jaybombalous on 2006-12-27
> **kcy29581 said:**
> see, my problem with this is that "no visible problems" does not immediately rule out any future/current non-visible problems.

Also, nvidia's quote just makes things worse; **how does one find out whether or not his distribution includes the latest drivers?**


Well nvidia list the files that are needed to use for nforce support. I am sure there is way to see which drivers are loaded for linux, but I am not the one to ask for that answer.

---

### Post by exc220 on 2007-01-10
Hi i am very interested in this also!
I have an nforce2 mobo and I woud like to know if there is any important gain in installing the official nvidia drivers!
Anyone have their own experience on this issue?

---

