---
title: "Software index is broken"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by baddison on 2008-05-05
Hi,
When I tried to run the update manager I get the following error: Software index is broken
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
When I run "sudo apt-get install -f" I get the following:
brett@brett-laptop:~$ sudo apt-get install -f
[sudo] password for brett:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  guile-1.8 lilypond-data libgail-gnome-module texlive-base texlive
  texlive-fonts-recommended pulseaudio texlive-common libpulse-mainloop-glib0
  texlive-base-bin guile-1.8-libs tetex-bin devhelp-common libgmp3c2
  libgbf-1-common texlive-latex-recommended libgnome-speech7 python-wxversion
  texlive-latex-base libqt0-ruby1.8 texlive-doc-base tex-common
  libglademm-2.4-1c2a python-orca-brlapi texinfo
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gnome-games
0 upgraded, 0 newly installed, 1 to remove and 12 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 4100kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 144600 files and directories currently installed.)
Removing gnome-games ...
dpkg: error processing gnome-games (--remove):
 cannot remove `/usr/games/sol': Permission denied
Errors were encountered while processing:
 gnome-games
E: Sub-process /usr/bin/dpkg returned an error code (1)
brett@brett-laptop:~$ 

This error is preventing me from installing new updates and upgrading to Ubuntu version 8.04.  If you can please help.
Thank you,
Brett

---

