---
title: "finding external hard drive"
date: 2004-10-24
forum: Installation &amp; Upgrades
---

### Post by jamaas on 2004-10-24
I've just installed a new version of Ubuntu on a HP notebook.  Before dumping the old version of Linux, I saved all my Mozilla settings and email etc on a exf3 filesystem on an external hard drive that is connected by usb.  When I did the Ubuntu install it found all the external hard drive partitions but for some reason must not have built th fstab file correctly because I'm not able to mount the external drive or filesyste.  Is there a debian type probe that will find the disk and directories?  I've already tried rebooting but that didn't work.

Also, what is the best way to install the newest Mozilla Communicator 1.8a4?  I tried downloading the source but found I didn't have a gcc?

Thanks in advance for any suggestions.

Best Regards

Jim

---

### Post by sfw5000 on 2004-10-24
Did you try just unplugging the USB HDD and then plugging it back in? It should auto-mount when you plug it in. If not, you can mount it yourself using
[HTML]sudo mount /dev/devicename /mnt/directoryname[/HTML] 
The command ```
dmesg
``` should list the HDD somewhere in there. On my machine the USB drive shows up as /dev/sdc1. It automounts either when I turn the drive on or plug it in.

Is that the testing release of Mozilla? The current stable release is 1.7.3 which is available in synaptic.

---

### Post by jamaas on 2004-10-25
Thanks a bunch, got it in one!  Actually I had thought of this... .but it never worked with previous distro.  This is great!  Now to see if it will find the same drive by firewire!

Looks great, thanks again.

Jim

---

