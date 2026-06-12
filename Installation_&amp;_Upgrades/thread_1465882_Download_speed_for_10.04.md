---
title: "Download speed for 10.04?"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by glastonbury on 2010-04-29
First post here ... 

Just want to make sure I am not crazy. I am downloading the upgrade right now (9 p.m. time Eastern U.S.), and not getting much faster than 31 kbps on the download. Regular web pages are loading quickly as normal. Are the Canonical servers overtaxed?

---

### Post by bdamon on 2010-04-29
If you use the torrent download you will have much better luck. Took me less than 20 minutes to download both the 32 and 64 bit iso's both at the same time.

---

### Post by kstrike155 on 2010-04-29
I wouldn't doubt it.  It's release day for 10.04 and everyone wants it.  That's why you should be using [BitTorrent]("https://help.ubuntu.com/community/BitTorrent").  It lightens the load on their servers, and you get it much faster.  Plus, you give back to the community that has given so much.

[i386 Torrent]("http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.iso.torrent")

[AMD64 Torrent]("http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent")

Brian

---

### Post by glastonbury on 2010-04-29
Thanks. Since this is an upgrade from 9.10, how will the process differ using the ISO vs. the update manager?

---

### Post by kstrike155 on 2010-04-29
Make sure you download the ALTERNATE version for an upgrade.

[AMD64 Torrent (Alternate)]("http://releases.ubuntu.com/10.04/ubuntu-10.04-alternate-amd64.iso.torrent")

[i386 Torrent (Alternate)]("http://releases.ubuntu.com/10.04/ubuntu-10.04-alternate-i386.iso.torrent")

Insert the disk or mount the ISO with your system already booted.  It should come up with a window and automatically ask to upgrade, but if it doesn't hit Alt-F2 and type: gksu "sh /cdrom/cdromupgrade".

Be sure to select "No" when it asks to include the latest updates from the internet.

Good luck.

---

### Post by glastonbury on 2010-04-29
Thanks. Just curious -- why do I not want the latest updates from the Internet? Weren't there some last-minute issues dealt with that didn't make it onto these images?

---

### Post by shannon.jacobs on 2010-04-29
Why isn't a transparent (as in mostly hidden) version of BitTorrent the default download protocol? It's not like they would have to develop a new technology to do it. Nor is this a new problem. This overload of the servers takes place with EVERY upgrade cycle. 

I already know about BitTorrent, so I was able to quickly make my CD version this morning, but even with the CD it took a long time to do the fresh install in a VM here, apparently while it was waiting for some extra files to download. (Then I encountered the first problem--but maybe a reboot will take care of it.) Meanwhile, another machine is attempting the upgrade behind me--with a current estimate of 22 hours for the files, though that's one of the lowest fluctuations. (Nope, the reboot didn't do it... Can't even log in. So let's try the full restart, eh?)

In conclusion, I think that Ubuntu could be MUCH more successful if they would try to learn from their problems. Heaven help the prospective new users. 

(I've been using Ubuntu for a couple of years now, but I have to say the last few upgrades have been MORE painful each time, not less painful, and if this one goes as badly, it may be the camel that breaks my straw back... Last time (Koala) the sound-related problems were terrible on MANY machines.)

---

### Post by kstrike155 on 2010-04-29
> **glastonbury said:**
> Thanks. Just curious -- why do I not want the latest updates from the Internet? Weren't there some last-minute issues dealt with that didn't make it onto these images?

Because if you do the updates from the internet then you're sitting there waiting for it to download from the Ubuntu web servers!  You'll be right back in the same boat you were in earlier.

---

### Post by kstrike155 on 2010-04-29
> **shannon.jacobs said:**
> (I've been using Ubuntu for a couple of years now, but I have to say the last few upgrades have been MORE painful each time, not less painful, and if this one goes as badly, it may be the camel that breaks my straw back... Last time (Koala) the sound-related problems were terrible on MANY machines.)

I agree.  The servers get hammered harder and harder each time.  They might have some success with a Java-based BitTorrent (or other peer-to-peer protocol) instead of downloading the ISOs directly.

It sucks that there are so many downloading ISOs because this is all I'm trying to do:
> 
47% [2 smbfs 956kB/2,026kB 47%]                    ** 1,441B/s 12min 22s**

Yeah.  That's 1.4KB/s. :(

Brian

---

