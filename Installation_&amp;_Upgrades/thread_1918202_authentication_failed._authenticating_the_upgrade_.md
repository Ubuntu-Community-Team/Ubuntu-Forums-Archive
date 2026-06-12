---
title: "authentication failed. authenticating the upgrade failed. there may be a problem with"
date: 2012-01-31
forum: Installation &amp; Upgrades
---

### Post by ravilive on 2012-01-31
I have got my new ubuntu laptop from Dell(Vestro).
I am exiting but it came with 10.10 version and when i am trying to upgrade to latest version it is giving my following error.


authentication failed. authenticating the upgrade failed. there may be a problem with the network or with the server

Please help me..my network and internet is fine and can upgrade other packages but not able to do release upgrade...

---

### Post by Paddy Landau on 2012-02-01
If this is a brand new computer with no data on it, I would recommend that you instead [download the latest ISO]("http://www.ubuntu.com/download/ubuntu/download"). Burn it to CD (or, preferably, USB flash). Boot from it to check that it all works OK -- check your Internet connection and anything else you need to check. If it all works, install it over your 10.10 installation.

A clean installation is usually easier and less error-prone than an upgrade.

---

### Post by ravilive on 2012-02-10
This is brand new Laptop with ubuntu preloaded on it..
I want to keep original build as it was came with some Dell utilities..
I found temporary work around to upgrade the ubuntu from the command prompt and now I am on 11.10.
but problem still persist. I tried to Dell ubuntu support but they redirect me to UK ubuntu specialist.

---

### Post by Paddy Landau on 2012-02-10
Here is what I suggest -- but you will need an external hard drive.

[LIST=1]
[*]Ensure your external hard drive can connect properly to your computer.
[*]Download [CloneZilla]("http://www.clonezilla.org/") and burn it to CD (or, preferably, to a USB flash disk).
[*]Boot from the CloneZilla CD (or USB flash disk, or even your external hard drive if you know how to do that).
[*]Do a full backup of your *entire* hard drive onto your external hard drive using CloneZilla. (It will back up into a folder on your external hard drive.)
[/LIST]
Then go ahead and install 11.10 on your computer. If it doesn't work, use CloneZilla to restore your entire hard drive, which will get you back to before you tried to install 11.10.

Two important things:

[LIST]
[*]**Back up all your data first** (otherwise you can't restore your data after you install 11.10).
[*]This presumes that a fresh installation will give you what you want without the Dell utilities. Alternatively, ask Dell how to download those utilities, so that you can install them after you have successfully installed 11.10.
[/LIST]

---

