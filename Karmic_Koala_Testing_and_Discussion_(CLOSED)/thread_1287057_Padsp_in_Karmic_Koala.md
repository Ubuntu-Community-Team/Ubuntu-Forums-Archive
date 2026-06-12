---
title: "Padsp in Karmic Koala"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by UpSignal on 2009-10-09
Guys, what's up. hey, just installed Karmic from the scratch, it's awesome, anyway, i was adding the command "padsp firefox %u" to my firefox shortcut, and i was blown away, it doesn't run at all!! as soon as i remove the "padsp" it runs fine! oh man, how can i make it run with padsp? i need it, because it's the only way to make java sound to work with the rest of the applications. Otherwise, java "steals" all the sound and i can't listen to mp3 or such :(

---

### Post by UpSignal on 2009-10-10
bump

---

### Post by ankspo71 on 2009-10-10
Hi,
I have never heard of this until now, so I don't know if this will help or not.

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
> If you experience problems with audio synchronization after installation, you may need to edit the file /etc/firefox/firefoxrc. The line referencing FIREFOX_DSP should read FIREFOX_DSP="padsp"

[FONT=Verdana]
[/FONT]James

---

### Post by UpSignal on 2009-10-10
Hum, yeah, i know that way man. Problem is.... since firefox version 3, the RC file is no longer there, so i can't edit it. Even if i create the file, it's useless. So, i use to add the command "padsp firefox" directly in firefox shortcut. But it's really weird, in karmic firefox doesn't even open up, with that on the shortcut. 
It's curious, so many ubuntu versions released..and this issue was never fixed. And it won't be, as far as i see. I would say, people don't use java too much, so they don't complain. Yes, i agree that this must be an issue with sunjava too...not just ubuntu fault, but anyway....i allways used this workaround, and now it doesn't work. It's pretty annoying having to close the java applet and the entire firefox, so it can "release" audio back to the rest of my computer :s

By the way, the game i play is "Runescape", don't know if you guys play it too. Anyway, i like to enable sound effects on the game, and then have my own mp3 player running. In this case, without padsp, i have 2 options:

 - listen the game sound and silence the rest of the computer
 - listen all of my computer and silence the game

pretty laughable :D

---

### Post by UpSignal on 2009-10-10
Wow.... just found out some more cool stuff....
As i'm watching youtube, i can't get sound notifications from AMSN  or Emesene or whatever. Nice... so, i'm guessing Karmic uses another audio engine. not pulse
I like karmic a lot, but this audio stuff is giving me a hell of a hard time. hope you guys can help, or i'm changing for jaunty

---

### Post by sandyd on 2009-10-10
pulseaudio has always been a major pain in the rear...
why not simply
```

sudo apt-get remove pulseaudio*

```
makes life simpler.

the system will then fall back to ALSA, which works wonders.

---

### Post by jpkotta on 2009-10-10
I gave up on PA [1].  Anyway, /usr/bin/firefox is a script that starts up the real Firefox executable.  Try adding a padsp to the relevant part of that script.  I just glanced at it, it's probably the line like
```
exec $LIBDIR/$APPNAME "$@"
```
```
exec padsp $LIBDIR/$APPNAME "$@"
```

[1] I couldn't get it to work well with an SDL game I have.  I'm guessing it's because the game is a 32-bit binary and my system is 64-bit.  We'll see if it gets better or if that game ever gets ported.

---

### Post by clive littlewood on 2009-10-10
Hi All

What am I doing wrong !!!!!!!

Sound in Karmic is fabulous for me.

The first time I have been able to use the laptop speakers with any effect on Ubuntu.

Well done devs

Clive

---

### Post by UpSignal on 2009-10-10
removed pulse audio, and i got a litle better. Now i can play all the stuff at the same time But java.... so, back to point 1. oh, and now i can't go to sound preferences also, because it says, waiting for device

---

### Post by UpSignal on 2009-10-11
ok, going back to jaunty. i'll take a look at the final version, but something's telling me... i might skip this version, for the first time. thanks guys

---

### Post by Mr. Picklesworth on 2009-10-11
To the completely off topic posters: PulseAudio isn't causing the problem here. It is your audio driver. File bugs and the problem may get fixed. Complain about PulseAudio, which is actually a damn good piece of technology, and nothing will change because *you are wrong* in the first place. Granted, the OP's issue is probably a bug with padsp ;)

(Disclaimer: I had crackly sound and horrible lag in Jaunty. It was traced back to Intel's HDA drivers and resolved there. The PulseAudio sound server was not touched).

Padsp worked for me just a little while back when I used it for flightgear, so it's either specific to Firefox or your particular setup. Either way, kind of odd. The underlying software definitely hasn't changed since I used it and it worked...
[https://launchpad.net/ubuntu/+source/pulseaudio](https://launchpad.net/ubuntu/+source/pulseaudio) (the pulseaudio source package also creates pulseaudio-utils).
Do you get any output at all in the terminal? Can you diagnose which application is crashing?
I couldn't find a bug report about your problem, so it would be worthwhile to make Firefox + padsp crash and then open the apport bug report dialog that appears in your notification area, or to run ubuntu-bug padsp. (The former would be the most effective).

It would be a shame if you guys missed PulseAudio due to the surrounding components not being up to snuff, since it works really beautifully this time through. Bluetooth audio is finally working as well as it does on handheld devices. (And then some since you can bounce individual streams to / from the headset). Volume can exceed 100% :)

---

### Post by Axx83 on 2009-10-27
NONSENSE

first you should explain what card you have

try: alsamixer -Dhw
in a terminal and check this out

then try this:
[http://ubuntuforums.org/showpost.php?p=7580623&postcount=3](http://ubuntuforums.org/showpost.php?p=7580623&postcount=3)

then this
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

and see if it helps

for me pulseaudio works PERFECTLY and there is no issue at all

---

