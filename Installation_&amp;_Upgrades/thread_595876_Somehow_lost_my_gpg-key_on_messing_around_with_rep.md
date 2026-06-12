---
title: "Somehow lost my gpg-key on messing around with repos"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by Saubazi on 2007-10-29
I somehow lost the GPG-key from synaptic and now I have some problems - any repos
I activate - even main - will give me:

W: GPG error: [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

I try:

$ gpg --keyserver hkp://subkeys.pgp.net --recv-keys 437D05B5 
gpg: requesting key 437D05B5 from hkp server subkeys.pgp.net
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0


What else can I do?

---

### Post by Saubazi on 2007-10-29
Solution seemed to be the small button "restore defaults" on authentication or so tab...

---

