---
title: "Fix for obtaining Firefox 2.0 instead Firefox 1.5"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by galder on 2006-10-27
Hello,

I had that problem. I was executing Firefox 1.5 instead Firefox 2.0, The problem was that ](*,) I installed myself Firefox 1.5 some time ago, and firefox was pointing to the 1.5 version.

I have searched for firefox binary files, and I have found the firefox 2.0 binary.

Just point to the 2.0 version doing this:

          root@galder:/usr/bin# mv firefox firefox.back

Thas has renamed the old version into firefox.back

          root@galder:/usr/bin# mv mozilla-firefox firefox

mozilla-firefox was the name given for the 2.0 binary. Now it has been renamed to firefox.

Open firefox from the top bar, or the menus, and 2.0 will run!

I hope this help you.

---

