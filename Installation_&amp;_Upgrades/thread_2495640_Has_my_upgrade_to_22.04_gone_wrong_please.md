---
title: "Has my upgrade to 22.04 gone wrong please?"
date: 2024-02-25
forum: Installation &amp; Upgrades
---

### Post by andrew-q2 on 2024-02-25
I was upgrading a Dell laptop from 16.04 (I think) to 22.04 when its power failed and the laptop went off.  It had done much of the upgrade (I did "do release upgrade" in Terminal) and it had paused to ask if it should remove several hundred obsolete packages.  I said Yes and it was doing this when it lost power.

The laptop now basically works and System Monitor (or something) says it is Ubuntu Studio at 22.04.  However when I've logged in, I get a screen saying Debian as per attached pic, which I can't imagine is right.  I have Ubuntu 22.04 on a desktop with the jammy jellyfish image and was expecting something like that on the laptop.

Also I don't think there was time before the crash to remove all the obsolete packages but when I do "sudo apt update" or "sudo apt upgrade" there is nothing to remove.  Also apt-get autoremove doesn't find them.  I'm not an expert user - is it ok to run the section from [here]("https://askubuntu.com/questions/539235/how-to-remove-obsolete-packages-after-failed-release-upgrade-via-do-release-upgr")  i.e.
------------------
sudo -i
apt-get update
apt-get autoremove
apt-get clean
 
UNUSCONF=$(dpkg -l|grep "^rc" | awk '{print $2}')
apt-get remove --purge $UNUSCONF

NEWKERNEL=$(uname -r|sed 's/-*[a-z]//g'|sed 's/-386//g')

ADDKERNEL="linux-(image|headers|ubuntu-modules|restricted-modules)"

METAKERNEL="linux-(image|headers|restricted-modules)-(generic|i386|server|common|rt|xen)"

UNUSKERNELS=$(dpkg -l | awk '{print $2}' | grep -E $ADDKERNEL | grep -vE $METAKERNEL | grep -v $NEWKERNEL)

apt-get remove --purge $UNUSKERNELS

update-grub
----------------------
Looks quite scary to me!

Apologies for upside-down photo

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293435&stc=1[/IMG]

---

### Post by guiverc on 2024-02-25
> **andrew-q2 said:**
> I was upgrading a Dell laptop from 16.04 (I think) to 22.04 when its power failed and the laptop went off.  It had done much of the upgrade (I did "do release upgrade" in Terminal) and it had paused to ask if it should remove several hundred obsolete packages.  I said Yes and it was doing this when it lost power.

The laptop now basically works and System Monitor (or something) says it is Ubuntu Studio at 22.04.  However when I've logged in, I get a screen saying Debian as per attached pic, which I can't imagine is right.  I have Ubuntu 22.04 on a desktop with the jammy jellyfish image and was expecting something like that on the laptop.


I'll just comment and give my 2c.

You mention an upgrade from 16.04 to 22.04???  Ubuntu 16.04 had two *fully supported* upgrade paths being to the next release (eg. 16.10) OR the next LTS (18.04), so what you were attempting is very unclear to me.

You've also mentioned Ubuntu Studio, which has changed desktop, and required a re-install due to this change.. eg. if you read [https://ubuntustudio.org/ubuntu-studio-22-04-lts-release-notes/](https://ubuntustudio.org/ubuntu-studio-22-04-lts-release-notes/)

> 
[B]Due to the change in desktop environment, direct upgrades to Ubuntu Studio 22.04 LTS from versions *prior* to 21.10 are unsupported.
[/B] 

which is there because of desktop breakage.. the DEBIAN logo you mention could just be an indication of some breakage the release notes warn you about.

Whilst I have no experience with the Xfce to KDE Plasma change with Ubuntu Studio, I did have significant experience with the Lubuntu LXDE to LXQt change.. as I used the *unsupported* upgrade on my primary system, and I spent near three weeks fixing issues, thus I'd not recommend the upgrade (*I did it pre-release as part of normal QA.. experiences like mine are why it was unsupported*)... though on other boxes where I'd made fewer changes, added fewer packages to my install the change was far less troublesome.

I don't understand what you did, given you describe an upgrade path which is **not supported **and your issues maybe a consequence of that (16.04 upgraded to 18.04! not 22.04, let alone the issue of Ubuntu Studio upgrade itself with a possible desktop change).

FYI:   You do mention being unsure of what you were running, it was likely something newer than 16.04 or the 2016-April release.. but that detail really matters in regards what I'd suggest.  Most issues in the Lubuntu LXDE to LXQt changes were rather *petty* in my experience; mild-annoyances.. just lowering the quality of the end-result, instead of causing outright-failures.. but I haven't QA-tested a Ubuntu Studio desktop change AND what you were running before upgrade is critical in my view.

---

### Post by andrew-q2 on 2024-02-26
guiverc,  thank you for this info and taking time to post it.
Re. what I did, I simply apt updated and upgraded, then did "do release upgrade".  It didn't give any warnings, just got on with it.
I can't remember when or if I previously upgraded, so guessed 16.04, but it could have been later.  I'm sure it was pre-21 because I always go for the LTS releases.
Anyway I probably should have read the release notes before doing this!
I think my best bet now is to scrap it, and do a fresh install onto an empty disk.  This will also allow me to delete an old Windows partition that is no use to me.
Thanks again, Andrew

---

### Post by guiverc on 2024-02-26
If you were using 16.04,  the `do-release-upgrade` would have only upgraded you to 18.04 IF it did anything..  (16.04 & 18.04 are EOSS and now only *supported* via ESM, thus I've not tried, but ESM *release-upgrades* are possible so that would probably have occurred).

You were likely using 20.04, which **would** *release-upgrade* to 22.04, as that is a *supported* upgrade...  This is what I believe you did, ie. upgrade a 2020-April release to the 2022-April release.

The official upgrade for the upgrade you did I believe, would be found on this page

[https://help.ubuntu.com/community/JammyUpgrades](https://help.ubuntu.com/community/JammyUpgrades)

which you'll note there too has *unsupported* warnings for Ubuntu Studio.

The [Ubuntu Release Upgrader tools]("https://launchpad.net/ubuntu-release-upgrader") are base Ubuntu tools, so will let you perform any upgrade available to the base Ubuntu system, including *unsupported* upgrades such as Lubuntu or Ubuntu Studio when they switched desktops.. The release notes & warnings published in the respective release notices (and warnings in Ubuntu docs) are all there was to warn you.  Your *base* system should have successfully upgraded; just the components that weren't *supported* in upgrade may have been left *broken* as 'warned'.

Anyway; if you (decide to) re-install, you can non-destructively re-install Ubuntu Desktop systems, which is actually easiest for the *flavors* too.

I'll provide a link I wrote elsewhere where I talk about it

[https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533](https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533)

Whilst I've not used this with Ubuntu Studio, I use it very regularly with Lubuntu (using the `calamares` installer), Xubuntu (using the `ubiquity` installer) & others.

It's just an *unclean* install that allows your data to survive, and the additional programs you've installed (from Ubuntu repositories) to auto-reinstall too, allowing you to get back to fully-operational pretty quickly.

Even if you have issues with the non-destructive re-install (*some third party apps can't cope with this, so manually installing them post-install isn't a significant problem anyway, but even if you have install problems*), you've still got a *clean* install option available to you anyway.

Regardless, backup all data that's important to you.

---

### Post by andrew-q2 on 2024-03-16
Thanks @guiverc, there's some interesting info you've posted there.

---

