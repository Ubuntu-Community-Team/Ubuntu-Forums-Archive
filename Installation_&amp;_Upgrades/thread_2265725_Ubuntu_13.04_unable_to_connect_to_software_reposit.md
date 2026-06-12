---
title: "Ubuntu 13.04: unable to connect to software repository"
date: 2015-02-17
forum: Installation &amp; Upgrades
---

### Post by Mr. Farlops on 2015-02-17
Hello, 

I have Raring Ringtail installed on my laptop and I've found I can't connect to the Software Center, to change or upgrade packages and applications. Nor can I upgrade the operating system to later versions of Ubuntu. 

How do I point to the current repository? Or do I have to update the system quasi-manually with a live Ubuntu stick? Ideally I'd like to upgrade the system to an LTS version.

Thanks in advance for any help you may have!

---

### Post by sudodus on 2015-02-17
***Start by backing up everything important***, because upgrading or installing new operating systems and editing partitions are risky operations.

You can't upgrade directly to a supported version, and upgrading in two steps 13.04 --> 13.10 --> 14.04.1 LTS is cumbersome (extra difficult because 13.04 and 13.10 have passed end of life). Instead I would recommend that you make a fresh installation of 14.04.1 LTS.

If you want to keep your personal settings, you can save your home directory, and make a ***home partition*** of it. Then during the upgrade you select ***Something else*** at the partitioning window and select the /home partition. Do ***not*** format it.
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

---

### Post by Mr. Farlops on 2015-02-19
Ah, yes, I sort of expected it would be something like this. 

Thanks!

---

