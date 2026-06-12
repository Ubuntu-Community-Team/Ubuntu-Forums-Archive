---
title: "Upgrade 8.10 -&gt; 9.10 | Gstreamer-plugins-good error"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by emoc on 2010-08-09
Hello all, 

I was running a dist-upgrade on my laptop to to go 9.10.  While the upgrade was running I lost some network connection, however it claimed the update was done and needed a restart.   Upon restarting I had issues with fstab and mounting.  I fixed that, however now I think I find myself in the middle of updating and can not get ubuntu to boot properly.  So I am attempting to go through recovery mode and finish the upgrade.

Here is the following problem I am experiencing. 

When I perform any apt-get  I get a notice about missing depends.  So I apt-get -f install.  Everytime it runs it errors on the gstreamer0.10-plugins-good_0.10.16-1ubuntu3_i386.deb
package.  I've went into the /archives and remove the package and reran.  it downloads it and outputs the same error.  I've wget from another site and ran dpkg -i on the deb, however I experienced depend error.  I would like some advice on different methods to fix.  I am getting the 9.10 iso and try that.

Ultimately, do you feel I should just copy out my home/user folder and do a fresh install.  My goal is to get to 10.04 however I was going version to version to eliminate this type of problem from happening.

Thank you for your assistance.

P.S.  A normal boot is no longer an option. My ubuntu boot gfx is white and not lined up properly, and fgrlx says no screens are active.

---

### Post by mörgæs on 2010-08-10
Yes, a clean install is the way to go. It is not worthwhile to try to rescue a system which crashed during upgrade.

---

### Post by emoc on 2010-08-10
Yeah.  in case anyone has a similar problem.  I ended up doing:
dpkg --force-all -i gstream0.10-blah blah
sudo apt-get -f install


eventually it got passed it.  But I ended up having some other problems.  All in all I did salvage it and had it running after about 5 other other issues.  

All in All, I ended up just copying off my home folder and formatting with 10.04  since I was going to go there anyway..  Runs perfect now.

and side note:  I am running it on a HP 6910p w/ ATI X2300 card.  Which has no more support, so do not install the ati drivers if you want to get compiz and other things running properly.  Including the ATI Catalyst Control center, it worked in 8.10 but no mas.

---

