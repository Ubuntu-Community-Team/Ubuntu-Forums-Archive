---
title: "error trying to upgrade to 18.04"
date: 2018-08-02
forum: Installation &amp; Upgrades
---

### Post by augusto_sf on 2018-08-02
I have been trying to upgrade to 18.04 from 17.10, but the system sends me the following error message and then closes the upgrade window (i am working with an ethernet connection so internet is not the problem):

W:[http://deb.opera.com/opera/dists/stable/InRelease:](http://deb.opera.com/opera/dists/stable/InRelease:) The key(s) in the keyring /etc/apt/trusted.gpg.d/jockey-drivers.gpg are ignored as the file is not readable by user '_apt' executing apt-key., W:GPG error: [http://deb.opera.com/opera](http://deb.opera.com/opera) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D615560BA5C7FF72, E:The repository 'http://deb.opera.com/opera stable InRelease' is not signed., W:Updating from such a repository can't be done securely, and is therefore disabled by default., ETC.

I cannot understand the message since i removed 'Opera' from my system a while ago. Could anyone please suggest a way out of this problem? Thanks a lot.

Augusto

---

### Post by Impavidus on 2018-08-02
Maybe you have removed the opera programme, but not the opera repository. Look into your software sources and disable it. Actually, disable all sources except the official ones. After the upgrade you may want to enable them again.

And be quick. Support for 17.10 has already ended.

---

