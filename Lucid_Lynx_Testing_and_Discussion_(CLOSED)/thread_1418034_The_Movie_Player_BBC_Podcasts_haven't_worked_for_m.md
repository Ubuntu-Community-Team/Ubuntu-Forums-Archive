---
title: "The Movie Player BBC Podcasts haven't worked for months"
date: 2010-02-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Robin Nixon on 2010-02-28
This isn't Lucid specific but I'm mentioning it here because hopefully somebody working on it will fix the problem for Lucid, which will then correct it for all versions.

Anyway, The Movie Player used to show a selection of BBC podcasts up until about six months ago. Since then when you click the drop down menu on the right hand side it only reports "*Could not connect to server*".

I think the likely problem is that URLs may have changed, so it should be dead easy to fix. For example, here are a few RSS feeds that can be used.

News: [http://downloads.bbc.co.uk/podcasts/radio/newspod/rss.xml](http://downloads.bbc.co.uk/podcasts/radio/newspod/rss.xml)
World Service: [http://downloads.bbc.co.uk/podcasts/worldservice/docarchive/rss.xml](http://downloads.bbc.co.uk/podcasts/worldservice/docarchive/rss.xml)
Best of Chris Moyles: [http://downloads.bbc.co.uk/podcasts/radio1/moyles/rss.xml](http://downloads.bbc.co.uk/podcasts/radio1/moyles/rss.xml)
Fighting Talk (sport): [http://www.bbc.co.uk/fivelive/programmes/fightingtalk_podcast.xml](http://www.bbc.co.uk/fivelive/programmes/fightingtalk_podcast.xml)

And there are plenty more here: [http://www.podcastingnews.com/forum/link_254.htm](http://www.podcastingnews.com/forum/link_254.htm)

---

### Post by gnomeuser on 2010-02-28
Nope, the BBC cut off access

[http://feeds.arstechnica.com/~r/arstechnica/index/~3/ZeZ2IXoHXM8/bbc-blocks-open-source-software-from-iplayer-video-service.ars](http://feeds.arstechnica.com/~r/arstechnica/index/~3/ZeZ2IXoHXM8/bbc-blocks-open-source-software-from-iplayer-video-service.ars)

---

### Post by Robin Nixon on 2010-02-28
> **gnomeuser said:**
> Nope, the BBC cut off access

[http://feeds.arstechnica.com/~r/arstechnica/index/~3/ZeZ2IXoHXM8/bbc-blocks-open-source-software-from-iplayer-video-service.ars]("http://feeds.arstechnica.com/%7Er/arstechnica/index/%7E3/ZeZ2IXoHXM8/bbc-blocks-open-source-software-from-iplayer-video-service.ars")

No, that's was about the iPlayer. The podcasts are all available outside of the iPlayer - I listed some URLs in my post. This happened when the BBC reorganized their podcasts into a single front end at [http://www.bbc.co.uk/podcasts/](http://www.bbc.co.uk/podcasts/) - however that's only a frontend and the XML feeds are still all available.

---

### Post by mc4man on 2010-02-28
here's a bug report on if you wish to add/affects me ect.
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/528728](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/528728)

---

### Post by phenest on 2010-02-28
> **Robin Nixon said:**
> No, that's was about the iPlayer.

If you're referring to the BBC plugin for Totem, then you never read that report. However, the breakage in that plugin might only be a bug.

---

