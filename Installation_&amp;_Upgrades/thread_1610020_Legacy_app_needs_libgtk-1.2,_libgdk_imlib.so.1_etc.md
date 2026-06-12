---
title: "Legacy app needs libgtk-1.2, libgdk_imlib.so.1 etc., how to install on 10.04?"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by T.E.N. on 2010-10-31
Occasionally I have to bring up the remote-control application for a legacy OS/2 firewall&NAT (running on early ancient first-gen Pentiums from -and continously ever since- the mid-1990s), fgui out of [http://www.fx.dk/download/linux/ijfire.tar.gz](http://www.fx.dk/download/linux/ijfire.tar.gz) as at [http://www.fx.dk/download/](http://www.fx.dk/download/) (still closed source AFAICS).

While a few libraries are in the tarball and can be used from a separate directory e.g. by
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/user/InJoy/lib
the ones below are notably missing
libgtk-1.2.so.0, libgdk-1.2.so.0, libgmodule-1.2.so.0, libgthread-1.2.so.0, libglib-1.2.so.0, libgdk_imlib.so.1
and cannot simply be symlinked to their successors as the interfaces won't match anymore:
./fgui: symbol lookup error: /home/user/InJoy/lib/libdw.so.1: undefined symbol: gtk_type_is_a

I recall these *1.2* libraries being available from Universe in Feisty at least and possibly up until Hardy, but how could they be integrated (maybe from the repository from an older version) these days into the current 10.04 LTS (maybe even just into the subdirectory for this one binary, to avoid causing confusion to any other applications)?

---

