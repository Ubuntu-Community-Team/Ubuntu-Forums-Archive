---
title: "cannot start gdm frontend or gnome, have tried everything..."
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by darkenemy on 2008-10-12
my fronted gdm and gnome wont seem to start.  by this i mean, when i log in, (i have the ubuntu studio theme installed) i can see my background and the mouse only.  there are no panels and i cannot right click with any luck.
i figured out that if i hit the print screen key on my keyboard it will pull up the dialogue asking where i want to save the screenshot, i then click the help key, and click around until i find something that takes me to firefox, and that all works fine.  i usually run compiz, but the lack of emerald and the lack of effects leads me to believe i am in metacity currently.

i have tried the following commands to no luck

sudo dpkg --congiure -a
sudo apt-get -f install
dpkg-reconfigure xserver-xorg
dpkg-reconfigure xserver-xorg -phigh
startx
chmod a-x /usr/bin/compiz
gksu -D usr/bin/jockey-gtk

i also tried the running the "top" command and killing processes because i have one zombie process, although i dont know what it is.

i would post some of the outputs of these commands, but i cant open the terminal except for the ctrl+alt+F(x) commands, and i dont know how to paste from there to here....

any help would be much appreciated, i have almost fixed this problem it seems, which by the way happened after a recent upgrade.

---

### Post by darkenemy on 2008-10-12
I figured out how to open a terminal by similar processes as described above!

here is the output of sudo apt-get upgrade
```

hardy@hardy-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gstreamer0.10-plugins-good
The following packages will be upgraded:
  icedtea6-plugin ifupdown openjdk-6-jre openjdk-6-jre-headless
  openjdk-6-jre-lib
5 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
32 not fully installed or removed.
Need to get 27.5MB of archives.
After this operation, 4096B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com intrepid/main openjdk-6-jre-lib 6b12~pre2-0ubuntu2 [4720kB]
Get:2 http://us.archive.ubuntu.com intrepid/main openjdk-6-jre-headless 6b12~pre2-0ubuntu2 [22.4MB]
Get:3 http://us.archive.ubuntu.com intrepid/universe icedtea6-plugin 6b12~pre2-0ubuntu2 [85.9kB]
Get:4 http://us.archive.ubuntu.com intrepid/main openjdk-6-jre 6b12~pre2-0ubuntu2 [229kB]
Get:5 http://us.archive.ubuntu.com intrepid/main ifupdown 0.6.8ubuntu11 [58.9kB]
Fetched 27.5MB in 47s (580kB/s)                                                
Preconfiguring packages ...
(Reading database ... 183293 files and directories currently installed.)
Preparing to replace openjdk-6-jre-lib 6b12~pre2-0ubuntu1 (using .../openjdk-6-jre-lib_6b12~pre2-0ubuntu2_all.deb) ...
Unpacking replacement openjdk-6-jre-lib ...
Preparing to replace openjdk-6-jre-headless 6b12~pre2-0ubuntu1 (using .../openjdk-6-jre-headless_6b12~pre2-0ubuntu2_amd64.deb) ...
Unpacking replacement openjdk-6-jre-headless ...
Preparing to replace icedtea6-plugin 6b12~pre2-0ubuntu1 (using .../icedtea6-plugin_6b12~pre2-0ubuntu2_amd64.deb) ...
Unpacking replacement icedtea6-plugin ...
Preparing to replace openjdk-6-jre 6b12~pre2-0ubuntu1 (using .../openjdk-6-jre_6b12~pre2-0ubuntu2_amd64.deb) ...
Unpacking replacement openjdk-6-jre ...
Preparing to replace ifupdown 0.6.8ubuntu10 (using .../ifupdown_0.6.8ubuntu11_amd64.deb) ...
Unpacking replacement ifupdown ...
Processing triggers for man-db ...
Setting up rarian-compat (0.8.1-1ubuntu1) ...
update-xmlcatalog: error: entity already registered
dpkg: error processing rarian-compat (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-applets-data:
 gnome-applets-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-applets-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of capplets-data:
 capplets-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing capplets-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (>= 1:2.24); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends on capplets-data (<< 1:2.25); however:
  Package capplets-data is not configured yet.
dpkg: error processing gnome-contNo apport report written because the error message indicates its a followup error from a previous failure.
                                                           No apport report written because the error message indicates its a followup error from a previous failure.
     No apport report written because MaxReports is reached already
                                                                   No apport report written because MaxReports is reached already
                                                 No apport report written because MaxReports is reached already
                               No apport report written because MaxReports is reached already
             No apport report written because MaxReports is reached already
                                                                           No apport report written because MaxReports is reached already
                                                         No apport report written because MaxReports is reached already
                                       No apport report written because MaxReports is reached already
                     rol-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-control-center (>= 1:2.22); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel-data:
 gnome-panel-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-panel-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (>= 1:2.24); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-panel-data (<< 1:2.25); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gnome-applets-data (>= 2.24); however:
  Package gnome-applets-data is not configured yet.
 gnome-applets depends on gnome-applets-data (<< 2.25); however:
  Package gnome-applets-data is not configured yet.
 gnome-applets depends on gnome-panel (>= 2.13.4); however:
  Package gnome-panel is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-user-guide:
 gnome-user-guide depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-user-guide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-docs:
 ubuntu-docs depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
 ubuntu-docs depends on gnome-user-guide; however:
  Package gnome-user-guide is not configured yet.
dpkg: error processing ubuntu-docs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of synaptic:
 synaptic depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing synaptic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-app-install:
 gnome-app-install depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing gnome-app-install (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on gnome-app-install; however:
  Package gnome-app-install is not configured yet.
 apturl depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bug-buddy:
 bug-buddy depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing bug-buddy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fast-user-switch-applet:
 fast-user-switch-applet depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing fast-user-switch-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gNo apport report written because MaxReports is reached already
                                  No apport report written because MaxReports is reached already
                No apport report written because MaxReports is reached already
                                                                              No apport report written because MaxReports is reached already
                                                            No apport report written because MaxReports is reached already
                                          No apport report written because MaxReports is reached already
                        No apport report written because MaxReports is reached already
      No apport report written because MaxReports is reached already
                                                                    No apport report written because MaxReports is reached already
                                                  No apport report written because MaxReports is reached already
                                No apport report written because MaxReports is reached already
              No apport report written because MaxReports is reached already
                                                                            No apport report written because MaxReports is reached already
                                                          edit:
 gedit depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-system-monitor:
 gnome-system-monitor depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-system-monitor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-terminal:
 gnome-terminal depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-terminal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-utils:
 gnome-utils depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gucharmap:
 gucharmap depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gucharmap (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jockey-gtk:
 jockey-gtk depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing jockey-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector:
 language-selector depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing language-selector (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-data:
 nautilus-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing nautilus-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on nautilus-data (>= 1:2.24); however:
  Package nautilus-data is not configured yet.
 nautilus depends on nautilus-data (<< 1:2.25); however:
  Package nautilus-data is not configured yet.
 nautilus depends on gnome-control-center (>= 2.6); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-cd-burner:
 nautilus-cd-burner depends on nautilus; however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-cd-burner (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-share:
 nautilus-share depends on nautilus (>= 2.10); however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-share (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on apturl (>= 0.1.2ubuntu1); however:
  Package apturl is not configured yet.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends oNo apport report written because MaxReports is reached already
       No apport report written because MaxReports is reached already
                                                                     No apport report written because MaxReports is reached already
                                                   No apport report written because MaxReports is reached already
                                 No apport report written because MaxReports is reached already
               No apport report written because MaxReports is reached already
                                                                             No apport report written because MaxReports is reached already
                                                           No apport report written because MaxReports is reached already
                                         n synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of zenity:
 zenity depends on rarian-compat | scrollkeeper; however:
  Package rarian-compat is not configured yet.
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing zenity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on fast-user-switch-applet; however:
  Package fast-user-switch-applet is not configured yet.
 ubuntu-desktop depends on gedit; however:
  Package gedit is not configured yet.
 ubuntu-desktop depends on gnome-app-install; however:
  Package gnome-app-install is not configured yet.
 ubuntu-desktop depends on gnome-applets; however:
  Package gnome-applets is not configured yet.
 ubuntu-desktop depends on gnome-control-center; however:
  Package gnome-control-center is not configured yet.
 ubuntu-desktop depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
 ubuntu-desktop depends on gnome-session; however:
  Package gnome-session is not configured yet.
 ubuntu-desktop depends on gnome-system-monitor; however:
  Package gnome-system-monitor is not configured yet.
 ubuntu-desktop depends on gnome-terminal; however:
  Package gnome-terminal is not configured yet.
 ubuntu-desktop depends on gnome-utils; however:
  Package gnome-utils is not configured yet.
 ubuntu-desktop depends on gucharmap; however:
  Package gucharmap is not configured yet.
 ubuntu-desktop depends on language-selector; however:
  Package language-selector is not configured yet.
 ubuntu-desktop depends on nautilus; however:
  Package nautilus is not configured yet.
 ubuntu-desktop depends on nautilus-cd-burner; however:
  Package nautilus-cd-burner is not configured yet.
 ubuntu-desktop depends on rarian-compat; however:
  Package rarian-compat is not configured yet.
 ubuntu-desktop depends on software-properties-gtk; however:
  Package software-properties-gtk is not configured yet.
 ubuntu-desktop depends on synaptic; however:
  Package synaptic is not configured yet.
 ubuntu-desktop depends on update-manager; however:
  Package update-manager is not configured yet.
 ubuntu-desktop depends on update-notifier; however:
  Package update-notifier is not configured yet.
 ubuntu-desktop depends on zenity; however:
  Package zenity is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up ifupdown (0.6.8ubuntu11) ...

Setting up openjdk-6-jre-lib (6b12~pre2-0ubuntu2) ...
Setting up openjdk-6-jre-headless (6b12~pre2-0ubuntu2) ...
Installing new version of config file /etc/java-6-openjdk/fontconfig.properties.src ...
Installing new version of config file /etc/java-6-openjdk/fontconfig.bfc ...

Setting up openjdk-6-jre (6b12~pre2-0ubuntu2) ...
Using '/usr/lib/jvm/java-6-openjdk/jre/bin/javaws' to provide 'javaws'.
Using '/usr/lib/jvm/java-6-openjdk/jre/bin/pluginappletviewer' to provide 'pluginappletviewer'.
Using '/usr/lib/jvm/java-6-openjdk/jre/bin/policytool' to provide 'policytool'.

Setting up icedtea6-plugin (6b12~pre2-0ubuntu2) ...

Errors were encountered while processing:
 rarian-compat
 gnome-applets-data
 capplets-data
 gnome-control-center
 gnome-session
 gnome-panel-data
 gnome-panel
 gnome-applets
 gnome-user-guide
 ubuntu-docs
 synaptic
 gnome-app-install
 apturl
 bug-buddy
 fast-user-switch-applet
 gedit
 gnome-system-monitor
 gnome-terminal
 gnome-utils
 gucharmap
 jockey-gtk
 language-selector
 nautilus-data
 nautilus
 nautilus-cd-burner
 nautilus-share
 software-properties-gtk
 ubufox
 update-manager
 update-notifier
 zenity
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

```



adn for dpkg --configure -a
```

hardy@hardy-desktop:~$ sudo dpkg --configure -a
[sudo] password for hardy: 
Setting up rarian-compat (0.8.1-1ubuntu1) ...
update-xmlcatalog: error: entity already registered
dpkg: error processing rarian-compat (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of zenity:
 zenity depends on rarian-compat | scrollkeeper; however:
  Package rarian-compat is not configured yet.
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing zenity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-docs:
 ubuntu-docs depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing ubuntu-docs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-terminal:
 gnome-terminal depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-terminal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-user-guide:
 gnome-user-guide depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-user-guide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-system-monitor:
 gnome-system-monitor depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-system-monitor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of capplets-data:
 capplets-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing capplets-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-data:
 nautilus-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing nautilus-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (>= 1:2.24); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends on capplets-data (<< 1:2.25); however:
  Package capplets-data is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of synaptic:
 synaptic depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing synaptic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bug-buddy:
 bug-buddy depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing bug-buddy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-control-center (>= 1:2.22); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gucharmap:
 gucharmap depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gucharmap (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jockey-gtk:
 jockey-gtk depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing jockey-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on nautilus-data (>= 1:2.24); however:
  Package nautilus-data is not configured yet.
 nautilus depends on nautilus-data (<< 1:2.25); however:
  Package nautilus-data is not configured yet.
 nautilus depends on gnome-control-center (>= 2.6); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets-data:
 gnome-applets-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-applets-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gedit; however:
  Package gedit is not configured yet.
 ubuntu-desktop depends on gnome-control-center; however:
  Package gnome-control-center is not configured yet.
 ubuntu-desktop depends on gnome-session; however:
  Package gnome-session is not configured yet.
 ubuntu-desktop depends on gnome-system-monitor; however:
  Package gnome-system-monitor is not configured yet.
 ubuntu-desktop depends on gnome-terminal; however:
  Package gnome-terminal is not configured yet.
 ubuntu-desktop depends on gucharmap; however:
  Package gucharmap is not configured yet.
 ubuntu-desktop depends on nautilus; however:
  Package nautilus is not configured yet.
 ubuntu-desktop depends on rarian-compat; however:
  Package rarian-compat is not configured yet.
 ubuntu-desktop depends on synaptic; however:
  Package synaptic is not configured yet.
 ubuntu-desktop depends on zenity; however:
  Package zenity is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-utils:
 gnome-utils depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel-data:
 gnome-panel-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-panel-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gnome-applets-data (>= 2.24); however:
  Package gnome-applets-data is not configured yet.
 gnome-applets depends on gnome-applets-data (<< 2.25); however:
  Package gnome-applets-data is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing apturl (--config
hardy@hardy-desktop:~$ sudo dpkg --configure -a
[sudo] password for hardy: 
Setting up rarian-compat (0.8.1-1ubuntu1) ...
update-xmlcatalog: error: entity already registered
dpkg: error processing rarian-compat (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of zenity:
 zenity depends on rarian-compat | scrollkeeper; however:
  Package rarian-compat is not configured yet.
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing zenity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-docs:
 ubuntu-docs depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing ubuntu-docs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-terminal:
 gnome-terminal depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-terminal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-user-guide:
 gnome-user-guide depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-user-guide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-system-monitor:
 gnome-system-monitor depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-system-monitor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of capplets-data:
 capplets-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing capplets-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-data:
 nautilus-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing nautilus-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (>= 1:2.24); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends on capplets-data (<< 1:2.25); however:
  Package capplets-data is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of synaptic:
 synaptic depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing synaptic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bug-buddy:
 bug-buddy depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing bug-buddy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-control-center (>= 1:2.22); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gucharmap:
 gucharmap depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gucharmap (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jockey-gtk:
 jockey-gtk depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing jockey-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on nautilus-data (>= 1:2.24); however:
  Package nautilus-data is not configured yet.
 nautilus depends on nautilus-data (<< 1:2.25); however:
  Package nautilus-data is not configured yet.
 nautilus depends on gnome-control-center (>= 2.6); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets-data:
 gnome-applets-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-applets-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gedit; however:
  Package gedit is not configured yet.
 ubuntu-desktop depends on gnome-control-center; however:
  Package gnome-control-center is not configured yet.
 ubuntu-desktop depends on gnome-session; however:
  Package gnome-session is not configured yet.
 ubuntu-desktop depends on gnome-system-monitor; however:
  Package gnome-system-monitor is not configured yet.
 ubuntu-desktop depends on gnome-terminal; however:
  Package gnome-terminal is not configured yet.
 ubuntu-desktop depends on gucharmap; however:
  Package gucharmap is not configured yet.
 ubuntu-desktop depends on nautilus; however:
  Package nautilus is not configured yet.
 ubuntu-desktop depends on rarian-compat; however:
  Package rarian-compat is not configured yet.
 ubuntu-desktop depends on synaptic; however:
  Package synaptic is not configured yet.
 ubuntu-desktop depends on zenity; however:
  Package zenity is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-utils:
 gnome-utils depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel-data:
 gnome-panel-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-panel-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gnome-applets-data (>= 2.24); however:
  Package gnome-applets-data is not configured yet.
 gnome-applets depends on gnome-applets-data (<< 2.25); however:
  Package gnome-applets-data is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector:
 language-selector depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing language-selector (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-share:
 nautilus-share depends on nautilus (>= 2.10); however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-share (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-cd-burner:
 nautilus-cd-burner depends on nautilus; however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-cd-burner (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (>= 1:2.24); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-panel-data (<< 1:2.25); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-app-install:
 gnome-app-install depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing gnome-app-install (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fast-user-switch-applet:
 fast-user-switch-applet depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing fast-user-switch-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on apturl (>= 0.1.2ubuntu1); however:
  Package apturl is not configured yet.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rarian-compat
 zenity
 ubuntu-docs
 gnome-terminal
 gnome-user-guide
 gnome-system-monitor
 capplets-data
 gedit
 nautilus-data
 gnome-control-center
 synaptic
 bug-buddy
 gnome-session
 gucharmap
 jockey-gtk
 nautilus
 gnome-applets-data
 ubuntu-desktop
 gnome-utils
 gnome-panel-data
 gnome-applets
 update-manager
 software-properties-gtk
 apturl
 language-selector
 nautilus-share
 nautilus-cd-burner
 gnome-panel
 gnome-app-install
 fast-user-switch-applet
 update-notifier
 ubufox
ure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector:
 language-selector depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing language-selector (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-share:
 nautilus-share depends on nautilus (>= 2.10); however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-share (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-cd-burner:
 nautilus-cd-burner depends on nautilus; however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-cd-burner (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (>= 1:2.24); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-panel-data (<< 1:2.25); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-app-install:
 gnome-app-install depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing gnome-app-install (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fast-user-switch-applet:
 fast-user-switch-applet depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing fast-user-switch-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on apturl (>= 0.1.2ubuntu1); however:
  Package apturl is not configured yet.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rarian-compat
 zenity
 ubuntu-docs
 gnome-terminal
 gnome-user-guide
 gnome-system-monitor
 capplets-data
 gedit
 nautilus-data
 gnome-control-center
 synaptic
 bug-buddy
 gnome-session
 gucharmap
 jockey-gtk
 nautilus
 gnome-applets-data
 ubuntu-desktop
hardy@hardy-desktop:~$ sudo dpkg --configure -a
[sudo] password for hardy: 
Setting up rarian-compat (0.8.1-1ubuntu1) ...
update-xmlcatalog: error: entity already registered
dpkg: error processing rarian-compat (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of zenity:
 zenity depends on rarian-compat | scrollkeeper; however:
  Package rarian-compat is not configured yet.
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing zenity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-docs:
 ubuntu-docs depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing ubuntu-docs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-terminal:
 gnome-terminal depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-terminal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-user-guide:
 gnome-user-guide depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-user-guide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-system-monitor:
 gnome-system-monitor depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-system-monitor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of capplets-data:
 capplets-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing capplets-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-data:
 nautilus-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing nautilus-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (>= 1:2.24); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends on capplets-data (<< 1:2.25); however:
  Package capplets-data is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of synaptic:
 synaptic depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing synaptic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bug-buddy:
 bug-buddy depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing bug-buddy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-control-center (>= 1:2.22); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gucharmap:
 gucharmap depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gucharmap (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jockey-gtk:
 jockey-gtk depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing jockey-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on nautilus-data (>= 1:2.24); however:
  Package nautilus-data is not configured yet.
 nautilus depends on nautilus-data (<< 1:2.25); however:
  Package nautilus-data is not configured yet.
 nautilus depends on gnome-control-center (>= 2.6); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets-data:
 gnome-applets-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-applets-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gedit; however:
  Package gedit is not configured yet.
 ubuntu-desktop depends on gnome-control-center; however:
  Package gnome-control-center is not configured yet.
 ubuntu-desktop depends on gnome-session; however:
  Package gnome-session is not configured yet.
 ubuntu-desktop depends on gnome-system-monitor; however:
  Package gnome-system-monitor is not configured yet.
 ubuntu-desktop depends on gnome-terminal; however:
  Package gnome-terminal is not configured yet.
 ubuntu-desktop depends on gucharmap; however:
  Package gucharmap is not configured yet.
 ubuntu-desktop depends on nautilus; however:
  Package nautilus is not configured yet.
 ubuntu-desktop depends on rarian-compat; however:
  Package rarian-compat is not configured yet.
 ubuntu-desktop depends on synaptic; however:
  Package synaptic is not configured yet.
 ubuntu-desktop depends on zenity; however:
  Package zenity is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-utils:
 gnome-utils depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel-data:
 gnome-panel-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-panel-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gnome-applets-data (>= 2.24); however:
  Package gnome-applets-data is not configured yet.
 gnome-applets depends on gnome-applets-data (<< 2.25); however:
  Package gnome-applets-data is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector:
 language-selector depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing language-selector (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-share:
 nautilus-share depends on nautilus (>= 2.10); however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-share (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-cd-burner:
 nautilus-cd-burner depends on nautilus; however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-cd-burner (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (>= 1:2.24); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-panel-data (<< 1:2.25); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-app-install:
 gnome-app-install depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing gnome-app-install (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fast-user-switch-applet:
 fast-user-switch-applet depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing fast-user-switch-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on apturl (>= 0.1.2ubuntu1); however:
  Package apturl is not configured yet.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rarian-compat
 zenity
 ubuntu-docs
 gnome-terminal
 gnome-user-guide
 gnome-system-monitor
 capplets-data
 gedit
 nautilus-data
 gnome-control-center
 synaptic
 bug-buddy
 gnome-session
 gucharmap
 jockey-gtk
 nautilus
 gnome-applets-data
 ubuntu-desktop
 gnome-utils
 gnome-panel-data
 gnome-applets
 update-manager
 software-properties-gtk
 apturl
 language-selector
 nautilus-share
 nautilus-cd-burner
 gnome-panel
 gnome-app-install
 fast-user-switch-applet
 update-notifier
 ubufox

 gnome-utils
 gnome-panel-data
 gnome-applets
 update-manager
 software-properties-gtk
 apturl
 language-selector
 nautilus-share
 nautilus-cd-burner
 gnome-panel
 gnome-app-install
 fast-user-switch-applet
 update-notifier
 ubufox

```


startx outputs

[/CODE]
hardy@hardy-desktop:~$ startx


Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.



[/CODE]
and then it hangs

if anyone would like the output of more commands just ask.


for some reason now there are icons visible on the desktop and i can right click on the desktop now, but no panels still.

---

### Post by darkenemy on 2008-10-12
also, when i use synaptic, anytime i try to make a change i get this error message 

An Error Occured
```

E: rarian-compat: subprocess post-installation script returned error exit status 1
E: gnome-applets-data: dependency problems - leaving unconfigured
E: capplets-data: dependency problems - leaving unconfigured
E: gnome-control-center: dependency problems - leaving unconfigured
E: gnome-session: dependency problems - leaving unconfigured
E: gnome-panel-data: dependency problems - leaving unconfigured
E: gnome-panel: dependency problems - leaving unconfigured
E: gnome-applets: dependency problems - leaving unconfigured
E: gnome-user-guide: dependency problems - leaving unconfigured
E: ubuntu-docs: dependency problems - leaving unconfigured
E: synaptic: dependency problems - leaving unconfigured
E: gnome-app-install: dependency problems - leaving unconfigured
E: apturl: dependency problems - leaving unconfigured
E: bug-buddy: dependency problems - leaving unconfigured
E: fast-user-switch-applet: dependency problems - leaving unconfigured
E: gedit: dependency problems - leaving unconfigured
E: gnome-system-monitor: dependency problems - leaving unconfigured
E: gnome-terminal: dependency problems - leaving unconfigured
E: gnome-utils: dependency problems - leaving unconfigured
E: gucharmap: dependency problems - leaving unconfigured
E: language-selector: dependency problems - leaving unconfigured
E: nautilus-data: dependency problems - leaving unconfigured
E: nautilus: dependency problems - leaving unconfigured
E: nautilus-cd-burner: dependency problems - leaving unconfigured
E: nautilus-share: dependency problems - leaving unconfigured
E: software-properties-gtk: dependency problems - leaving unconfigured
E: ubufox: dependency problems - leaving unconfigured
E: update-manager: dependency problems - leaving unconfigured
E: update-notifier: dependency problems - leaving unconfigured
E: zenity: dependency problems - leaving unconfigured
E: ubuntu-desktop: dependency problems - leaving unconfigured


```

---

### Post by darkenemy on 2008-10-12
any help would be great, or else i have to reimage my drive, which would not be great, considering all the things that would have to be reconfigured...

---

### Post by overdrank on 2008-10-12
Moved to Intrepid Ibex Testing and Discussion

---

### Post by iponeverything on 2008-10-13
The key is backing out -- Look at the first few failures and back out those packages first then try the configure -a as you go along .. backing out packages as you go along until it takes off on its own.

The first two that I see are scrollkeeper, gnome-applets-data, and capplets-data.

Look in your archives directory for the previous version and install it with
dpkg -i <pre-version>

cd /var/cache/apt/archives
ls scrollkeeper*

---

### Post by yosemite610 on 2008-10-13
This is what helped me fix it:
[https://bugs.launchpad.net/ubuntu/+source/rarian/+bug/256131/comments/8](https://bugs.launchpad.net/ubuntu/+source/rarian/+bug/256131/comments/8)

Sorry I can't be more detailed, with all the other 'issues' I just don't remember any more specifics. 

Oh! Look! A chicken!   *wanders off*

---

### Post by jerrylamos on 2008-10-13
On Beta I had to 

sudo apt-get remove compiz
sudo apt-get remove compiz-core

to get Gnome desktop to load and run on this IBM Thinkpad R31 see bug 277344.

Compiz works fine (I'm dual booted) on Alpha 5 NOT UPDATED!!

Jerry

BTW, I'm all about applictions.  I use Firefox full screen, Office full screen, Picasa full screen, etc.  I can't figure out what Compiz would ever do for me except slow things down with add in extra in-line code.  Only time Compiz would come into play is when I have to do some command line stuff that the GUI windows won't do, and in doing command line stuff I'm not paying any attention to any "Compiz eye candy".

---

