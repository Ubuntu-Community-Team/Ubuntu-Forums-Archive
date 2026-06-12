---
title: "SLOW graphics"
date: 2011-04-24
forum: Installation &amp; Upgrades
---

### Post by kakashi_12 on 2011-04-24
I just reinstalled my OS (Ubuntu 10.04) and on a new and faster drive than before. And now it's running slower! wtf?!!?
 
I was an IDE drive before and not it's SATA and at higher RPM's.
The first thing I noticed was that my game, "Armagetron" was not the same. The graphics are really screwed up in it. It looks like a diff version altogether! and i can't find any other versions.
Also the controls were different! I have never had to change the controls before.
 
This is what it use to look like before the format:
[http://gaygamer.net/images/632.jpg](http://gaygamer.net/images/632.jpg)
 
This is what it looks like now:
(see below)
 
Then I played some other games just to see and test. They don't look different but they DEFINATELY LAG.....
LIKE LLLLLLLLLLLLLLLLLLLLLLLLLLAAAAAAAAAAAAAAAAAAAAGGGGGGGGGGGGG!!!

---

### Post by kakashi_12 on 2011-04-24
I just tried the windows version and it works fine, minus the controls are still different.

The only thing that is different (minus the drive) is that i did not make a swap partition this time. but i was told that would not matter if i had 8 GB of RAM and a quad core. What's the point of having all this power if the pc won't use it!?

---

Ok, so i went to search for drivers. and found the accelerated graphics driver. i installed, activated, and rebooted. THAT solved the slow issue. But that still does not explain why the walls in my game are missing or are black! I have messed with ALL the setting. If anyone else has this game and can give me a screenshot or list of their settings, i'll see if they match. or maybe there is something else missing?! I have uninstalled and reinstalled the game as well.

---

### Post by balta on 2011-04-24
I think (but I may be completely wrong these) that swap must alway be created and its function is not only to compensate a lack of hardware power. I too have a 4-core (17-920) with 8Gigs of ram.I use 4Gigs of swap and everything runs really fine (even steam games play quite fine, even tough I do definitely prefer to run steam under windows).
You may try to create a swap partition using gParted.

---

### Post by kakashi_12 on 2011-04-24
gPart? what will that do... create it in the existing partition?

I just installed in windows and looked at the settings. i see one setting missing. that must be it.

System Setup > Display Settings >
Use SDL OpenGL: On

This setting is not available in the linux version i have. I would download from the site, but I don't know how to install stuff in linux unless i am either using the software center, synaptics package manager, or the terminal. I dont know how to go to a site, download, and install. because when i do, it does not install under applications > games or whereever... plus it just shows as a tgz or zip file without extracting.

can someone inform me how to do that... install without terminal and where to install stuff?!

---

### Post by kakashi_12 on 2011-04-24
I've found the game forum and directed the question there. ill wait to see if i get anything there.

---

### Post by kakashi_12 on 2011-04-25
maybe this will help... (can any of you help with this?)...

[quoted from the Armagetron forum]
kakashi_12 wrote:
I  tried the Windows version and it works fine. I tried going through  settings and found one thing missing that does not show in my Linux  version for some reason. Am I running a diff version?! The setting  missing is "Use SDL OpenGL" under "System Setup > Display Settings "

Reply:
That's just for initialization, it was necessary back in the days of SDL 1.0, but not any more. No significant difference.

A  couple of the rendering settings active in your screenshot are those  used by default if software rendering is detected. Could it be that you  haven't properly reactivated accelerated OpenGL after your  reinstallation? Closed source drivers always require some manual steps.

---

