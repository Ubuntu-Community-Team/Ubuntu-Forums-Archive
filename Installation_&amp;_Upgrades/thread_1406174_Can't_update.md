---
title: "Can't update"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by dodgingspam2 on 2010-02-13
I have Ubuntu 8.04 Desktop Edition running on my PC. I've had it for some time and it worked great, however recently when I tried to run Update Manager I started to get the following error message:
> W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

Any updates are aborted after that message.

What do I do to update my system?

Thanks.

---

### Post by suseendran.rengabashyam on 2010-02-15
Hi,

Go to Applications > Accessories > Terminal, execute these commands:

```
wget http://archive.ubuntu.com/ubuntu/project/ubuntu-archive-keyring.gpg -O- | sudo apt-key add -

sudo apt-key update

sudo apt-key net-update
```

Now try running the Update Manger and let me know if you get the same error.

---

### Post by MelDJ on 2010-02-15
or if the way the other poster gave did not work, try the link in my sig

---

### Post by dodgingspam2 on 2010-02-17
Suseendran's suggestion took care of the error. However when I try to run Update Manager it does not download anything, saying that the last update was less then an hour ago.

I don't remember downloading and installing any upgrades for months...

---

