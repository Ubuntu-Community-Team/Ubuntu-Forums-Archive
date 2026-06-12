---
title: "Ubuntu Desktop and RAID"
date: 2014-07-30
forum: Installation &amp; Upgrades
---

### Post by Tyler_Meier on 2014-07-30
I'm a rank beginner with command-line os in general. I'd like to pry my reliance on Windows out of my office and make the change, and it seems a reasonable starting point is Ubuntu. I have a secondary system at my desk, and my hope for it is to RAID 5 the 4x 2TB hdds to decrease the probability of catastrophic data loss to insignificant levels. I should add that my experience with RAID is generally absent. What I have accomplished so far is the successful installation of Ubuntu Server, which allowed me to make the system RAID 5, and at that point, I hoped that I would be able to install Ubuntu Desktop to soften the switch from Windows nearly exclusively GUI styled interface to the starkly colored, moderately intimidating, command-line interface of (apparently) most (if not all) properly configured Linux OS. I failed. When I tried to install Ubuntu Desktop, I had ceaseless problems. The farthest I got was to a login screen, that upon proper password entry, would freeze. after repeatedly trying to find a solution (at this point I am several long days into this project) I became somewhat disillusioned with my prior perceived ability to plow my way into Ubuntu with a fairly minimal amount of pain. There is another thread pertaining to my struggles, and [Here]("http://ubuntuforums.org/showthread.php?t=2234050") is that. Please note that my apparent familiarity with commands and command format was due to the bleed-over from my friend who was visiting at the time. Any and all suggestions and help are most welcome. Also, as a side note, my hope is, that at the end, I can use software like Synergy or something similar to use one mouse/kb for both systems without having to physically switch them around. I suppose PuTTy is an option too, but I'm not sure. I was using PuTTy in my earlier attempts, it seems to work fairly well.

In any case, I look forward to all replies and suggestions. Hopefully together we can take the first step toward exiling Windows from my office.

---

### Post by ian-weisser on 2014-07-30
Your description seems to indicate that you wanted to install a Graphical User Interface (GUI) as a mere tool to help set up the server.

Do you _really_ want to set up a GUI?
Or do you simply want to set up the server? Unlike a Windows server, I don't think a GUI will help you much anyway.

---

### Post by Tyler_Meier on 2014-07-31
I'm hoping to set it up initially as just a second computer, running ubuntu desktop, with the disks in RAID 5 configuration. Where I go from there is currently unplanned.

---

### Post by steeldriver on 2014-07-31
If you want to use RAID for **data** security you could just install the regular Ubuntu Desktop iso system on a small regular partition (or additional HDD), then add RAID support after

OTOH if you want help debugging the GUI issues I suggest you bump your other thread with info about your graphics hardware

---

### Post by ken18 on 2014-07-31
I've been running Ubuntu desktop on a RAID system for about 6 months.  I first installed Ubuntu server (to set up the RAID), then upgraded to Ubuntu Desktop.  Seems to work fine.

---

### Post by Tyler_Meier on 2014-08-01
> **ken18 said:**
> I've been running Ubuntu desktop on a RAID system for about 6 months.  I first installed Ubuntu server (to set up the RAID), then upgraded to Ubuntu Desktop.  Seems to work fine.

That's exactly what I'm trying to do. The server install went smoothly (I've formatted and done it a second time as well) and Desktop installs fine as well (I guess) but it repeatedly crashes at the login screen after password entry. I don't understand why or what to do differently.

---

