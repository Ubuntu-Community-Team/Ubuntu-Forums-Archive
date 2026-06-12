---
title: "Problem Installing a Program."
date: 2011-08-27
forum: Installation &amp; Upgrades
---

### Post by noisysoul on 2011-08-27
(SOLVED - THANK YOU SO MUCH :D)

Hi!

I use:
- Ubuntu 11.04
- Unity > Ubuntu Classic (Gnome)

I was trying to install a program (using Ubuntu Software Centre) and it shows up a message saying: "To install -Pogram Name-, these items must be removed:" and it shows a list of packages that I dare not to delete, it also has 2 buttons: "Install Anyway" and "Cancel".

This way:

[[img]http://www.freeimagehosting.net/t/0dc7a.jpg[/img]](http://www.freeimagehosting.net/0dc7a)

[SIZE="3"]_**So I don't know what to do, please help me! Thanks a lot  :)**_[/SIZE]

---

### Post by ottosykora on 2011-08-27
well lot of programs can not exist simultaneously on one system. 
You may have some similar program installed on the system and so the other doing probably something very same must be removed.
Sometimes it means only that some libs has to be removed and will be replaced by other version or other lib doing same thing, but needed by the program you want install.

So I recommend you to leave it remove the libs in question, as they will probably be simply replaced by something doing the same job.

---

### Post by saltmarshlamb on 2011-08-27
If you ran the install command from the terminal it would show you exactly what was being installed and removed - it's very likely that the list would be longer than you imagine, doing so on a xubuntu install gives 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apport-hooks-medibuntu dvdauthor imagemagick libavcodec-extra-52
  libavformat-extra-52 libavutil-extra-50 libbluray0 libcdt4 libgraph4 libgvc5
  libiso9660-7 liblircclient0 liblqr-1-0 liblzo2-2 libmagickcore3
  libmagickcore3-extra libmagickwand3 libnetpbm10 libopenjpeg2 libpathplan4
  libpostproc-extra-51 libsvga1 libswscale-extra-0 libvcdinfo0 libvdpau1
  mencoder mplayer netpbm vcdimager
Suggested packages:
  imagemagick-doc autotrace curl enscript ffmpeg gnuplot grads hp2xx html2ps
  libwmf-bin povray radiance texlive-base-bin transfig ufraw-batch libfaad0
  libbluray-bdj lirc nvidia-vdpau-driver vdpau-driver mplayer-doc netselect
  fping
The following packages will be REMOVED
  libavcodec52 libavformat52 libavutil50 libpostproc51 libswscale0
The following NEW packages will be installed
  apport-hooks-medibuntu devede dvdauthor imagemagick libavcodec-extra-52
  libavformat-extra-52 libavutil-extra-50 libbluray0 libcdt4 libgraph4 libgvc5
  libiso9660-7 liblircclient0 liblqr-1-0 liblzo2-2 libmagickcore3
  libmagickcore3-extra libmagickwand3 libnetpbm10 libopenjpeg2 libpathplan4
  libpostproc-extra-51 libsvga1 libswscale-extra-0 libvcdinfo0 libvdpau1
  mencoder mplayer netpbm vcdimager
0 upgraded, 30 newly installed, 5 to remove and 1 not upgraded.
Need to get 16.8 MB/17.6 MB of archives.
After this operation, 31.0 MB of additional disk space will be used.
```

---

### Post by Mark Phelps on 2011-08-27
If, as you say, you "dare not delete them" -- then you are stuck.

You can't have both Libav and your other app on your PC at the same time.  

I would not go just removing objects.  As mentioned, you should run the command in the terminal to see the FULL list of items it will remove.  If some are used by other apps, that removal will break them as well.

---

### Post by noisysoul on 2011-08-27
Thank you so much buddies! I'll unistall the other program and see what happens, if there are still too much packages to be uninstalled I'd rather look for a different program instead of running such a risk. I really appreciate your opinions, and your explanations couldn't have been better. Thanks a lot =D
Greetings from Chile.

---

