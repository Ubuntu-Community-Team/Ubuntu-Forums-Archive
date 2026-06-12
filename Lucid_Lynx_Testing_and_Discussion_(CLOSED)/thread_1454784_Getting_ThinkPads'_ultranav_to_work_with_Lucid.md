---
title: "Getting ThinkPads' ultranav to work with Lucid"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Miguel on 2010-04-15
Dear all,

I'm a happy owner of a Thinkpad T400, with its characteristic red trackpoint (or ultranav, as it's called in thnkpad-land). Under karmic, I could get the ultranav scrolling to work with some hal rules (see [ThinkWiki](http://www.thinkwiki.org/wiki/Install_Ubuntu_9.10_%28Karmic_Koala%29_on_a_ThinkPad_T400#Scrolling_with_Trackpoint).

Since only two libhal* packages are installed by default in Lucid, does anybody know hoy I can get srolling to work in Lucid? Is it possible to translate the HAL trackpoint rules to udev?

The closest thing I've found is perhaps [this ubuntuforums post](http://ubuntuforums.org/showthread.php?t=1197550), with a link to a Debian bug. Nevertheless, those udev rules seem to deal only with trackpoint speed.

Or will I have to aptitude install hal again?

EDIT:

OK, I've been silly. Somehow I missed that I had to adjust the path to the trackpoint device here:
[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Determining_TrackPoint_Path_ID](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Determining_TrackPoint_Path_ID)

This link, by the way, includes several ways on how to configure your trackpoint. I'm restarting udev and xorg before marking this as fixed.

---

### Post by Miguel on 2010-04-15
Dammit, spoke too soon. I might have to fiddle with the buttons, but for now I'm off to work.

---

