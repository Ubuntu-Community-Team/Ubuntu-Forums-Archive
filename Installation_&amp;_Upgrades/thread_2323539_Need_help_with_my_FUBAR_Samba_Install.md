---
title: "Need help with my FUBAR Samba Install"
date: 2016-05-06
forum: Installation &amp; Upgrades
---

### Post by U&amp;?@&lt;i5}-+ on 2016-05-06
Hey everyone,

I need some help fixing Samba on my HTPC. I tried to fix the following error by purging and reinstalling Samba:

[IMG]http://i.imgur.com/FJzMYsf.png[/IMG]

Only after purging Samba it removed something which broke my installation of Kodi. Now when I try run Kodi I receive the following error:

```
/usr/lib/kodi/kodi.bin: error while loading shared libraries: libtalloc-report.so.0: cannot open shared object file: No such file or directory
```

If I try to complete the installation of Samba in the hopes of it restoring the missing file above, this happens:

```

Setting up samba (2:4.3.9+dfsg-0ubuntu0.14.04.1) ...
smbd start/pre-start, process 9307
start: Job failed to start
invoke-rc.d: initscript samba-ad-dc, action "start" failed.
dpkg: error processing package samba (--configure):
 subprocess installed post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I then came across this command on another thread, which highlights something else is missing, but it didn't have any information on how to fix this problem.

```

$ samba-tool testparm --parameter-name="server role" give
Traceback (most recent call last):
  File "/usr/bin/samba-tool", line 33, in <module>
    from samba.netcmd.main import cmd_sambatool
  File "/usr/lib/python2.7/dist-packages/samba/__init__.py", line 28, in <module>
    import samba.param
ImportError: libserver-role.so.0: cannot open shared object file: No such file or directory

```

If anyone has any ideas on how to fix this I am all ears.

---

### Post by U&amp;?@&lt;i5}-+ on 2016-05-08
Never mind. It was quicker to just reinstall and upgrade to 16.04 than troubleshoot this problem.

---

