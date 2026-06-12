---
title: "Lucid RC Live CD installer hangs after keyboard selection (Step 3)"
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by andyevans01 on 2010-04-24
Can anyone suggest a way I can get past this?  I have successfully installed Lucid RC on my EeePC 701 netbook at home, but using the same live CD on my Acer Aspire at work, it hangs after the keyboard selection stage (step 3) of the install process.  

Does anyone have any suggestions on how to gather diagnostics, or of any workarounds I might try.  After looking through the threads on this forum I have tried the "nomodeset" and removing "quiet splash" from the boot options - bot made no difference at all.

If I allow the live CD to boot it all seems to go fine, and I get the live system up on the PC.  Trying to do an unstall from this system gives me the same hang as it does without loading the live system first.

Any help would be gratefully received.

Best regards

Andy.

---

### Post by kansasnoob on 2010-04-24
Sounds like it could possibly be due to this bug in ubiquity:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/553087](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/553087)

It was supposed to be fixed in updates yesterday but since there are no new daily build's ATM you'll have to boot to the Live Desktop and install updates, then click on the install icon to try it.

---

### Post by andyevans01 on 2010-04-24
OK, thanks for that - I can't really do an update as I am having a lot of trouble getting my wireless USB adapter recognised.  I seem to remember having an awful problem getting it to work with 9.10 too, but can't remember what it was that finally got it going!

I'll probably wait until next week and try the full release version instead.

---

### Post by kansasnoob on 2010-04-24
They may also re-enable the daily's. If not there will be iso-testing beginning about the 26th I'd guess.

---

### Post by andyevans01 on 2010-04-25
I'll probably wait and pick up the full release.  I have given up on my aging RALINK USB wireless dongle, and have ordered a newer Atheros based dongle in the hope that it will be supported on Lucid without having to fiddle too much, or without having to use NDISWRAPPER, which still doesn't want to play ball in Lucid with the RALINK.  So I have to wait until that arrives first anyway.

---

