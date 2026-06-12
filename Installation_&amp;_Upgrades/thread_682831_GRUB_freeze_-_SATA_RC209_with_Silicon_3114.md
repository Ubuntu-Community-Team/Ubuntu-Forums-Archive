---
title: "GRUB freeze - SATA: RC209 with Silicon 3114"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by brent113 on 2008-01-30
I have 2 SATA controllers in my Ubuntu server in addition to the IDE drive Ubuntu is installed on. I am using the cards only as controllers so I can use mdadm.

If there are no hard drives connected to the SATA controllers at boot time it boots normally. I can even then add the hard drives back after it has finished booting and have it be completely functional.

If I connect the SATA hard drives before I turn the computer on, the controllers correctly identify the drives in their respective bios. But GRUB will not load. It gets to Grub loading, please wait and freezes there. It doesn't give an error, it just doesn't do anything. I have to take the drives out and restart the computer in order to boot again.

I have done a lot of research into this but I haven't found anything that has solved the problem. All help is appreciated!

---

