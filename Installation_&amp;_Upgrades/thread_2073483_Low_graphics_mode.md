---
title: "Low graphics mode"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by canadianwriterman on 2012-10-19
I'm having an issue with a clean install of 12.10 Ubuntu 64-bit. It's similar to other posts I've seen to do with GRUB and nvidia, but in my case it's happening with Intel HD4000 graphics. I get a window on bootup with "Low graphics mode." It happens about 90% of the time I boot. I have to keep rebooting until my graphics card is finally recognized. Any suggestions, folks?

---

### Post by pesho21 on 2012-10-20
I have the same problem. My processor is i3 2125 with embedded intel hd3000 graphics.

---

### Post by canadianwriterman on 2012-10-20
Seems there are only the two of us, pesho21. There are many posts about xorg and the display manager having issues related to the nvidia video driver, but none about the Intel video driver in 12.10.

---

### Post by pesho21 on 2012-10-21
This sounds badly for us. I tried to understand when the problem is occurred, but it seems that the problem is reproducing randomly. In my case it happens in 60-70% of boot times.

---

### Post by pesho21 on 2012-10-21
I have reinstalled my 64 bit Ubuntu 12.10, but this doesn't help. Ubuntu 12.10 is the best Ubuntu I've ever seen, but this issue makes me crazy. If someone can help - I'll be very grateful.

---

### Post by ronzo on 2012-10-21
Same problem here. Intel HD4000 Graphics. Here's a snippet of the Xorg.log:

```
[     1.967] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
	Ivybridge Server (GT2), Haswell Desktop (GT1), Haswell Desktop (GT2),
	Haswell Desktop (GT2+), Haswell Mobile (GT1), Haswell Mobile (GT2),
	Haswell Mobile (GT2+), Haswell Server (GT1), Haswell Server (GT2),
	Haswell Server (GT2+), Haswell SDV Desktop (GT1),
	Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT2+),
	Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
	Haswell SDV Mobile (GT2+), Haswell SDV Server (GT1),
	Haswell SDV Server (GT2), Haswell SDV Server (GT2+),
	Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
	Haswell ULT Desktop (GT2+), Haswell ULT Mobile (GT1),
	Haswell ULT Mobile (GT2), Haswell ULT Mobile (GT2+),
	Haswell ULT Server (GT1), Haswell ULT Server (GT2),
	Haswell ULT Server (GT2+), Haswell CRW Desktop (GT1),
	Haswell CRW Desktop (GT2), Haswell CRW Desktop (GT2+),
	Haswell CRW Mobile (GT1), Haswell CRW Mobile (GT2),
	Haswell CRW Mobile (GT2+), Haswell CRW Server (GT1),
	Haswell CRW Server (GT2), Haswell CRW Server (GT2+),
	ValleyView PO board
[     1.968] (II) VESA: driver for VESA chipsets: vesa
[     1.968] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     1.968] (II) FBDEV: driver for framebuffer: fbdev
[     1.968] (++) using VT number 7

[     1.968] (II) intel(0): using device path '/dev/dri/card0'
[     1.968] (WW) Falling back to old probe method for vesa
[     1.968] (WW) Falling back to old probe method for modesetting
[     2.031] (WW) Falling back to old probe method for fbdev
[     2.031] (II) Loading sub module "fbdevhw"
[     2.031] (II) LoadModule: "fbdevhw"
[     2.031] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     2.031] (II) Module fbdevhw: vendor="X.Org Foundation"
[     2.031] 	compiled for 1.13.0, module version = 0.0.2
[     2.031] 	ABI class: X.Org Video Driver, version 13.0
[     2.086] (EE) intel(0): [drm] Failed to open DRM device for pci:0000:00:02.0: No such file or directory
[     2.086] (EE) intel(0): Failed to become DRM master.
[     2.086] (II) UnloadModule: "intel"
[     2.086] (EE) Screen(s) found, but none have a usable configuration.
[     2.086] 
Fatal server error:
[     2.086] no screens found
[     2.086] (EE) 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[     2.086] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[     2.086] (EE) 
[     2.150] Server terminated with error (1). Closing log file.

```

---

### Post by pesho21 on 2012-10-21
Here is the snippet from the Xorg.0.log.old. I found only this error:

```
[    14.072] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
	Ivybridge Server (GT2), Haswell Desktop (GT1), Haswell Desktop (GT2),
	Haswell Desktop (GT2+), Haswell Mobile (GT1), Haswell Mobile (GT2),
	Haswell Mobile (GT2+), Haswell Server (GT1), Haswell Server (GT2),
	Haswell Server (GT2+), Haswell SDV Desktop (GT1),
	Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT2+),
	Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
	Haswell SDV Mobile (GT2+), Haswell SDV Server (GT1),
	Haswell SDV Server (GT2), Haswell SDV Server (GT2+),
	Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
	Haswell ULT Desktop (GT2+), Haswell ULT Mobile (GT1),
	Haswell ULT Mobile (GT2), Haswell ULT Mobile (GT2+),
	Haswell ULT Server (GT1), Haswell ULT Server (GT2),
	Haswell ULT Server (GT2+), Haswell CRW Desktop (GT1),
	Haswell CRW Desktop (GT2), Haswell CRW Desktop (GT2+),
	Haswell CRW Mobile (GT1), Haswell CRW Mobile (GT2),
	Haswell CRW Mobile (GT2+), Haswell CRW Server (GT1),
	Haswell CRW Server (GT2), Haswell CRW Server (GT2+),
	ValleyView PO board
[    14.072] (II) VESA: driver for VESA chipsets: vesa
[    14.072] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    14.072] (II) FBDEV: driver for framebuffer: fbdev
[    14.072] (++) using VT number 7

[    14.756] vesa: Ignoring device with a bound kernel driver
[    14.756] (WW) Falling back to old probe method for vesa
[    14.800] (WW) Falling back to old probe method for modesetting
[    14.800] (II) modesetting(2): using default device
[    14.800] (II) Loading sub module "fbdevhw"
[    14.800] (II) LoadModule: "fbdevhw"
[    14.800] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    14.800] (II) Module fbdevhw: vendor="X.Org Foundation"
[    14.800] 	compiled for 1.13.0, module version = 0.0.2
[    14.800] 	ABI class: X.Org Video Driver, version 13.0
[    14.800] (**) FBDEV(3): claimed PCI slot 0@0:2:0
[    14.800] (II) FBDEV(3): using default device
[    14.800] (EE) Screen 0 deleted because of no matching config section.
[    14.800] (II) UnloadModule: "vesa"
[    14.800] (EE) Screen 0 deleted because of no matching config section.
[    14.800] (II) UnloadModule: "modesetting"
[    14.800] 
Fatal server error:
[    14.800] Cannot run in framebuffer mode. Please specify busIDs        for all framebuffer devices
[    14.800] 
[    14.800] (EE) 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    14.800] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    14.800] (EE) 
[    14.807] Server terminated with error (1). Closing log file.
```

---

### Post by Floaty on 2012-10-21
Hello, I have the same problem. I did find a workaround however annoying.

I often end up with the "Your system is running in low-graphics mode"
Reboot does not help.
I found that if I, when the error occurs, reinstall lightdm then it's all ok for a while.
Like this:
I see the error and press ctrl+alt+F1 and login.
sudo su
service lightdm stop
aptitude reinstall lightdm
reboot
*** edit***
I just found a different method.
ctrl+alt+F1 and login
sudo service lightdm restart
***/edit***

Then things are ok for a while. How come it's necessary to do that?
Can it be fixed somehow?

Ubuntu 12.10 with Unity
Asus P8Z77-V pro/Thunderbolt
Intel Core i7 3770
Intel HD4000

---

### Post by pesho21 on 2012-10-21
This works only for the first boot after reboot. After that the problem has appeared again.

---

### Post by fjgaude on 2012-10-21
I'm using Intel HD3000 and have the same issue on both 12.10 and 12.04, but only from partitions that are on SSDs.

```
ctrl+alt+F1 and login
sudo service lightdm restart
```

The above works for me when I get a black screen with the cursor blinking in the upper left-hand corner.

On an HDD with 12.04 and 11.10, installed early in the dev cycles I have no such issue. I even DDed the 12.04 to an SSD partition and the issue returned. So I think it is a 'race' problem with the speed of an SSD and lightdm loading. Just a guess, of course.

Anyone here have a permanent fix for this?

---

### Post by Floaty on 2012-10-21
My install is on a ssd also.
I have changed from lightdm/unity to gdm/gnome-shell and so far (only a few boots) no problems.
I wanted to try out Unity so using gnome is really not what I had in mind.
If it's a race problem it would be solved by installing on a traditional hard drive perhaps.
But that was not what I had in mind either.

Anybody else using ssd?

---

### Post by pesho21 on 2012-10-22
My install is NOT on ssd. My hdd is 2,5" 150gb. I also think, that this is some kind of synchronization problem.

@fjgaude your proposal works for me, is it possible to implement some script, that at boot time restart lightdm ?

---

### Post by Arkandias on 2012-10-22
Hi everyone. Same problem here !
Intel HD Graphics and SSD ; Ubuntu 12.10 randomly boots with "system in low graphic mode" error ; Xorg log says "Fatal Error : no screens found"...
I have been seaching for several days, no solution yet.

---

### Post by Arkandias on 2012-10-22
Some precisions : I am using 64 bits version too, and since screens seems to be involved in this, mine is a Iiyama XB2374HDS...

Here is a funny thing : for other reasons I had to replace the DVI cable by a HDMI one, and since then I had no boot problem. I do not see why this would change anything but still, no problem with HDMI for now...

---

### Post by fjgaude on 2012-10-22
> **pesho21 said:**
> My install is NOT on ssd. My hdd is 2,5" 150gb. I also think, that this is some kind of synchronization problem.

@fjgaude your proposal works for me, is it possible to implement some script, that at boot time restart lightdm ?

The startup routine is complex, AFAIK, and I would not know where to put an addition to it all.

Maybe someone here who has the technical knowledge could help.

Yes, please help!

---

### Post by fjgaude on 2012-10-22
> **Arkandias said:**
> Some precisions : I am using 64 bits version too, and since screens seems to be involved in this, mine is a Iiyama XB2374HDS...

Here is a funny thing : for other reasons I had to replace the DVI cable by a HDMI one, and since then I had no boot problem. I do not see why this would change anything but still, no problem with HDMI for now...

Well, my monitor is DVI only. I can't see how that and SSD has anything to do with my issue. I have no problem when booting from an HHD, just SSD.

Hopefully someone or something will come along that points to a solution for us who are using SSDs.

---

### Post by pesho21 on 2012-10-22
I'm using HDD and HDMI and the problem is here. So I don't think, that this is related to Hard disk type or output port.

---

### Post by fjgaude on 2012-10-22
> **pesho21 said:**
> I'm using HDD and HDMI and the problem is here. So I don't think, that this is related to Hard disk type or output port.

The issue is really how the OS detects the capability of the hardware, if it is fast enough for Unity3D or not, something of that sort. And the testing, parsing the results determines what is selected. In our case 'low-res graphics'. Ugh! 

It seems to involves the dm lightdm and restarting it, but who can say for sure? I wonder if we could delete it and use gdm?

---

### Post by pink mongoose on 2012-10-22
thanks for this post - I am using a Lenovo W500 and upgraded from 12.04 to 12.10 today and ended up in a hell of a mess with my graphics.  I removed fglrx, and changed my settings to use intel graphics, which improved the situation but did not resolve it. Then found your post and bingo!  all looks good so far

---

### Post by fjgaude on 2012-10-22
> **pink mongoose said:**
> thanks for this post - I am using a Lenovo W500 and upgraded from 12.04 to 12.10 today and ended up in a hell of a mess with my graphics.  I removed fglrx, and changed my settings to use intel graphics, which improved the situation but did not resolve it. Then found your post and bingo!  all looks good so far

You will have to use the terminal commands each time you re-boot. Sooner or later there will be a fix for this, not just a work-around.

---

### Post by Arkandias on 2012-10-22
I do not know why it does not happen with HDMI (maybe some completely independant phenomena). With DVI it does exactly like you all.

Another issue I am encountering which might be related (since it involves xorg) : my keyboard and mouse (logitech wireless) are lagging very badly (even though the computer works fine and quickly).

---

### Post by fjgaude on 2012-10-22
> **Arkandias said:**
> I do not know why it does not happen with HDMI (maybe some completely independant phenomena). With DVI it does exactly like you all.

Another issue I am encountering which might be related (since it involves xorg) : my keyboard and mouse (logitech wireless) are lagging very badly (even though the computer works fine and quickly).

All a mystery, so far! I have no issues once I'm into Unity. Very fast main box, notice my signature.

---

### Post by powder on 2012-10-23
Hi guys,

I'm also having this problem and filed a bug for it.  Feel free to comment or mark yourself affected.

[https://bugs.launchpad.net/bugs/1070150](https://bugs.launchpad.net/bugs/1070150)

---

### Post by fjgaude on 2012-10-23
Very good... maybe someone will fix it, one way or another. I added by comment to the bug report.

---

### Post by fjgaude on 2012-10-23
I decided to install gdm and select it instead of lightdm and all is okay now.

It's an issue with parsing the video card and lightdm. This can be fixed by the developers if attention is given to it.

Try it and see, but first use Software Center to install gdm, then:

```
sudo dpkg-reconfigure gdm
```

Make the selection to gdm and reboot. The login screen is back to the old themes but the OS boots normally to the desktop.

Let us know how this goes for you. Thanks!

---

### Post by mpkossen on 2012-10-25
I'm having the exact same issue as the OP and others. I'll try the lightdm workaround. It's a workable workaround for me if it works: it saves me a lot of battery power.

---

### Post by pesho21 on 2012-10-25
I can confirm, that gdm-lightdm workaround works very well for me.

---

### Post by avli on 2012-10-29
After carefully reading [this bug report]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/873495") I've found a solution, that works for me. I've added the following code into /etc/rc.local script

```
sleep 1 && service lightdm restart
```

Don't forget check the script is executable. Good luck! :)

---

### Post by fjgaude on 2012-10-29
> **avli said:**
> After carefully reading [this bug report]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/873495") I've found a solution, that works for me. I've added the following code into /etc/rc.local script

```
sleep 1 && service lightdm restart
```

Don't forget check the script is executable. Good luck! :)

Doesn't work for me, but I see that the devs are working on it. For me it goes back to 12.04.

---

### Post by broomie on 2012-10-29
This fixed it for me across two machines.  Software sourcees is screwed on both (this is a messy ubuntu upgrade and no mistake) so use comad line

or use a 3rd-party repository created by Tomasz Makarewicz for this purpose only. (I personally recommend it)

sudo add-apt-repository ppa:makson96/fglrx
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install fglrx-legacy

see [http://www.unixmen.com/ubuntu-12-10-and-amd-catalyst-problem-solved/](http://www.unixmen.com/ubuntu-12-10-and-amd-catalyst-problem-solved/)

let me know

Paul

---

### Post by fjgaude on 2012-10-29
The issue started during 12.04 before 12.04.1. It points to the devs not having enough fast computers that are prone to 'race' issues. At least that's my opinion. Has something to do with moving from the initial openings to the login, lightdm. Seems to not have the issue when gdm is used instead of lightdm.

---

### Post by powder on 2012-10-29
> **fjgaude said:**
> Doesn't work for me, but I see that the devs are working on it. For me it goes back to 12.04.

It might help to try increasing the sleep time if you have a fast system.  I'm using sleep 10 so that I can see the error before lightdm restarts.

---

### Post by fjgaude on 2012-10-29
> **powder said:**
> It might help to try increasing the sleep time if you have a fast system.  I'm using sleep 10 so that I can see the error before lightdm restarts.

Thanks! I did as you say and can see the error msg, 'waiting for battery check' or something like that.

I went from a sleep of 10 to 5 and it works. I still think the issue has to do with how the code goes from initial to lightdm. It seems to work fine with gdm instead of lightdm. So the routine must be different between the two programs. The devs are working on it. I'm sure it will be fixed one of these days, but sorry to see the issue goes back to late versions of 12.04.

Thanks again!

---

### Post by pesho21 on 2012-11-02
Strangely, but the problem is gone for me. I have reverted to lightdm and now my PC turns on every time without a problem. May be it is fixed with some update. Can you check that on your machines ?

---

### Post by powder on 2012-11-02
I'm fully updated and still experiencing the issue.

---

### Post by fjgaude on 2012-11-02
I tried lightdm on 12.04.1, 12.10, and 13.03 and it didn't work. Back to using gdm. It's not fixed for me.

---

### Post by pesho21 on 2012-11-03
It works for me every time more than 50 boots. May be I have installed something that made my PC running slower or faster in some appropriate way.

---

### Post by avli on 2012-11-03
By the way, I don't have the problem when updating from 12.04 instead of installing 12.10 from CD.

---

### Post by bj44 on 2012-12-09
I also have an SSD on my ASUS laptop which I don't think is the cause. I solved the issue by installing some of the libraries which lightdm had on 12.04 but missing on 12.10. The easy way to do this is, simply install gdm along side lightdm and reboot the system. Then I went ahead and un-installed gdm after reboot. I have not seen the low-graphics mode since. Hope this helps...

---

### Post by rdettogni on 2012-12-09
Acctually the tag of the thread is about the problem with the intel HD4000 and not ATi graphics. I did what you suggested and I almost had to format my machine.

---

### Post by bj44 on 2012-12-09
Yes that is correct, it is actually for Intel Graphics HD4000 and HD3000 Dynamic Video Memory Technology. As I mentioned no more low-graphics mode when I reboot for now. Hope we get a permanent fix for this soon...

---

### Post by flatwater on 2012-12-10
hi all! i'm new here and i just passed this thread while looking after a different problem.
but you'r occasion sounds to me like the framebuffer problem. have you already tried to deactivate the framebuffer by setting 'vga=normal' in the grub menu?

---

### Post by monkeytrash32 on 2012-12-11
> **avli said:**
> After carefully reading [this bug report]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/873495") I've found a solution, that works for me. I've added the following code into /etc/rc.local script

```
sleep 1 && service lightdm restart
```

Don't forget check the script is executable. Good luck! :)

This worked for me. Thanks! 

Also, for anyone else trying to determine the cause, none of my 2nd generation i3-based builds experience this issue, while all of my 3rd generation i7-based builds with HD4000 do.

---

### Post by Jim_in_Omaha on 2012-12-13
[QUOTE=avli;12324703]After carefully reading [this bug report]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/873495") I've found a solution, that works for me. I've added the following code into /etc/rc.local script

```
sleep 1 && service lightdm restart
```

My problem is that during a boot, I get to the login screen and it is low resolution. I login, and the desktop is the same low resolution. This is with a fresh install 12.10 and NVIDIA drivers 310. 

I tried this and it does work in my case. Not sure what is up, because I rebuilt this and I did not have the problem the first time I installed (fresh) 12.10.

---

### Post by fjgaude on 2012-12-13
> **Jim_in_Omaha said:**
> [QUOTE=avli;12324703]After carefully reading [this bug report]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/873495") I've found a solution, that works for me. I've added the following code into /etc/rc.local script

```
sleep 1 && service lightdm restart
```

My problem is that during a boot, I get to the login screen and it is low resolution. I login, and the desktop is the same low resolution. This is with a fresh install 12.10 and NVIDIA drivers 310. 

I tried this and it does work in my case. Not sure what is up, because I rebuilt this and I did not have the problem the first time I installed (fresh) 12.10.

Most of us were, are having this issue with Intel HD3000/4000 graphics and booting from a SSD. Nothing to do with Nvidia graphics. It's a 'race' issue with Intel and speed, quickness.

---

### Post by Jim_in_Omaha on 2012-12-15
There must be something to the Intel thingy. I had two SSD's, the Linux and a Windows 8. I unhooked the Windows 8 and noticed the resolution problem went away. To be sure I remarked out the line in rc.local and sure enough, Ubuntu is loading to proper resolution now.

---

### Post by dsv47 on 2012-12-15
There are currently two known workarounds to your problem at this link:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1070150](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1070150)

---

### Post by tehwizardd on 2012-12-27
Well bad news. Intel was fine with Ubuntu at 10.04.xx, but after that it's all gone to hell.

Since 11.10 or so Ubuntu hasn't recognized Intel chips at all.

Right now I have laptop with Intel HD 3000 and running Windows 7. No go for Ubuntu 12.04, just like the last laptop, Intel HD on it, not working with Ubuntu.

I am sad since I like the linux community, but the gfx cards functionality is really important to me. I need to be able to use some 3d and watch video from my TV via laptop.

---

### Post by tjajab on 2012-12-28
> **Jim_in_Omaha said:**
> [QUOTE=avli;12324703]After carefully reading [this bug report]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/873495") I've found a solution, that works for me. I've added the following code into /etc/rc.local script

```
sleep 1 && service lightdm restart
```

My problem is that during a boot, I get to the login screen and it is low resolution. I login, and the desktop is the same low resolution. This is with a fresh install 12.10 and NVIDIA drivers 310. 

I tried this and it does work in my case. Not sure what is up, because I rebuilt this and I did not have the problem the first time I installed (fresh) 12.10.
You could try to install the linux-headers-x.x.x-xx and linux-headers-x.x.x-xx-generic where x.x.x-xx is the kernel release number (you could get it with uname -r). Reboot it the Nvidia issue may be solved until next kernel upgrade.

---

### Post by wangrui on 2012-12-31
I finally find a solution.

```
sudo apt-get install gdm
```

When the system asks you to select login method, select gdm instead of lightdm. Never use lightdm again.

The problem of gdm is that once you enter a wrong password then you have to reboot from console. But it's much better than lightdm. It has its own mood. Maybe reboot ten times and it's either low graphics mode or complete blank. Especially it may work after an update and then has mood again after the next update. So disappointed that I rebooted my laptop many times every morning and still can't access my data.

---

### Post by markbl on 2013-01-01
> **wangrui said:**
> I finally find a solution.

```
sudo apt-get install gdm
```

dsv47 posted a link to that solution just above, 2 weeks ago. Replacing lightdm by gdm is an easy & effective solution to this problem.

I hadn't realise that gdm had improved it's looks so well. Used to be very ugly compared to lightdm.

---

### Post by dunbrokin on 2013-01-28
This worked for me....but how do you make gdm permanent?

---

### Post by powder on 2013-01-28
> **dunbrokin said:**
> This worked for me....but how do you make gdm permanent?

I'm not using gdm but this should do the trick:

```
sudo dpkg-reconfigure gdm
```

---

### Post by beatmag on 2013-02-17
I have a Intel HD4000 also. and recently have been experiencing this issue. Never before have I had this issue before. Anyone know what causes it?

It just suddenly started happening.............???
Also I haven't managed to fix it yet :(

---

### Post by rainbatt on 2013-03-25
Still no fix for this problem in 13.04?

---

### Post by markbl on 2013-03-26
> **rainbatt said:**
> Still no fix for this problem in 13.04?
[Bug 1070150](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1070150) has existed for ages about this. In the last few days that bug was marked as "fix released" although as the last [comment 52](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1070150/comments/52) says, there is no comment or detail about what was fixed etc.

---

### Post by jrda on 2013-04-13
I have this Bug also on my T410 with Intel Graphics and M4 SSD.
Seems there is no fix for this Bug so far, only Workarounds?!

---

### Post by Jim_in_Omaha on 2013-04-22
Since I had subscribed to this thread, 

I glanced through some of the original posts. There may be at least two different problems mixed in here maybe. The original was when it would boot up into low resolution. Then some point the problem with the lightdm booting up to a blank screen with blinking cursor. For what it's worth, I have actually dealt with both of them.

Right now I am on the 13.04. I can say on my big computer, it installed without a hitch except for the standard battle the Nvidia driver install process. On the Lenovo T500 with SSD I do get the blank screen with blink cursor. I did this suggestion and set it to a 1 second delay and fixed the problem. Perhaps this has already been mentioned... For what it's worth.

[http://www.webupd8.org/2013/01/ubuntu-lightdm-black-screen-when-using.html]("http://www.webupd8.org/2013/01/ubuntu-lightdm-black-screen-when-using.html")

---

### Post by jrda on 2013-05-13
For me it seems that Update to 13.04 solved the Problem so far on my T410 with Crucial m4 SSD

---

### Post by jrda on 2013-05-16
Failure is back again here in 13.04 :mad:
dmesg - [http://paste.ubuntu.com/5671315/](http://paste.ubuntu.com/5671315/)
syslog - [http://paste.ubuntu.com/5671323/](http://paste.ubuntu.com/5671323/)
xorg - [http://paste.ubuntu.com/5671331/](http://paste.ubuntu.com/5671331/)

---

### Post by Nick_Buonanno on 2013-12-04
I see this problem doesn't appear to be solved quite yet; I'm having a vaguely similar issue with a 13.10 (Server, x86) install on an ASUS EeePC 900 that I do-release-upgraded to from 12.04. I'm running Slim and Openbox, both of which worked normally on 12.04, 12.10, and 13.04. Similar to what someone posted on the first page of this thread, if I log in to a console and restart slim, everything comes up normally. The sleep and restart workaround in rc.local didn't work for me. I haven't tried switching display/login managers yet, but I'd like to stick with the current setup, if possible.

My Xorg.0.log file: [http://paste.ubuntu.com/6520891/](http://paste.ubuntu.com/6520891/)

---

