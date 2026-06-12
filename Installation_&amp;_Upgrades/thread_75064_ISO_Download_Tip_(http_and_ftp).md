---
title: "ISO Download Tip (http and ftp)"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by jdtanner on 2005-10-13
(repost from the developnment archive)

Just a tip for those of you downloading via ftp or http (tut tut...you should be using bittorrent ;-)). Open a terminal and use the following command

wget -c [http://releases.ubuntu.com/5.10/ubun...stall-i386.iso](http://releases.ubuntu.com/5.10/ubun...stall-i386.iso)

making sure that the url is a local mirror (see [http://www.ubuntu.com/download/](http://www.ubuntu.com/download/) for a list of mirrors). This command will allow you to resume a broken download without you having to start from the beginning.

Once you have the .iso head over to [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto) to see how to get it onto a CD/DVD.

Cheers,
John

---

