---
title: "synaptic: broken package, but I need it"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by scotc on 2009-12-27
Dear all,
Karmic amd64.  I am installing the printer epson aculaser c1100.
I CAN do it with a force-architecture fix.

Only thing is, synaptic then tells me I have a broken package and requires it to be removed.  

Synaptic cites dependency issues for packages that are "uninstallable".  (libstdc5++  for example )

I have to remove the printer driver. Then the printer no longer works, of course.

It uses a dependency that I think is from Jaunty.  This may be the problem.

I'm not skilled enough to know what is going on here.

I have copied below the process (gathered from others, my notes in [square brackets]  )

Step 1.
Download package:
wget from ubuntu.mirrors.tds.net/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_i386.deb  
[this is the jaunty dependency]

Install it 
sudo dpkg -i --force-architecture libstdc++5_3.3.6-17ubuntu1_i386.deb

step 2. Prepare your alien
sudo apt-get install alien

step 3. get Epson-ALC1100-filter-1.2-0.i386.rpm and epson-alc1100-filter-cups_1.2-2_all.deb from [http://www.avasys.jp](http://www.avasys.jp)

Install both by converting from rpm
sudo alien -t Epson-ALC1100-filter-1.2-0.i386.rpm  [gives error -see * below - but appears to create a .tgz file]
sudo alien -t Epson-ALC1100-filter-cups-1.2-0.i386.rpm [as above]

sudo alien Epson-ALC1100-filter-1.2.tgz  [ generated ok]
sudo alien Epson-ALC1100-filter-cups-1.2.tgz  [as above]

sudo dpkg --force-architecture -i epson-alc1100-filter_1.2-2_all.deb
sudo dpkg --force-architecture -i epson-alc1100-filter-cups_1.2-2_all.deb
sudo /etc/init.d/cups restart
sudo aa-complain cupsd
[all the last 4 above worked ok]

Then I install the printer and it works fine.

Except for synaptic.

* The error while alien converts is
error: incorrect format: unknown tag
Warning: Skipping conversion of scripts in package Epson-ALC1100-filter: postrm
Warning: Use the --scripts parameter to include the scripts.

Can anyone help?
Scot

---

### Post by scotc on 2009-12-28
Anything anyone?

---

### Post by sandybrownlee on 2009-12-30
I'm having the same trouble, not been able to find anything to solve it yet but will post here if I do!

---

### Post by MelDJ on 2009-12-30
tried fixing the broken packages then reinstalling?

---

### Post by dstew on 2009-12-30
Try doing what the error message says, and invoke alien with the **--scripts** parameter to make it include the post-removal script that apt-get will need. Maybe then Synaptic (which is just a graphical front-end for apt-get) will work properly. Its worth a try anyway.

---

