---
title: "E: tzdata: subprocess post-installation script returned error exit status 1"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by demarshall on 2008-03-15
I'm running Gutsy 7.10 and had an error with Adept Updater in that it wouldn't finish an update.

I started Synaptic because often it gives instructions about how to fix problems like this but it didn't.

I then had Synaptic select the updateable packages and told it to apply the changes.

The files that it was going to update are:

language-pack-en
language-pack-es
language-pack-kde-en
libvlc0
lighttpd
mozilla-plugin-vlc
vlc
vlc-nox

It came up with this error after a minute or so:

E: tzdata: subprocess post-installation script returned error exit status 1

I attempted to run "sudo dpkg --configure -a" in a console

Here is the output:

Setting up tzdata (2008a-0ubuntu0.7.04) ...
Running 'tzconfig' to set this system's timezone.
/var/lib/dpkg/info/tzdata.postinst: line 27: /usr/sbin/tzconfig: No such file or directory
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 tzdata


Does anybody have any suggestions as to how to fix this?

Thanks

---

### Post by demarshall on 2008-03-16
I read through the error message to see what I could determine since nobody else is responding and I found that /usr/sbin/tzdata has disappeared. 

How would I get that file back in that directory?

---

