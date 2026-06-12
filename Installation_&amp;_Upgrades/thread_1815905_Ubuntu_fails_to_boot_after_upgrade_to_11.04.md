---
title: "Ubuntu fails to boot after upgrade to 11.04"
date: 2011-08-01
forum: Installation &amp; Upgrades
---

### Post by Rubenknex on 2011-08-01
I just upgraded to ubuntu 11.04 but now all the kernels fail to boot. The resolution of grub changed and the older kernels are put into a 'previous kernels' folder. The most recent kernel halts at the message '* Stopping userspace bootsplash [ OK ]' and the previous kernels fail with the message 'Unlink after no-irq. Controller is probably using the wrong IRQ', 
[IMG]http://i54.tinypic.com/15gcxhw.jpg[/IMG]
or show the background of the login screen with just a white box.
[IMG]http://i52.tinypic.com/2qiv1og.jpg[/IMG]
I think the cause is that I have an ATI graphics card (HD Radeon 3650), because on my 2 other computers ubuntu upgrades fine and they have NVIDEA graphics cards.

As a last resort I tried installing different distro's like Linux Mint but it also gived me the 'unlink after no-irq' message.

Do you guys know what the problem might be and how I can solve it? Thanks.

---

### Post by Eleos on 2011-08-07
Did you ever find a solution?  I uninstalled Nouveau in 11.04 and installed the NVIDIA driver, and I have the same problem, hangs at the same spot...

-Eleos

---

### Post by plugnplay on 2011-12-31
i habe the same problem i have stopped workimg please help

---

