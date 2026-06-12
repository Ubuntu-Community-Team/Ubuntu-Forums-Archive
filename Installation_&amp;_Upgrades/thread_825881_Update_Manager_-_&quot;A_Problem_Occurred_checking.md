---
title: "Update Manager - &quot;A Problem Occurred checking for Updates&quot;"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by star38hero on 2008-06-11
Instead of having a red arrow, I have a little red circle with a line through it.  The pop up menu from it says "A problem occurred checking for updates."

Can anyone help me fix this?

---

### Post by avtolle on 2008-06-11
I'm guessing that when the update manager went to check, there was a network problem of some kind. 

Try this (from the terminal)```
sudo aptitude update && sudo aptitude safe-upgrade
``` and post any error messages you get.

---

### Post by johnnyg2008 on 2009-01-18
I'm having the same problem. When I code sudo aptitude update it comes back as: segmentation fault. When I code sudo aptitude safe upgrade it lists actions.:confused:Ideas? TIA

---

### Post by notoriousmic24 on 2009-02-23
BUMP same issue here. Also can't open Synaptic PM or Add/Remove...

---

### Post by puddlejumper on 2010-01-08
I am having exactly the same problem with Ubuntu 9.04.  I'm afraid that, if a fix becomes available, I will be unable to install it because of this problem.:(

---

### Post by frankO on 2010-01-27
This [http://ubuntuforums.org/archive/index.php/t-358900.html](http://ubuntuforums.org/archive/index.php/t-358900.html) helped some people with a segmentation problem.

---

### Post by costoich on 2010-03-24
These are the errors that I got:

sudo aptitude update && sudo aptitude safe-upgrade

A bunch of these:
aptitude: /usr/local/lib/libstdc++.so.6: no version information available (required by aptitude)

And some of these:
aptitude: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)

And:
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)

And finally:
aptitude: relocation error: aptitude: symbol _ZSt16__ostream_insertIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_PKS3_i, version GLIBCXX_3.4.9 not defined in file libstdc++.so.6 with link time reference


Thanks for any help on this.

---

### Post by 9.10 on 2010-04-23
PLZ HELP THIS IS URGENT 

1. i get the update error
2. i can't open the Ubuntu software center (instantly quits)
3. i can't open .deb package files (instantly quits)

---

### Post by cybercookie72 on 2011-02-04
Greetings...

I am running 10.04 and saw the upgrade button....ooooo the BUTTON...yeah well I pressed it.  

And the Red circle with a white line through the middle popped up (when moused over says "A problem occured when checking for the updates."

When I click on it seemed that the package manager tried to start but then quit right away.  I could not start the Update Manager either (it quit right away).

solution for me was:::

Opening a terminal 
and 
sudo rm /var/cache/apt/*.bin 

then 

sudo apt-get update && sudo apt-get upgrade

and all seemed to work again....

the solution came from halfvolle melk's post that had this url::

[http://askubuntu.com/questions/12950/update-manager-a-problem-occurred-when-checking-for-the-updates](http://askubuntu.com/questions/12950/update-manager-a-problem-occurred-when-checking-for-the-updates)




thanks all for your posts...good luck

---

### Post by adatol on 2011-09-02
Cybercookie72, that did the trick for me! Thanks!

---

