---
title: "adobe flashplayer for ubuntu 8.04+ installation problem"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by bobmac on 2010-01-13
Folks,

I've been trying to install Adobe flashplayer 8.04+ for ubuntu from the Adobe site.

I seem to be able to download it ok and it drops the installation file on my desktop.

However, the instructions for the .deb file don't seem to work. These instructions are:

1.Click the download link to begin installation. If a dialog box appears, follow the instructions to save the installer to your desktop.
2.Save the .deb package to your desktop, and wait for it to download completely.
3.Double-click on the .deb package and follow the instructions to complete installation.
-or-
Issue one of the following commands from the terminal:
dpkg --install [filename].deb
dpkg -i [filename].deb
4.To verify the plugin is installed in Mozilla, launch Mozilla and choose Help > About Plug-ins from the browser menu.

I've tried all three. The first opens a couple of dialogs which have an install button which I have tried to use to install it. The result is the following message:

dpkg -i '///home/calban/Desktop/install_flash_player_10_linux.deb' ;echo RESULT=$?
(Reading database ... 204208 files and directories currently installed.)
Preparing to replace adobe-flashplugin 10.0.42.34-1 (using .../install_flash_player_10_linux.deb) ...
Unpacking replacement adobe-flashplugin ...
Setting up adobe-flashplugin (10.0.42.34-1) ...

RESULT=0

with the dpkg --install [filename].deb
dpkg -i [filename].deb

commands all I get is a message telling me that the file doesn't exist and yep I navigate to the desktop via the monitor and enter the file name - install_flash_player_10_linux.deb

I'm anything but a linux/ubuntu expert so needless to say I'm baffled as to what I'm doing wrong.

Any help (printable ) will be gratefully appreciated

Bob

---

### Post by slakkie on 2010-01-13
Please, do not crosspost/post duplicate posts for one problem.

[http://ubuntuforums.org/showthread.php?t=1379880](http://ubuntuforums.org/showthread.php?t=1379880)

---

### Post by Elfy on 2010-01-13
Closed.

---

