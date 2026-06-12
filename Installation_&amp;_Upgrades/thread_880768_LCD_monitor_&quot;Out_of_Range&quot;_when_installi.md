---
title: "LCD monitor &quot;Out of Range&quot; when installing"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by jamoncillo on 2008-08-05
OK.. I installed ubuntu on a new PC (presario SG3309LA) with a HP W15e LCD monitor. The problem is that my monitor displays an 'out of range' message. It happened also when running the Live CD (I used an old monitor to install it)

I've read some posts about this very same problem, but couldn't understand how to fix it (I'm kinda new to Linux) so if someone could provide me with a step-by-step guide That would be awesome! thanks in advance

---

### Post by overdrank on 2008-08-05
> **jamoncillo said:**
> OK.. I installed ubuntu on a new PC (presario SG3309LA) with a HP W15e LCD monitor. The problem is that my monitor displays an 'out of range' message. It happened also when running the Live CD (I used an old monitor to install it)

I've read some posts about this very same problem, but couldn't understand how to fix it (I'm kinda new to Linux) so if someone could provide me with a step-by-step guide That would be awesome! thanks in advance

Hi and welcome, could you give us some system specs? Like graphics and memory and so on. If you used a different monitor for the install then you may use the xfix option by booting into recovery mode. Which is usually the second choice from the grub.

---

### Post by mikebear on 2008-11-25
I had the same problem, I ran the Live CD off my PC last night, and Ubuntu boots up, but my screen goes blank and it displays an "Out of range" message. 

My current rig specs:
AMD 2.4 GHz (not sure)
2 GB RAM
ATI Radeon HD 2600
120 GB HDD
Im also using a standard CRT monitor connected to the videocard using DVI converter
1280x1024 resolution

---

### Post by decard_pain on 2008-11-25
this is a resolution problem.i get it on my flat panel when the resolution is too high or too low.
this could be tricky to fix if you can't see the screen.have you tried recovery mode?

---

### Post by mikebear on 2008-11-25
sorry i'm totally new to all this. what's a recovery mode? i was able to boot it up under safe graphics mode, is that what you're asking? I didn't proceed to install from there though , since I might still encounter that "out of range" thing after I've installed ubuntu

I've been hearing that this might be because of my video card as well? is it not supported?

---

### Post by decard_pain on 2008-11-25
i'd say it was just the monitor not being detected properly.this would be why the resolution is too high or too low.
ok when you boot up do you see a list of options.
if not look at the screen when booting if it says press some key to get to the grub menu(there should be a 5-15 second timer)

when at the menu pick the one that says recovery in brackets .
this should let you atempt to fix the resolution problem

---

### Post by mikebear on 2008-11-25
Okay I'll try that later tonight :) So what's in recovery mode? what do I do when i get there?

Basically what i see when i pop in the cd is the list of  languages, I choose English
Then i see what I actions i can take, the Live CD, Install Ubuntu, etc

And I see a few options below which i can access using the Function keys

---

### Post by decard_pain on 2008-11-25
just follow the on screen instructions.
at some point you may need to pick you gfx card and screen resolution from the safemode screen.
just pick what ever resolution you normaly use in windows
my flat pannel is not very good it only accepts 1024 x 768
anything else and i get the same message on screen as you get.

---

### Post by mikebear on 2008-11-25
> **decard_pain said:**
> 
ok when you boot up do you see a list of options.
if not look at the screen when booting if it says press some key to get to the grub menu(there should be a 5-15 second timer)

when at the menu pick the one that says recovery in brackets .
this should let you atempt to fix the resolution problem

What's a grub menu?

---

### Post by decard_pain on 2008-11-25
sorry i think i've missed something.
i take it you have not installed it yet then...you have only tried the live cd.
in this case there is no recovery mode.
you may get a screen asking if you want low gfx mode..if i remember corectly .you can set the card and screen settings on that screen..
hope this helps..

ps. if you do install.just follow the instructions i've put further up in this thread.it should fix the problem if not just boot in low gfx mode and ask for more assistance.from there we can take a good look at your xorg.conf

---

### Post by decard_pain on 2008-11-25
grub is the bootloader that gets installed .(it lets you pick your other os if you have 1 .)

---

### Post by jamoncillo on 2010-01-23
it was a hardware driver problem, since the computer has an Nvidia chip. Just went to system->administration-> hardware drivers    an enabled them. thanks

---

