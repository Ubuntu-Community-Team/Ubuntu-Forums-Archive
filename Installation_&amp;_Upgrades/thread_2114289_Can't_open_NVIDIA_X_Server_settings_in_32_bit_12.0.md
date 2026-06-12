---
title: "Can't open NVIDIA X Server settings in 32 bit 12.04?"
date: 2013-02-09
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2013-02-09
NVIDIA X Server settings was just installed in 32 bit 12.04 and I can't find the icon to open it in applications even through Synaptic says is was installed.

How do you open it?

I want to change the monitor resolution and 'Displays' only has 2 options and  I don't like either.

---

### Post by bogan on 2013-02-10
Hi!, **cybrsaylr,**

You should find Nvidia XServer Settings in Dash. Enter 'NV' in the search box.

Or, if you are logged-in to Gnome Classic (no effects), in the Applications>System Tools>Administration Menu.

Or. in a Terminal: ```
gksudo nvidia-settings # or:
gksudo nvidia-settings-updates
```As you need to run it from root, to be able to save the settings.

Chao!, **bogan**.

---

### Post by cybrsaylr on 2013-02-10
Thanks bogan, 
Typing NV in Dash did nothing but I got NVIDIA X Server settings to open with this in terminal: 
 > gksudo nvidia-settings #
but I then get this popup message:


> You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

and I'm not sure what to do next?

---

### Post by cybrsaylr on 2013-02-10
Presently I'm locked into: 1024 x 768 (4:3) resolution or can choose 800 x 600 (4:3) which is worse.

I'm using Unity.

---

### Post by bogan on 2013-02-10
Hi!, **cybrsaylr**.

Is the problem with your desktop or the laptop?

Please Post: ```
uname -r
lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p
apt-cache policy nvidia-current*
```Note. from the last command the only info of interest is what driver and its version is installed. If none show as installed, run: ```
apt-cache policy nvidia*
```Chao!, **bogan.**

---

### Post by cybrsaylr on 2013-02-10
It's and old P4 desktop with a square 17" LCD HP monitor.
Here's the output:
> h@h-OptiPlex-GX270:~$ uname -r
3.2.0-37-generic-pae
h@h-OptiPlex-GX270:~$ lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x] [10de:0181] (rev c1)
	Subsystem: NVIDIA Corporation Device [10de:0191]
	Kernel driver in use: nouveau
	Kernel modules: nouveau, nvidiafb
h@h-OptiPlex-GX270:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Nouveau
OpenGL renderer string: Mesa DRI nv18 x86/MMX/SSE2
OpenGL version string:  1.2 Mesa 8.0.4

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        no
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Unity 3D supported:       no
h@h-OptiPlex-GX270:~$ apt-cache policy nvidia-current*

> h@h-OptiPlex-GX270:~$ apt-cache policy nvidia-current*
nvidia-current:
  Installed: (none)
  Candidate: 295.40-0ubuntu1.2
  Version table:
     295.40-0ubuntu1.2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/restricted i386 Packages
     295.40-0ubuntu1.1 0
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/restricted i386 Packages
     295.40-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/restricted i386 Packages
nvidia-current-updates:
  Installed: (none)
  Candidate: 304.64-0ubuntu0.2
  Version table:
     304.64-0ubuntu0.2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/restricted i386 Packages
     295.49-0ubuntu0.2 0
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/restricted i386 Packages
     295.40-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/restricted i386 Packages
nvidia-current-updates-dev:
  Installed: (none)
  Candidate: 304.64-0ubuntu0.2
  Version table:
     304.64-0ubuntu0.2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/restricted i386 Packages
     295.49-0ubuntu0.2 0
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/restricted i386 Packages
     295.40-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/restricted i386 Packages
nvidia-current-dev:
  Installed: (none)
  Candidate: 295.40-0ubuntu1.2
  Version table:
     295.40-0ubuntu1.2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/restricted i386 Packages
     295.40-0ubuntu1.1 0
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/restricted i386 Packages
     295.40-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/restricted i386 Packages
nvidia-current-modaliases:
  Installed: (none)
  Candidate: (none)
  Version table:
h@h-OptiPlex-GX270:~$ 


---

### Post by grahammechanical on 2013-02-10
As you are on 12.04 you could open Addittonal Drivers (in the Dash) and see if you are actually running on the Nvidia driver. It is possible that the Nouveau driver has been activated at some point.

Regards.

---

### Post by MAFoElffen on 2013-02-10
Please backup a second.

If it exists, open /etc/X11/xorg.conf and post here.

If it doesn't exist
```

sudo nvidia-xconfig

```
That will probe the hardware through the nvidia utilities and xorg to generate one. It should also set the driver in the xorg.conf to "nvidia". Then post that here.

Please tell us whether it was already existing or newly generated.

If on reboot, after generating a new xorg.conf, if it locks up on the graphics... reboot to the rescue menu, go root and rename that filename appending .bak as a file extension... Then reboot.

*** Problem I noticed with some new installs a few weeks ago was that a new nvidia driver install from additional driver did not produce an xorg.conf file. 2 other installs (separate hardware) genrated the xorg.conf file, but configured X to use the "default" driver instead of the "nvidia" driver.

So, I now suspect this was not an "isolated problem." If it is this, then users should report it to launchpad as a problem so it can get addressed and resolved in the nvidia driver packages.

---

### Post by cybrsaylr on 2013-02-10
> **grahammechanical said:**
> As you are on 12.04 you could open Addittonal Drivers (in the Dash) and see if you are actually running on the Nvidia driver. It is possible that the Nouveau driver has been activated at some point.

Here's what Additional Drivers shows:
[ATTACH]231265[/ATTACH]
When I activated that version 96 the resulting resolution was worse/larger than  800 x 600 (4:3) so I went back to the previous setting which gives me  1024 x 768 (4:3) resolution.

---

### Post by cybrsaylr on 2013-02-10
> **MAFoElffen said:**
> Please backup a second.

If it exists, open /etc/X11/xorg.conf and post here.

If it doesn't exist
```

sudo nvidia-xconfig

```

Here's the output:
> h@h-OptiPlex-GX270:~$ sudo nvidia-xconfig
[sudo] password for h: 
sudo: nvidia-xconfig: command not found

---

### Post by bogan on 2013-02-11
Hi!, **cbrsaylr**,

According to nvidia.com/drivers, the correct recommended driver for the"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x] [10de:0181] (rev c1)" is version 96.43.23, dated 14.9.2012, which is compatible with XOrg xserver 1.12.
 > Added support for X.Org xserver versions 1.11 and 1.12.
Improved compatibility with recent Linux kernels.The previous version 96.43.20 dated 17.8.2011 is only compatible with v 1.10.

Please Post: ```
apt-cache policy nvidia-96
```To see which version you tried, unsuccessfully, to install.

[Highlight the output and press the '#' symbol in the toolbar at the top of the 'New Reply' edit box, to put it in 'Code' tags, for easy reading].

No doubt **MAFoElffen** will advise you, if he thinks it necessary to try the nvidia.com/drivers download route.

Chao!,** bogan**.

---

### Post by MAFoElffen on 2013-02-11
> **bogan said:**
> Hi!, **cbrsaylr**,

According to nvidia.com/drivers, the correct recommended driver for the"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x] [10de:0181] (rev c1)" is version 96.43.23, dated 14.9.2012, which is compatible with XOrg xserver 1.12.
 The previous version 96.43.20 dated 17.8.2011 is only compatible with v 1.10.

Please Post: ```
apt-cache policy nvidia-96
```To see which version you tried, unsuccessfully, to install.

[Highlight the output and press the '#' symbol in the toolbar at the top of the 'New Reply' edit box, to put it in 'Code' tags, for easy reading].

No doubt **MAFoElffen** will advise you, if he thinks it necessary to try the nvidia.com/drivers download route.

Chao!,** bogan**.
So, you didn't say, but there wasn't an xorg.conf file... was there? (LOL)

Bogan-
Think if the OP does 
```

dpkg -l | grp nvidia

```
and if he checks his APT install logs (like you posted), that we'll find that nvidia proprietary driver's were not installed yet or that they errored out. If nvidia-xconfig did not get installed, then the install was not a borked install, it didn't get far enough to install that utility or the driver.

He did say that he installed the nvidia proprietary driver right? Didn't he? I thought he said that... or did I just assume that since he installed nvidia-settings that he already installed the nvidia video driver. LOL

What do I recommend? The OP's machine is defaulting the the Nouveau driver currently. He could surely install nvidia-96... BUT-

My experience (and my opinion) with the old NV-1x to the Geoforce 2xxx AGP cards and Ubuntu since about 1-1/2 to 2 years ago is that the nouveau drivers since then added capabilities to those those cards that the standard NVidia driver doesn't. I can't say about that driver and the newer cards since those, but I can for those particular series cards. My tests they came out being faster graphics and better quality rendering. I think the "nouveau 3D experiemntal" that I tested back in the dev cycle for Natty is the "standard" nouveau driver now.

cybrsaylr-
I think if you install the nvidia-96 driver and evaluate for yourself, you would see that for yourself... Your call. You could always change back easily or switch easily. All it would take is to install it, then edit the xorg.conf device section, driver line to switch it between "nouveau" or "nvidia"... Or just rename the xorg.conf file to "something else" when you just want to default to nouveau.

---

### Post by bogan on 2013-02-11
Hi!, **MAFoElffen**,

I assume your cmd:```
 dpkg - | grp nvidia
```was a typo for: ```
dpkg -l | grep nvidia
```You Posted:> He did say that he installed the nvidia proprietary driver right? Didn't he? What he said was:> When I activated that version 96 the resulting resolution was  worse/larger than  800 x 600 (4:3) so I went back to the previous  settingWhich left things a bit vague as to whether it was fully installed, and whether he un-installed it.

I believe the 'ACTIVATE' button, in Additional Drivers, does not always do what it says on a single press.

Edit: Synaptic in my 12.04, shows nvidia-96 as v.96.43.23, and nvidia-96-updates as the earlier v. 96.43.20

So, presumably, there would not be any advantage in going the nvidia.com download route.
@**cbrsaylr**,,

Can you please clarify this?

Apart from the two commands apt-cache and dpkg, what does SynapticPackage Manager show for nvidia-96?
 Listed? Installed ??[ ie greenflagged ] version ??   Edit: See note above,

Chao!, **bogan**,

---

### Post by MAFoElffen on 2013-02-11
Just a note- Synaptic is no longer installed in Ubuntu by default, so you may have to install that to check what Bogan asked... I prefer it and usually install it after a fresh install on someone's hardware.

---

### Post by cybrsaylr on 2013-02-11
I uninstalled nvidia-96 because the resolution was larger than 800 x 600 (4:3).
I have Synaptic installed and it shows nvidia-96 is not installed right now.

Output for 'dpkg -l | grep nvidia':
> h@h-OptiPlex-GX270:~$ dpkg -l | grep nvidia
rc  nvidia-96                              96.43.23-0ubuntu0.1                     NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                          1:0.2.44.2                              Find obsolete NVIDIA drivers
ii  nvidia-settings                        295.33-0ubuntu1                         Tool of configuring the NVIDIA graphics driver


So I believe I'm using whatever default settings came with 32 bit 12.04 which gives me only two resolution settings. Am using  1024 x 768 (4:3) resolution, which is ok but just wanted to try a few other resolution options that I assumed NVIDIA X Server settings would give me.

---

### Post by bogan on 2013-02-11
Hi!,** cbrsaylr,**

Ok, so that is the correct nvidia-96 version.

You Posted: > So I believe I'm using whatever default settings came with 32 bit 12.04 That is correct, 'lspci' showed you are using Nouveau.

Please Post the /etc/X11/xorg.conf file, as requested by MAFoElffen in his post #8

Chao!, **bogan.**

---

### Post by cybrsaylr on 2013-02-11
> **bogan said:**
> You Posted: That is correct, 'lspci' showed you are using Nouveau.

Please Post the /etc/X11/xorg.conf file, as requested by MAFoElffen in his post #8

Not sure how to post that /etc/X11/xorg.conf file....
Where is it?


Did a little digging into 12.04 and found this...
Is this that /etc/X11/xorg.conf file:

....opps take that back below.... used the wrong PC....
Can't seem to find /etc/X11/xorg.conf file.

This is all I find in X11 folder:
[ATTACH]231308[/ATTACH]

---

### Post by MAFoElffen on 2013-02-11
> **cybrsaylr said:**
> Not sure how to post that /etc/X11/xorg.conf file....
Where is it?


Did a little digging into 12.04 and found this...
Is this that /etc/X11/xorg.conf file:

....opps take that back below.... used the wrong PC....
Can't seem to find /etc/X11/xorg.conf file.

This is all I find in X11 folder:

It does not exist. Uninstall of nividia-96 via apt would have removed it. So, NVidia driver with that card is not as good with the nouveau driver... You confirmed what I posted above about those 2 drivers with your card.

So if good video, but you want to add more resoltutions, I need info. Bogan please follow along so yuo can help others on this.

Please install hwinfo:
```

sudo apt-get install hwinfo

```
Collect info from your system to post here:
```

sudo hwinfo --framebuffer > ~/Documents/framebuffer.txt
sudo hwinfo --monitor > ~/Documents/monitor.txt
cp /var/log/Xorg.0.log ~/Documents/xorg.log.txt

```
Post those 3 created files here please...

The first command will probe your video card for all it's modes.
The second will probe the monitor for all it's modes. 
The Xorg.0.log also probes the hardware, tests modes and looks for matching modes.

It may be that it's not getting back valid EDID data from the monitor during that probe. That would be in the Xorg.0.log.

I need to know the make and model of your monitor.

I can create an xorg,conf file for you with that info/data. It will point to the nouveau driver (like it does now) but I will also recreate the EDID data to add any matching resolutions between the video card and monitor. I will explain how I do it so you both know how... 

Bogan, I've done this before and I think you've seen it from me, but there have been some changes since then. I usually do this for people with NVidia... But it can be done with any video driver, not just nvidia.

Sound good?

---

### Post by bogan on 2013-02-12
Hi!, **MAFoElffen**,

> Sound good?Yeah!, I am with you on that all the way.

I was aware of your technique, from your Sticky, but did not feel confident enough to try and lead others through it. 'Modlines' yet!

Chao!. **bogan.**

---

