---
title: "Software Center - Skype - Install issues"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Steel-Bunz on 2010-04-23
I installed Lucid RC today. Went into Software Center, added the Skype repository. Then I searched for Skype and tried installing it. Got a "Package can not authenticated" warning, I clicked o.k, then proceeded to install.

I expected the Skype to install. However, it didn't happen and no message thrown got thrown either. I couldn't find a similar issue posted in this forum.

Is it a known issue with software center? By the way, I eventually installed skype through agt-get...

---

### Post by MichaelSM on 2010-04-24
What's the actual problem? Skype is fine wherever you get it from.

I'll say one other thing.....

MANY thanks to the Lucid team for fixing Logitech USB headset/Skype/PulseAudio disasters in Karmic and previous Ubuntus.

Lucid RC picked up the Logitech headset, then there was nothing else to touch. Skype is amazingly clear (even better than W7 which was excellent) SUPERB!

Small bugs with Lucid RC like guessable drop-menus are easy to cope with.

Never happier! 

Mike.

---

### Post by nystire on 2010-04-24
2 things:

1.) If you remove skype (apt-get purge skype) and then try to reinstall it via Software Center, do you get the same problem? if so, please open a bug about it.

2.) Are you running the 32-bit version or the 64-bit version of Lucid?

---

### Post by BrokeMahPC on 2010-04-24
You have to go to applications->Internet->Skype to start it after install?
It doesn't just run automatically like it does on windows. (I'm sure you already know this but have to check)

I always get the .deb from the skype website:
[http://www.skype.com/intl/en-gb/download/skype/linux/choose/](http://www.skype.com/intl/en-gb/download/skype/linux/choose/)
Just double click it to install. Works for me in Lucid.

Want skype to run at startup - go to:
System->Prefs->Startup applications
Choose add:
Name: skype
Command: skype
Comment: it's skype fool (or whatever u want)
Select add
Skype will start at startup
It's great this - the constant rebooting/logging on n off to look at things, sort out drivers, test themes drives everyone on my contact list nuts!:lolflag:

---

### Post by Steel-Bunz on 2010-04-24
My mistake; looks like it is a known issue since Karmic and there are couple of bug reports:(.. 

Synaptic works flawlessly and so is CLI apt-get... I generally don't use Software Center. However, for my newbie friends, I recommended Software Center instead of Synaptic. I advised them against "double-click .DEB" install of any package. That's how I ran into this problem with Skype install.

I am running 32bit Lucid. Skype works well except the microphone "echo" with the default configuration. Have to figure it out...

Thank you for your time... Appreciate it...

---

