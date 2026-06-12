---
title: "Kernel update"
date: 2011-09-19
forum: Installation &amp; Upgrades
---

### Post by An Sanct on 2011-09-19
Greetings!

I would like to update my Maverick (10.10 64b) kernel, currently 2.6.35-30-generic to the current version, that Oneiric 11.10 beta uses (and later to newer versions).

Is this even possible, will Maverick work afterwards? Is this just a stupid idea I got? Are you laughing at me right now? :) whichever it will be, post it here.

---

### Post by ibutho on 2011-09-19
Theoretically its possible. You'd need to edit your software sources, add the oneiric repos and install the desired kernel. I'm not sure how well the kernel would work with Maverick.

---

### Post by Frogs Hair on 2011-09-19
I read about a person using the latest kernel on 10.04 . If you have some idea what the benefits or drawbacks may be , feel free to play . If it is just an experiment I wouldn't recommend it .

---

### Post by VanR on 2011-09-19
I'm running 3.0.0-0300 on 10.10 (actually Zorin OS 4) basically because that kernel on my machine will mute my PC speakers when the headphones are plugged in. No other kernel I've used will do this. You can go [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) and download the kernel you want and use the software center to install it.

---

### Post by garvinrick4 on 2011-09-19
I run a Maverick on 3.0 kernel and up also. ( I do it because my wireless driver only works in N with a 3.0 kernel and up)
First you need to upgrade the module-init-tools to 3.13
[https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1](https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1)
click on 32 or 64 bit builds will take you to a page where you can download
a .deb package (lower left of page), download it and then click on it to install thru Ubuntu Software center
Next is headers and image.
_[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")_
Take the one of your choice 3.0 and up at bottom of page.
all.deb
32 or 64 bit headers (whichever is yours) uname -a
32 or 64 bit image (whichever is yours) uname -a
Download those 3 and install in that order, they are in .deb so if you click on will install
thru UBuntu software center. Install in order given, all.deb, headers, image.

If any trouble can install at command line;
Drop all three on Desktop:
cd Desktop
ls
sudo dpkg -i (copy and paste all.deb)
sudo dpkg -i (copy and paste headers)
sudo dpkg -i (copy and paste image)
Now reboot and enjoy your new Kernel.
To see the kernels installed in terminal:
grep menuentry /boot/grub/grub.cfg

---

### Post by An Sanct on 2011-09-20
Thank you all for your reply :), I will try the method garvinrick4 proposed and see what happens.

Don't worry, I'll play on a virtual machine first and then, if successful&happy, slowly move to production.

PS. I like to go "bleeding edge" as far as it does not mean recompiling the whole OS (if I wanted that, I would use gentoo ;)), so Im multi booting Maverick, Win8 dev preview and Oneiric beta ... I kind of dislike the Unity thingie :-?, but want to be up to date...

---

### Post by VanR on 2011-09-20
I like to use gdebi to install the kernel. Sometimes software center will hang for me.

---

### Post by Blasphemist on 2011-09-20
I do think you'll succeed with the instructions above. I do also want to note that bodhi linux 1.2 uses ubuntu 10.04 as its base but does use the 3.0.0 kernel. It also uses Enlightenment E17 instead of Gnome, etc.

---

