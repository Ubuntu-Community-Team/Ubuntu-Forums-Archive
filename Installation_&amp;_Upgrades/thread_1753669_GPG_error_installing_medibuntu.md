---
title: "GPG error installing medibuntu"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by redber20 on 2011-05-09
When I installed Medibuntu via the console, I received this message at the end

Reading package lists...
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220

I tried this method and it didn't work 
gpg --keyserver keyserver.ubuntu.com --recv 6AF0E1940624A220 gpg --export --armor 6AF0E1940624A220 | sudo apt-key add -

---

