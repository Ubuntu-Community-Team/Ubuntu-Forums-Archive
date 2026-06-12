---
title: "can't get rid of openoffice3.1"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by peterroots on 2010-03-18
I am running Kubuntu9.1 on several machines at work - (and also 8.04 but not noticed this problem with them).
I wanted openoffice 3.2
So....
I uninstalled everything I could find related to openoffice
Then I installed ooo3.2 from ooo web site (after removing the gnome package and moving the deb menu package into the same folder as the other debs to make life easy)
Then I was happy :-)
Then one day the menu item for ooo3.2 lost is icon, and did not work anymore.
when I typed soffice in terminal I got ooo3.1
So.....
I uninstalled everything I could find that was not ooo3.2
installed the deb menu bit of ooo3.2 again
Then I was happy :-) until it happened again :-(
This has so far happened in 3 machines, one of them twice so far

Updates I normally do with apt-get and obviously I have not seen masses of ooo files to update and just said yes to them. So why is this happening?
Anyone else had this problem?
How to I prevent it?

---

### Post by wojox on 2010-03-18
Did you try This thread: [http://ubuntuforums.org/showthread.php?p=8808996](http://ubuntuforums.org/showthread.php?p=8808996)

---

### Post by peterroots on 2010-03-18
no I didn't read that but it is not much help as it only tells me to do what I did and has no mention of my problem at all but thanks anyway

---

### Post by Hagar Delest on 2010-03-20
If the desktop integration package is in a separate folder, it may be for a reason. I were you I would install in 2 steps: first the core packages and once they're installed the desktop integration one.

---

### Post by peterroots on 2010-03-20
That is a thought, I have always assumed it is because OOo assume it is optional and you may not want to mess with your menus. It still puzzles me as to what is putting OOo3.1 back again after I uninstalled it.
After each subsequent uninstall of 3.1 I have only reinstalled the debian menu package to restore all the menu links.
After the last reappearance of 3.1 (yesterday) I tried to remove the whole lot 3.1 and 3.2 for a totally clean start - apt-get remove openoffice*.* failed to work as the debian menu package could not be found. Just uninstalling this package failed as it could not be found - I was assuming this was because of 3.1 removing it due to a conflict but not fully getting rid of the evidence.
Thus you may be right that there is something odd about this package that is part of or all of the problem.
Next time (if it does it again) I will try a total uninstall (piece by piece if I have to) then install the main bits then the menu changes and see what happens.
Thanks for the suggestion

---

### Post by peterroots on 2010-03-22
Ok so it is not the deb menus that are causing the problem. I just installed Kubuntu 9.10 64 bit on a new machine.
I removed openoffice
sudo apt-get remove openoffice*.*
I installed openoffice 3.2 from the ooo website (64 bit this time)
I then installed the debian menu integration package

Then I did some things like set the system language (had forgotten to do this earlier installed some other software like google chrome, google desktop, skype etc)

tried to run openoffice and it was back to 3.1 again!

How on earth do I get rid of 3.1?

---

### Post by jimmers on 2010-03-22
Try this
  	 	 	 	 	 	  This tutorial will explain how to install latest version of openoffice in ubuntu
 You can check what is new in openoffice 3.2 from [here]("http://www.openoffice.org/dev_docs/features/3.2/")
  First go to the [OpenOffice website]("http://download.openoffice.org/other.html") and download the Linux .deb file (On your [[COLOR=#006400]_desktop_[/COLOR]]("http://www.ubuntugeek.com/how-to-install-openoffice-3-2-in-ubuntu.html#"))
 1 - Once you have done that, extract the .deb file,
 [INDENT]OOo_3.2.0_LinuxIntel_install_en-GB_deb.tar.gz[/INDENT] Run the following command from terminal or just right click select extract
 [INDENT]tar xzvf OOo_3.2.0_LinuxIntel_install_en-GB_deb.tar.gz[/INDENT] Then you’ll see a file called OOO320_m12_native_packed-1_en-GB.9483
 2 - You can remove the existing version of OpenOffice if you wish with this command:
 [INDENT]sudo apt-get remove openoffice*.*[/INDENT] 3 - Copy and paste OOO320_m12_native_packed-1_en-GB.9483 onto the desktop then open Terminal and paste this command:
 [INDENT]sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-GB.9483/DEBS/*.deb[/INDENT] 4 - Then paste this command:
 [INDENT]sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-GB.9483/DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9472_all.deb[/INDENT] Once you’ve done that you’ll find OpenOffice 3.2 in Office.

---

### Post by Chame_Wizard on 2010-03-22
Best thing is to add the PPA:[https://launchpad.net/~openoffice-pkgs/+archive/ppa]("https://launchpad.net/~openoffice-pkgs/+archive/ppa")

---

### Post by peterroots on 2010-03-22
Jimmers - that is exactly what I did and I can't stop 3.1 coming back! THAT is my problem.

Chame_wizzard - I tried that with both 8.04 and 9.10 before I resorted to doing what Jimmers suggested. Initially, with 8.04 and 3.1 it worked but then stopped quite some time ago. 9.10 has never worked with 3.2 so I am left with using the download from OOo - all I need is a way to stop 3.1 coming back

---

### Post by Chame_Wizard on 2010-03-22
Click on the [read about installing]("https://launchpad.net/+help/soyuz/ppa-sources-list.html").:popcorn:

---

### Post by Hagar Delest on 2010-03-22
> **peterroots said:**
> I installed openoffice 3.2 from the ooo website (64 bit this time)
I then installed the debian menu integration package
What do you mean? Have you installed the menus with the desktop-integration package or another package?

---

### Post by jimmers on 2010-03-22
Peterroots,

Instead of apt-get remove, try apt-get purge

---

### Post by julianb on 2010-03-22
This is not an ideal solution, and it may not be of any use at all in your circumstances:

To the best of my knowledge, Ubuntu 10.04 beta 1 works great. One option available to you is to install 10.04 beta, which doesn't include openoffice 3.1 at all.

I am running Lubuntu 10.04 on my machine.

---

### Post by peterroots on 2010-03-23
Hagar - as you suggested I installed the core packages then the desktop integration for debian (that was included in the OOo download)

Jimmers - after the most recent reversion I tried apt-get remove openoffice*.* --purge so I will see what happens next!!

Julianb - I might try this on my laptop but not for the work computers, I depend on them remaining stable but thanks it is good to know it is working for you.

Chame_wizzard - I have had the ppa active for weeks and had nothing show up so about 2 weeks ago I removed it from my sources.list as various posts kept saying 'any day now' and nothing ever happened. Today I tried re enabling it and this time update picked up OOo3.2 so I am trying an install right now - if it works that will be great. Still leaves a mystery as to 'why?' though and does not help anyone who does not like the Ubuntuised version of OOo (there always seems to be something in it that upsets someone!

Still, what ever happens, in a month or so it won't be an issue as I can upgrade all my machines to the next LTS version anyway :-)

Thanks All for you help and suggestions
Peter

---

### Post by Chame_Wizard on 2010-03-23
You should enable  all options in the USC software sources(multiverse universe repositories etc,all kinds of updates,daily notifications,statics).:popcorn:

---

### Post by peterroots on 2010-03-23
The install from ppa went ok - I  prefer the look of the OOo version (I expect I can change that though) but as long as it works and as long as 3.1 stays gone then I am happy :-)
Thanks

---

