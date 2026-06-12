---
title: "Open Office 2.x uninstallation and Open Office 3.0.0 installation"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by fuzzybear3965 on 2008-11-13
This is a noob guide to removing old OpenOffice from your system and installing the new OpenOffice 3.0.0 with a 32-bit CPU configuration.

First: Download the .deb packages from either

                      1.  [[COLOR="RoyalBlue"]Here[/COLOR]]("http://download.openoffice.org/other.html") making sure to click the column labeled **Linux DEB** and the column of your desired language. (**go to step 2**)

       or
 
                      1.  [COLOR="RoyalBlue"][[COLOR="RoyalBlue"]Here[/COLOR]]("http://distribution.openoffice.org/p2p/")[/COLOR] again making sure to click the drop down bars to the right distribution (**Linux(x86) (.deb based)**).  Then select version, OpenOffice.org 3.0.0, or as desired.  Next, click desired language of choice and start saving the torrent with a torrent client (deluge, transmission, utorrent, vuze, utorrent (**utorrent needs WINE**)) (**go to step 2**)

2.  Save the OpenOffice file to a subdirectory called OpenOffice in your home folder (e.g. /home/john/openoffice) make sure it's all lower case.  Linux is case sensitive and lowercase will make it easier in the future.  Next begin by removing all traces of previous OpenOffice with the terminal.

3.  Open the terminal and type 

            [CENTER] sudo apt-get --purge remove openoffice.org-core
[/CENTER]
4.  Then navigate to your openoffice directory 

[CENTER]               cd /home/*_**user**_*/openoffice[/CENTER]

5.  extract the .deb file either by

            a.  right-clicking and selecting 'extract here'

            b.  with a terminal command (e.g. 
        
         [CENTER] tar -xvzf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz [/CENTER] )

6.  Open the terminal if you have not, navigate to the extracted DEBS directory inside OOO300_m9_native_packed-1_en-US.9358 and type:

                      [CENTER] sudo dpkg -i *.deb
[/CENTER]

7.  Finally, and optionally, to install a pre-made set of launchers and other useful accessibility features type in terminal:

                    [CENTER] cd desktop-integration[/CENTER]
followed by:

         [CENTER]sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb [/CENTER]

8.  Once it has successfully installed you can delete the extracted folders and either delete the downloaded .deb or you can save it for later use (reinstallation purposes, for example)

That's it!!! If you find errors either respond to this post or send me an email at [email]fuzzybear3965@yahoo.com[/email]

---

### Post by ad_267 on 2008-11-13
It's probably a better idea to install from the PPA repositories. A PPA is now available for Hardy. See [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml) for 8.10 instructions and [http://kshoster.net/node/56](http://kshoster.net/node/56) for 8.10 and 8.04.

---

### Post by fuzzybear3965 on 2008-11-14
Yeah that's an option but for noobs I'd rather they don't modify their repositories just yet.  Best to break them in with the debian package system and I don't want them thinking they need to add a repository every time just to download a single package.  But yes, if you are more comfortable with altering repositories and know the risks involved, then feel free.

---

### Post by shavano47 on 2008-11-16
I am running Ubuntu 8.10. I followed your directions for un-installing
OpenOffice2.4 and installing OpenOffice3.0 until I tried to install the
launchers. Here is what I got at the Terminal:

DellLatitude:~/openoffice/OOO300_m9_native_packed-1_en-US.9358/DEBS/desktop-integration$ sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb
dpkg: regarding openoffice.org3.0-debian-menus_3.0-9354_all.deb
containing openoffice.org-debian-menus:
 openoffice.org-common conflicts with openoffice.org-debian-menus
  openoffice.org-debian-menus (version 3.0-9354) is to be installed.
dpkg: error processing openoffice.org3.0-debian-menus_3.0-9354_all.deb
(--install):
 conflicting packages - not installing openoffice.org-debian-menus
Errors were encountered while processing:
 openoffice.org3.0-debian-menus_3.0-9354_all.deb
nigel@NigelDellLatitude:~/openoffice/OOO300_m9_native_packed-1_en-US.9358/DEBS/desktop-integration$

There seems to be some kind of conflict. Synpatic Package Manager shows
that Open Office  3.0 is installed but it doesn't show in the Applications menu?:(

I very much appreciate your guidance.   shavano47

---

### Post by shavano47 on 2008-11-16
Correction I am running Ubuntu 8.04 Hardy Heron

Newbie  shavano47

---

### Post by fuzzybear3965 on 2008-11-16
The reason it does not show it in the applications menu is because, while it is technically installed, the launchers (a link to the actual program) are not written to the applications menu.  So while you could navigate to the installation directory and click it manually every time, that command I gave that failed is supposed to install launchers so that the program is easily accessible.


My advice would be to open a terminal and issue this command...

> sudo apt-get --purge remove openoffice.org-common

If that fails you can also go to synaptic package manager search "openoffice.org-common" deselect the box there and click apply.  This will remove your previous version's common directory and you should be good to go.  Contact me if you have further problems, please!

Once you have removed the "openoffice.org-common" directory you can try reinstalling the menus (repeat steps 6-8 )

---

### Post by shavano47 on 2008-11-16
FuzzyBear,   That worked! I'm now  using Open Office 3.0

Thanks a bunch.   shavano47

---

### Post by optimistique1 on 2008-11-17
WOW I managed to finally install OPen Office 3.  However, I have two things that are not right.  I cannot get the updates via the application or via the 'add/remove' software program.  How do I resolve this?

Also, I have placed the open office 3.0 icons in the WBar (I am using gOS operating system based on ubuntu 8.4).  However, when I click the icons I get the following error - see attached pic.

Hope someone can help

Thx

Garry

---

### Post by ad_267 on 2008-11-17
Edit: Never mind, I see you're using gOS so I don't know that installing from the Ubuntu repository would work.

Of course you can't get updates, because the OpenOffice in the repositories is still version 2. You have to actually add new repositories like the link I posted to get updates. That method is also much easier and adds menu launchers.

---

### Post by fuzzybear3965 on 2008-11-17
Do you mean that you installed the launchers via command prompt or that you dragged the command file to the applications menu?

Edit:  Also since gOS (a new linux version to me) is based on Ubuntu 8.04 you should add the PPA repositories advised by ad_267.  This should work; if not, we'll keep working on this.  Keep in mind I have never touched gOS and do not know its repository system.  However, if it works on a debian package system and you have the capability to add repositories to your database you should be able to add those PPAs and be good to go.  Follow ad_267's link up towards the top.

---

### Post by loveandequality on 2008-12-16
this is more simple.

> **1/0 said:**
> Its not that difficult actually. All you have to do is:

1) Download the compressed file from the [downloads page](http://download.openoffice.org/index.html). The torrent was damn fast!

2) Open a terminal (next steps are all in the same terminal window) and go to the directory containing the downloaded file, often Desktop.

```
cd Desktop
```

3) Extract the file check the name.

```
tar -zxvf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz
```

4) Enter the DEBS directory in the decompressed directory (check that its the correct name).

```
cd OOO300_m9_native_packed-1_en-US.9358/DEBS
```

5) Install Openoffice.

```
sudo dpkg -i *.deb
```

That's it. If you'd like to remove the old Openoffice do the following in terminal:

```
sudo apt-get remove openoffice.org openoffice.org-base openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human openoffice.org-writer
```

If you've removed the old Openoffice, you can install the package that contains the menu options (Not otherwise as you'll remove the links to the old Openoffice):

```
sudo dpkg -i ~/Desktop/OOO300_m9_native_packed-1_en-US.9358/DEBS/desktop-integration/openoffice.org3.0-debian-menus_3.0-9354_all.deb
```

I've done all steps so I don't know if Ooo3 turns up in the menu if you have both versions installed. In worst case type "/opt/openoffice.org3/program/soffice" in terminal.

Installation went really smooth for me. No problems at all. So my suggestion is to give it a try. You can always go back to the "stable" version. Just copy paste but make sure the names are the same. "ls" will list the files in the path. If you get any problems. Make a post or PM me.

---

### Post by mynydd on 2008-12-31
I used loveandequality's install method on my acer aspire one; worked first time no problems; thanks.:D

---

### Post by Claxton on 2009-01-06
I'm a brand new user of Ubuntu (3 days) this thread has been very useful thanks all.

---

