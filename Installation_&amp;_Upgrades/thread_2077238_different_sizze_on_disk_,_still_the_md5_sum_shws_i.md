---
title: "different sizze on disk , still the md5 sum shws it correct."
date: 2012-10-28
forum: Installation &amp; Upgrades
---

### Post by gs777 on 2012-10-28
I have downloaded ubuntu-12.04.1-desktop-amd64.iso using bittorrent using windows  client utorrent.I used this torrent file [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-amd64.iso.torrent](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-amd64.iso.torrent). Size of the file that is listed on the server is 694 MB. But the file that I have got after download is of the size 728 MB.I have verified the md5sum and found that the downloaded file have same md5sum as listed in this file-  [http://releases.ubuntu.com/12.04.1/MD5SUMS](http://releases.ubuntu.com/12.04.1/MD5SUMS). Please tell me if the file is safe to use .

---

### Post by Wim Sturkenboom on 2012-10-28
Yep; although it is theoretically possible to get the same md5sum for two files, the chances in practice are absolutely minimal that it will happen.

'size on disk' does not mean much as it depends on the block size used and is therefore rounded to the number of blocks that fit the complete file. E.g. create a small file of a few bytes in windows and you will see that the size on disk will (probably) be 4kB.

---

### Post by gs777 on 2012-10-29
thank you .This solved my puzzle.

---

### Post by Wim Sturkenboom on 2012-10-29
Great; you can mark the thread as solved using the thread tools just above the first post on this page.

---

