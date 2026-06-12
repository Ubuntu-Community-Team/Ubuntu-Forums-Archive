---
title: "Unable to boot Ubuntu 14.04 with xen hypervisor (bootrepair URL incl)"
date: 2014-08-14
forum: Installation &amp; Upgrades
---

### Post by wrjbarber on 2014-08-14
After an in place upgrade from 12.04 to 14.04 mangled Nvidia and Compiz, I backed up my home folder and exported the list of installed packages. Then I did a clean install from CD and I seem to recall being asked during the install about Xen and misunderstood it to be Ubuntu supporting Xen for other OSes, not Xen with Ubuntu on top. 

After I had the desktop up and running, I imported the package markings into synaptic and spent a great deal of time fixing broken packages and missing dependancies. Among the many packages and upgrades was GRUB. When prompted during the GRUB install, I wasn't clear if it needed to be pointed at sda, sda1 or sda2. From the description included, I chose sda.

Now the machine won't boot. I get "error hwmatch command not found", then it says it is loading ubuntu with xen hypervisor, then initramfs and the screen goes black. From that point, the backlight on my monitor goes on and off a few times, making the black screen go from black to blacker and back. Then it just sits there.

I have two closely related issues here:

1) Obviously, I need to get my machine booting again.
2) I want Ubuntu running directly on the hardware. I will be running a VM within that later (and probably not Xen) So I also need to remove that virtualized kernel. 

I tried bootrepair with the standard options. Here is the url it generated when it gave up.
[http://paste.ubuntu.com/8042070/](http://paste.ubuntu.com/8042070/)

thank you.

---

### Post by wrjbarber on 2014-08-14
I was able to boot directly into Ubuntu by hitting Esc before Xen could load. I have now removed everything Xen related which should solve the problem. I will update this thread once I have tested it.

---

