---
title: "Need help installing Nvidia beta v185.13"
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by GARoss on 2009-03-18
I'm hoping for this newbie to get some advice with AMD64 Nvidia drivers.
I downloaded these deb files from [https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)
 
[I][B]nvidia-glx-180_185.13-0ubuntu0~intrepid1_amd64.deb
nvidia-glx-180-dev_185.13-0ubuntu0~intrepid1_amd64.deb[/B]
nvidia-180-kernel-source_185.13-0ubuntu0~intrepid1_amd64.deb
nvidia-180-libvdpau_185.13-0ubuntu0~intrepid1_amd64.deb
nvidia-180-libvdpau-dev_185.13-0ubuntu0~intrepid1_all.deb
nvidia-180-modaliases_185.13-0ubuntu0~intrepid1_amd64.deb[/I]

As a newbie, it's not clear whether **one** or **all** are needed. I tried to install all of them. The last 4 would install, however the 1st 2 would not giving *xserver-xorg-core conflicts with xserver-xorg-video-4* error. After that, I re-booted & all I could use was the low graphic driver. I really had things screwed up! I did un-install the 4 that did install,
 
[I](nvidia-180-kernel-source_185.13-0ubuntu0~intrepid1_amd64.deb
nvidia-180-libvdpau_185.13-0ubuntu0~intrepid1_amd64.deb
nvidia-180-libvdpau-dev_185.13-0ubuntu0~intrepid1_all.deb
nvidia-180-modaliases_185.13-0ubuntu0~intrepid1_amd64.deb[/I]

& re-installed the 180.37s & got it back to where I started.

In an earlier thread, [http://ubuntuforums.org/showthread.php?t=1096124&highlight=185.13](http://ubuntuforums.org/showthread.php?t=1096124&highlight=185.13),
I found this post by plun;

> **plun said:**
> It works just fine but gave me some trouble during install

nvidia-glx-180 and dkms removed and also 180.37 from nVidia earlier installed.

also sanitized all nVidia.ko
```

locate nvidia.ko
```


```
sudo sh NVIDIA-Linux-x86_64-180.37-pkg2.run **--uninstall**
```

after that it was OK with a install....  "snappy" and good performance including Compiz.   

;)

If I'm understand the post, the old Nvidia drivers need to be un-installed first, true?

So, do I use the terminal to
```

locate nvidia.ko
```
& then 
```
sudo sh NVIDIA-Linux-x86_64-180.37-pkg2.run **--uninstall**
```

Then, install nvidia-glx-180_185.13-0ubuntu0~intrepid1_amd64.deb, or all of the downloaded deb files above?
If any of this sounds confusing, it's because I am!;)
All suggestions are appreciated.

---

### Post by paul_in_london on 2009-03-18
Instead of installing "manually", it would be easier to use this ppa:

[https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)

It includes the 64 bit packages.

---

### Post by caryb on 2009-03-18
> **paul_in_london said:**
> Instead of installing "manually", it would be easier to use this ppa:

[https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)

It includes the 64 bit packages.

Has anyone used this update with success?


Cary

---

### Post by GARoss on 2009-03-18
> **paul_in_london said:**
> Instead of installing "manually", it would be easier to use this ppa:

[https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)

It includes the 64 bit packages.
Paul,
These are the same files I've already tried & **failed** to install as I described above.

---

### Post by douham on 2009-03-18
> **caryb said:**
> Has anyone used this update with success?


Cary

Yep, I just downloaded 185.133 from the firstm's ppa and rebooted. No real improvements for me, but my card is only a 8400gs.
Doug

---

### Post by GARoss on 2009-03-18
> **caryb said:**
> Has anyone used this update with success?


Cary
As I stated in my 1st post, it seems the old ones must be un-installed first. The post by Paul points to the same launchpad site I downloaded & tried to, but fail to install. I'm sure they work, but, without more experience it's easy to make mistakes, as I did.

---

### Post by GARoss on 2009-03-18
> **douham said:**
> Yep, I deactivated the 180 driver and removed all instances of Nvidia from Synaptic first. Rebooted and downloaded 185.133 from the firstm's ppa, then reactivated the 180 driver. No real improvements for me, but my card is only a 8400gs.
Doug
So, deactivate the 180.37 driver to the low rez driver? & Un-install all 180.37 from Synaptic. Did you use all these;
(for AMD64)
[I]nvidia-glx-180_185.13-0ubuntu0~intrepid1_amd64.deb
nvidia-glx-180-dev_185.13-0ubuntu0~intrepid1_amd64.deb
nvidia-180-kernel-source_185.13-0ubuntu0~intrepid1_amd64.deb
nvidia-180-libvdpau_185.13-0ubuntu0~intrepid1_amd64.deb
nvidia-180-libvdpau-dev_185.13-0ubuntu0~intrepid1_all.deb
nvidia-180-modaliases_185.13-0ubuntu0~intrepid1_amd64.deb[/I]

or just the 1st one,  *nvidia-glx-180_185.13-0ubuntu0~intrepid1_amd64.deb which* is 16.6 mbs?

---

### Post by paul_in_london on 2009-03-18
> **GARoss said:**
> Paul,
These are the same files I've already tried & **failed** to install as I described above.

Hi,

Using this ppa ([https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)), I was able to upgrade to v185.13 successfully a few days ago. Admittedly that was 32 bit, so I don't know whether there's a problem specific to 64 bit here.

Add these entries to your apt sources list:

deb [http://ppa.launchpad.net/thefirstm/ppa/ubuntu](http://ppa.launchpad.net/thefirstm/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/thefirstm/ppa/ubuntu](http://ppa.launchpad.net/thefirstm/ppa/ubuntu) jaunty main

and then update/upgrade in the normal way.

From what I seem to remember reading at some point, the Nvidia installer doesn't necessarily uninstall the drivers cleanly and this can cause conflicts with official/ppa versions and/or mess up sym links.

Using a ppa also allows smoother transition when the official packages "catch up".

---

### Post by douham on 2009-03-18
In Synaptic, just tick for installation of the 180_185.13 kernel sources and all the other bits and pieces of the 185 driver (modaliases etc) will automaticaly be will required and added automatically.
You still have to add thefirstm's ppa and reload sources other wise the 180_185.13 drivers won't show up in Synaptic.

---

### Post by GARoss on 2009-03-18
Status report!
This is strange. The main reason to change to 185.13 was to see is one of my programs that mysteriously stopped working once the 180.11 drive was installed & didn't fix once the upgrade to 180.37 was made, would work again. The program, Bibble 5 Pro, is an beta version made for Linux as well as Mac & Windows.
So, I changed over to the 173 driver thinking there would be no conflicts while trying to install an 185 series driver. Well there was a conflict anyway, but out of curiosity I checked the Bibble program & it's working again!
At this moment I think I have the 185.13 installed, but I had to go to System/Administration/Nvidia Xserver Settings to see that it was. In any case, Bibble 5 Pro doesn't work with 185.13; only 173.
Another strange thing is in System/Administration/Hardware Drivers it simply says Nvidia. Normally there's several drivers listed. What happened there? What do I un-install to get that back?

---

### Post by paul_in_london on 2009-03-18
Yeah, Nvidia X Server settings seems to tell the truth and

paul@jaunty-sdb:~$ sudo egrep 185.13 /var/log/apt/term.log gives stuff like this:

Preparing to replace nvidia-180-kernel-source 180.37-0ubuntu1 (using .../nvidia-180-kernel-source_185.13-0ubuntu0_i386.deb) ...
Preparing to replace nvidia-180-libvdpau 180.37-0ubuntu1 (using .../nvidia-180-libvdpau_185.13-0ubuntu0_i386.deb) ...
Preparing to replace nvidia-180-modaliases 180.37-0ubuntu1 (using .../nvidia-180-modaliases_185.13-0ubuntu0_i386.deb) ...
Preparing to replace nvidia-glx-180 180.37-0ubuntu1 (using .../nvidia-glx-180_185.13-0ubuntu0_i386.deb) ...
Setting up nvidia-180-kernel-source (185.13-0ubuntu0) ...
driver version= 185.13
Setting up nvidia-180-libvdpau (185.13-0ubuntu0) ...
Setting up nvidia-180-modaliases (185.13-0ubuntu0) ...
Setting up nvidia-glx-180 (185.13-0ubuntu0) ...
 *  nvidia (185.13)...                                                          nvidia (185.13): Installing module.
 *  nvidia (185.13)...                                                          nvidia (185.13): Already installed on this kernel.
 *  nvidia (185.13)...                                                          nvidia (185.13): Already installed on this kernel.
 *  nvidia (185.13)...                                                          nvidia (185.13): Already installed on this kernel.
 *  nvidia (185.13)...                                                          nvidia (185.13): Installing module.
 *  nvidia (185.13)...                                                          nvidia (185.13): Already installed on this kernel.

---

### Post by Nullack on 2009-03-18
Its pretty simple

Turf the old driver, vdpau, nvidia settings
log out

stop gdm /etc/init.d/gdm stop
sudo sh NV (tab) to autcomplete the filename
Accept licence
Build module
Dont build 32bit compatability on 64bit
Dont allow installer to modify xorg.conf
Now modify xorf.conf to use nvidia instead of nv
start gdm /etc/init.d/gdm start

Your done

---

### Post by GARoss on 2009-03-19
After all the issues installing 185.13 it didn't fix an issue I having with one of my programs, so, I've reinstalled v173.14.16 & now the program is functioning again. I have made a reported in lauchpad. Basically, any nvidia driver from 180 & above causes the program to crash on launch. This is strange. I was hoping 185.13 would fix the issue but it doesn't, so, back to 173.
Finally, I must of deleted a package that offers a variety of drivers in System/Administration/Hardware Drivers. Now, it simply says Nvidia; that's all & it list the 71 driver in the discription.
What package needs to be restored to get this back to normal?

---

