---
title: "Failed to fetch (Failed to download repository information)"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by linuxsyst on 2011-05-02
Update manger:
```
Failed to download repository information

Check your Internet connection.

W:Failed to fetch http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/natty/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

```

when I do this: ```
sudo apt-get update
``` in terminal it also gives me this: ```
W: Failed to fetch http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
``` 

Can you help me please.

---

### Post by dino99 on 2011-05-02
the "source" might not exist, so open synaptic third parties repo to uncheck or remove the "source" line, then update again

---

