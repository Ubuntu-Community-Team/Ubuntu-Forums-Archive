---
title: "how to: (once again) a beginner to ubuntu maverick (&#960;&#940;&#956;&#949; &#963;&#945;&#957; &#940;&#955;&#955;&#959;&#964;&#949;)"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by Claus7 on 2010-10-13
Hello,

here I will post the experience I got since I came across with 10.10 ubuntu maverick, while already having gained some experience on how to modify my machine to my needs. So this is more for personal use rather than something else, yet someone might find some useful things for someone's system.

**32bit to 64bit**
My system was already a 32 bit one, really hard configured so I wanted to keep most of my configurations intact while making full use of my memory which was >3GB. It is well known that 32 bit OS are not able to harness memory more than the aforementioned one. Since 64 bit has become common among 64 pc owners I decided to take the big step.

In order to keep your system as intact as possible, the /home partition should be separate from / (root). That way some of your configurations will remain intact such as bookmarks, the entire home partition, wine, ms office installation and some other things. Build essential, vim, skype,gnome-open-terminal, fortran compilers (either from repos or manually installed), vmd, matlab and pulse along other libraries and programs should be reinstalled.

**graphics** 
the graphics configurations I had in 32 bit transfered manually from the 32 bit system to 64 without any glitch. So if you take a lot of time harnessing this stubborn xorg conf file, this will pay off.

**flashplayer**
there is a 64 bit version that works pretty nicely, so the installation both in opera and firefox is the same as before, yet a different version is proposed at the time of writing codenamed "square"

Open Firefox and go to Help-> About Mozilla Firefox and check the version you have (here *3.6.10*).

Then go to /usr/lib/firefox-*3.6.10* (note the version in italics) and type ls -l
There you will see among others the line:
lrwxrwxrwx 1 root root       25 2010-10-13 18:54 plugins -> ../firefox-addons/plugins

so you have to go to /usr/lib/firefox-addons/plugins and place there the libflashplayer.so file

For opera, after you have done the above, you have to go to Tools->Preferences->Advanced->Downloads(4th on the left)->Plugins->Change path->Add path->and put the above one->click ok and you are ok! 

**sounds**
both version share the same configurations, so here it applies the same as the graphics thing.

**dns issue**
if your internet does not work pretty well, as mine, I had to tamper with the dns provider as this in every single version of ubuntu caused me troubles. The thing is that with some tweaking this ceased to be a problem as well.

**keyboard preferences**
yes I know, something pretty common, yet always hard to find

On the top panel click on keyboard preferences and then choose Layouts -> Options -> key(s) to change layouts choose the combination you prefer.

More or less, these things for now,
Regards and happy ubuntuing!

---

