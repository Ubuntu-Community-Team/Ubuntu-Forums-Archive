---
title: "usplash after update?"
date: 2005-10-26
forum: Installation &amp; Upgrades
---

### Post by dsd on 2005-10-26
I ran "apt-get update" followed by "apt-get dist-upgrade" and everything seems to have worked out okay (upgrading from Hoary to Breezy), but usplash (which wasn't installed before) doesn't seem to work quite right.

The grub screen is still console text (should this be different?), and when loading the text style changes, but there is no real splash screen.

How can I fix this?

(PS. I didn't do a "apt-get install ubuntu-base ubuntu-desktop", could this affect this?)

---

### Post by wellery on 2005-10-26
You need to do:

```
sudo dpkg-reconfigure linux-image-`uname -r`
```

---

### Post by JOKe on 2005-10-26
btw how can i install splashcreen ?

---

