---
title: "What's the best way to re-install Gutsy?"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by RostokMcSpoons on 2008-01-24
I'm having problems trying to get my wifi to work, I'm at the point of giving up on Linux and it's arcane command line gibberish.  

So I'm trying once more, for luck.  I'd like to reinstall Gutsy from scratch.  Is there a clean and simple way to do this without resorting to formatting the hard drive?

Could I just rm -f (or whatever the particular gibberish is) and let the LiveCD installer sort it out?

---

### Post by njparton on 2008-01-24
Pop in the live CD and run the installer.  On the partitioning screen, delete your existing partitions, then start again.  No need to specifically format them first.

BTW, it may not be "linux's" fault that your wifi doesn't work - has the hardware manufacturer released drivers?

---

### Post by RostokMcSpoons on 2008-01-24
> **njparton said:**
> Pop in the live CD and run the installer.  On the partitioning screen, delete your existing partitions, then start again.  No need to specifically format them first.

BTW, it may not be "linux's" fault that your wifi doesn't work - has the hardware manufacturer released drivers?



Thanks - I guess I've been an idiot on two fronts...

1) I wasn't seeing the CD's menu when I booted it up - I assumed (and we all know what that does) that was on purpose, as I have a 'real' installation already.  I guess the real reason is the boot order is HD ... CD  ... floppy, but I thought it was CD ... HD ... floppy.  I need to check!

However I'm not going to do that just yet... 

cos

2) I've just got my wifi to work !!!    The problem is I don't really know why - the only thing extra I've done is a 'make clean' followed by a 'make debug', so maybe there was something wrong in my previous build... I don't know ... I've just got to try to make it work even after a reboot now (which might be more 'fun')

so - apologies, and thanks for your help :)

---

