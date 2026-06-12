---
title: "Strange problem with all IM applications ---"
date: 2010-04-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jerrynewt on 2010-04-18
If this post is on the wrong forum, please let me know. I am using my laptop (specs in signature) here in Fort Worth, Tx -- while on a job. Been here for about 4 months now and just began experiencing a problem I have never had before. All IM programs ( empathy, gyachi, amsn, and even pidgin) can no longer connect. I get network error notification on all of them. Accessing internet via ethernet cable (broadband provided by the hotel). However when I connect to the internet via my usb760 Verizon aircard, they all hook up just fine -- no problems at all.
All updates work just fine with ethernet cable and although speed isn't all that great (50-200 KB/s) it works ok. Only additional problem is when trying to add public key via terminal the download speed falls to zero and key will not download.
Sorry for the long post but just wondering if I inadvertently did something to mess up the eth0 wired connection. Thanks for the time.

---

### Post by jerrynewt on 2010-04-19
bump

---

### Post by bash on 2010-04-19
If I understand this correctly and the IM apps only **don't** work when connected via the Hotel "Internet", then the Hotel is probably blocking the ports that the IM protocols are using.

---

### Post by jerrynewt on 2010-04-19
Yes that seems to be the case. Would this also affect the problem with getting the public key downloaded, and updates stalling at "waiting for headers" for long periods of time? Guess I can try to change the ports on the IM settings and see what happens. Thanks for the response.

---

### Post by jerrynewt on 2010-04-19
Got it. Changing the port number worked just fine. Dunno why the hotel is blocking the ports I normally use for IM's but oh well -- golden now. Thanks for the nudge.

---

