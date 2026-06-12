---
title: "old distro version after upgrading"
date: 2011-09-13
forum: Installation &amp; Upgrades
---

### Post by maspai on 2011-09-13
hi all

i have ubuntu maverick here. if i upgrade to natty or higher via update manager, will maverick stay (like what happen to kernel when being upgraded)..or get removed?

thanx..

---

### Post by coffeecat on 2011-09-13
No, you won't be able to boot into Maverick once you've upgraded to Natty. Upgrading a release is considerably more involved than upgrading a kernel. As you've discovered, when you upgrade a kernel, the previous one remains and can still be used. This is because the directories and files that each kernel are kept in are distinct. When you upgrade from one Ubuntu release to the newer one, a very large number of packages are completely replaced by newer versions. Things such as the xserver, all the many elements that make up the gnome desktop, gnu utilities and so on.

Be warned that upgrading from one release to the next is a one-way street. If you upgrade to Natty and find that you are your hardware don't like it, the only way to revert to Maverick is to re-install. Back up all your personal data before upgrading!

Good luck!

---

