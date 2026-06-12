---
title: "Installation stalling"
date: 2012-12-05
forum: Installation &amp; Upgrades
---

### Post by Scary Rob on 2012-12-05
I'm trying to install lubuntu 12.10 on a Toshiba SatellitePro L450 17K. When I try to get it to install from a USB pen, I get the first screen (with the checklist of RAM, internet connection etc, all detected as fine) and click "continue," and what I get is the mouse arrow changing to the "busy" wheel. I've let this go on for half an hour and it still hasn't moved on to a new screen or given any indication that it's installing anything (no loading bars or filepaths).

I've tried installing straight from the unetbootin menu and from the desktop icon on a USB boot. I've also tried installing without updates and the MP3 codec.

Ubuntu 11.10 installed and ran fine on this laptop, if a little sluggishly for my liking.

Any advice would be gratefully appreciated at this stage.

---

### Post by ibjsb4 on 2012-12-05
Even though you are installing 12.10, I wonder if you getting hit with this bug.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568)

Post #16 has a possible solution.

---

### Post by 2F4U on 2012-12-05
What are your hardware specs? Did you verify the checksum of the downloaded iso file before putting it on the usb flash drive?
I had problems using unetbootin on several occasions and no longer use it. Can you try creating a liveUSB using something else than unetbootin? Seems as if you are already running 11.04, so you could use the startup disc creator that comes with 11.04.

---

### Post by Scary Rob on 2012-12-06
Thanks, guys. I tried using lubuntu 12.04 instead and that seemed to work.

I did check both the .iso file and the finished pen before installing. Not sure of the hardware specs off the top of my head, but the laptop was supplied with Windows 7, so there shouldn't be any shortfall in terms of RAM etc. (And I also checked that the graphics card wasn't one of the ones mentioned as problematic in the release notes, but that's a side-issue, really.)

I'll try it again at some point using an alternative to unetbootin and see what happens.

---

### Post by Androzani1 on 2012-12-07
Now that 12.04 is installed, can you update to 12.10?

---

### Post by Scary Rob on 2013-03-03
Unfortunately, when the system updates come, there's never a button for a 12.10 upgrade. Which strikes me as a mite odd. I've left it for now, as my computer's functioning happily with 12.04. Not being an advanced user, I'm loath to tempt fate for the minute.

---

### Post by Rex Bouwense on 2013-03-04
To get your computer to report version updates go to menu->Preferences->Software Sources->Updates.  Navigate to "Notify me of a new Ubuntu version" and choose from the drop down menu "For any new version".  Close the window and you should be good to go.

---

