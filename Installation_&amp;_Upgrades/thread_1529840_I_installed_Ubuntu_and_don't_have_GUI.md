---
title: "I installed Ubuntu and don't have GUI"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by Alex Dumitru on 2010-07-12
Hi,

I have installed Ubuntu 10.04 for about 20 times on two identical computers in the last 3 days and I've never got a GUI.

First, I get an error after pressing the Install button if I don't check the "nomodeset." If I check it, the install works perfect, but after the restart I only have a command line. I also tried "startx", but I only get a black screen.

Also I have to mention that the Live CD works great and I have an Intel GMA 3100 on-board graphics card. 

I've also tried to install it from the Live CD and from Windows, but I got the same result - Command Line. 

I also tried to install the "ubuntu-desktop", but all my repositories were links actually and I didn't manage to connect to the internet from the command line. 

What else could I do ?

---

### Post by oldfred on 2010-07-13
I had to do this:
boot from the cd, press F6 and then select the nomodeset option.
(I edited my grub.cfg as I use USB installer with grub to boot ISO, Also can edit in syslinux.cfg or text.cfgfor other type USB installers)
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

I had nvidia and just install the nvidia driver.

if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

---

