---
title: "hplip driver will not install"
date: 2016-11-17
forum: Installation &amp; Upgrades
---

### Post by harlie on 2016-11-17
using ubuntu 16.04 and need to install hplip-3.16.10run but it will not install I get the error message    cant open hplip-3.16.10run   same for   hplip-3.16.7run
this is in the terminal window. the printer is a HP Envy 5660.  Help!!!!













11

---

### Post by oldfred on 2016-11-17
If printer is not brand new, you can just install the version in Ubuntu repository. 
With 16.04, I see 3.16.3.
sudo apt-get install hplip-gui
gksudo hp-setup


If you have a very new printer you can download the newest .run (needs dot) from HP directly and run that.

With 14.04 version in repository was older, so I got this type of message.
You have selected Ubuntu 14.04 using the HP Envy 4500 E-all-in-one.
Ubuntu 14.04 supplies HPLIP 3.11.5 by default, which does not support your printer.
You must ensure latest HPLIP version (recommemded), or at least HPLIP 3.13.6 in order to use your printer with Ubuntu 14.04.

Creates lots of folders & files, best if in its own sub-directory if downloaded .run file

---

### Post by harlie on 2016-11-17
that is an old version that came with the 16.04 install it is out of date and will not drive my printer correctly. the reccomended version is 3.16.7  or newer version now recommended by hp open source is 3.16.10. that is what i need to install but it can't
open the file. I need to check again to be sure I did use the dot after 3.16.10 I could have missed it.

I checked again and I did miss the dot the install is going ahead now.

Thanks

---

