---
title: "Gdebi Install Fails - Required for ZOOM"
date: 2022-04-28
forum: Installation &amp; Upgrades
---

### Post by electrosteam on 2022-04-28
Lubuntu 21.04
Kernel 5.11.0-49-generic

Trying to install ZOOM, which requires gdebi.
Followed instructions and got an entry in the Application Menu under System Tools: GDebi Package Installer.

When select GDebi get error:
    Downloading the package failed: file" 'g-io-error-quark: Operation not supported (15)'
    
In the terminal try gdebi:

~$ gdebi --version
0.9.5.7+nmu4

~$ gdebi-gtk

(gdebi-gtk:20575): GLib-GIO-CRITICAL **: 16:19:40.963: g_dbus_proxy_new: assertion 'G_IS_DBUS_CONNECTION (connection)' failed


The Muon Package Manager seems happy with gdebi.

Where to from here ?
Keep well,
John

---

### Post by guiverc on 2022-04-28
Ubuntu 21.04 (*and all flavors like Lubuntu 21.04*) is [I]end-of-life.

[/I]- [https://lubuntu.me/hirsute-eol/](https://lubuntu.me/hirsute-eol/)
- [https://fridge.ubuntu.com/2022/01/21/ubuntu-21-04-hirsute-hippo-end-of-life-reached-on-january-20-2022/](https://fridge.ubuntu.com/2022/01/21/ubuntu-21-04-hirsute-hippo-end-of-life-reached-on-january-20-2022/)

The 5.11 kernel you mention is *unpatched* and no longer *supported* by Ubuntu, so I hope your system is *offline*.

I'd suggest you concentrate on a *release-upgrade*, or re-install of a *supported* release of Lubuntu.  Refer [https://manual.lubuntu.me/stable/D/upgrading.html](https://manual.lubuntu.me/stable/D/upgrading.html) though note as you're using an EOL release, there are added complications to your EOL system.

In future, I'd suggest using a LTS release if you don't want to *release-upgrade* every 6-9 months; 21.04 told you it was the 2021-April release (*year.month* format is used) so calculating the EOL is easy if you know your release.

Many repositories get dropped for EOL releases, others get moved; if it's a moved repository the following maybe helpful

- [URL="https://help.ubuntu.com/community/EOLUpgrades"]https://help.ubuntu.com/community/EOLUpgrades


[/URL]

---

### Post by electrosteam on 2022-04-28
Interesting.
I am only a low-level user of Linux, and I have really tried to keep my install up-to-date.
Low-level as in getting involved with the system, I do use the system extensively for all the normal activities.

I went from 20.04 LTS to the 21.04 only because pdf printing did not work for me.
Every upgrade offered since then has been installed.

What do I have to do to enable the system to advise me of necessary upgrades ?
As 22.04 is on temporary hold, should I upgrade to 21.10 ?
Then re-install gdebi ?

I will check the reference links suggested.
Thanks,
John.

---

### Post by guiverc on 2022-04-28
Your system hasn't received security updates since it reached EOL (*for the main packages, those installed from Ubuntu/Lubuntu as deb packages; snap packages will likely still get upgrades as they're identical for all releases*).

A number of 21.04 upgrades that were sitting in -proposed (*they sit there a time allowing people who've opted to use them to use them, reporting errors if they detect them before they go out to everyone*) were actually deleted so the repositories could be closed (*they'd not sat in -proposed long enough when it was closed; deleting or keeping the repository open were the option; deleting was chosen*), as users got the updates after they'd upgraded to 21.10 was the thinking.  I'd thus *release-upgrade* to 21.10 asap.

There is noupgrade path direct from 21.04 to any release except for 21.10, as being a non-LTS release, the next release is all it's intended to be upgraded to. You will be able to *release-upgrade* from 21.10 to 22.04, but you cannot go direct without forcing it (*meaning QA wasn't performed to ensure it's safe and without problems*) or via re-install.

Quick checks of the `gdebi` package detail provided show it's not a *supported* Ubuntu version, but it may have been an *hirsute* package but I can't know as it's EOL & no longer show as *supported*. 

FYI:   A quick check of [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/) show it doesn't look like the main repository has moved; however if using a *mirror*, they can choose to *drop* support anytime after EOL is reached, so you may still need to make the changes mentioned in the EOLUpgrades link I provided, but I'd try *release-upgrading* before making any changes first.

---

### Post by electrosteam on 2022-04-28
guiverc,
Thanks for the prod.

System upgraded to:
Ubuntu 21.10
5.13.0-40-generic.

gdebi opens.

Now to deal with Zoom.

I will do a clean install of 22.04 before 21.10 goes EOL.
Have a great day.

John.

---

### Post by electrosteam on 2022-04-29
Zoom is up and running.

Original problem may have been the settings for Software Sources:
 - 'Ubuntu Software' tab - all the "Downloadable from the Internet' boxes cleared, not ticked.

So I did not get the correct notifications.

As my fingers are the only ones touching this system, it must have been me.

John.

---

