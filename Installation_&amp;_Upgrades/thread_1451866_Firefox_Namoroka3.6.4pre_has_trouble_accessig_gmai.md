---
title: "Firefox Namoroka/3.6.4pre has trouble accessig gmail and yahoo mail"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by rabbitoid on 2010-04-11
I have upgraded yesterday trough the regular update-manager my version of firefox ("nakamura") to 3.6.4~hg20100410r34032+nobinonly-0ubuntu1~umd1~karmic (karmic).

Since then I cannot access gmail or yahoo mail (I get a grey zombie screen which I can only kill)
other sites (of course, I haven't checked all 25412456917582145 of them) seem to be working fine. 
Any suggestions?

---

### Post by kellemes on 2010-04-11
> **rabbitoid said:**
> I have upgraded yesterday trough the regular update-manager my version of firefox ("nakamura") to 3.6.4~hg20100410r34032+nobinonly-0ubuntu1~umd1~karmic (karmic).

Since then I cannot access gmail or yahoo mail (I get a grey zombie screen which I can only kill)
other sites (of course, I haven't checked all 25412456917582145 of them) seem to be working fine. 
Any suggestions?

Clean FF cache? Maybe that helps..

---

### Post by nikkichowchow on 2010-04-11
Yes cleared cache and cookies.

Found a new site that has the same problem: [www.pagesjaunes.fr](www.pagesjaunes.fr) (French phone directory)
If it persists I'll try to go back to firefox 3.5 (after all, 3.6 is not yet standard for ubuntu 9.10)

---

### Post by wblogan on 2010-04-11
> **rabbitoid said:**
> I have upgraded yesterday trough the regular update-manager my version of firefox ("nakamura") to 3.6.4~hg20100410r34032+nobinonly-0ubuntu1~umd1~karmic (karmic).

Since then I cannot access gmail or yahoo mail (I get a grey zombie screen which I can only kill)
other sites (of course, I haven't checked all 25412456917582145 of them) seem to be working fine. 
Any suggestions?

I'm having the same problem. After clearing all private data and even rebooting  I completely uninstalled and reinstalled the 3.6.4 - same problem. If I can figure out how I'm going back to 3.5.

---

### Post by FirstByté on 2010-04-11
> **wblogan said:**
> I'm having the same problem. After clearing all private data and even rebooting  I completely uninstalled and reinstalled the 3.6.4 - same problem. If I can figure out how I'm going back to 3.5.

Well, I was trying to update to ff 3.6.x following the issues I'm having opening my mails: -**GMail** and - **Yahoo Mail** when I stumbled at this post.

I at present I still use FF.3.5.8 and exactly about 2weeks ago, I suddenly can't access gmail nor READ the contents of my Yahoo Mails, though for yahoo I could see the mail headers; as for GMail, it often presents me with the white screen :)

I discovered I couldn't even post on Facebook [suspecting something to do with dynamic sites]. I contacted my ISP after much router resting and routing table clearing. To my surprise GMail and Yahoo!Mail works smoothly on my Windoz Vista. Sorry I seldom use Windoz but I guess the ff in there is 3.6 or so.

I'm guess it has a problem to do with some update/upgrades on the 'network kernels' in the 2.6.31.***20***

To check I installed Galeon, Chrome Web Browsers none of them solved this issue, so IMO it's more of an OS issue and not just FF.



THIS IS PAIN FOR ME, cause all my work is in Ubuntu! :confused: Can't believe I need to switch to windoz now... just to check mail. Even my ISP's customer satisfaction mail, I can't access.. funny!:guitar:

---

### Post by thudon on 2010-04-11
I had the same problem, played around with disabling all the plugins and brought them back one by one.  It seems that 'shockwave flash 10.0 r45' was the issue for me.  Of course now I have to find a way around that, but isn't that part of the fun of linux?

---

### Post by wblogan on 2010-04-11
> **thudon said:**
> I had the same problem, played around with disabling all the plugins and brought them back one by one.  It seems that 'shockwave flash 10.0 r45' was the issue for me.  Of course now I have to find a way around that, but isn't that part of the fun of linux?

I've found something wierd: I completely removed firefox from the system using the synaptic package manager but the icon I had on my taskbar was still there. I clicked on it and firefox namoroka 3.6.4pre loaded! What's the deal with this?

I read your post and was doing the same thing (diabling plugins) and found that 'shockwave flash 10.0 r45' was causing my problem as well.

But I don't know why firefox is running... everything else seems to be working well.

Can anyone explain this to me?

---

### Post by thudon on 2010-04-11
Here's a little more information on the shockwave-player (and how to actually remove it, which proved more difficult than expected).  [http://ubuntuforums.org/archive/index.php/t-1128720.html](http://ubuntuforums.org/archive/index.php/t-1128720.html)

This is definitely the source of the problem and I've tried installing flash from adobe in several different ways all with the same results.  I suppose gnash or swfdec could work, but one is in beta and the other doesn't look like it's been updated in over a year.  Any ideas?

in the mean time I'm going to take advantage of this and get some work done instead of getting distracted by flash games and movies...  open to any ideas on this though so that I can get back to procrastinating!

---

### Post by kellemes on 2010-04-11
Strange, I'm running 3.6.4pre without this issue.

Maybe you should delete the profile, a new one will be created at first run.. or simply create a new profile to begin with.
Just to see what happens.
```
firefox -profilemanager
```

---

### Post by LumbeeNDN on 2010-04-11
...this started last nigh for me. Major headache. I do all of my web development on my laptop. Needless to say until this is fixed I can't get any work done. I'll post back when I come up with something.

---

### Post by abra1 on 2010-04-11
I had a similar problem with Firefox Namoroka/3.6.4pre - couldn't access emails and sites kept freezing and it was getting worse. No problem whatsoever in Opera.

So I updated to Ubuntu 10.04 b2 - clean install -  and I see that it came with Firefox 3.6.3 which works fine- at least so far. 

I had no trouble with the clean install though some people report that they get frustrated initially. 

Once you have it running it looks really great!

---

### Post by LumbeeNDN on 2010-04-11
...thats 3 hours of my life I'll never get back! Blew every firefox folder away in /usr/lib, then downloaded (via FTP) the 3.6.3 tar ball and dropped that in /usr/lib, and it seems to be running OK. Don't ask me why that took 3 hours. :confused:

---

### Post by jervin2 on 2010-04-11
I too am having the problem with Firefox 3.6.4pre under Ubuntu 9.10.  I've tried the standard fixes, cleared everything out.  I tried uninstalling and reinstalling.  Deleted and Created new Profile.  I turned off all add-ons to no avail. I did notice that when I started firefox via cmd line with firefox and then go to igoogle.com, I get the following shortly after arriving...

(firefox-bin:13448): GLib-WARNING **: g_set_prgname() called multiple times

** (firefox-bin:13479): WARNING **: Serious fd usage error 14

** (firefox-bin:13479): WARNING **: Serious fd usage error 12

and it turns grey.  So, it's a problem with certain websites.  It happens on gmail.com, igoogle.com, but many other sites work fine, like maps.google.com, mycpbc.org, msn.com.  No problems with google chrome.  It reaches a point during the loading of the page, the usage error messages pop up and it freezes.  If you hit the "home" button or the "stop" button to kill the load, then it doesn't freeze (assuming your home page isn't one that freezes too).  

After the freeze, I can hit the "X" in the upper right corner to get out. I get a The Window "iGoogle - Namoroka" is not responding.  Forcing the application will cause you to lose any unsaved changes.  [Cancel] [Force Quit] and can force it out or I can go to the System Monitor and Kill it.  It's very reproducible.  Are there any log's I can get that might help?

---

### Post by jervin2 on 2010-04-11
Oh yes, I also tried bringing it up in save mode, went to igoogle.com and it still hung on me.  Tried -jsconsole and it hung at the same time that the firefox hung.

---

### Post by mody on 2010-04-12
Hi,

I'm using Jaunty with deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main PPA for the latest Firefox. I had the same problem today after I've upgraded the Firefox to version firefox_3.6.4~hg20100410r34032+nobinonly-0ubuntu1~umd1~jaunty.

Tried -save-mode, tried new profile neither helped. Fortunately I have older versions in my apt cache that still work: firefox_3.6.4~hg20100406r33809+nobinonly-0ubuntu1~umd1~jaunty

I can post the last working version somewhere if needed.

mody

---

### Post by adrian2mil8 on 2010-04-12
> **jervin2 said:**
> I too am having the problem with Firefox 3.6.4pre under Ubuntu 9.10.  I've tried the standard fixes, cleared everything out.  I tried uninstalling and reinstalling.  Deleted and Created new Profile.  I turned off all add-ons to no avail. I did notice that when I started firefox via cmd line with firefox and then go to igoogle.com, I get the following shortly after arriving...

(firefox-bin:13448): GLib-WARNING **: g_set_prgname() called multiple times

** (firefox-bin:13479): WARNING **: Serious fd usage error 14

** (firefox-bin:13479): WARNING **: Serious fd usage error 12

and it turns grey.  So, it's a problem with certain websites.  It happens on gmail.com, igoogle.com, but many other sites work fine, like maps.google.com, mycpbc.org, msn.com.  No problems with google chrome.  It reaches a point during the loading of the page, the usage error messages pop up and it freezes.  If you hit the "home" button or the "stop" button to kill the load, then it doesn't freeze (assuming your home page isn't one that freezes too).  

After the freeze, I can hit the "X" in the upper right corner to get out. I get a The Window "iGoogle - Namoroka" is not responding.  Forcing the application will cause you to lose any unsaved changes.  [Cancel] [Force Quit] and can force it out or I can go to the System Monitor and Kill it.  It's very reproducible.  Are there any log's I can get that might help?

i've the same error after last namoroka update firefox_3.6.4~hg20100410r34032+ in karmic , pages with flash videos hang the browser at all , only you see a grey box and close it with the close button , before this update run very fine , i think what is a namoroka bug with flash , i try all 
normal fixes but nothing work . Maybe fix it in the next update.
Meanwhile i uninstalled this version and download the binaries of 
firefox_3.6.4~hg20100406r33809 for karmic i386 and install with dpkg and now work fine again .

---

### Post by elendilnl on 2010-04-12
> **wblogan said:**
> I'm having the same problem. After clearing all private data and even rebooting  I completely uninstalled and reinstalled the 3.6.4 - same problem. If I can figure out how I'm going back to 3.5.
I am running Lucid 10.04 beta 2 and I had the same problems. In the end I uninstalled Firefox, disabled the daily update ppa and installed FF 3.6.3

---

### Post by itzame on 2010-04-12
Set dom.ipc.plugins.enabled.libflashplayer.so to false...WFM.

---

### Post by rabbitoid on 2010-04-12
> **itzame said:**
> Set dom.ipc.plugins.enabled.libflashplayer.so to false...WFM.

Thanks! This solves the problem for me. I can live without the flashes.

---

### Post by LumbeeNDN on 2010-04-12
> **itzame said:**
> Set dom.ipc.plugins.enabled.libflashplayer.so to false...WFM.

...where is this configured?

---

### Post by FirstByté on 2010-04-12
That God I still dual-boot... I couldn't have read this forum again since I locked myself out from the Namoroka upgrade :D

Let's see how disabling the FlashPlayer 10 eases this off for now...


Thanks y'all for sharing :P

---

### Post by thudon on 2010-04-12
Ok, so disabling the flash plugin works, but we obviously lose flash support.  This may be a stupid question, but is there any way to simply roll back to a previous version of firefox that doesn't have this problem?  The update came up automatically for me and I just did it, but can't figure out a straight forward way to undo it.  

open to suggestions on this one folks.  and yes, I almost certainly fall into the 'newbie' category.

---

### Post by jervin2 on 2010-04-12
Thanks for the Tip, it worked. Odd thing, I went over to the adobe flash site and it still seemed to think I had flash.  But I did confirm that I can now get to gmail and igoogle.com.

---

### Post by adrian2mil8 on 2010-04-12
> **LumbeeNDN said:**
> ...where is this configured?

open a new tab and type in the address bar about:config

---

### Post by adrian2mil8 on 2010-04-12
> **thudon said:**
> Ok, so disabling the flash plugin works, but we obviously lose flash support.  This may be a stupid question, but is there any way to simply roll back to a previous version of firefox that doesn't have this problem?  The update came up automatically for me and I just did it, but can't figure out a straight forward way to undo it.  

open to suggestions on this one folks.  and yes, I almost certainly fall into the 'newbie' category.



uninstall your version and download the binaries of 
firefox_3.6.4~hg20100406r33809 for you distribution and install it with dpkg

---

### Post by thudon on 2010-04-12
Adrian, thanks for the tip.  I actually found an easier solution - which I'm excited to post after using the forums so much to solve my own ubuntu problems.  Assuming you have the pre installed and want to go back just go into synaptic and completely remove firefox.  Then go to settings --> repositories and uncheck "http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu" under 'other software'.  click reload and select firefox for install again.  you may have to go under package --> force version and select the 3.6.3 version.  

Sorry if this is too simplistic, I'm no ubuntu expert (or even a novice really), but I hope this is helpful to those with as rudimentary a knowledge of ubuntu as I have.  plus, I'd like to be helpful instead of just leaching off forums!

---

### Post by xrecar on 2010-04-14
> **thudon said:**
> Adrian, thanks for the tip.  I actually found an easier solution - which I'm excited to post after using the forums so much to solve my own ubuntu problems.  Assuming you have the pre installed and want to go back just go into synaptic and completely remove firefox.  Then go to settings --> repositories and uncheck "http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu" under 'other software'.  click reload and select firefox for install again.  you may have to go under package --> force version and select the 3.6.3 version.  

Sorry if this is too simplistic, I'm no ubuntu expert (or even a novice really), but I hope this is helpful to those with as rudimentary a knowledge of ubuntu as I have.  plus, I'd like to be helpful instead of just leaching off forums!

Simple and effective. Thank you!

---

### Post by heldal on 2010-04-15
It is possible to use the new version of flashplayer that is distributed with the development version of Google Chrome. The browser-plugin APIs are being modified/improved and this may be the reason why namoroka doesn't work with the older flash API. You may try this:

1. Uninstall flashplugin

2. Add Google's APT repo: [www.google.com/linuxrepositories/apt.html](www.google.com/linuxrepositories/apt.html) and refresh

3. Install google-chrome-unstable. This is the only one that comes with the new flash-plugin

4. Make the flash plugin available to other apps with:
sudo ln -s /opt/google/chrome/libgcflashplayer.so /usr/lib/mozilla/plugins/


The developement version of chromium has the same problem with the old-flashplayer and will also work better with this version.

---

### Post by gsparky2004 on 2010-04-15
Thudon, you get the "You're My Everything!" award for today!  Your solution worked perfectly for me!  Not only did you solve my Firefox problem, you also solved my Thunderbird problem.  You ROCK!  

I'll add one bit of extra info.  You suggest going into "settings -> repositories".  For those of you who do not know where to find this, go to "System -> Administration -> Update Manager".  When the "Update Manager" window opens, click on "Settings".  You'll probably be asked for your password (if you haven't already).  Then click on the "Other Software" tab.  If you had the same problem as I and thudon did, you will have a selection that has "ubuntu-mozilla-daily/ppa" in it.  If so, uncheck the box next to that.  Now, click "Close", then click "Close" on the "Update Manager" window.  Finish by following the rest of thudon's directions.  Go into "Synaptic" (System -> Administration -> Synaptic Package Manager) and remove Firefox, or Thunderbird, or whatever.  Once you've done so, when you next check for Firefox, or Thunderbird, or whatever, it will be the older, stable version, not the bleeding-edge version which probably caused your problem.

---

### Post by mody on 2010-04-16
Perfect! Thank you, this works!

Mody

---

### Post by adrian2mil8 on 2010-04-16
> **heldal said:**
> It is possible to use the new version of flashplayer that is distributed with the development version of Google Chrome. The browser-plugin APIs are being modified/improved and this may be the reason why namoroka doesn't work with the older flash API. You may try this:

1. Uninstall flashplugin

2. Add Google's APT repo: [www.google.com/linuxrepositories/apt.html](www.google.com/linuxrepositories/apt.html) and refresh

3. Install google-chrome-unstable. This is the only one that comes with the new flash-plugin

4. Make the flash plugin available to other apps with:
sudo ln -s /opt/google/chrome/libgcflashplayer.so /usr/lib/mozilla/plugins/


The developement version of chromium has the same problem with the old-flashplayer and will also work better with this version.

the last flash version 10.1-rc and stable 10.0.45 have the same problem with firefox_3.6.4~hg20100406r34032 and new 34076 build. 
I have try it today and flash hang all browser tabs at least to me .I've uninstalled again and reinstall 33809 was the last  build working without problem with flash.

Greetings

---

