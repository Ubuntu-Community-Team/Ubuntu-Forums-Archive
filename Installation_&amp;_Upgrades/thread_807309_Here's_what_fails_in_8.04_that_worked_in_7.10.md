---
title: "Here's what fails in 8.04 that worked in 7.10"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by dfrossar on 2008-05-25
This applies to my Linux desktop at home. My Linux laptop at work -- running the same OS (and both installed from scratch, not as upgrades) -- is fine, with none of the following issues. At home...

1. Upon booting, Ubuntu 8.04 locks up solid about half the time -- Ctrl-Alt-Backspace (and, in fact, any key combination) has no effect and I have to do a hard-reset. The other half the time, the OS starts and works as expected.

1a. Rarely, the OS locks up much later, after booting successfully, and requires a hard reset.

2. Suspend no longer work at all. Clicking on Suspend causes 8.04 to return to a login screen. This feature worked fine on this machine under 7.10 and previous versions.

3. When the machine is left on for a long time without activity, 8.04 blanks the screen and no amount of key-pushing or mouse-wiggling brings it back. A hard reset is the only cure.

I don't mean to be too negative -- after all, I got an entire OS and thousands of programs for free -- but unless someone can give me a quick fix, I'm going back to 7.10.

---

### Post by Pumalite on 2008-05-25
I'd do a memtest and check the power supply.

---

### Post by MaindotC on 2008-05-25
It sounds to me like you have some issues concerning your video driver.  Did you use the restricted driver manager in Gutsy?

---

### Post by Patb on 2008-05-25
> **dfrossar said:**
> 1. Upon booting, Ubuntu 8.04 locks up solid about half the time -- Ctrl-Alt-Backspace (and, in fact, any key combination) has no effect and I have to do a hard-reset. The other half the time, the OS starts and works as expected.
If it doesn't get as far as the gui screen, you could edit the grub options temporarily to get more information.  At the grub menu, press "e" to edit the menu, move to the line beginning "kernel" then press "e" again to edit.  Remove the options "quiet" and "splash" and then press "b" to boot (not escape - that will ignore your changes).  

This should give you a chance to look in detail at where it is locking up and perhaps reveal something useful.

Cheers, Pat.

---

### Post by dfrossar on 2008-05-26
> **Pumalite said:**
> I'd do a memtest and check the power supply.

I did both. Memtest is clean (four passes) and the power supply looks fine.

I also updated today to the newest kernel release. 8.10 still locks up about every other time I boot.

David

---

### Post by dfrossar on 2008-05-26
> **strAlan said:**
> It sounds to me like you have some issues concerning your video driver.  Did you use the restricted driver manager in Gutsy?

I do use proprietary drivers when necessary (I'm not a purist in that regard), but in this case I have none loaded. 8.10 is using standard drivers for my video (on the motherboard). This worked fine in v. 7.10, too, of course.

---

### Post by dfrossar on 2008-05-26
> **Patb said:**
> If it doesn't get as far as the gui screen, you could edit the grub options temporarily to get more information...

This should give you a chance to look in detail at where it is locking up and perhaps reveal something useful.

Pat, that was a good idea. Thanks for the help with Grub. Unfortunately, nothing in the character-based part of the boot process seems to be at fault. Bootup proceeds as usual. Then the lockup occurs after I get to the GUI login and log in. Usually, things come to a stop when I start moving the mouse and try to click on an icon.

I could believe I have problems with the mouse driver, though, again, everything worked fine in 7.10. 

And I can't think of a reason why my Suspend function would be affected at all by this. (Though, of course, these may be two completely separate problems.)

---

### Post by Pumalite on 2008-05-26
Is this an upgrade or a clean install?

---

### Post by dfrossar on 2008-05-27
> **Pumalite said:**
> Is this an upgrade or a clean install?

A clean install from disk.

---

### Post by dfrossar on 2008-05-27
Thanks for the help everyone, but I need to use this machine and need it to be reliable, so I'm going back to Gutsy tonight.

My apologies to everyone who would prefer to keep going until we figured this out.

David

---

### Post by MaindotC on 2008-05-27
I agree with you 100 percent - check my sig :)

---

### Post by dfrossar on 2008-06-02
BTW, just for closure, I'm back on 7.10 and Suspend works fine, and it never locks up. I think I'll stay here for awhile and not worry about upgrading.

Thanks everyone for their help.

David

---

