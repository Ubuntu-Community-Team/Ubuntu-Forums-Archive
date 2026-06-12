---
title: "Recent update killed compiz"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by repawn on 2010-04-08
Just updated tonight - I usually update every day - after the partial upgrade gnome uninstalled and compiz completely died. Anyone else have this problem? I have not been able to get compiz to start again and gnome do no longer gives me the ability to run docky.

---

### Post by bshosey on 2010-04-08
I think you can fix it try the following

sudo apt-get update
sudo apt-get install ubuntu-desktop

reboot

sudo aptitude safe-upgrade

---

### Post by 23meg on 2010-04-08
[QUOTE=repawn]after the partial upgrade gnome uninstalled and compiz completely died[/QUOTE]

There's [a sticky thread about partial upgrades]("http://ubuntuforums.org/showthread.php?t=1343434") that it sounds like you could benefit from reading, if you haven't.

---

### Post by descendent87 on 2010-04-08
Must have updated metacity-common, currently it want's to remove ubuntu-desktop & compiz.
Theres usually a reason why things are held back

---

### Post by repawn on 2010-04-08
Thanks for the info - read after the update unfortunately. I had some initial problems moving from 9.10 when 10.4 was in alpha - things have been stable for quite some time and was a bit surprised to have this sort of problem at the beta 2 level. I was able to re-install compiz and f-spot as it turned out - going to work on getting metacity working again.

---

### Post by The Recorder on 2010-04-09
I made the same mistake with the "Partial Upgrade".  However, in the meantime, I have chosen to use metacity with no visual effects (and compiz-gnome **UN**-installed).  Does anyone know for which update I will be looking; metacity or compiz-gnome (or paerhaps both)?  Because I don't have compiz-gnome installed, I will not know if it is upgraded.

---

### Post by psyke83 on 2010-04-09
As I'm sure you've discovered (since I assume you have since read the sticky thread), it's not a good idea to do partial upgrade. Having said that, if you need to fix the problem...

> **bshosey said:**
> I think you can fix it try the following

sudo apt-get update
sudo apt-get install ubuntu-desktop

reboot

sudo aptitude safe-upgrade

These instructions will only work when the repository is in a consistent state, and all necessary packages have been uploaded. In other words, there is no guarantee that this will fix a system broken by a partial upgrade at any given time, so you may need to be patient.

---

### Post by The Recorder on 2010-04-09
This doesn't fix the problem.  Will only let you have metacity **OR** compiz-gnome installed, not both.  That is why I wanted to know for which update I will be looking; metacity or compiz-gnome (or paerhaps both)? Again, because I don't have compiz-gnome installed, I will not know if it is upgraded.

---

### Post by psyke83 on 2010-04-09
> **The Recorder said:**
> This doesn't fix the problem.  Will only let you have metacity **OR** compiz-gnome installed, not both.  That is why I wanted to know for which update I will be looking; metacity or compiz-gnome (or paerhaps both)? Again, because I don't have compiz-gnome installed, I will not know if it is upgraded.

The solution is *patience*. My suspicion is that the metacity package incorrectly lists "compiz-gnome" within its "reverse provides", so you need to wait until metacity's package is updated.

The Partial Upgrades sticky is essential reading, and you monitor new packages uploads [here]("https://lists.ubuntu.com/archives/lucid-changes/").

---

### Post by naql on 2010-04-09
I'm guilty of running it without thinking too. It happens at least the system still works.

Found this line in the metacity changes on that list:
  * debian/control: add breaks to compiz-gnome if < new rebuild

I guess that means it breaks it if it is lower than whatever the latest version is? The latest compiz I see is 0.8.4-0ubuntu13.

---

### Post by jppr on 2010-04-09
sometimes i wonder people who use the development version without the  basic system are controlled

---

### Post by deanjm1963 on 2010-04-09
Killed my compiz too, so I'm gonna try the Kubuntu Beta 2 ... at least the KDE should be stable ... :P

---

### Post by Funnnny on 2010-04-09
Don't blame Gnome, blame your bad

---

### Post by elementxyz on 2010-04-09
get compiz to run on beta 2 but my minimize close buttons are gone! anyone with the same problem ? or a solution ?

---

### Post by lavinog on 2010-04-09
This seems bizzare:
```

aptitude show compiz-gnome
Package: compiz-gnome
State: installed
Automatically installed: no
Version: 1:0.8.4-0ubuntu13
Priority: optional
Section: x11
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 557k
Depends: libatk1.0-0 (>= 1.29.3), libc6 (>= 2.7), libcairo2 (>= 1.2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78),
         libdecoration0, libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.2.1), libgconf2-4 (>= 2.27.0), libglib2.0-0 (>= 2.16.0),
         libgnome-desktop-2-17 (>= 1:2.29.4), libgnome-window-settings1 (>= 1:2.17.5), libgtk2.0-0 (>= 2.10.0), [b]libmetacity-private0 (>=
         1:2.26.0)[/b], libpango1.0-0 (>= 1.14.0), libstartup-notification0 (>= 0.10), libwnck22 (>= 2.22.0), libx11-6, libxcursor1 (>
         1.1.2), libxrender1, zlib1g (>= 1:1.1.4), gconf2 (>= 2.12.1-1), compiz-core (= 1:0.8.4-0ubuntu13), compiz-plugins (=
         1:0.8.4-0ubuntu13), compizconfig-backend-gconf (>= 0.7.4)
Suggests: gnome-themes
...

```
apparently apt is thinking that for libmetacity-private0: version 1:2.30.0-0 is not >=1:2.26.0

looks like a bug in the package manager if I am not mistaken.

---

### Post by naql on 2010-04-09
Here is the issue:
```
aptitude show metacity
Package: metacity
State: not installed
Version: 1:2.30.0-0ubuntu1
Priority: optional
Section: x11
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 758k
Depends: libatk1.0-0 (>= 1.29.3), libc6 (>= 2.4), libcairo2 (>= 1.2.4),
         libcanberra-gtk0 (>= 0.2), libcanberra0 (>= 0.2), libgconf2-4 (>=
         2.27.0), libglib2.0-0 (>= 2.23.5), libgtk2.0-0 (>= 2.18.0), libice6 (>=
         1:1.0.0), libmetacity-private0 (>= 1:2.26.0), libpango1.0-0 (>=
         1.14.0), libsm6, libstartup-notification0 (>= 0.10), libx11-6 (>= 0),
         libxcomposite1 (>= 1:0.3-1), libxcursor1 (> 1.1.2), libxdamage1 (>=
         1:1.1), libxext6 (>= 0), libxfixes3 (>= 1:4.0.1), libxinerama1,
         libxrandr2 (>= 0), libxrender1, metacity-common (>= 1:2.30),
         metacity-common (< 1:2.31), zenity
Recommends: gnome-session | x-session-manager
Suggests: gnome-control-center (>= 1:2.5.4), gnome-themes, xdg-user-dirs
Breaks: compiz-gnome (< 1:0.8.4-0ubuntu14)
Replaces: metacity-common (< 1:2.28.0-2ubuntu1)
Provides: x-window-manager

```

See the "Breaks: compiz-gnome (< 1:0.8.4-0ubuntu14)" line? The newest compiz-gnome in the repo is 1:0.8.4-0ubuntu13. So I guess the metacity update was pushed out before the compiz-gnome version it needs was.

---

### Post by lavinog on 2010-04-09
> **naql said:**
> 
See the "Breaks: compiz-gnome (< 1:0.8.4-0ubuntu14)" line? The newest compiz-gnome in the repo is 1:0.8.4-0ubuntu13. So I guess the metacity update was pushed out before the compiz-gnome version it needs was.
I Missed that line.

---

### Post by repawn on 2010-04-09
> **elementxyz said:**
> get compiz to run on beta 2 but my minimize close buttons are gone! anyone with the same problem ? or a solution ?

That is where I am at now. I think the solution is to wait until they update either compiz or metacity I think compiz.)

Did the upgrade remove anything else on your system? It removed F-spot and Gnome-Do from mine for some reason. 

Anyway, lesson learned for me - no more partial upgrades.

---

### Post by elementxyz on 2010-04-09
f-spot and gnome-do are still here. The only problems that i have are no compiz, when compiz installed no minimize close button, and in my log in screen is no mouse cursor. Sometimes i can see a big x as mouse cursor.

---

### Post by Half-Left on 2010-04-09
> **23meg said:**
> There's [a sticky thread about partial upgrades]("http://ubuntuforums.org/showthread.php?t=1343434") that it sounds like you could benefit from reading, if you haven't.

I think there is a flaw here. Partial upgrades should 'never' be offered in the first place.

I'm all for testing but bring up a messages in the UI saying such things and then in real terms saying it's dangerous is just bad management.

---

### Post by lucazade on 2010-04-09
New metacity update breaks close button in the top-right corner.. 
I can only drag the window from the edge. :(

---

### Post by The Recorder on 2010-04-09
MY "compiz" and "compiz-gnome" packages have now been updated to 1:0.8.4-0ubuntu15.  However, in "Appearance Preferances"/"Visual Effects", if I choose "Normal", it asks me if I want to accept the changes, but none appear on the screen, and when I click "accept", it freezes.  If I choose "Extra", in "Appearance Preferances"/"Visual Effects", it tells me that "Desktop effects could not be enabled."

Anyone else having similar problems after this last update?

---

### Post by Lord Finga on 2010-04-09
> **The Recorder said:**
> MY "compiz" and "compiz-gnome" packages have now been updated to 1:0.8.4-0ubuntu15.  However, in "Appearance Preferances"/"Visual Effects", if I choose "Normal", it asks me if I want to accept the changes, but none appear on the screen, and when I click "accept", it freezes.  If I choose "Extra", in "Appearance Preferances"/"Visual Effects", it tells me that "Desktop effects could not be enabled."

Anyone else having similar problems after this last update?

Hm, the update simply doesn't arrive me... maybe they removed it from the repos again because of this bug?

---

### Post by go7Ul1ai on 2010-04-09
> **The Recorder said:**
> MY "compiz" and "compiz-gnome" packages have now been updated to 1:0.8.4-0ubuntu15.  However, in "Appearance Preferances"/"Visual Effects", if I choose "Normal", it asks me if I want to accept the changes, but none appear on the screen, and when I click "accept", it freezes.  If I choose "Extra", in "Appearance Preferances"/"Visual Effects", it tells me that "Desktop effects could not be enabled."

Anyone else having similar problems after this last update?

I am also having this problem, it sucks ^_^

---

### Post by draki on 2010-04-09
I'm also having similar problems - If I try to install Compiz-Fusion-Icon it asks me to remove mysql and install KDE - among other things:

> sudo apt-get install fusion-icon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnet-daemon-perl libmysqlclient15off libdbi-perl libhtml-template-perl
  libreadline5 libdbd-mysql-perl zlib1g-dev libplrpc-perl libmysqlclient15-dev
  mysql-client-5.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  akonadi-server compiz-kde compizconfig-backend-kconfig exiv2 gdebi-kde
  icoutils install-package kdebase-runtime kdebase-runtime-data
  kdebase-workspace-bin kdebase-workspace-data
  kdebase-workspace-kgreet-plugins kdelibs-bin kdelibs-data kdelibs4c2a
  kdelibs5 kdelibs5-data kdepim-runtime kdepimlibs-data kdepimlibs5 kdesudo
  kpackagekit ksysguardd kubuntu-debug-installer libakonadiprivate1 libattica0
  libavahi-qt3-1 libboost-program-options1.40.0 libclucene0ldbl
  libdbusmenu-qt2 libexiv2-6 libiodbc2 libkdecorations4 libkephal4
  libkfontinst4 libkscreensaver5 libksgrd4 libkworkspace4 liblua50 liblualib50
  libpackagekit-glib2-12 libpackagekit-qt-12 libphonon4
  libplasma-applet-system-monitor4 libplasma-geolocation-interface4 libplasma3
  libplasmaclock4 libplasmagenericshell4 libpolkit-qt-1-0 libprocesscore4
  libprocessui4 libqca2 libqimageblitz4 libqt3-mt libqt4-assistant
  libqt4-designer libqt4-help libqt4-qt3support libqt4-script
  libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-test
  libqt4-webkit libqt4-xmlpatterns libraptor1 librasqal2 librdf0
  libsolidcontrol4 libsolidcontrolifaces4 libsoprano4 libssh-4
  libstreamanalyzer0 libstreams0 libtaskmanager4 libweather-ion4
  mysql-server-core-5.1 oxygen-icon-theme packagekit packagekit-backend-apt
  phonon phonon-backend-xine plasma-dataengines-workspace
  plasma-scriptengine-javascript plasma-widgets-workspace polkit-kde-1
  python-kde4 python-packagekit python-qt4 python-sip
  shared-desktop-ontologies software-properties-kde soprano-daemon ttf-dejavu
  ttf-dejavu-extra update-manager-kde virtuoso-nepomuk
Suggested packages:
  libterm-readline-gnu-perl libterm-readline-perl-perl djvulibre-bin
  plasma-scriptengines perl-suid hspell libqca2-plugin-cyrus-sasl
  libqca2-plugin-gnupg libqca2-plugin-ossl libqca2-plugin-pkcs11
  libqt3-mt-psql libqt3-mt-mysql libqt3-mt-odbc libqt4-dev raptor-utils
  redland-utils librdf-storage-postgresql librdf-storage-mysql
  librdf-storage-sqlite phonon-backend-gstreamer phonon-backend-vlc
  phonon-backend-mplayer kcm-phonon-xine python-qt4-dbg
The following packages will be REMOVED
  mysql-server-5.0 mysql-server-core-5.0 squeezeboxserver
The following NEW packages will be installed
  akonadi-server compiz-kde compizconfig-backend-kconfig exiv2 fusion-icon
  gdebi-kde icoutils install-package kdebase-runtime kdebase-runtime-data
  kdebase-workspace-bin kdebase-workspace-data
  kdebase-workspace-kgreet-plugins kdelibs-bin kdelibs-data kdelibs4c2a
  kdelibs5 kdelibs5-data kdepim-runtime kdepimlibs-data kdepimlibs5 kdesudo
  kpackagekit ksysguardd kubuntu-debug-installer libakonadiprivate1 libattica0
  libavahi-qt3-1 libboost-program-options1.40.0 libclucene0ldbl
  libdbusmenu-qt2 libexiv2-6 libiodbc2 libkdecorations4 libkephal4
  libkfontinst4 libkscreensaver5 libksgrd4 libkworkspace4 liblua50 liblualib50
  libpackagekit-glib2-12 libpackagekit-qt-12 libphonon4
  libplasma-applet-system-monitor4 libplasma-geolocation-interface4 libplasma3
  libplasmaclock4 libplasmagenericshell4 libpolkit-qt-1-0 libprocesscore4
  libprocessui4 libqca2 libqimageblitz4 libqt3-mt libqt4-assistant
  libqt4-designer libqt4-help libqt4-qt3support libqt4-script
  libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-test
  libqt4-webkit libqt4-xmlpatterns libraptor1 librasqal2 librdf0
  libsolidcontrol4 libsolidcontrolifaces4 libsoprano4 libssh-4
  libstreamanalyzer0 libstreams0 libtaskmanager4 libweather-ion4
  mysql-server-core-5.1 oxygen-icon-theme packagekit packagekit-backend-apt
  phonon phonon-backend-xine plasma-dataengines-workspace
  plasma-scriptengine-javascript plasma-widgets-workspace polkit-kde-1
  python-kde4 python-packagekit python-qt4 python-sip
  shared-desktop-ontologies software-properties-kde soprano-daemon ttf-dejavu
  ttf-dejavu-extra update-manager-kde virtuoso-nepomuk
0 upgraded, 99 newly installed, 3 to remove and 0 not upgraded.
Need to get 111MB of archives.
After this operation, 205MB of additional disk space will be used.
Do you want to continue [Y/n]? 



Think I'll wait and hope they resolve the dependency issues!

---

### Post by cpmman on 2010-04-09
Appearance Clearlooks sorted it for me - you can cycle through the alternatives and watch the min/max/close buttons cycle on and off.

---

### Post by elementxyz on 2010-04-09
new updates breaks my login.
recovery boot

shell with network

and sudo apt-get install ubuntu-desktop let's me start the system again.

But compiz is not available for now.

---

### Post by praveenthivari on 2010-04-09
> **elementxyz said:**
> f-spot and gnome-do are still here. The only problems that i have are no compiz, when compiz installed no minimize close button, and in my log in screen is no mouse cursor. Sometimes i can see a big x as mouse cursor.

Exactly same thing happened here.
I have installed back metacity and compiz and running the system without any compiz effects at the moment.

Edit: I think the problem is [COLOR="Red"]SOLVED[/COLOR] in recent updates. I ran refresh of updates and there were about 40 Mb of new updates and after restart, I tried to install compiz back and there was no conflict. So went ahead and intalled tht. Now having both without any apparent prob:-)

---

### Post by 0004tom on 2010-04-09
> **praveenthivari said:**
> Exactly same thing happened here.
I have installed back metacity and compiz and running the system without any compiz effects at the moment.

Edit: I think the problem is [COLOR="Red"]SOLVED[/COLOR] in recent updates. I ran refresh of updates and there were about 40 Mb of new updates and after restart, I tried to install compiz back and there was no conflict. So went ahead and intalled tht. Now having both without any apparent prob:-)

Nope, I just ran all of last nights updates, and most of todays so far, and it just broke my compiz

edit wait there, just ran the update manager again, now i have 55 new updates :s

edit, installed the updates, reboot, compiz is still dead here for me atleast. Try and enable the effects, Appearence Preferences, locks up have to force quit it :( oh and the updates, had added like 30seconds to my boot time :'(

---

### Post by hsoulen on 2010-04-09
Folks,

If you borked your Lucid Compiz with a partial upgrade and have since fixed your repositories (see earlier in the thread) and have then re-installed compiz through synaptic but still cannot re-enable desktop effects, try re-installing your proprietary graphics driver.

Can't speak for AMD/Intel etc. but Nvidia 195 driver re-install worked for me. Back to my lovely "wobble".

Hope this helps...

Hank

---

### Post by repawn on 2010-04-09
This mornings updates have resolved the problem for me.
 
The only odd thing I have now is that the Indicator Applet Session no longer has the logged in user name listed (the place where you show if you are available, busy etc.. Anyone else have this - I just have the power button?

---

### Post by manoriax on 2010-04-09
Still no working compiz here. But patience is my friend.

---

### Post by sports fan Matt on 2010-04-09
Just getting around to updating..will post my findings in a few.

---

### Post by sports fan Matt on 2010-04-09
Only Issue with Compiz was my settings dialog box after I re enabled them froze up.

---

### Post by sonicb00m on 2010-04-09
seems the package name changed from gnome-compiz to compiz-gnome.


sudo apt-get install compiz-gnome 

set it all right for me.

---

### Post by manoriax on 2010-04-09
> Use 'apt-get autoremove' to remove them.
Suggested packages:
  gnome-themes
The following packages will be REMOVED:
  metacity ubuntu-desktop
The following NEW packages will be installed:
  compiz-gnome
0 upgraded, 1 newly installed, 2 to remove and 0 not upgraded.
Need to get 110kB of archives.
After this operation, 246kB disk space will be freed.
Do you want to continue [Y/n]? 


It wants to remove metacity and ubuntu-desktop; I think this is kind of bad, isn't it? :D

---

### Post by 23meg on 2010-04-09
> **Half-Left said:**
> I think there is a flaw here. Partial upgrades should 'never' be offered in the first place.

I'm all for testing but bring up a messages in the UI saying such things and then in real terms saying it's dangerous is just bad management.

They're never offered in stable releases, and it's reasonable to expect people who test the development branch to be knowledgeable about [the underlying reasons that cause the situation]("http://ubuntuforums.org/showthread.php?t=1343434"), but [I agree that Update Manager could benefit from better design when dealing with those]("http://ubuntuforums.org/showpost.php?p=8146677&postcount=128") in any case.

---

### Post by Xorlathor on 2010-04-09
Same problem here - I stupidly accepted to the partial upgrade, and it apparently deleted compiz-gnome. I'm installing it again via:

```
sudo apt-get install compiz-gnome
```

Hopefully it'll fix things.

---

### Post by Xorlathor on 2010-04-09
> **repawn said:**
>  Anyway, lesson learned for me - no more partial upgrades. 

Haha same here - I'm not making this same mistake ever again. I'm learning this lesson the hard way, but hey, at least I'm learning it.:P

---

### Post by The Punisher on 2010-04-09
compiz-kde doesn't work since the KDE 4.4 release, even on Kubuntu 9.10
On compiz.org there is a patch since february but nobody implemented It yet :(

---

### Post by Uncle Spellbinder on 2010-04-09
Haven't updated in 3 days. 156 updates waiting, no partials. I'll see what happens now.....

---

### Post by Xorlathor on 2010-04-09
Kay, just installed the recent updates and everything's fixed compiz-wise now. You have to check the boxes on all compiz plugins you used via the "CompizConfig Settings Manger," but the settings are all the same, so you don't have to tweak everything all over again.

---

### Post by manoriax on 2010-04-09
I'm updating right now. Hopefully things are going correctly afterwards.

---

### Post by Uncle Spellbinder on 2010-04-09
Fully updated, all is *perfect*.

---

### Post by manoriax on 2010-04-09
Same here.

---

### Post by wilee-nilee on 2010-04-09
Same here all installed no problem, and I loaded the daily today on a thumb boots like it should.

---

### Post by The Recorder on 2010-04-10
Discovered what my problem was.  Compiz would not start with the dual-monitor, 2048x768 setup I had.  When I changed to only one screen (monitor), compiz worked perfectly.

Now, if I can only discover why it won't handle a dual-monitor setup that it handled before the compiz updates.  Odd thing is that the compiz script, "compiz-check", done under the dual-monitor setup, returns the following:

*************

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV410 [Radeon X700 (PCIE)]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

*************

Anyone have any ideas/suggestions?

---

### Post by elementxyz on 2010-04-10
everything fine here too. But had to reinstall compiz-gnome.

---

### Post by rpi+ on 2010-04-10
I had similar problems, too.

I updated now again and compiz worked, but I was not able to configure it.

Installlation of the package [FONT=Courier New]"compizconfig-settings-manager"[/FONT] was necessary, now everything works fine!

rpi.

---

### Post by t.rei on 2010-04-10
Works here again, too. However the gtk-window-decorator is not responding to the gnome-appearance-properties dialog anymore. 

I'll see how to configure it manually and hope thats another fix to come.


*update*

After going to:
gconf-editor
apps -> gwd

and unchecking and rechecking the "use_metacity_theme" checkbox, things are back to wonderfull.

---

