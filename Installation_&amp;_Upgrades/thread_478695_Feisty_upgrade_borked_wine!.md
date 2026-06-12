---
title: "Feisty upgrade borked wine!"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by Skeorx13 on 2007-06-19
When I was running edgy I had wine running properly with CDex and mIRC. However after upgrading to feisty, the interface for both programs will not pop up. CDex would error saying it needs ASPI drivers for NT systems (My default wine is set to XP) and then asks if you should use the native drivers. I clicked yes and it worked fine (back in edgy). Now after upgrading, it has the error but no option for anything. The graphical interface will not run and the system monitor says the program is running but sleeping. (I tried to load the aspi dll's but none of them worked in any directory they were installed in, always got the same ASPI error) mIRC had NO problems before upgrading. Now it loads the tiny screen that notes how many trial days are left and when you hit continue it disappears and nothing else comes up. Again, program running but sleeping, no interface. I upgraded to version 0.9.39 and tried it again. Still same results. Does anyone know how to fix this problem? I hate having to restart to log into windows...

---

### Post by Skeorx13 on 2007-06-19
Ok I installed a later version of CDex (the 170beta version) and it seems to work now. When I close the preferences menu, though, it closes the program if I don't have a disc in the cd drive. I can live with that though... mIRC however, is slightly more complicated. I reinstalled mIRC into a different directory so I wouldn't overwrite any info, and the program loads but without any of my settings. So I started copying files in the mirc directory over from my older installation to the newer one and reloaded the program after each overwrite. It worked each time except until I got to mirc.ini so there's gotta be an issue with that file and either feisty or wine.

Edit:
Fixed the mirc loading problem. This line of text in the mirc.ini file caused some kind of problem so I reverted this one line of text to the original file's text in the fresh install and left all the rest of the file alone (the previous install) and I retained all of my info and the program loads with no issues now.

[quote="mirc.ini"]
[windows]
main=**-2**,1284,73,877,0,1,0[/quote]
The bolded part was a 0 in my original mirc.ini. I think this might have caused some kind of alignment issue out of the bounds of the layout or something...

---

### Post by Skeorx13 on 2007-06-19
grr...
Well at least cdex is running decent. mIRC keeps locking up and closing by itself. So far it has closed itself several times from a script and from switching servers (which it doesn't like to connect to).

---

