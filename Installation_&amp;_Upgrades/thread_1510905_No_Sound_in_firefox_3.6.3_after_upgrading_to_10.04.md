---
title: "No Sound in firefox 3.6.3 after upgrading to 10.04"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by jimmysheldon on 2010-06-16
Hi

Upgraded my system to ubuntu 10.04 and its looking good. Problem is, i have no sound on firefox. I'm not really too sure where to start looking to fix this, can anyone offer me any direction?

Also, sound is fine for all music player programs etc

Cheers

---

### Post by jimmysheldon on 2010-06-16
No one else out there? I'm sure its an easy fix, just not sure im looking for.

---

### Post by jimmysheldon on 2010-06-16
I still can't "hear" you. lol.

(BOOST)

---

### Post by perspectivist on 2010-06-20
Im having the exact same problem
all other sound apps work, just no sound when watching video in firefox

.... anyone?

:-) thx

---

### Post by PSyMastR on 2010-06-20
By sound you mean in flash videos, or HTML5 videos?  If flash videos (youtube/games/etc...) try reinstalling flash from Ubuntu Software Center.

---

### Post by perspectivist on 2010-06-21
Worked!
Thanks.... so simple, feeling like a tool now
;-)

---

### Post by perspectivist on 2010-06-21
wait... nope.... it was temporary

so I've tried reinstalling flash and firefox, tried chromium as well
and removing all other flash programs except adobe flash 10 player
with no luck
?????

---

### Post by pbhill on 2010-06-25
Same thing... it worked for a while then stopped. No sound again. What gives?

---

### Post by pbhill on 2010-06-29
Anyone out there? 
Just got Firefox 3.6.6 and it didn't help. 
Thought it was a Flash problem (I had messages on certain websites saying I needed to upgrade to Flash 10) Upgraded, didn't help.
It seems to be only Youtube and other web videos that are affected. Once in a while the sound returns, but not for long.

---

### Post by llangwm on 2010-07-07
Same here ... WMVs are fine and files stored by downloadhelper play their sound (even if it didn't inside firefox)

---

### Post by pbhill on 2010-07-07
I'm pretty discouraged with this sound issue... I've installed and uninstalled 10.04 three times over the last few months trying to figure this out. 9.10 doesn't have this problem. I'm trying to avoid a fourth time!
If nobody out there has any ideas, how about a suggestion of where else to look for help? There is some mention of it on the Mozilla forums, but no solution as far as I can tell.

---

### Post by jimmysheldon on 2010-09-03
I'm still struggling with this problem. Such a pain too. I think I may just go back to 9.10, like you said.

---

### Post by thisdishtowel on 2010-09-29
I have a similar problem. Videos, music, etc. doesn't play in chrome/chromium or firefox. 

I found a 'fix' which involved uninstalling pulseAudio and relying on esound. While this allowed me to hear sound played in my internet browsers, I lost control over the volume through my hardware buttons - and there's no big accessible volume button on screen. 

There is a help page about configuring pulseAudio but it involves editing files, folders and menu items that I don't have in 10.04. 

Help?

Thanks.

---

### Post by thisdishtowel on 2010-10-03
I have sound in Chromium now. It involved finding the adobe flash player plugin and moving it into the chromium plugin folder:

sudo cp /usr/lib/flashplugin-installer/libflashplayer.so /usr/lib/chromium-browser/plugins

Then I started Chromium like so:

chromium-browser --enable-plugins

It didn't work right away. I had to restart my computer. 

Firefox is still silent. The same procedure could work for it, maybe.

---

### Post by Paulgirardin on 2010-10-08
I have exactly the same problem.
No sound in Firefox and Opera,reinstalling Flash temporarily fixes it but it is only for a short time.

---

### Post by efflandt on 2010-10-09
When I recently upgraded a 32-bit system (using Update Manger) from 9.10 to 10.04  flashplugin-installer appeared to be installed in Synaptic, but did not show up in Firefox Add-ons Plugins.

For some reason ubuntu-restricted-extras became uninstalled during the upgrade, so I installed that.  Flash is included in that. but that did not fix flash that the system thought was already installed.

So I had to mark flashplugin-installer for **Reinstallation**, then it showed up in Firefox and worked.

Someone mentioned Firefox 3.6.3, but current version after upgrade to Lucid should end up 3.6.10.

---

