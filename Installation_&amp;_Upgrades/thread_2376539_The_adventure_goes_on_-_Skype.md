---
title: "The adventure goes on - Skype"
date: 2017-11-03
forum: Installation &amp; Upgrades
---

### Post by strixtux on 2017-11-03
Dear Foristi,

After an encouraging start I wiped Windows from all my computers and now I have three ones running smoothly on Ubuntu Studio 16.04 (Old Compaq, who does not recognize the mouse nor his built-in keyboard under any 17 version), Ubuntu Studio 17.10 on my workhorse, a Dell inspiron 1525 and a deskktop PC with 64-bit Ubuntu 17.10.

So far so good.

Skype is a different can of worms as it is proprietary and not an original Linux piece. My Shleptops are 32-bitters, so it's futile to install Skype there. So I got it on the 64-bit Desktopper. The Beta version worked fine, then came the update to regular and, well, Skype unionized: it's still present, but no longer works. Shows a blank page instead and crashes.

Does anyone here have an idea what happened? Deinstall and reinstall gave no result with which I could do anything.
The Dektopper is a MSI mainboard with an AMD Athlon three core CPU,NVIDIA PCI bus and 2 GB RAM. 250 MB HDD. All parts work fine and I can't complain about the machine. Brosix does a good job on all three.
Just Skype doesn't...

Just puzzling...

---

### Post by ajgreeny on 2017-11-03
See the thread I started a few days ago with similar, if not exactly the same problem.
[https://ubuntuforums.org/showthread.php?t=2376306](https://ubuntuforums.org/showthread.php?t=2376306)

As far as I can make out the problem disappears if you disable the "Start Minimised" option in the tools menu, though Skype then, of course, starts with an active window that has to be manually minimised back to the panel icon.
I prefer to use the autostart minimised to panel option but that just leads to an empty window frame that is totally non responsive and can only be made to be active by right clicking on the panel icon and choosing "Open Skype", when the proper window appears, and then manually minimising to the panel icon.

It does, however, work fine for me apart from this startup niggle which is already known about by Skype/Microsoft; see
[https://answers.microsoft.com/en-us/skype/forum/skype_linux-skype_startms-skype_installms/skypeforlinux-8901/313d0f20-ed27-4ff8-9a93-6b1494bb3c19?rtAction=1509708311686&auth=1](https://answers.microsoft.com/en-us/skype/forum/skype_linux-skype_startms-skype_installms/skypeforlinux-8901/313d0f20-ed27-4ff8-9a93-6b1494bb3c19?rtAction=1509708311686&auth=1)
and
[https://answers.microsoft.com/en-us/skype/forum/skype_linux-skype_startms-skype_signms/skype-for-linux-8901/606a1b98-b87b-4d57-9386-3ef827b2c8f9](https://answers.microsoft.com/en-us/skype/forum/skype_linux-skype_startms-skype_signms/skype-for-linux-8901/606a1b98-b87b-4d57-9386-3ef827b2c8f9)

---

### Post by strixtux on 2017-11-04
I'll try right now. THANK YOU!!!

---

### Post by Bucky Ball on 2017-11-04
Is this 8.9.0.1? I have that installed, the latest Skype for Linux version, and, while I have read about this issue, it doesn't effect me. What does effect me, and I would assume all Linux users as Skype openly state that it affects the Mac version but say nothing about Linux, is that you cannot send SMS messages to mobiles or landlines.

Not asking for support for this here as there isn't any. It just doesn't work yet, but posting as a warning that SMS to landlines and mobiles will not work if that is one of the reasons you're installing. Skype claim they are working on it and it is coming, but don't hold your breath. If someone has SMS working in Skype for Linux 8.9.0.1, love to hear about it and have my theory proved wrong. ;)

Skype, through their previous treatment of the Linux community, has shown that we are basically second class citizens. They'll fix Linux stuff when they're good and ready. If there was an alternative, I'd be using it, and am only still using Skype as I had about $30 in my account when problems began (first off I couldn't call phones at all, but the latest update seems to have fixed that) so now just trying to burn through that money by making phone calls and then get out until they fix the SMS issue!

Good luck. :)

---

### Post by strixtux on 2017-11-06
Try Brosix. Works fine, even on my 32-bit Shleptop

---

### Post by ajgreeny on 2017-11-06
> **strixtux said:**
> Try Brosix. Works fine, even on my 32-bit Shleptop
There are many alternatives, but as a lot of users have said before, they are useless if you have to contact those who use Skype and do not want to change from that to anything else, and in my experience, that is a lot of people.

Technology inertia! Why do you think there are so many Windows XP users still?

---

### Post by strixtux on 2017-11-07
You are absolutely right. That's life!
I wiped off the new Skype, replaced it by Skype 5.5 beta and well, it works.
...

---

### Post by strixtux on 2017-11-28
Couple of days later, 5.5 screwed up, then the entire contraption crashed. I wiped the HD, made a clean new installation of Studio 17.10 and installed Skype 8.11, crossed fingers and - well it works, sort of.

---

