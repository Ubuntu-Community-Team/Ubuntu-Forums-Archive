---
title: "&quot;An unresolvable problem occurred while calculating the upgrade.&quot;"
date: 2017-10-30
forum: Installation &amp; Upgrades
---

### Post by gauss4563 on 2017-10-30
Hi,

So I closed the terminal which prompted the sys upgrade right in the middle of the upgrade (while downloading pckgs) and now I get "An unresolvable problem occurred while calculating the upgrade." when trying to upgrade. 
I ran ```
grep Broken /var/log/dist-upgrade/apt.log
``` and got many lines like: ```
Broken ubuntu-session:amd64 Breaks on unity:...
``` and ```
Broken qml-module-ubuntu-settings-components...
```
What should I do in order to be able to upgrade now (from 17.04 to 17.10)?

I also tried a bunch of stuff from the links below which didn't work for me, unfortunately:
[https://askubuntu.com/questions/805175/unable-to-upgrade-from-14-04-to-16-04-could-not-calculate-the-upgrade-an-unres](https://askubuntu.com/questions/805175/unable-to-upgrade-from-14-04-to-16-04-could-not-calculate-the-upgrade-an-unres)
[https://askubuntu.com/questions/16494/upgrade-manager-wants-me-to-do-a-partial-upgrade](https://askubuntu.com/questions/16494/upgrade-manager-wants-me-to-do-a-partial-upgrade)

from the first link I ran the command and got many linkes of BROKEN things, but I don't know how to fix it. Do I need to do it one by one? Is there some quicker way to do it? How do I fix each one?

Thanks in advance!

---

### Post by ian-weisser on 2017-10-30
If you are sure that you were still *downloading* packages (before installing any of them), then try to run the release upgrade tool again.
```
do-release-upgrade
```
If there are errors, then please copy and paste the *entire* output here. Use [code] tags to retain the formatting of the output.

If, upon reflection, you believe that downloading may have completed and installing was underway, please say so. Different technique at that point.

---

### Post by gauss4563 on 2017-10-30
so this is what I get when trying to use ```
do-release-upgrade
```:

```
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [819 B]                                           
Get:2 Upgrade tool [1,255 kB]                                                  
Fetched 1,256 kB in 0s (0 B/s)                                                 
authenticate 'artful.tar.gz' against 'artful.tar.gz.gpg' 
extracting 'artful.tar.gz'
[sudo] password for cauchy: 


Reading cache


Checking package manager
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Ign http://archive.ubuntu.com/ubuntu trusty InRelease                          
Hit http://archive.ubuntu.com/ubuntu trusty-security InRelease                 
Hit http://archive.ubuntu.com/ubuntu trusty-updates InRelease                  
Hit http://archive.ubuntu.com/ubuntu trusty Release                            
Fetched 0 B in 0s (0 B/s)                                                      
Reading package lists... Done    
Building dependency tree          
Reading state information... Done


Updating repository information


Third party sources disabled 


Some third party entries in your sources.list were disabled. You can 
re-enable them after the upgrade with the 'software-properties' tool 
or your package manager. 


To continue please press [ENTER]


Hit http://archive.ubuntu.com/ubuntu artful InRelease                          
Fetched 0 B in 0s (0 B/s)                                                      


Checking package manager
Reading package lists... Done    
Building dependency tree          
Reading state information... Done


Calculating the changes


Calculating the changes


Could not calculate the upgrade 


An unresolvable problem occurred while calculating the upgrade. 


This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 


If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. 




Restoring original system state


Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done

```



Besides that, the output for ```
[COLOR=#111111][FONT=Consolas]grep Broken /var/log/dist-upgrade/apt.log[/FONT][/COLOR]
``` is: 
```
Broken adwaita-icon-theme:amd64 Breaks on adwaita-icon-theme-full:amd64 < 3.24.0-0ubuntu1 @ii mK Ib > (< 3.26.0-0ubuntu2)
Broken libgstreamer1.0-0:amd64 Breaks on gstreamer1.0-plugins-bad:amd64 < 1.10.4-1ubuntu1 @ii mK > (< 1.11.1)
Broken libqt5qml5:amd64 Depends on qtbase-abi-5-7-1:amd64 < none @un H >
Broken libqt5quick5:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.7.1)
Broken texlive-base:amd64 Conflicts on prosper:amd64 < 1.00.4+cvs.2007.05.01-4.1 @ii mK > (< 2017.20170628)
Broken texlive-base:amd64 Conflicts on texlive-extra-utils:amd64 < 2016.20170123-5 @ii mK > (< 2017.20170628)
Broken texlive-base:amd64 Conflicts on texlive-font-utils:amd64 < 2016.20170123-5 @ii mK > (< 2017.20170628)
Broken texlive-base:amd64 Conflicts on texlive-fonts-recommended:amd64 < 2016.20170123-5 @ii mK > (< 2017.20170628)
Broken texlive-base:amd64 Conflicts on texlive-generic-extra:amd64 < 2016.20170123-5 @ii mK > (< 2017.20170628)
Broken texlive-base:amd64 Conflicts on texlive-generic-recommended:amd64 < 2016.20170123-5 @ii mK > (< 2017.20170628)
Broken texlive-base:amd64 Conflicts on texlive-latex-extra:amd64 < 2016.20170123-5 @ii mK > (< 2017.20170628)
Broken texlive-base:amd64 Conflicts on texlive-latex-extra-doc:amd64 < 2016.20170123-5 @ii mK > (< 2017.20170628)
Broken texlive-base:amd64 Conflicts on texlive-pictures:amd64 < 2016.20170123-5 @ii mK > (< 2017.20170628)
Broken texlive-base:amd64 Conflicts on texlive-pstricks:amd64 < 2016.20170123-5 @ii mK > (< 2017.20170628)
Broken texlive-base:amd64 Conflicts on texlive-pstricks-doc:amd64 < 2016.20170123-5 @ii mK > (< 2017.20170628)
Broken texlive-base:amd64 Conflicts on texlive-science:amd64 < 2016.20170123-5 @ii mK > (< 2017.20170628)
Broken texlive-base:amd64 Conflicts on texlive-science-doc:amd64 < 2016.20170123-5 @ii mK > (< 2017.20170628)
Broken libreoffice-core:amd64 Breaks on libreoffice-gtk2:amd64 < 1:5.3.1-0ubuntu2 @ii mK Ib > (< 1:5.4.1-0ubuntu1)
Broken qml-module-qtquick2:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken gnome-settings-daemon:amd64 Breaks on gnome-session:amd64 < 3.24.0-0ubuntu1 @ii mK Ib > (< 3.25.4)
Broken qml-module-ubuntu-components:amd64 Depends on qml-module-qtquick2:amd64 < 5.7.1-1ubuntu1~7 @ii mR >
Broken qml-module-qtquick-window2:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken libsane1:amd64 Breaks on libsane:amd64 < 1.0.25+git20150528-1ubuntu4 @ii mK Ib > (< 1.0.27-1)
Broken ubuntu-system-settings:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken qml-module-qtquick-layouts:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.1.0)
Broken gnome-control-center-faces:amd64 Conflicts on unity-control-center-faces:amd64 < 15.04.0+17.04.20170402.6-0ubuntu1 @ii mK >
Broken evolution-data-server:amd64 Breaks on evolution-data-server-online-accounts:amd64 < 3.22.7-0ubuntu1 @ii mK Ib > (< 3.24.2-0ubuntu2~)
Broken libubuntugestures5:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken qml-module-ubuntu-performancemetrics:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken qtdeclarative5-unity-action-plugin:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken libubuntumetrics5:amd64 Depends on libqt5quick5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.4.0)
Broken libubuntumetrics5:amd64 Depends on libqt5quick5-gles:amd64 < none @un H > (>= 5.4.0)
Broken libubuntutoolkit5:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.6.0~beta)
Broken xserver-xorg:amd64 Breaks on xdiagnose:amd64 < 3.8.5 @ii mK > (< 3.8.8)
Broken qml-module-qtfeedback:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken qml-module-qtgraphicaleffects:amd64 Depends on qml-module-qtquick-window2:amd64 < 5.7.1-1ubuntu1~7 @ii mR >
Broken qml-module-ubuntu-components-labs:amd64 Depends on libubuntugestures5:amd64 < 1.3.2190+17.04.20170327 @ii mR > (= 1.3.2190+17.04.20170327)
Broken libqt5multimedia5:amd64 Depends on qtbase-abi-5-7-1:amd64 < none @un H >
Broken ubuntu-system-settings-online-accounts:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken qml-module-qtsysteminfo:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken qtdeclarative5-ubuntu-content1:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken libgjs0g:amd64 Conflicts on libgjs0f:amd64 < 1.48.3-0ubuntu0.1 @ii mK >
Broken liboxideqt-qmlplugin:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken ubuntu-session:amd64 Breaks on hud:amd64 < 14.10+17.04.20170106.1-0ubuntu1 @ii mK > (< 14.10+17.10.20170619)
Broken ubuntu-session:amd64 Breaks on unity:amd64 < 7.5.0+17.04.20170407.1-0ubuntu1 @ii mK NPb IPb > (< 7.5.0+17.10.20170619)
Broken ubuntu-session:amd64 Breaks on unity-settings-daemon:amd64 < 15.04.1+17.04.20170418-0ubuntu1 @ii mK NPb IPb > (< 15.04.1+17.04.20170619)
Broken qtdeclarative5-ubuntu-ui-extras0.2:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken qtdeclarative5-gsettings1.0:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken qml-module-biometryd:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken qml-module-qt-labs-folderlistmodel:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken gnome-software:amd64 Conflicts on sessioninstaller:amd64 < 0.20+bzr150-0ubuntu4.1 @ii mK >
Broken qmenumodel-qml:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken qml-module-qtmultimedia:amd64 Depends on qml-module-qtquick2:amd64 < 5.7.1-1ubuntu1~7 @ii mR >
Broken qtdeclarative5-qtquick2-plugin:amd64 Depends on qml-module-qtquick2:amd64 < 5.7.1-1ubuntu1~7 @ii mR >
Broken ubuntu-keyboard-data:amd64 Depends on qml-module-ubuntu-components:amd64 < 1.3.2190+17.04.20170327 @ii mR >
Broken qml-module-ubuntu-onlineaccounts:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken qml-module-ubuntu-connectivity:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken libqt5contacts5:amd64 Depends on qtbase-abi-5-7-1:amd64 < none @un H >
Broken qml-module-ofono:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 Depends on qml-module-ubuntu-components:amd64 < 1.3.2190+17.04.20170327 @ii mR >
Broken qml-module-ubuntu-onlineaccounts-client:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken qml-module-ubuntu-onlineaccounts2:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.1.0)
Broken libqt5feedback5:amd64 Depends on libqt5multimedia5:amd64 < 5.7.1~20161021-2ubuntu1~3 @ii mR > (>= 5.0.2)
Broken qml-module-ubuntu-layouts:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.6.0~beta)
Broken qml-module-ubuntu-test:amd64 Depends on qml-module-ubuntu-components:amd64 < 1.3.2190+17.04.20170327 @ii mR >
Broken liboxideqtquick0:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.1.0)
Broken libgslcblas0:amd64 Conflicts on libgsl2:amd64 < 2.3+dfsg-1 @ii mK >
Broken qml-module-qtqml-models2:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.1.0)
Broken libqt5xmlpatterns5:amd64 Depends on qtbase-abi-5-7-1:amd64 < none @un H >
Broken qml-module-qttest:amd64 Depends on qml-module-qtquick2:amd64 < 5.7.1-1ubuntu1~7 @ii mR >
Broken qtubuntu-desktop:amd64 Conflicts on qtubuntu-appmenutheme:amd64 < 0.64+17.04.20170404-0ubuntu1 @ii mK Ib >
Broken qml-module-qt-labs-settings:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken unity-greeter:amd64 Depends on unity-settings-daemon:amd64 < 15.04.1+17.04.20170418-0ubuntu1 @ii mR NPb > (>= 15.04.1+16.10.20160615-0ubuntu1)
Broken libqt5quicktest5:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.5.0)
Broken qml-module-ubuntu-web:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.1.0)
Broken kerneloops:amd64 Breaks on kerneloops-daemon:amd64 < 0.12+git20140509-2ubuntu1 @ii mK > (< 0.12+git20140509-6ubuntu1)
Broken ubuntu-web-launchers:amd64 Breaks on unity-asset-pool:amd64 < 0.8.24+15.04.20141217-0ubuntu2 @ii mK > (< 0.8.24+17.10.20170507)
Broken webbrowser-app:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.1.0)
Broken libqt5positioning5:amd64 Depends on qtbase-abi-5-7-1:amd64 < none @un H >
Broken url-dispatcher:amd64 Depends on qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 < 1.3.2190+17.04.20170327 @ii mR >
Broken qml-module-io-thp-pyotherside:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken libqt5versit5:amd64 Depends on libqt5contacts5:amd64 < 5.0~git20140515~29475884-0ubuntu23~3 @ii mR >
Broken libpurple0:amd64 Depends on perlapi-5.24.1:amd64 < none @un H >
Broken telephony-service:amd64 Depends on libqt5contacts5:amd64 < 5.0~git20140515~29475884-0ubuntu23~3 @ii mR >
Broken onboard:amd64 Depends on python3:amd64 < 3.5.3-1 -> 3.6.3-0ubuntu2 @ii umU > (< 3.6)
Broken libqt5organizer5:amd64 Depends on qtbase-abi-5-7-1:amd64 < none @un H >
Broken qtmir-desktop:amd64 Depends on libqt5quick5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.1.0)
Broken qtmir-desktop:amd64 Depends on libqt5quick5-gles:amd64 < none @un H > (>= 5.1.0)
Broken qtmir-desktop:amd64 Depends on qtbase-abi-5-7-1:amd64 < none @un H >
Broken qtdeclarative5-ubuntu-download-manager0.1:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken libhistoryservice0:amd64 Depends on libqt5contacts5:amd64 < 5.0~git20140515~29475884-0ubuntu23~3 @ii mR >
Broken qmlscene:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken content-hub:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken libqofono-qt5-0:amd64 Depends on libqt5xmlpatterns5:amd64 < 5.7.1~20161021-3build1~3 @ii mR > (>= 5.0.2)
Broken history-service:amd64 Depends on libhistoryservice0:amd64 < 0.1+17.04.20161130-0ubuntu1 @ii mR >
Broken ubuntu-terminal-app:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.1.0)
Broken libpurple-bin:amd64 Depends on libpurple0:amd64 < 1:2.12.0-1ubuntu1 @ii mR >
Broken qtdeclarative5-ubuntu-telephony0.1:amd64 Depends on telephony-service:amd64 < 0.1+17.04.20161213.1-0ubuntu1 @ii mR > (>= 0.1+17.04.20161213.1-0ubuntu1)
Broken ubuntu-printing-app:amd64 Depends on qml-module-qtquick2:amd64 < 5.7.1-1ubuntu1~7 @ii mR >
Broken qml-module-ubuntu-settings-components:amd64 Depends on qml-module-biometryd:amd64 < 0.0.1+16.10.20160922.3-0ubuntu2 @ii mR >
Broken qml-module-qmltermwidget1.0:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken qml-module-pamauthentication0.1:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken unity-webapps-qml:amd64 Depends on liboxideqt-qmlplugin:amd64 < 1.21.5-0ubuntu1 @ii mR > (>= 1.3.0)
Broken unity-webapps-qml:amd64 Depends on qml-module-qtwebkit:amd64 < none @un H >
Broken unity-webapps-qml:amd64 Depends on qtdeclarative5-qtquick2-plugin:amd64 < 5.7.1-1ubuntu1~7 @ii mR >
Broken libqt5multimedia5-plugins:amd64 Depends on libqt5multimedia5:amd64 < 5.7.1~20161021-2ubuntu1~3 @ii mR > (= 5.7.1~20161021-2ubuntu1~3)
Broken signon-ui-x11:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken libqt5multimediawidgets5:amd64 Depends on libqt5multimedia5:amd64 < 5.7.1~20161021-2ubuntu1~3 @ii mR > (>= 5.0.2)
Broken libqt5sensors5:amd64 Depends on qtbase-abi-5-7-1:amd64 < none @un H >
Broken libqt5webkit5:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.1.0)
Broken qml-module-qtqml-statemachine:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.7.1)
Broken qtdeclarative5-qtmir-plugin:amd64 Depends on qtmir-desktop:amd64 < 0.5.1+17.04.20170404-0ubuntu2 @ii mR > (= 0.5.1+17.04.20170404-0ubuntu2)
Broken qtdeclarative5-qtmir-plugin:amd64 Depends on qtmir-android:amd64 < none @un H > (= 0.5.1+17.04.20170404-0ubuntu2)
Broken qtdeclarative5-qtmir-plugin:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken libqgsttools-p1:amd64 Depends on libqt5multimedia5:amd64 < 5.7.1~20161021-2ubuntu1~3 @ii mR > (>= 5.4.0)
Broken url-dispatcher-tools:amd64 Depends on url-dispatcher:amd64 < 0.1+17.04.20170328-0ubuntu2 @ii mR > (= 0.1+17.04.20170328-0ubuntu2)
Broken libpango1.0-0:i386 Depends on libpango-1.0-0:i386 < 1.40.4-1 -> 1.40.12-1 @ii umU > (= 1.40.4-1)
Broken libpango1.0-0:amd64 Depends on libpango-1.0-0:amd64 < 1.40.4-1 -> 1.40.12-1 @ii umU > (= 1.40.4-1)
Broken unity8:amd64 Depends on qmenumodel-qml:amd64 < 0.2.12+17.04.20170404-0ubuntu1 @ii mR > (>= 0.2.11)
Broken gtk2-engines-pixbuf:amd64 Depends on libgtk2.0-0:amd64 < 2.24.31-1ubuntu1.1 -> 2.24.31-2ubuntu1 @ii umU > (= 2.24.31-1ubuntu1.1)
Broken qtdeclarative5-dev-tools:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.6.0~beta)
Broken qml-module-ubuntu-thumbnailer0.1:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken qtdeclarative5-unity-notifications-plugin:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken unity-greeter-session-broadcast:amd64 Depends on url-dispatcher-tools:amd64 < 0.1+17.04.20170328-0ubuntu2 @ii mR >
Broken qtdeclarative5-test-plugin:amd64 Depends on qml-module-qttest:amd64 < 5.7.1-1ubuntu1~7 @ii mR >
Broken onboard-data:amd64 Depends on onboard:amd64 < 1.4.1-0ubuntu1 @ii mR > (< 1.4.1-0ubuntu1.1)
Broken libqt5multimediaquick-p5:amd64 Depends on libqt5multimedia5:amd64 < 5.7.1~20161021-2ubuntu1~3 @ii mR > (>= 5.5.0)
Broken qtubuntu-print:amd64 Depends on content-hub:amd64 < 0.3+17.04.20170403-0ubuntu2 @ii mR >
Broken webapp-container:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken libusermetricsoutput1:amd64 Depends on libqt5xmlpatterns5:amd64 < 5.7.1~20161021-3build1~3 @ii mR > (>= 5.0.2)
Broken unity8-common:amd64 Depends on qml-module-qtquick-layouts:amd64 < 5.7.1-1ubuntu1~7 @ii mR >
Broken signon-ui:amd64 Depends on signon-ui-x11:amd64 < 0.17+17.04.20170320-0ubuntu1 @ii mR >
Broken signon-ui:amd64 Depends on ubuntu-system-settings-online-accounts:amd64 < 0.7+17.04.20170308.2-0ubuntu3 @ii mR > (>= 0.4)
Broken qml-module-qtquick-xmllistmodel:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.5.0)
Broken address-book-service:amd64 Depends on libqt5contacts5:amd64 < 5.0~git20140515~29475884-0ubuntu23~3 @ii mR >
Broken qtdeclarative5-accounts-plugin:amd64 Depends on qml-module-ubuntu-onlineaccounts:amd64 < 0.6+17.04.20170405-0ubuntu1 @ii mR >
Broken flashplugin-installer:amd64 Depends on libpango1.0-0:amd64 < 1.40.4-1 @ii mR >
Broken qtcontact5-galera:amd64 Depends on address-book-service:amd64 < 0.1.2+17.04.20161124.1-0ubuntu1 @ii mR > (= 0.1.2+17.04.20161124.1-0ubuntu1)
Broken unity8-private:amd64 Depends on qtdeclarative5-gsettings1.0:amd64 < 0.1+16.04.20160329-0ubuntu3~1 @ii mR >
Broken unity-plugin-scopes:amd64 Depends on libqt5positioning5:amd64 < 5.7.1-1ubuntu1~1 @ii mR > (>= 5.6.0)
Broken gnome-shell-extensions:amd64 Depends on gnome-shell:amd64 < 3.24.2-0ubuntu0.1 -> 3.26.1-0ubuntu4 @ii umU > (< 3.25)
Broken imagemagick-common:amd64 Depends on imagemagick-6-common:amd64 < 8:6.9.7.4+dfsg-3ubuntu1.2 -> 8:6.9.7.4+dfsg-16ubuntu2 @ii umU > (= 8:6.9.7.4+dfsg-3ubuntu1.2)
Broken g++-5:amd64 Depends on gcc-5-base:amd64 < 5.4.1-8ubuntu1 -> 5.5.0-1ubuntu1 @ii umU > (= 5.4.1-8ubuntu1)
Broken g++-6:amd64 Depends on gcc-6-base:amd64 < 6.3.0-12ubuntu2 -> 6.4.0-8ubuntu1 @ii umU > (= 6.3.0-12ubuntu2)
Broken acroread-bin:i386 Depends on libpango1.0-0:i386 < 1.40.4-1 @ii mR > (>= 1.14.0)
Broken checkbox-converged:amd64 Depends on qml-module-io-thp-pyotherside:amd64 < 1.4.0-2 @ii mR >
Broken libnss-resolve:amd64 Depends on systemd:amd64 < 232-21ubuntu7.1 -> 234-2ubuntu12 @ii umU > (= 232-21ubuntu7.1)
Broken unity8-desktop-session:amd64 Depends on qtmir-desktop:amd64 < 0.5.1+17.04.20170404-0ubuntu2 @ii mR >
Broken libreoffice-gtk:amd64 Depends on libreoffice-gtk2:amd64 < 1:5.3.1-0ubuntu2 @ii mR >
Broken ubuntu-core-launcher:amd64 Depends on snapd:amd64 < 2.27.5+17.04 -> 2.28.5+17.10 @ii umU > (= 2.27.5+17.04)
Broken telepathy-haze:amd64 Depends on libpurple0:amd64 < 1:2.12.0-1ubuntu1 @ii mR > (>= 1:2.7.0)
Broken pyotherside:amd64 Depends on qml-module-io-thp-pyotherside:amd64 < 1.4.0-2 @ii mR >
Broken gfortran-6:amd64 Depends on gcc-6-base:amd64 < 6.3.0-12ubuntu2 -> 6.4.0-8ubuntu1 @ii umU > (= 6.3.0-12ubuntu2)
Broken gnome-sushi:amd64 Depends on libgjs0-libmozjs-38-0:amd64 < none @un H >
Broken gfortran-5:amd64 Depends on gcc-5-base:amd64 < 5.4.1-8ubuntu1 -> 5.5.0-1ubuntu1 @ii umU > (= 5.4.1-8ubuntu1)
Broken libwebkit2gtk-4.0-37-gtk2:amd64 Depends on libwebkit2gtk-4.0-37:amd64 < 2.18.0-0ubuntu0.17.04.2 -> 2.18.0-2 @ii umU > (= 2.18.0-0ubuntu0.17.04.2)
Broken unity-control-center:amd64 Depends on unity-settings-daemon:amd64 < 15.04.1+17.04.20170418-0ubuntu1 @ii mR NPb >
Broken ubuntu-session:amd64 Breaks on unity-settings-daemon:amd64 < 15.04.1+17.04.20170418-0ubuntu1 @ii mK NPb IPb > (< 15.04.1+17.04.20170619)
Broken qtdeclarative5-ubuntu-settings-components:amd64 Depends on qml-module-ubuntu-settings-components:amd64 < 0.12+17.04.20170118-0ubuntu1 @ii mR >
Broken indicator-network:amd64 Depends on libqofono-qt5-0:amd64 < 0.90+16.10.20160901-0ubuntu1 @ii mR >
Broken liboxideqtcore0:amd64 Depends on libqt5feedback5:amd64 < 5.0~git20130529-0ubuntu15~1 @ii mR >
Broken liboxideqtcore0:amd64 Depends on libqt5positioning5:amd64 < 5.7.1-1ubuntu1~1 @ii mR > (>= 5.6.0)
Broken libqt5feedback5:amd64 Depends on libqt5multimedia5:amd64 < 5.7.1~20161021-2ubuntu1~3 @ii mR > (>= 5.0.2)
Broken unity-webapps-service:amd64 Depends on webapp-container:amd64 < 0.23+17.04.20170321-0ubuntu1 @ii mR >
Broken libqt5positioning5:amd64 Depends on qtbase-abi-5-7-1:amd64 < none @un H >
Broken libqofono-qt5-0:amd64 Depends on libqt5xmlpatterns5:amd64 < 5.7.1~20161021-3build1~3 @ii mR > (>= 5.0.2)
Broken qml-module-ubuntu-settings-components:amd64 Depends on qml-module-biometryd:amd64 < 0.0.1+16.10.20160922.3-0ubuntu2 @ii mR >
Broken webapp-container:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken unity-control-center:amd64 Depends on unity-settings-daemon:amd64 < 15.04.1+17.04.20170418-0ubuntu1 @ii mR NPb >
Broken ubuntu-session:amd64 Breaks on unity-settings-daemon:amd64 < 15.04.1+17.04.20170418-0ubuntu1 @ii mK NPb IPb > (< 15.04.1+17.04.20170619)
Broken qtdeclarative5-ubuntu-settings-components:amd64 Depends on qml-module-ubuntu-settings-components:amd64 < 0.12+17.04.20170118-0ubuntu1 @ii mR >
Broken indicator-network:amd64 Depends on libqofono-qt5-0:amd64 < 0.90+16.10.20160901-0ubuntu1 @ii mR >
Broken liboxideqtcore0:amd64 Depends on libqt5feedback5:amd64 < 5.0~git20130529-0ubuntu15~1 @ii mR >
Broken liboxideqtcore0:amd64 Depends on libqt5positioning5:amd64 < 5.7.1-1ubuntu1~1 @ii mR > (>= 5.6.0)
Broken libqt5feedback5:amd64 Depends on libqt5multimedia5:amd64 < 5.7.1~20161021-2ubuntu1~3 @ii mR > (>= 5.0.2)
Broken unity-webapps-service:amd64 Depends on webapp-container:amd64 < 0.23+17.04.20170321-0ubuntu1 @ii mR >
Broken libqt5positioning5:amd64 Depends on qtbase-abi-5-7-1:amd64 < none @un H >
Broken ubuntu-desktop:amd64 Depends on ubuntu-session:amd64 < 3.24.0-0ubuntu1 | 3.26.1-0ubuntu5 @ii umR >
Broken libqofono-qt5-0:amd64 Depends on libqt5xmlpatterns5:amd64 < 5.7.1~20161021-3build1~3 @ii mR > (>= 5.0.2)
Broken qml-module-ubuntu-settings-components:amd64 Depends on qml-module-biometryd:amd64 < 0.0.1+16.10.20160922.3-0ubuntu2 @ii mR >
Broken webapp-container:amd64 Depends on libqt5qml5:amd64 < 5.7.1-1ubuntu1~7 @ii mR > (>= 5.0.2)
Broken qtdeclarative5-ubuntu-settings-components:amd64 Depends on qml-module-ubuntu-settings-components:amd64 < 0.12+17.04.20170118-0ubuntu1 @ii mR >
Broken liboxideqtcore0:amd64 Depends on libqt5feedback5:amd64 < 5.0~git20130529-0ubuntu15~1 @ii mR >
Broken libqt5xmlpatterns5:amd64 Depends on qtbase-abi-5-7-1:amd64 < none @un H >
Broken unity-webapps-service:amd64 Depends on webapp-container:amd64 < 0.23+17.04.20170321-0ubuntu1 @ii mR >
Broken libqofono-qt5-0:amd64 Depends on libqt5xmlpatterns5:amd64 < 5.7.1~20161021-3build1~3 @ii mR > (>= 5.0.2)
Broken libunity-webapps0:amd64 Depends on unity-webapps-service:amd64 < 2.5.0~+16.04.20160201-0ubuntu2 @ii mR >
Broken unity-webapps-common:amd64 Depends on unity-webapps-service:amd64 < 2.5.0~+16.04.20160201-0ubuntu2 @ii mR > (>= 2.3.8-0ubuntu3)
Broken indicator-network:amd64 Depends on libqofono-qt5-0:amd64 < 0.90+16.10.20160901-0ubuntu1 @ii mR >
Broken unity-control-center:amd64 Depends on unity-settings-daemon:amd64 < 15.04.1+17.04.20170418-0ubuntu1 @ii gR NPb >
Broken ubuntu-session:amd64 Breaks on unity-settings-daemon:amd64 < 15.04.1+17.04.20170418-0ubuntu1 @ii gK NPb IPb > (< 15.04.1+17.04.20170619)
Broken account-plugin-google:amd64 Depends on unity-asset-pool:amd64 < 0.8.24+15.04.20141217-0ubuntu2 @ii gR > (> 0.8.24daily12.12.05-0ubuntu1)
Broken account-plugin-flickr:amd64 Depends on unity-asset-pool:amd64 < 0.8.24+15.04.20141217-0ubuntu2 @ii gR > (> 0.8.24daily12.12.05-0ubuntu1)
Broken account-plugin-facebook:amd64 Depends on unity-asset-pool:amd64 < 0.8.24+15.04.20141217-0ubuntu2 @ii gR > (> 0.8.24daily12.12.05-0ubuntu1)
Broken unity-control-center:amd64 Depends on unity-settings-daemon:amd64 < 15.04.1+17.04.20170418-0ubuntu1 @ii gR NPb >
Broken ubuntu-session:amd64 Breaks on unity-settings-daemon:amd64 < 15.04.1+17.04.20170418-0ubuntu1 @ii gK NPb IPb > (< 15.04.1+17.04.20170619)
Broken unity-scope-gdrive:amd64 Depends on account-plugin-google:amd64 < 0.13+17.04.20170314-0ubuntu1 @ii mR >
Broken unity-control-center:amd64 Depends on unity-settings-daemon:amd64 < 15.04.1+17.04.20170418-0ubuntu1 @ii gR NPb >
Broken ubuntu-session:amd64 Breaks on unity-settings-daemon:amd64 < 15.04.1+17.04.20170418-0ubuntu1 @ii gK NPb IPb > (< 15.04.1+17.04.20170619)
Broken ubuntu-session:amd64 Breaks on unity-settings-daemon:amd64 < 15.04.1+17.04.20170418-0ubuntu1 @ii gK NPb IPb > (< 15.04.1+17.04.20170619)
Broken ubuntu-desktop:amd64 Depends on ubuntu-session:amd64 < 3.24.0-0ubuntu1 | 3.26.1-0ubuntu5 @ii umR >
Broken ubuntu-session:amd64 Depends on gnome-session-bin:amd64 < 3.24.0-0ubuntu1 -> 3.26.1-0ubuntu5 @ii umU > (< 3.25)
Broken ubuntu-session:amd64 Depends on gnome-session-common:amd64 < 3.24.0-0ubuntu1 -> 3.26.1-0ubuntu5 @ii umU > (= 3.24.0-0ubuntu1)

```

---

### Post by ajgreeny on 2017-10-30
Upgrading from what to what, or was it a normal OS package upgrade, ie a **sudo apt upgrade** command?

---

### Post by gauss4563 on 2017-10-30
Upgrading from 17.04 to 17.10 from the update manager - the graphical updater.

---

### Post by ian-weisser on 2017-10-30
You seem to have non-Ubuntu software installed:
```
Broken libqt5xmlpatterns5:amd64 Depends on **qtbase-abi-5-7-1**:amd64 < none @un H >
```

qtbase-abi-5-7-1 is not an Ubuntu package. Figure out why you installed it, and uninstall ALL non-Ubuntu software.
Then try do-release-upgrade again.

---

### Post by gauss4563 on 2017-10-30
How do I remove all non-Ubuntu software?

Sorry for the newbie questions, but new to Linux. Will this work?
[https://askubuntu.com/questions/79665/keep-only-essential-packages](https://askubuntu.com/questions/79665/keep-only-essential-packages)

---

### Post by ian-weisser on 2017-10-30
While that link will technically work, I don't see how it will help your problem.

Here are a few ways:

1) Search your memory.
Recall everything you wanted to install or update that wasn't in the Ubuntu Repositories.
Everything that you added a PPA or some other non-Ubuntu source for.

2) Search your sources
Review all the files in /etc/apt/sources.list*
Exclude Ubuntu-provided repositories
Recall why you added that repo. Uninstall all software from that non-Ubuntu source, then disable the source.

3) Use apt
See what rocks this turns over. Please show us the complete output.
```
apt policy qtbase-abi-5-7-1
sudo apt --simulate remove qtbase-abi-5-7-1
```

---

### Post by gauss4563 on 2017-10-30
Seems like a clean install and reinstalling all the necessary apps will be easier. No?

---

### Post by ian-weisser on 2017-10-30
That's your decision, and a valid way to solve the problem.

However, you may cause the problem again.
It's almost never a mistake or error by the system. Package version conflicts are almost always a human-caused situation.

---

