---
title: "Feisty Flunked Upgrade, but Passed the Course"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by tesseract420 on 2007-04-21
Here's my upgrade experience:

I used the alternate cd because I can't be assured of a steady internet connection for the duration of the upgrade. The upgrade is supposed to start automatically when you insert the CD, but it didn't. Alt + F2 and then gksu "sh /cdrom/cdromupgrade" started the process, however. The first error message said,

"Some 3rd party entries were disabled. You can re-enable them after the upgrade with the 'software-properties' tool or your package manager.'

The upgrade went fine until,

"setting up bluez-utils (3.90ubuntu4)..."

The system hung. Nothing happened. I just let it sit there. Then a BLANK error box came up. Still I did nothing. I clicked on the 'x' in the upper right hand corner. I was asked, " "" is not responding. Do you want to force-quit "" "? I clicked on yes, and the upgrade window disappeared. I'm still on the desktop, so I Alt-F2 again and start the upgrade again, but now it tells me that my password is wrong. It's the only password, I can't get around it, so no more upgrade.

I then tried to re-install the system without deleting any data. For a while I got stuck in partition hell because Ubuntu doesn't--or at least didn't--recognize that there was already a file system on my main partition. It recognized the type of file system--ext3, but not that there were already files there. So I placed a new root file system where the old one still was. At no time did Ubuntu (using the text-based install) recognize the existence of an already-existing installation.  Note that I had already tried to "repair broken install" without any success because the options always and only led to a partition deletion or format, which would mean data loss. 

When the installer finished, the system booted up a brand new install of Feisty. All the customization, network, proxy settings, etc. were gone [yes I know the text based installer has a sequence that asks you how you connect with the outside world, but where I am there are two proxies, not one--don't ask]. My data files were still around, though it took some time to find them. 

I wish I could have upgraded the installation. However, I still think it was worth even having only a new install. The network printing dialogue (module?) is absolutely terrific. I've been trying since Dapper to get network printing to work, and Feisty found the office network printer, installed a driver, and --it just works. This alone is worth the upgrade. Open Office on Edgy was broken. I had to use Abiword, which is a good program, but I had gotten used to OO. 

The bad part is that I'll have to spend time installing all of the programs I use. And where's Opera? Not in Synaptic, that's for sure. 

Anyway, my advice is, back-up your data, don't expect a flawless upgrade, but at the end of the day it was worth it.

---

