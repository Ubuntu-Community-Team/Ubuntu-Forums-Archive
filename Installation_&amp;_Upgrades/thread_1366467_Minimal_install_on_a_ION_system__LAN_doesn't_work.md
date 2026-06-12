---
title: "Minimal install on a ION system:  LAN doesn't work"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by Iskendar on 2009-12-28
Hi all,

I'm trying to set up a HTPC based upon a Zotac IONITX-F mobo. The idea was to use the karmic mimimal install and then run xbmc. Problem is that the ION board has an nvidia ethernet controller, which doesn't get recognized by the install disk. Since minimal installs everything from the net, I'm pretty much stuck at the 'configure network' step. 

When running a full kubuntu 9.10 boot disk, the installer can't manage to get ahold of a dhcp connection either, but after install, I can get the network working.

So my question is, is there a way to get ubuntu minimal working with an nvidia network controller somehow, or am I stuck doing full installs and trying to uninstall unnecessary stuff afterwards?

---

### Post by solitaire on 2009-12-29
It sounds like you'l have to make your own Minimal install disk.

If you are installing via USB  then it's easy-ish...:
If you know what ".deb"s you require, you can just download them and put them into the proper folder within the "/pool/" directory.
Their might be a few more steps but that should at lest give you access to the network.
The install should then see those debs during install and you can install them.

Hopefully others here can give you a bit more help... ^_^

---

### Post by Iskendar on 2009-12-31
> **solitaire said:**
> It sounds like you'l have to make your own Minimal install disk.

If you are installing via USB  then it's easy-ish...:
If you know what ".deb"s you require, you can just download them and put them into the proper folder within the "/pool/" directory.
Their might be a few more steps but that should at lest give you access to the network.
The install should then see those debs during install and you can install them.

Hopefully others here can give you a bit more help... ^_^

Interesting info, I might just need that later on. However, for this problem, I found the source: bad cable :oops: The reason I didn't pick up on this was that I managed to get my netbook connected with the same cable, no prob. When I connected the htpc with a different cable, the network worked like a charm :rolleyes:
Anyway thanks for the info. I have different problems now, but that's for another thread...

---

