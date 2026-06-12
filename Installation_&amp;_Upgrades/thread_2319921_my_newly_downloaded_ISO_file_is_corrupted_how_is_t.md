---
title: "my newly downloaded ISO file is corrupted how is this possible ?"
date: 2016-04-08
forum: Installation &amp; Upgrades
---

### Post by zap199x on 2016-04-08
i just downloaded ubuntu 14.04 LTS ISO directly from Ubuntu.com through google chrome.
i couldn't load it to startup disk creator so i checked its md5sum and it was wildly different from any md5sum ubuntu.com provided here [http://releases.ubuntu.com/trusty/MD5SUMS](http://releases.ubuntu.com/trusty/MD5SUMS) 
so my question is how is this possible ? i didn't do anything to the iso , i didn't even open it , i just downloaded it a second ago , didn't even restart my PC :confused:

---

### Post by Bucky Ball on 2016-04-08
Try downloading the ISO via a torrent from[ down the page here]("http://www.ubuntu.com/download/alternative-downloads"). Fairly foolproof as the md5sum is checked on the way down.

Don't know why your ISO became corrupted by do know it happens ... :-k

---

### Post by howefield on 2016-04-08
Something has gotten corrupted during download or storage on your disk. There is no built-in checksumming done on http downloads so data can be corrupted for a number of reasons.

To increase your chances of a good download, use the [torrent options]("http://www.ubuntu.com/download/alternative-downloads") as this will check the files as they download.

---

### Post by Bucky Ball on 2016-04-08
Snap! :D

---

### Post by howefield on 2016-04-08
:)

At least we pretty much said the same thing.

---

### Post by slickymaster on 2016-04-08
Yes, it's possible. In particular on poor quality internet connections.

The HTTP protocol does not have any provisions for ensuring data integrity. On transport layer, TCP does have error detection by using a checksum, but that does not account for data being corrupted either before transit, during storage (power failure), and after storage (corrupted hard drive).

---

### Post by zap199x on 2016-04-08
ty guys i downloaded it through torrent and got a md5sum match.

---

