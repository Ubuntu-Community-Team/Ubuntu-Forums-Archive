---
title: "Upgrade to 20.04 reset my LXDE configuration back to Gnome desktop"
date: 2021-05-14
forum: Installation &amp; Upgrades
---

### Post by dhfx on 2021-05-14
About a month ago I successfully upgraded Ubuntu 18.04 with LXDE to 20.04. Subsequently I accepted an "upgrade" requiring a reboot, and when I rebooted I saw the following:
1) Auto-login had somehow been enabled, bypassing the login screen which offers a choice of desktop session types.
2) LXDE had been replaced by the basic Gnome desktop manager gdm3.
3) The "sudo dpkg-reconfigure" procedure to select the default DM offers only gdm3, lightdm and sddm as choices - lxde does not appear.

I have been attacking the auto-login issue first. The Users GUI does not show it enabled on my account. I looked at /etc/*gdm3*/custom.conf and found all items there to be commented out.

At this point I am at a loss to figure out what else could be enabling auto-login. Does anyone out there have any suggestions?

---

### Post by tea for one on 2021-05-15
> **dhfx said:**
> 3) The "sudo dpkg-reconfigure" procedure to select the default DM offers only gdm3, lightdm and sddm as choices - lxde does not appear.

gdm3, lightdm and sddm are all display managers i.e. log in screens which then load the desktop environment.

lxde is a desktop environment

Therefore, you will need to choose either lightdm or sddm (because gdm3 is used by gnome)

Just a reminder - lxde used to be integral in Lubuntu 18.04 but now Lubuntu 20.04 uses lxqt and this change may also be influencing other difficultiies which you mentioned i.e an older version of lxde on a newer Ubuntu 20.04

---

### Post by guiverc on 2021-05-15
Lubuntu 18.04 LTS was the last LXDE release, and all upgrades beyond that point should have been made through re-install.  If you check out the release statements for releases after 18.04, you'll note statements like

[URL="https://lubuntu.me/focal-2-released/"]Lubunutu 20.04.2 LTS Released!
[/URL]
> ***Note***, due to the extensive changes required  for the shift in desktop environments, the Lubuntu team does not support  upgrading from 18.04 or below to any greater release. Doing so will  result in a broken system. If you are on 18.04 or below and would like  to upgrade, please do a fresh install.

You may have considered yourself a LXDE user, but you were using Lubuntu packages (LXDE was Lubuntu up to 18.04) so if you used any meta packages in your install, you likely tied your system to Lubuntu (*and not specifically LXDE*); esp. given your mention of `sddm`. 

The upgrade was not supported due to the breaks, which yes can be fixed, but a re-install is usually far quicker (as many things aren't noticed at first, they'll be menu items that no longer work as they should you may not discover for weeks, months or years.. ie. a less than ideal or broken UI (*even if only minor*)).

---

### Post by ajgreeny on 2021-05-15
Did you actually install Lubuntu 18.04 or was this a Ubuntu install to which you added LXDE as the metapackage.

If the latter, I think your upgrade should still work as LXDE as a metapackage is still available in the standard repos for 20.04, and it will have pulled in as dependencies many other packages that are required, all of which should still be available, but would not be in the repos nay more had you installed lubuntu-desktop in your 18.04 version.  I am not sure how much development is happening with LXDE any more, if any, so bear that in mind when making your final choice.

As tea for one has mentioned, gdm3, lightdm and sddm are not the DE itself but the display manager that run beneath the DE of your choice and provides the login screen.  How autologin has come to be active I can not say but there will be a configuration setting somewhere which depends on the display manager used to disable autologin.

You could probably choose any of those three display manager when running the reconfigure command and still get to the DE you want but if gnome is to be your eventual DE, gdm3 would make most sense as that is what Ubuntu itself uses by default.

---

### Post by dhfx on 2021-05-16
In answer to ajgreeny: I added LXDE to an Ubuntu 18.04 install, then recently upgraded to 20.04.  I understand that the LXDE that I added is likely not compatible with 20.04.  I only added the LXDE because I wanted something better than the default Gnome desktop, which is what I'm back to now.  Can I try adding a different DE - e.g., Cinnamon - short of doing a complete reinstall?

---

### Post by guiverc on 2021-05-16
Yes you can install other desktops.  My own box was originally a Ubuntu (*artful*) install on which I added `xubuntu-desktop`, `lubuntu-desktop` and `ubuntu-mate-desktop`. I select which I want to use at login.

The `lubuntu-desktop` now means I have LXQt (*I've also since removed `ubuntu-mate-desktop` as I used it the least, and needed some disk space*). I tried to keep LXDE & LXQt on my box for awhile, but gave up as attempts to make it possible for Lubuntu users using LXDE to automatically upgrade to LXQt (without re-install, and not end up with both & an inefficient system) just made it more trouble than it was worth.

LXDE is GTK2 which is deprecated so I'd not suggest using it...  Yes it's light, but the lack of maintenance in regards security is the issue.

I'd suggest removing all remnants of LXDE before adding another desktop (a re-install maybe faster; you can re-install without touching user files too, even have your programs re-installed automatically if available in your 'new' release in Ubuntu repositories; key is to re-use partitions and do not format any using "*something else*").

I won't advise on Cinnamon though as I don't use it.

---

### Post by ajgreeny on 2021-05-16
I used gnome 2 until it disappeared back about 10 or 11 years ago, tried gnome 3 but hated it, so moved straight on to Xubuntu with Xfce which is brilliantly fast, incredibly configurable, can be made to look and behave just about any way you want it to, and has now been my "go to" of the Ubuntu family since then.

I have tried all the other DEs that are available but find some of them not to my taste, and others too full of eye candy which I don't want or need.

You should be able to add **xubuntu-desktop** package very easily and can try to remove as much of LXDE as possible, though it is probably not completely necessary.  You may be able to find all the packages that were added when you installed LXDE by running command ```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log
``` finding the date and time LXDE was installed, making a note of all the other packages installed at the same time, and then removing them.

---

### Post by dhfx on 2021-05-17
[**[COLOR=#C61919][B]ajgreeny**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=27747"): thanks for the suggestion - my install of LXDE was long enough ago that it no longer appears in the logs. I tried purging everything LXDE-related and installed XFCE, but cannot switch to it (I did get a different window background) because for some reason the system gives me auto-login so I don't see a login screen (I will start another thread for this). I googled for ways to switch the default DE from the command line, but there seems to be general confusion between DE's and DM's in the responses. Meanwhile I can work as long as I can bring up a command shell (LXterm or XFCEterm), so I can research further meanwhile.

---

