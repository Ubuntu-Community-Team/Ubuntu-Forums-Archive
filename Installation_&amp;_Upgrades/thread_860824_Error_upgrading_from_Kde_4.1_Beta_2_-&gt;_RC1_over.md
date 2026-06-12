---
title: "Error upgrading from Kde 4.1 Beta 2 -&gt; RC1 overwriting file also in libkdepim4-kde4"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by Ubuntiac on 2008-07-15
Hi there,

I've been using Hardy with KDE 4.1 beta 2 and just did my "sudo apt-get update && sudo apt-get dist-upgrade"to upgrade to KDE 4.1 RC1.

All downloaded fine, but on installing it gave me the error:

"trying to overwrite `/usr/lib/kde4/share/icons/oxygen/32x32/actions/appointment-new.png', which is also in package libkdepim4-kde4.

If I do a "dpkg --configure -a" I'm told that virtually everything depends on kde-icons-oxygen which isn't installed yet. If I do an apt-get -f install it gives me the first error message.

Any ideas anyone?

---

### Post by pacodani on 2008-07-16
Try to use the overwrite force option of dpkg with the oxygen deb package. I solved it yesterday that way.

---

### Post by yug23 on 2008-07-16
Thanks, I had the same problem and this sorted it out:

```
sudo dpkg -i --force-overwrite libkdepim4-kde4_4%3a4.0.83-0ubuntu1~hardy1~ppa2_i386.deb
```

:)

---

