---
title: "Serious Upgrade problem"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by yoman82 on 2010-02-24
When I try to upgrade to 10.04, I succeed in clicking the start button and disabling the karmic sources, but an error is encountered on the next step, namely:
Error during update

A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.


This has been going on for days, and I can use update-manager normally. 
Below it, it says:
```

W:GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DA360C64005E0276, W:Failed to fetch http://www.ksplice.com/apt/dists/lucid/ksplice/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://www.ksplice.com/apt/dists/lucid/ksplice/source/Sources.gz  404  Not Found
, W:Failed to fetch http://linux.dropbox.com/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://linux.getdropbox.com/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://deb.playonlinux.com/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/lucid/non-free/binary-amd64/Packages.gz  404  Not found
, W:Failed to fetch http://repo.mdc.ru/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/banshee-unstable-team/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/shutter/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/markuz/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/shanepatrickfagan/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/specto/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/rvm/mplayer/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/chmsee/karmic/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/ibus-dev/ibus-1.2-karmic/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/tualatrix/gloobus/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/blueman/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/tweenk/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/njpatel/clutter-edgers/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/dylanmccall/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/spicebird/test-build/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/osd-lyrics/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/pdfmod-team/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/moblin/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/exaile-devel/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/jonabeck/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/alex-hunziker/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/banshee-team/banshee-unstable/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/bjfs/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/coolwanglu/scanmem/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/dockbar-main/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/dr-akulavich/qwit/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/gmpc-trunk/gmpc-stable/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/invernizzi/gtg-daily/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/gtg/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/sunab/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/keepassx/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/linux-deepin/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/listen-devel/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/meerkat/stable/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/meerkat/testing/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/qgis/unstable/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/qutim/qutim/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/segler-alex/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/firerabbit/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/xsisqox/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by snowpine on 2010-02-24
You need to comment all those 3rd party software sources out of your sources. They are not official Ubuntu repositories and probably aren't available for Lucid yet.

```
gksu gedit /etc/apt/sources.list
```

Type a # symbol at the start of every line that is giving you trouble.

---

### Post by yoman82 on 2010-02-25
This worked, but could this possibly be automated? I have a LOT of sources, and it was VERY tedious. I did not have to do this for previous upgrades.

---

### Post by zebtonson on 2010-03-31
You could iterate commenting out half, and narrowing it down. e.g. for 60 sources 

60/2  (try reloading and see if it breaks... then you know what side it's on commented or not)  so it should take you about 5 times or so.

---

### Post by snowpine on 2010-03-31
> **yoman82 said:**
> This worked, but could this possibly be automated? I have a LOT of sources, and it was VERY tedious. I did not have to do this for previous upgrades.

You could simply delete them all, if you don't think you'll need them in Lucid. That would be a lot quicker obviously. I suggested the commenting method originally in case you wanted to try and add them again after the update (I would not personally recommend it).

---

### Post by eris23 on 2010-04-10
Go into software sources and uncheck tracker-unstable

Then, in a terminal:
sudo add-apt-repository ppa:tracker-team/tracker-unstable

In believe (through trial and error) that that one is responsible for NO_PUBKEY DA360C64005E0276

It believe that I had ubuntu-tweak add that repository

---

### Post by LordDelta on 2011-02-13
Um, guys? What happened here...

Seems like the maverick repository went missing...

My Update Manager and Synaptic Manager both tell me they can't read the reps, and with good reason, if I try go to those urls there's no directory there.

Just wondering if this is a periodic issue, or something pretty serious managed to corrupt somewhere....

To be specific, it looks like the launchpad meerkat main reps are missing.

---

### Post by midwayplane on 2011-02-26
I've been wondering this myself.  It's been happening for months now.

---

