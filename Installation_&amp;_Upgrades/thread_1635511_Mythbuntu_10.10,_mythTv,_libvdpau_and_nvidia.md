---
title: "Mythbuntu 10.10, mythTv, libvdpau and nvidia"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by dian_h on 2010-12-01
Allrigt, I am a noob, so take it easy with me ;)
 
I installed mythbuntu 10.10 a couple of days ago.
I had problem with my Nvidia card (as everyone else it seems). 
I have a Geforce3 Ti500 GPU card (and I am running on a 32-bit version).
 
First I had to enable all the (almost all) flags in the installation gui by pressing F6 (other options) (using live CD).
 
Then when the installation was made, it all froze at the startup.
I managed to get a prompt by holding ESC at startup (I never got it to work with CTRL+ALT+F1, it was perhaps me or perhaps that won't work before the system is restarted and the installation complete?).
 
Allright, to be able to startup, I downloaded new drivers (well, old ones it seems), 
NVIDIA-Linux-x86-96.43.19-pkg1.run 
 
I tried to install them (un-successfully) with following command:
sudo ./NVIDIA-Linux-x86-96.43.19-pkg1.run 
(have also tried with sudo sh ./NVIDIA-Linux-x86-96.43.19-pkg1.run )
 
The script told me that it didn't work, and I didn't manage to get much more info from it.
"The distribution-provided pre-install script failed".
(How can I get more info about the reason?)
 
Anyhow, after that I removed existing nvidia-drivers, and restarted and then installation worked and after that the freeze was gone.
(the installation process also disabled the nouveau, but I don't think that will affect it, right?)
 
However, when I try to configure mythTv backend I get an error-message telling me that the libvdpau.so.1 can't be found.
Not strange at all, since the file is not there.
The thing is that it was there before I removed the nvidia drivers, but never came back when I installed them again.
 
I believe that I removed the drivers in a bad way:
sudo apt-get --purge remove nvidia-*
 
Do you know if the fault was caused by my removal?
Do you have any ideas, how I can remove it in a better way?
Or perhaps you have another solution on the shelf?
 
Thanks in advance /dian_h the noob

---

### Post by dian_h on 2010-12-02
I have done some progress.
After installation of Mythbuntu 10.10 when I have the bootingproblem, I instead of removing nvidiastuff, changed some settings.
I modified /etc/11/xorg.conf (changed the text nvidia to nv)
I modified /etc/modprobe.d/blacklist.conf (added blacklist for vga16fb, nouveau, rivafb, nvidiafb, rivafb)
 
One of those changes made it boot up :-)
It seems like the xorg.conf made the difference (to be verified).

Note that I still haven't got the nvidia driver I am supposed to, thats next step now I guess.
 The backend setup also works now!
 
So my problem is now to install the nvidia driver.
I tried to use the packet manager to download/install it (found 96.43.18 as the closest one). Seems like its not completely installed so then I...
tried to use the nvidia-xconfig (manually), that one created a new xorg.conf file, so after that I had boot problems again.

If I try to install it by running sudo sh ./NVIDIA-Linux-x86-96.43.19-pkg1.run, I always end up with the error message mentioned above.
What happens when I write nv in the xorg.conf file?
Does anyone know why I get the error message when installing the package?
I heard that there are tools to handle those kind of drivers (like envy), is that to recommend?
I didn't find it in the packages presented by the packet manager, can someone specify where to find it (if you believe it's a good tool)?

---

### Post by dian_h on 2010-12-05
My problem is solved! :)

I succeeded to install the nvidia driver by ignoring the error-message:
"The distribution-provided pre-install script failed".
and continued the installation anyway.

This is something I have tried before, however is seems like it needed a restart before this action.

---

