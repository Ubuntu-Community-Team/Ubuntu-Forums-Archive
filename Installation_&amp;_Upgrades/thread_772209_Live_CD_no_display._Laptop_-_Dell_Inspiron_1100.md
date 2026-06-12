---
title: "Live CD no display. Laptop - Dell Inspiron 1100"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2008-04-28
Using Hardy - at the time when I would expect x to be started and displaying, I am not getting a display with the live CD on many occasions. Just a black blank screen. Sometimes the display comes up, many times it does not.

On the failed occasions, it seems that x may be running, but somehow the display is not coming up it just remains black.
ctrl alt F1 and startx gives an error message that x is already running or similar.

I have tried all of the boot options I can see or think of, no reliable improvement.

The live CD function is important to me because this machine is a demonstration machine, it has to be a reliable live CD machine.

Subsequent use of ctrl alt backspace sometimes leads to a correct display. I have looked at the file  /var/log/Xorg.0.log
 and I notice that apparently that something is loaded kernel module for "i915" driver.

With previous use of this laptop I have so far found success only with i810 driver. I wonder if it is possible that problems I am having may be associated with the use of i915.

I would like to test this. How do I go about changing to, or somehow forcing, the module for i810?

In Hardy the xorg version is 7.3 which produces a rather empty file for xorg.conf and I am not at all sure what to look at or do - next. Comments appreciated

---

