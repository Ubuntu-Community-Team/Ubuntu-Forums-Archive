---
title: "Desktop won't load"
date: 2013-02-03
forum: Installation &amp; Upgrades
---

### Post by arizonalarry2 on 2013-02-03
Installed Ubuntu Studio 11.10, installed the proprietary graphics driver for GeForce 5200fx card, used the system for a while and everything worked fine.

Came here, did the Multimedia setup thing, everything went fine.

Rebooted, I get the 'Linux for Creative Humans' splash screen, then I get a black screen. No cursor, no nothing, just a black screen.

What went wrong?

---

### Post by MAFoElffen on 2013-02-04
> **arizonalarry2 said:**
> Installed Ubuntu Studio 11.10, installed the proprietary graphics driver for GeForce 5200fx card, used the system for a while and everything worked fine.

Came here, did the Multimedia setup thing, everything went fine.

Rebooted, I get the 'Linux for Creative Humans' splash screen, then I get a black screen. No cursor, no nothing, just a black screen.

What went wrong?
Which driver and what form of driver did you load? Packaged or binary?

There are many nvidia drivers on their site as well as many driver's that come up in Ubuntu's Additional Driver list when it comes up. The binary drivers from NVidia, you have to pick the right one for your card. 

The packaged driver's that come up in Additional Driver's, well previous versions of Ubuntu, it used to see what model you had and only presented the drivers that worked for that card. I notice that now, there is too much of a choice, so a user can pick a driver that doesn't work.

If you selected a driver and installed it, then did other work as you said, the video driver would not take affect until you rebooted. Then on reboot, it would look at the xorg.conf file to see which video driver to use.

If you boot, press shift to get to the grub menu. From the grub menu, go to the rescue menu. From the rescue menu, select the root prompt. From the root prompt:
```

sudo mv \etc\X11\xorg.conf \etc\X11\xorg.conf.bak

```
That will rename your xorg.conf file. 

On booting the graphics, since the system won't find a file specifically named "xorg.conf", the xorg-server will query the hardware to see what driver will work. It should end up falling back to xorg-driver-video-vesa or xorg-driver-video-nouveau... 

Basically, it should work for you again just like it did before you installed the last driver. 

If it stil doesn't boot into the graphics session, visit the Graphics Resolution link in my sig line... Some where in the first 3 posts will direct you to instructions on how to temporarily edit the grub boot line to add a nomodeset parameter.

From there, look at my 2nd post there for links to instructions on how to find the hardware ID number of your NVidia card, find the driver for that ID and to install the driver. Tell me how it goes here (in this thread.)

---

### Post by arizonalarry2 on 2013-02-04
Booted into the Grub menu, dropped down to the command line shell and typed in the command (being sure to include the sudo command part).

Result - got a message saying 'cannot rename, read-only file system'... never did ask for my password.

Then I tried booting an Ubuntu live DVD, went to the hard drive, and it said I couldn't change the permissions because I was not the owner.

How do you get out of read-only mode?


Hold on, got it - 

- Booted up live DVD (12.04)
- Pressed ctrl-atl-t to bring up a terminal
- Typed in 'gksudo nautilus' to start the nautilus shell (nautilus complained that it couldn't create a directory so I had to create it before it would start)
- Accessing the hard drive from the nautilus shell allowed me to rename the file.


Rebooted and it worked! 

I'm going to try some other drivers and see what happens, I'll post the results here.

Thanks for the help, really appreciate it!

---

### Post by arizonalarry2 on 2013-02-05
Really bad now - desktop icons disappeared and I can't get to my home folder, Firefox takes 30 seconds to load a page, Chromium crashes as soon as a page is loaded... guess I'll have to read up on how to write an xorg.conf file or something.

---

### Post by MAFoElffen on 2013-02-05
> **arizonalarry2 said:**
> Really bad now - desktop icons disappeared and I can't get to my home folder, Firefox takes 30 seconds to load a page, Chromium crashes as soon as a page is loaded... guess I'll have to read up on how to write an xorg.conf file or something.

Slow down and breath... 

Please tell me the driver you are trying to use. The one(s) you loaded.

Then post the results of this:
```

lspci -vnn | grep VGA

```
The post the results of 
```

uname -r

```
(That will list the kernel version you are running)
and Post
```

dpkg -l 'linux-*'

```
That will list out all he linux kernel packages that are installed. What we are looking for is the card you have, that the package you are selecting is the right one for that card, and that the kernel headers and source are there for that package to install correctly.

If you could also post the results of 
```

dpkg -l 'nvidia-*'

```
Then we can make sure that you don't have "fragments" of different nvidia drivers installed on top of each other... Safest way to install a different driver is to completely remove the old driver before you install a new one. But you didn't breathe first...

---

### Post by MAFoElffen on 2013-02-06
So here's what I'm suspecting, but need info from you to confirm.

You have installed drivers unsuccessfully twice on a new install(?).

- That could mean that you are installing the wrong driver for the card.

- If the correct driver, then it may not be being installed right because of unmet dependencies.

 -- If not installing right it could be that the header files for the linux kernel are not there to install it correctly.

 ---- If not there it may be that that kernel header file was not installed during upgrades. (A common recent problem.)

 ---- It may also be that your grub update did not default to the most recent kernel... What happens there is that update installs the new kernel, removes the header file for the old kernel, but due to a grub update problem, your system is not running on that newest kernel. When other packages try to install that require the kernel header file, it can't find the header for the kernel it's running on.

---

### Post by arizonalarry2 on 2013-02-06
> **MAFoElffen said:**
> 

Slow down and breathe... 



You know I've often told people Ubuntu would take their breath away but that's not exactly what I meant LOL.

> **MAFoElffen said:**
> 

Please tell me the driver you are trying to use. The one(s) you loaded.



I went to the Nvidia website and used their 'autodetect' feature which downloaded the package 'NVIDIA-Linux-x86-173.14.36-pkg1.run' which I then installed. According to the hex number of my card this is supposed to be the correct package.

> **MAFoElffen said:**
> 

Then post the results of this:
```

lspci -vnn | grep VGA

```



01:00.0 VGA compatible controller [0300]: nVidia Corporation NV34 [GeForce FX 5200] [10de:0322] (rev a1) (prog-if 00 [VGA controller])


> **MAFoElffen said:**
> 

The post the results of 
```

uname -r

```
(That will list the kernel version you are running)



3.0.0-30-generic


> **MAFoElffen said:**
> 
and Post
```

dpkg -l 'linux-*'

```



Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                      Version                   Description
+++-=========================-=========================-==================================================================
un  linux-doc-3.0.0           <none>                    (no description available)
ii  linux-firmware            1.60.1                    Firmware for Linux kernel drivers
ii  linux-generic             3.0.0.30.34               Complete Generic Linux kernel
un  linux-headers             <none>                    (no description available)
un  linux-headers-3           <none>                    (no description available)
un  linux-headers-3.0         <none>                    (no description available)
ii  linux-headers-3.0.0-12    3.0.0-12.20               Header files related to Linux kernel version 3.0.0
ii  linux-headers-3.0.0-12-ge 3.0.0-12.20               Linux kernel headers for version 3.0.0 on x86/x86_64
ii  linux-headers-3.0.0-30    3.0.0-30.47               Header files related to Linux kernel version 3.0.0
ii  linux-headers-3.0.0-30-ge 3.0.0-30.47               Linux kernel headers for version 3.0.0 on x86/x86_64
un  linux-headers-686-pae     <none>                    (no description available)
un  linux-headers-amd64       <none>                    (no description available)
ii  linux-headers-generic     3.0.0.30.34               Generic Linux kernel headers
un  linux-image               <none>                    (no description available)
un  linux-image-3.0           <none>                    (no description available)
ii  linux-image-3.0.0-12-gene 3.0.0-12.20               Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-3.0.0-30-gene 3.0.0-30.47               Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-generic       3.0.0.30.34               Generic Linux kernel image
un  linux-initramfs-tool      <none>                    (no description available)
un  linux-kernel-headers      <none>                    (no description available)
un  linux-kernel-log-daemon   <none>                    (no description available)
ii  linux-libc-dev            3.0.0-30.47               Linux Kernel Headers for development
un  linux-restricted-common   <none>                    (no description available)
ii  linux-sound-base          1.0.24+dfsg-0ubuntu2      base package for ALSA and OSS sound systems
un  linux-source-3.0.0        <none>                    (no description available)
un  linux-tools               <none>                    (no description available)


> **MAFoElffen said:**
> 
That will list out all he linux kernel packages that are installed. What we are looking for is the card you have, that the package you are selecting is the right one for that card, and that the kernel headers and source are there for that package to install correctly.



> **MAFoElffen said:**
> 
If you could also post the results of 
```

dpkg -l 'nvidia-*'

```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                      Version                   Description
+++-=========================-=========================-==================================================================
ii  nvidia-173                173.14.30-0ubuntu8.2      NVIDIA binary Xorg driver, kernel module and VDPAU library
un  nvidia-173-modaliases     <none>                    (no description available)
un  nvidia-180-modaliases     <none>                    (no description available)
un  nvidia-185-modaliases     <none>                    (no description available)
un  nvidia-96                 <none>                    (no description available)
ii  nvidia-common             1:0.2.35                  Find obsolete NVIDIA drivers
un  nvidia-current            <none>                    (no description available)
un  nvidia-current-modaliases <none>                    (no description available)
un  nvidia-libvdpau           <none>                    (no description available)
un  nvidia-libvdpau-ia32      <none>                    (no description available)
un  nvidia-libvdpau1          <none>                    (no description available)
un  nvidia-libvdpau1-ia32     <none>                    (no description available)
ii  nvidia-settings           280.13-0ubuntu2           Tool of configuring the NVIDIA graphics driver
un  nvidia-vdpau-driver       <none>                    (no description available)

[QUOTE=MAFoElffen;12494698]
Then we can make sure that you don't have "fragments" of different nvidia drivers installed on top of each other... Safest way to install a different driver is to completely remove the old driver before you install a new one. But you didn't breathe first...

Taking a nice deep breath now :p

---

### Post by MAFoElffen on 2013-02-06
Okay. 

Your card, an NVidia Geoforce FX5200, will work with Ubuntu 11.10 and newer. But is not capable of driving the stock setting of Unity (3D)... It can do Unity 2D and Gnome.

You are running on the newest kernel version and you have a matching kernel header file present for it. That is the good news.

If you look at the results for your nvidia drivers installed... and from what you just said... You need to backup, cleanup and make some decisions before you go back into the forward direction.

You could run the ubuntu packaged nvidia-173 --OR-- the binary installation acript that you downloaded from NVidia. I and others have felt that it is never a good idea to mix both methods in the same install. Sometimes files from each don't like playing together well.

If going from a packaged video driver to a binary driver(or the other way around)... or even from one driver version (EX- 96, 173 or current) of the same type to another... first cleanup (remove/purge) the old driver(s) before installing the new one.

A good example for that is that you have driver packages present for your card and two others that do not work for your card. nvidia-173 works with your card. nvidia-96 and nvidia-current do not work with your card. 

If you look at this post in my Graphics Resolution sticky, that is the latest method to install an NVidia binary driver "from" NVidia:
 [http://ubuntuforums.org/showpost.php?p=12487320&postcount=1126](http://ubuntuforums.org/showpost.php?p=12487320&postcount=1126)

_"You" really need to concentrate on section "2a", first and foremost._ Go directly to it and clean things up before installing *the driver type you will decide to install.*

Why did I say that last part? Because then you need to decide whether you want to go Ubuntu packed driver for NVidia, which is a binary driver from Nvidia, tested through 2 different PPA's (Edgers and XSwat) and tweaked before it goes to Main... Or Install the binary drivers directly from NVidia. As you can see from that post, these instructions are pretty detailed and it's just not running the script to get it going right.

Pro to the Binary driver file is that you are on the "latest" driver. People debate whether that is the best approach, but no matter. One drawback is that you have to occasionally remember tor run nviadia-installer to check for driver updates. Another is that sometimes during a release upgrade or some kernel upgrades, you may need to reinstall the driver.

The packaged drivers update during normal system updates. Sometimes during a major kernel update, you still may need to reinstall the driver, but not as often as the binary type driver. Just my experience on that.

If you do go back to a packaged driver, clean up the old (referred section 2a). Then
```

sudo apt-get install nvidia-173 nvidia-settings
sudo nvidia-xconfig

```

---

### Post by arizonalarry2 on 2013-02-07
Thank you, I appreciate all the help. It'll take me a while to work through all this, I want to take it slow and learn as much as I can. I'll let you know how it works out.

Thanks again!

---

### Post by MAFoElffen on 2013-02-07
If you do want to learn and/or need more reference, please feel free to visit my graphics sticky. The meat is in the first 3 posts. Post 2 has links to other info and tutorials within that sticky. Note that some has been updated later on in the thread. Sort of an admin problem prevents being able to edit and update those first 3 posts anymore. Some of the other tutorials have minor changes with 12.04 and 12.10... Posts older than 6 months became locked for editing. But most of it is correct, just some minor things changed. Such as you used to be able to remove and purge all nvidia drivers with a single global command... Now you have to name them individually. Minor things.

I'm currently rewriting a replacement for my graphics sticky that I hope will be easier for users to find information on up-to-date graphics tutorials, diagnostics, fixes and workarounds. I also still want the new sticky to remain as help desk place-to-go with their graphics problems. I have a plan...

---

