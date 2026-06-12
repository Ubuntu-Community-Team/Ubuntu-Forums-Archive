---
title: "Ubuntu Kernel Updating 2.6.34 problem"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by Michael64 on 2010-06-04
Alright I will try to make this short and sweet. If I have posted this in the incorrect section please feel free to move it thanks.
 
I downlaoded Ubuntu 10.0.04 about a month ago onto an external HDD. It is connected through usb to a Dell 8000 or soemthing I believe. I don't remember the exact model, and am currently in school so I can't find it.
 
When I try to go on the internet- using both firefox and opera the videos load very fast and suddenly stop. Internet pages load extremely slow. I have exhausted ever possilbe solution.
 
I am currently using a WUSB45G V.4 wireless adapter to connect to the internet and have been told that 2.6.32 kernel versions have a problem with that adapter and that it has been fixed in 2.6.34. I was told to hook up via ethernet to router (Which has fixed all my problems, everything loads perfectly). 
 
I downloaded the new kernel and tried to load from it. It will load like normal and then right before a login screen I get a blackish purple screen that is blank. I am going to give you the code I used to download the kernel. I hope you guys can find the problem. Thanks.
 
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild#Using%20Ubuntu%20Kernel%20Configuration]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild#Using%20Ubuntu%20Kernel%20Configuration")
 
1. sudo apt-get install git-core kernel-package fakeroot build-essential ncurses-dev
2. cd $HOME
3. git clone git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux-2.6.git
4. cd linux-2.6
5. cp /boot/config-`uname -r` .config
6. make oldconfig
7. yes '' | make oldconfig
8. make-kpkg clean
 
9. cd $HOME
10. git clone git://kernel.ubuntu.com/ubuntu/ubuntu-lucid.git
11. cp -a /usr/share/kernel-package ubuntu-package
12. cp ubuntu-lucid/debian/control-scripts/{postinst,postrm,preinst,prerm} ubuntu-13. package/pkg/image/
 
14.cp ubuntu-lucid/debian/control-scripts/headers-postinst ubuntu-package/pkg/headers/
 
15. cd $HOME/linux-2.6
16. CONCURRENCY_LEVEL=`getconf _NPROCESSORS_ONLN` fakeroot make-kpkg --initrd --append-to-version=-custom --overlay-dir=$HOME/ubuntu-package kernel_image kernel_headers
 
17. cd ..
 
My deb files cam out different so I had to modify the code.
 
18. sudo dpkg -i linux-image-2.6.24-rc5-custom_2.6.24-rc5-custom-10.00.Custom_i386.deb
 
19. sudo dpkg -i linux-headers-2.6.24-rc5-custom_2.6.24-rc5-custom-10.00.Custom_i386.deb
 
20. sudo reboot

---

### Post by bumanie on 2010-06-04
Try going [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/") and downloading the appropriate linux-image - (you should not need the headers). It is a .deb, so just double click to install.

---

### Post by Michael64 on 2010-06-04
I am pretty sure that I am i386 but how do you check for i386 or amd64.

---

### Post by alphacrucis2 on 2010-06-04
> **Michael64 said:**
> I am pretty sure that I am i386 but how do you check for i386 or amd64.

```
uname -a
```

will tell you.

---

### Post by Michael64 on 2010-06-04
This is the response

Linux michael 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

There is no i386, but i686?

---

### Post by wojox on 2010-06-04
> **Michael64 said:**
> This is the response

Linux michael 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

There is no i386, but i686?


That's thirty two bit.

---

### Post by Michael64 on 2010-06-04
Alright so then I want to download i386 version right?

Plus why do you not need the headers?

Does that mean when I was downloading my updated kernel that installing the header portion messed it all up?

---

### Post by wojox on 2010-06-05
Also go into Firefox and *about:config* in the url box.

Search for ipv6 and click it to true.

---

