---
title: "Yelp not opening external documents after upgrade"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by keyboardashtray on 2007-10-19
When I try right clicking some HTML documents and selecting "open with yelp", Yelp opens for a second down in the taskbar, then immediately closes. 

I also have these documents bookmarked in yelp, and the same thing happens when I use the bookmarks from withing yelp while it is already running: it closes/crashes yelp.

Anyone have any ideas?

Edit: This is what the terminal says, when I've opened Yelp from in the terminal, and then use the bookmark:

```
(yelp:7183): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(yelp:7183): atk-bridge-WARNING **: IOR not set.

(yelp:7183): atk-bridge-WARNING **: Could not locate registry

(yelp:7183): GLib-CRITICAL **: g_filename_to_uri: assertion `filename != NULL' failed
Segmentation fault (core dumped)
```

But I don't know how I'd go about getting the error output from when I right click the file itself from my home directory, and select "open with Yelp", maybe it'd just be the same thing though.

Edit: Launchpad link: [https://bugs.launchpad.net/ubuntu/+source/yelp/+bug/157762](https://bugs.launchpad.net/ubuntu/+source/yelp/+bug/157762)

---

