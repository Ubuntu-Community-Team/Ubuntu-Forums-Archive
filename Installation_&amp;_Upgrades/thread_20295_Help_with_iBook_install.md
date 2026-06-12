---
title: "Help with iBook install"
date: 2005-03-16
forum: Installation &amp; Upgrades
---

### Post by Arizona on 2005-03-16
I'm having troubles with installing Ubuntu on an old iBook. I'm not an expert computer user. I'm doing this to test out how an ordinary sod manages Linux.

It's a G3 clamshell iBook, 300MHz with 64 or 128Mb memory (can't remember which but it's more than the 32Mb specified on the Ubuntu Ver 4.10 PowerPC Edition CD cover).

I know that there is a problem with this iBook but I was hoping it wouldn't be fatal. The battery is dead and the iBook can only work off a powerpoint through the adapter. As I understand it, this means the internal clock isn't keeping time. 

Anyway, the install seemed to go OK but when I first tried to boot up, I got 3 error messages just after the Ubuntu logo showed up with a little nice music in the background. As expected, during the boot, there were grumbly messages relating to time-keeping but otherwise things seemed OK. Anyway, here are the messages:

#1 (the message on top of the other two)
Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory. Killing bonobo-activation-server and restarting Nautilus may help fix the problem.

#2
There was an error starting GNOME Settings Daemon. Some things, such as themes, sounds, or background settings may not work correctly.

#3
There was a problem registering the panel with the bonobo-activation server.
The error code is: 3
The panel will now exit.

Having clicked OK on all three error messages, I was left with a blank screen. Is this the grey screen of death?

I re-booted and wrote out all the messages on a scrap of paper and have typed them in here on my normal WinXP machine. I have no idea how to chase any little bonobo monkey around factories so as to get seashells working properly, LOL.

Can anyone help?

Is this installation doomed to failure?

---

### Post by jrronimo on 2005-03-19
Hmm... sounds as if the packages on the install CD aren't well.

During install, did you get any messages about packages dying? Or did you make like me and start the install and come back an hour or two later? :)

If you know how to verify the .iso itself, that would be a good start -- I honestly don't. It's something to do with the md5 sum, I can tell you that, haha.

After that, I'd suggest reburning the .iso, if you can. Maybe at a slower burning speed just in case.

If that all fails, then it's possible that the install .iso has an error in it or the clock issue really is an issue.

---

### Post by yakkmeister on 2005-05-17
[QUOTE=Arizona]I'm having troubles with installing Ubuntu on an old iBook. I'm not an expert computer user. I'm doing this to test out how an ordinary sod manages Linux.

It's a G3 clamshell iBook, 300MHz with 64 or 128Mb memory (can't remember which but it's more than the 32Mb specified on the Ubuntu Ver 4.10 PowerPC Edition CD cover).

I know that there is a problem with this iBook but I was hoping it wouldn't be fatal. The battery is dead and the iBook can only work off a powerpoint through the adapter. As I understand it, this means the internal clock isn't keeping time. 

Anyway, the install seemed to go OK but when I first tried to boot up, I got 3 error messages just after the Ubuntu logo showed up with a little nice music in the background. As expected, during the boot, there were grumbly messages relating to time-keeping but otherwise things seemed OK. Anyway, here are the messages:

#1 (the message on top of the other two)
Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory. Killing bonobo-activation-server and restarting Nautilus may help fix the problem.

#2
There was an error starting GNOME Settings Daemon. Some things, such as themes, sounds, or background settings may not work correctly.

#3
There was a problem registering the panel with the bonobo-activation server.
The error code is: 3
The panel will now exit.

Having clicked OK on all three error messages, I was left with a blank screen. Is this the grey screen of death?

I re-booted and wrote out all the messages on a scrap of paper and have typed them in here on my normal WinXP machine. I have no idea how to chase any little bonobo monkey around factories so as to get seashells working properly, LOL.

Can anyone help?

Is this installation doomed to failure?[/QUOTE]
 I have had this same problem.
Only I have a working battery.

I read your SLUG posts and so forth but I didn't get too far to a solution.
I did a whole bunch of research and I discovered that it is the date stuffing up the bonobo-activation-server.

using 'hwclock' I reset the hardware clock to the true current date and time (as opposed to the false time it was telling the system, as you know it was circa 1905)

> sudo hwclock --set --date "05/18/2005 04:20:00"

This set the time to 4:20 am on the 18th of May, 2005.
This is the *hardware clock setting*
I think there is a function of the 'date' program that resets the system time to the hardware clock, but I don't know it.
Instead I used:

> sudo hwclock --hwtosys

Then I tested it with the 'date' function, to make sure it worked.
After it was OK, I rebooted, using:

> sudo shutdown now

Then turned off the machine, then on again.
Expecting the worst, I was pleasently suprised!

Ubuntu does run a little slow though ...
But it runs now.

In all it took me ~4 hours to debug this.
PHUN!

---

### Post by yottzumm on 2005-11-20
I had someone install the Live CD on an iBook and her power went dead
after she turned off the machine (she thought it was too slow, I guess).
I am across the Pacific from this person, so it's hard to diagnose.  The
machine sounds like it is kaput.  Perhaps something happened to the
battery on her machine as well?  Thanks for any help you can give.
:( 
yottzumm

---

### Post by jeffburg on 2006-04-19
im having the exact same problems as you guys
it happens on both the live cd and the full install
it was working previously, but then it just stopped and I assume its from the date change.  But those commands you listed above don't work.  the first says that it cannot set the hardware clock by any knowm method.  and the second command if I use hctosys instead of hwtosys (which does nothing) i get the same error as above.

---

### Post by jeffburg on 2006-04-19
ummm in a random try to reset the clock by some other means i booted into the tiger install disc.  there was nothing in there to set the clock with.  However, when i booted back into ubuntu, no errors.... im confused.  But im just gonna not touch the clock.

---

### Post by jeffburg on 2006-04-19
oh and specifically about the computer being blacked... when you turn it on and it makes the bong noise and then nothing.  That happened to me as well.  I just fiddled with everything in the computer until it booted again.  I think what worked was I unplugged it and then remove the motherboard battery and tried to turn it on.  Put it back to gether and it booted.  But again I can't know for sure.

---

### Post by mxcl on 2006-07-07
This bug still struck for me with 6.06.

My clock battery has also apparently failed, I couldn't set the time with hwclock (failed with Cannot access the Hardware clock etc.), so I set it using

date --set "2006/07/07"

And then the gnome session started successfully.

I'm totally new to Ubuntu so I don't know where to report bugs etc. Even though this is Gnome's fault, Ubuntu's quality suffers because of it.

---

