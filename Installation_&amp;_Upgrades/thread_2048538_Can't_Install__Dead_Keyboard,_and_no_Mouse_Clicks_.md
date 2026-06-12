---
title: "Can't Install : Dead Keyboard, and no Mouse Clicks after booting from live cd."
date: 2012-08-26
forum: Installation &amp; Upgrades
---

### Post by eric_son on 2012-08-26
Help!

I'm trying to re-install 12.04 x64. (dual boot with w7)
After booting from CD, I'll reach a point where I'll be offered a choice between trying out the LiveCD and Installing.

Here's where the problem starts.
The mouse would first appear to be unresponsive for up to one minute.  During this time, the mouse pointer will only respond sluggishly.
After a minute or so, the mouse pointer will now be responsive.  But that's as far as I can go.  Clicking the LMB does not do anything.  Hence, I can't click on the [Install] button. :(
The keyboard is unresponsive as well.

Thinking it could be an x64 problem, I also tried it with a 12.04 x86.  Same results -- dead mouse for 1 minute, then non-responsive LMB later on.

Any ideas how to proceed?
Thanks.

My system:
- CPU i5 
- MOBO P8h61-M LX3Plus
- USB Keyboard
- USB Mouse

---

### Post by Icarus315 on 2012-08-27
It is a shot in the dark, but, in your computer's BIOS settings (usually press the del key or the f1, f2 or such key right when the computer starts), try looking for and changing "Legacy USB Devices" to enabled.  The "Legacy USB Devices" may be phrased in a variation of that wording.

---

### Post by eric_son on 2012-08-27
> **Icarus315 said:**
> It is a shot in the dark, but, in your computer's BIOS settings (usually press the del key or the f1, f2 or such key right when the computer starts), try looking for and changing "Legacy USB Devices" to enabled.  The "Legacy USB Devices" may be phrased in a variation of that wording.

Thanks!  
But I also took that shot in the dark as well.  No luck. :(

---

### Post by Icarus315 on 2012-08-27
Well, that sucks.  Another thing you can try is to get USB to PS/2 adapters (two of them, one for mouse and one for keyboard) and plug them into the legacy PS/2 ports.  One is purple (keyboard), and the other is green (mouse).  This would put the keyboard and mouse inputs on different hardware paths before they reached a higher-level operating system.  It might work and it might not.

USB to PS/2 adapters go for about $1.50 each.

---

### Post by eric_son on 2012-08-27
Thanks.
Sounds like a plan.  I'll check with some of my friends to see if they still have those keyboards and mice.

---

### Post by Icarus315 on 2012-08-27
Another thing to try, just occured to me, is when the installation media gets to that selection screen: unplug and replug the USB keyboard and mouse.  It is totally safe to do that and it may establish a connection - hopefully.

---

### Post by stoneguy on 2012-08-27
> **Icarus315 said:**
> Another thing to try, just occured to me, is when the installation media gets to that selection screen: unplug and replug the USB keyboard and mouse.  

I have a few boxes like that. But things have been getting better with later versions.

---

### Post by eric_son on 2012-08-28
Oh!  That sounds good.
I'll try it when I get home from work.

Thanks again!

OT: This is really weird... Save for an occasional sound driver issue, I've never really encountered problems installing Linux.  This is the first time for me.  
Anyway, thanks for the help I'll definitely try the unplug+plug later.

---

### Post by eric_son on 2012-08-28
:( Still no luck.
After booting from CD, and reaching that point where the mouse pointer moves but does not respond to clicks, I unplugged the mouse and plugged it back in.  After that, the mouse failed to move at all. Hehehe.
I'll have to find another way.  I still have to try the approach of using an old PS/2 mouse + keyboard.

---

### Post by amdijefri on 2012-08-30
I am experiencing exactly the same problem as described and have attempted all the workarounds suggested without luck. I have an ASUS AMD motherboard, not sure of the model.

---

### Post by eric_son on 2012-08-30
I've yet to try the alternative installer.  I'll check it out during the weekend.  (Crossing my fingers)

But I'm not hoping for much.  I have already tried LinuxMINT and OpenSUSE, and got the very same results --- mouse pointer moves, but does not respond to clicks.  

I think it's an ASUS mobo issue. :(

---

### Post by eric_son on 2012-08-31
Holy cr*p!  I think I'm in!
I went to the ASUS subforum and found a lot of similar complaints about Linux refusing to install on ASUS boards.  I saw a thread (unfortunately, I forgot which one) that mentioned hitting F6 before the CD boots.  This will then bring up a settings screen which will allow you to set the boot options.  I tinkered with the boot options until I was finally able to boot to Ubuntu with a fully functional Mouse and Keyboard.  I'm writing this response after my first successful boot so I don't remember exactly the names of those options.  All I can saw is that I disabled the first 3 options on the boot option menu. ( I think noapic is one of them. ) Sorry...  

It's a bit late.  I'll crash for now and try to install tomorrow.

---

### Post by eric_son on 2012-08-31
Ubuntu installed!

So to summarize:

[LIST=1]
[*]Boot from Live CD
[*]Tap on the F6 key before the OS loads.  (Much like you'd tap on F8 on Windows)  This will bring up an options screen.
[*]Choose your language.
[*]Tap F6 to bring up the boot options.
[*]Select the first option (damn...I forgot the exact name again.  Rest assured it's the first option! :) )
[*]Hit ESC.
[*]Select Try Ubuntu, at least to test if your KB + Mouse is working.
[*]At this point, I was able to boot to the live CD with mouse and kb working.  I proceeded to install the OS.
[/LIST]

Now I system is only outputting stereo sound.  I can't seem to make it output 5.1.  Minor problem.  At least I was able to install.

---

