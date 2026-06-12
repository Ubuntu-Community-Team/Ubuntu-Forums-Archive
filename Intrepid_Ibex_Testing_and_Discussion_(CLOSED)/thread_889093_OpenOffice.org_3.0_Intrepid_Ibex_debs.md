---
title: "OpenOffice.org 3.0 Intrepid Ibex debs"
date: 2008-08-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by calc on 2008-08-13
I wanted to mention that if anyone is interested in testing out the OpenOffice.org 3.0 test debs they are located at [https://launchpad.net/~openoffice-pkgs/+archive]("https://launchpad.net/~openoffice-pkgs/+archive").

If you decide to file a bug please file them using the Help->Report a bug, so that the full apport details are included.

The 3.0 release candidate is currently scheduled for release on Aug 25, if it is released on time I should have it around that date.

Thanks,

Chris (calc)

---

### Post by caryb on 2008-08-13
Dumb question? Where is it installed to:confused:


Cary

---

### Post by olskar on 2008-08-13
It looks like /usr/bin

If you open the debs in the package installer and click on included files you can see where they will be installed :)

---

### Post by calc on 2008-08-13
> **caryb said:**
> Dumb question? Where is it installed to:confused:


Cary

In /usr/bin it replaces the 2.4.1 packaging in Intrepid. The only reason they aren't in Intrepid directly is because I haven't determined if 3.0 will be released in time to make it into Intrepid. If they keep to the Aug 25 RC1 release schedule then 3.0 should be released by Oct 6 at the latest (hopefully) which means we should be able to get it in.

[Intrepid Ibex OpenOffice.org 3.0 Upload Schedule]("http://wiki.ubuntu.com/OOo30Schedule")

---

### Post by caryb on 2008-08-13
Thats strange as when I fire up OOO it still says 2.4 & I thought that it would remove the old version.


Cary

---

### Post by ShirishAg75 on 2008-08-13
Hi all, 
 I had installed Openoffice 3.0 beta using this guide [http://tombuntu.com/index.php/2008/05/08/test-drive-openoffice-3-beta-in-ubuntu/](http://tombuntu.com/index.php/2008/05/08/test-drive-openoffice-3-beta-in-ubuntu/)

now how do I uninstall it so I can use the launchpad archive?

---

### Post by calc on 2008-08-13
> **caryb said:**
> Thats strange as when I fire up OOO it still says 2.4 & I thought that it would remove the old version.


Cary

Ah I forgot to replace the splash screen, that is just a cosmetic bug. If you go to the about box it should show the correct version. The graphic there will probably show 2.4 as well, but below that it should show the right version number.

---

### Post by caryb on 2008-08-13
Ok so I'm not going insane:lolflag:


Cary

---

### Post by calc on 2008-08-13
> **ShirishAg75 said:**
> Hi all, 
 I had installed Openoffice 3.0 beta using this guide [http://tombuntu.com/index.php/2008/05/08/test-drive-openoffice-3-beta-in-ubuntu/](http://tombuntu.com/index.php/2008/05/08/test-drive-openoffice-3-beta-in-ubuntu/)

now how do I uninstall it so I can use the launchpad archive?

First make sure the

dpkg -l | grep (EXACT package version number) | cut -f 3 -d " "

command returns only OpenOffice.org related packages or it might remove some packages you want to keep.

Then run the following command and it should purge all the packages.

dpkg -l | grep (EXACT package version number) | cut -f 3 -d " " | xargs dpkg --purge

If extra packages were returned in the first step then manually purge each OpenOffice.org package by doing:

dpkg --purge (package name)

---

### Post by afv on 2008-08-13
Hi,

I can't open more than one file/OOo application simultaneously :-|

I was using the same build (debs from [http://download.openoffice.org/3.0beta/](http://download.openoffice.org/3.0beta/)) and this didn't happen.

Anyone with the same problem?

---

### Post by klange on 2008-08-13
I'll have to remove my original debs from beta 2, but I'll be sure to get myself up and running on the Ubuntu packages ASAP.

---

### Post by ShirishAg75 on 2008-08-14
> **calc said:**
> First make sure the

dpkg -l | grep (EXACT package version number) | cut -f 3 -d " "

command returns only OpenOffice.org related packages or it might remove some packages you want to keep.

Then run the following command and it should purge all the packages.

dpkg -l | grep (EXACT package version number) | cut -f 3 -d " " | xargs dpkg --purge

If extra packages were returned in the first step then manually purge each OpenOffice.org package by doing:

dpkg --purge (package name)

How do I get the exact package version number?

I know it would involve do a some grepping but what or how it should be no idea.

---

### Post by calc on 2008-08-14
> **ShirishAg75 said:**
> How do I get the exact package version number?

I know it would involve do a some grepping but what or how it should be no idea.

This command will likely return a bunch of packages, which hopefully have the same version number for most of them anyway:

dpkg -l | grep openoffice.org

---

### Post by mitchellcipriano on 2008-08-14
I added the debs to my software sources, but Update Manager tells me I can only do a partial install and the OpenOffice selections are grayed out.

Any ideas?

---

### Post by caryb on 2008-08-14
Same happened for me just install what will install & the rest will install straight after! for some reason some of the packages wont install because of dependency problems but once they are installed the rest happily install:)


Cary

---

### Post by mitchellcipriano on 2008-08-14
> **caryb said:**
> Same happened for me just install what will install & the rest will install straight after! for some reason some of the packages wont install because of dependency problems but once they are installed the rest happily install:)


Cary

That is what I expected, but so far it has not installed. I will try again later.

---

### Post by ShirishAg75 on 2008-08-14
Hi all, 
 I installed the source in the sources list, the packages are being upgraded and stuff. I would be looking for a clear path though from the PPA to Intrepid sources as and when Openoffice.org 3.0 makes it to Main or Universe wherever it fits in.

Calc, I&#7743; looking forward to your response on this, even if its the RC1 which would be put up.

---

### Post by mitchellcipriano on 2008-08-15
> **caryb said:**
> Same happened for me just install what will install & the rest will install straight after! for some reason some of the packages wont install because of dependency problems but once they are installed the rest happily install:)


Cary

I tried another machine and I have the same problem. I tried to do a partial install, but it says the packages can not be authenticated.

Any suggestions?

---

### Post by darco on 2008-08-15
Getting same as error as mitchellcipriano

darco

---

### Post by nanog on 2008-08-15
Calc,

Powerpoints that reproducibly crash 2.4 (bug filed in ubuntu and upstream) mostly work now. The bug that prevents remote access of documents via gvfs on ftp, sftp, and webdav is still present, however.

Any chance you could press the magic build button for 8.04? I know there are many users who would really appreciate it. As an incentive I am very willing to donate $100 (US) to you directly or to a FOSS project of your choosing.

Cheers,

nanog

---

### Post by afv on 2008-08-15
> **afv said:**
> Hi,

I can't open more than one file/OOo application simultaneously :-|

I was using the same build (debs from [http://download.openoffice.org/3.0beta/](http://download.openoffice.org/3.0beta/)) and this didn't happen.

Anyone with the same problem?

Is it just me? :?

---

### Post by caryb on 2008-08-15
I scanned a bank statement into writer then it would not let me save any document, I had to kill the session via the terminal. I can reproduce this bug.


Cary

---

### Post by jfernyhough on 2008-08-25
Bit of a bump:

Will there be an updated 'release' with m29 (or whichever milestone svn is at now)? I note the version is the original beta, m3, which is a bit rough; m29 is far better.

Having said that, I've only had this build of m3 Writer crash on me once so far.

---

### Post by Darwin Award Winner on 2008-08-25
If the packages are Intrepid-only, please remove hardy from the "Display sources.list entries" list.

---

### Post by Vadi on 2008-08-25
Yeah. What a tease

---

### Post by FrancoNero on 2008-08-27
> **calc said:**
> 
The 3.0 release candidate is currently scheduled for release on Aug 25...

... so when will the release candidate be out?

---

### Post by edujose on 2008-08-27
Out of curiosity, are the toolbars in OO 3.0 less taller than in 2.4?

Still not testing OO.o 3.0, but having more compact toolbars (and/or smaller toolbar icons) would save some screen space for us having to deal with 1024x768 screens/laptops.

This is a thing I miss from word 200x, space-saving toolbars in the UI.

---

### Post by andrewabc on 2008-08-27
> **FrancoNero said:**
> ... so when will the release candidate be out?

They keep moving it back. Currently set at September 1.
Not even sure on official release date anymore (it has a question mark).

[http://wiki.services.openoffice.org/wiki/OOoRelease30](http://wiki.services.openoffice.org/wiki/OOoRelease30)

---

### Post by ssam on 2008-08-30
not sure where you want bugs filed. i tried the help->report bug, but it seems to do nothing (if i run oowriter from the CLI i get the message "sh: /usr/lib/openoffice/program/ooo87965.execute.sh: not found").

anyway.

open openoffice writer.
drag an image file into the page (i used a png)
now click the image to get the green resizing handles.
as you move the mouse over the handles the cursor should change to a double headed arrow, but it stays as a hand.

**this is fixed in the RC version**

===

create 2 odt files.
double click on one in nautilus, it opens
now double click the other, nothing happens.

**Fixed in the RC version**
===

for people having trouble with updatemanager. it is upset because some packages need to be removed to install the new ones. open synaptic, find the openoffice.org package, set it to upgrade and press apply.

the unauthenticated messages are because these are not official packages. they are not signed with a key that your apt trusts.

---

### Post by mitchellcipriano on 2008-08-30
> **ssam said:**
> not sure where you want bugs filed. i tried the help->report bug, but it seems to do nothing (if i run oowriter from the CLI i get the message "sh: /usr/lib/openoffice/program/ooo87965.execute.sh: not found").

anyway.

open openoffice writer.
drag an image file into the page (i used a png)
now click the image to get the green resizing handles.
as you move the mouse over the handles the cursor should change to a double headed arrow, but it stays as a hand.

===

create 2 odt files.
double click on one in nautilus, it opens
now double click the other, nothing happens.

===

for people having trouble with updatemanager. it is upset because some packages need to be removed to install the new ones. open synaptic, find the openoffice.org package, set it to upgrade and press apply.

the unauthenticated messages are because these are not official packages. they are not signed with a key that your apt trusts.

This is what I needed to get it installed. It works great now. Many thanks!

---

### Post by vishalrao on 2008-08-31
if anyone is counting votes: +1 from me for inclusion in alpha5 and eventually for final release by default! please take an "intrepid" decision, like the kernel team moving to .27, and pick OOo 3 for Intrepid :)

---

### Post by ssam on 2008-08-31
a crasher

start OO presentation, the presentaion wizard come up.
click next on the first page
on page 2 of the wizard there is a box of options for the background. in mine i have
```
<Original>
Dark Blue with Orange
Subtle Accents
```
click on "Subtle Accents"
click on "<Original>". crash

happens everytime. on amd64

**Fixed in the RC version**

---

### Post by xerosis on 2008-08-31
I don't seem to have any icons here, perhaps a dependency is missing?

---

### Post by FrancoNero on 2008-09-01
> **vishalrao said:**
> if anyone is counting votes: +1 from me for inclusion in alpha5 and eventually for final release by default! please take an "intrepid" decision, like the kernel team moving to .27, and pick OOo 3 for Intrepid :)

+1 here as well.

---

### Post by FrancoNero on 2008-09-01
no sign of the RC anywhere..... ;-(

---

### Post by razmakati on 2008-09-01
If anybody knows how to enable Dictionaries could you please post a how-to
I've tried the suggestions on OpenOffice wiki but to no avail. 

Thank you in advance

---

### Post by nanog on 2008-09-01
Ooohhhhhhhhhh nooooooooooooo:

  Timeline for 3.0

    * A fixed release date cannot be determined in the moment. Martin hopes that it'll be in September but maybe that's not realistic

[http://wiki.services.openoffice.org/wiki/ReleaseStatus_Minutes#Agenda_for_next_meeting](http://wiki.services.openoffice.org/wiki/ReleaseStatus_Minutes#Agenda_for_next_meeting)

---

### Post by FrancoNero on 2008-09-02
> **nanog said:**
> Ooohhhhhhhhhh nooooooooooooo:

  Timeline for 3.0

    * A fixed release date cannot be determined in the moment. Martin hopes that it'll be in September but maybe that's not realistic

[http://wiki.services.openoffice.org/wiki/ReleaseStatus_Minutes#Agenda_for_next_meeting](http://wiki.services.openoffice.org/wiki/ReleaseStatus_Minutes#Agenda_for_next_meeting)

oh come on. it's a release candidate. it doesn't have to be finished. they can have an RC2 and RC3 etc... I just want to have it ;-)

---

### Post by calc on 2008-09-06
> **FrancoNero said:**
> oh come on. it's a release candidate. it doesn't have to be finished. they can have an RC2 and RC3 etc... I just want to have it ;-)

It appears that 3.0 RC1 might be released by upstream next Monday. But 3.0 final likely won't be released until sometime around Oct 20 if they take as long to stabilize as 2.4, which would put it being too late to be the standard version of OOo in Intrepid.

---

### Post by vishalrao on 2008-09-06
i wish rc1 would appear by default in alpha 6 for more people to test, so that intrepid might include the rc (if stable enough) by default upon release and then update to final like it was done for firefox in hardy - i know that was because hardy was lts blah blah - but ibex should live up to its name and be, you know, intrepid :D

---

### Post by victorche on 2008-09-06
> **calc said:**
> It appears that 3.0 RC1 might be released by upstream next Monday. But 3.0 final likely won't be released until sometime around Oct 20 if they take as long to stabilize as 2.4, which would put it being too late to be the standard version of OOo in Intrepid.

RC1 WAS released ;)
[ftp://sunsite.informatik.rwth-aachen.de/pub/mirror/OpenOffice/contrib/rc/3.0.0rc1/OOo_3.0.0rc1_20080904_LinuxIntel_install_en-US.tar.gz](ftp://sunsite.informatik.rwth-aachen.de/pub/mirror/OpenOffice/contrib/rc/3.0.0rc1/OOo_3.0.0rc1_20080904_LinuxIntel_install_en-US.tar.gz)

---

### Post by amano on 2008-09-06
Is there a release announcement?

---

### Post by calc on 2008-09-06
> **vishalrao said:**
> i wish rc1 would appear by default in alpha 6 for more people to test, so that intrepid might include the rc (if stable enough) by default upon release and then update to final like it was done for firefox in hardy - i know that was because hardy was lts blah blah - but ibex should live up to its name and be, you know, intrepid :D

An upstream RC is almost certainly not going to be very stable, they are still finding lots of major bugs each week. It seems they just decided to push out an RC because they were so far behind schedule. Also, when 2.4 was released and included in hardy (it was released in time) it was still so buggy that I had to petition to have 2.4.1 included into hardy-updates which required a lot of extra work and code review between several people to have included. So the likelyhood of an upstream RC release being good enough to actually ship as the final version for Intrepid is infinitesimally small, and no one wants to have the repeat the process of uploading a new release (3.0.1) into updates for Intrepid, with all the work and code review that involves.

So we will probably have an openoffice.org package (2.4.1) and openoffice.org3 package (3.0.0) or something similar to that.

---

### Post by calc on 2008-09-06
> **victorche said:**
> RC1 WAS released ;)
[ftp://sunsite.informatik.rwth-aachen.de/pub/mirror/OpenOffice/contrib/rc/3.0.0rc1/OOo_3.0.0rc1_20080904_LinuxIntel_install_en-US.tar.gz](ftp://sunsite.informatik.rwth-aachen.de/pub/mirror/OpenOffice/contrib/rc/3.0.0rc1/OOo_3.0.0rc1_20080904_LinuxIntel_install_en-US.tar.gz)

Its sort of released, it will be announced on Monday. :)

---

### Post by vishalrao on 2008-09-07
> **calc said:**
> It seems they just decided to push out an RC because they were so far behind schedule.

gotta hate it when projects do that :)

> **calc said:**
> So we will probably have an openoffice.org package (2.4.1) and openoffice.org3 package (3.0.0) or something similar to that.

that would be a good thing if it were to happen.

thanks for the post calc.

---

### Post by nanog on 2008-09-07
*So we will probably have an openoffice.org package (2.4.1) and openoffice.org3 package (3.0.0) or something similar to that.*

Terrific. 

3.0 fixes multiple bugs that have made OOo unuseable in a professional/technical environement (e.g. error bars and charting improvements). Is backporting it to Hardy possible?

---

### Post by Jingo on 2008-09-08
OpenOffice 3.0 RC 1 released

[http://download.openoffice.org/680/](http://download.openoffice.org/680/)

---

### Post by stoffe on 2008-09-09
> **Jingo said:**
> OpenOffice 3.0 RC 1 released

[http://download.openoffice.org/680/](http://download.openoffice.org/680/)

Anybody got that to work? I used to run beta 2 and that worked, even if it had a few bugs. With this RC it just crashes instantly no matter what I do, even when opening a new project. The only thing I see is this:
```
$ /opt/openoffice.org3/program/soffice
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'

```
Reports have been sent via automated tool.

Has anybody else got it to work, and if so, what could I do? :)

---

### Post by ntetreau on 2008-09-09
I can' t get it to work either...

---

### Post by syko21 on 2008-09-09
Try removing all the .openoffice / .ooo-dev configuration folders from your home directory.

---

### Post by mvbozkurt on 2008-09-09
Just rename /home/<your username>/.openoffice.org/3/user/uno-packages folder name to sth else "uno-packages-bak" then it should work

---

### Post by stoffe on 2008-09-10
Thanks guys, got it started now! (I removed the directories completely, as I didn't have much configured). Much appreciated!

---

### Post by lautert on 2008-09-10
I have OpenOffice 2.4 installed (Default)
And now i´v instaled 3.0, but it crashs..

After Looking the last post
i´v tried:

#pwd
/home/lautert
#ls -a
(...)
.openoffice.org
.openoffice.org2
(...)
#rm -Rf .openoffice.org
#rm -Rf .openoffice.org2

just set inital config again and its done!!! working!!

---

### Post by ShirishAg75 on 2008-09-12
Hi all, 
 I am using the PPA made by Calc. While Openoffice 3.0 beta 2 is firmly planted and works I'm looking forward to RC 1 . When updating I get something like this :-

```

shirish@Mugglewille:~$ dpkg -l openoffice.org
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                   Version                Description
+++-======================-======================-============================================================
ii  openoffice.org         1:3.0.0~beta2-1ubuntu2 OpenOffice.org Office suite

```

This is what it shows me when trying to run the upgrade scenario :-

```

shirish@Mugglewille:~$ sudo aptitude full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages are BROKEN:
  libipe1c2a openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-draw 
  openoffice.org-filter-binfilter openoffice.org-impress openoffice.org-math openoffice.org-officebean 
  openoffice.org-writer openoffice.org-writer2latex python-uno 
The following NEW packages will be installed:
  language-support-translations-mr{a} openoffice.org-l10n-mr-in{a} 
The following packages will be REMOVED:
  openoffice.org-core{a} 
The following packages will be upgraded:
  language-support-mr libfreetype6 libfreetype6-dev 
3 packages upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
Need to get 1461kB of archives. After unpacking 99.0MB will be freed.
The following packages have unmet dependencies:
  openoffice.org-writer: Depends: openoffice.org-core (= 1:3.0.0~beta2-1ubuntu2) but it is not installable
  openoffice.org-impress: Depends: openoffice.org-core (= 1:3.0.0~beta2-1ubuntu2) but it is not installable
  openoffice.org-draw: Depends: openoffice.org-core (= 1:3.0.0~beta2-1ubuntu2) but it is not installable
  openoffice.org-filter-binfilter: Depends: openoffice.org-core (= 1:3.0.0~beta2-1ubuntu2) but it is not installable
  openoffice.org-writer2latex: Depends: openoffice.org-core (>= 1:2.3.0~oog680m1) but it is not installable
  openoffice.org-math: Depends: openoffice.org-core (= 1:3.0.0~beta2-1ubuntu2) but it is not installable
  python-uno: Depends: openoffice.org-core (= 1:3.0.0~beta2-1ubuntu2) but it is not installable
  libipe1c2a: Conflicts: libfreetype6 (>= 2.3.6) but 2.3.7-2ubuntu1 is to be installed.
  openoffice.org: Depends: openoffice.org-core (= 1:3.0.0~beta2-1ubuntu2) but it is not installable
  openoffice.org-officebean: Depends: openoffice.org-core (= 1:3.0.0~beta2-1ubuntu2) but it is not installable
  openoffice.org-base: Depends: openoffice.org-core (= 1:3.0.0~beta2-1ubuntu2) but it is not installable
  openoffice.org-calc: Depends: openoffice.org-core (= 1:3.0.0~beta2-1ubuntu2) but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
language-support-mr

Keep the following packages at their current version:
language-support-translations-mr [Not Installed]
libfreetype6 [2.3.5-1ubuntu4 (now)]
libfreetype6-dev [2.3.5-1ubuntu4 (now)]
openoffice.org-core [1:3.0.0~beta2-1ubuntu2 (<NULL>, now)]
openoffice.org-l10n-mr-in [Not Installed]

Score is 728

Accept this solution? [Y/n/q/?] 


```

As one can see the unpopular scenario is to remove openoffice.org-core (and rightly so) so when is it going to get updated?

Can wait for a while ;)

---

### Post by calc on 2008-09-17
> **ShirishAg75 said:**
> Hi all, 
 I am using the PPA made by Calc. While Openoffice 3.0 beta 2 is firmly planted and works I'm looking forward to RC 1 . When updating I get something like this

Have you removed all openoffice.org language packs? I'm pretty certain it won't install with them and 3.0.0~beta2 only has language packs for English. I'll be uploading a set of rc1 debs soon, it would have been earlier but I had to evacuate for Hurricane Ike. My home is ok but still doesn't have power so I am staying with a coworker.

---

### Post by Ub1476 on 2008-09-20
No 64-bit debs (for Hardy)? :(

---

### Post by lonniehenry on 2008-09-21
There is a release candidate for 64 bit oo3.  
[ftp://ftp.ussg.iu.edu/pub/openoffice...b/rc/3.0.0rc2/](ftp://ftp.ussg.iu.edu/pub/openoffice...b/rc/3.0.0rc2/)
and the instructions :
1. Head to the download page and select the Linux (deb) or Linux 64 bit (deb) download. Decompress the archive to your desktop.
2. Installing OpenOffice requires installing a large number of DEB packages. It&#8217;s easiest to install them using the terminal. Open a terminal, switch to the directory where you decompressed the download to, and install all the packages at once:
cd ~/Desktop/OOO300_m7_native_packed-1_en-US.9354
sudo dpkg -i DEBS/*.deb
3. That will not have added you any Application menu items. You can create one yourself using the menu editor (System->Preferences->Main Menu). Menu icon graphics are available in /usr/share/icons/hicolor/48×48/apps. Launch OpenOffice with this command:
/opt/openoffice.org3/program/soffice
4. You can delete the download from your desktop after the installation.

Want to remove OpenOffice 3? I&#8217;ve compiled this huge command (it&#8217;s all one line) to remove all of the OpenOffice 3 packages:
sudo apt-get remove ooobasis3.0-base ooobasis3.0-binfilter ooobasis3.0-calc ooobasis3.0-core01 ooobasis3.0-core02 ooobasis3.0-core03 ooobasis3.0-core04 ooobasis3.0-core05 ooobasis3.0-core06 ooobasis3.0-core07 ooobasis3.0-draw ooobasis3.0-en-us ooobasis3.0-en-us-base ooobasis3.0-en-us-binfilter ooobasis3.0-en-us-calc ooobasis3.0-en-us-draw ooobasis3.0-en-us-help ooobasis3.0-en-us-impress ooobasis3.0-en-us-math ooobasis3.0-en-us-res ooobasis3.0-en-us-writer ooobasis3.0-gnome-integration ooobasis3.0-graphicfilter ooobasis3.0-images ooobasis3.0-impress ooobasis3.0-javafilter ooobasis3.0-kde-integration ooobasis3.0-math ooobasis3.0-onlineupdate ooobasis3.0-ooofonts ooobasis3.0-ooolinguistic ooobasis3.0-pyuno ooobasis3.0-testtool ooobasis3.0-writer ooobasis3.0-xsltfilter openoffice.org3 openoffice.org3-base openoffice.org3-calc openoffice.org3-dict-en openoffice.org3-dict-es openoffice.org3-dict-fr openoffice.org3-draw openoffice.org3-en-us openoffice.org3-impress openoffice.org3-math openoffice.org3-writer openoffice.org-ure

you may have to change the commands to match the version that you downloaded.

---

### Post by zoomy942 on 2008-09-21
so once i install this version 3, can i uninstall 2.4 and not hurt anything?

---

### Post by lonniehenry on 2008-09-22
You can have both versions and that won't hurt anything.  You can set up the file association to point to whichever version you want.

---

### Post by Ub1476 on 2008-09-22
Thank you! Downloading now. Hope I get it working with Gnome-Do..

Ugh, seems to be quite unstable on 64-bit. I heard it's built on some kind of compability layer from 32-bit so I guess that's why.. Problem is soffice can't open a document when launching the program at the same time. Has to open Writer, then open a document from there. A bit complicated, but still better than using soffice 2.4.

---

### Post by EmptyCinema on 2008-09-22
> **calc said:**
> Have you removed all openoffice.org language packs? I'm pretty certain it won't install with them and 3.0.0~beta2 only has language packs for English. I'll be uploading a set of rc1 debs soon, it would have been earlier but I had to evacuate for Hurricane Ike. My home is ok but still doesn't have power so I am staying with a coworker.


Hey calc,

Hope things are going well for you with the recovery from Ike!  I was wondering if you had any idea when debs for rc1 or rc2 would be available.  I know things must be hectic for you, but I have a particular need for OO3 coming up and was wondering if I should attempt to build myself or if yours were coming soon.  :)

---

### Post by andrewabc on 2008-09-22
Release Candidate 2 has been released.
[http://download.openoffice.org/680/](http://download.openoffice.org/680/)

---

### Post by lonniehenry on 2008-09-22
instructions changed as the links changed to rc2 


[ftp://ftp.ussg.iu.edu/pub/openoffice...b/rc/3.0.0rc2/](ftp://ftp.ussg.iu.edu/pub/openoffice...b/rc/3.0.0rc2/)
and the instructions :
1. Head to the download page and select the Linux (deb) or Linux 64 bit (deb) download. Decompress the archive to your desktop.
2. Installing OpenOffice requires installing a large number of DEB packages. It&#8217;s easiest to install them using the terminal. Open a terminal, switch to the directory where you decompressed the download to, and install all the packages at once:
cd ~/Desktop/OOO300_m7_native_packed-1_en-US.9354
sudo dpkg -i DEBS/*.deb
3. That will not have added you any Application menu items. You can create one yourself using the menu editor (System->Preferences->Main Menu). Menu icon graphics are available in /usr/share/icons/hicolor/48×48/apps. Launch OpenOffice with this command:
/opt/openoffice.org3/program/soffice
4. You can delete the download from your desktop after the installation.

Want to remove OpenOffice 3? I&#8217;ve compiled this huge command (it&#8217;s all one line) to remove all of the OpenOffice 3 packages:
sudo apt-get remove ooobasis3.0-base ooobasis3.0-binfilter ooobasis3.0-calc ooobasis3.0-core01 ooobasis3.0-core02 ooobasis3.0-core03 ooobasis3.0-core04 ooobasis3.0-core05 ooobasis3.0-core06 ooobasis3.0-core07 ooobasis3.0-draw ooobasis3.0-en-us ooobasis3.0-en-us-base ooobasis3.0-en-us-binfilter ooobasis3.0-en-us-calc ooobasis3.0-en-us-draw ooobasis3.0-en-us-help ooobasis3.0-en-us-impress ooobasis3.0-en-us-math ooobasis3.0-en-us-res ooobasis3.0-en-us-writer ooobasis3.0-gnome-integration ooobasis3.0-graphicfilter ooobasis3.0-images ooobasis3.0-impress ooobasis3.0-javafilter ooobasis3.0-kde-integration ooobasis3.0-math ooobasis3.0-onlineupdate ooobasis3.0-ooofonts ooobasis3.0-ooolinguistic ooobasis3.0-pyuno ooobasis3.0-testtool ooobasis3.0-writer ooobasis3.0-xsltfilter openoffice.org3 openoffice.org3-base openoffice.org3-calc openoffice.org3-dict-en openoffice.org3-dict-es openoffice.org3-dict-fr openoffice.org3-draw openoffice.org3-en-us openoffice.org3-impress openoffice.org3-math openoffice.org3-writer openoffice.org-ure

you may have to change the commands to match the version that you downloaded.

---

### Post by ShirishAg75 on 2008-09-26
> **calc said:**
> Have you removed all openoffice.org language packs? I'm pretty certain it won't install with them and 3.0.0~beta2 only has language packs for English. I'll be uploading a set of rc1 debs soon, it would have been earlier but I had to evacuate for Hurricane Ike. My home is ok but still doesn't have power so I am staying with a coworker.

Hi calc, looking forward to the updated RC1 or RC2 ones whenever you can. Purged the language pack and then libfreetype6 got upgraded. 

I do pray and hope that Hurricane Ike leaves your home in peace or if has to do some damage, then let it do the minimal damage it can.

---

### Post by caryb on 2008-09-26
I'm trying to get a "working" 64 bit deb link, can someone post a correct one please?



Thanks Cary

---

### Post by lonniehenry on 2008-09-26
I keep having trouble putting up the link

Try this one:    [http://openofficeorg.secsup.org/contrib/rc/3.0.0rc2/](http://openofficeorg.secsup.org/contrib/rc/3.0.0rc2/)


it came from [http://download.openoffice.org/3.0beta/](http://download.openoffice.org/3.0beta/) and clicking extended mirrors and picking from the local list.

---

### Post by UbuWu on 2008-09-27
RC2 is now available from this PPA:

[https://launchpad.net/~openoffice-pkgs/+archive/](https://launchpad.net/~openoffice-pkgs/+archive/)

(a little patience is needed, the packages are apparently still building)

---

### Post by jfernyhough on 2008-09-27
> **UbuWu said:**
> (a little patience is needed, the packages are apparently still building)I was going to say, the amd64 builds have been there for a few hours (12?) - I'm waiting on the i386 to complete... :)

---

### Post by caryb on 2008-09-27
Nope 64bit ones are not complete, see thumbnail.

Cary

---

### Post by ShirishAg75 on 2008-09-27
from where one can know where the packages are being built? This is what I am getting atm :-

```

shirish@Mugglewille:~$ sudo aptitude full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages are BROKEN:
  openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-draw openoffice.org-filter-binfilter 
  openoffice.org-impress openoffice.org-math openoffice.org-officebean openoffice.org-writer 
  openoffice.org-writer2latex python-uno 
The following NEW packages will be installed:
  language-support-translations-en{a} libdb-je-java{a} libdb4.5-java{a} libdb4.5-java-gcj{a} libjtidy-java{a} 
  liblucene2-java{a} openoffice.org-help-en-gb{a} openoffice.org-l10n-common{a} openoffice.org-l10n-en-gb{a} 
  openoffice.org-l10n-en-za{a} thunderbird-locale-en-gb{a} 
The following packages will be REMOVED:
  openoffice.org-core{a} 
The following packages will be upgraded:
  openoffice.org-help-en-us 
1 packages upgraded, 11 newly installed, 1 to remove and 0 not upgraded.
Need to get 19.8MB/20.1MB of archives. After unpacking 35.2MB will be freed.
The following packages have unmet dependencies:
  openoffice.org-writer: Depends: openoffice.org-core (= 1:3.0.0~beta2-1ubuntu2) but it is not installable
  openoffice.org-impress: Depends: openoffice.org-core (= 1:3.0.0~beta2-1ubuntu2) but it is not installable
  openoffice.org-draw: Depends: openoffice.org-core (= 1:3.0.0~beta2-1ubuntu2) but it is not installable
  openoffice.org-filter-binfilter: Depends: openoffice.org-core (= 1:3.0.0~beta2-1ubuntu2) but it is not installable
  openoffice.org-writer2latex: Depends: openoffice.org-core (>= 1:2.3.0~oog680m1) but it is not installable
  openoffice.org-math: Depends: openoffice.org-core (= 1:3.0.0~beta2-1ubuntu2) but it is not installable
  python-uno: Depends: openoffice.org-core (= 1:3.0.0~beta2-1ubuntu2) but it is not installable
  openoffice.org: Depends: openoffice.org-core (= 1:3.0.0~beta2-1ubuntu2) but it is not installable
  openoffice.org-officebean: Depends: openoffice.org-core (= 1:3.0.0~beta2-1ubuntu2) but it is not installable
  openoffice.org-base: Depends: openoffice.org-core (= 1:3.0.0~beta2-1ubuntu2) but it is not installable
  openoffice.org-calc: Depends: openoffice.org-core (= 1:3.0.0~beta2-1ubuntu2) but it is not installable
The following actions will resolve these dependencies:

Keep the following packages at their current version:
language-support-translations-en [Not Installed]
openoffice.org-core [1:3.0.0~beta2-1ubuntu2 (now)]
openoffice.org-help-en-gb [Not Installed]
openoffice.org-help-en-us [1:3.0.0~beta2-1ubuntu3 (now)]
openoffice.org-l10n-en-gb [Not Installed]
openoffice.org-l10n-en-za [Not Installed]

Score is 727

Accept this solution? [Y/n/q/?] 

```

---

### Post by UbuWu on 2008-09-27
> **ShirishAg75 said:**
> from where one can know where the packages are being built?

Openoffice is pretty big (almost a gigabyte of source packages) and takes a long time to get build. You can see on the PPA page if it is still building or finished. According to the site, building amd64 took 3 hours, so in 6 more hours probably everything is ready.

---

### Post by ShirishAg75 on 2008-09-27
UbuWu, thank you for the information but where do I see that information, in the right-hand corner, the left-hand corner, where?

Update:- I can see it building at 

[https://edge.launchpad.net/~openoffice-pkgs/+archive/+builds?build_text=&build_state=building](https://edge.launchpad.net/~openoffice-pkgs/+archive/+builds?build_text=&build_state=building)

The trick is to click on View Build Records. Then where there is a drop-down list where it says Needs Building , drop-down to Currently Building and one knows what is happening. After this one can go more down to actually have snapshots of where its building and all but seeing that supposedly takes more time to build. Anyways happies to find a way to know when its built or did not built, Sunday is a good day as any for packages to be built ;)

1. The version of OO.O is 1170 in the bzr branch. I was just browsing through the changes and control file that one can view at [http://bazaar.launchpad.net/~openoffice-pkgs/openoffice/3.0-intrepid/revision/1170]("http://bazaar.launchpad.net/%7Eopenoffice-pkgs/openoffice/3.0-intrepid/revision/1170")

and one thing caught my eye is this :-

 Vcs-Svn: svn://svn.gnome.org/svn/ooo-build/branches/ooo-build-3-0 
13  Homepage: [http://www.go-oo.org](http://www.go-oo.org)

A glance at the go-oo.org gives some interesting things which could happen. Looking forward to testing it when it happens.

---

### Post by lonniehenry on 2008-09-27
Try this one:    [http://openofficeorg.secsup.org/contrib/rc/3.0.0rc2/](http://openofficeorg.secsup.org/contrib/rc/3.0.0rc2/)


it came from [http://download.openoffice.org/3.0beta/](http://download.openoffice.org/3.0beta/) and clicking extended mirrors and picking your version from the local list.

and the instructions :
```
1. Head to the download page and select the Linux (deb) or Linux 64 bit (deb) download. Decompress the archive to your desktop.
2. Installing OpenOffice requires installing a large number of DEB packages. It’s easiest to install them using the terminal. Open a terminal, switch to the directory where you decompressed the download to, and install all the packages at once:
cd ~/Desktop/OOO300_m7_native_packed-1_en-US.9354
sudo dpkg -i DEBS/*.deb
3. That will not have added you any Application menu items. You can create one yourself using the menu editor (System->Preferences->Main Menu). Menu icon graphics are available in /usr/share/icons/hicolor/48×48/apps. Launch OpenOffice with this command:
/opt/openoffice.org3/program/soffice
4. You can delete the download from your desktop after the installation.

Want to remove OpenOffice 3? I’ve compiled this huge command (it’s all one line) to remove all of the OpenOffice 3 packages:
sudo apt-get remove ooobasis3.0-base ooobasis3.0-binfilter ooobasis3.0-calc ooobasis3.0-core01 ooobasis3.0-core02 ooobasis3.0-core03 ooobasis3.0-core04 ooobasis3.0-core05 ooobasis3.0-core06 ooobasis3.0-core07 ooobasis3.0-draw ooobasis3.0-en-us ooobasis3.0-en-us-base ooobasis3.0-en-us-binfilter ooobasis3.0-en-us-calc ooobasis3.0-en-us-draw ooobasis3.0-en-us-help ooobasis3.0-en-us-impress ooobasis3.0-en-us-math ooobasis3.0-en-us-res ooobasis3.0-en-us-writer ooobasis3.0-gnome-integration ooobasis3.0-graphicfilter ooobasis3.0-images ooobasis3.0-impress ooobasis3.0-javafilter ooobasis3.0-kde-integration ooobasis3.0-math ooobasis3.0-onlineupdate ooobasis3.0-ooofonts ooobasis3.0-ooolinguistic ooobasis3.0-pyuno ooobasis3.0-testtool ooobasis3.0-writer ooobasis3.0-xsltfilter openoffice.org3 openoffice.org3-base openoffice.org3-calc openoffice.org3-dict-en openoffice.org3-dict-es openoffice.org3-dict-fr openoffice.org3-draw openoffice.org3-en-us openoffice.org3-impress openoffice.org3-math openoffice.org3-writer openoffice.org-ure

you may have to change the commands to match the version that you downloaded.
```

---

### Post by ShirishAg75 on 2008-09-27
lionel, just a suggestion, when you are giving a big command, go to Go Advanced, on the bar above which has many functions, use the # or CODE function, wrap the command in the CODE function. It makes it much much easier for :-
a) people to distinguish the command from rest of the stuff 
b) it does not make the post look so big

The end result, the post looks beautiful and thought about.

---

### Post by IanW on 2008-09-28
It seems that the 32-bit packages have now been successfully built.

---

### Post by ShirishAg75 on 2008-09-28
Correct and I am downloading it as we speak. No need to wait for it to show up in the NEW queue and stuff. Get the show on the road and see what is happening ;)

Update:- Downloaded and using. It works, would do more testing later but it downloaded and installed without any issues and that is good for starters ;)

---

### Post by caryb on 2008-09-28
I downloaded the 64 bit version & installed, all works great but when I try to update from adept I get this..

root@stinkpad:~# apt-get -f upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  ooobasis3.0-base ooobasis3.0-calc ooobasis3.0-core02 ooobasis3.0-core03
  ooobasis3.0-core04 ooobasis3.0-core05 ooobasis3.0-core07 ooobasis3.0-draw
  ooobasis3.0-en-us ooobasis3.0-en-us-base ooobasis3.0-en-us-calc
  ooobasis3.0-en-us-draw ooobasis3.0-en-us-help ooobasis3.0-en-us-impress
  ooobasis3.0-en-us-math ooobasis3.0-en-us-writer
  ooobasis3.0-gnome-integration ooobasis3.0-graphicfilter ooobasis3.0-images
  ooobasis3.0-impress ooobasis3.0-javafilter ooobasis3.0-kde-integration
  ooobasis3.0-math ooobasis3.0-onlineupdate ooobasis3.0-ooofonts
  ooobasis3.0-ooolinguistic ooobasis3.0-pyuno ooobasis3.0-testtool
  ooobasis3.0-writer ooobasis3.0-xsltfilter openoffice.org3
  openoffice.org3-base openoffice.org3-calc openoffice.org3-dict-en
  openoffice.org3-dict-es openoffice.org3-dict-fr openoffice.org3-draw
  openoffice.org3-en-us openoffice.org3-impress openoffice.org3-math
  openoffice.org3-writer
0 upgraded, 0 newly installed, 41 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1254kB disk space will be freed.
Do you want to continue [Y/n]?


Cary

---

### Post by plun on 2008-09-28
> **ShirishAg75 said:**
> 
Update:- Downloaded and using. It works, would do more testing later but it downloaded and installed without any issues and that is good for starters ;)

Yup, installed and works

full output

[http://paste.ubuntu.com/51575/](http://paste.ubuntu.com/51575/)

Minor issues with these:

```
- javaldx: Could not find a Java Runtime Environment! ( my comment>JRE installed)

-dpkg: openoffice.org-core: dependency problems, but removing anyway as you request:  python-uno depends on openoffice.org-core (= 1:2.4.1-9ubuntu1).

-dpkg: openoffice.org-l10n-en-gb: dependency problems, but removing anyway as you request: openoffice.org-help-en-gb depends on openoffice.org-l10n-en-gb; however:  Package openoffice.org-l10n-en-gb is to be removed.
```

---

### Post by ssam on 2008-09-28
the 1:3.0.0~rc2-1ubuntu2 version in the PPA fixes my previous issues.

Thanks for all the work.

---

### Post by jfernyhough on 2008-09-28
Up and running with rc2.

Interestingly, though, this rc2 says it's m7 - I used an m27 build a month ago. Unless the m27 was  branch for ooo3.0.1 or something....

---

### Post by Bou on 2008-09-28
Is there a comprehensive list of all the new features somewhere?

Thanks guys.

---

### Post by UbuWu on 2008-09-28
> **Bou said:**
> Is there a comprehensive list of all the new features somewhere?


A pretty list is here: [http://marketing.openoffice.org/3.0/featurelistbeta.html](http://marketing.openoffice.org/3.0/featurelistbeta.html)

A comprehensive list is here: [http://development.openoffice.org/releases/3.0.0rc2.html](http://development.openoffice.org/releases/3.0.0rc2.html)

---

### Post by victorche on 2008-09-28
There is RC3 already:
[http://development.openoffice.org/releases/3.0.0rc3.html](http://development.openoffice.org/releases/3.0.0rc3.html)

Download:
[ftp://sunsite.informatik.rwth-aachen.de/pub/mirror/OpenOffice/contrib/rc/3.0.0rc3/OOo_3.0.0rc3_20080927_LinuxIntel_install_en-US.tar.gz](ftp://sunsite.informatik.rwth-aachen.de/pub/mirror/OpenOffice/contrib/rc/3.0.0rc3/OOo_3.0.0rc3_20080927_LinuxIntel_install_en-US.tar.gz)

---

### Post by ShirishAg75 on 2008-09-28
The way these guys are making new builds (going hammer and tongs), our friend calc is going to have a horrid time rebuilding stuff to make us happy. Of course we all hope in the end we get some bleeding edge coolness :P

---

### Post by nanog on 2008-09-28
Variable error bars in calc. An excel 1997 feature.

---

### Post by jfernyhough on 2008-09-29
> **nanog said:**
> Variable error bars in calc. An excel 1997 feature.Word autocompletion in Writer. A Word 2009 feature? :P

---

### Post by nanog on 2008-09-29
[http://wiki.services.openoffice.org/wiki/ReleaseStatus_Minutes_2008-09-29_IRC_log](http://wiki.services.openoffice.org/wiki/ReleaseStatus_Minutes_2008-09-29_IRC_log)

Looks like no show-stoppers in RC3 so far. Final release on track for Tues next week.

---

### Post by ntetreau on 2008-09-29
> **victorche said:**
> There is RC3 already:
[http://development.openoffice.org/releases/3.0.0rc3.html](http://development.openoffice.org/releases/3.0.0rc3.html)

Download:
[ftp://sunsite.informatik.rwth-aachen.de/pub/mirror/OpenOffice/contrib/rc/3.0.0rc3/OOo_3.0.0rc3_20080927_LinuxIntel_install_en-US.tar.gz](ftp://sunsite.informatik.rwth-aachen.de/pub/mirror/OpenOffice/contrib/rc/3.0.0rc3/OOo_3.0.0rc3_20080927_LinuxIntel_install_en-US.tar.gz)

To download the [debs]("http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.0.0rc3"):
[http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.0.0rc3](http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.0.0rc3)

---

### Post by LavianoTS386 on 2008-09-30
^ Are those for 32 and 64 bit?

---

### Post by thonuz on 2008-09-30
64, 32 etc here.
[ftp://sunsite.informatik.rwth-aachen.de/pub/mirror/OpenOffice/contrib/rc/3.0.0rc3/](ftp://sunsite.informatik.rwth-aachen.de/pub/mirror/OpenOffice/contrib/rc/3.0.0rc3/)

No problems here so far. I don't see any changes in the HTML editing really, but I guess its all writer or same.

---

### Post by bash on 2008-10-06
Got OOo 3 up and running from Calcs repo. Works smooth so far. Now I wanted to test out the new PDF Import feature and downloaded the OOo extension from their website ([Link]()). Every time I try to install the extension then in the Extension Manager I get an error along the lines of "The extension does/will not run on your computer".

Anyone got an idea what I might be doing wrong?

---

### Post by victorche on 2008-10-06
And RC4 is here too:
[http://spout.ussg.indiana.edu/openoffice/contrib/rc/3.0.0rc4/OOo_3.0.0rc4_20080930_LinuxIntel_install_en-US.tar.gz](http://spout.ussg.indiana.edu/openoffice/contrib/rc/3.0.0rc4/OOo_3.0.0rc4_20080930_LinuxIntel_install_en-US.tar.gz)
:popcorn:

---

### Post by ShirishAg75 on 2008-10-06
poor calc, now he has to make an RC4 as well and we would gladly take it ;)

---

### Post by UbuWu on 2008-10-07
> **ShirishAg75 said:**
> poor calc, now he has to make an RC4 as well and we would gladly take it ;)

And so he did... rc4 is now in the PPA. just a little more waiting until the packages have been built!

---

### Post by nanog on 2008-10-07
*salivates*

---

### Post by fubarbundy on 2008-10-08
> **UbuWu said:**
> And so he did... rc4 is now in the PPA. just a little more waiting until the packages have been built!

WARNING - it looks like openoffice.org-common is missing from the latest build, and if you (accidentally) update without realising it is uninstalling most of openoffice, you may not be able to use ooo 3.0 until the missing file reappears (the rc2 build is no longer available).

Can you tell it happened to me? :)

---

### Post by autocrosser on 2008-10-08
Hey mate---your link goes nowhere--I would like to look at it to see. Please repost.


> **bash said:**
> Got OOo 3 up and running from Calcs repo. Works smooth so far. Now I wanted to test out the new PDF Import feature and downloaded the OOo extension from their website ([Link]("http://Link")). Every time I try to install the extension then in the Extension Manager I get an error along the lines of "The extension does/will not run on your computer".

Anyone got an idea what I might be doing wrong?

---

### Post by plun on 2008-10-08
After a "loooooooong" build RC4 is ready.... :)

No problems with install and apps starts.

---

### Post by olskar on 2008-10-08
> **autocrosser said:**
> Hey mate---your link goes nowhere--I would like to look at it to see. Please repost.

Think this is it

[http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport)

---

### Post by adam on 2008-10-08
Open Office fails to start in Kubuntu Intrepid. Upon launching, it brings up the document recovery screen, but then fails, saying "due to an unexpected error, Open Office has crashed..."

Error from terminal:
```
QPainter::begin: A paint device can only be painted by onepainter at a time.
QPainter::setWorldTransform: Painter not active 
```

Then...
```
ASSERT: "slOpt" in file /build/buildd/kde4libs-4.1.2/kdeui/kernel/kstyle.cpp, line 3314
```

---

### Post by UbuWu on 2008-10-08
> **olskar said:**
> Think this is it

[http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport)

It is also available as a package in the PPA.

---

### Post by bruno666 on 2008-10-09
> **adam said:**
> Open Office fails to start in Kubuntu Intrepid. Upon launching, it brings up the document recovery screen, but then fails, saying "due to an unexpected error, Open Office has crashed..."


Same error on my Kubuntu Intrepid amd64 :/

I wonder if openoofice.org 3 could work with KDE4/QT4. I can't even launch any ooo app with ppa's rc4 packages, and it crashed with rc2 each time I tried to save or open a document.

Maybe it's a KDE4/Oxygen style related bug. If I use another style in systemsettings (plastik for instance), oowriter crashed immediately with this message in console :

QPixmap: Invalid pixmap parameters
X-Error: BadDrawable (invalid Pixmap or Window parameter)
        Major opcode: 55 (X_CreateGC)
        Resource ID:  0x0
        Serial No:    5113 (5113)

---

### Post by adam on 2008-10-09
Any ideas on how to fix the KDE problem?

Thanks.

---

### Post by DC@DR on 2008-10-11
Sorry for going offtopic, but is there any chance that we will get OOo 3.0 into Hardy?

---

### Post by jblackhall on 2008-10-11
> **DC@DR said:**
> Sorry for going offtopic, but is there any chance that we will get OOo 3.0 into Hardy?

It will almost definitely be available in backports in Hardy.  Or did you mean Intrepid?

---

### Post by exploder on 2008-10-11
I would hope OpenOffice 3 will be available for Hardy because of it's ability to work with MS Office 2007 documents. Many will stay with the LTS release, especially businesses.

---

### Post by dasunst3r on 2008-10-11
And now the final's out.  Looks like calc is gonna need to build debs for that!

---

### Post by mc4100 on 2008-10-11
Is anyone else having trouble changing the icon styles with 3.0 (yes, the openoffice.org-style packages are installed)?

---

### Post by Golgoth on 2008-10-11
> **mc4100 said:**
> Is anyone else having trouble changing the icon styles with 3.0 (yes, the openoffice.org-style packages are installed)?

same problem here...

---

### Post by wgrant on 2008-10-11
> **mc4100 said:**
> Is anyone else having trouble changing the icon styles with 3.0 (yes, the openoffice.org-style packages are installed)?

What!? NO!! A bug!? NO SUCH THING! We must put it into Intrepid, as it is flawless! Damn developers being stupid.

</usermode>

---

### Post by int on 2008-10-11
> **wgrant said:**
> What!? NO!! A bug!? NO SUCH THING! We must put it into Intrepid, as it is flawless! Damn developers being stupid.

</usermode>

lol :guitar:

---

### Post by ShirishAg75 on 2008-10-11
I am just looking when calc does the final build, he did come in yesterday as his profile shows

---

### Post by victorche on 2008-10-12
> **wgrant said:**
> What!? NO!! A bug!? NO SUCH THING! We must put it into Intrepid, as it is flawless! Damn developers being stupid.

</usermode>

Excuse me, but i don't think this type of fun is needed here ...
All those users who ask for OO 3.0 have their reasons.

I'm one of those and believe me, i have reasons for that. Not just the number "3" as i am not some kind of voodoo man who makes magic with numbers.

I need OO 3.0 for a office with some PC's who have Ubuntu installed. And the people working there really need to deal with MS Office 2007 documents.

And since Ubuntu is userfriendly... some kind of "click and install" OS... i prefer to have it as an official .deb package.

Don't worry about me. I am writing this post from a OS, where kernel source is installed by default and where commands like configure & make are available.

So all those users ask for it, because they need it and they prefer the easier way of having it. They don't want to search in Google, to use some unofficial debs, to deal with console errors...
"Linux for human beings"... Remember ;)

---

### Post by wgrant on 2008-10-12
> **victorche said:**
> Excuse me, but i don't think this type of fun is needed here ...
All those users who ask for OO 3.0 have their reasons.


And all of those developers who say "no" have their reasons too.

> So all those users ask for it, because they need it and they prefer the easier way of having it. They don't want to search in Google, to use some unofficial debs, to deal with console errors...
"Linux for human beings"... Remember ;)

Most human beings don't want the latest crack. They want something that works, and works well.

---

### Post by plun on 2008-10-12
> **wgrant said:**
> And all of those developers who say "no" have their reasons too.

Most human beings don't want the latest crack. They want something that works, and works well.

Well, in this case there is a situation and a "glory chance" to get rid of MS Office.

Everyone IS looking at OO 3.0 as substitute, NOT OO-2.4.

Can you please direct us to a open discussion about this ?  (mailing list)

---

### Post by wgrant on 2008-10-12
> **plun said:**
> Everyone IS looking at OO 3.0 as substitute, NOT OO-2.4.

Do you have evidence for this? Most people don't know that it exists.

---

### Post by victorche on 2008-10-12
> **wgrant said:**
> Most human beings don't want the **latest crack**...

You're calling OpenOffice this way? :)

Nice approach... So Sun makes a "crack", Fedora (Red Hat), SuSE, Mandriva is using this "latest crack".

But Ubuntu is above all those "cracks" and groups of amateurs... Forgot that, sorry :confused:

---

### Post by plun on 2008-10-12
> **wgrant said:**
> Do you have evidence for this? Most people don't know that it exists.

YES, "tons of them". 

The big dragon IDG is running a "filial" in Sweden and they also got a great Open Source editor (also a Ubuntu fan :))

It has been several articles about going over to OpenOffice and this is a discussion among persons working for public institutions (boss position) and professionals/admins.

Article in swedish when those met:
[http://www.idg.se/2.1085/1.182189](http://www.idg.se/2.1085/1.182189)

and they discusses **OO 3.0** !!!

----

To discuss:

-  Cd size, exclude presentation perhaps

-  Debian, not a reason

-  Bugs, lets test

-  Operational against MS Office 2007... is it a problem ?


So I want better argument from you then "the standard argument" for not  as you wrote earlier...

This is important !

---

### Post by inportb on 2008-10-12
> **victorche said:**
> You're calling OpenOffice this way? :)

Nice approach... So Sun makes a "crack", Fedora (Red Hat), SuSE, Mandriva is using this "latest crack".

But Ubuntu is above all those "cracks" and groups of amateurs... Forgot that, sorry :confused:

Of course! What else would you call a bit of software that's attracted 12 pages of posts in such a short time? :)

---

### Post by wgrant on 2008-10-12
> **victorche said:**
> You're calling OpenOffice this way? :)

Nice approach... So Sun makes a "crack", Fedora (Red Hat), SuSE, Mandriva is using this "latest crack".

But Ubuntu is above all those "cracks" and groups of amateurs... Forgot that, sorry :confused:

This is the term we use for general new untested software.

---

### Post by wgrant on 2008-10-12
> **inportb said:**
> Of course! What else would you call a bit of software that's attracted 12 pages of posts in such a short time? :)

It could be good, or it could be broken. Note the recent threads about the wallpaper and the Firefox EULA. Or it could just have a particularly vocal set of users. Length of thread has little bearing on anything.

---

### Post by forger on 2008-10-12
Calm down everyone :KS I also agree that new software should be decently tested before being exposed to a broader sum of users.
If something got broken in a stable release, then users would whine, just as they do for the ugly default wallpaper in intrepid beta :P

You have two options:
1) If you want to test it, test it and make everyone, including yourself and the developers happy. But know that it can be broken and that by testing you would make everyone even happier if you **report any bugs** you may come up with.
2) If you don't want to test it, don't test it and make everyone, including yourself and the developers happy.

ooo 3.0 will be in the repos when it's considered usable, reliable, not breakable and surely not a release candidate :)

---

### Post by plun on 2008-10-12
Well... it is tested.

[http://qa.openoffice.org/issue_handling/submission_gateway.html](http://qa.openoffice.org/issue_handling/submission_gateway.html)

I have not seen any download statistics from calcs repo but
probably a huge amount.

So I dont buy the single argument "Users wants stable software"


In this case there are also huge strategic reasons for choosing OO 3.0

IMHO  :)

---

### Post by inportb on 2008-10-12
> **wgrant said:**
> It could be good, or it could be broken. Note the recent threads about the wallpaper and the Firefox EULA. Or it could just have a particularly vocal set of users. Length of thread has little bearing on anything.

... or it could be **crack**. I like the name, so let's keep it.

---

### Post by Perfect Storm on 2008-10-12
> **forger said:**
> Calm down everyone :KS I also agree that new software should be decently tested before being exposed to a broader sum of users.
If something got broken in a stable release, then users would whine, just as they do for the ugly default wallpaper in intrepid beta :P

You have two options:
1) If you want to test it, test it and make everyone, including yourself and the developers happy. But know that it can be broken and that by testing you would make everyone even happier if you **report any bugs** you may come up with.
2) If you don't want to test it, don't test it and make everyone, including yourself and the developers happy.

ooo 3.0 will be in the repos when it's considered usable, reliable, not breakable and surely not a release candidate :)

+1

But I guess it's hard to make both camp happy :popcorn:
I suggest that those who wants to play with oo3 either download and install it manually or ask the guys at getdeb.
[https://launchpad.net/~getdeb](https://launchpad.net/~getdeb)

---

### Post by Buffalo Soldier on 2008-10-12
Moaner and whiner 1: *"!@#$%^&& developer, why **DIDN'T** they include ABC software version X.Y??? It rocks!!!"*

Moaner and whiner 2: *"!@#$%^&& developer, why **DID** they include ABC software version X.Y??? It sucks!!!"*

Both groups thinks the developers are purposely doing things to screw everyone... have not gone through meeting, discussions, testing and etc before coming to a decision.

Since early 2005 till now... things still haven't changed :(

---

### Post by gnomeuser on 2008-10-12
> **Buffalo Soldier said:**
> Moaner and whiner 1: *"!@#$%^&& developer, why **DIDN'T** they include ABC software version X.Y??? It rocks!!!"*

Moaner and whiner 2: *"!@#$%^&& developer, why **DID** they include ABC software version X.Y??? It sucks!!!"*

Both groups thinks the developers are purposely doing things to screw everyone... have not gone through meeting, discussions, testing and etc before coming to a decision.

Since early 2005 till now... things still haven't changed :(

And to play devils advocate..

Some of this rests solely on the developers hands, if you know a major release is coming within your release cycle you can either elect to adopt the work early and help remove the kinks or you can sit back and ensure that way that your users are stuck with a version of the software that is potentially unsupported by upstream.

---

### Post by int on 2008-10-12
For who want to test OpenOffice 3.0 Ubuntu intrepid add this in sources.

calc's PPA

```

deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main

```

then:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

It have the RC4 version, but in this week will release the final one.
Work well for me..

---

### Post by plun on 2008-10-12
Lets use it....:)   and have fun !  


**Useful tips and tricks for 3.0**

[http://openoffice.blogs.com/](http://openoffice.blogs.com/)
.

---

### Post by nanog on 2008-10-12
Plun, I thought wgrant's </usermode> post was not only hilarious but also very salient. And this is coming from someone who believes that OOo 3 *should* be in intrepid. My reasoning is that 2.4 has a number of use-ability bugs that, IMO, make it useless at the enterprise level. Until open office 3 came out I had to use R, gnumeric, m$ office, and OOo presentation to get any serious work done.

---

### Post by _oOMOo_ on 2008-10-12
Is there any particular reason why OpenOffice (and the GIMP for that matter) insist on leaving scroll bars cluttering up the screen when the working area is not full? On a large laptop screen it's an irritation, on a small form factor screen it's a gross waste of important screen real estate.

I suppose [the bug]("http://www.openoffice.org/issues/show_bug.cgi?id=42100") is only 2 and a half YEARS old, no sense in moaning.

---

### Post by exploder on 2008-10-12
I will wait for the 3.0 version to be released in the main repos. Things are finally looking good for Intrepid. I would rather be patient, the OpenOffice update will become available when it is ready.

---

### Post by plun on 2008-10-12
> **nanog said:**
> Plun, I thought wgrant's </usermode> post was not only hilarious but also very salient. And this is coming from someone who believes that OOo 3 *should* be in intrepid. My reasoning is that 2.4 has a number of use-ability bugs that, IMO, make it useless at the enterprise level. Until open office 3 came out I had to use R, gnumeric, m$ office, and OOo presentation to get any serious work done.

Well.. it is nearly useless for corporate needs.

I am just checking his arguments and I don't find them
convincing for me.  

But maybe there are more better arguments...

Its so "damned" easy to give someone a Ubuntu CD and just say, "Please test "

Without O0 3.0 its much more work with a ppa or backport to test OO 3.0

Or that a user must test it on Windoooze...:---)

EDIT

The time is also right now for OO 3.0...

---

### Post by mc4100 on 2008-10-12
> **_oOMOo_ said:**
> Is there any particular reason why OpenOffice (and the GIMP for that matter) insist on leaving scroll bars cluttering up the screen when the working area is not full? On a large laptop screen it's an irritation, on a small form factor screen it's a gross waste of important screen real estate.

I suppose [the bug]("http://www.openoffice.org/issues/show_bug.cgi?id=42100") is only 2 and a half YEARS old, no sense in moaning.

You can turn the horizontal scrollbar off:
Tools -> Options; OpenOffice.org Writer -> View; Uncheck the box.

---

### Post by _oOMOo_ on 2008-10-12
> **mc4100 said:**
> You can turn the horizontal scrollbar off:
Tools -> Options; OpenOffice.org Writer -> View; Uncheck the box.

Thanks, I wasn't aware of that setting.

It does beg the question that if someone was bothered to code that into the preferences/settings, would it have been that much more of a stretch to add a " display if required" option?

---

### Post by eyelessfade on 2008-10-12
Since nothing else is breaking on my system lately I'll have to try ooo ppa :)

---

### Post by olskar on 2008-10-12
> **eyelessfade said:**
> Since nothing else is breaking on my system lately I'll have to try ooo ppa :)

If you want breakage you should use something else then ooo ;) I think it is very stable

---

### Post by inportb on 2008-10-12
Hm... OO.o 3.0 via Calc crashes upon launch, for me. I'd not like to see that in Intrepid-proper in the current state. lol.

---

### Post by int on 2008-10-12
> **inportb said:**
> Hm... OO.o 3.0 via Calc crashes upon launch, for me. I'd not like to see that in Intrepid-proper in the current state. lol.

work's very well for me..

---

### Post by plun on 2008-10-12
OO 3.0 uploads

> Subject: 3.0.0 upload status


Hi,

should be distributing now. If you like to help with doing release QA 
for the en-US files then you could help eg. by testing the en-US 
language packs. Linux 64 bit wJRE would be a candidate as well...

[http://qatrack.services.openoffice.org/view_status.php?version=3.0.0&language](http://qatrack.services.openoffice.org/view_status.php?version=3.0.0&language)[]=en-US&available=60&uri=&view=detailed

Kind regards, Joost



[http://www.openoffice.org/servlets/BrowseList?listName=releases&by=date&from=2008-10-01&to=2008-10-31&first=1&count=71](http://www.openoffice.org/servlets/BrowseList?listName=releases&by=date&from=2008-10-01&to=2008-10-31&first=1&count=71)

Out tomorrow...

Bug status from my own country was "Zero"....

---

### Post by LadFromWales85 on 2008-10-12
> **bruno666 said:**
> Same error on my Kubuntu Intrepid amd64 :/

I wonder if openoofice.org 3 could work with KDE4/QT4. I can't even launch any ooo app with ppa's rc4 packages, and it crashed with rc2 each time I tried to save or open a document.

Maybe it's a KDE4/Oxygen style related bug. If I use another style in systemsettings (plastik for instance), oowriter crashed immediately with this message in console :

QPixmap: Invalid pixmap parameters
X-Error: BadDrawable (invalid Pixmap or Window parameter)
        Major opcode: 55 (X_CreateGC)
        Resource ID:  0x0
        Serial No:    5113 (5113)

Is there any fix knocking about for this issue?

---

### Post by olskar on 2008-10-12
> **plun said:**
> 
Bug status from my own country was "Zero"....

Glad to hear that ;)

---

### Post by plun on 2008-10-12
> **olskar said:**
> Glad to hear that ;)

Well, there are bugs, but not any "shipping bugs"..

ZDnet was even earlier

[http://blogs.zdnet.com/hardware/?p=2704](http://blogs.zdnet.com/hardware/?p=2704)

All servers will be synchronised tonight for release.....

---

### Post by inportb on 2008-10-12
> **int said:**
> work's very well for me..

Heh, it worked well enough for me, until I decided to reinstall to clean up some stuff. Then:

```
ASSERT: "slOpt" in file /build/buildd/kde4libs-4.1.2/kdeui/kernel/kstyle.cpp, line 3314
```

I know it's been mentioned in this thread before, and it's related to KDE. However, I know it worked for me before I reinstalled, which is funny :)

---

### Post by JGrubbs on 2008-10-13
I just upgraded my OOo to 3.0 by adding the following lines to my Software Sources:

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

I have been running Ibex for about a week now, so far I haven't had any problems with OOo 3.0.

---

### Post by elfgoh on 2008-10-13
> **JGrubbs said:**
> I just upgraded my OOo to 3.0 by adding the following lines to my Software Sources:

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

I have been running Ibex for about a week now, so far I haven't had any problems with OOo 3.0.

I am sorry if this has been answered elsewhere. But may I ask if Intrepid will be shipped with OOo 3.0 eventually?

---

### Post by Sef on 2008-10-13
> I am sorry if this has been answered elsewhere. But may I ask if Intrepid will be shipped with OOo 3.0 eventually?

Unlikely, but it will be available in the backports.

---

### Post by jbernardo on 2008-10-13
Anyone tested the final version with KDE 4.1.2 yet?

---

### Post by jbernardo on 2008-10-13
Anyone tested the final version with KDE 4.1.2 yet?

---

### Post by ger_macaco on 2008-10-13
> **inportb said:**
> Heh, it worked well enough for me, until I decided to reinstall to clean up some stuff. Then:

```
ASSERT: "slOpt" in file /build/buildd/kde4libs-4.1.2/kdeui/kernel/kstyle.cpp, line 3314
```

I know it's been mentioned in this thread before, and it's related to KDE. However, I know it worked for me before I reinstalled, which is funny :)

Same here. I get a recovery file dialog and then this ASSERT.

---

### Post by inportb on 2008-10-13
Yep. And you know what's the best thing? I tried starting up OO.o while running a different WM/Desktop (Enlightenment DR17), *and get the same result*, with the KDE 4.1.2 assert and all. Naturally one would go "wtf," right? =p

---

### Post by xebian on 2008-10-13
> **jbernardo said:**
> Anyone tested the final version with KDE 4.1.2 yet?


I just installed the debs from OO, and it works very nicely in KDE4.1.2

---

### Post by inportb on 2008-10-13
Where do the OO debs install the software?

---

### Post by fballem on 2008-10-13
> **inportb said:**
> Where do the OO debs install the software?

In subfolders under /opt - at least on my system.

---

### Post by rbmorse on 2008-10-13
under /opt here, too (IA32)

---

### Post by xebian on 2008-10-13
> **inportb said:**
> Where do the OO debs install the software?

rightfully so in /opt

---

### Post by inportb on 2008-10-14
Ah great; I might be installing these packages myself, then. Thanks.

---

### Post by ger_macaco on 2008-10-14
> **ger_macaco said:**
> Same here. I get a recovery file dialog and then this ASSERT.

Removing repository's installation and installing official .deb files from openoffice.org solved it.

---

### Post by muzzamo on 2008-10-14
> **JGrubbs said:**
> I just upgraded my OOo to 3.0 by adding the following lines to my Software Sources:

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

I have been running Ibex for about a week now, so far I haven't had any problems with OOo 3.0.

Then how do you you upgrade?

Do you just do an "apt-get upgrade" or do you install new packages?

---

### Post by sayantandas on 2008-10-14
thanx for the PPA clac.

i hve added the repo and used update manager. it came up with all the upgradeable options for OO3.0, now its downloading updates. hopefully it will install properly

PS: it installed perfectly fine.. no issues.. it just replaced the 2.4.1 version

---

### Post by NachoMas on 2008-10-14
a fresh installation from the ppa repository installs already in /usr. Anyway, has anyone succeded in installing some extensions? I have tried with three different extensions and the extension manager always complains with 'loading component library failed'. I have checked that the JRE is recognized as Sun Micro 1.6.0_07 so I don't understand why it is not working... 
Any hints?
Tx!

---

### Post by plun on 2008-10-14
> **NachoMas said:**
> a fresh installation from the ppa repository installs already in /usr. Anyway, has anyone succeded in installing some extensions? I have tried with three different extensions and the extension manager always complains with 'loading component library failed'. I have checked that the JRE is recognized as Sun Micro 1.6.0_07 so I don't understand why it is not working... 
Any hints?
Tx!

What gives this

```
sudo update-alternatives --config java
```

JRE ? 

Can you also post a URL for this extension ?

OpenJava broken  :confused:

---

### Post by NachoMas on 2008-10-14
nacho@Caliope:~$ sudo update-alternatives --config java

There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.

and I have tried with three different extensions:

[http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport)
[http://extensions.services.openoffice.org/project/presenter-screen](http://extensions.services.openoffice.org/project/presenter-screen)
[http://extensions.services.openoffice.org/project/PresentationMinimizer](http://extensions.services.openoffice.org/project/PresentationMinimizer)

and all of them complained the same way...

---

### Post by plun on 2008-10-14
> **NachoMas said:**
> nacho@Caliope:~$ sudo update-alternatives --config java

There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.

and I have tried with three different extensions:

[http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport)
[http://extensions.services.openoffice.org/project/presenter-screen](http://extensions.services.openoffice.org/project/presenter-screen)
[http://extensions.services.openoffice.org/project/PresentationMinimizer](http://extensions.services.openoffice.org/project/PresentationMinimizer)

and all of them complained the same way...


I posted my install log earlier within this thread  :)

[http://ubuntuforums.org/showpost.php?p=5868816&postcount=78](http://ubuntuforums.org/showpost.php?p=5868816&postcount=78)

```
- javaldx: Could not find a Java Runtime Environment! 
```

Going to test this later....

---

### Post by plun on 2008-10-14
Tested and with the same error

[[img]http://ubuntu-pics.de/thumb/4442/oo3_ouE50E.jpg[/img]](http://ubuntu-pics.de/bild/4442/oo3_ouE50E.jpg)


We need someone with a **"Final" install** testing this...(don't want to mess up my PC)


EDIT we probably needs a developer...

[http://udk.openoffice.org/common/man/concept/uno_corba.html](http://udk.openoffice.org/common/man/concept/uno_corba.html)

---

### Post by orduek on 2008-10-14
same problem here.

---

### Post by plun on 2008-10-14
Well... now I messed up my PC and the Final version works. :)

But...you cannot have 2 versions installed.

-RC4 removed

- /.openoffice and /.openoffice2  removed  (hidden folders)

OO crashes otherwise

- Install final and run from /opt

---

### Post by orduek on 2008-10-14
does the final version should hit Calc's repos soon?

---

### Post by Gina on 2008-10-14
I've now upgraded to OOo 3 and running the database (added via Synaptic as the standard installation doesn't include the database).  OK so far.

---

### Post by calc on 2008-10-14
BTW - upstream rc4 is final, they decided it was good enough to rename to final.

However I will also be uploading a openoffice.org 1:3.0.0-2ubuntu1 later today, probably in a couple hours. Since we use ooo-build it will include more fixes via patches so won't be exactly the same as the rc4 build from last week.

---

### Post by Gina on 2008-10-14
> **calc said:**
> BTW - upstream rc4 is final, they decided it was good enough to rename to final.

However I will also be uploading a openoffice.org 1:3.0.0-2ubuntu1 later today, probably in a couple hours. Since we use ooo-build it will include more fixes via patches so won't be exactly the same as the rc4 build from last week.Sounds good :)  Thank you :)

---

### Post by xebian on 2008-10-14
> **muzzamo said:**
> Then how do you you upgrade?

Do you just do an "apt-get upgrade" or do you install new packages?

Same thing as you have been doing - apt-get upgrade.  OO is not that special.  However, if you have Ubuntu's repo then you are always behind.

If you installed direct from OO official debs, then you are always updated when OO release updates by online updates direct from the menu.

---

### Post by calc on 2008-10-14
> **xebian said:**
> Same thing as you have been doing - apt-get upgrade.  OO is not that special.  However, if you have Ubuntu's repo then you are always behind.

If you installed direct from OO official debs, then you are always updated when OO release updates by online updates direct from the menu.

But then you won't have any of the over 500 patches from ooo-build (go-oo.org) that fix many problems and add features, etc.

---

### Post by inportb on 2008-10-14
Yeah, and this is why I hesitate to install the official packages. Yet... this bug annoys me :(
I look forward to the new packages ^^

---

### Post by jbernardo on 2008-10-15
Lets just hope that none of those patches add back the kde4 incompatibility... :)

---

### Post by orduek on 2008-10-15
> **plun said:**
> Well... now I messed up my PC and the Final version works. :)

But...you cannot have 2 versions installed.

-RC4 removed

- /.openoffice and /.openoffice2  removed  (hidden folders)

OO crashes otherwise

- Install final and run from /opt

after updating for the latest in Calc's Repo - still same problem.
Do I need to remove everything first?

---

### Post by adam on 2008-10-15
Works in kde now!

---

### Post by plun on 2008-10-15
> **orduek said:**
> after updating for the latest in Calc's Repo - still same problem.
Do I need to remove everything first?

Everything isn't built yet

[https://launchpad.net/~openoffice-pkgs/+archive](https://launchpad.net/~openoffice-pkgs/+archive)

Core packages was just ready.


(Final standalone works just fine)

---

### Post by orduek on 2008-10-15
So it'll be a while before I'll be able to use those extensions?

---

### Post by plun on 2008-10-15
> **orduek said:**
> So it'll be a while before I'll be able to use those extensions?

I just tested and switched back to ppa and the new version installs

- The old yellow splash, not the blue one as with Final

- I cannot import extensions.

Maybe I have a mess so others must confirm it.

---

### Post by bash on 2008-10-15
I can't install yet. If I try to upgrade from RC4 to final, it still wants to remove all my language-support files (not just the ones from OOo).

---

### Post by ViRMiN on 2008-10-15
Should be okay now... I was getting the same earlier on but, not now.

---

### Post by bash on 2008-10-15
> **ViRMiN said:**
> Should be okay now... I was getting the same earlier on but, not now.

Yea works fine now.

> **plun said:**
> I just tested and switched back to ppa and the new version installs

- The old yellow splash, not the blue one as with Final

- I cannot import extensions.

Maybe I have a mess so others must confirm it.

Importing extensions works for me me, but I also still get the yellow splash. I have the splash disabled by default anyways, so I'm not really bothered about it.

---

### Post by orduek on 2008-10-15
I still am unable to install Sun extensions (like PdfImport).

---

### Post by plun on 2008-10-15
> **orduek said:**
> I still am unable to install Sun extensions (like PdfImport).

Yup, I have double check my install and basic functionality such as Suns extensions are broken.

The final OpenOffice version can be installed parallell

[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

It might also be needed to remove settingsfolders /.openoffice /.openoffice2, had some crashes otherwise.

---

### Post by orduek on 2008-10-15
I don't like this.
I rather wait until the Calc repo will be fine for installing extensions otherwise its to much fuss for me right now.

---

### Post by mwcrowley on 2008-10-15
for those who can't wait.
Use at your discretion.

wget [http://openofficeorg.secsup.org/stab...-US_deb.tar.gz](http://openofficeorg.secsup.org/stab...-US_deb.tar.gz)

tar -xvzf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz

sudo dpkg -i OOO300_m9_native_packed-1_en-US.9358/DEBS/*.deb

enjoy, I am.

---

### Post by inportb on 2008-10-15
calc's already uploaded the stuff; I'm getting it now :)

### EDIT ###
Ooh, and the best part is that it doesn't crash anymore. Thanks calc!

---

### Post by bruno666 on 2008-10-15
The final release works fine with KDE4 now ;-) (Kubuntu Intrepid AMD64)

---

### Post by jbernardo on 2008-10-16
> **bruno666 said:**
> The final release works fine with KDE4 now ;-) (Kubuntu Intrepid AMD64)

I can confirm that, no problems with OOo 3.0 final until now on kubuntu.

---

### Post by orduek on 2008-10-16
> **orduek said:**
> I don't like this.
I rather wait until the Calc repo will be fine for installing extensions otherwise its to much fuss for me right now.

I just don't know if what I said here makes any sense.
does it?

---

### Post by kennydidit on 2008-10-17
ok I added the two apt sources.list entries from PPA and upgraded my openoffice, but now I get a splash screen that says 3.0 then an error box that just flashes so fast I cannot read it. so I went back to PPA and started to manually load the files most say I need openoffice.org-core. then when I go to install that file I get an error: dependency is not satisfiable: libgtk2.0-0, but that file is in stalled. so what I am missing or doing wrong? any help

---

### Post by inportb on 2008-10-17
Can you post your sources.list?

> **orduek said:**
> [QUOTE=orduek;5969313]I don't like this.
I rather wait until the Calc repo will be fine for installing extensions otherwise its to much fuss for me right now.I just don't know if what I said here makes any sense.
does it?[/QUOTE]

I tend to have the same attitude.

---

### Post by shane19174 on 2008-10-17
I'm really sorry if this should be obvious to me by now, but can someone tell me what the easiest and/or safest way to install OOo 3.0 is now? I understand people's trepidations about installing before it's in backports, but I'm hoping that 3.0 will allow me to ditch MS Office (almost) completely and really don't want to wait any longer than necessary. The thing I really need is the new marginal notes function, which I need to test for compatibility with MS Office-generated notes. (I use these notes to communicate with colleagues on academic papers.)

So how can I upgrade safely (i.e. without removing ubuntu-desktop and without wiping out all my language settings, etc)? Ideally, OOo 3.0 would start as the default app when I click on a .doc file, and it would be updated automatically through synaptic when the time comes.

I appreciate any help on this,
Shane

---

### Post by nanog on 2008-10-17
Put Calc's ppa (Ubuntu Dev who packages OOo3) in your sources.list:

#Calc's_open_office_ppa
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

upgrade and install.

---

### Post by plun on 2008-10-17
Well I can take the penalty for posting this again.

[[IMG]http://brainstorm.ubuntu.com/idea/14433/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/14433/)

---

### Post by xebian on 2008-10-17
> **plun said:**
> Well I can take the penalty for posting this again.

[[IMG]http://brainstorm.ubuntu.com/idea/14433/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/14433/)

You guys are being inconsiderate of the other 'buntu users.  The OO is about 155MB plus maybe another 50MB for the java stuff.  So how can you fit it in the 700MB CD, and which one going to be left behind?  We have to be realistic here.  Leave it in the repo for those who wants it.  :)

---

### Post by plun on 2008-10-17
> **xebian said:**
> You guys are being inconsiderate of the other 'buntu users.  The OO is about 155MB plus maybe another 50MB for the java stuff.  So how can you fit it in the 700MB CD, and which one going to be left behind?  We have to be realistic here.  Leave it in the repo for those who wants it.  :)

Well, I am a *proud* Ubuntu user and not a stupid "buntu" user which Debians Offtopic group talks about.

This can be arranged and its just to make it possible  !

This IS about bug No 1 and also about normal users need.

[http://www.librarian.net/stax/2042/do-you-ubuntu/](http://www.librarian.net/stax/2042/do-you-ubuntu/)

Jessamyn needs OO-3 within her library with donated PCs!

---

### Post by mister_pink on 2008-10-17
> **plun said:**
> Well I can take the penalty for posting this again.

[[IMG]http://brainstorm.ubuntu.com/idea/14433/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/14433/)

I think this is why the devs more or less ignore brainstorm. Users don't seem to understand the words "not going to happen". Think about it - the release is 2 weeks away. There is no way they are going to suddenly upgrade a core package. 

If they had ever wanted to include version 3 it would have been in there as a beta since the beginning to ease the transition (think firefox 3 in hardy).

---

### Post by Toadinator on 2008-10-17
> **xebian said:**
> You guys are being inconsiderate of the other 'buntu users.  The OO is about 155MB plus maybe another 50MB for the java stuff.  So how can you fit it in the 700MB CD, and which one going to be left behind?  We have to be realistic here.  Leave it in the repo for those who wants it.  :)

I do believe that we can just remove the existing OOo and replace it with the new one, which isn't that much larger, correct?

---

### Post by dasunst3r on 2008-10-17
> **xebian said:**
> You guys are being inconsiderate of the other 'buntu users.  The OO is about 155MB plus maybe another 50MB for the java stuff.  So how can you fit it in the 700MB CD, and which one going to be left behind?  We have to be realistic here.  Leave it in the repo for those who wants it.  :)OpenOffice.org 2.4.1 is already included in the initial install (which, it is fair to assume, is on the CD).  As someone mentioned, replacing OpenOffice.org 2.4.1 with Openoffice 3 would work.

---

### Post by inportb on 2008-10-17
It would not work, because users would no longer have the choice to install the more stable OO.o off the disc.

---

### Post by xebian on 2008-10-17
> **dasunst3r said:**
> OpenOffice.org 2.4.1 is already included in the initial install (which, it is fair to assume, is on the CD).  As someone mentioned, replacing OpenOffice.org 2.4.1 with Openoffice 3 would work.

You & Toadinator are right.  I didn't realize it's in Ubuntu.:oops: I'm a K/X 'buntu user which does not include OO.  Anyway, my point is, it's available from the repo (finally I hope) as well as from OO direct for those who wants it.  Not just for Intrepid but for Hardy as well.  No waiting.  :biggrin:

---

### Post by Joe on 2008-10-17
I seem to have broken something since I upgraded Kubuntu Intrepid to OpenOffice 3 using the Calc repos.  I can't login anymore unless I do it from the terminal under sudo.  KDM just gets to the globe icon and hangs from there.  It must be a permission problem somewhere since I'm able to login as sudo.

edit: Looks like it changed the permissions for .ICEauthority in my home folder.  Changing them back fixed my problem.

---

### Post by inportb on 2008-10-17
> **xebian said:**
> I'm a K/X 'buntu user which does not include OO.

orly? I'm using Kubuntu and OO.o 2.4.x was installed off the disc.

---

### Post by DouglasAWh on 2008-10-17
> **inportb said:**
> orly? I'm using Kubuntu and OO.o 2.4.x was installed off the disc.

I'm pretty sure Xubuntu doesn't though...

---

### Post by DouglasAWh on 2008-10-17
> **xebian said:**
> it's available from the repo 

which repo is OOo3 in?  I was under the impression it wouldn't be in Hardy?

---

### Post by inportb on 2008-10-17
Yeah. Xubuntu comes with abiword&co.?

---

### Post by shane19174 on 2008-10-18
> Put Calc's ppa (Ubuntu Dev who packages OOo3) in your sources.list:

#Calc's_open_office_ppa
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

upgrade and install.

OK, I did this and all went well. OOo 3.0 is now the standard application for .docs and the rest. However, I am no longer able to switch between English and German dictionaries, spell-checkers, etc. It seems the English language packages were all updated through Calc's repo, but none of the German packages. So my question: how does one go about adding non-English language support at the moment? Are the packages being prepared? Any idea how long I would have to wait? I would prefer getting them from a repository rather than downloading and manually installing extensions (if this is possible), so that everything remains updated.

Any suggestions are appreciated,
Shane

---

### Post by javierrivera on 2008-10-22
Hi,

This is quite a big thread, and I don't know if this is the best place to report a bug, but I can't find another (and I asked).

I have upgraded openoffice using this ppa and everything went well. After a while I tried to install the pdfimport extension from Sun, and it failed. So I take a closer look and I find that it tries to link libstlport_gcc.so and fails. I checked /usr/lib and found only a file called libstlport_gcc.so.4.6, so I made a new link (so that /usr/lib/libstlport_gcc exists). After that I has been able to install the pdfimport extension and import a couple of PDFs.

So, what should I do to have this bug fixed?. Here?. Libstlport mantainer? Upstream?.

Javier.

---

### Post by olskar on 2008-10-22
The version in Calcs repo is slower on my computer then the official debs, has anyone else experienced that?

---

### Post by wilbur.harvey on 2008-10-22
I noticed that on my large .odt document, it is MUCH slower than the official open office release. Lots of very long pauses trying to scroll through the document, where as the official open office release zips right through without any delays.

Earlier builds of open office had similar delays.

---

### Post by olskar on 2008-10-22
> **wilbur.harvey said:**
> I noticed that on my large .odt document, it is MUCH slower than the official open office release. Lots of very long pauses trying to scroll through the document, where as the official open office release zips right through without any delays.

Earlier builds of open office had similar delays.

A bug should perhaps be filed about this?

---

### Post by yostral on 2008-10-22
> **javierrivera said:**
> After a while I tried to install the pdfimport extension from Sun,
pdfimport is in the repos and it works.

---

### Post by javierrivera on 2008-10-23
> **yostral said:**
> pdfimport is in the repos and it works.

Nice. But I still think that the "normal" version downloaded from the "normal" openoffice.org extension repositories should work.

Specially when the problems is as simple to solve as adding a link.

There are two sane options from an user point of view, make the Ubuntu OpenOffice work with upstream extensions, or pack every possible extension in Ubuntu repos. Only one is sane from a developer pov.

Javier.

---

### Post by danf_1979 on 2008-10-23
Yes, it is slow here too, specially when opening presentation files. If you look the system monitor or top when opening files, you'll see openoffice using 100% CPU till the file is completely loaded. It does open all files though. The thing is that it seems to take forever to do so.

---

### Post by sjhstorm on 2008-10-23
I am using the official debs version in Kubuntu 8.10, which I find to be noticeably quicker than previous versions. I also installed pdfimport from openoffice and it works fine.

I have been very lucky with the official debs as it also picked up the KDE look and feel. As it stands I think I will remain with this even when it is put in the ubuntu repo.

---

### Post by wilbur.harvey on 2008-10-23
> **yostral said:**
> pdfimport is in the repos and it works.

Yes, it works, but it is VERY slow.

---

### Post by petersaints on 2008-10-24
So If I want OpenOffice.org 3.0 should I use this Repository or just the Official Debs?

---

### Post by ShirishAg75 on 2008-10-24
Hi guys, 
 I reinstalled Intrepid from scratch due to some issues and then installed Oo3.0 from calc's repository. I tried to get pdfimport from the Oo.0 extension but pdfimport didn't get installed. I did a
```
gksudo oowriter 
```

I get this :-

```

loading component library failed:

file:///var/spool/openoffice/uno_packages/cache/uno_packages/0qQBE2_/pdfimport.oxt/pdfimport.uno.so

```

Any ideas gentleman.

---

### Post by javierrivera on 2008-10-24
> **ShirishAg75 said:**
> Hi guys, 
Any ideas gentleman.

Two ideas:

1) Install the pdfimport extension from the repository.

or

2) 

```
sudo ln -s /usr/lib/libstlport_gcc.so.4.6 /usr/lib/libstlport_gcc.so

```

and the extension should work.

Javier.

---

### Post by ShirishAg75 on 2008-10-24
lol, what do I know, the extension is in the repo as  openoffice.org-pdfimport , thanx  javierrivera

---

### Post by MJWitter on 2008-10-25
Hey, not sure if anyone has tried to use open office 3 with Guest session?

When i try to open any of the applications(Spreadsheet,Word Processor etc) I get the following:

"Open office - Fatal Error
The application cannot be started.
The component manager is not available.  Start the setup application to repair the installation from the CD or the folder containing the installation packages.  "

Im not sure if this is caused by OO(using calcs repo) or Guest session.

Is anyone else getting this behaviour?

---

### Post by shuttleworthwannabe on 2008-10-26
Hi There
just installed OOo3 using calc's repo's. Is this still beta or the final release of OOo?
I must say it is very quick to launch and responds quickly as well.

Many thanks
S

---

### Post by ktp on 2008-10-26
it should be the final release version

---

