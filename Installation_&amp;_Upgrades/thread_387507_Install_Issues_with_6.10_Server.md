---
title: "Install Issues with 6.10 Server"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by joehack on 2007-03-18
Hello

I'm currently **trying** to install 6.10 server. The system loads the kernel, blanks the screen and stops after a while. :mad: Installation is not possible!

I assume there are 2 problems, that cause the problem:
1. Framebuffer is not recognized. It's a ATI X300 something. However, I don't need a framebuffer console. How do I get a PLAIN text console install?:confused: 

2. Booting CD from SCSI CDROM. Since my DVD-RW drive is broken, I had to install my old Adaptec 2940UW plus a Plextor drive. I assume, I have to specify the Adaptec driver in order to get the boot running. However since I don't even have a text output, I don't even see (potential) error message.

In general, I asking myself why does the server install CD requires a framebuffer? A server is ment to be installed by professionals. If an admin requires a mouse, she/he should go out and play with windows.

Thanks for your help!

Jochen

---

### Post by tomazb on 2007-03-18
Try installing from alternate CD (which is text based) and after you are done just install linux-server in order to get server kernel stuff.

---

