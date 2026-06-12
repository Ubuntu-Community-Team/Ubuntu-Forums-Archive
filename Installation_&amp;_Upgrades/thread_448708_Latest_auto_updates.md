---
title: "Latest auto updates"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by GingerAlex on 2007-05-19
This morning the updater flagged up 4 new updates - 

- 1 was app-install-data-commercial
- the other three are metacity and associated libraries

However- it appears to be unable to check the signing, there was a message about this when I tried to install, and if I press 'Check' in update manager I get the message:

**W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783**

So I've not installed them for now - there's no point having things signed if I ignore these types of messages! Are these updates safe?

cheers,
Alex.
I am on 7.04.

---

### Post by taurus on 2007-05-19
Open a terminal and run

Applications -> Accessories -> Terminal
```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by GingerAlex on 2007-05-19
Hello, thank you for the quick response!

Unfortunately after the 1st line I get:

**gpg: no valid OpenPGP data found.**

Perhaps a server is down? Should I just leave it and try later?

cheers,
Alex

---

### Post by taurus on 2007-05-19
Yes.  On the other hand, you still can install media stuff from medibuntu.sos-sts.com right now if you wish.

---

### Post by GingerAlex on 2007-05-19
ok, I've done it and it went through without messages this time.


Thanks,
Alex

---

