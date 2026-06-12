---
title: "Bittorrent broken on Edgy?"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by uid0 on 2006-11-02
After a clean install of Edgy, I discovered that the Bittorrent client appears to have broken.  I can start a single download going without any problems but when I go to start subsequent downloads I get an "address already in use" error.  Once the running download is finished I can click retry and the new download starts properly.  Anyone else notice this?

---

### Post by treb0r on 2006-11-07
Mine is broken too. I had a load of half finished torrents that I tried to resume after an edgy upgrade.  The torrent files are recognised, it asks me if I want to resume, then nothing. No activity at all. Won't work with new torrents either.

Help!

---

### Post by treb0r on 2006-11-07
Actually, bt works if if the torrent is opened directly from firefox, and not saved to disc first...

---

### Post by lomomo on 2006-11-09
I can confirm this bug, I download one torrent but when I try to download a second one I get the 'Address already in use' error. So I've to download torrents one by one.

---

### Post by dsmith on 2006-11-09
very same issue with multiple downloading of torrents/ 1 at a time works / 'address in use' error on opening 2nd item.

tried reinstalling bt but no change.

any suggestions?

---

### Post by dsmith on 2006-11-11
found solution here:

[https://features.launchpad.net/distros/ubuntu/+ticket/2364](https://features.launchpad.net/distros/ubuntu/+ticket/2364)

all is good now!

---

