---
title: "Ubuntu, Vista from different boot drives"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by tomjackson1 on 2007-03-26
OK, here's the deal. I'd like to install 6.10 on a USB hard drive attached to my laptop. I have seen the info on how to do that, so that part is fine. However, too many people have had trouble with dual booting Ubuntu and Vista. As this is my critical work machine, I have to be extremely careful not to muck it up.

So... if I install Ubuntu to the external USB hard drive and use the Dell option of "boot from attached USB drive" using the F12 key on startup, will any changes of any kind have to be made to the normal bootable C-Drive? I use the live CD but need a bit more.

Thanks!

Tom

---

### Post by bernardfrancois on 2007-03-26
Normally I don't expect you to have any problems.

To be 100pct safe, you could unplug the hard drive containing windows before installing ubuntu on your external hard drive. After you installed ubuntu you can use it and plug your windows drive back in.

---

### Post by esodin on 2007-03-26
I would also suggest that you unplug hard-drive before you install or pay very close attention to the installation procedure. Ubuntu wants very much to install Grub (the boot loader) on the primary drive, That said, I installed Ubuntu on top of Vista on top of XP and they all work as they should - i did want the Grub boot loader for a boot loader, though. 

Good luck

---

### Post by tomjackson1 on 2007-03-26
Thanks y'all! I'll give it a try being EXTREMELY careful. Hmmm... I guess I'll backup the C Drive first.

Tom

---

