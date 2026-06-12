---
title: "update manager"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by gillesg06 on 2010-09-23
I got this pop up???  what can I do ??

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4EA3A911D48B8E25

Thank's for your time:guitar:

---

### Post by plucky on 2010-09-24
> **gillesg06 said:**
> I got this pop up???  what can I do ??

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4EA3A911D48B8E25

Thank's for your time:guitar:

From [Here](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/59304)

```
gpg --keyserver keyserver.ubuntu.com --recv 4EA3A911D48B8E25
gpg --export --armor 4EA3A911D48B8E25 | sudo apt-key add -
```

Good Luck

---

### Post by gillesg06 on 2010-10-20
Thank's plucky.

---

