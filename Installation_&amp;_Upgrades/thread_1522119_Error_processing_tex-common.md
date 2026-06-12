---
title: "Error processing tex-common"
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by mousomer on 2010-07-01
I recently upgraded to Leeenux-linux - a version of Ubuntu NR ([http://www.leeenux-linux.com](http://www.leeenux-linux.com)) on eeepc 4G. I then tried to install texlive from the repositories (via synaptic). It didn't install.
It seems that the problem is with tex-common. dpkg exits on post-instalation script for tex-common returning error exit status 10. 
> Errors were encountered while processing:
 tex-common
Segmentation fault


I tried purge and reinstall using dpkg and apt-get. Also:
> apt-get --configure -a 
didn't work.

Help, please?

---

