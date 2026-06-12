---
title: "Re: Fox News is not working"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by silvagroup on 2010-01-06
This [link]("http://newyork.ubuntuforums.org/showthread.php?p=7164731") is old but recently I have problems watching Fox News also.
It all worked fine then one day nada.

Now when in Fox News I get a a notice in the upper left hand corner of the video window that says "Get Adobe Flash Player".

So I figured somethings wrong with flash plugin. So I clicked on the Get Adobe player and I got some download error. Checked to make sure I had  flash installed via synaptic, and it was installed, reinstalled and it did no good. Went to Adobe site found the .deb for the new flash, removed old and installed new version, and still no Fox video.

If I do about:plugins in Firefox it shows that Shockwave Flash 10.0r42 is installed as well as FutureSplash Player. But I still get "Get Adobe Flash Player" and no video.

Any suggestions please so I don't have to log into Windows just to watch Fox News. 

Thanks in advance.

---

### Post by Sef on 2010-01-07
Moved post to its own thread.

---

### Post by silvagroup on 2010-01-11
Thanks Sef.
But from what I can see everything is installed as per the links recommended.
I am using 9.10 latest updates but this actually began about a month ago in 9.04.
The reason I upgraded was thinking it may clear up problem but it didn't.
Firefox works fine in XP from a vm just not a go in Ubuntu.
So for now I watch Fox News in XP in a VM.

---

### Post by efflandt on 2010-01-11
You must have some other flash lurking on your system, because I have never seen "FutureSplash Player" as a plugin (can you disable it).

Are you running 32-bit or 64-bit OS?  I had no trouble using flashplugin-installer installed automatically with ubuntu-restricted-extras.  But on 64-bit systems after installing restricted-extras I completely remove flashplugin-installer (which is 32-bit with wrapper) and use real 64-bit flash.  Although, on my old Athlon64 3200+ I also have to use flashplugin-lahf-fix.so because my cpu is missing the lahf_lm instruction apparently used by 64-bit flash.

One problem with FoxNews is that there are so many flash ads that some of them can momentarily bog down your system (especially one on FoxNews Business that makes a big ball of sunshine popup that is incredibly slow).

---

### Post by silvagroup on 2010-01-12
efflandt thanks for the suggestions.
I got it working on my desktop by doing an install of Adobe AIR. But trying the same thing on my laptop still does not work.
Both my desktop and laptop show the FutureSlpash, not sure where it came from or how to remove or disable it since it doesn't show up in addons just in about:plugins, but that doesn't seem to be the cause.
I am in the process of completely removing and reinstalling fireofox and all adobe from my laptop to see if that clears the problem.
Will post back.

---

### Post by silvagroup on 2010-01-12
Well after spending half of the day with trying to get this to work on my laptop I am no better off than when I started.
I've tried every thing I can imagine even wiping all signs of firefox and adobe off the laptop and reinstalling everything, to no avail.
Desktop is working fine however.
May try a clean install on the laptop given the time later on.

---

### Post by silvagroup on 2010-02-02
This problem is specific to my laptop and fox news.
I can go to the adobe flash test web site and no problems but when I go to fox news firefox doesn't see that flash is still installed.
I have now upgraded my desktop and my wifes to 9.10 and both work just fine in this matter, but not my laptop.
All three system were (I have reinstalled firefox several times and have not yet added other add ons on laptop) identical when I checked about:plugins when problem started.

Is there some way to have firefox not check to see if flash is installed? 

Trying to find a way to solve this very confusing problem. It certainly appears to be something with my laptop and firefox config, but what.

Trying not ot have to do a complete os reinstall just to get this minor problem fixed.

Any ideas would be greatly appreciated.

---

### Post by efflandt on 2010-02-02
I am not really an expert with grep, but you might try the following (make your terminal wide first) and see what shows up in the list for working flash vs. non-working flash:

**locate plugin | grep flash | grep \.so**

---

### Post by silvagroup on 2010-02-22
Sorry for not respoonding for so. Things have been busy.
Output of grep is:
/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so

Which by the way is the exactly same thing on my desk top which works fine.
I know it's some crazy configuration thing some where on my laptop.
Keep threatening to do fresh install but other than this my laptop is running fabulous. Really don't feel like getting it all set up and optimized again for just this hiccup.

---

### Post by spottedhog on 2010-03-17
I am having a similar problem.  Upon opening Firefox, the videos on Fox News work perfectly.  It will sometimes work all day, even after viewing YouTube videos for 2 or 3 hours at night. 

The problem seems to come from when I leave the Fox News website open, even on the Home page, all night while leaving the laptop connected.  The following morning there will be an audio skipping problem, much like a bad CD that gets stuck on one location and bounces the specific sound repeatedly before moving to another sound, repeating this same scenario.

The video portion seems only slightly to not being affected.

When this problem occurs, I try the exact same page in a different browser, and all works perfectly.  If I shut down Firefox and re-open Firefox, all is OK again.

I have tried many things, even doing a fresh install (9.10).  I have spent countless hours reading 100's of web pages, but nothing is helping.  I am wondering if the multiple flash files on the Fox News video pages are conflicting...

---

### Post by CTBuckweed on 2010-03-17
Yes, I have the same problem with my installation of Karmic Koala 9.10. I go to foxnews.com and I get the "install flash player" when trying to view videos. I go to load it. The load/install is reported as being successful  but it still doesn't work - just the prompt to install flash player again. I get the same symptom with my Windows XP Pro partition with Firefox 3.5 & 3.6 and also (dare I say it) IE v7.0. And this happens on all of my XP systems in my home.

---

### Post by auh2o on 2010-03-17
Ubuntu 9.10, Firefox 3.6 & Adobe Flash 10.0 r45. I've never had any problems watching videos on foxnews.com.

That's not much help to you guys, I know. But just to inform you that it can indeed work, and that the problems you're having must be specific on your machines.

---

### Post by silvagroup on 2010-04-30
OK problem solved.
Just stupid on my part.
I was still trying to figure it out and finally realized that I had a host block file which I put in years ago. I went to update it and it hit me that maybe this was my problem.
Renamed it for a test and voila, problem gone.
Leaving it like that because I added Ad Block Plus to Firefox which works much better and w/Fox News.

---

### Post by hansdown on 2010-04-30
Haha!

Nice work silvagroup.:)

Glad you got things sorted.

---

