---
title: "List of applications not available"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by Krudtugle on 2008-03-15
I have just made a fresh installation of Ubuntu 7.10 and now I want to install EasyTag. Trying to use Synaptic, it doesn´t find EasyTag at all. When using Add/Remove Applications in the Applications menu (All available applications), I find EasyTag, but when ticking the check box, I get the pop-up message "List of applications not available".I click Refresh and some files seem to be downloaded, but then nothing more happens. I can repeat this as many times as I want, ticking the check box.

The same thing happens when using the Update Manager. I click Refresh and some files are downloaded, but no available updates appear. This seems strange, since the system is  just installed.

It wasn´t like this at all in Ubuntu 6.10. It worked perfectly there.

(Another strange thing, Synaptic doesn´t find Thunderbird. This can't be right?)

---

### Post by taurus on 2008-03-15
It cannot find anything to install because you have most if not all your repos disable in /etc/apt/sources.list.  Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and make sure there is a check mark in front of the first four lines, except the last one, Source code and Cdrom in the window below.  Close it and press Refresh.  Now, see if you can install anything with either synaptic or Add/Remove.

---

### Post by Krudtugle on 2008-03-15
Yes! That solved it. Thanks a lot!!!

---

