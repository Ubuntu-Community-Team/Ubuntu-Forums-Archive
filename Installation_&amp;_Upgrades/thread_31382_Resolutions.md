---
title: "Resolutions"
date: 2005-05-03
forum: Installation &amp; Upgrades
---

### Post by dougmal on 2005-05-03
I just installed Ubuntu on my two computers.  I really like it, and i like the ideas behind it.  

I am a linux noob, and hopefully this will help me work into a linux enviroment more.  My problem is this: When i was installing, both times, i was unable to add or delete screen resolutions.  On this current computer i only have 3 options. 1024X768, 800X600, and  640X480.  I have a good monitor, and was running windows on it at resolutions up to 1600X1200.  I'm not sure if i just didn't know how to uncheck a resolution or what.  I could go up and down with arrows, but nothing i did would uncheck the box.  I finally tried pressing enter to change it, and it ended up going on with the installation.  I tried again the next time, and same thing.

I don't know where/how to change this.  I got into the gnome desktop preferences, and the screen resolution window, but only have the three choices.  I tried finding an answer on the gnome website, and by reading through the FAQ here.  I must admit, i only scanned the first two pages of this forum, i couldn't find a search button.  Hopefully i am posting this in the right place, if not sorry for the faux pas!

Any help would be greatly appreciated!  I don't want to get too far into this system, since i may have to reinstall to change the resolutions.  (I'm sure there's SOME way to do it without, but i don't know what it is yet.)

Doug

---

### Post by heimo on 2005-05-03
Hi!
 
You can edit xorg.conf to include other resolutions or you can reconfigure xorg using dpkg-reconfigure. All that you should need to know about these is already written on this thread:
[http://www.ubuntuforums.org/showthread.php?t=21984]("http://www.ubuntuforums.org/showthread.php?t=21984")
 
For some deeper tweaking or problem solving, see my post:
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21]("http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21")
 
 
Cheers!

---

### Post by dougmal on 2005-05-03
Thanks much! Once i actually have a managable screen size, hopefully things will be a bit easier to figure out! =)

---

### Post by dougmal on 2005-05-03
OK, i just tried to make those changes on my second comp (this one only has 640X480) as an option) and the xconf file already had larger resolutions in it.  Here is the part:

> Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor		"electron19b"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

any thoughts?


*EDIT* nevermind, apparently, just opening and closing the file, and restarting the computer was enough to fix it, it suddenly booted up in 1600X1200.

---

