---
title: "Work-arround for some Ubuntu 12.04 printer problems"
date: 2012-07-11
forum: Installation &amp; Upgrades
---

### Post by richpri on 2012-07-11
Ubuntu 12.04 [Percise Pangolin] switched the pdftops CUPS filter from Poppler to Ghostscript. It also allowed higher image rendering resolutions when the pdftops filter has to turn graphical structures of the PDF input file into bitmaps.

These changes seem to be causing a number of problems with various printers.  Some of these have been totally or partially resolved. Others have not.

Till Kamppeter created a work-around for these problems which involves reverting from Ghostscript to Poppler.  This is discussed in various Launchpad bug reports such as 
[https://bugs.launchpad.net/ubuntu/+source/cups-filters/+bug/998087](https://bugs.launchpad.net/ubuntu/+source/cups-filters/+bug/998087)

With this work-around you can switch between use of Poppler and Ghostscript and change the resolution limit. 

You can run the following commands in a terminal window for switching between Ghostscript and Poppler:

lpadmin -p <printer> -o pdftops-renderer-default=gs
lpadmin -p <printer> -o pdftops-renderer-default=pdftops

and you can also use

lpadmin -p printer -R pdftops-renderer-default

to remove the setting.

To change the resolution limit to [for example] 1440 run the following command:

lpadmin -p <printer> -o pdftops-max-image-resolution-default=1440

and to set unlimited resolution run the following command:

lpadmin -p <printer> -o pdftops-max-image-resolution-default=0

To remove your resolution setting run:

lpadmin -p <printer> -R pdftops-max-image-resolution-default

NOTE: Always replace "<printer>" by your printer's queue name. 
You can use the command "lpstat -v" to find your printer's queue name.

I was able to fix a problem with my Brother HL-5250DN using these commands.

For general information about Poppler and Ghostscript see:

[http://en.wikipedia.org/wiki/Poppler_(software](http://en.wikipedia.org/wiki/Poppler_(software))
[http://en.wikipedia.org/wiki/Ghostscript](http://en.wikipedia.org/wiki/Ghostscript)

---

### Post by richpri on 2012-07-17
Is there any easy way to find out what the current pdftops-renderer-default setting is?

---

