---
title: "nvidia driver manual install"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by namelessone on 2007-06-13
So I have a custom compiled kernel, which means that I can't use the restricted drivers manager. This means that I have to install the nvidia driver the hard way.

I downloaded the installer from nvidia's website, moved it to /usr/src and ran it. The installer crashed halfway through and told me too look at the log file, so I did. Most of it was incomprehensible, but here's what I think in the important part:

 >   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (         
\
        echo;                                                           \
        echo "  ERROR: Kernel configuration is invalid.";               \
        echo "         include/linux/autoconf.h or include/config/auto.conf are 
mis
   sing.";      \
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix
 it
   .";  \
        echo;                                                           \
        /bin/false)

so I ran make oldconfig && make prepare on the kernel source, but that didn't work:

> #
# configuration written to .config
#
scripts/kconfig/conf -s arch/i386/Kconfig

*** Error during writing of the kernel configuration.

make[2]: *** [silentoldconfig] Error 1
make[1]: *** [silentoldconfig] Error 2
make: *** No rule to make target `include/config/auto.conf', needed by `include/config/kernel.release'.  Stop.


Now I don't know what to do. Can anyone help me?

---

### Post by Pumalite on 2007-06-13
> **namelessone said:**
> So I have a custom compiled kernel, which means that I can't use the restricted drivers manager. This means that I have to install the nvidia driver the hard way.

I downloaded the installer from nvidia's website, moved it to /usr/src and ran it. The installer crashed halfway through and told me too look at the log file, so I did. Most of it was incomprehensible, but here's what I think in the important part:

 

so I ran make oldconfig && make prepare on the kernel source, but that didn't work:



Now I don't know what to do. Can anyone help me?

Make sure you have kernel-headers and that they match your kernel version. Also make sure you have: 'make', 'automake''gcc latest version' and 'autoconf'. Then try again.

---

### Post by namelessone on 2007-06-13
> **Pumalite said:**
> Make sure you have kernel-headers and that they match your kernel version. Also make sure you have: 'make', 'automake''gcc latest version' and 'autoconf'. Then try again.

Yes, I have kernel headers, and I have make and the latest version of gcc that's in the ubuntu repo. I didn't have automake or autoconf, so i installed them, but it didn't help any. I still get the same error messages.

---

### Post by Pumalite on 2007-06-13
> **namelessone said:**
> Yes, I have kernel headers, and I have make and the latest version of gcc that's in the ubuntu repo. I didn't have automake or autoconf, so i installed them, but it didn't help any. I still get the same error messages.

Something is missing in your custom compiled kernel.

---

### Post by namelessone on 2007-06-13
yes, but *what* is missing?

I compiled my kernel using the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=157560"). My kernel compiled without errors, and seems to work fine.

---

### Post by namelessone on 2007-06-18
Well, I took the time to re-re-compile my kernel, and now everything is there...I don't know why it didn't work before...maybe it was because I didn't have automake or autoconf?

Now I have a new problem, though... X crashes when it starts up because it says that it can't find /dev/nvidiactl (no such device or address), but /dev/nvidiactl exists...

There is another /dev file called nvidia0 that is owned by root with group video...nvidiactl is owned by root with group root...do you think that nvidiactl needs to be in group video?

---

### Post by Pumalite on 2007-06-18
> **namelessone said:**
> Well, I took the time to re-re-compile my kernel, and now everything is there...I don't know why it didn't work before...maybe it was because I didn't have automake or autoconf?

Now I have a new problem, though... X crashes when it starts up because it says that it can't find /dev/nvidiactl (no such device or address), but /dev/nvidiactl exists...

There is another /dev file called nvidia0 that is owned by root with group video...nvidiactl is owned by root with group root...do you think that nvidiactl needs to be in group video?

If you now have the the packages I asked for before; you could try a coupla of things:



 At the command prompt: type sudo dpkg-reconfigure -phigh xsever-xorg

Then just select vesa as your video driver and use the space bar to select the resolutions
Then reboot.

If that doesn't work; you could try propietary drivers following this recipe: ( you have to download [with Live CD] the driver of your choice and place it in /home/<username>)

[http://ubuntuforums.org/showthread.php?t=470821](http://ubuntuforums.org/showthread.php?t=470821)

As an example, installation of NVIDIA driver: sudo sh NVIDIA-Linux-x86-xxxxxx.run

---

### Post by namelessone on 2007-06-18
> **Pumalite said:**
> If you now have the the packages I asked for before; you could try a coupla of things:



 At the command prompt: type sudo dpkg-reconfigure -phigh xsever-xorg

Then just select vesa as your video driver and use the space bar to select the resolutions
Then reboot. 

The thing is, I *want* the nvidia driver (for the full 3d capabilities of my card). That's why I'm going through all of this.

Here's what I've done:

Ctrl+Alt+F1
/etc/init.d/gdm stop
sudo mv ~/Desktop/nvidia*.run /usr/src
cd /usr/src
sudo chmod 775 nvidia*.run
sudo ./nvidia*.run

It then tried to look up on the internet to see if a module already existed for my linux kernel--there wasn't one because I have a custom compiled kernel. It then proceeded to compile the module...and then it asked me if I wanted it to reconfigure my xorg.conf for me I said yes. next I did /etc/init.d/gdm start...and i got the error I mentioned in mt last post.

---

### Post by Pumalite on 2007-06-18
> **namelessone said:**
> The thing is, I *want* the nvidia driver (for the full 3d capabilities of my card). That's why I'm going through all of this.

Here's what I've done:

Ctrl+Alt+F1
/etc/init.d/gdm stop
sudo mv ~/Desktop/nvidia*.run /usr/src
cd /usr/src
sudo chmod 775 nvidia*.run
sudo ./nvidia*.run

It then tried to look up on the internet to see if a module already existed for my linux kernel--there wasn't one because I have a custom compiled kernel. It then proceeded to compile the module...and then it asked me if I wanted it to reconfigure my xorg.conf for me I said yes. next I did /etc/init.d/gdm start...and i got the error I mentioned in mt last post.

You should do:
sudo /etc/init.d/gdm stop
sudo sh NVIDIA*.run
Accept the license
Let it reconf your xorg file, the, at the command prompt again, do:
sudo /etc/init.d/gdm start

That should work. (make sure you have your driver in /home/<username>)

---

### Post by namelessone on 2007-06-19
The way I did it was just as correct as the way you did it...but I did it your way just cuz i'm desperate...and guess what? I got the same error.](*,)

> can't find /dev/nvidiactl (no such device or address)

What does this mean? /dev/nvidiactl is there! I tried changing it's group to video and that didn't work, so I changed it back and changed it's permissions to 775 and that didn't work either! I am very very frustrated...can anyone help me?

---

### Post by namelessone on 2007-06-21
I did it! :-D After a little searching around the nvidia forums, I finally came up with a solution. I removed the package linux-restricted-modules-common, commented out the line in /etc/modprobe.d/lrm-video that said to use the lrm/video script with the nvidia module, added nvidia to /etc/modules, and now it all works!

Thanks for trying to help me, Pumalite!

---

### Post by semateos on 2008-03-16
I tried what you said above and am still having problems with my manual nvidia driver on startup - it works fine directly after I run the installer, I can do gdm and everything starts up fine, but when I reboot it doesn't work - goes to limited graphics mode - if I re-run the nvidia installer it works again... any ideas?

---

### Post by namelessone on 2008-03-16
well, here's a stab in the dark...

maybe something is screwing with your xorg.conf file. Since everything is installing okay, probably something (and I don't really know what that something is) is resetting your xorg.conf file back to the older settings

You ran the nvidia installer as root, right?

---

