---
title: "installation problems"
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by Sunokw72 on 2011-01-31
Hi, I have just installed the newest version of ubuntu (10.10 the maverick meerkat) and im struggling installing any programs, wine and vlc arnt appearing on synaptic package manager and anything i try to do in either the command promt or ubuntu software centre doesnt work either. On the command promt when i follow the commands as seen on various tutourials the command promt comes back with an error. VLC example given below. 

sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-plugin-vlc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Unable to locate package vlc
E: Unable to locate package vlc-plugin-pulse
E: Package 'mozilla-plugin-vlc' has no installation candidate

this message is very similar to any other software i try to install manually.
any information as to how to sort this out would be great. :)

---

### Post by Rubi1200 on 2011-01-31
Hi and welcome to the forums :-)

If you have just installed, run ```
sudo apt-get update && sudo apt-get upgrade
``` before trying to install new packages.

---

### Post by Sunokw72 on 2011-02-01
Okay, ive done that. But I am still having problems with the synaptic package manager. Im trying to install wine and vlc but i cant find either on the search. However when i check which version of wine i have vie command propt it tells me i have wine 1.0 and 1.2. I just dont understand why i cant then see it on synaptic package manager.

---

### Post by weblordpepe on 2011-02-01
Hi there. 

Have you enabled the 'universe' or 'multiverse' categories? 

The repositories are divided into different categories, with each having different levels of support. The 'main' categoriy is stuff which caninical supports totally. The universe & multiverse ones are kinda like community maintained.

Its under the options in Synaptic. I can't recall exactly where to find the options & I can't look cos I'm currently upgrading to 10.10 myself :P

---

### Post by kansasnoob on 2011-02-01
This might help you:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Be sure Main, Universe, Restricted, and Multiverse are enabled:

[https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=SoftwareSources-UbuntuSoftware.png](https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=SoftwareSources-UbuntuSoftware.png)

Enable the Partner repo:

[https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=SoftwareSources-Partner.png](https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=SoftwareSources-Partner.png)

---

### Post by Sunokw72 on 2011-02-01
Yep they are all enabled. Also when using the software centre it gives a message for both vlc and wine that they are not compatable with my type of computer. My laptop is an acer extensa 5620Z and is a few years old but i dont see how that has anything to do with it. 

any other suggestions??

---

