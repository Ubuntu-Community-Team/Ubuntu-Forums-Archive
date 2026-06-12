---
title: "Custom kernel with 'make menuconfig'"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by Bucky Ball on 2008-07-09
After much thought, figuring this is possibly the most appropriate place for this post.

Have been looking at 'make menuconfig' and following the instructions outlined on this page;

[http://www.beginlinux.com/index.php/desktop_training/ubuntu/ubfile_m/ub_compile](http://www.beginlinux.com/index.php/desktop_training/ubuntu/ubfile_m/ub_compile)

I have looked around at some other sites and will continue to research, but thought I might see if I can get any knowledgeable heads in the forum to give me some tips if they've already been here.

I'm not exactly a newb (Ubuntu/Linux over the last 6 months, mostly during uni holidays), but I am also no coding wizard by a long shot, so this is what I want to do and looking for a few guidelines. Like to make a custom kernel for my laptop using 'menuconfig'. Worked with computers for awhile and suppose I was bordering on 'power user' with windows and have built a few machines, so the settings for the hardware not really the issue (and 'help' info in the program really good anyhow). What I really want to know is this ...

Can I copy my existing kernel, tweaked to work with my wireless card and other hardware (and working like a treat), drop the things I don't need at boot with menuconfig in my custom kernel (a copy of the working kernel), and save that? Reasons are obvious; if I screw up, I still have my original to fire up.

Instructions on the website I mention seem to be about compiling a whole new kernel, loading that at boot then tweaking to work. Correct me if I'm wrong. Would be much easier to start with a kernel I know is operational and tweak that. Learning and attempting to understand what I am doing as I go so any help appreciated. :)

Hardy Heron 8.04, HP dv6000 series laptop, Turion 64 x2, 2Gb RAM

---

### Post by PmDematagoda on 2008-07-09
If you are talking about doing this on Ubuntu, then just download the Ubuntu kernel source itself through:-
```
sudo apt-get install linux-source
```
which will install the source to /usr/src and is also the Ubuntu kernel source with the configurations and patches.

---

### Post by Bucky Ball on 2008-07-09
Thanks Pm. I followed the page I mentioned through that part last night and wound up with everything I needed in a directory in /usr/src called 'linux' with everything I needed in there. Then I performed the 'make menuconfig' command, interface came up, I selected 'open alternative kernel' and it provided me with the one I'd prepared -  .config

I looked around and made a lot of changes in 'menuconfig' program but chickened out at the last minute when I got back to 'save alternative kernel'. I wasn't sure what to name it ... the name it presented me with was the '.config' one.

Do I name it with a period first? as in '.custom'? or is the idea 'custom.config'? Or do I just keep it as '.config'? It takes awhile to then compile it apparently, so didn't want to screw up there and inadvertantly create quicksand nightmare!

It is at this naming point in the process I am getting a little confused. Not sure where my custom kernel is going or what to call it. And yes, as I say, using Hardy Heron 8.04.

Thanks for your post and love ur 'Bing Tuxby' avatar!

---

### Post by g320907aa on 2008-07-09
[http://newbiedoc.sourceforge.net/system/kernel-pkg.html#KPKG-KERNEL-PKG](http://newbiedoc.sourceforge.net/system/kernel-pkg.html#KPKG-KERNEL-PKG)

[https://help.ubuntu.com/community/Kernel/Compile#head-8587f42b684c3694ba72bdcc89e461ec289cbf02](https://help.ubuntu.com/community/Kernel/Compile#head-8587f42b684c3694ba72bdcc89e461ec289cbf02)

---

### Post by hal8000 on 2008-07-09
> **Bucky Ball said:**
> Thanks Pm. I followed the page I mentioned through that part last night and wound up with everything I needed in a directory in /usr/src called 'linux' with everything I needed in there. Then I performed the 'make menuconfig' command, interface came up, I selected 'open alternative kernel' and it provided me with the one I'd prepared -  .config

I looked around and made a lot of changes in 'menuconfig' program but chickened out at the last minute when I got back to 'save alternative kernel'. I wasn't sure what to name it ... the name it presented me with was the '.config' one.

Do I name it with a period first? as in '.custom'? or is the idea 'custom.config'? Or do I just keep it as '.config'? It takes awhile to then compile it apparently, so didn't want to screw up there and inadvertantly create quicksand nightmare!

It is at this naming point in the process I am getting a little confused. Not sure where my custom kernel is going or what to call it. And yes, as I say, using Hardy Heron 8.04.

Thanks for your post and love ur 'Bing Tuxby' avatar!


Have a look at this link to compile to 2.6.x kernel

[http://www.linuxforums.org/forum/linux-kernel/55612-mini-howto-compile-linux-kernel-2-6-a.html](http://www.linuxforums.org/forum/linux-kernel/55612-mini-howto-compile-linux-kernel-2-6-a.html)

After configuring the kernel options with make menuconfig

You then compile the kernel with
make
make modules_install

This builds the new kernel and module tree but depending on your configured options, you may need to create a new initial ramdisk.
Finally you would copy the new kernel from the kernel source to /boot and modify grub


You need the kernel source in /usr/src
a symbolic link called "linux" points to the kernel source.
the configuration of the ubuntu kernel is stored in the file .config so you can back this file up first
cp .config .config_orig

Any changes made in menuconfig then affect the modified .config file, you could also save this as .config_custom

This part is the easiest part, you wont build a successful kernel first time, it takes patience and a lot of practise.

---

### Post by PmDematagoda on 2008-07-09
> **hal8000 said:**
> You need the kernel source in /usr/src
a symbolic link called "linux" points to the kernel source.

Not really, I compile some kernels in my home directory and in some cases in other drives/partitions, but if you do want to use the kernel source when compiling drivers, etc. then you must ensure that the folder containing the kernel source does not move anywhere or else the link to the source found in /lib/modules/kernel-version will become stale and you would have to update it with the new location.

---

