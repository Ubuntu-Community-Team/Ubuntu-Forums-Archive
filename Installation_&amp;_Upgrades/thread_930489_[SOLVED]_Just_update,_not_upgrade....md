---
title: "[SOLVED] Just update, not upgrade..."
date: 2008-09-26
forum: Installation &amp; Upgrades
---

### Post by erik.almen on 2008-09-26
Hi!

I've just done a fresh install of Ubuntu 7.10 but when I try to update (through update manager) everything I get is the "upgrade to Ubuntu 8.04"-option. Is it possible to just get the usual updates?

(I don't wish to upgrade since I've got a RT61 wlan card which quite often crashes the 8.04. There doesen't seem to be a solution that works for everyone but from what I've read it's working in 8.10. Just need a non-crashing os until the 8.10 release:))


Thanks
/Erik

---

### Post by tommcd on 2008-09-26
Just click on: system > administration > update manager, if you only want the updates for Ubuntu 7.10.
Also, have a look at enabling extra repositories for getting extra software:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
Also see:
[https://help.ubuntu.com/community/KeepingUbuntuUpdated?action=fullsearch&context=180&value=updating+ubuntu&titlesearch=Titles](https://help.ubuntu.com/community/KeepingUbuntuUpdated?action=fullsearch&context=180&value=updating+ubuntu&titlesearch=Titles)
[https://help.ubuntu.com/community/Repositories/Ubuntu?highlight=(updating)|(ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu?highlight=(updating)|(ubuntu))
You should upgrade (or do a clean install) to Hardy 8.10 at some point though, for newer software, kernel, video drivers, xorg, etc.

Oh, and welcome to the Ubuntu Forums!

---

### Post by lisati on 2008-09-26
Upgrading is optional. There's always the notification icon if there are updates available, and you don't have to go to update manager if there aren't any. All you have to do is click on the "install updates" button if it's not greyed out.

---

### Post by amac777 on 2008-09-26
I am running Ubuntu 7.10 and I get new updates for it occasionally. They show up in the update-manager like normal and you can install them without upgrading to 8.04. If you haven't got any yet, it might be because the update manager has not checked for new updates yet. Probably just need to wait a bit and then it will remind you that updates are available. If you're impatient, you could try running "sudo apt-get update" from the command prompt. That will update your repository package lists and then update-manager should "see" that there are newer version of some software available.

---

### Post by robert shearer on 2008-09-26
I have not used this but believe it will work...
Open Synaptic and click on Settings=>Preferences

Go to the far right tab = Distribution

Change the radio button to  "always prefer the installed version"

Hover the cursor over this to see the caveats involved.!!

If you're happy then Apply.

EDIT this might be a better solution..

Open Synaptic and select Settings=>Repositories
Click on the Updates tab and use the selection arrows in the Release upgrade box to choose Never.

---

### Post by erik.almen on 2008-09-26
Thanks guys!

I found the problem, in preferenses -> Software Sources every box was unchecked (including security and recommended updates). Kind of weird for a fresh install, but I guess the Ubuntu team want everybody to upgrade...

---

