---
title: "Recover from broken uninstall of old headers (14.04)"
date: 2015-05-10
forum: Installation &amp; Upgrades
---

### Post by colinhercus on 2015-05-10
Hi,

Disk space on my OS partition was getting low so I tried to clean up old header sources using procedure at [http://mikedixson.com/2014/10/cleaning-up-linux-headers/](http://mikedixson.com/2014/10/cleaning-up-linux-headers/)

dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed  "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^  ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge

but after this when I boot the display doesn't work, it's just blocky and noise. It's okay on the password screen.

I can boot in recovery made and screen comes up but I can't run the second monitor.

I've been searching for ways to recover but nothing has helped. 

I also tried reinstall from 14.04.02 DVD but though the system started from DVD once I selected Install option it proceeded to boot from HD rather than DVD so I couldn't do repair or install and screen was still all blocky/noisy.

So I'm stuck in recovery mode and not sure what to do.

anyhelp would be appreciated.

Thanks, Colin

---

### Post by ubfan1 on 2015-05-11
That command deletes more than just the old headers, it gets rid of all the kernels except the running (latest?) one.  What video/graphics does your machine have?  Sounds like you need a proprietary driver, which maybe didn't get installed with the latest kernel (which is all you have now).  Does nomodeset help when booting (use "e" to edit the word onto the grub line starting with "linux".

---

### Post by colinhercus on 2015-05-11
Thanks for the help. I tried nomodeset and that boot in similar fashion to recover mode. I still only had one default monitor detected.

So I did some more Googling and found a post about reinstalling gdm. That made things worse and I ended up booting to a black screen with mouse pointer. After googling about that I reinstalled lightdm but hat didn't help.

Next I found a page about installing AMD graphics drivers and reconfiguring XORG so I installed fglrx

sudo apt-get install fglrx
sudo amdconfig --initial
sudo reboot
 
which fixed it.

To others, a warning about Mike Dixsons header purge, it also gets rid of gcc and a lot of development libraries.

---

