---
title: "Warsaw package broken and cannot uninstall"
date: 2018-10-19
forum: Installation &amp; Upgrades
---

### Post by macozz on 2018-10-19
Hi,
I just upgrade to 18.10 from 18.04 an all runs fine but the warsaw package, necessary to use internet banking is broken.
Tentatives of unistall previous version gave those error mesages:
```
sudo apt-get remove -y warsaw
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  warsaw
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 47,8 MB disk space will be freed.
(Reading database ... 300320 files and directories currently installed.)
Removing warsaw (1.12.5.1) ...
dpkg: warning: while removing warsaw, unable to remove directory '/usr/local/lib/warsaw/libXrandr.so.2': Operation not permitted - directory may be a mount point?
dpkg: warning: while removing warsaw, unable to remove directory '/usr/local/lib/warsaw/libXrender.so.1': Operation not permitted - directory may be a mount point?
dpkg: warning: while removing warsaw, unable to remove directory '/usr/local/lib/warsaw/libpangocairo-1.0.so.0': Operation not permitted - directory may be a mount point?
dpkg: warning: while removing warsaw, unable to remove directory '/usr/local/lib/warsaw/libtasn1.so.6': Operation not permitted - directory may be a mount point?
dpkg: warning: while removing warsaw, unable to remove directory '/usr/local/lib/warsaw/libpixman-1.so.0': Operation not permitted - directory may be a mount point?
dpkg: warning: while removing warsaw, unable to remove directory '/usr/local/lib/warsaw/libXinerama.so.1': Operation not permitted - directory may be a mount point?
dpkg: warning: while removing warsaw, unable to remove directory '/usr/local/lib/warsaw/libroken.so.18': Operation not permitted - directory may be a mount point?
dpkg: warning: while removing warsaw, unable to remove directory '/usr/local/lib/warsaw/libc.so.6': Operation not permitted - directory may be a mount point?
dpkg: warning: while removing warsaw, unable to remove directory '/usr/local/lib/warsaw/libpcre.so.3': Operation not permitted - directory may be a mount point?
dpkg: warning: while removing warsaw, unable to remove directory '/usr/local/lib/warsaw/libp11-kit.so.0': Operation not permitted - directory may be a mount point?
dpkg: warning: while removing warsaw, unable to remove directory '/usr/local/lib/warsaw/libsasl2.so.2': Operation not permitted - directory may be a mount point
dpkg: warning: while removing warsaw, unable to remove directory '/usr/local/lib/warsaw/libheimntlm.so.0': Operation not permitted - directory may be a mount point?
dpkg: warning: while removing warsaw, unable to remove directory '/usr/local/lib/warsaw/libgtk-x11-2.0.so.0': Operation not permitted - directory may be a mount point?
dpkg: warning: while removing warsaw, unable to remove directory '/usr/local/lib/warsaw/libgpg-error.so.0': Operation not permitted - directory may be a mount point?
dpkg: warning: while removing warsaw, unable to remove directory '/usr/local/lib/warsaw/libgcc_s.so.1': Operation not permitted - directory may be a mount point?
dpkg: warning: while removing warsaw, unable to remove directory '/usr/local/lib/warsaw/libXext.so.6': Operation not permitted - directory may be a mount point?
dpkg: warning: while removing warsaw, unable to remove directory '/usr/local/lib/warsaw/libSM.so.6': Operation not permitted - directory may be a mount point?
dpkg: warning: while removing warsaw, unable to remove directory '/usr/local/lib/warsaw/librtmp.so.1': Operation not permitted - directory may be a mount point?
dpkg: warning: while removing warsaw, unable to remove directory '/usr/local/lib/warsaw/libuuid.so.1': Operation not permitted - directory may be a mount point?
dpkg: warning: while removing warsaw, unable to remove directory '/usr/local/lib/warsaw/libexpat.so.1': Operation not permitted - directory may be a mount point?
dpkg: error processing package warsaw (--remove):
 unable to securely remove '/usr/local/lib/warsaw/wslbmid.so.dpkg-tmp': Operation not permitted
Errors were encountered while processing:
 warsaw
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

What I am doing wrong?

Thank you!

---

### Post by oldos2er on 2018-10-19
Did you install warsaw from the repositories? Wondering why /usr/local/ was used since to my knowledge APT is not going to install anything there.

---

### Post by raccoonstrait on 2018-10-19
macozz

Have you tried removing [COLOR=#000000][FONT=&amp]'/usr/local/lib/warsaw/* manually? You may need to be root to do so, or use something like Krusader in root mode. 

or try


[/FONT][/COLOR]```

sudo aptitude purge warsaw

```

Either way it appears getting rid of  [COLOR=#000000]'/usr/local/lib/warsaw/* is necessary to something. It might also remove your credentials, so make sure you know what you need to know to get back in to your bank.

These are things I would try, but things I try don't always work, so be careful, and maybe wait for more responses.

But what do I know?

Raccoon Strait[/COLOR]

---

### Post by macozz on 2018-10-25
Honestly, I do not remmeber.  But I guess it was...

---

### Post by macozz on 2018-10-25
I tried without success.
First, as I have no aptitude installed, it does not let me install anything because the warsaw cannot be removed
Tring to do it manually give me "Operation not permitted"...
So, I nor even can update the software!

---

