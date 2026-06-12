---
title: "How-to upgrade HPLIP?"
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by george3095 on 2007-12-23
In trying to determine why HPLIP Version 2.7.7 (only available from "Applications Add/Remove") would cause my printer to go bananas, I first tried what I hoped would be an upgrade by getting three .RUN files from HP, each for a different version. Each attempt bombed. Finally, I used Synaptic Package Manager and installed every relevant file displayed when I searched for "HPLIP". Of course, it was Version 2.7.7 even though there are 2.7.9, 2.7.10, and 2.7.12 upgrades from HP) I'm hopeful this time will be the charm. But, here's the REAL reason for the post: What does it take to make the three newer upgrades available via Synaptic?

---

### Post by Sef on 2007-12-23
To upgrade you have to go to [HP's site]("http://hplip.sourceforge.net/downloads.html") and download the latest version.   

The repositories don't always have the latest version.

---

### Post by george3095 on 2007-12-24
I had done exactly what you're suggesting, I downloaded three versions newer than my 2.7.7. First, I "ran" the .RUN file for the latest version, 2.7.12, but that failed when the activity indicator kept "rotating" but NOTHING happened for a VERY long time. Secondly, I tried uninstalling 2.7.7 and then installing it as I did with 2.7.12. Same result. The only way to install without glitches is through the "Applications, Add/Remove Applications"; but then the only version available is 2.7.7.

---

### Post by jaime256 on 2008-03-17
I second this. I got an HP Laserjet 1020 that stopped working and now I'm trying to upgrade the HPLIP software to see if this will fix the printer just not printing anything at all. The light is on but each time I try to print to it, the job gets sent but then... just poof, it disappears.

I just had a little chat with the HP support online and this is the link I got...the second one is the install I tried but keep getting too many different problems like something isn't here or I don't have that...I just want to upgrade it...the one under the package manager is the 2.7.7. I'm trying to upgrade to 2.8.2 in Ubuntu 7.10.

[http://hplip.sourceforge.net/index.html](http://hplip.sourceforge.net/index.html)
[http://hplip.sourceforge.net/install/manual/distros/ubuntu.html](http://hplip.sourceforge.net/install/manual/distros/ubuntu.html)

Just type this in a terminal window to find out what version of HPLIP you have installed, you don't need to be sudo:
hp-toolbox

Any help from the admins...thanks...I'm liking hp, at least they were kind enough to point me in the right direction for the drivers when it came to Linux...

I forgot to mention that I tried the self installer, but that still didn't install the latest version. It looked like it did, but then I rebooted and still got the same 2.7.7 so that's why I came and posted, maybe I missed something.

---

### Post by jaime256 on 2008-03-20
Any word on the printer issue from the admins. I just upgraded Ubuntu 7.04 to 7.10 and the hp laserjet 1020 printer still doesn't print anything. I already knew this wasn't going to change anything, but I had to check. So basically the printer just stopped printing under Ubuntu. I installed it under a windows machine and the printer worked fine. So I know the printer is working, but since I couldn't even print under any of the Ubuntu versions I just had to post because something has changed with the printing in Ubuntu and now the person can't print their work. Any help is much appreciated, Is anyone else having their hp just stop printing in the last week. Thanks.

---

