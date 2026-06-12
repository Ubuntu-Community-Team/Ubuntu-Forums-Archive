---
title: "Why is OpenSSL not upgraded?"
date: 2014-08-07
forum: Installation &amp; Upgrades
---

### Post by dwhitney67 on 2014-08-07
I received info regarding OpenSSL from the updater:
```

Version 1.0.1f-1ubuntu2.5:
This update was issued on 08/07/14 4:03 AM
  * SECURITY UPDATE: double free when processing DTLS packets
    - debian/patches/CVE-2014-3505.patch: fix double free in ssl/d1_both.c.
    - CVE-2014-3505
  * SECURITY UPDATE: DTLS memory exhaustion
    - debian/patches/CVE-2014-3506.patch: fix DTLS handshake message size
      checks in ssl/d1_both.c.
    - CVE-2014-3506
  * SECURITY UPDATE: DTLS memory leak from zero-length fragments
    - debian/patches/CVE-2014-3507.patch: fix memory leak and return codes
      in ssl/d1_both.c.

```

I am synced in with Ubuntu 14.04 LTS.  Why is OpenSSL 1.0.1f still being pushed to the repositories?

Probably the wrong place to voice an opinion, but please (Canonical) post an updated version that addresses the "ancient" Heart-Bleed issue reported months ago.  The OpenSSL release that should be made available is (at least) 1.0.1g.

---

### Post by nerdtron on 2014-08-07
Although the heartbleed.com site says 1.0.1f version is vulnerable, the openssl package from the Ubuntu repositories was already patched and is already safe from the heartbleed. It may just be a naming convention now. I remember this has been discussed in the forum many times.
Canocical did pushed a patched on day the heartbleed bug was made public. You are safe as long you updated your ubuntu.

---

### Post by ian-weisser on 2014-08-07
This has been discussed several times already.

You are assuming that the newest version of OpenSSL is the only way to get the fix.
And for many users, who don't want to patch and compile, that may be true.

The heartbleed fix, like many security patches, was promptly *backported* to the versions of OpenSSL in the Ubuntu Repositories.

Indeed, the patched version was uploaded to all supported Ubuntu repositories within 24 hours of public release of the vulnerability. The fixed version may have been in the Ubuntu repos (and pushed to your system) before many users even heard the news.

And you know, *that happens all the time*. The Ubuntu Security Team pushes hundreds of patched packages every year. See [http://www.ubuntu.com/usn/](http://www.ubuntu.com/usn/) for the list. In fact, they pushed a fix to *another* OpenSSL vulnerability within the last 24 hours!

Why doesn't Ubuntu simply upgrade to the next version instead of backporting? Well, because some upstreams don't release new versions for every patch. And Ubuntu is tested with the older version; replacing with newer versions can (and does) fix one vulnerability...but may introduce new vulnerabilities, bugs, and incompatibilites. It's *untested*. On the LTS versions, Ubuntu has *promised* not to update the software; that's the whole point of 'stability.'

---

### Post by dwhitney67 on 2014-08-08
nerdtron & ian-weisser -

Thank you for your answers.

---

