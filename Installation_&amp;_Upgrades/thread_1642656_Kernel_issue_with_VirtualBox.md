---
title: "Kernel issue with VirtualBox"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by aperture123 on 2010-12-10
Greetings ubuntu gurus,

  The day before yesterday I had the _bright_ idea of downloading and compiling the latest kernel for my machine (ubuntu 10.04 LTS), which is an acer aspire one. So I compiled it and went through the whole process and updated grub2 and then rebooted. (not it's 2.6.36.1) However, I found some errors and my mouse wasn't working, but one more restart later and everything was just dandy. So, I wanted to also test out zenwalk on the virtualbox, so I went on over to sun virtualbox official website, downloaded the .deb file, and then installed it. Created zen.vdi, went to start it, and got back an error that vboxdrv wasn't loading/permission problem. error was "Kernel driver not installed (rc=-1908). So, it told me to run ```
sudo /etc/init.d/vboxdrv setup
```, but when looking into that folder, I found that indeed vboxdrv was NOT there. Instead there was "vboxdrv.dpkg-bak" and "vbox.dpkg-dist", and running the -bak one did nothing, but the -dist one ATTEMPTED to work, but still didn't (stopped at "uninstalling old VirtualBox DKMS kernel modules). So I updated my computer, but still it doesn't work. 

I'm sure this is dealing with the kernel, and when I try this command:
```
sudo apt-get install linux-headers-$(uname -r)
```

I get that there were no packages found. ANY HELP PLEASE!? :confused:

---

### Post by Sam Lars on 2010-12-11
Ah, the fun of messing with kernels. You're running 2.6.36.1 now?
If you compiled your own kernel, it's going to be more complicated doing things like VirtualBox, and you're not going to get your kernel headers from Ubuntu (you're using a different version now than Ubuntu offers, that's your last error from apt-get).
I found a couple of pages that might help:
[http://www.uluga.ubuntuforums.org/showthread.php?t=972399](http://www.uluga.ubuntuforums.org/showthread.php?t=972399)
[http://forums.virtualbox.org/viewtopic.php?f=7&t=17764&start=0](http://forums.virtualbox.org/viewtopic.php?f=7&t=17764&start=0)

---

