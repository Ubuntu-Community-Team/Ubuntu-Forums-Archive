---
title: "Xubuntu checksums do not match"
date: 2011-12-18
forum: Installation &amp; Upgrades
---

### Post by joseelsegundo on 2011-12-18
I've been trying to get a ISO for Xubuntu 11.10 AMD64, however when I do any of the checksums they do not match the checksum provided.

For instance, for xubuntu-11.10-alternate-amd64.iso I get:

```

md5sum (published): 52cd07c95fb4788538b385cc02f7e7dc
md5sum (observed):  fe6ba29abf64947714a45cf5d4bc4da6

sha1sum (published): be84ceef3a1e459c75a2387f0552ec92b2080d0b
sha1sum (observed): c09b5731c15e9045ee3bdabeda90137736cfa48d

sha256sum (published): 491f3e644e52457d401aa74ba9751f14b774ab72d083e0a37b6abdda1f50aa79
sha256sum (observed): 762c9e8d4fe385fd3e3c87508f75e8f65468c0a8fb720a55923c2ae8c2c4892f

```

The timestamps for the checksum files are October 13, 2011 and the timestamp for xubuntu-11.10-alternate-amd64.iso is October 11, 2011 so you would think that there would have been plenty of time to notice this.

I've done the download directly, and also with a torrent but I get the same result.

I can't find any contact info for the admin to report this (if this is indeed an error). 

Is anyone else seeing this?

---

### Post by coldraven on 2011-12-18
I don't know for 64bit but I downloaded the 32bit Alt install two days ago (via torrent) and the md5sum is correct.

---

### Post by joseelsegundo on 2011-12-18
Well I was able to get an ISO downloaded for the desktop install that matched the md5sum so I'm going to roll with that. 

Interestingly, I had left the torrent open in my client for the alternate install and later saw it reported an error. I'm don't know if that lends any information as to whether it is something on my end or at the mirror....

---

