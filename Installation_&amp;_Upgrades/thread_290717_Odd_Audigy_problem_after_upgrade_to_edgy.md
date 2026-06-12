---
title: "Odd Audigy problem after upgrade to edgy"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by fanoodlehey on 2006-11-01
After upgrading to edgy my sound works fine from the headphone jack on my Audigy's front panel. But I have no sound on the main line out.

Any ideas?

---

### Post by woedend on 2006-11-01
run alsamixer from terminal and check levels.  
also, scroll far to the right and try toggling the digital analog option by pushing the m key.
let me know if you have success

---

### Post by fanoodlehey on 2006-11-01
Thanks for the quick reply but I already checked the alsamixer and everything looks fine. Any other suggestions?

---

### Post by woedend on 2006-11-01
yes, make sure its your default soundcard.  double click the sound icon, go to file, then to device...your soundcard should be number 0.

---

### Post by fanoodlehey on 2006-11-01
I'm using Kubuntu so I'm not sure that advice applies. Can you translate for kde?

By the way the quick replies are much appreciated.

---

### Post by clickwir on 2006-11-01
I had upgraded my Kubuntu dapper to edgy with a apt-get dist-upgrade and had no sound from my Audigy card.

After racking my system and changing kernels a few times and all a bunch of things, I was messing around in alsamixer and had to mute "Audigy Analog/Digital Output Jack". As soon as I hit that I was blasting White and Nerdy.

Only reason I say this is because I "THOUGHT" I had checked it before,  but missed it about a dozen times going into alsamixer. It's also backwards than what most people would think, it needs to be muted, not "unmute everything" like some people suggest.

---

### Post by fanoodlehey on 2006-11-02
No luck that way either. I don't think it's a mixer issue.

---

### Post by Cable on 2006-11-02
Do you have an onboard sound card as well as your Audigy?  If so, you may want to check out my [problem thread]("http://www.ubuntuforums.org/showthread.php?t=290977") and see if it's similar to yours.  I haven't gotten any answers yet unfortunately.

---

