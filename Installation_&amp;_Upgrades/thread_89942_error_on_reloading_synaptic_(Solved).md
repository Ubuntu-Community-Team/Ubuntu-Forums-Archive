---
title: "error on reloading synaptic (Solved)"
date: 2005-11-13
forum: Installation &amp; Upgrades
---

### Post by gdlx on 2005-11-13
Have Ubuntu Hoary running on a AMD-64 laptop WinXP dual boot.
Had a message that packages were out of date and needed to reload.

On trying to reload, received following error.

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

What do I need to do to clear this and reload pkg info?

---

### Post by PerfMonk on 2005-11-13
This solution worked from me.   Previously found by Antipex.  Just search for "apt-get GPG error" in this forum.

[QUOTE=netrattler]Antipex just change the backport link in your /etc/apt/sources.list file to one of there mirrors and you should have no more trouble.

deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-backports main universe multiverse restricted
deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-extras main universe multiverse restricted

Joe[/QUOTE]

If you have another country source  just change the names to point to the ubuntu source.  

Regards,
          BT

---

### Post by gdlx on 2005-11-14
Thanks for the help. I learn something every day.

---

### Post by gdlx on 2005-11-14
removed us from all packages and it cleared the problem. All updates loaded.

Tnx

---

