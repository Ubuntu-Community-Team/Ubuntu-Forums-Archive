---
title: "Safely removing old kernels"
date: 2010-10-03
forum: Installation &amp; Upgrades
---

### Post by tim042849 on 2010-10-03
Using ubuntu 10.04 32-bit.
Reference: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

At the link above I find the following statement: > 
Note: If you don't want all your old kernels to appear in the menu list, remove their files from /boot.

OK. Which files? To elaborate, let's take the oldest (on my machine) kernel.
Two files are listed in that entry: **/boot/vmlinuz-2.6.32-21-generic**
and **/boot/initrd.img-2.6.32-21-generic**. Which of these should I remove? Both of them? Or should I do: ```

rm ls *21-generic
``` 

I think there is lots of room for confusion and possible hosing of the system
:confused: at least for me.

Could something elaborate on what files should really be removed?
thanks
tim

---

### Post by drs305 on 2010-10-03
I've replaced this entry as I have created a new tutorial which enhances the information I previously wrote in this post. It is found here:
[HOWTO: Remove Older Kernels via GUI]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by oldfred on 2010-10-03
We typically recommend you keep two kernels incase the newest has issues, so you can boot the previous.

Uninstall extra kernels:-------------------------
In synaptic search for linux-image to choose to delete old ones
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

A Very Easy Alternate GUI Method - Ubuntu-Tweak
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

kernels do not take a lot of space, so if not constrained for space you can modify grub just to show two kernels and occasionally houseclean.

Partial Custom menu:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

---

### Post by tim042849 on 2010-10-03
Thanks to drs305 for the reference to ubuntu-tweak.. I downloaded it and
used it to purge all but the two latest kernels. I noted that 'tweak' also
ran update-grub.

Thanks for the tip. Good stuff!
tim

---

### Post by tim042849 on 2010-10-03
> **oldfred said:**
> We typically recommend you keep two kernels incase the newest has issues, so you can boot the previous.

...
Good stuff also. Thanks!

---

### Post by hectorivand on 2010-10-03
You can deleted safely with [GtkOrphan]("http://translate.google.com/translate?hl=es&sl=auto&tl=en&u=http%3A%2F%2Fwww.techdays.com.ar%2F2010%2F09%2F01%2Felimina-paquetes-huerfanos-con-gtkorphan%2F")

---

### Post by tim042849 on 2010-10-03
> **hectorivand said:**
> You can deleted safely with [GtkOrphan]("http://translate.google.com/translate?hl=es&sl=auto&tl=en&u=http%3A%2F%2Fwww.techdays.com.ar%2F2010%2F09%2F01%2Felimina-paquetes-huerfanos-con-gtkorphan%2F")
Getting strange performance on Opera from that link. Apparently has
something to do with the translator. I will google **GtkOrphan**.
thanks
tim

---

