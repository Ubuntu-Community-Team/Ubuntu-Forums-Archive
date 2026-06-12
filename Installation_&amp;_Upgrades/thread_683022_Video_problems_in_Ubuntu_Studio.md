---
title: "Video problems in Ubuntu Studio"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by lil0tik on 2008-01-30
Hi All -

Until last evening i was running a vanilla Ubuntu (Gutsy) install with no problems whatsoever on a Dell Inspirion laptop w/ ATI Xpress 1150 video chipset, and video drivers installed via Restricted Drivers Manager.  I decided to install the Ubuntu Studio audio package, desktop, and realtime kernel, and since then I am having terrible video-glitch problems.  

In either the generic or RT kernel, I get a lot of glitching on startup and shut-down; it looks like it is trying to adjust the screen resolution or something.  

With the RT kernel, the display problems become much worse.  Upon almost any interaction with the desktop (opening windows, etc), there is a lot of glitching, diagonal "wipes" of distortion across the screen, and very slow performance.  

Is there some known issue with UbuntuStudio / rt-kernel and the ATI drivers (which I've heard are problematic)..?  Any help here?  Any more information I can give?

If there is a reasonable way to revert the system by removing the ubuntustudio-desktop, ubuntustuido-audio, and linux-rt packages, I'll take that route too.  I'd just rather not have to reinstall Ubuntu altogether (though it's still a LOT faster than Vista).

---

### Post by Khidr on 2008-02-06
I'd love to know if you figured it out.  I have the same issue on a dell m1330...  I got most of it working again, but it was definitely slow going,

---

### Post by lil0tik on 2008-02-06
No, unfortunately I didn't; I don't usually give up too quickly, but I did on this one, mostly because I just recently got the system and was just anxious to use it!  

I reverted the system back to a vanilla Gutsy install, and installed the software I wanted manually; as lI'm not doing a lot of intense real-time music making, the rt kernel doesn't really make that much of a difference to me.  I mainly just wanted to experiment with it.

If you have any insights into the problem, though, I'd certainly like to hear them, as I plan on trying again sometime in the near future!

---

### Post by lapcat66 on 2008-02-06
I found that generic gutsy + ubuntu studio installed from synaptic behaved very differently for audio than installing ubuntu studio from the dvd, even though the apps and the rt kernel were the same.  There must be some configuration issues with the former path.

You might want to try installing ubuntu studio from the dvd and see if that improves things.

---

### Post by lil0tik on 2008-02-06
Thanks for the info!  I'll try a fresh DVD install next time.

---

### Post by Khidr on 2008-02-06
for what it's worth, I'm dual booting ubuntu and vista, and my workaround is this:  the original (generic) build of ubuntu is still on there as a choice, the rt kernel was simply a choice I avoided.   I just choose generic when I boot, and I get 100% of the compatibility back, but all of my extra programs and settings transfer.  So, basically, I threw in the towel too.   

May not help you depending on your setup, but I figured I'd share.

---

### Post by bwtranch on 2008-02-06
Hate to sound like a school teacher, but make backups. This will eliminate all your screwups.

---

