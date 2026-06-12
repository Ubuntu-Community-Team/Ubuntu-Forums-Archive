---
title: "Ubuntu 14.04 hashes cannot be positively verified against  Ubuntu public key"
date: 2014-04-20
forum: Installation &amp; Upgrades
---

### Post by Invisibilis on 2014-04-20
Hi!

I downloaded Ubuntu 14.04 LTS Trusty Tahr 64-bit ISO from [http://www.ubuntu.com/download/desktop/thank-you?country=US&version=14.04&architecture=amd64](http://www.ubuntu.com/download/desktop/thank-you?country=US&version=14.04&architecture=amd64) and all the hashes from [http://releases.ubuntu.com/14.04/](http://releases.ubuntu.com/14.04/). I checked downloaded ISO against the provided hashes (MD5SUMS, SHA1SUMS, SHA256SUMS). Everything was correct. Any integrity issues were revealed.

_**Unfortunately, I cannot positively verify given hashes against the Ubuntu public key. **_I had gpg installed, so I imported FBB75451 key from keyserver.ubuntu.com.

$ gpg --keyserver hkp://keyserver.ubuntu.com --recv-keys 0xFBB75451
gpg: requesting key FBB75451 from hkp server keyserver.ubuntu.com
gpg: key FBB75451: public key "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" imported
gpg: 3 marginal(s) needed, 1 complete(s) needed, PGP trust model
gpg: depth: 0  valid:   2  signed:  12  trust: 0-, 0q, 0n, 0m, 0f, 2u
gpg: depth: 1  valid:  12  signed:   8  trust: 0-, 0q, 0n, 6m, 6f, 0u
gpg: depth: 2  valid:   4  signed:   4  trust: 1-, 0q, 0n, 0m, 3f, 0u
gpg: depth: 3  valid:   1  signed:   0  trust: 0-, 0q, 0n, 0m, 1f, 0u
gpg: next trustdb check due at 2008-04-14
gpg: Total number processed: 1
gpg:               imported: 1

_**However, when the command $ gpg --verify MD5SUMS.gpg MD5SUMS is put into terminal, the result is as follows:**_

gpg: Signature made Sat 19 Apr 2014 12:38:11 AM CEST using DSA key ID FBB75451
gpg: **_BAD signature_** from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"

**_Could you explain me why gpg previews bad signature? What went wrong?_**

Thank you for your responses.

---

### Post by Invisibilis on 2014-04-21
I downloaded the checksums once again an hour ago and everything was verified positively. What was the cause of my problem, I don't know. :)

---

