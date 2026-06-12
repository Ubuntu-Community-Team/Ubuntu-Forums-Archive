---
title: "Update-alternatives issue"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by shirsch on 2007-02-24
After fighting with the installation of IBM Java, I now see this every time anything tries to use update-alternatives:

mv: cannot move `/usr/lib/firefox/plugins' to a subdirectory of itself, `/usr/lib/mozilla-firefox/plugins/libjavaplugin.so'

update-alternatives: unable to rename /usr/lib/firefox/plugins to /usr/lib/mozilla-firefox/plugins/libjavaplugin.so: Invalid argument

Found a lot of discussion that dances around the edge of the issue, but nothing on point.  Clearly, something is messed up in the directory structure (I'm guessing a link where a directory is expected), but what?

Can some kind soul post an ls -alR of /usr/lib/firefox so I can straighten things out?

Steve

---

