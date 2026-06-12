---
title: "Fresh install 16.04 to PC, sound card not recognized"
date: 2016-11-14
forum: Installation &amp; Upgrades
---

### Post by Qualtrough on 2016-11-14
I just did a fresh install of 16.04 and I am pretty sure my sound card is not recognized. The internal speaker(s) work, but not the plug in.

I have checked mute buttons, volume, etc. and tried everything I found on this forum and elsewhere and I still have no external sound.

If there is no cure for this, would switching to another sound card possibly help? Is there a brand or type that is more likely to be recognized?

This is what I have installed:

```
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
        Subsystem: IBM NM10/ICH7 Family High Definition Audio Controller
	Flags: bus master, fast devsel, latency 0, IRQ 27
	Memory at d01c0000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel


```

---

### Post by mörgæs on 2016-11-14
Before buying more hardware I would try a live boot of 16.10. Costs only half an hour of your time.

---

### Post by Qualtrough on 2016-11-14
Thanks for your reply. Can you expand a bit on what is involved in a live boot?

---

### Post by Qualtrough on 2016-11-15
Further to my question, I assume that would involve my needing to copy and reinstall my data and reconfigure my three email accounts, etc. Is that right?

My card is supposed to be recognized by 16.04 so I don't know why I can't get it to work. Since the cards are cheap and easy to install, wouldn't  finding out from someone here what cards/card types are known  to work and then purchasing and installing one of those be an option?

---

### Post by mörgæs on 2016-11-15
> **Qualtrough said:**
> I assume that would involve my needing to copy and reinstall my data and reconfigure my three email accounts, etc. Is that right?

Yes, if the live boot shows that 16.10 works better. You could also try an upgrade in-place but it's more risky.


> **Qualtrough said:**
> 
My card is supposed to be recognized by 16.04
Please post the source for that. Might help in troubleshooting. 


> **Qualtrough said:**
> 
Since the cards are cheap and easy to install, wouldn't finding out from someone here what cards/card types are known to work and then purchasing and installing one of those be an option?

Yes but I try to avoid hardware solutions if a software solution will do. Let's see if anyone has a suggestion.

---

### Post by Qualtrough on 2016-11-15
> **mörgæs said:**
> Yes, if the live boot shows that 16.10 works better. You could also try an upgrade in-place but it's more risky.



Please post the source for that. Might help in troubleshooting. 




Yes but I try to avoid hardware solutions if a software solution will do. Let's see if anyone has a suggestion.

Forsomereasonmyspacebarisnotworkinghere!Itworksintextdocs.Iwillfixthisandreplylater.Whatheadaches.

---

