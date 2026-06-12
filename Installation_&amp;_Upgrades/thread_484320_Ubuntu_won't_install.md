---
title: "Ubuntu won't install"
date: 2007-06-25
forum: Installation &amp; Upgrades
---

### Post by Mouseplatterman on 2007-06-25
I'm running a roughly three-year old midrange dell desktop. I recently added 512 more MB RAM, an Edimax Wireless LAN PCI adapter, and audigy SE sound blaster sound card. I reinstalled windows a while ago with some difficulty, and haven't been able to install (or even run the live CD of) Ubuntu, but have tried persistently. When I try to start the live CD normally, after what appears a normal proceeding a long string of code or something comes up, and some times it goes on endlessly until I reboot. However, after I installed the sound card (for a while I'd suspected there was something wrong with the onboard sound and that might have had something to do with it, but I don't know too much about computers) it stopped after a while, proudly displaying an error message at the end. I rebooted and tried again, and this time at the bottom was displayed something like:

[ 86.053240]  AGPGART: AGP aperture is 128M @ 0xd0000000

the first error message, after a long string of similar lines, read something like:

[    89.0258976] [<c0169876876>]    error_code+0x7c/0x90

When I try to start Ubuntu in safe graphics mode, the little horizontal orange scroll bar stalls out about an eighth of the way through after it's done bouncing back and forth. 

Any help? Should I try an older version (this was feisty fawn)?
Sorry if this has already been answered, and sorry if I was too vague--I can clarify anything too hazy.

---

### Post by stchman on 2007-06-25
> **Mouseplatterman said:**
> I'm running a roughly three-year old midrange dell desktop. I recently added 512 more MB RAM, an Edimax Wireless LAN PCI adapter, and audigy SE sound blaster sound card. I reinstalled windows a while ago with some difficulty, and haven't been able to install (or even run the live CD of) Ubuntu, but have tried persistently. When I try to start the live CD normally, after what appears a normal proceeding a long string of code or something comes up, and some times it goes on endlessly until I reboot. However, after I installed the sound card (for a while I'd suspected there was something wrong with the onboard sound and that might have had something to do with it, but I don't know too much about computers) it stopped after a while, proudly displaying an error message at the end. I rebooted and tried again, and this time at the bottom was displayed something like:

[ 86.053240]  AGPGART: AGP aperture is 128M @ 0xd0000000

the first error message, after a long string of similar lines, read something like:

[    89.0258976] [<c0169876876>]    error_code+0x7c/0x90

When I try to start Ubuntu in safe graphics mode, the little horizontal orange scroll bar stalls out about an eighth of the way through after it's done bouncing back and forth. 

Any help? Should I try an older version (this was feisty fawn)?
Sorry if this has already been answered, and sorry if I was too vague--I can clarify anything too hazy.

Try the alternate install CD.

---

### Post by floke on 2007-06-25
+1

---

### Post by Mouseplatterman on 2007-06-25
> **stchman said:**
> Try the alternate install CD.

Will I be okay if it doesn't install right, though? I don't want to gork my system by installing an OS without testing it first...

---

### Post by Mouseplatterman on 2007-06-25
I tried version 6.06, but that didn't work either. I got: 

[171963.36800]   <0>kernel panic--not syncing: fatal exception in interrupt

Neither cd had any defects

---

### Post by stchman on 2007-06-26
> **Mouseplatterman said:**
> I tried version 6.06, but that didn't work either. I got: 

[171963.36800]   <0>kernel panic--not syncing: fatal exception in interrupt

Neither cd had any defects

It sounds as though you have a hardware problem.  You may try the safe graphics mode.  I had a machine that I could not install to and turns out the RAM was bad.

---

### Post by Mouseplatterman on 2007-06-26
I tried safe graphics... didn't work.

Is a "bad RAM" fixable? and how do i tell what's broken?

---

### Post by stchman on 2007-06-27
> **Mouseplatterman said:**
> I tried safe graphics... didn't work.

Is a "bad RAM" fixable? and how do i tell what's broken?

Unfortunately bad RAM sometimes does not rear its ugly head in a noticeable fashion.

The LiveCD has a memtest I believe.  Run that and if there are LOTS of errors then RAM may be the culprit.  Also your RAM might be too aggressively timed.  Tracking down faulty parts can be difficult.

---

### Post by Mouseplatterman on 2007-06-28
I ran the test, and I don't think I saw any errors. Just in case though, I think I might remove one of my ram's and then try to boot ubuntu again (and then try the other RAM)

---

### Post by dabl on 2007-06-28
The AGP thing is the problem, I think.  There is a special software switch that needs to be set during bootup for a few late-model cards that somehow get mis-recognized as AGP-port cards, when they are actually PCI cards.  I can't for the life of me remember exactly what card I saw the posting about, but it might have been that SB Audigy card.  Search the forums, or Google for "AGP error" or "Linux AGP error" etc., and you should be able to turn up a few posts and find the switch you need to enter to get it to boot.  Once booted, you can set it up so it won't be a problem in the future.  Sorry I can't just write the answer for you.   :(

---

