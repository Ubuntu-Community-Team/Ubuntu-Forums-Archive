---
title: "Problem installing certain packages, held broken packages error."
date: 2015-10-26
forum: Installation &amp; Upgrades
---

### Post by amantripathi4u on 2015-10-26
Hello community. I am using Kubuntu 15.10, It is running well but when I try to install certain packages like: 

```
gnu[FONT=monospace][COLOR=#000000]@WorkstationUbuntu:~$ sudo apt-get install clipgrab[/COLOR]
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 clipgrab : Depends: libav-tools (>= 6:9.14)
            Depends: libavcodec-extra-56 (>= 6:11-1) but it is not installable
E: Unable to correct problems, you have held broken packages.

[/FONT]
```

I get above error. For solving the error, I searched several forums and got suggestions like using: 
```
sudo apt-get install -f
```
```
sudo dpkg --configure -a
```

and many more....
here dpkg--configure doesn't produces any output, and apt-get install -f only shows 
```
gnu[FONT=monospace][COLOR=#000000]@WorkstationUbuntu:~$ sudo apt-get install -f[/COLOR]
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmikmod3 libsdl-net1.2 libsdl-sound1.2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/FONT]
```

also when I try to get held packages by using: 

```
sudo apt-mark showheld
```

It also doesn't provide any output.

Synaptic is not showing any broken packages as well.

when I try to install missing dependencies individually, for example: 

```
gnu[FONT=monospace][COLOR=#000000]@WorkstationUbuntu:~$ sudo apt-get install libav-tools[/COLOR]
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Note, selecting 'libav-tools-links' instead of 'libav-tools'
The following packages were automatically installed and are no longer required:
  libmikmod3 libsdl-net1.2 libsdl-sound1.2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ffmpeg libavdevice-ffmpeg56 libavfilter-ffmpeg5 libavresample-ffmpeg2 libpgm-5.1-0
  libsodium13 libzmq3
Suggested packages:
  ffmpeg-doc
The following NEW packages will be installed:
  ffmpeg libav-tools-links libavdevice-ffmpeg56 libavfilter-ffmpeg5 libavresample-ffmpeg2
  libpgm-5.1-0 libsodium13 libzmq3
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 134 kB/2,248 kB of archives.
After this operation, 5,034 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
[/FONT] 
```

It install some packages but some times it removes other important packages as well.

I am continuously getting this problem and tried nearly everything, even installed Kubuntu from scratch.

Kindly tell me the way to sort out this problem. Tell  me how can I install every essential dependency required to run kubuntu properly.
Any help is appreciated. Thanks in advance.

---

### Post by Bucky Ball on 2015-10-26
Have you installed kubuntu-restricted-extras and can you install other things just fine and are only having issues with Clipgrab? As Clipgrab is intended to download clips from Youtube we will not provide support for installing it, so please don't ask. Thanks. 

See [here]("http://ubuntuforums.org/showthread.php?t=1850955").

---

### Post by amantripathi4u on 2015-10-26
Yes I have installed kubuntu-restricted-extras. Currently I am getting problem with Clipgrab, but as I said I have reinstalled the system, and before reinstalling I was getting same problem with many packages like yakuake, kdenlive etc. Also if you don't provide support regarding clip grab, I request you to provide me the way, to resolve such problems, in future. And yes, thanks for your rapid response.

---

### Post by Bucky Ball on 2015-10-26
What problems are you getting now, not prior to the reinstall? Are you only having problems with Clipgrab or do you need help with something we can help you with?

> **amantripathi4u said:**
> ... if you don't provide support regarding clip grab, I request you to provide me the way, to resolve such problems, in future.

That would be providing you with support to install Clipgrab, so you are on your own getting that to work, sorry. Good luck.

We can only really give you effective support with issues you are having now, and that excludes Clipgrab.

---

### Post by amantripathi4u on 2015-10-26
> **Bucky Ball said:**
> What problems are you getting now, not prior to the reinstall? Are you only having problems with Clipgrab or do you need help with something we can help you with?



That would be providing you with support to install Clipgrab, so you are on your own getting that to work, sorry. Good luck.

We can only really give you effective support with issues you are having now, and that excludes Clipgrab.

Thanks Bucky Ball. I am not getting this problem with other packages, as of now. I would let you know if get any. Also I would like to share one more problem with you, after reinstalling the system I am not able to install and activate new services menu items in Dolphin file manager. They are not working. When I try to download new services, it says it is installed, but they doesn't show up in services selection menu, or in context menu. I would I appreciate if you provide me with some workaround for the same as well. Thanks very much again.
P.S. System is fully updated, with (may be) all important packages installed. And I have tried to reinstall the kubuntu desktop as well.

---

### Post by Bucky Ball on 2015-10-26
As you are now asking support for something we can give you support with, and it is not related to the title of this thread, I suggest you post a new thread with a title describing the services problem in the appropriate forum section and we close this one. If you include the last part of your last post in the new thread:

> ... after reinstalling the system I am not able to install and activate new services menu items in Dolphin file manager. They are not working. When I try to download new services, it says it is installed, but they doesn't show up in services selection menu, or in context menu. I would I appreciate if you provide me with some workaround for the same as well. Thanks very much again.
P.S. System is fully updated, with (may be) all important packages installed. And I have tried to reinstall the kubuntu desktop as well. 

... and add anything else you can think that might help potential helpers (which release and flavour of Ubuntu you are using) that would be a good start. This will improve your chances of support for your new problem as it will describe your new problem on a thread with an appropriate title and you won't have your support request buried half way down the page. 

Good luck with it and I will no doubt spot the thread in my travels. :)

*Thread closed.*

---

