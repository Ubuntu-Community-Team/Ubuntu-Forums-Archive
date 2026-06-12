---
title: "libavcodec2 in hoary?"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by thirda on 2005-04-13
Hi,

Does anyone know about the status of the package libavcodec2 in hoary? It seems that mozilla-mplayer and mplayer-custom depend on it, but hoary doesn't provide an installation candidate for it.

Marillat's repositories include a newer version of libavcodec2 which depend on versions of libvorbis0a and libvorbisenc2 which are not available in hoary or on Marillat's repository. (Presumably they're in Debian sid.) 

The upshot of all of this is that every time I do apt-get upgrade, or run Ubuntu Update Manager, I get complaints that libavcodec2 cannot be upgraded. I'd really rather not have these errors if I can avoid it.

Surely hoary shouldn't contain packages without also containing their dependencies? Any thoughts?

Thanks in advance!

Allan

---

