---
title: "Jaunty install borks xorg confic file"
date: 2009-03-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by zeldarocks on 2009-03-10
I recently attempted to install jaunty Jackalope alpha 5, the install itself went smoothly, but upon rebooting, it gave me "Ubuntu is running in low graphics mode", when I finally got to the desktop, I get a crash report for xorg.conf. I restart again and check Xorg.conf, to my surprise, the config file turns up completely empty... Jaunty essentially borked my system from the inside...

---

### Post by RAOF on 2009-03-10
An empty xorg.conf is, or should be, perfectly fine.  If you're using an open-source driver you shouldn't even need the file /etc/X11/xorg.conf to exist - everything is, or should be, detected on the fly.

Only if you're using a restricted driver, the nouveau driver, or other such non-default driver will you need an xorg.conf.

EDIT: Likely what has happened is that you hit the "fix my xorg.conf" button (or whatever it's called) when Failsafe X came up and offered a couple of options.  This will rewrite your xorg.conf to the default, empty, one.

---

### Post by Ng Oon-Ee on 2009-03-10
Sorry, but is this a fresh install or an upgrade? If its a fresh install you won't have your xorg.conf from a previous install anyway, since there's no way to re-use the previous root.

---

### Post by zeldarocks on 2009-03-10
I had upgraded to Jaunty straight from Intrepid, via internet, not ISO

EDIT: I don't know if I hit the "fix xorg.conf" option, I don't recall getting an option like that. Although I did get an option about X server or something, during boot I got a blue screen, no mouse cursor, saying something about X server if I remember correctly, it had a yes and no option, that's it.

---

### Post by Ng Oon-Ee on 2009-03-10
> **zeldarocks said:**
> I had upgraded to Jaunty straight from Intrepid, via internet, not ISO

EDIT: I don't know if I hit the "fix xorg.conf" option, I don't recall getting an option like that. Although I did get an option about X server or something, during boot I got a blue screen, no mouse cursor, saying something about X server if I remember correctly, it had a yes and no option, that's it.
Okay, so it was an upgrade not an install. Having a blank xorg is fine, as the previous poster said. What's your graphics hardware, nvidia/ati?

---

### Post by zeldarocks on 2009-03-10
nvidia

---

### Post by cornflake000 on 2009-03-11
I've been running jaunty alpha5. It runs without a hitch once I get logged in but I am having the a similar problem to this one.. error messages...

Your screen, graphics card and input devices could not be detected correctly. You will need to configure them yourself.

Then you are directed to low graphics mode. After which you get the message...

There already appears to be an xserver running on display:0. The specified display number was busy, so this server was started on display:1.

Finally I get to the login screen.

Out of curiosity, I looked in /tmp and found an .X0-lock and an .X1-lock. Why would I have 2 display locks? I am only running one graphics interface and one monitor. Since I am still testing out jaunty, I reinstalled and still have the same problem. I have an installation of intrepid on the same machine that has never had this hitch. Both installations are ltsp installs.

Looking over the internet for 3 days, I have still to find a solution that applies even though this kind of thing has come up since 2004 in several distros.

Maybe this can help.  I would sure like to know what's happening here

Thank you ^2

---

### Post by Kow on 2009-03-11
I believe nvidia works without the xorg.conf SO LONG as you are using the ubuntu package and not manually installed from nvidia's website.

---

### Post by cornflake000 on 2009-03-11
I don't think nvidia is a central issue for this problem.  I know it's not an issue for me.  I have seen this on several distros and several versions of Ubuntu on the web since 2004.  Each seems to have a different fix.  I haven't found one yet for this issue.  I guess I'm just going to wait for the proprietary drivers to debug then see what happens.

---

### Post by Tux Aubrey on 2009-03-11
The same problem has turned up in Alpha 5 for me - with no nvidia or other "special" video issue.  It has to go through several loops (as described above) before I get to login to safe graphics mode.  I tried using a working xorg.conf from another installation but with no luck. 

I had installed Alpha 4 successfully and downloaded a fresh daily build of Alpha 5 to give it a spin.

---

### Post by Nullack on 2009-03-11
> **Kow said:**
> I believe nvidia works without the xorg.conf SO LONG as you are using the ubuntu package and not manually installed from nvidia's website.

Why? How is it any different at a binary level?

I dont think so :)

All I have in my conf is to specify the nvidia module, which both the Ubuntu package and the NVIDIA installer do. I routinely run nvidia versions while waiting for Ubuntu to update the repo.

---

