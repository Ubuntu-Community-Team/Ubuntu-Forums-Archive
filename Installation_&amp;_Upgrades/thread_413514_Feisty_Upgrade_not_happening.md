---
title: "Feisty Upgrade not happening"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by OsakaWilson on 2007-04-19
I followed the advice of the sticky post and used the line below to attempt an upgrade to Feisty Fawn. I go the result below, then the Software Updates window opened and told me my system is up to date. It didn't upgrade to Feisty. What's up? I'm using 64bit Edgy now.

$ gksu "update-manager -c"
warning: could not initiate dbus

---

### Post by Fraoch on 2007-04-19
Same thing here.  I also have an update that I haven't been able to apply for about a week - "libpath-class-perl'.  Looks to download, looks to install...but it comes right back.

Has Feisty been released or pushed back a day?  I can't seem to load the Ubuntu page properly so I may be reading a cached version, but it's still saying "Release is tomorrow".

---

### Post by NICU on 2007-04-19
I have the exact same error... Not sure what's causing this.  Lets hope someone can post some handy info.  My system is a generic desktop PC running Ubuntu 6.10.  I have modified my sources.list file to include Beryl and Automatix.  Those are my only changes to that file.

---

### Post by palmerthegeek on 2007-04-19
It has been released, Im downloading from:
[http://cdimage.ubuntu.com/releases/feisty/release/](http://cdimage.ubuntu.com/releases/feisty/release/)
[http://cdimage.ubuntu.com/releases/7.04/release/](http://cdimage.ubuntu.com/releases/7.04/release/)

However I do have the same problem (and error) with the update-manager.

---

### Post by Fraoch on 2007-04-19
I decided to ignore the issue (hopefully it won't come back to get me) and I'm upgrading using these instructions:

[https://help.ubuntu.com/community/FeistyUpgrades](https://help.ubuntu.com/community/FeistyUpgrades)

...which was written 12 minutes *in the future*, BTW.  LOL!

I'll see if things go smoothly.  Crossing fingers!

edit: I notice the link is down now.  Hope it wasn't giving bad advice.  But it advised to go into Systenm - Administration - Update Manager.  The 7.04 update is right at the top.

---

### Post by OsakaWilson on 2007-04-19
I'm using the System/Admin/Update Manager to upgrade my laptop and it seems to be working. The only problem is that it is SLOW. I had it downloading all night and its not even a third complete. It is clean of unofficial applications, so I'm not surprised that its working smoothly.

On my desktop computer, though, is giving me an error message:

[INDENT]Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz) Sub-process gzip returned an error code (1)[/INDENT]

Looks like the server is down.

---

### Post by cogadh on 2007-04-19
The servers have been getting their butts kicked all day and it actually seems to be getting worse. I just had a clean install fail on a machine as it was trying to install apt. It couldn't update the repositories and just hung for a half hour. I finally killed it and started over with a fresh format and now that one is locking up in the same way.

---

### Post by Fraoch on 2007-04-19
Well...things went smoothly here, although quite slowly.  Downloading took 11 hours!

Everything installed and configured successfully though!  No particular issues.  Even my two NTFS partitions automounted - they never did that before.

Also that pesky "libpath-class-perl" update - gone, as I hoped it would.

So, happy camper here.

BTW I guess the good thing about the servers being so slow is it's an indication Ubuntu's getting popular.

---

