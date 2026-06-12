---
title: "A few issues with fresh Hardy install"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by sparky_hall on 2008-04-30
Hi All,

I'm new to linux and I have been using Gutsy without any issues for about four weeks now so I'm still going up a very steep learning curve. Anyhow I've been trying Ubuntu Hardy but I've been having a few issues and I'm not really sure where they should be posted/reported so I thought I try here until told otherwise. I run my system as a multi boot system so Hardy was a fresh install on a clean partition.

Hardy install went OK but I use a CRT monitor and wanted to use a different resolution screen than default, this is when things started going wrong. Gutsy can detect my monitor but Hardy cannot, not a problem thought I as this can be manually set using the screens and graphics app once I'd found  were it had been moved to. I set the resolution how I like it and all seemed OK. Then I went about setting up an account for my wife with a different screen resolution but found the option she likes to use (1280x960_75Hz) was not there. I also noticed that the next time I booted the log on screen was different as if it was trying to be displayed over a much larger screen. To cut a long story short I managed to sort both of these issues out by manually editing /etc/x11/xorg.conf and the /home/myname/.gnome2/monitor.xml files for both accounts. To stop the log on screen from being oversized I had to reduce the virtual screen size to the native screen size in xorg.conf, you don't need to do this on Gutsy by the way.

The next issue is with Firefox 3. My wife does the weekly shop online at Tesco but when you log on to Tesco to do the shop some of the links confuse Firefox such that it opens the save dialogue rather than following the link, this seems to be somewhat erratic as sometimes it will follow the link correctly. This does not happen with Firefox 2 or IE6. I have no solution for this other than installing Firefox 2.

The issue I have now is with large pdf files. I have some motorbike workshop manuals in pdf format that are around 30meg so not huge. When I click on one of these at takes 80 seconds for it to open in Hardy but less than 2 seconds in Gutsy. Initially I thought there was a problem with evince but if I right click then go to properties it takes 80 seconds before the property dialogue shows. During this 80 second period my CPU is running flat out (athlon XP 3200 with 1G of RAM) and when I'm opening the file with evince its evince that shows cpu usage at 95%+ whereas opening the properties dialogue it's nautilus that show 95%+ cpu usage. Smaller pdfs open fine and I've not tested any other types of large files yet. Anybody have any ideas as what could be causing this?

While I'm here I would just like to thank all of the developers and testers for giving a me a viable alternative to MS.

Chris

---

### Post by sparky_hall on 2008-04-30
A little bit of an update with my large pdf load times. I have tried a new Hardy and Gutsy install on a second PC and the pdf load times are still very slow on hardy when compared to gutsy. I have also tried making a 16meg and 36meg bmp file just to check it's nothing to do with the file size, both of these load and display the property dialogue in around a second so it's not simply a file size issue.

Am I the only one experiencing issues with large pdf files?

Should I submit a bug report if so how do I go about this?

Any other ideas?

Thanks,

Chris

---

