---
title: "x broken, v basic instruction needed"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by visctrix on 2007-02-10
Hey there, sorry but I've read as much of the warning re latest update thread and I can't work out what to do in my case.

The first step of the kernel upgrade went ok for me yesterday, then today I agreed to install updates, rebooted, and got a message that x was broken due to something about the nvidia-glx.

I managed to boot into the previous kernel from Grub (2.6.17.10...) and because I'd used envy in the past I went to [http://albertomilone.com/latest_nvidia_udsf_edgy.html]("http://albertomilone.com/latest_nvidia_udsf_edgy.html") and followed the instructions there:
```
sudo apt-get install linux-386
```
```
sudo apt-get install nvidia-glx-legacy nvidia-xconfig nvidia-settings
```
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
```
sudo nvidia-xconfig
```

Then I tried to reboot into the newest kernel version and x was still broken, then I found X was broken in all versions of Ubuntu and I'm now reduced to booting with a live cd.

Following advice on this forum I tried ```
sudo apt-get dist-upgrade
``` and ```
sudo aptitude dist-upgrade
``` and neither made any changes.

Now I read
> which
requires you to recompile and reinstall all third party kernel modules
you might have installed. If you use linux-restricted-modules, you
have to update that package as well to get modules which work with the
new kernel version. Unless you manually uninstalled the standard
kernel metapackages (linux-386, linux-powerpc, linux-amd64-generic), a
standard system upgrade will automatically perform this as well.
but I don't know how to do this.

I'm considering doing
```
sudo aptitude purge envy
```
```
sudo apt-get install envy_0.6.1-0ubuntu1_all.deb
```
```
envy
```

I really don't know what I'm doing though, as you can probably tell. Also it's taking me ages to constantly reboot, retry things, get the live cd up and running again. presumably I can't do this without removing the live cd and returning to my old installation...? Is there any useful admin I can do through the live cd, so I can continue mnitoring the forum?

Thanks

I'm running an old 1.2GHz AMD Athlon with a Nvidia GeForce 2 MX video card

---

### Post by mikewhatever on 2007-02-10
Hi, you can probably still boot in the old kernel, and I too have no idea what the following means.
> requires you to recompile and reinstall all third party kernel modules
you might have installed. If you use linux-restricted-modules, you
have to update that package as well to get modules which work with the
new kernel version. Unless you manually uninstalled the standard
kernel metapackages (linux-386, linux-powerpc, linux-amd64-generic), a
standard system upgrade will automatically perform this as well.

---

### Post by visctrix on 2007-02-10
> **visctrix said:**
> 
I'm considering doing
```
sudo aptitude purge envy
```
```
sudo apt-get install envy_0.6.1-0ubuntu1_all.deb
```
```
envy
```


I tried this, but none of the steps actually worked. Run out of ideas now.

Thanks for any help.

visctrix

I'm running an old 1.2GHz AMD Athlon with a Nvidia GeForce 2 MX video card

---

### Post by dabang on 2007-02-10
If you're using the nVidia drivers from [www.nvidia.com](www.nvidia.com) you have to install them again for the new kernel. If - like me - you're using the *nvidia-glx* drivers provided by Ubuntu you'll have to install the *linux-restricted-modules* for the new kernel. Boot into the old kernel, start synaptic, search for that package and install it. Reboot into the new kernel and you'll be fine. (I had the same problem...) I guess it's a bug in dependencies, because *linux-restricted-modules* should be updated automatically.

---

### Post by visctrix on 2007-02-10
Since I can't get into the GUI (I never get as far as the login screen) presumably I need to try to get to a command prompt again and type this?
```
sudo apt-get install linux-restricted-modules
```
Would that be right?
I did say v basic instructions needed...

Thanks :-)

---

### Post by persona_o on 2007-02-10
> **dabang said:**
> If you're using the nVidia drivers from [www.nvidia.com](www.nvidia.com) you have to install them again for the new kernel. If - like me - you're using the *nvidia-glx* drivers provided by Ubuntu you'll have to install the *linux-restricted-modules* for the new kernel. Boot into the old kernel, start synaptic, search for that package and install it. Reboot into the new kernel and you'll be fine. (I had the same problem...) I guess it's a bug in dependencies, because *linux-restricted-modules* should be updated automatically.

I'm having the exact same problem, but when using synaptic and selecting that module for installation it also wants to install "linux-image-2.6.17.11-386." But I thought I just updated to 2.6.17.11-386 from 2.6.17.10? 

I'm still pretty new to this whole linux thing, I just want to be careful that I don't mess my system up!

---

### Post by visctrix on 2007-02-10
I was able to log in to the old kernel (in recovery mode) briefly. Synaptic sid I already had the linux-restricted-modules installed, so I tried reinstalling them, but that din't help.

I also looked for anything I could find related to nvidia, glx, and envy, but I couldn't find anything that looked out of place or helpful.

Now I'm back to not being able to get into the GUI at all. I get the message:
> (EE) Failed to load /usr/lib/xorg/modules/libglx.so
(EE) Failed to load module @glx@ (loader failed, 7)
(EE) NVIDIA (0): Failed to initialize the GLX module; please
(EE) check in your X log file that the GLX module has
(EE) been loaded in your X Server, and that the module is
(EE) the NVIDIA GLX module. If you continue to encounter 
(EE) problems, please try reinstalling the NVIDIA driver.
FATAL: could not open '/lib/modules/2.6.17-11-386/volatile/nvidia.ko'

Now I just want to get rid of everything connected to Nvidia so I can use my computer again. It looks like I will only be able to do this from the command line but I need some instructions. Can anyone help?

Thanks

---

### Post by mikewhatever on 2007-02-10
> **dabang said:**
> If you're using the nVidia drivers from [www.nvidia.com](www.nvidia.com) you have to install them again for the new kernel. If - like me - you're using the *nvidia-glx* drivers provided by Ubuntu you'll have to install the *linux-restricted-modules* for the new kernel. Boot into the old kernel, start synaptic, search for that package and install it. Reboot into the new kernel and you'll be fine. (I had the same problem...) I guess it's a bug in dependencies, because *linux-restricted-modules* should be updated automatically.
That seemed like a logical move, but having installed 2.6.17-11-generic while booted in 2.7.17-10 kernel, did nothing at all to xserver.

---

### Post by visctrix on 2007-02-10
I ran dpkg-reconfigure xserver-xorg. Now I can boot up, but my screen resolution has gone down to 1024x768 maximum, and when I try to scroll down in Firefox I get a horrible and really slow rippling effect.

This is still effectively unuseable. Why has Ubuntu made me end up in this position? And will it be fixed soon?

---

### Post by LaneLester on 2007-02-15
> **visctrix said:**
> This is still effectively unuseable. Why has Ubuntu made me end up in this position? And will it be fixed soon?

I, like you, find it hard to understand that updates will be posted which break nvidia systems. It's not like nvidia is some weird brand. I had glx working great before this upgrade, now I don't know what to do (I'm running an old Kubuntu Dapper on another partition right now).

When I try to boot with the xorg.conf that was working before the upgrade, X says that I'm running X module 1.0-9746 and nvidia module 1.0-8776. But Synaptic says that the nvidia files are 9746. I don't know where the "8776" comes from.

Later: I was able to boot the .10 kernel instead of the new .11, and my good video was restored. I think I'll leave well enough alone for now.

Lane

---

