---
title: "Installer hangs leaving blank screen"
date: 2006-07-09
forum: Installation &amp; Upgrades
---

### Post by butterman on 2006-07-09
I've seen several posts that describe the same problem I'm having: the installer hangs at the 60% completion point and shows a blank screen except for two white rectangles. Some have suggested the CD is bad. I downloaded again and burned again (on a different drive) but the installer hung at the exact same point.  Others suggested using the server version, but I need Alternate to configure a dual boot.  Anybody find a solution to the problem?

1) System Specifications:
Dell Dimension 5150
Monitor: 19" LCD 1280 x1024
Ram Amount:1 GB
HD: SATA
Onboard Graphics Card: Intel 945G
CPU: Pentium D 2.8 GHz
MainBoard: Intel?
2) Version of Ubuntu your using: Ubuntu 6.06 Alternate
3) Error or output codes you receive durring the install or after: At approximately the 60% mark, a blank screen with two white rectangles appears. Text description may have said "building Ubuntu Desktop."

---

### Post by stevenprentice on 2006-07-09
I was experiencing the same problems with Edubuntu and I think they are related because Edubuntu uses the text-based installer.

I was able to resolve it by changing the VGA settings at the boot screen. I set mine to 800x600x16 and everything worked fine. The screen flickered at the same place, but came back to the install progress indicator.

The problem seems to occur during the xserver configuration when it is autodetecting the screens.

-Steve

---

### Post by butterman on 2006-07-10
Thanks for your reply.  How do I get to the boot screen?

---

### Post by Nutley on 2006-07-10
I think he is referring to the screen that comes up prior to installation that gives you the options of the install...

There is a VGA button on the bottom of the screen, I think it is F4 but may be F5... 

I am having the same issue so I am going to go try this when I get   home.. hopefully this will solve my problem.

---

### Post by butterman on 2006-07-10
I will look for a VGA button too.  In the meantime, for the benefit of others, I will try to clarify the problem.  I'm using the text installer with Alternative 6.06. The installation proceeds to the part entitled "select and install software."  During this part of the installation, the progress bar reaches 58% and shows "preparing to configure Ubuntu desktop."  At this point the progress bar stalls and, after less than a minute, the screen goes blank except for two white rectangles.  I tried this three times and got the same result everytime.

---

