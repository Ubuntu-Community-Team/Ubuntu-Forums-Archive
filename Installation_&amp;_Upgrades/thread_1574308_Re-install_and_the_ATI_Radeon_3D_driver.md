---
title: "Re-install and the ATI Radeon 3D driver"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by Unterseeboot_234 on 2010-09-14
Hi people,

I've always had and used Ubuntu. When I installed and did not like the stability of a certain version, I just reformatted the partition and used LiveCD.

OK, on a virgin SATA, 300-gig partition, I installed 10.04 and that took the ATI Radeon 3rd-party graphics driver. No problem. Then, the family wanted 2 languages on the machine. The German keyboard screwed me in terminal and I wiped out Home and all their data. I used Scalpel to image-carve 300-gig onto a 400-gig partition and tried to re-install Ubuntu 10.10.

The ATI's fglrx will not install, that's the error. That same file prevents upgrades of Ubuntu to current status.

is this thread current for my problem with 10.10?
[**http://ubuntuforums.org/showthread.php?t=651566**]("http://ubuntuforums.org/showthread.php?t=651566")

Or, do I have that 400-gig with the backup cross-pollinating?

Any ideas, thanks...

---

### Post by mörgæs on 2010-09-14
> **Unterseeboot_234 said:**
> 
is this thread current for my problem with 10.10?
[**http://ubuntuforums.org/showthread.php?t=651566**]("http://ubuntuforums.org/showthread.php?t=651566")



No, it ended in 2007 :-)

This one is:
[http://ubuntuforums.org/showthread.php?t=1561685](http://ubuntuforums.org/showthread.php?t=1561685)

---

### Post by Unterseeboot_234 on 2010-09-14
The Symptoms...
1. A month ago, the Live CD of 10.04 installed flawlessly on AMD64 Phenom-II hexacore. Restricted Hardware driver menu activated Radeon driver.Update manager installed several updates over the days. I needed to reinstall. 
2. Live CD installs. On a reboot I get a wild scrolling black monitor with messages flying by for about 5 minutes. Go thru BIOS, login and then I get a jittery 1/3 of the desktop for a minute and finally a desktop.

That has to be X11-org.
3. The Restricted hardware menu (with the Activate button) would not install the driver. Update Manager failed to install the new Linux kernel offered in apts.

4. I googled around for fglrx. There is a wiki article
**[http://en.wikipedia.org/wiki/Fglrx]("http://en.wikipedia.org/wiki/Fglrx")**

The section for External Links: lead me to **[The Unofficial Linux ATI Wiki - http://wiki.cchtml.com/index.php/Main_Page]("http://wiki.cchtml.com/index.php/Main_Page")** a link there for Ubuntu and finally a link to Lucid 10.04 installtion.

That recipe is terminal-based. The instructions caused the existing Linux kernel to be patched and fetch fglrx. That installs.

5. Updates for Ubuntu ... so good so far, they do install. I unchecked a lot of stuff on Update, but made sure to include the new Linux image, linux-kernel; anything with the word 'linux'.

Reboot.

6. The wild visual artifacts in Shutdown and To-Desktop are gone. What's weird is I now have a two new Menu Items for Catalyst Control Center that the original LiveCD / Update from a month ago did not put there.

So, I have got almost a fix. A month ago, the GUI-Windows had pretty little halos when you hovered over the buttons.

The little halos I'll miss. 

This current install I will back up onto an external. I wished I had backed up a month ago.

---

