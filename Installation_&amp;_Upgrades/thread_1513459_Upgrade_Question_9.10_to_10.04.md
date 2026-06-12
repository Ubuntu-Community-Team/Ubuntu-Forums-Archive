---
title: "Upgrade Question 9.10 to 10.04"
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by golfnut324 on 2010-06-19
Pretty new to Linux and running 9.10. I have it set up just the way I like it (desktop, quick launch icons, settings, etc.). What happens to all of that when I upgrade to 10.04? Do I have to start over?


FYI:
2gb swap
30gb root ext4
608gb home ext4  ....................Does this matter?

Thanks for the help. Been lov'n Linux.

Craig

---

### Post by cogier on 2010-06-19
If you upgrade all the settings should stay the same. I have upgraded a couple of computers to 10.04 and it's worked very well. DO A BACK UP JUST IN CASE!

---

### Post by ajgreeny on 2010-06-19
If your /home is a separate partition, which I assume is the case from your list, life will be a bit easier, and if everything goes well you should end up with a system that looks like your current one, as all the configuration, or most of it anyway, is in /home as hidden files and folders.

You could try an on-line upgrade with the package manager, which often works well.  If you do not have any applications installed from other than the standard repos, you should be able to upgrade all your system and applications easily, and it will leave your /home untouched.

If you have any ppa repos enabled at the moment, or, for example, medibuntu, disable them or remove them completely from your software sources before you try the on-line upgrade, as they can cause problems.

If the on-line upgrade does not succeed, you will need to do a clean install by running the normal install and then choosing manual partitioning at that stage.  Choose your current 30GB / again as /root and tick the format button, and choose your current 608GB as /home, but DO NOT TICK THE FORMAT BOX.  If that is formatted you will lose everything.  I still strongly recommend backing up /home somewhere else before you do this upgrade.

Finally consider this;  do you really need to upgrade to 10.04 if you have 9.10 running as you want it?  There ir no real need to do so, unless you must have the most up to date packages, or are having some problems that you know will be solved by moving to 10.04, such as wireless reception, which generally gets better with each version of Ubuntu.

---

### Post by oldsoundguy on 2010-06-19
another method to upgrade (to be safe)
Burn an ISO of the new version.
save your ~/home folder to a thumb drive.
(that is JUST IN CASE something goes south)
Then run the upgrade.
Did that on 4 boxes .. no problems except on an upgrade from 8.10 LTS it dragged along a very outdated xorg.conf file.   Simply removing that from terminal: sudo rm etc/X11/xorg.conf
Solved the problem upon reboot.  Everything but Skype works perfectly .. Skype .. well, that's SKYPE'S problem (3rd party software)

---

### Post by golfnut324 on 2010-06-20
Thank you all for the good advice and help. Exactly what I needed to know.

Craig

---

