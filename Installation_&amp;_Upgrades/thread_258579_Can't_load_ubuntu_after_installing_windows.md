---
title: "Can't load ubuntu after installing windows"
date: 2006-09-16
forum: Installation &amp; Upgrades
---

### Post by eGrant on 2006-09-16
Ok, so I already had windows xp installed with ubuntu (Dapper Drake 6.06), and they both worked fine together. But then, the windows made some trouble and I had to reinstall it. So I've formatted the HD belonging to the windows (ubuntu is installed on its own HD) and installed a fresh new windows xp. Now I can't boot ubuntu any more, and basically I have no access to it at all, as I don't even get the choice screen of the OS's that I had before.
I'll appreciate any help you can give me!

---

### Post by kidders on 2006-09-16
Hi there,

Windows installs quite commonly seem to overwrite your master boot record ... I'm convinced the developers did that on purpose, just to be irritating!

If you re-install your bootloader, everything will be fine. All you need is to boot from a CD and chroot into your Ubuntu. I'm sure there are plenty of HOWTOs around for this ... it's quite common, but if you run into trouble, post back :-)

---

### Post by eGrant on 2006-09-16
Thanks :)

I didn't really knew how to do what you've told me, so I've looked for some guides, and finally found a great solution at:
[http://my.opera.com/Mr%20Green/blog/show.dml/224803](http://my.opera.com/Mr%20Green/blog/show.dml/224803)

I typed exactly what the guy wrote there and it worked great.. And now I'm back in my Ubuntu again :) Thanks!

---

### Post by kidders on 2006-09-16
Glad to hear it :-)

---

