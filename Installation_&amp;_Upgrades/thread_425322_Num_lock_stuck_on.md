---
title: "Num lock stuck on"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by leona on 2007-04-27
Install Fiesty on my IBM Thinkpad 600x and it seems the number lock is stuck on, I can't turn it off, so only half of my keyboard is usable, I can't type in terminal or anything, it happens just after I log in, how can I disable the number lock?

Thanks.

arr quick update SHIFT+NumLk turned it off, but the light stayed on which was confusing me.
I think I see from the bug tracker that this is known Kernel bug. 
Still amuses me that things that where working fine in old versions get broken with updates :) old adage, if its not broke, Don't fix it!

Hum, thought I had fixed, this but it keep turning the num lock on every time I start up, can I do something about that?  Also it turns it on if I press caps lock. WtF is that about?

---

### Post by zvacet on 2007-04-28
This is how to turn it on.Look if you have that lines and delete them.That is all I can think of.

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_turn_on_Num_Lock_on_GNOME_startup]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_turn_on_Num_Lock_on_GNOME_startup")

---

### Post by leona on 2007-04-28
thanks, but those lines whee not there, do you think I could follow that and put 
```

if [ -x /usr/bin/numlockx ]; then
 /usr/bin/numlockx** off**
fi

```
?????

---

### Post by Jingo on 2007-04-29
Same problem here.

This problem comes and goes... worked fine on edgy, didn't on dapper or breezy(can't remember). Works fine with external usb keyboard though.

Try opening gconf-editor, and search for "numlock".
Turn off "remember_numlock_state".
Turn off numlock "numlock_on".

This is what I did, now numlock is always off, when I log in.
Don't know about the caps-lock problem... never seen that one.

/Jingo

---

### Post by TekNullOG on 2007-04-30
The Numlock doesn't work on my IBM T43. When I dock my laptop at home, i turn Numlock on with my external keyboard but if i forgot to turn it off when i would take the pc to go and I would be unable to type with the built in keyboard till i was next to an external to turn it off again. Nightmare!

Thanks to your posts, i am free of that! It is always turned off by default.

Very useful tip Jingo!!!

---

### Post by jganetsk on 2007-04-30
I have the same exact problem as the first poster. Caps lock turns num lock on as well.  I have an IBM Thinkpad T41p. Any help would be MUCH appreciated.

---

### Post by leona on 2007-04-30
> **Jingo said:**
> Same problem here.

This problem comes and goes... worked fine on edgy, didn't on dapper or breezy(can't remember). Works fine with external usb keyboard though.

Try opening gconf-editor, and search for "numlock".
Turn off "remember_numlock_state".
Turn off numlock "numlock_on".

This is what I did, now numlock is always off, when I log in.
Don't know about the caps-lock problem... never seen that one.

/Jingo

Arr, good idea, worked a charm, after I remembered to search for a key 'name' ! :)

Thank you

---

### Post by TekNullOG on 2007-05-03
Ok, first my problem wass that Numlock would remember my previous settings so when i would leave home, i would be stuck with my caplock on since the button to turn it off doesn't seem to work on my T43 under Ubuntu Feisty.

I fixed this thanks to posts above but now i get that syndrome of CapLock turning on my NumLock at the same time. How annoying!!! For some reason, my NumLock button works now so i can turn it off when it happens but then the NumLock light stays on!

Basically, this is not a major problem but it is enough to be really annoying!

How do we fix the CAPLOCK / LumLock problem and how do we turn off that darn light? Any suggestions?

---

### Post by leona on 2007-05-03
Arr so its not only me with this Caps lock turning on the Numlock as well problem then, phew, I was worried there.  Yep my light stays on as well, 
[Its been filed here]("https://bugs.launchpad.net/ubuntu/+bug/92482") and [Here]("https://bugs.launchpad.net/ubuntu/+bug/109879")
There is something in the [wiki]("https://wiki.ubuntu.com/LaptopTestingTeam/HotkeyResearch") that they say might help, I've not read it yet.

---

### Post by TekNullOG on 2007-05-04
> **leona said:**
> Arr so its not only me with this Caps lock turning on the Numlock as well problem then, phew, I was worried there.  Yep my light stays on as well, 
[Its been filed here]("https://bugs.launchpad.net/ubuntu/+bug/92482") and [Here]("https://bugs.launchpad.net/ubuntu/+bug/109879")
There is something in the [wiki]("https://wiki.ubuntu.com/LaptopTestingTeam/HotkeyResearch") that they say might help, I've not read it yet.


Please let me know as soon as you find something. I will keep looking too. I appreciate the help!

Cheers

---

### Post by Titan3025 on 2007-05-20
I have the same problem with numlock on my t43p. I cannot turn the numlock led on or off with my t43p keyboard. Only with a USB keyboard which is attached to my laptop from time to time :-(

---

### Post by racekarl on 2007-06-27
Just wanted to chime in that I have the exact same set of symptoms on my Thinkpad T42

To wit:

- When undocked (e.g. no external KB), the numlock key never turns off even when num lock is actually off
- Turning on caps lock also turns on num lock

---

### Post by Titan3025 on 2007-07-02
yeah true.. caps lock has the same effect on my laptop. 

Everything worked fine in Edgy. Hope Feisty will be fixed soon.

---

### Post by cliptin on 2007-07-17
Thinkpad X31

Same problem. 

The num lock light comes on but the numbers do not work. After hotkey press, the num lock light stays on but the letters work.

---

### Post by jshayden on 2007-07-19
Thinkpad Z60t

Numlock "flashes" and and off consistently; Not just the light, either.  Numlock is actually enabled every 3 seconds for about 0.5 seconds.

I'm using Edgy.  It wasn't always this way in Edgy.  Must have been caused by an update...

Josh

<UPDATE>
I upgraded to Feisty today; Didn't fix it
</UPDATE>

<UPDATE2>
FIXED!!  I uninstalled the package *tleds*, and all is well.  NumLock and CapsLock work as designed, without interfering with one another.
If you have a thinkpad, make sure you don't have this package installed.
</UPDATE2>

---

### Post by Captain Trips on 2007-08-29
I had the same Problem. But this helped:

[http://kogs-www.informatik.uni-hamburg.de/~meine/thinkpad](http://kogs-www.informatik.uni-hamburg.de/~meine/thinkpad)

---

### Post by cliptin on 2007-09-02
> **cliptin said:**
> Thinkpad X31

Same problem. 

The num lock light comes on but the numbers do not work. After hotkey press, the num lock light stays on but the letters work.

To clarify, at the login screen the num lock is off by default. This is correct behavior. After login the num lock defaults to on and the light will not go off even if num lock is turned off.

---

### Post by evaristegalois on 2007-09-20
Just had a similar problem and want to post the solution, as described above. I upgraded to feisty, everything worked fine. Then I plugged in a USB keyboard into my IBM Lenovo Thinkpad R40 2722. After I unplugged it, the laptop keyboard had numlock turned on and there was no way to turn it off. The laptop usually turns off numlock by pressing Shift NumLk but that didn't work (it didn't have anything to do with the laptop itself anyways because when I logged in the keyboard still worked -- only when I was inside gnome did the trouble begin and persist). 

Solution:

open the terminal (Applications > Accessories > Terminal)

type "gconf-editor" <ENTER>

in the Configuration Editor go to Edit > Find

enter "numlock" in the search field and turn on "Search also in key names"

Turn off "remember_numlock_state".
Turn off numlock "numlock_on".

Worked for me.

---

### Post by cwgannon on 2007-09-24
evaristegalois:

Thank you for that solution -- it's very much appreciated.

---

### Post by soysaucesam on 2007-09-29
I had the same problem with an IBM R40.  I stumbled across a mouse-only solution (I didnt have a USB keyboard handy and obviously the commands wouldnt work half of the keys dissabled)

I went to System > Preferences > Keyboard > Layout Options > Use Keyboard LED to show alternative group
Then I checked the box that said "NumLock LED shows alternative group"

Then the keyboard worked normally....

---

### Post by Titan3025 on 2007-10-27
@soysaucesam: didn't help with my t43p :(

I am running Ubuntu Gutsy

---

