---
title: "libreoffice incredibly buggy in 12.10?"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by ogresav on 2012-10-21
I just upgraded to quantal and I'm working on a paper in libreoffice writer and have noticed a number of bugs.
 ](*,)
After saving the paper, the menu items have disappeared. I can click the menu title but no menu items show up. I closed LibreOffice and reopened it, and am having the same issue.
I couldn't insert a page break either.
Is this a problem with my system or are other people experiencing anything like this in the stock libreoffice with 12.10?
I'd really like to work with some reliable office suite soon because this semester is pretty busy. I have to favor usability and reliability over features right now..
Any suggestions? A good alternative to LibreOffice in the repos, or is it something else wrong with my system?

Thanks!

---

### Post by twipley on 2012-10-23
This is problematic. I am in the same situation as you are in right now, and when that happens one has to either remember shortcuts, or reboot the computer, which is kind of an inconvenience.

---

### Post by stbub on 2012-10-23
> **ogresav said:**
> I just upgraded to quantal and I'm working on a paper in libreoffice writer and have noticed a number of bugs.
 ](*,)
After saving the paper, the menu items have disappeared. I can click the menu title but no menu items show up. I closed LibreOffice and reopened it, and am having the same issue.

Thanks!

I did a very quick check, and I haven't seen the problem.

I'm using gnome shell, not unity.  Unity does weird things with the menus.  Are you using Unity or Gnome Shell as your desktop environment?  Logoff, and try switching (you might have to first install gnome shell if you don't already have it).

---

### Post by twipley on 2012-10-24
Using default Unity the problem is there sometimes, but not always, though (which I forgot to note).

---

### Post by rattskjelke on 2012-10-24
LibreOffice 3.6.2 crashed a couple times on Xubuntu 12.10 and I have also had the 3.6.2 Windows version "Not Responding" for up to about 20 seconds on Windows 7 several times so I don't think it is a Ubuntu problem.

I never had any problems with earlier versions of LO.

---

### Post by sabinedoll on 2012-10-27
I have the same problem. Libre0ffice is unusable, frequently crashes, and the items in the new "global menu" do not work reliably (i.e. no response or crash).
I will have to try to install an older version or go back to Ubuntu 12.04, or another operating system. I also do not like that the window menus were removed.

---

### Post by twipley on 2012-10-28
> **sabinedoll said:**
> I also do not like that the window menus were removed.
This one is not a bug, though, as it was intended, being part of the Unity integration, which was the whole objective for Quantal.

[http://www.omgubuntu.co.uk/2012/05/uds-q-summary-bye-bye-unity-2d-hello-gnome-shell-spin](http://www.omgubuntu.co.uk/2012/05/uds-q-summary-bye-bye-unity-2d-hello-gnome-shell-spin)

---

### Post by judderwocky on 2012-10-29
yes. very buggy for me as well. 

somehow it truncated a novel i've been working on when i saved it, and then uploaded it to the cloud. 

it destroyed the file. i'm lucky i obsessively backup everything. 

12.10 is horrible in every possible way.

---

### Post by jrog on 2012-10-29
The issue with the disappearing menu is a known bug that is still being worked on. There have been various bug reports for it -- here, for example: [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1064962](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1064962). So, you're not the only one! I believe the options right now are (i) dealing with it :(, (ii) using a WM other than Unity, (iii) removing the package 'indicator-appmenu' from your system, thereby disabling the global menus, or (iv) trying the experimental packages mentioned toward the end of the bug report to which I linked, if you are able to get them (they've been having problems building).

---

### Post by offgridguy on 2012-10-29
> **judderwocky said:**
> 

12.10 is horrible in every possible way.

Hmmmm..........

---

### Post by El Ploppo on 2012-10-30
Got the same thing here. (If) the top menu appears, the menu will work normally for some time, then it will become totally unresponsive and LO will not even react to keyboard-shortcuts. Things like 'Recent Files' will open the wrong files, when you click on one LO will open an other.
Under 12.04 LO was reasonably workable, but under 12.10 it's almost unworkable. (BTW: I use LO Calc most of the time).

I really hope this will get solved, or is it time to look for another distro than Ubuntu? (Or is this a LO problem?)

---

### Post by harlequin_ on 2012-11-23
Hi,

Just wanted to note it's the same story for me as well (while using Calc): Weird behaviour of the top panel menu, as it sometimes does not appear. Frequent crashes..

one way to get around the menu problem is to open (from dash home) a new Calc sheet and make switches back and forth between the sheet with no menu bars and newly opened sheet.

---

### Post by jrog on 2012-11-23
> **harlequin_ said:**
> Hi,

Just wanted to note it's the same story for me as well (while using Calc): Weird behaviour of the top panel menu, as it sometimes does not appear. Frequent crashes..

one way to get around the menu problem is to open (from dash home) a new Calc sheet and make switches back and forth between the sheet with no menu bars and newly opened sheet.
When's the last time you upgraded the software on your system? They recently released an update that should have fixed at least some of this behavior.

---

### Post by vanadium on 2012-11-24
These issues are due to a bad support of the Unity global menu for libre office. Even when these issues are fixed, which I think they are (I only upgraded to 12.10 a week ago and did not experience these issues), you will be stuck with Alt+key combinations to use the menu are not working.

What is there now, is the HUD, of course. However, I don't feel that can replace for convenient direct keyboard access to the menu. The hud is excellent to find items that you do not know here they are in the menu. It works slower, though, than using some key combinations to get directly where you want.

Current workaronds (if are not a tester and need your work done) are:
1) Disable global menu support for LibreOffice. In previous versions, you'd remove one package, lo-menu. Currently, you must remove libreoffice-gtk to remove global menu support. However, you will also loose all other gnome integration.

2) Disable the global menu and revert to window specific menu's: "sudo apt-get autoremove indicator-appmenu appmenu-gtk appmenu-gtk3 appmenu-qt". That's how I currently survive.

---

### Post by Hagar Delest on 2012-11-25
For the problems not linked to the menu, you can try first to [reset your OpenOffice user profile](http://forum.openoffice.org/en/forum/viewtopic.php?p=58403#p58403).

If no change, you can install LO with the official .debs available on their website. See: [[Ubuntu] Installing OOo on Debian and Co.](http://forum.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

You can also switch to Apache OpenOffice, much less buggy IMHO, install with the same process as above.

---

### Post by wribeiro on 2012-11-26
LibreOffice is unusable under Ubuntu 12.10. How can Canonical release an operating system so buggy?
Office Suite is a key part of Ubuntu and needs to be treated carefully so that always works perfectly, in every version.
It would have been better to Canonical postpone 12.10 than launch it with so many problems. 
I'm very disappointed about this.
:mad:

---

### Post by wribeiro on 2012-11-26
This is what happens when we open multiple documents with double-click in Nautilus:

[IMG]http://www.topos.inf.br/imagens/libreoff_ub1210_bug-scrshot1.png[/IMG]

[IMG]http://www.topos.inf.br/imagens/libreoff_ub1210_bug-scrshot2.png[/IMG]

:confused:

---

### Post by Zill on 2012-11-26
> **wribeiro said:**
> ...It would have been better to Canonical postpone 12.10 than launch it with so many problems...
You do realise that Ubuntu 12.10 is basically an interim (eg. beta) release of Ubuntu based on Debian Testing?  This is not, by definition, a "stable" system.

No one forces anyone to upgrade to the latest six-monthly release.  These releases are aimed at those who are happy to "test-drive" and accept occasional breakage.  If you want a stable OS and applications then stick to the older releases, preferably LTS.  eg.  Ubuntu 10.04 is still fully supported until April 2013 and includes the (relatively bug-free) OpenOffice.org v3.2.

---

### Post by wribeiro on 2012-11-26
Zill, thanks for your reply.

In 6 years I have been one of the biggest promoters of Ubuntu because I believe strongly in the project.
But when a standard user accesses Ubuntu site and is invited to download the CD, nothing is said about the instability and the possibility of errors of the latest version.
I complain because I know these problems can create serious rejection on new users because of this.

---

### Post by vasa1 on 2012-11-26
> **wribeiro said:**
> ...
... But when a standard user accesses Ubuntu site and is invited to download the CD, nothing is said about the instability and the possibility of errors of the latest version.
I complain because I know these problems can create serious rejection on new users because of this.
+1.
Both Ubuntu and LibreOffice get a bad rep. Even though LibreOffice has "production" and less stable versions, one has to dig a bit to know that the latest isn't necessarily the greatest.

---

### Post by vanadium on 2012-11-26
> You do realise that Ubuntu 12.10 is basically an interim (eg. beta) release of Ubuntu based on Debian Testing? This is not, by definition, a "stable" system.
This is not how the Ubuntu release shedule is conceived. The 6 month releases of Ubuntu are designed to be stable releases, useable by end-users yet providing the latest technology. The LTS releases are intended for users or environments where stability, both in the meaning of "error free" and "predictable", is of prime importance at the expense of latest features.

Yet that argument would it make even worse when the release has highly visible and blatant bugs with core productivity software such as an office suite.

I stepped into 12.10 only a week ago. My mayor problem was that Alt+hotkey menu access is not available with the global menus. I have disabled the global menu as a temporary stop measure, and thus I do not have extensive experience of LO with the global menu. However, some of the most severe issues may have been fixed in the mean time.

Another issue I still see is the interaction with the launcher. When an icon is locked, starting a document from nautilus starts a different icon rather than using the pinned icon. Still not working correctly, although the current situation is way better than in stock 12.04, where instances of LibreOffice would disappear from the laucher and could not anymore be activated, not using the launcher and not using Alt+tab. As a stop measure here, I removed pinned LO icons from the launcher. LO is quite useable and troube free since.

---

### Post by Hagar Delest on 2012-11-26
wribeiro, your problem is with the font used. Go to Tools>Options>LibreOffice>View and check the option Use system font for user interface.

As for Ubuntu, even if their packaging is way too much "integrated" with some applications (like LibreOffice), I've never faced major problems, even using beta versions of FF and TB installed directly from the tarballs.

---

### Post by Zill on 2012-11-26
> **vanadium said:**
> This is not how the Ubuntu release shedule is conceived. The 6 month releases of Ubuntu are designed to be stable releases, useable by end-users yet providing the latest technology. The LTS releases are intended for users or environments where stability, both in the meaning of "error free" and "predictable", is of prime importance at the expense of latest features...
Err, I'm afraid Ubuntu releases *were* conceived this way from the outset.  Ubuntu has always been based on either Debian unstable (non-LTS) or Debian testing (primarily LTS releases).

While both Debian unstable and testing are "relatively" stable for normal use, this point must be borne in mind by users who need reliable, stable systems, such as for work.

See "[Ubuntu is based on Debian unstable]("http://mdzlog.alcor.net/2009/03/08/ubuntu-is-based-on-debian-unstable/")" by Matt Zimmerman, former Canonical chief technical officer.

---

### Post by vasa1 on 2012-11-26
> **Zill said:**
> Err, I'm afraid Ubuntu releases *were* conceived this way from the outset.  ....
Concepts apart, if people sincerely want to get past the "~1% desktop share" they should be more clear about what is what. 

Expecting potential users to immerse themselves in the history and philosophy of something may be too much. And while some may be familiar with the *release early, release often* mantra, others won't.

*Each* release has a beta and a release candidate. Just like software intended as a production release. Why? To avoid confusion, the non-LTS versions should carry "unstable" or "testing" as part of their name.

---

### Post by TenPlus1 on 2012-11-27
Am using Lubuntu 12.10 and no problems so far using LibreOffice...

---

### Post by vasa1 on 2012-11-27
> **TenPlus1 said:**
> Am using Lubuntu 12.10 and no problems so far using LibreOffice...
Same here ;) but I got my LibO 3.6.2.2 (Build ID: da8c1e6) direct and not via a ppa and will be in no hurry to update it.

But OP has LibreOffice running on Unity which is where the problem, if any, lies. See this: [http://ubuntuforums.org/showthread.php?p=12375336#post12375336](http://ubuntuforums.org/showthread.php?p=12375336#post12375336)
and this: [http://ubuntuforums.org/showthread.php?p=12375345#post12375345](http://ubuntuforums.org/showthread.php?p=12375345#post12375345)

---

### Post by wribeiro on 2012-11-27
> **Hagar Delest said:**
> wribeiro, your problem is with the font used. Go to Tools>Options>LibreOffice>View and check the option Use system font for user interface.


Hagar Delest, LibreOffice font is correctly configured in my system. Everything works fine while there is only one or two documents opened in LO. 
I suppose that you will get the same behavior if you repeat the steps in your system. Just open multiple documents, one at a time, by double clicking filename in Nautilus. At some point the screen flashes and system font (menus and toolbars) gets shuffled. Other open applications (Chromium, for example) are also affected at this moment and everything must be closed.

---

### Post by jrog on 2012-11-27
> **wribeiro said:**
> Hagar Delest, LibreOffice font is correctly configured in my system. Everything works fine while there is only one or two documents opened in LO. 
I suppose that you will get the same behavior if you repeat the steps in your system. Just open multiple documents, one at a time, by double clicking filename in Nautilus. At some point the screen flashes and system font (menus and toolbars) gets shuffled. Other open applications (Chromium, for example) are also affected at this moment and everything must be closed.
I tried to replicate your bug and failed. I opened ten different LO documents, one by one, by double-clicking on the filenames in Nautilus, and there were no problems. I've also never seen anyone else mention this bug. Does it exist on Launchpad, for example? If it doesn't, I'm wondering if perhaps something is misconfigured on your system (fonts or locales, perhaps?).

---

### Post by wribeiro on 2012-11-27
jrog, thanks for making the tests.
Fonts and locale are correctly configured here.
Since the problem can not be replicated in other environments, I must assume that it is a conflict between LibreOffice and proprietary video driver nvidia-experimental-304 that I'm using on my HP Pavilion dv6000.
That does not happen in any other circumstance, only when opening files in LibreOffice and affects other open applications.

---

### Post by wribeiro on 2012-11-27
Changing video driver to nvidia-current-updates the problem keeps happening, but we need to open more documents until the menu font becomes scrambled.
In the last test I had to open 12 text document.

Can someone please make this test by opening a large amount of text documents (over 15 or 20), one by one, with double click?

---

### Post by Hagar Delest on 2012-11-27
I've opened 15 documents (.doc and .odt) with right click in Nautilus (default association is set to AOO on my system). No problem so far, even after a while.

With LO 3.6.2.2 on Quetzal and Gnome 3.6.0.

If you change the font in the View options, does it help?

---

### Post by wribeiro on 2012-12-03
Hagar Delest, thanks for making the tests.

Actually this bug became less important to me, as another, much more serious, caused by kernel update (3.7), brought me serious trouble with video driver. I'm able to live with LibreOffice bugs, I'll wait for a new version and hope they stop to occur.
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1084523](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1084523)

---

### Post by kevinr1 on 2012-12-04
My bug seems to be that the menus in LO appear but don't work, i.e., File -> Save does not work when clicked on.  For me the solution was to restart LO and not having to reboot... yet.

---

### Post by eec on 2012-12-04
I have two machines  with Ubuntu. One has 12.10 amd64 and the other has i386. Both versions have a very buggy LibreOffice. LOs crash all the time, respond very late, you cannot even scroll down in a document without having a problem. Most of the problems are to be seen in the Writer.

On the both machines I removed the LO (3.6.2etc) that came default and installed a newer version from the LO (3.6.3) website. And, that was it. It works perfect now.

Of course, Ubuntu has to fix the problem. But, I really cannot deal with it and spend my time to find some solutions on Google.

---

### Post by vanadium on 2012-12-05
No problem here with stock Libre Office, except for known issues 1) no hotkey acces to main menu (e.g. Alt+F to open the file menu); workaround: I removed global menu, and 2) after some time, instances of LibreOffice are not anymore attached to a locked LO icon, but appear as a separate icon (that, at least, is fully functional; workaround: no locked LO icons in the launcher for now. With these two workarounds, I am left with a stable LO on 12.10.

---

### Post by wribeiro on 2012-12-12
There are other people experiencing the same problem:
[http://ubuntuforums.org/showthread.php?t=2074308](http://ubuntuforums.org/showthread.php?t=2074308)

---

