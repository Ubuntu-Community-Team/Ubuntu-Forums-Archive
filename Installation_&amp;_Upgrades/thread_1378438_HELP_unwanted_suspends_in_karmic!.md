---
title: "HELP unwanted suspends in karmic!"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by bodhidharma on 2010-01-11
Friends,

I have a desktop machine to which I attached a UPS a month ago,
when I was running jaunty jackalope... I haven't set up the UPS
software at all (frankly, because I have no idea how to do so and
need to read some easy HOWTO which I haven't yet found -- any
suggestions?); but it didn't change my machine's behavior at all.

Then I upgraded to karmic koala -- now, when I do not touch the
computer for a while (I don't know exactly how long; certainly
it is less than an hour), I come back and find the machine ...
well, it's either suspended or hibernated (I'm a little unclear
on the difference).  I have to hit the power button, it comes
back, all windows there (although network not), yaddayadda.

Any ideas how to stop this?  I want the machine to stay on!
(By the way, I have no idea if this behavior has anything to do
with the UPS, I'm just trying to describe the power-relevant
configuration information.)

Oh, and I have checked the Power Management in System->Preferences,
and it says "Never" for "Put the computer to sleep when inactive
for:" under "On AC Power"; also "Never" for "Put the computer to sleep
when inactive for:" under "On UPS Power"; also "Hibernate" "When
UPS power is low:" under "On UPS Power".  (So one conjecture
would be that it somehow thinks the UPS power is low, but
we've had good AC power each time this has happened, and the
UPS is new so I don't think this could be it.)  Are there other
controls I should be looking at?

THANKS IN ADVANCE!

---

### Post by SecretCode on 2010-01-11
How quickly does it recover?

Hibernate means all RAM is saved to disk (the swap partition). You can unplug the power, take out the battery if you have one, plug in back in a month later and resume where you were. On a desktop it can reduce your electricity bills to hibernate overnight, so some people do it.

Suspend means everything is put on low power, but the RAM is still in RAM and you need a bit of power. I see no point in doing this on a desktop, but it helps with battery life.

Recovery from hibernation can take 2-3 minutes - longer even than booting up. Recovery from suspend should take maybe 10 - 30 seconds. Any quicker than this and all you have is screen blanking!

I'm not aware of other relevant controls, but it seems hard to get those settings to actually take effect (my screen-blank setting is not what the power management settings say). Try setting them, and then rebooting.

---

### Post by audiomick on 2010-01-11
Hi.
No idea what's wrong, but why don't you try putting everything on "never" for a start, and see if that changes anything. That way you will at least know (maybe) if it is seeing the UPS power level wrongly.

---

### Post by bodhidharma on 2010-01-11
Audiomick -- that's a clever idea... but the "On UPS Power"
options do not include "Never"!  So I don't know how to do
troubleshooting....

Secret Code: well, it comes back in a matter of seconds, so
I guess that's suspend, not hibernate....  Particularly
odd since nothing says suspend at all that I can find
(e.g., the Power Management UPS settings all mention
hibernate, not suspend).

Does anyone know of software that can monitor the UPS's
current state?  ... assuming this has something to do with
the UPS.  If not, does anyone know of anything that tends
to put the machine into suspend after a period of inactivity
(which now seems to me to be about half an hour)?  Which
is different in karmic than it was in jaunty?

Thanks for the questions/suggestions, y'all!

---

### Post by SecretCode on 2010-01-11
A matter of 2 seconds or 10 seconds? 

Do you have a screensaver set? (system > prefs > screensaver)

I don't have a UPS (:oops: though I have many power failures ... Africa) so I can't explore that - don't even get those tabs.

On the 'general' tab can you set 'always display an icon'? That might give some warning.

---

### Post by bodhidharma on 2010-01-11
Secret Code: hey, thanks for the thoughts!

It seems to come back in closer to two seconds than ten... The screen
was in powersaver, the desktop itself (this is a Dell Optiplex 745)
had a power button whose internal LED was *blinking*.  When I hit the
keyboard or moved the mouse, nothing happened.  So I quickly pressed
the power button, and the screen came back on in just a few seconds,
everything seemed OK.

(Funny, I'm running a UPS because I'm in a public university in the
west of the US, so we often loose power.)

Oddly enough, I *didn't* have a screensaver.  I chose one, now
we'll see if that had any effect ... I'm going to teach a class in
a few minutes, so the machine will be idle for a while.

Thanks again....

---

