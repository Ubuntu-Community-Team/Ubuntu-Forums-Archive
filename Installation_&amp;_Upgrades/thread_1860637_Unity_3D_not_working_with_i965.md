---
title: "Unity 3D not working with i965"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by dnaws on 2011-10-15
I recently upgraded to oneiric, and wanted to try the new updated Unity (I was using gnome2 previously).  Logging in using a Unity session failed -- the screen went black and returned to the login screen.  The Unity 2D session worked, however, so I got to do some troubleshooting.

"glxinfo | grep render" showed that DRI was off.  Setting LIBGL_DEBUG=verbose and rerunning the glxinfo command showed that i965_dri.so was trying to be loaded from several different places, but the file didn't exist in any of them.  Interestingly, Xorg.0.log indicated that it loaded i965_dri.so successfully.

Running 'locate i965_dri.so' indicated the file existed at /usr/lib/i386-linux-gnu/dri/i965_dri.so, which WASN'T being searched by glxinfo.  So I ran "sudo ln -s /usr/lib/i386-linux-gnu/dri/i965_dri.so /usr/lib/dri" to create a symlink in a location glxinfo WAS looking.  A quick glxinfo indicated that DRI was now ON, and the regular Unity session worked like a charm!

Posting this in case anyone else comes across this issue as well.  Does anyone know a "better" long-term solution?  driconf doesn't appear to be able to change the search directories.

I've got a core i5 sandybridge with the HD3000 chip.

---

