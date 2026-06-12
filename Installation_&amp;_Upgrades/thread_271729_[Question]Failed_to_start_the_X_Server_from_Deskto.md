---
title: "[Question]Failed to start the X Server from Desktop CD"
date: 2006-10-05
forum: Installation &amp; Upgrades
---

### Post by jixing_alex on 2006-10-05
I had downloaded ubuntu 6.06 LTS desktop i386.iso, checked MD5
and burn it to CD. Boot from the CD, select 'start or install
ubuntu'. My screen became unnormal. After perpared to start X
Server, follow comment was appear:
----Failed to start the X Server (your graphical interface). It
----is likely that it is not set up corrently. Would you like to
----view the X Server output to diagnose the....?
----        <Yes>             <No>
then came into console. So I can't install ubuntu to my hardware.

Who can solve it? Please help me!

My computer:
    AMD64 Sempron 2800
    1GB RAM
    SATA 160GB
    ATI Randoen X700 SE (RV410) (PCIE)

---

### Post by Kateikyoushi on 2006-10-05
When you boot the live cd select start ubuntu in safe graphics mode.

---

### Post by Herman on 2006-10-05
Try clicking on the following link and see if that will help you, [sudo dpkg-reconfigure xserver-xorg]("http://users.bigpond.net.au/hermanzone/p7.html")
Regards, Herman :D

---

