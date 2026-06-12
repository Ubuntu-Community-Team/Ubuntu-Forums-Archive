---
title: "Upgrading from Feisty...Frustrating"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by eeshking on 2007-11-23
Well, I've encountered a lot of problems upgrading from Feisty to Gutsy. First off, before I even upgraded, my wireless internet connection has been pretty bad ever since I got Feisty. I'm using a Netgear WG111v2 and it had out of the box support from the wireless network connection thing, but unfortunately, the connection kept crashing every once in a while. I tried using ndiswrapper but to no avail. Because of this, I was unable to download the update to get from Feisty to Gutsy--the internet connection would crash too frequently to successfully download it. So, I downloaded the Gutsy alternate install CD on another computer and burned it. I successfully used that to upgrade from Feisty to Gutsy, but when the upgrade finished and my computer restarted, the screen resolution was at 800x600. First, I tried to look at the screen resolution settings page to set it from to a higher resolution, but 800x600 was the only resolution there. Then, I thought the proprietary driver for the ATI Radeon graphics card might not be enabled, so i went on over to the restricted drivers manager, only to find out that it wouldn't start up after I entered the password. I tried running it from the command line, only to find an error message. Then I tried updating apt-get and reinstalling restricted-manager, but it did absolutely nothing. Furthermore, I can't even change my sources list from the GUI. So basically, I've got three problems: (1) Internet connection isn't great. If anyone knows how to make a WG111v2 work properly, I'd appreciate the knowledge. Right now, whenever the internet connection goes down, my preferred method of repair is to take out the network card from the USB port and stick it back in. (2) the resolution is stuck at 800x600, and it's possible that my proprietary drivers aren't working and (3) I can't change the sources list from GUI, nor can I access the restricted-manager

---

### Post by Danikar on 2007-11-23
Not sure about the WiFi issues, also might want to check if it is a hardware problem.

Here is some help with your resolution issue.  I had the same problem.

[http://ubuntuforums.org/showpost.php?p=129379&postcount=21]("http://ubuntuforums.org/showpost.php?p=129379&postcount=21")

---

### Post by m404 on 2007-11-23
it's an hardware issue.

i have a WG111v2 myself here , and the quality is just close to "not usable".
whether i use WinXP , Vista or Ubuntu, the same problem keeps happening.
Every once in a while, the Wireless connection crashes, and i have to reconnect (in WinXP i cant even just reconnect, i HAVE to disconnect the stick from the USB port and reconnect it, otherwise it won't find any networks).

i have 3 machines to test it on, with various operating systems, and it kept happening.

so i went and made alot of research on the net, including official netgear forums.
guess what? they know about it, they will replace your stick if you send it in.
it's a common error of the WG111 series (v1 had it aswell) and it seems to happen more often when u use the long cable provided by netgear when you buy the stick (some users reported that there is a definitely huge difference in signal quality whether you use the original cable (bad) or a seperately bought cable (good) ... pathetic, in my eyes).

never, EVER again am i buying netgear hardware !
i'm a certified IT consultant, i work with various pieces of hardware every day, and although i agree there are a handful of really good netgear products out there, the overall quality of their products is really at a low level.

---

