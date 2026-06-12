---
title: "Upgrade from/to LTS problems, crashes, apt errors and power management"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by Bugs318 on 2010-05-17
I have been using 8.04 since it's release (my first committed Linux usage) and just performed my first laptop upgrade to 10.04 with some (fairly) disastrous results.  There are several problems leading me to several questions.  I will note these shortly, but aside from individual fixes for each of the problems I am asking for any thoughts on the following if possible as well.

1) Can each of these problems be fixed on their own or would I be best suited to either return my system to its previous state (through Remastersys) and upgrade via synaptic again?  Or would I be better off saving my data, reformatting and doing a clean install?  Otherwise, should I put debian on my laptop (where I need the purportedly improved stability) while keeping ubuntu on the desktop?  Is debian that much more stable as often mentioned?

2) If I do either a clean install or a debian install, does my home folder remain intact (on a separate partition, as it is)?

Problems:

1) Despite power management settings that don't ask it to do this, my system now locks after 10 minutes of inactivity (whether on battery or not) and after 30 minutes either locks up completely (necessitating hard power down/reboot) or suspends and locks up upon an unlocking login.  It also seems to lock up with very few programs running, far fewer than ever caused problems before.

2) Update Manager and apt-get upgrade offer me the following (extremely lengthy) error messages without fail:


:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
39 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ubuntu-docs (10.04.3) ...
update-alternatives: error: alternative link /usr/share/ubuntu-artwork/home/index.html is already managed by firefox-homepage.before_restore_2008-09-28_19.19.27.528884.
dpkg: error processing ubuntu-docs (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up xterm (256-1ubuntu1) ...
update-alternatives: error: alternative link /usr/bin/x-terminal-emulator is already managed by x-terminal-emulator.before_restore_2008-09-28_19.19.27.528884.
dpkg: error processing xterm (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up gnome-terminal (2.29.6-0ubuntu5) ...
update-alternatives: error: alternative link /usr/bin/x-terminal-emulator is already managed by x-terminal-emulator.before_restore_2008-09-28_19.19.27.528884.
dpkg: error processing gnome-terminal (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up xfce4-terminal (0.4.3-1ubuntu2) ...
update-alternatives: error: alternative link /usr/bin/x-terminal-emulator is already managed by x-terminal-emulator.before_restore_2008-09-28_19.19.27.528884.
dpkg: error processing xfce4-terminal (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of transcode:
 transcode depends on xterm | x-terminal-emulator; however:
  Package xterm is not configured yet.
  Package x-terminal-emulator is not installed.
  Package xfce4-terminal which provides x-terminal-emulator is not configured yet.
  Package xterm which provides x-terminal-emulator is not configured yet.
  Package gnome-terminal which provides x-terminal-emulator is not configured yet.
dpkg: error processing transcode (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dvdrip:
 dvdrip depends on transcode (>= 2:1.0.2-0.8); however:
  Package transcode is not configured yet.
dpkg: error processing dvdrip (--configure):
 dependency problems - leaving unconfigured
Setting up epiphany-browser (2.30.2-1ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            update-alternatives: error: alternative link /usr/bin/x-www-browser is already managed by x-www-browser.before_restore_2008-09-28_19.19.27.528884.
dpkg: error processing epiphany-browser (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up firefox (3.6.3+nobinonly-0ubuntu4) ...
update-alternatives: error: alternative link /usr/bin/x-www-browser is already managed by x-www-browser.before_restore_2008-09-28_19.19.27.528884.
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox (= 3.6.3+nobinonly-0ubuntu4); however:
  Package firefox is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-gnome-support:
 firefox-3.0-gnome-support depends on firefox-gnome-support; however:
  Package firefox-gnome-support is not configured yet.
dpkg: error processing firefox-3.0-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.5-gnome-support:
 firefox-3.5-gnome-support depends on firefox-gnome-No apport report written because MaxReports is reached already
                                                                                                                  No apport report written because MaxReports is reached already
                   No apport report written because MaxReports is reached already
                                                                                 No apport report written because MaxReports is reached already
                                                                                                                                               support; however:
  Package firefox-gnome-support is not configured yet.
dpkg: error processing firefox-3.5-gnome-support (--configure):
 dependency problems - leaving unconfigured
Setting up metacity (1:2.30.1-0ubuntu1) ...
update-alternatives: error: alternative link /usr/bin/x-window-manager is already managed by x-window-manager.before_restore_2008-09-28_19.19.27.528884.
dpkg: error processing metacity (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up gnome-session (2.30.0-0ubuntu1) ...
update-alternatives: error: alternative link /usr/bin/x-session-manager is already managed by x-session-manager.before_restore_2008-09-28_19.19.27.528884.
dpkg: error processing gnome-session (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up ibus (1.2.0.20091215-1ubuntu4) ...
update-alternatives: error: alternative link /etc/X11/xinit/xinput.d/ja_JP is already managed by xinput-ja_JP.before_restore_2008-09-28_19.19.27.528884.
dpkg: error processing ibus (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ibus-m17n:
 ibus-m17n depends on ibus (>= 1.2); however:
  Package ibus is not configured yet.
dpkg: error processing ibus-m17n (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ibus-table:
 ibus-table depends on ibus (>= 1.2); however:
  Package ibus is not configured yet.
dpkg: error processing ibus-table (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Setting up im-switch (1.19) ...
update-alternatives: error: alternative link /etc/X11/xinit/xinput.d/all_ALL is already managed by xinput-all_ALL.before_restore_2008-09-28_19.19.27.528884.
dpkg: error processing im-switch (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up kdebase-workspace-bin (4:4.4.2-0ubuntu14) ...
update-alternatives: error: alternative link /usr/bin/x-session-manager is already managed by x-session-manager.before_restore_2008-09-28_19.19.27.528884.
dpkg: error processing kdebase-workspace-bin (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kpackagekit:
 kpackagekit depends on kdebase-workspace-bin; however:
  Package kdebase-workspace-bin is not configured yet.
dpkg: error processing kpackagekit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kubuntu-debug-installer:
 kubuntu-debug-installer depends on kpackagekit; however:
  Package kpackagekit is not configured yet.
No apport report written because MaxReports is reached already
                                                              dpkg: error processing kubuntu-debug-installer (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kubuntu-notification-helper:
 kubuntu-notification-helper depends on konsole | x-terminal-emulator; however:
  Package konsole is not installed.
  Package x-terminal-emulator is not installed.
  Package xfce4-terminal which provides x-terminal-emulator is not configured yet.
  Package xterm which provides x-terminal-emulator is not configured yet.
  Package gnome-terminal which provides x-terminal-emulator is not configured yet.
dpkg: error processing kubuntu-notification-helper (--configure):
 dependency problems - leaving unconfigured
Setting up scim (1.4.9-2) ...
No apport report written because MaxReports is reached already
                                                              update-alternatives: error: alternative link /etc/X11/xinit/xinput.d/ja_JP is already managed by xinput-ja_JP.before_restore_2008-09-28_19.19.27.528884.
dpkg: error processing scim (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of scim-bridge-agent:
 scim-bridge-agent depends on scim; however:
  Package scim is not configured yet.
dpkg: error processing scim-bridge-agent (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of scim-bridge-client-gtk:
 scim-bridge-client-gtk depends on scim-bridge-agent; however:
  Package scim-bridge-agent is not configured yet.
dpkg: error processing scim-bridge-client-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of scim-bridge-client-qt:
 scim-bridge-client-qt depends on scim-bridge-agent; however:
  Package scim-bridge-agent is not configured yet.
dpNo apport report written because MaxReports is reached already
                                                                No apport report written because MaxReports is reached already
                                                                                                                              No apport report written because MaxReports is reached already
                               No apport report written because MaxReports is reached already
                                                                                             No apport report written because MaxReports is reached already
                                                                                                                                                           No apport report written because MaxReports is reached already
                                                            kg: error processing scim-bridge-client-qt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of scim-gtk2-immodule:
 scim-gtk2-immodule depends on scim; however:
  Package scim is not configured yet.
dpkg: error processing scim-gtk2-immodule (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of scim-modules-table:
 scim-modules-table depends on scim; however:
  Package scim is not configured yet.
dpkg: error processing scim-modules-table (--configure):
 dependency problems - leaving unconfigured
Setting up skim (1.4.5-4ubuntu5) ...
update-alternatives: error: alternative link /etc/X11/xinit/xinput.d/all_ALL is already managed by xinput-all_ALL.before_restore_2008-09-28_19.19.27.528884.
dpkg: error processing skim (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of scim-qtimm:
 scim-qtimm depends on scim | skim; however:
  Package scim is not configured yet.
  Package skim is not configured yet.
dpkg: error processing scim-qtimm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of scim-tables-additional:
 scim-tables-additional depends on scim-modules-table (>= 0.5.9-1); however:
  Package scim-modules-table is not configured yet.
dpkg: error processing scim-tables-additional (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            No apport report written because MaxReports is reached already
                             dpkg: dependency problems prevent configuration of xorg:
 xorg depends on xterm | x-terminal-emulator; however:
  Package xterm is not configured yet.
  Package x-terminal-emulator is not installed.
  Package xfce4-terminal which provides x-terminal-emulator is not configured yet.
  Package xterm which provides x-terminal-emulator is not configured yet.
  Package gnome-terminal which provides x-terminal-emulator is not configured yet.
dpkg: error processing xorg (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gnome-session; however:
  Package gnome-session is not configured yet.
 ubuntu-desktop depends on gnome-terminal; however:
  Package gnome-terminal is not configured yet.
 ubuntu-desktop depends on metacity; however:
  Package metacity is not configured yet.
 ubuntu-desktop depends on xorg; however:
  Package xorg is not configured yet.
 ubuntu-desktop depends on xterm; however:
  Package xterm is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up xfce4-session (4.6.1-1ubuntu3) ...
No apport report written because MaxReports is reached already
                                                              update-alternatives: error: alternative link /usr/bin/x-session-manager is already managed by x-session-manager.before_restore_2008-09-28_19.19.27.528884.
dpkg: error processing xfce4-session (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xfce4-utils:
 xfce4-utils depends on xterm | x-terminal-emulator; however:
  Package xterm is not configured yet.
  Package x-terminal-emulator is not installed.
  Package xfce4-terminal which provides x-terminal-emulator is not configured yet.
  Package xterm which provides x-terminal-emulator is not configured yet.
  Package gnome-terminal which provides x-terminal-emulator is not configured yet.
dpkg: error processing xfce4-utils (--configure):
 dependency problems - leaving unconfigured
Setting up xfwm4 (4.6.1-1ubuntu2) ...
No apport report written because MaxReports is reached already
                                                              update-alternatives: error: alternative link /usr/bin/x-window-manager is already managed by x-window-manager.before_restore_2008-09-28_19.19.27.528884.
dpkg: error processing xfwm4 (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xfwm4-themes:
 xfwm4-themes depends on xfwm4 (>= 4.6.0); however:
  Package xfwm4 is not configured yet.
dpkg: error processing xfwm4-themes (--configure):
 dependency problems - leaving unconfigured
Setting up xubuntu-docs (9.10.1) ...
No apport report written because MaxReports is reached already
                                                              update-alternatives: error: alternative link /usr/share/ubuntu-artwork/home/index.html is already managed by firefox-homepage.before_restore_2008-09-28_19.19.27.528884.
dpkg: error processing xubuntu-docs (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of epiphany-browser-dbg:
 epiphany-browser-dbg depends on epiphany-browser (= 2.30.2-1ubuntu1); however:
  Package epiphany-browser is not configured yet.
dpkg: error processing epiphany-browser-dbg (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gnome-dbg:
 gnome-dbg depends on epiphany-browser-dbg; however:
  Package epiphany-browser-dbg is not configured yet.
dpkg: error processing gnome-dbg (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Processing triggers for menu ...
Errors were encountered while processing:
 ubuntu-docs
 xterm
 gnome-terminal
 xfce4-terminal
 transcode
 dvdrip
 epiphany-browser
 firefox
 firefox-gnome-support
 firefox-3.0-gnome-support
 firefox-3.5-gnome-support
 metacity
 gnome-session
 ibus
 ibus-m17n
 ibus-table
 im-switch
 kdebase-workspace-bin
 kpackagekit
 kubuntu-debug-installer
 kubuntu-notification-helper
 scim
 scim-bridge-agent
 scim-bridge-client-gtk
 scim-bridge-client-qt
 scim-gtk2-immodule
 scim-modules-table
 skim
 scim-qtimm
 scim-tables-additional
 xorg
 ubuntu-desktop
 xfce4-session
 xfce4-utils
 xfwm4
 xfwm4-themes
 xubuntu-docs
 epiphany-browser-dbg
 gnome-dbg
E: Sub-process /usr/bin/dpkg returned an error code (1)



THANK YOU SO MUCH in advance, as though I wouldn't call myself a noob, it is my first live upgrade attempt and I am unsure of the best way to proceed!  Thanks!!!

---

### Post by Bugs318 on 2010-05-17
Don't feel like you have to address everything to respond, I know there is a lot there, but if you can respond to any of these questions or help resolve any of these issues that will have been a huge help and step in the right direction!

---

### Post by Bugs318 on 2010-05-17
I have also now noticed that Evolution mail now crashes every time I send a message (though the message is sent, I must also reopen the program afterwards).

---

### Post by Bugs318 on 2010-05-17
Now, tonight, while in use the system simply turned off.  Not shut down, not locked up, but flat out turned off.  I pushed the power button and it rebooted fine and checked the temperature and found no problems.

Does anybody have advice or any ideas on what to check or try for any of these problems?  I keep searching to no avail and am grasping at straws here.

---

### Post by pradeepthundiyil on 2010-05-17
Hi,

Its working perfect.. My issue was with my hard disk..

---

### Post by Bugs318 on 2010-05-20
I have found a solution to the crashing:

It seems the upgrade somehow installed kacpi (even though I am not running KDE), and when I kill that process it no longer crashes, though it still locks the system even when my power management settings say to do otherwise.  Help on this would be useful.

As far as the apt-errors go, if I remove the packages the errors seem to go away.  Does anyone know if this would be a major problem?

---

