---
title: "[SOLVED] Firefox 3 upgrade"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by bilijoe on 2008-07-11
I have been trying to upgrade my FireFox from version 2 to version 3, with confusing results.  Every time I go to the Mozilla page and follow the instructions, everything appears to work normally, and after the installation is complete, I have FireFox version 3 running and acting normally.  However, when I shut it down, the next time I open it, I have FireFox version 2 again.  I was attempting the upgrade because something I was trying to install (a FireFox add-on or plug-in) required it.  I am so confused now, I don't even remember what it was I was trying to install in the first place.:confused:  Can anyone tell me what might be going on here?  I'd really appreciate it.

---

### Post by aysiu on 2008-07-11
Two questions:

1. Are you using Ubuntu 7.10 or Ubuntu 8.04?

2. What are the instructions you're following (link, please)?

---

### Post by bilijoe on 2008-07-11
I have been clicking on a "Free Download" button on [http://www.mozilla.com/en-US/firefox/](http://www.mozilla.com/en-US/firefox/), which takes me to a page (at [http://www.mozilla.com/en-US/products/download.html?product=firefox-3.0&os=linux&lang=en-US](http://www.mozilla.com/en-US/products/download.html?product=firefox-3.0&os=linux&lang=en-US)) which opens up a dialog box that starts out with "You have chosen to open firefox-3.0.tar.bz2", and gives me the options "Open with Archive manager (default) / DownThemAll! / dta OneClick!" [I don't even know where those last two came from--I have never seen them before] / or "Save to Disk".  I always save my downloads to disk, and then run them.  When I double click on the firefox-3.0.tar.bz2 icon, the archive manager creates a folder named "firefox".  Inside this folder are a bunch of files, one of which is named "Updater" and has an executable file icon.  (Note: the link I started from was a Linux-specific link, and the update is labeled as an update for Linux.)  When I click on "Updater", either nothing happens, or the system wants to "open" the file with Crossover (Wine), as if it were a Windows executable, but it has no .exe extension--no extension at all.  A little poking around, looking at the contents of some of the other files led me to one named "firefox" with an icon that is a page with a small executable icon on it, the contents of which looked exactly like a complex install script, so I double clicked it.  It did its thing, and then opened a normal looking, [apparently] fully functional copy of FireFox 3, which I used for a while, and then closed.  A short time later, I clicked on my desktop FireFox icon, and up popped FireFox 2.  I looked around the file system, to make sure I didn't have two copies of firefox hanging around, and then re-ran the "Get FireFox 3 free, now" routine.  Same exact result.  Before I ran it this time, I made sure to close all FireFox windows that were opened, when the download window opened, so FireFox itself was not running during the download and install.  When the install was finished, it launched FireFox 3 again.  But again, when I closed that session of FIreFox, and opened another, I got Fire Fox 2.:confused:  I'm confused, and it's almost 100 degrees here today, so I am also exhausted, sweaty, and frustrated.  Any ideas?

---

### Post by Bubba64 on 2008-07-12
It sounds like the panel launcher is the FF2 launcher it doesn't change to FF3 you have to build a launcher in the menu, right click on the menu-edit menus click on internet if that is where you want the launcher to be the click on new item then build a launcher if you right click on the FF2 browser icon-properties you can see the basic type of stuff you need in there. Hopefully somebody will give you a better explanation. Your FF3 download will not have the plugins from FF2 but should have the add ons getting the plugins to work is exsplained on multiple threads on the forum and on the web.

---

### Post by bilijoe on 2008-07-12
**[COLOR=Black][B]aysiu, I just read your tip "**[/COLOR]Want to install Firefox from Mozilla?".  I think it has answered my questions and will allow me to do a proper install.  Thank You.
[/B]

---

### Post by bilijoe on 2008-07-31
Having finally been able to get FireFox running on all my systems (thanks to the link in aysiu's signature), I have just finished downgrading all my systems back to FireFox2. I encountered too many problems that, as an ex-developer, I recognize as "BetaBugs". I think the folks at Mozilla still consider v3 a Beta version. In any case, it still acts like a beta version, so for the time being, I'm going back to v2. Just FYI.

---

