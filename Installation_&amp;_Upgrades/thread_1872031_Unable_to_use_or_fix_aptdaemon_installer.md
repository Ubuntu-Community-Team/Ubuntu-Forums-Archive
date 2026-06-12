---
title: "Unable to use or fix aptdaemon installer"
date: 2011-10-29
forum: Installation &amp; Upgrades
---

### Post by Chuo FPS on 2011-10-29
Hi,

Like my first thread, my problem comes from being in Japan. I tried to install a Brother printer on my Asus K53E laptop on which I use Ubuntu 11-10. The printer is an MFC-8820JN, which is specific to Japan and not sold anywhere else, hence there is no Brother package available for installation with Ubuntu. Result is I tried to install it using the closest printer package possible, e.g. MFC 8820, MFC 8420 or MFC 8820D etc., but with no luck. In any case, I can live without the printer, but ever since I have been unable to install anything else on my computer!

Each time I try to install something (e.g., VLC) a pop up window appears saying "Impossible to install VLC media player, items must be removed" and it indicates "Brother lpr printer definitions mfc8420lpr" as the package to be removed.

I'm a novice and have searched the forums and come across this post ([http://ubuntuforums.org/showthread.php?t=1610154](http://ubuntuforums.org/showthread.php?t=1610154)), but couldn't find a solution using the Synaptics Package manager, and this post ([http://ubuntuforums.org/showthread.php?t=1854573](http://ubuntuforums.org/showthread.php?t=1854573)), but when I run a Terminal as suggested I get this screen (after eventually following the Terminal's advice to install dselect):

sudo apt-get install dselect
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  mfc8420lpr
The following NEW packages will be installed
  dselect
0 upgraded, 1 newly installed, 1 to remove and 28 not upgraded.
1 not fully installed or removed.
Need to get 0 B/179 kB of archives.
After this operation, 1,155 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 144800 files and directories currently installed.)
Removing mfc8420lpr ...
/var/lib/dpkg/info/mfc8420lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing mfc8420lpr (--remove):
 subprocess installed post-removal script returned error exit status 127
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 mfc8420lpr

In a word, I can't install anything until I delete "mfc8420lpr", but I don't seem to be able to! Help, please!

Thanks.

---

### Post by Chuo FPS on 2011-10-31
I seem to have found a solution after hours trawling the forums. I went here [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/135179](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/135179) and at the bottom of the page followed this advice:

$ sudo rm /var/lib/dpkg/info/mfc8420lpr.postrm

which didn't work, then I did this:

$ sudo apt-get remove mfc8500lpr mfc8420lpr

which removed the mfc8429lpr package that was preventing aptdaemon from working. I've since been able to update and install VLC without any problems!

---

