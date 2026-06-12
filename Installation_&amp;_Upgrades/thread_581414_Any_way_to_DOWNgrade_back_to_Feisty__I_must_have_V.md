---
title: "Any way to DOWNgrade back to Feisty?  I must have VMWare Player."
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by davidshere on 2007-10-19
I upgraded this morning to 7.10 and it appears to have whacked VMWare Player on my machine.  I just tried to reinstall and it says "VMware Player cannot be installed on your computer type (i386) Either the application requires special hardware features or the vendor decided to not support your computer type."

I have two virtual machines that I must start back up, a mail server and a web server.  Is there any way to down grade back to Feisty?

I'm a little irked about this, but I'm trying to stay calm.  I have a good attitude.

---

### Post by adaddona on 2007-10-19
Yes, I had the same issue. I had to remove the  linux-image-2.6.22-14-386 and modules. I rebooted with the geneic kernel and vmware worked again. This also fixed the sound card on my Dell 390.

---

### Post by loganm10 on 2007-10-19
you shouldnt have to uninstall the kernel, when your computer boots GRUB loads, if you hit ESC right when it loads, it should give you a list of kernels, just choose the feisty kernel


But you should be able to reinstall vmware, ive done it, it does require a fresh install everytime you get a new kernel

are you sure you are using the same arch? did you switch to amd64? because you would have to redownload the amd64 version of vmware if you did

---

### Post by davidshere on 2007-10-19
Is the Feisty kernel just the 2nd one down?  I suppose I could just try that instead of just asking.

---

### Post by itismike on 2007-10-19
> **davidshere said:**
> I upgraded this morning to 7.10 and it appears to have whacked VMWare Player on my machine...

I don't think I'm overstating it to say that this is unacceptable.  Not what I was looking forward to after a fresh install of 7.10. :mad:

---

### Post by davidshere on 2007-10-22
bump

I tried installing the VMWare player after booting the computer under each of the kernels available to me on the Grub menu.  Each time I got the same error message as above.

I definitely want to go back to Feisty.  Can I do so without reinstalling?

---

### Post by davidshere on 2007-10-22
Well I backed up my data and I'm reinstalling fresh with Feisty.  My dog will be happy.

Very disappointing.  I hope they fix this in 8.04.

---

### Post by fridaythe14th on 2007-10-23
Here's the bug:
[https://bugs.launchpad.net/ubuntu/+bug/155362](https://bugs.launchpad.net/ubuntu/+bug/155362)

VMWare needs to be recompiled from source every time you update your kernel (VMWare Server anyway), there's supposed to be a script included in WMWare for updating after a kernel update ("/usr/bin/vmware-config.pl"), but if you installed the ubuntu package you didn't get that script.

---

### Post by davidshere on 2007-10-23
Ya got any info on VMWare player?  I just need the player.

No biggie if you don't... I already re-installed Feisty: [http://ubuntuforums.org/showthread.php?t=588112](http://ubuntuforums.org/showthread.php?t=588112)  ... and my virtual machines are happily up and running.

I beta tested Gutsy on two different machines for the last two months -- one real one and one virtual one.   I wish I had tried to install VMWare Player.

---

### Post by BoardDWorld on 2007-10-23
Guys VirtualBox is awesome! Just add it from your add/remove programs app. remember to enable universe and add the following after you have installed it:

```
sudo gpasswd -a YOURUSERNAME vboxusers
```

---

### Post by outlaw686 on 2007-10-23
see if you are useing the 386 kernel by typing "uname -r" in the terminal. try booting in generic by hitting esc when grub loads. [http://ubuntuforums.org/showthread.php?t=580833&highlight=386+kernel](http://ubuntuforums.org/showthread.php?t=580833&highlight=386+kernel)

---

### Post by davidshere on 2007-10-23
I tried that, in fact, with all of the available kernels.  I still was not allowed to install VMware Player.  I have a screenshot; I've actually posted about this in another thread somewhere.

---

### Post by dalebert on 2007-10-25
My drawing pad quit working completely when I upgraded and this is one of the main things I use my computer for. It took a lot of work to get it working on FF. I'm going to try recompiling the driver that I downloaded for it, but I couldn't help noticing that no one has yet posted an answer as to whether it's possible to downgrade back to FF without a complete re-install. Anyone know if it can be done?

---

### Post by komputes on 2007-11-19
I got this error as well, and so I decided to do it manually instead of through add/remove or synaptic package manager.


1) Download the player
[URL="http://download3.vmware.com/software/vmplayer/VMware-player-2.0.2-59824.i386.tar.gz"]http://download3.vmware.com/software/vmplayer/VMware-player-2.0.2-59824.i386.tar.gz
[/URL]
2) Untar and run install script (read and answer all questions)
```
tar -xvvf VMware-player-2.0.2-59824.i386.tar.gz 
cd vmware-player-distrib/
sudo ./vmware-install.pl

```
3)Run VMware Player
```
vmplayer
```

Hope this helps.

---

### Post by davidshere on 2007-11-19
I believe I did something similar and didn't get anywhere.  The problem came when it wanted to recompile my kernel.  I did my best to answer all the questions that it asked me, but it was unable to proceed past that point.  I can't recall further details.

I've already downgraded back to Feisty, and I'll probably stay here until vmware is installable through the add/remove programs under Gutsy, or Hardy, or whatever comes out in the future.

---

