---
title: "Video hang ups."
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by Peter Bell on 2011-05-12
I am using an Intel DH55-HC mobo with i5-650 processor.  This system first had 10.04 installed and has been upgraded through 10.10 to 11.04.  I am using the on-chip graphics processor and the hdmi connection.

Since installing 11.04, I have been experiencing video lockups at random intervals.  The only solution I have found is to reboot the machine each time.

However, the whole machine does not lock up - just the video freezes.  The mouse pointer still moves on the screen, and will change shape, but none of the screen contents will update.

The machine carries on processing - for instance, I was copying a large number of files from the local disk onto my fileserver earlier today.  After about 30 minutes, the screen froze - no menus would appear, no windows would move, the on-screen clock stopped updating etc.  However, the file copying continued for another 90 minutes, running to completion.

Can anyone suggest what causes this problem and how to fix it?

What is really turning me crazy is that I have recollections of having experienced a similar problem in the past and that crafting an xorg.conf with one of the features of the intel driver disabled fixed it.  However, I cannot recall precise details, and googling hasn't brought up anything useful.

---

### Post by Peter Bell on 2011-05-12
Okay, I've just realised that I can reach a text console (Ctrl-Alt-F1) while the graphics screen is hung.  Is there anything I can do from the text console to investigate the cause of the hang (the Xorg.0.log doesn't seem to show anything peculiar), or to recover from the hang.

I know that I can do 'reboot'!

---

### Post by kuriosity on 2011-06-22
I have the same problem.

This never happend while i was on Ubuntu's earlier versions - 9.10, 10.04 & 10.10. The video hangs are quite often on my current 11.04 ubuntu version. 

It is annoying and I hate to turn off my laptop without shutting down! :(

is there a fix for this.. ?

---

