---
title: "Upgrade to 8.04 FROZE/DIED; lost Ubuntu altogether"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by stevecro on 2008-05-24
Hello,

Now working from the other install/partition (my OpenSuSE 10.3) on my multi-boot machine (Dell Dimension E521). Ran the Ubuntu in-place upgrade to 8.04 (from 7.10) starting last night. After 8-1/4 hours of downloading and about 90% of the installing done (started with "34 minutes remaining" and got down to "3 minutes remaining"), when process got down to updating an "avahi" program (I was watching with the "Terminal" option), process just FROZE/DIED. I knew something was wrong because on the only app that I had left up during the install, my gkrellm monitors, everything, even the cpu activity graphs, just STOPPED. Watched a frozen machine for a few minutes and then sadly did the Ctrl-Alt-SysRq-r-e-i-s-u-b routine to reboot the machine.

Initial startup through grub and into my OpenSuSE 10.3 still works fine, from which I'm writing this (thank Goodness). But any hopes of picking up where my stopped ("it did the stopping, not me!") Ubuntu upgrade left off have been dashed. 

NO secondary grub menu comes up for Ubuntu on its partition like I had coming off of the main grub menu before. It just starts up with the orange progress bar on black background splash screen, then a command-mode login prompt for my password, etc.. Then graphical mode tries to start and I get a warning about being in a low-graphic mode. Then the blank orange screen. Mouse works. After fumbling with some keys managed to pop up something asking if I wanted to do a screen snapshot (rather ironic, being offered to save a screen snapshot of a totally blank orange screen).

Looks like I will now have to try to download a totally new image and start all over on my Ubuntu partition. 

(Does anyone think there's a chance I could download the "alternate CD" for upgrade (they still have these, right?) and boot from it and salvage/finish this upgrade?) 

Had done some backup onto an external drive before I started, but this (about 220 megs worth) was just of my /var, /etc, /home, and one other directory. Not sure yet how useful this will be. All I have to say is that I'm darned glad that my Ubuntu was NOT where I was doing my file saving, email, etc.. It was just a place where I used to watch videos (before they started freezing all the time in 7.10 -- was hoping that would be corrected with 8.04), and more of an educational thing. 

I will hang in there with Ubuntu, but needless to say I am VERY, VERY disappointed with the upgrader (upgrading 7.04 to 7.10 like this actually worked with no problems). :-( SC

---

### Post by stevecro on 2008-05-25
Replying to my own post (please excuse, a little new at forum participation and still learning the customs):

Problem now SOLVED

Many THANKS to all who may have contributed the information that I used (I took procedure from a contribution posted as a reply to someone by iaculallad).

I did, on a subsequent boot up attempt, get the secondary (for my system) GRUB menu, and went into recovery mode. An "arrow keys" type of menu (not GUI) came up, from which I started running dpkg, which did not finish all the way, then went back to the menu and invoked the choice for a root shell, then tried the sequence of:
dpkg --configure -a
apt-get -f install
apt-get update
apt-get upgrade,
which I actually had to try more than once. After more than one try (and I think a reboot), finally got this procedure to run all the way through (I could tell by all the gnome packages setting themselves up that I had not seen yet in the lists scrolling by). Upon reboot after finishing this, 8.04 started up quite well. A bit of initial desktop wierdness with the icons representing other partitions, but now OK.
Thanks again to all who help here (and to those developers who knew that a system needs a way to recover from interrupted (by its own freezing, or externally) updates and built that in). SC

---

