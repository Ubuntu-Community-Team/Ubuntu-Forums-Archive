---
title: "Edubuntu 8.04 thinclient config with ltsp problem"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by hildebrand_us on 2008-06-17
I need to set up a network of about eight pcs in a lab in thin client configuration. I read online in some forums that it was possible to get ltsp almost out of the box using edubuntu.
It is a P4 system with only one ethernet card.
After reading some documentation online I did the following:-
1. Installed a basic desktop with the ubuntu 8.04 alternate desktop. (I forgot to do F4 and say mode to be ltsp here).
2. After this was installed I added all the sources and installed the edubuntu-desktop + edubuntu-desktop-withkde (or similar named) package.
3. Realising that I had forgotten to install ltsp I installed this package as specified on [https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall) page: sudo apt-get install ltsp-server-standalone openssh-server
4. Then I created the client environmenton the server with.
    sudo ltsp-build-client

As per page i should be able to boot with another PC (in whose bios I made the boot on lan configuration) what could be the problem?

Awaiting an early reply
Regards
Hildebrand

---

