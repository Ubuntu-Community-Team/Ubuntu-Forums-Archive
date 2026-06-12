---
title: "Force-version &amp; Lock-version &amp; updates?"
date: 2014-07-05
forum: Installation &amp; Upgrades
---

### Post by r_avital on 2014-07-05
Hi all,

Ubuntu 14.04 LTS -64Bit.

I do not like Firefox 30.x and to make sure I didn't upgrade to that, this is what I did:

1. Uninstalled FF.
2. In Synaptic, highlighted FF and in the Package menu, selected "Force Version."  From there, selected version 28.
3. Installed FF.  So far so good, I got version 28.
4. In Synaptic, highlighted FF again, from the Package menu, selected "Lock version."

Today, "Software Updater" launched and asked me to update.  I allowed the update, only to end up with the now familiar message, "requires installation of untrusted packages."

Since we can't count on reliable updates anymore with the Software Updater (way to go for an LTS release), I went to a terminal and issued "sudo apt-get upgrade"

The upgrade went without incidents, and when I launched FF, it's version 30 again.  By the way, when I looked, very carefully, at the list of upgrades in "software updater" there was absolutely no mention of Firefox.

What did I do wrong?

Please:
1. No lectures about the mortal perils of not updating Firefox, I know the risks, I won't sue anyone if I get hit with a security issue.
2. No lectures about fixing/cleaning up the repository, because I followed all the instructions about cleaning/recreating a clean repo list and the "requires installation of untrusted packages" happened anyway.

Are the "force version" and "lock version" at this point just two more menu options that do nothing but frustrate users with false confidence because they're going to be ignored anyway, or is there a way to perform upgrades while still locking a particular package to a particular version?

TIA :)

---

### Post by Dennis N on 2014-07-05
I believe Synaptics "lock version" is only honored by Synaptic. Using apt-get upgrade will ignore it in calculating the upgrade. You can carry out your upgrading through Synaptic and its "Mark all Upgrades" button.

Another method, honored by apt-get:
See [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)
Maintainance Commands, #9.

---

### Post by r_avital on 2014-07-05
Wow, Thanks Dennis!  That's a useful link for apt-get.
I suppose many believe that Synaptic is just a front-end to apt, but it's good to know that pinning versions in it will only be honored by Synaptic.

Also figured out that the "unauthenticated" packages are all MATE packages, I guess they're slow on providing authentication keys.

Thanks again and all the best :)

---

### Post by ajgreeny on 2014-07-05
Are you aware of the classic-theme-restorer add-on for FF?

It allows you to get the look and behaviour of FF back to what it was previously, and for me was a real help as the australis theme was not to my taste at all.

[https://addons.mozilla.org/en-US/firefox/addon/classicthemerestorer/?src=ss](https://addons.mozilla.org/en-US/firefox/addon/classicthemerestorer/?src=ss)
[http://www.dedoimedo.com/computers/firefox-disable-australis.html](http://www.dedoimedo.com/computers/firefox-disable-australis.html)

---

### Post by r_avital on 2014-07-07
Thanks, ajgreeny, yes, I'm aware of it, and installed it.

---

