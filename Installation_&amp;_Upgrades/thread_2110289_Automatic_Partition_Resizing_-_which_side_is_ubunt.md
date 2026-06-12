---
title: "Automatic Partition Resizing - which side is ubuntu?"
date: 2013-01-29
forum: Installation &amp; Upgrades
---

### Post by ArlieS on 2013-01-29
Ubuntu 12.10, installing on a system which already had windows 7 (NTFS5). 

I was kind of vaguely following [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

I got to the Automatic partition resizing, and it gave me 2 *unlabelled* graphics, where I could shrink one and grow the other. But which one was for Ubuntu and which one was for Windows? I guessed wrong, and left most of the space with windows. Worse, I didn't clearly record which side I'd guessed as Windows. 

A variety of other "exciting" things then happened, with the result that IT is now re-imaging my disk - once again as Windows-only, whole disk. (I asked, and their tools don't let them use only part of the disk for Windows.) 

So I'm going to be back in the same place, doing my install-and-repartition again. Before I get there, can anyone produce a labelled graphic, or simply tell me "left side is Ubuntu" or "left side is Windows"? 

Thank you.

---

### Post by oldfred on 2013-01-30
Much better to use Windows MMC to resize Windows and reboot a couple of times. Windows has to run chkdsk and make other repairs on a resize and sometimes that causes issues if not done by Windows.

Then you have be able to install into the unallocated space you have created. If dual booting with Windows best to create a shared NTFS data partition for any data you want to share between systems and mount Windows system partition as read-only from Ubuntu. That often avoids issues.

       Install options, Do not use erase entire drive unless that is really what you want.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by ArlieS on 2013-01-30
> **oldfred said:**
> Much better to use Windows MMC to resize Windows and reboot a couple of times. Windows has to run chkdsk and make other repairs on a resize and sometimes that causes issues if not done by Windows.



Aha - that makes sense. I'm pretty much a clueless luser on Windows, so my instincts were to use the convenient interface provided by the Ubuntu install. The result was an unrecoverable NTFS file system ;-) (Windows *tried*, claimed to have succeeded - and then couldn't reboot.) Hence the reimage and restart.

I don't suppose you have any handy links for how to do this on windows 7? Googling "windows MMC" is giving me articles about customizing an administrator's console on Windows 2000, and similar. I'm guessing I need to find the name of the specific windows tool, and google that. Or get lucky with broader searches.

[Update: found the right thing to google: "windows disk management"]

---

