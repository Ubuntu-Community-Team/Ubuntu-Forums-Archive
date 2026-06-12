---
title: "Copy encrypted home directory"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by joux on 2010-01-11
I got myself a bigger hard drive and installed a fresh Karmic on it. Now I want to copy my old /home directory to the new system.

I set up the encrypted home directory feature on both the old and the new installation. Now I tried to simply copy the contents of /home/.ecryptfs/<username> to the new drive.

As both encrypted data (.Private) and the wrapped key (in .ecryptfs) are now copied, and my login password and username are the same as on the old system, I expect this to work. But is does not. When Gnome starts, there are several error messages, showing that my home directory was not mounted.

Is there anything outside of /home/.ecryptfs/<username> that I need to copy to a new installation?

Thank you for help and suggestions.

---

### Post by joux on 2010-01-11
OK, this one is solved.

It was a rather ordinary file permission problem. I copied the data as root from a Live CD system. So the owner was root, but should have been my normal user, of course. chown solved it.

---

