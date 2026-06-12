---
title: "replace the 10.10 kernel with a 10.04 kernel?"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by roop_s on 2010-10-20
A problematic system has this kernel:
2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:26:05 UTC 2010 x86_64 GNU/Linux

A working system has this kernel:
2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux

Can I put the working kernel onto the problematic system? I've copying the contents of /boot from the working system (I did *not* copy the /boot/grub directory). Should I manually start editing grub.cfg for a dual kernel boot or is there a better way?

The problematic issues are with video playback (choppy after upgrade) and video capture - you can only open the capture device once, then you have to reboot since upgrading.

---

### Post by roop_s on 2010-10-21
after some experimenting and a lot of reading:

ubuntu 9.10 and above uses grub2 which doesn't have many user modifiable files. certainly none in /boot/grub (they don't affect the system boot).

/etc/default/grub has a user-modifiable flle. this allows you to turn the boot menu on so you can select a different kernel (comment GRUB_HIDDEN_TIMEOUT).

next you can simply copy the kernels and their associated files into /boot

finally you can run sudo update-grub. this will look at the modifications you made to /etc/default/grub as well as create a boot menu based on the files found in /boot/.

you do also need the modfules... /lib/modules needs to have the directory of the kernel you want to run containing all the drivers.

when i rebooted i selected the old kernel. it seemed to load but then hungs :(
i then tried copying the modules for the specific issue i was having (possibly CX88 driver issue) but the same problem occured. well at least i learned alot.

if anyone has ideas on why the kernel hung, let me know.

---

### Post by coffeecat on 2010-10-21
It is possible, but not the way you have done it. Simply copying files over won't work. For one thing, an initrd.img needs to be generated for your system.

What you need to do is to download the .deb files for the kernel and install them manually in Maverick. I have done this - installing a Lucid kernel in maverick - and it works.

First - clear out all the copied files in Maverick. Don't bother with an update-grub now. That comes later.

Boot into Lucid, open Synaptic and search for "2.6.32". It will show all the packages installed for that kernel, three for each incremental release. In my case the packages linux-image-2.6.32-25-generic_2.6.32-25.45_amd64.deb, linux-headers-2.6.32-25_2.6.32-25.45_all.deb and linux-headers-2.6.32-25-generic_2.6.32-25.45_amd64.deb. Mark the three for re-installation but don't re-install. Instead choose 'Generate package download script' from the File menu. Here's what I got which you can use if you want.

```
#!/bin/sh
wget -c http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-25-generic_2.6.32-25.45_amd64.deb
wget -c http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-25_2.6.32-25.45_all.deb
wget -c http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-25-generic_2.6.32-25.45_amd64.deb
```However, that's for the 2.6.32-25 kernel. If you have a particular reason for wanting the 2.6.32-22 kernel, you must run your own script. If you generate your own script it will be owned by root and made executable for you, so if you copy mine, you need to make it executable although it doesn't need to be owned by root.

Transfer the script to your Maverick install and run it to download the three deb files. Now, simply double-click on each in turn to install or:

```
sudo dpkg -i linux*deb
```... in the same directory as the downloaded deb files.

Alternatively, in Firefox, go to:

[http://archive.ubuntu.com/ubuntu/pool/main/l/linux/](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/)

...and find the three deb packages you need and download them. Note that in my script it shows the GB Ubuntu archive, whereas in that link above I've given you the main one. You can go to any mirror of your choice and use the same path.

The  package manager will run update-grub for you, but you'll find that the Lucid kernel appears after the 2.6.35 Maverick one in the grub menu. I'll leave you to sort that out. :)

**Edit:** I want to thank you for posting this. The reason I tried the Lucid kernel in Maverick was because the Maverick kernel has broken the Fn key brightness keys on my Sony laptop. The 2.6.36 kernel has now been uploaded to the servers for Natty Narwhal testing, so I've downloaded and installed the 2.6.36 kernel in Maverick on my Sony - posting from there now - and I'm delighted to find my Fn keys work again. You could try the 2.6.36 kernel yourself if you want but be aware that there will be frequent updates to it over the coming months which the package manager will not tell you about. You'll need to check yourself. Since this could be a security issue, you must do this. Similarly if you want updates to the 2.6.32 kernel you need to check for yourself.

---

### Post by roop_s on 2010-10-21
thanks for the reponse. i just clean installed 10.04 and updated it. with kernel 2.6.32-21 the specific problem i was having is no longer occuring.

i'm going to try to get 10.10 on an earlier kernel following your advice later today, thanks for the input!

---

### Post by roop_s on 2010-10-21
It worked, thank you so much! In case someone stumbles on this in the future, here are the details of the problem:

ATSC channel viewing from a hauppauge 1800 card (cx88) stopped working after the upgrade from 10.04 to 10.10. the card worked because it ran in another computer no problem. These two specific issues occured to the card:

Channel scanning would never complete:
scan /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB -o zap | tee channels.conf

After using the card for one single task (watching a channel or channel scanning) you would have to reboot otherwise face a bunch of errors and be unable to use the card.

To make this problem even more specific, the card works fine in 10.10 on one system - ASUS maximus formula motherboard, intel core2duo CPU and ATI 3870 video. On another system, it only worked properly in 10.04: ASUS m2n68-vm nvidia onboard graphics, amd athlon ii x2 CPU.

To remove as many other variables as I could, I had clean installed a few times and even just tried the old cx88 drivers but the same problem occurred. Channel viewing on different version of vlc/mplayer made no difference. Downgrading the kernel allowed me to use the card normally in 10.10:

roop@phoenix:~$ uname -a
Linux phoenix 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:52:42 UTC 2010 x86_64 GNU/Linux
roop@phoenix:~$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

This is the ideal solution for me. Fixing whatever bug caused this would be great but I'm replacing the motherboard in this system shortly. If the problem occurs in the new motherboard then I'll have to file a bug report.

---

