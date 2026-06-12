---
title: "Can I install jaunty correctly after I install lucid?"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by HandLotion on 2010-07-02
New computer, System 7 and Lucid already installed. Can I add jaunty as a third boot option without messing up Grub?  It doesn't seem that I would want to replace the newer version of Grub that comes with Lucid when I do a Jaunty install in a separate partition.
How do I do this right to to have triple boot of Lucid/Jaunty/System 7 ?

There are some software programs not available in Lucid so I still want to run the Jaunty versions.

---

### Post by darkod on 2010-07-02
When installing click on the Advanced button in the last screen of the installer, before clicking Install. There you can select not to install the bootloader (grub).
At first boot Jaunty won't be in the menu of course. Once you have booted Lucid, just run:

sudo update-grub

to detect it.

---

### Post by HandLotion on 2010-07-02
Thanks darkod for the quick reply.  I'll do just as you say.

---

