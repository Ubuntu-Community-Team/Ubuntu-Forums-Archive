---
title: "Failed to Download Package Files"
date: 2011-08-13
forum: Installation &amp; Upgrades
---

### Post by Mike Henthorne on 2011-08-13
I posted this on the WineHQ Forum and they told me to come here, any ideas?

>I just recently installed Ubuntu on my laptop and  was attempting to install Wine on it this morning. I went through the  proper procedure listed on the site, but once I get back to the Software  Center and hit "install" it gives me an error a second later saying  "Failed to Download Package Files. Check your Internet connection." I  know that my connection is working fine, so does anyone else have any  ideas? 
 
-Mike

---

### Post by realzippy on 2011-08-13
Welcome.
open a terminal,run 
```
sudo apt-get update
```

errors?

---

### Post by Mike Henthorne on 2011-08-13
yes

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0

Otherwise nothing else

---

### Post by realzippy on 2011-08-13
I think launchpad is experiencing problems or something...try again later?

---

### Post by Mike Henthorne on 2011-08-13
Fixed the problem. I got the PUB_KEY from the keyserver and now Wine is installing no problem.

---

### Post by realzippy on 2011-08-13
Fine.
Please set thread as solved then (threadtools).

---

### Post by realzippy on 2011-08-22
Just cleaning up my subscribed threads.
Please set thread as solved (ThreadTools)...thanks

---

