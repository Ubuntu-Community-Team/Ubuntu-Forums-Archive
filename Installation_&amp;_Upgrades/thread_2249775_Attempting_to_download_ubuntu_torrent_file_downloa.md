---
title: "Attempting to download ubuntu torrent file downloads DVD image itself"
date: 2014-10-24
forum: Installation &amp; Upgrades
---

### Post by prshah on 2014-10-24
Hello,

I am trying to download Utopic torrents from [http://releases.ubuntu.com/](http://releases.ubuntu.com/) ; however, clicking on the (eg) [http://cdimage.ubuntu.com/xubuntu/releases/utopic/release/xubuntu-14.10-desktop-i386.iso.torrent](http://cdimage.ubuntu.com/xubuntu/releases/utopic/release/xubuntu-14.10-desktop-i386.iso.torrent) link downloads the entire DVD image itself, rather than the torrent file!

(also for lubuntu, xubuntu, etc). All browsers ; firefox, chromium, etc.

Am I missing something? Think it's an error at the server end; How do I alert the relevant people?

---

### Post by ian-weisser on 2014-10-24
Website bug report: [https://bugs.launchpad.net/ubuntu-website](https://bugs.launchpad.net/ubuntu-website)

---

### Post by prshah on 2014-10-24
> **ian-weisser said:**
> Website bug report: [https://bugs.launchpad.net/ubuntu-website](https://bugs.launchpad.net/ubuntu-website)

Cheers, bug report #1385424 filed.

[https://bugs.launchpad.net/ubuntu-website/+bug/1385424](https://bugs.launchpad.net/ubuntu-website/+bug/1385424)

Regards

---

### Post by ajgreeny on 2014-10-24
I have just tried this and the torrent file (44KB) downloaded as it should have, not the whole .iso file.

Has the problem been sorted or did you click on the wrong link? There is a torrent download link on the far left of the line for each torrent file which does not download the torrent file itself but goes to a download link for the .iso file.

---

### Post by ian-weisser on 2014-10-24
I confirmed prshah's report. The link *was* wrong.
However, it's now fixed.

Hooray for fast responses to bug reports.

---

### Post by prshah on 2014-10-24
> **ian-weisser said:**
> I confirmed prshah's report. The link *was* wrong.
However, it's now fixed.

Hooray for fast responses to bug reports.

Yes, fixed now. Thanks for the confirmation. Cheers.

---

### Post by prshah on 2014-10-24
> **ajgreeny said:**
> 
Has the problem been sorted or did you click on the wrong link?

Apparently the problem has been sorted. For the record, I was not clicking on the link; I was leeching all torrent files using wget ; ubuntu torrents downloaded fine, but derivative torrent links had a problem.

```

cat scripts/getallubuntu.sh
#!/bin/bash

# Get all Ubuntu / Variants Torrents

# check env overrides
[ -z "$LOC" ] && LOC=/content/torrents
[ -z "$URL1" ] && URL1=releases.ubuntu.com
[ -z "$URL2" ] && URL2=cdimage.ubuntu.com
[ -z "$UVER" ] && UVER="utopic"

pushd $LOC

echo $URL1/$UVER
wget -r -np -nd -nv -A.torrent --wait=1 -e robots=off --reject="index.html*" $URL1/$UVER/

echo $URL2/$UVER

for lvar in xubuntu kubuntu ubuntu-gnome ubuntustudio ; do echo $lvar ; wget -r -np -nd -nv -A.torrent --wait=1 -e robots=off --reject="index.html*" $URL2/$lvar/releases/$UVER/release/ ; done ;

# == end

```

---

