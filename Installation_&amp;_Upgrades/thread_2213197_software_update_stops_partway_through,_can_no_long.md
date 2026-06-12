---
title: "software update stops partway through, can no longer update anything"
date: 2014-03-25
forum: Installation &amp; Upgrades
---

### Post by a-you on 2014-03-25
This problem surfaced many months ago and I never managed to fix it. I searched high and low but never found anything that seemed at all relevant; maybe I'm the only one that has experienced this?

If I try to use the Software Updater GUI it checks for updates, reports that there are some, then it apparently fully downloads the updates but after that it gets stuck with this showing in the terminal window (please see see screen shot "install_stuck-1.png").

[ATTACH=CONFIG]251452[/ATTACH]

At the end of the text in the terminal there's the name of a file in /tmp highlighted. At this point the process of updating simply stops. If I scroll down in the terminal eventually I arrive at what you see in the next screen shot ("install_stuck-2") where "(END)" is highlighted in the window. But the packages don't actually get installed.

[ATTACH=CONFIG]251453[/ATTACH]

For I guess at least a year now I've adjusted to this by rebooting and selecting the "Fix broken packages" option in the special boot menu. The packages would not be downloaded again (because I was not online yet) but the ones that had just been downloaded would be installed, and though it was awkward it worked.

Now though, for the first time, the same thing happens even when trying to "fix broken packages."

Rebooting doesn't help, nor does this sequence of steps:

```

sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get dist-upgrade

```

Btw each time this happens the name of the temporary file is different, and when I reboot the file is gone, but that still doesn't allow the packages to actually be installed. Also the same thing happens whether I use the Software Updater or if I simply try to do dist-upgrade from terminal from the start.

Anybody have any idea what to do?? (*Thanks* in advance)

Quantal 64 bit, but I see from notes I kept that the same thing happened when I was using Natty (never got it fixed).

---

### Post by ajgreeny on 2014-03-25
**"Quantal 64 bit**"

There is your main problem, and I suspect your "many months ago" was October 2013 as quantal (12.10) has not had any support for that length of time, and updating will be impossible using the normal repos.

It is theoretically possible to make use of some End-Of-Life repos, but frankly, I wouldn't bother.  Just upgrade to a new version using a clean install and get yourself a fresh start.
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by oldos2er on 2014-03-25
If something like the first screenshot you posted happens again, type **q** and the update should continue normally.

---

### Post by a-you on 2014-03-26
Thanks [**[COLOR=#C61919][B]oldos2er**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=338320") so much! That worked, and so simple!! I guess I gotta learn more about the basics of bash, or would that be dash. There's always more to learn about this fabulous OS (the good news and the bad news ;-) )

And thanks [**[COLOR=#000000]ajgreeny[/COLOR]**]("http://ubuntuforums.org/member.php?u=27747") for your comments but even now it installed a new kernel version plus several other things. I'm still using quantal because it's working real nicely (apart from the above mentioned snag) and so I decided to wait until the next long term support release before I upgrade.

---

### Post by ajgreeny on 2014-03-26
Sorry, my mistake, but it will soon overtake you and become unsupported.
From [http://ubuntuguide.org/wiki/Ubuntu_Quantal](http://ubuntuguide.org/wiki/Ubuntu_Quantal)
> Quantal Quetzal is not an LTS (Long Term Support) release. It will be  supported with security updates for both the desktop and server versions  until April 2014. 

---

### Post by oldos2er on 2014-03-26
> **a-you said:**
> Thanks [**[COLOR=#C61919][B]oldos2er**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=338320") so much! That worked, and so simple!! I guess I gotta learn more about the basics of bash, or would that be dash. 

You're welcome. q is a somewhat standard way of cleanly exiting the "less" program (also man pages, top, and many other CLI tools) which was what I assumed was showing in your screenshot.

---

