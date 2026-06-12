---
title: "Edgy: mouse not recognized"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by darkghost on 2006-10-26
Hello, 
I was planning to uninstall Dapper and make a fresh install of Edgy on my PC.
I tried to launch the live CD to see if everything was fine but I can't move my mouse.
The strange thing is that in Dapper it gets recognized with no problems.

It's a Logitech MX(??I throwed the box months ago) wireless mouse.

The Logitech cordless keyboard is recognized.

Any suggestion on how to solve this problem ?

Thanks
Darkghost

(I forgot, it's Kubuntu edgy - one of the latest isos available, not the final of course)

---

### Post by Akita on 2006-10-26
Is the interface at the PC USB? Edgy lost the USB mouse that I use on my laptop. The cure turned out to be adding "usbcore" to the beginning of the list in /etc/modules. OTOH I'm pretty sure this is due to ndiswrapper (wireless) getting added to the usb devices by the new kernel, so it may not fix your problem.

---

### Post by darkghost on 2006-10-26
Thanks, im going to try this...if I was able to launch a console without mouse... any key combination to launch the console? I can't remember..

---

