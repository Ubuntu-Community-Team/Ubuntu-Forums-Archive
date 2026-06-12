---
title: "Where are the updates stored?"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by rishabh_destiny on 2010-05-22
I have Ubuntu 10.04 on my two machines. I installed the restricted extras on one machine along with all other updates. Is it possible to just copy those updates into the other machine, without wasting time and bandwidth in entire new update?

If not, please tell me for atleast restricted extras.

Thanks

---

### Post by wojox on 2010-05-22
Look in **/var/cache/apt/archives**. They should be in there unless you've cleaned them out.

---

### Post by mac9416 on 2010-05-22
Hi,

The updates are stored in /var/cache/apt/archives. You can copy the .deb files from there to a flash drive and from the flash drive to the /var/cache/apt/archives directory on the target machine.

However, because you may not have run 'apt-get update' on the target machine, it may not know that ubuntu-restricted-extras is available. If that is the case, you'll want to look at [Keryx]("http://keryxproject.org"), which will handle updating APT for you.

---

### Post by rishabh_destiny on 2010-05-22
Thanks. Please clarify one more thing, do I have to run the debian files which I'll copy in the flash drive, or just paste them in the target folder?

---

### Post by wojox on 2010-05-22
Just copy the whole package.

---

### Post by rishabh_destiny on 2010-05-22
Thanks, wojox :)

---

### Post by wojox on 2010-05-22
> **rishabh_destiny said:**
> Thanks, wojox :)

Your welcome. :)

---

