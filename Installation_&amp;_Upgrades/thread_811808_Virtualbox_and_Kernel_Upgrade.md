---
title: "Virtualbox and Kernel Upgrade"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by mnorwood154 on 2008-05-29
Sorry if this post is a repetition of another post.  

With an upgrade to a new kernel version in Hardy Heron and after rebooting, I found that I could no longer start my Virtualbox VMs.  I was getting an error message regarding the kernel device /dev/vboxdrv. (Sorry don't remember the text of the error).  

To make Virtualbox work again I had to open Synaptic, uninstall all installed virtualbox packages, reinstall all virtualbox-xxx-generic packages,(only the ones without a kernel version in the name of the package which in turn prompts to install the correct virtualbox-xxx-kernelversion-generic packages) and then reboot.  After I did this, virtualbox works properly.

I hope this can help someone else that is having the same problem.

---

### Post by wolfen69 on 2008-05-29
try to start virtualbox again to check the message, but i believe it will say /etc/init.d/vboxdrv

you will need to restart this with:
```
sudo /etc/init.d/vboxdrv
``` again, double check the exact message. no need to uninstall anything.

---

### Post by Mr.TAEL on 2008-05-29
Update your modules .

(New modules is available on Update Manager)

```
sudo aptitude install virtualbox-ose-modules-2.6.24-17-generic
```

---

### Post by AliTabuger7 on 2008-05-29
This may not be true anymore, but about a week ago I had to temporarily enable the pre-release updates in order to download those modules.

---

### Post by Kristopher on 2008-06-04
Am needing 2.6.24-18 module added :(

---

### Post by grem91 on 2008-06-04
How long after a Kernel upgrade does the new VirtualBox Module become usually become available?

---

### Post by wkulecz on 2008-06-04
sudo /etc/init.d/vboxdrv setup

Shold rebuild the kernel modules and allow virtual box to run afterwards.

I use the "non-free" version from Sun, as I need USB support.

--wally.

---

### Post by grem91 on 2008-06-04
I just tried that,this appeared:

 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}

and it still doesn't work.

---

### Post by Joeb454 on 2008-06-04
What happens if you stop it first, then try setup?

And are you using the non OSS version from Sun or the OSE version in the repo's?

---

### Post by grem91 on 2008-06-04
I just tried stopping it, it made no difference. I am using the OSE version.

---

### Post by grem91 on 2008-06-04
Nevermind, I uninstalled and downloaded the .deb version from Sun's website and that works. Thanks anyway.

---

### Post by Chrierton on 2008-06-05
For now I'm just logging into the old kernel, 2.6.24-17.

---

### Post by lamborghiniwang on 2008-06-05
> **Chrierton said:**
> For now I'm just logging into the old kernel, 2.6.24-17.

Same here. Waiting for the kernel header for 2.6.24-18

---

### Post by Kristopher on 2008-06-09
Still waiting, anyone hear any word one when it will be added?

---

### Post by rathervague on 2008-06-09
I'm also awaiting advancement for kernel 2.6.24-18..

The last one appeared a few days after kernel was updated.

---

### Post by gareth_005 on 2008-06-10
The ose kernel driver for 2.6.24-18-generic is available in synaptic, I just installed it and started my xp vm, nice :)

---

### Post by rathervague on 2008-06-18
Geez.. now awaiting kernel 2.6.24-19

---

### Post by Fanless_Puppy_Fan on 2008-06-21
> **gareth_005 said:**
> The ose kernel driver for 2.6.24-18-generic is available in synaptic, I just installed it and started my xp vm, nice :)

Perhaps you could elaborate with a little more basic description of how you went about this for us noobs out here.

---

### Post by m_bridge on 2008-06-24
Yo guys there's no need to  wait for modules to appear on the repository
as you can make and install them quite easily.

1. Make sure you have kernel headers
2. Install  the 'virtualbox-ose-source (Source for the VirtualBox module)
   It will just install this file: /usr/src/virtualbox-ose.tar.bz2
3. extract that archive and cd into it
4. make
   if there's no error
5. sudo make install
6. sudo /etc/init.d/vboxdrv start

Now virtual machines should start just fine.

---

### Post by Fanless_Puppy_Fan on 2008-06-26
Thanks for the exact spoon-feeding I required. Update accomplished.

---

### Post by balaji.ramasubramanian on 2008-11-18
These instructions are rather not correct. They let you fix VirtualBox the hard way. You should not have to reinstall VirtualBox. This is no good fix. So here is what you should do. First try this command:

dpkg -l | grep linux-headers-`uname -r`

This should ideally give you a package name with details. This is to ensure that VirtualBox can rebuild itself for the new kernel on its own. Otherwise rebuild will fail. If the command does not give you a package name with linux-headers-..., then do the following:

sudo apt-get install linux-headers-`uname -r`

This should install the linux headers needed.

Now you only need to update VirtualBox using the following command: 

sudo /etc/init.d/virtualbox setup

It will take some time and recompile VirtualBox and you are ready to go as usual.

---

### Post by SpamIsCannedMeat on 2009-01-14
> **balaji.ramasubramanian said:**
> These instructions are rather not correct. They let you fix VirtualBox the hard way. You should not have to reinstall VirtualBox. This is no good fix. So here is what you should do. First try this command:

dpkg -l | grep linux-headers-`uname -r`

This should ideally give you a package name with details. This is to ensure that VirtualBox can rebuild itself for the new kernel on its own. Otherwise rebuild will fail. If the command does not give you a package name with linux-headers-..., then do the following:

sudo apt-get install linux-headers-`uname -r`

This should install the linux headers needed.

Now you only need to update VirtualBox using the following command: 

sudo /etc/init.d/virtualbox setup

It will take some time and recompile VirtualBox and you are ready to go as usual.

If you are using the 'non-free' version as I am (I also need USB support), you must change the last command in the above instructions to the following:

sudo /etc/init.d/vboxdrv setup

---

### Post by mellowtothemax on 2009-09-25
> **wkulecz said:**
> sudo /etc/init.d/vboxdrv setup

Shold rebuild the kernel modules and allow virtual box to run afterwards.

I use the "non-free" version from Sun, as I need USB support.

--wally.

This works. Thanks.

---

