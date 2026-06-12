---
title: "Remove Nouveau &amp; install nVidia 96"
date: 2011-08-19
forum: Installation &amp; Upgrades
---

### Post by SilverbearSDCA on 2011-08-19
Preface that I'm a neophyte in Linux, however have installed a number of ubuntu distros and currently running the 11.04 Natty on older hardware with AMD64 and an AGP nVidia GeForce3 card.

Generally, my system runs great - but I hate the color. I used a shared monitor with my Win7 box (for my work with Adobe graphics suite) and the color is great. When I switch to ubuntu machine the color sucks and I want better tools to change _*refresh rate*_ as well as *color, hue, saturation, brightness & contrast.*

Under 10.10 the nVidia "additional hardware driver" worked well, however the version that want's to be validated under 11.04 does not work. The Nouveau driver has wrong refresh and so there is lots of flickering, and if I close a window fragments remain preventing viewing of windows that were below the closed one.

I know that nVidia driver 96.43.20 is the one I need and I've even downloaded this directly from nVidia but I have yet to find a method that works for removing nouveau and adding the nvidia legacy driver.

Should I just give up this search and resign myself to Windows superiority (g*d forbid! as I generally think Windows sucks) installing video drivers? A step-by-step process would be great - I'm not great with the command line - have searched everywhere and found nothing that worked.

---

### Post by Hakunka-Matata on 2011-08-19
no, don't give up yet, you've just got started.  
> @Amax As you don't post your sources, it  is hard to verify if they used the Additional Drivers installer or if  they did it manually. If you use the Additional Drivers installer as  suggested, Nouveau will be blacklisted from the kernel module prober.  However, if you install it manually, you need to create a file in /etc/modprobe.d/ that contains blacklist nouveau. &#8211; [Egil]("http://askubuntu.com/users/13570/egil") Apr 14 at 6:50


**AND** have you changed anything yet with the video driver?  Such as letting "System > Administration > Additional drivers" search, find and install the driver it thinks is best?

---

### Post by SilverbearSDCA on 2011-08-19
The additional drivers installer only gives the choice for the newer driver package which does not include my legacy card. I know this from experience (which forced a reinstall of nouveau).

---

### Post by realzippy on 2011-08-19
So why not stay with 10.04...
Your hardware simply reaches EOL.

---

### Post by Duncan Williams on 2011-08-19
make sure `nvidia current' is installed via synaptic or software manager, then have a look at `additional drivers' (after a reboot)

---

### Post by realzippy on 2011-08-19
> **Duncan Williams said:**
> make sure `nvidia current' is installed via synaptic or software manager, then have a look at `additional drivers' (after a reboot)

?????????????????????????????????

nVidia GeForce3

---

### Post by Duncan Williams on 2011-08-19
nvidia current installation triggers `additional drivers' to look at the nvidia drivers, and should allocate the correct one for your nvidia product!!!!!

---

### Post by Duncan Williams on 2011-08-19
[http://keithelder.net/2001/10/17/nvidia-geforce-3-under-debian-linux/](http://keithelder.net/2001/10/17/nvidia-geforce-3-under-debian-linux/)

[http://www.justlinux.com/forum/showthread.php?t=86994](http://www.justlinux.com/forum/showthread.php?t=86994)

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/155231](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/155231)

---

### Post by realzippy on 2011-08-19
> **Duncan Williams said:**
> [http://keithelder.net/2001/10/17/nvidia-geforce-3-under-debian-linux/](http://keithelder.net/2001/10/17/nvidia-geforce-3-under-debian-linux/)
10 years old.
> **Duncan Williams said:**
> 
[http://www.justlinux.com/forum/showthread.php?t=86994](http://www.justlinux.com/forum/showthread.php?t=86994)

7 years old.
> **Duncan Williams said:**
> 
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/155231](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/155231)
3 years old.

nvidia-current is the current nvidia-driver,as the name says.
It "triggers" nothing for a geforce 3 card.
This chip is not supported by the current nvidia driver.
It needs the 96.xx driver.No kernel modules for this old driver exist,so they are not offered by jockey (additional drivers GUI)

---

### Post by Duncan Williams on 2011-08-19
fair enough, they used to recognise my old fx5200 card. Old posts for old card. I had no reference in `additional drivers' awhile back and installing nvidea current then made it suggest drivers, but as you said if the kernel don't know what it is then it can't.

---

### Post by Duncan Williams on 2011-08-19
I can highly recommend a cheap new video card that flies in ubuntu.
nvidia geforce 6200 (based on 6800 series) only $40 here with 1/2 gig and it loves linux...

---

### Post by Duncan Williams on 2011-08-19
previously stated: *make sure `nvidia current' is installed via synaptic or software manager, then have a look at `additional drivers' (after a reboot)*

sorry guys meant:

make sure `**nvidia common**' is installed via synaptic or software manager, then have a look at `additional drivers' (after a reboot)

(me=To many tabs and not enough brains)

---

### Post by realzippy on 2011-08-19
ahhh,that makes sense now.  ;-)

---

