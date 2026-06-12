---
title: "Installing Oracle 9i on Ubuntu 7.04 via SSH"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by kidders on 2008-04-09
Hi there,

You could use X11 forwarding to run the UI on your local X server. Assuming everything is reasonably well configured on both sides of the connection, you should be able to do a quick test with something like...```
ssh -X server-name
xclock &
```
You may find you need to alter your xhost setting or tweak other security-related things to get it to work.

---

