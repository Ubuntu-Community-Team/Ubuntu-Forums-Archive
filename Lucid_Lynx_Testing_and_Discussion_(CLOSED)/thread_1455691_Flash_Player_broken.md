---
title: "Flash Player broken?"
date: 2010-04-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bwallum on 2010-04-16
Latest Lucid downloads (13:20 GMT Fri 16th), 64bit AMD, ATi IXP400 embedded graphics.

Possibly a streaming issue. Flashplayer runs ....and runs, wheel spins on black screen. BBC iPlayer all works well so also possibly not a streaming issue.

Tried removing nspluginwrapper and installed latest flashplayer.so from adobe labs. No change.

Any ideas on how to get flash working again?

---

### Post by ajgreeny on 2010-04-16
If BBC iPlayer works OK, then surely it is not flash that is the problem, as that is a flash stream.  Is your problem related to specific sites or most other flash sites.

---

### Post by Spektakel on 2010-04-16
> **bwallum said:**
> Latest Lucid downloads (13:20 GMT Fri 16th), 64bit AMD, ATi IXP400 embedded graphics.

Possibly a streaming issue. Flashplayer runs ....and runs, wheel spins on black screen. BBC iPlayer all works well so also possibly not a streaming issue.

Tried removing nspluginwrapper and installed latest flashplayer.so from adobe labs. No change.

Any ideas on how to get flash working again?
I think I have the same issue: flash is installed (latest .deb package from adobe site, tried different versions) and seems to be working on most (video) websites, but not on all. 

More specifically, Youtube video's don't work. The whole player loads (including scrolling recommended video's), but the video itself won't load. There's the black screen with the spinning wheel for a few seconds, and then the message "An error occurred. Please try again later".

I have had this issue since installing Ubuntu Netbook Edition 10.04 beta2.

---

### Post by Gjallarbru on 2010-04-16
I had the same problem, but only on one of my PCs.  This made me think it was a local configuration problem.

I saved my bookmarks to a file, then deleted the .mozilla, .adobe and .macromedia folders in my "home".  When I restarted firefox, flash worked again.

Be SURE TO **SAVE YOUR BOOKMARKS** before deleting those folders.  Of course, the history, the cookies and the saved password will also be deleted.  But it did fix it for me.

Hope this is useful to you.

---

### Post by Spektakel on 2010-04-17
> **Gjallarbru said:**
> I had the same problem, but only on one of my PCs.  This made me think it was a local configuration problem.

I saved my bookmarks to a file, then deleted the .mozilla, .adobe and .macromedia folders in my "home".  When I restarted firefox, flash worked again.

Be SURE TO **SAVE YOUR BOOKMARKS** before deleting those folders.  Of course, the history, the cookies and the saved password will also be deleted.  But it did fix it for me.

Hope this is useful to you.

I just tried this, but it didn't help. The problem remains exactly the same. Searching on these and other forums suggests it's just a cookies problem, but that doesn't seem to be the case here.

Any further suggestions would appreciated.

---

### Post by Gjallarbru on 2010-04-17
**Checking where the problem is...**

I forgot to mention that a new account I created for testing had no problem running flash on the affected computer.

Just to figure things out, make a new user and try Firefox/Flash from that account.  (You can delete the account later.)  If flash works from the new account, then you have something in your account that is screwed and would look no further than files in your home.  Right now, I don't know what files that would be aside from those mentioned earlier..

**What's next...**

If flash doesn't work in the new account, it is system wide.  In the case I would purge the flash plugin and reinstall - Synaptic can do that for you. (restart firefox of course).  If you are using the standard 32 bits plugin, you can apparently use: sudo update-flashplugin in a terminal. (taken from [https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash))

**The nuke...**

If it doesn't work then I would purge the plugin again and perhaps delete the following folders afterwards (if they exist, as take from the french documentation page: [http://doc.ubuntu-fr.org/flashplayer](http://doc.ubuntu-fr.org/flashplayer)).

sudo rm -f /usr/lib/mozilla/plugins/*flash*  
sudo rm -f /usr/lib/firefox/plugins/*flash*  
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*  
sudo rm -rfd /usr/lib/nspluginwrapper  

Of course, all plugins/extensions will be gone, along with bookmarks if you haven't already saved them.  After all that is deleted, along with the original folders I suggested above, I would then proceed to reinstall the plugin.

**Final thoughts**

If you are using the 32 bits flash, you might consider the 64 bits flash plugin.  The link the the English documentation page will tell you how to add the repos and what to use. I'm using the 64 bits flash and it works great aside from a problem similar to that which you described. (fixed with prior method).

Sorry for the trial and error, but that is the extent of my experience and ability.  None of this should prevent your system from booting though, so there is little risk as far as I know.  (Firefox isn't a system critical software).  If none of this works, I'm stomped!

---

### Post by bwallum on 2010-04-17
'super' nuked it I'm afraid, Did a complete reinstall (it's really quite quick and I have been bashing Lucid about a bit). Did the job but I didn't learn much from it. Thanks for all the help.

Along the way I did learn about saving Firefox bookmarks though. [http://ubuntuforums.org/showthread.php?t=1455544](http://ubuntuforums.org/showthread.php?t=1455544)

---

### Post by Gjallarbru on 2010-04-17
Yeah, a joy of Ubuntu and other distros, you're up and running from a fresh install in no time.

Especially when compared to an other ubiquitous OS.

---

### Post by scaine on 2010-04-18
I'm running Lucid 64-bit, fresh install from Beta1.  I've had problems with flash since install.  Originally, I thought it was because I'd restored my firefox profile using FEBE, so I imported all my history, bookmarks and so on from the previous install (Karmic).

But seeing this thread, I tried the same tests using a completely untouched, fresh install of Chromium and I get the same behaviour :

1. Certain flash elements just don't load.
2. Some do, but then won't play.
3. Embedded videos frequently won't play.

For an example, my own (rarely updated) blog has some embedded youtube videos on the front page.  If you click on them, the big "play" button will pulse, but the video won't play.  That's on [http://www.scaine.net](http://www.scaine.net).

But it's hit and miss.  [The Escapist videos]("http://www.escapistmagazine.com/videos/view/zero-punctuation/1546-Battlefield-Bad-Company-2") all play fine.

I'll have a hunt on Launchpad and see if anyone has filed a bug.

---

### Post by zevans on 2010-04-18
Ah I've got this too, and a weird problem with Flash sometimes grabbing the audio devices, even though it's using pulse correctly. I had eradicated all these types of problems on the Karmic partition, so there's some sort of regression in Lucid for sure.

It also seemed strange to me that Flash didn't get installed automatically by anything - surely something in GNOME or Kubuntu (got both installed) ought to pull it in without me needing to type apt-get commands?

Chromium will trigger use of HTML5 instead of Flash on some sites, so that might be a bit of a red herring. Would concentrate on troubleshooting with Firefox.

---

### Post by Gjallarbru on 2010-04-18
I've tried everything, including videos of [http://www.scaine.net/](http://www.scaine.net/), and everything works on both my laptop and desktop.

I'm using the 64 bits plugin from the sevenmachines ppa though.  I've read that the 32 bits flash plugin in a 64 bits Ubuntu is subject to weird unpredictable behavior, including, but not limited to, buttons not working.

What are you guys using?  Unless you added the ppa repo for flash 64bit, you are using 32 bits in a 64 bits environment. Ubuntu default repos don't have the 64 bits plugin.

So really, are you using 32bits flash or 64 bits?

just in case:

sudo add-apt-repository ppa:sevenmachines/flash
sudo apt-get update && sudo apt-get install flashplugin64-installer

---

### Post by bwallum on 2010-04-18
scaine.net works for me from a standard 64bit beta2 install

---

### Post by Spektakel on 2010-04-19
> **Gjallarbru said:**
> **Checking where the problem is...**

I forgot to mention that a new account I created for testing had no problem running flash on the affected computer.

Just to figure things out, make a new user and try Firefox/Flash from that account.  (You can delete the account later.)  If flash works from the new account, then you have something in your account that is screwed and would look no further than files in your home.  Right now, I don't know what files that would be aside from those mentioned earlier..

**What's next...**

If flash doesn't work in the new account, it is system wide.  In the case I would purge the flash plugin and reinstall - Synaptic can do that for you. (restart firefox of course).  If you are using the standard 32 bits plugin, you can apparently use: sudo update-flashplugin in a terminal. (taken from [https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash))

**The nuke...**

If it doesn't work then I would purge the plugin again and perhaps delete the following folders afterwards (if they exist, as take from the french documentation page: [http://doc.ubuntu-fr.org/flashplayer](http://doc.ubuntu-fr.org/flashplayer)).

sudo rm -f /usr/lib/mozilla/plugins/*flash*  
sudo rm -f /usr/lib/firefox/plugins/*flash*  
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*  
sudo rm -rfd /usr/lib/nspluginwrapper  

Of course, all plugins/extensions will be gone, along with bookmarks if you haven't already saved them.  After all that is deleted, along with the original folders I suggested above, I would then proceed to reinstall the plugin.

**Final thoughts**

If you are using the 32 bits flash, you might consider the 64 bits flash plugin.  The link the the English documentation page will tell you how to add the repos and what to use. I'm using the 64 bits flash and it works great aside from a problem similar to that which you described. (fixed with prior method).

Sorry for the trial and error, but that is the extent of my experience and ability.  None of this should prevent your system from booting though, so there is little risk as far as I know.  (Firefox isn't a system critical software).  If none of this works, I'm stomped!

Thanks for all the help and suggestions! I have tried all of this, except the 64 bits flash plugin. Removed, uninstalled, reinstalled everything a lot of times, without any improvement.

In the end, I decided to just back everything up and reinstall UNR 10.04 beta2 completely, updating the installer first. After this, a regular install of flash worked perfectly. Solved, but not so clean...

---

### Post by scaine on 2010-04-20
Yeah, well, I've used Febe for about... 2 and half years now, so I'm not really keen to do a clean install.  I'm not losing that kind of browse history, but the reality is that it's almost certainly what's causing my problem.

I'll try that 64 bit repo - I just installed ubuntu-restricted-extras, so yep, that'll be 32-bit flash then.  This is the first time I've tried a 64-bit install.

[edit : or maybe not the source of my problem!  I created a new profile with "firefox -ProfileManager" and it exhibits the same problem.  Guess I'll try that 64 bit flash to see if that has any effect]

---

### Post by franc00018 on 2010-04-20
All video plays in konqueror(with both KHTML and webkit) and in Firefox
But, I have no sound in any of them. Sound is working great in every other apps I tried.

I have an intel onboard soundchip (which works well but I never use it), usb M-Audio MobilePre soundcard (which I always use) and a usb webcam

Here are my installed package details
[http://pastebin.ca/1870553](http://pastebin.ca/1870553)

---

### Post by Gjallarbru on 2010-04-20
@ franc00018

I found 3 possible solutions:

**1)** [http://ubuntuforums.org/showthread.php?t=255422](http://ubuntuforums.org/showthread.php?t=255422)

**2)** The other could be as follows (english translation follows)

Le problème était tout bête. Par défaut, le volume du son des animations flash est à zéro et non pour le reste.

- Cliquer sur le haut-parleur dans la barre des tâches de KDE
- Cliquer sur Mixeur
- Réhausser la jauge avec le signal bleu 

**ENGLISH**

By default, volume of flash animations is at zero, but such is not the case for the rest.  [To solve]

- Click on the speaker icon on the kde taskbar
- Click on the mixer
- Raise the volume on the "blue signal"

Since I'm under gnome, I can't verify the precision of these instructions.  I thought I'd post them in case they were meaningful for you.

**3)** Apparently, the package padevchooser might also help set up your sound for flash.  Lauch it in a terminal.

Good luck!

---

### Post by Yellow Pasque on 2010-04-20
A great script to install 64-bit Flash (which works better than the default of 32-bit Flash + nspluginwrapper): [http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)
Getting Flash (and other ALSA apps) to play nice with pulseudio: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

---

### Post by Trespasser on 2010-04-20
Flash Player 10.0.45.2 64 bit sucks for flash games ala Facebook (my wife , not me...:)). On the other hand running flash player 10.1 RC with nspluginwrapper works great. YouTube videos play great as well. The 10.1 beta 3 gave me problems but the RC is very smooth. Give it a try.

---

### Post by scaine on 2010-04-23
Quick update - I uninstalled flash-installer from the repo, downloaded the 64-bit 10.0 plug-in from the flash site, extracted it and copied it to /usr/lib/mozilla/plugins and voila : all working again.

Can't comment on the performance (haven't used it much since last night), but at least I can click on embedded flash videos again to play them successfully.

Thanks for the suggestions everyone.

@bwallum : Manually saving your bookmarks is pretty tedious.  I fully recommend that you look at either "syncplaces" for bookmark sync/backup/restore, or for the full cahoona experience, try FEBE.  You'll never look back!  :)

---

### Post by sdowney717 on 2010-04-23
xmarks keeps a restore-able  bookmark history.

[https://login.xmarks.com/?referrer=https%3A%2F%2Fmy.xmarks.com%2F](https://login.xmarks.com/?referrer=https%3A%2F%2Fmy.xmarks.com%2F)

---

