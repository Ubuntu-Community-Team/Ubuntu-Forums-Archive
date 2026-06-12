---
title: "Alpha5 and flash-nonfree plugin - Firefox"
date: 2009-03-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rbmorse on 2009-03-01
Anyone else having problems with Firefox/flashpluging-nonfree on A5?  Worked just ducky on A4, but I did a dist-upgrade today and now any flash page just locks Firefox up tight.

---

### Post by kansasnoob on 2009-03-01
Yes! The new "flashplugin-nonfree" (10.0.22.87) stopped working for me so I had to remove it and install the "adobe-flashplugin" which is 10.0.12.36.

BTW I must always use Flashblock (currently 1.5.8), not the repo version but just by going to Tools > Add-ons > Get Add-ons.

Otherwise web pages that are heavily flash laden cause me to crash continually!

---

### Post by kansasnoob on 2009-03-01
Oops the smiley should be - 1.5.8

---

### Post by philinux on 2009-03-01
Working ok here. No crashes at all

---

### Post by perlluver on 2009-03-01
I noticed that when I got the update to the new flash plugin, my computer feels like it's dragging along.  I think I will just wait it out and see what happens.

---

### Post by kvarley on 2009-03-01
Thanks, this helped me. I thought it was just my PC.

You can also now get the flash plugin from the Adobe website as a .deb file.

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Just select the Ubuntu version.

---

### Post by dBuster on 2009-03-01
No problems here but then again I am running 64 bit and never installed the non-free flash... only the 64 bit flash was ever installed and updated on this machine...

---

### Post by waspbr on 2009-03-02
I must say I am worried, I tried using the flash non-free from the medibuntu repos but I ended up getting the infamous grey boxes. So I have decided to use the beta (alpha drivers) [http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html"). So that fixed the breakage problems. But now... when I try to watch a flash video the CPU load goes up by a lot, and soon enough my CPU temperature is 80 something degrees. 

Sure I am running on a small laptop, it gets warm every once in a while but 80 C degrees is just too much... what gives, why is flash so damn heavy in ubuntu?

---

### Post by Flywaver on 2009-03-04
Here I installed Alpha 5 fresh this morning, then I go to adobe, select linux...ubuntu 8.04+, points me to: install_flash_player_10_linux.deb
I d/l, and when I extract it says: Error: Wrong architecture 'i386'

And then I install gnash...works fine in FF! I install Opera, and then the problems starts...when I had opera and FF open at once it would completely halt the system...found out it was flash related, then tried to manually install an old flash 9 which worked...but on youtube a video would simply dissapear after a few seconds! :(

This is really annoying :rolleyes:

Cheers!

---

### Post by Nullack on 2009-03-04
Why dont you just use the Ubuntu repos. This works and deals with the nsplugin for 32bit on 64 bit platforms.

Its not feasible to be using the 64bit native plugin yet. Its missing major features, such as OpenGL acceleration.

---

### Post by Flywaver on 2009-03-04
> **Nullack said:**
> Why dont you just use the Ubuntu repos. This works and deals with the nsplugin for 32bit on 64 bit platforms.

uhhh...?? Newbie question here...but what? :D
Which flash plugin and where lol...tried through synaptic, adobe...no luck! :(

---

### Post by Kow on 2009-03-05
> **Flywaver said:**
> uhhh...?? Newbie question here...but what? :D
Which flash plugin and where lol...tried through synaptic, adobe...no luck! :(

You need to enable the multiverse repository in System -> Administration -> Software Sources. You may need to enable the universe repository too. Then install flashplugin-nonfree from synaptic.

---

### Post by jerrylamos on 2009-03-05
Flash?

Well, I cheat.  I've got a libflashplayer.so which I copy into /usr/lib/mozilla/plugins, fire up Firefox and away I go.  

The .so is dated November 18 and works fine even full screen for youtube, BBC news, etc.  That is, works fine except TA DA!  PulseAudio is crackling again.  Maybe some day it'll settle down.  See the sticky at the top of jaunty forum.

Flash video copied in to the lib works fine on today's ubuntu daily build 20090305 (finally fits 700 mb).

Jerry

---

### Post by blackened on 2009-03-05
> **vitium said:**
> Thanks, this helped me. I thought it was just my PC.

You can also now get the flash plugin from the Adobe website as a .deb file.

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Just select the Ubuntu version.

This was what I did a few days ago. The repo version was making all videos run at 2x normal speed.

---

### Post by Nullack on 2009-03-06
Getting it from anywhere but the repos is problematic, especially the need to use 32bit lib on a 64 bit platform. The native 64bit flash doesnt support OpenGL acceleration amongst other features.

---

### Post by ubu-for on 2009-03-06
> **Flywaver said:**
> And then I install gnash...works fine in FF!
How could you install gnash?

Synaptic doesn't find it, even if I turn on universe, multiverse and backport!

---

### Post by nanog on 2009-03-06
Because the 64 bit alpha2 *just works* on the dozen or so boxes I administer while nsplugin-wrapper constantly fails. And working flash is a requirement because our university sites run under it. 64 bit is also a requirement for algorithmic reasons.

---

### Post by Nullack on 2009-03-06
> **nanog said:**
> Because the 64 bit alpha2 *just works* on the dozen or so boxes I administer while nsplugin-wrapper constantly fails. And working flash is a requirement because our university sites run under it. 64 bit is also a requirement for algorithmic reasons.

64bit has no opengl acceleration

---

### Post by Flywaver on 2009-03-06
I installed 10.0.22.87 through synaptic this morning and opera and FF go nuts! 

gnash was working fine in ff but would make opera go nuts! :(

Forget the last line, I removed flashplugin-free (10.0.22.87), installed gnash, fired up ff and as soon as I encountered a site that uses flash it made gnash crash/quit!

---

### Post by Flywaver on 2009-03-08
ok it's the npviewer.bin that crashes in ff and opera!

---

### Post by gjoellee on 2009-03-08
> **philinux said:**
> Working ok here. No crashes at all
same here

---

### Post by noworry on 2009-03-13
I also had this problem. But after reinstalling flashplugin-nonfree, it is back to normal :)

---

