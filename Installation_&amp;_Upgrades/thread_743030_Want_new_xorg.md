---
title: "Want new xorg"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by peakshysteria on 2008-04-02
How can i overwrite or replace my current xorg with a new one? Is this possible? Running Ubuntu Hardy Heron Alpha 6 with xorg 7.3.

---

### Post by logos34 on 2008-04-02
You mean you want to replace/downgrade xorg program, or do you want to reconfigure your graphics?

You can do the latter with

sudo dpkg-reconfigure xserver-xorg

and save the changes to xorg.conf file.

If the former, you could tell synaptic to go back to xorg_7.2-5ubuntu13, and lock that version.

---

### Post by peakshysteria on 2008-04-05
I'll try sudo dpkg-reconfigure xserver-xorg thanks. But (i'm a newbie) how do i save the changes to my xorg. Can't i just open xorg in a text editor and save it there? Or doesn't it overwrite the old one and get saved default?

---

