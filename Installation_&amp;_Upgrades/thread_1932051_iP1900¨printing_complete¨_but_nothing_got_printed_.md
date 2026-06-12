---
title: "iP1900¨printing complete¨ but nothing got printed at all"
date: 2012-02-26
forum: Installation &amp; Upgrades
---

### Post by mummak on 2012-02-26
Hello all. Good evening!

My cannon Ip1900 was intalled correctly and printing ok,followed the steps below:

[http://ubuntuforums.org/archive/index.php/t-1305248.html](http://ubuntuforums.org/archive/index.php/t-1305248.html)

...and suddenly I got the error message

cups insecure filter

(*obs: this error ocurred after I tried to configure draft quality print...printed out 1 sheet and then BUG!)

which was half corrected in the same post mentioned above. The commands to correct such error were:

sudo chown -hR root /usr/lib/cups/filter
sudo chown -hR root /usr/lib/cups/backend
sudo chgrp -hR root /usr/lib/cups/filter
sudo chgrp -hR root /usr/lib/cups/backend

They removed the error message, and my pc thinks it is printing out a document: I can see the ¨printing document¨ message in the printing monitor windows, and the ¨printing completed¨ message as well but nothing comes out of the printer at all..it stays idle all this time..does not even make any sound.

I tried removing and readding the printer and its drivers. It did not work. I think I did not really remove everythin I neede which were: the printer, cnij common and ip1900 packages.

ANy ideas, please?

Thank you and have a nice week.

/*----------------------------------------------------*/
/*----------------------------------------------------*/
/*----------------------------------------------------*/

SOLUTION BELOW \/

---

### Post by mummak on 2012-02-28
Ok. Got it. Did lots of things,I dont know which one might have solved.

I spent at least ...30 hours trying to solve the problem before posting for help. I guess this forums gives magic to solving stuff.
Here it goes:

1. First of all: Unplug the print and
Got the Gtk warning when using sudo gedit. Solved with

mkdir -p /root/.local/share

gedit is used in step (4)

2. Check which packages were being installed with the .deb files. There were 2 debs meant to be installed. I checked which package they installed with:

dpkg --info cnijfilter-common_3.00-1_i386.deb
dpkg --info cnijfilter-ip1900series_3.00-1_i386.deb

which were:

cnijfilter-common
cnijfitler-ip1900series

3. COMPLETELY REMOVED THE PACKAGES AND CONFIGURATION FILES WITH
( I guess that was the key move)

dpkg --purge for both packages

4. Followed the procedures here:

[http://ubuntuforums.org/showthread.php?t=1305248](http://ubuntuforums.org/showthread.php?t=1305248)

5. Plugged in the print

Back to happy printing days of youthness.

Best wishes to all of ya.

---

