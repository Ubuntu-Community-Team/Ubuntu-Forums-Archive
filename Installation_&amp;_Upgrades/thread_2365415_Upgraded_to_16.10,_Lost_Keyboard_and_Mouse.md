---
title: "Upgraded to 16.10, Lost Keyboard and Mouse"
date: 2017-07-06
forum: Installation &amp; Upgrades
---

### Post by bdmcgrew on 2017-07-06
Good morning all...  I'm brand new to Ubuntu and haven't been able to find a usable answer yet.

Last night while updating my 16.04LTS system I was prompted for the upgrade to 16.10 so I accepted the challenge.  While watching in a terminal everything seem to go smoothly and the system rebooted.  After reboot I now have no keyboard or mouse at all.  And, the grub screen is gone so I can no longer go back and boot an older kernel.  

Please help?  The system is a HP AIO with a standard USB keyboard and mouse, nothing funny at all.  

How do I go about recovering at this point?

thanks,

-brian

---

### Post by slickymaster on 2017-07-06
*Thread moved to **Installation & Upgrades**.*

---

### Post by bdmcgrew on 2017-07-07
Anyone?

---

### Post by monkeybrain20122 on 2017-07-07
Not sure about what happened. But three pieces of suggestions.

1) If you are new to Ubuntu or use Ubuntu for work you should stick to LTS. The interim releases are kind of beta in preparation for the next LTS. There are some good ones, but all have only 9 month support. As a new user you don't want to keep blowing up your OS. There are less risky ways to upgrade your software without going through the 9 month OS upgrade cycle (use ppas and there are snap packages for a small numbers of applications)

2)  When you update your OS it is better to do a clean install than "upgrade", it is a lot faster and less problem prone. If you look at these threads a lot of problems are the results of bad upgrades. All these disappear with a new install.  Next time when you install, go for advanced instead of automatic install in the installer and keep separate root (mount point /) and home partitions (mount point /home) so you can just reinstall / when you do a clean install and leave your data intact.

3)16.10 will reach end of life this month, so there is no point trouble shooting it. It is a dead OS walking (and it is buggy anyway. I have tested it on a spare hd for a few months before getting rid of it), so just nuke it and reinstall 16.04 LTS. You can install 17.04, but it is another interim, also it is kind of buggy, I am running it on a test install, a few things that work in 16.04 don't work in 17.04.e.g logging out freeze your system, it is a known bug.

---

