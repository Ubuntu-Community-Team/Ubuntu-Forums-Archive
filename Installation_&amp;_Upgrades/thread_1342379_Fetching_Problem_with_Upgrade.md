---
title: "Fetching Problem with Upgrade"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by The_Fool on 2009-11-30
I am upgrading from Ubuntu 9.04 to 9.10, 64-bit.  The upgrade works until it reaches the "getting new packages" step.  At this point, it stops when fetching file 1307 of 1307.  It says:

Failed to fetch http:// archive.ubuntu.com/ubuntu/pool/main/libs/libsexy/libsexy2_0.1.11-2build1_amd64.deb 503 Service Unavailable [IP: 91.189.88.134 80]

Did this file disappear, did the server disappear, or is the source wrong?

---

### Post by howefield on 2009-11-30
You have a space between "http://" and "archive"

The url is not valid.

Close the space and it should complete.

---

### Post by The_Fool on 2009-11-30
Actually, I did that to show the entire link (part of it would have been missing since the forum would have set it to an actual link).  It is a proper URL inside the error box.

---

### Post by Geoff918 on 2009-11-30
Are you able to manually insert the IP address in-place of the archive name?

Are you able to successfully ping the archive?

Did you think about changing the archive pool you're trying from? (You can change that in Synaptic under preferences)

[http://archive.ubuntu.com/ubuntu/pool/main/libs/libsexy/libsexy2_0.1.11-2build1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/libs/libsexy/libsexy2_0.1.11-2build1_amd64.deb)

It's definitely there.

Maybe try just [http://archive.ubuntu.com/ubuntu/pool/main/libs/libsexy/](http://archive.ubuntu.com/ubuntu/pool/main/libs/libsexy/) and see for yourself.

---

### Post by howefield on 2009-11-30
Ok, in that case, don't know why it is not getting it, but you could manually download the file and double click to install.

[http://archive.ubuntu.com/ubuntu/pool/main/libs/libsexy](http://archive.ubuntu.com/ubuntu/pool/main/libs/libsexy)

The file is there and available.

---

### Post by The_Fool on 2009-11-30
Apparently, the content filter on my router didn't like that the URL contained the word "sex".  Once that was disabled for this computer it downloaded perfectly fine.

---

