---
title: "Blank screen issues, Ati X700 and Acer Aspire 5020 on Gutsy Gibbon 7.10"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Morkalin on 2007-10-19
Hi everyone,

I'm having issues with my Acer Aspire 5020 (model 5024WLMi) both with booting the LiveCD and after installing.  When I boot the LiveCD (this is the 32-bit standard desktop CD) in normal graphics mode my screen goes blank when it's supposed to be starting X.  It's as if the screen is actually turning off because the backlighting seems to be off.

I didn't have much hope with that since even LTS doesn't work for this laptop in that mode, however it worked a treat with safe graphics mode... not so with Gutsy...

So the next thing I tried was using safe graphics mode.  This one shows me a bit more info - it kind of flashes once (to blank) then reverts to the command line where it has things listed like Starting GDM etc. and then periodically flashes to blank screen and back every 3 seconds or so.

After that I did some searching around the net and specifically these forums and it seems some people have got theirs up and running (although nobody seems to have it as bad as my system) and I have tried roughly the following combination of workarounds, all of which have fixed similar issues with Ati for somebody but none of which works for me:

- Removed quiet and splash from boot options and added:
-- noapic irqpoll noirqdebug
-- noapic acpi=noirq nolapic
I even tried the above two combos without removing quiet and nosplash.

Further googling resulted in me finding the release notes for Gutsy and it seems the Ubuntu folks have acknowledged some issues with Ati but I think that mine are more serious than just a "blank screen".  For what it's worth they suggested adding the following to the Device section of Xorg.conf:

Option "LVDSBiosNativeMode" "false"

I did this (with the detected "ati" driver in use) and it made no difference.  I also tried changing the driver to "radeon" because a "man radeon" was the only man page that suggested this option was available.  No go.

I also tried the old break=bottom option and then modifying xorg.conf to use vesa (works on Fiesty for me IIRC although it's been a few months) but this time round nano doesn't load because it can't find the ncurses library.

Next thing was on to the Alternate iso.  Downloaded that and did a text-based install which worked fine of course.  Now I just have the same problems described above but it loads faster because of no CD loading times :-)  Tried the same fixes on the installed system with the same results.

I did modify xorg.conf to give me vesa and that did the flashing screen thing again (I'm guessing that safe mode graphics uses vesa anyway).  I had a quick look at the Xorg.log.0 (?) file in /var/log and it seems to be complaining about the horizontal refresh rate or something and then it goes on to say that it can't find a usable screen mode.  If anyone would like specific parts of the Xorg log file I will do my best to get it in here but I really don't know what I'm looking for in there or if that is even the problem.

Any ideas?  Anyone having the exact same problems as me?

Regards,
Wayne aka Morkalin

---

### Post by Morkalin on 2007-10-19
Bump...?  Anyone?

---

### Post by Rimfrost on 2007-10-23
Does your machine has a 64-bit architecture? 
I dont know if that's whats causing your problems, but it might be worth a shot installing the 64-bit version of Ubuntu. 
I did it on my machine, which is the same model as yours, and it worked after implementing the "usplash.conf" fix, so it shouldn't be a general incompability problem I think.

---

### Post by finite9 on 2007-10-23
I have this laptop and have been able to use LTS and Feisty just fine (although Edgy did not work whatsoever).

When booting from the LiveCD and upon getting black screen with X, go into a tty console by pressing CTRL-ALT-F1 and login, then edit the /etc/X11/xorg.conf file by typing 'sudo nano /etc/X11/xorg.conf'and change the video adapter to vesa.  Now save the file with CTRL-o, then exit with CTRL-x, log out of the TTY and press CTRL-ALT-F7 to get back to the black X screen and restart X by pressing CTRL-ALT-Backspace.  This will give you a working driver so that you can install the proprietary fglrx driver later (see the community wiki for install guide).  The issue is that the inbuilt ati driver that is autodetected does not support this graphics chipset.  This has been the case right up until Feisty but I have not tried Gutsy yet.

It really is a shame that these issues persist across upgrades and that new posts appear regarding old issues...makes it harder to find 'new' issues in the forums, but this is not your fault, simply a negative aspect of forums.

---

### Post by Rimfrost on 2007-10-23
Not helping with your current problem, but since you also use an Acer machine, you might run into the same problem I did with your WIFI-card once you get your graphics up and running:
[http://ubuntuforums.org/showthread.php?t=587804](http://ubuntuforums.org/showthread.php?t=587804)

---

### Post by bernehj on 2007-10-23
Hi

I have just the same problem with Acer Aspire 5020, furthermore it has started crashing/abruptly turning itself off seemingly random, however I suspect it can be connected to the graphic card from ATI.

I'll never nuy another Acer and recomend everyone else who wants a proper laptop not to bother with Acer. Choose a Laptop supporting Linux from start.

This computer havent been anything else but problems.

---

### Post by Jpr80 on 2007-10-24
Hi folks.

I'm having the same problems with my Aspire 5024WMLi / Mob. Radeon x700. Installation from LiveCD went pretty much with no problems. First boot went ok, but when I added Composite "Enable" to my xorg.conf -> stopped booting -> black screenie. Changed it back, but still black screenie.

Reinstalled, but after the first boot from the hard disk I installed the new fglrx driver (that supposedly supports AIGLX) and modified my xorg.conf again -> stopped booting like before.

So far I've tried fiddling with my xorg.conf with no results, at least not any positive ones. Will keep fiddling some more.

EDIT: I made it work. Here's how:

I figured what the hell, I'll go back to Feisty if this isn't working for me. So, installed feisty, and that went allright. However, as the new fglrx driver for reasons beyond my knowledge refused to install, I upgraded to Gutsy, disregarding the thoughts of wisdom trying to burst out from the pits of my dark mind. But to my disbelief - it worked after upgrade. AND the new fglrx+AIGLX works too, albeit somewhat slowly.

Go figure.

---

### Post by frup on 2007-10-26
I have just finished fixing my cousins Acer Aspire 5024 WLMi which has had some major problems until now

6.06 64bit is what we have had to use until today when I brought round 7.10. 32bit works (this is preferred in this situation for ease of use with flash etc.) After installing acer-acpi the wireless is also functioning correctly.

Suspend and Hibernate don't seem to work. 

At boot I have to press ALT F1 to get the boot process to work (this is usually when Usplash would start) that enables the boot to start text based until GDM.

---

### Post by Jpr80 on 2007-10-26
> **Morkalin said:**
> I did modify xorg.conf to give me vesa and that did the flashing screen thing again (I'm guessing that safe mode graphics uses vesa anyway).  I had a quick look at the Xorg.log.0 (?) file in /var/log and it seems to be complaining about the horizontal refresh rate or something and then it goes on to say that it can't find a usable screen mode.  If anyone would like specific parts of the Xorg log file I will do my best to get it in here but I really don't know what I'm looking for in there or if that is even the problem.

Any ideas?  Anyone having the exact same problems as me?

Regards,
Wayne aka Morkalin

I got past this problem by lowering the refresh rates in my xorg.conf - the defaults definitely did not work. Install in safe graphics mode, after everything hopefully goes well, just drop the rates from your xorg.conf to a value that works. I dropped them to around 40-50, but higher values might work. I just can't be arsed to spend time finding the optimal ones.

Cheers

---

