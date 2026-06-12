---
title: "Running uTorrent 2.1 Beta with video streaming in Lucid Alpha 1"
date: 2009-12-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2009-12-18
Hi All,

Tried uTorrent 2.1 Beta in wine in Lucid. Its working perfectly. Love this torrent client. I wish if they could get a native version.

SK.

---

### Post by cariboo on 2009-12-18
From the µTorrent faq:

> 2. Is µTorrent open source?
No. It is not likely to become open source ever.

---

### Post by A_T on 2009-12-18
Why is uTorrent better than the Linux clients like Deluge?

---

### Post by Regenweald on 2009-12-18
> **soham_1207 said:**
> Hi All,

Tried uTorrent 2.1 Beta in wine in Lucid. Its working perfectly. Love this torrent client. I wish if they could get a native version.

SK.

Don't need a native client, works perfectly in wine.

> **A_T said:**
> Why is uTorrent better than the Linux clients like Deluge?

Don't really know, just is :D

---

### Post by A_T on 2009-12-18
There has to be a really good reason for me to put up with those fugly wine fonts.

---

### Post by BrokenKingpin on 2009-12-18
Transmission is as good as uTorrent and come installed with Ubuntu. I never understood people relying on wine so much. If you use that many Windows apps, then just use Windows.

---

### Post by Tibuda on 2009-12-18
> **cariboo907 said:**
> From the µTorrent faq:

So is Skype, Nero, VMWare, Adobe Flash Player, Adobe Reader, NVIDIA drivers... They don't need to open the source to release a Linux version. They need to port it, tough.

EDIT: This is the relevant question in their FAQ:
> [url="http://www.utorrent.com/faq#faq3"]3. Is there a Linux or Mac version?

The OSX port is in progress. A Linux port is currently not planned for the future.[/url]

---

### Post by alphaniner on 2009-12-18
> **BrokenKingpin said:**
> Transmission is as good as uTorrent and come installed with Ubuntu.

Sorry, no.  Transmission is a solid client, but the lack of intelligent queuing makes it incomparable to uTorrent.  Otherwise, I would agree.

---

### Post by donniezazen on 2009-12-18
> **cariboo907 said:**
> From the µTorrent faq:

Yeah, we don't want them to open source it, we just want them to build a Linux version.

> **A_T said:**
> Why is uTorrent better than the Linux clients like Deluge?

> **A_T said:**
> There has to be a really good reason for me to put up with those fugly wine fonts.

I do not have concrete data to prove it but in my observation uTorrent is fast, clean and sleek. It's UI is very simple and it is very small standalone software unlike Vuze.

---

### Post by pt123 on 2009-12-18
The best part of uTorrent is that it was bought up by BitTorrent Inc.
> Los Angeles &#8211; - BitTorrent Founder and CEO Bram Cohen and Motion Picture Association of America, Inc. (MPAA) Chairman and CEO Dan Glickman announced today that the motion picture industry and BitTorrent, Inc. are collaborating with the goal of inhibiting film piracy.
[http://torrentfreak.com/bittorrent-and-mpaa-join-forces/](http://torrentfreak.com/bittorrent-and-mpaa-join-forces/)

---

### Post by lovinglinux on 2009-12-18
uTorrent is not better than Deluge or Ktorrent, which are the two clients I recommend for Gnome and KDE respectively. Besides it is not open source and needs Wine. So I don't see any reason to use it, unless you can't get rid of your old Windows habits.

About the video streaming, that is a lot of crap. What it does is to prioritize the first pieces of the torrent content and download it sequentially, which is extremely bad for the swarm. Imagine that everyone decides to use it. Then most of the peers on a swarm will be downloading the first pieces of the file, so when the streaming reaches the final segments will become much harder to find peers with available pieces to upload to you. 

BitTorrent streaming technology works with you have a server seeding the content and the peers just helping to reduce the load. The BitTorrent protocol is fast because you can get any pieces of the files from anyone in the swarm, if everyone downloads the files sequentially, it would be much slower.

Not to mention the fact that most users using streaming will probably be those that can't wait a couple of hours for a download and can't wait to download another video after completing the first one, so they would probably stop seeding after the streaming completes, which makes the situation even worse.

---

