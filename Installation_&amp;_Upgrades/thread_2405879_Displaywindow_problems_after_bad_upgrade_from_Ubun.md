---
title: "Display/window problems after bad upgrade from Ubuntu 16 to 18.04"
date: 2018-11-12
forum: Installation &amp; Upgrades
---

### Post by tamj0rd2 on 2018-11-12
During an upgrade from Ubuntu 16 (I think 16.04) to 18.04 a dialog box disappeared so I restarted my computer to try to start the upgrade again. Any time I logged in it would take me back the login screen again.

I ran these commands I found in an Ask Ubuntu thread from the Recovery Ubuntu launch thing to try to finish the upgrade:
> 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get dist-upgrade


I was able to log in but now I have a few display issues for the built in Ubuntu apps (like software updater, terminal etc). Images [https://imgur.com/a/8St0Xil](https://imgur.com/a/8St0Xil)

[LIST=1]
[*]Menu items are squashed together, making them difficult to read
[*]Things like dropdown menus just look like plain text with nothing indicating they're dropdown menus. If you click on it, it shows options that look squashed together like the window menu items
[*]Buttons also just look like plain text
[*]None of the apps have borders anymore
[*]My terminal has changed itself from dark grey to light grey
[/LIST]

I haven't noticed any problems other than the display of the built in Ubuntu apps. I've checked and there aren't any updates for my system. I have these problems regardless of whether I use Unity or Gnome.

Does anyone have any suggestions?

I'm worried about reinstalling because my internet is too slow to redownload the software I'm using and I'll use a lot of personal settings. But if reinstalling is the only way to go, can someone please suggest a way to backup my settings and apps if possible? I already have my documents stored on a separate drive. I'm hoping I don't have to reinstall because so far it only looks like a window problem.

---

### Post by ccerrillo on 2019-07-27
Same problem, did you solve this?

Edit: i solved this with dconf reset -f /

---

