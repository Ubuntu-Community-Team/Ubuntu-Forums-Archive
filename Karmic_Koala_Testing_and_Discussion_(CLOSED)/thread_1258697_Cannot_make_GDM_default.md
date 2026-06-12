---
title: "Cannot make GDM default"
date: 2009-09-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by NeoFax on 2009-09-05
I have tried everything short of manually changing files and re-install to get GDM back as the default graphical login.  I have done :
sudo apt-get remove --purge gdm (which pulls out lots of stuff I had installed)
sudo dpkg-reconfigure gdm (the screen that asks you to select never comes up)
sudo apt-get remove kdm (thought if GDM was the only one installed it would not give me the error it is not the default)

So, what else can I try to fix this problem?

---

### Post by taavikko on 2009-09-05
Edit /etc/X11/default-display-manager
And change /usr/bin/kdm -> /usr/sbin/gdm

---

