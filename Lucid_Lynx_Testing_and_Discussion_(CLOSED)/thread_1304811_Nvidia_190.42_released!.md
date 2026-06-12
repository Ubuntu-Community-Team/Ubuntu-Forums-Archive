---
title: "Nvidia 190.42 released!"
date: 2009-10-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by froggyswamp on 2009-10-29
[http://www.nvidia.com/object/linux_display_ia32_190.42.html](http://www.nvidia.com/object/linux_display_ia32_190.42.html)

A big pile of improvements folks, but too late. Afaik, unlike Fedora, the Ubuntu devs don't update the drivers after distro release, right?

---

### Post by Twintop on 2009-10-29
OpenGL 3.2, X crashing bug fixes, VDPAU, and the ability to control my GPU fan speed? Frickin' sweet! All the more reason to move to LL! :twisted:

---

### Post by whoop on 2009-10-29
VDPAU seems cool, although my card only seems to support feature set A :-(

---

### Post by kestal on 2009-10-29
Tried it a few days ago, and 190.36 appears a bit more stable on my end (at least with OpenGL)

---

### Post by Technoviking on 2009-10-29
They did upgrade some drivers in this PPA.

[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates)

T-V

---

### Post by SevenMachines on 2009-10-30
I tend to keep updated nvidia drivers in[ this ppa]("https://launchpad.net/%7Esevenmachines/+archive/nvidia"). 190.42 for Karmic just now and Lucid soon. Just in case anyone needs them

---

### Post by ktp on 2009-10-30
Here is the one I use most of the time and is good about staying on top of updates:

[https://launchpad.net/~nvidia-vdpau/+archive/ppa/+packages](https://launchpad.net/~nvidia-vdpau/+archive/ppa/+packages)

---

### Post by dino99 on 2009-10-31
> **ktp said:**
> Here is the one I use most of the time and is good about staying on top of updates:

[https://launchpad.net/~nvidia-vdpau/+archive/ppa/+packages](https://launchpad.net/~nvidia-vdpau/+archive/ppa/+packages)

that's mine too

---

### Post by plun on 2009-10-31
> **SevenMachines said:**
> I tend to keep updated nvidia drivers in[ this ppa]("https://launchpad.net/%7Esevenmachines/+archive/nvidia"). 190.42 for Karmic just now and Lucid soon. Just in case anyone needs them

Yup I am using this ppa without any trouble, thanks !

---

### Post by sdowney717 on 2009-10-31
[https://launchpad.net/~nvidia-vdpau/+archive/ppa/+packages](https://launchpad.net/~nvidia-vdpau/+archive/ppa/+packages)

on this ppa, what is the ppa line to be placed in software sources

---

### Post by NCLI on 2009-10-31
> **sdowney717 said:**
> [https://launchpad.net/~nvidia-vdpau/+archive/ppa/+packages]("https://launchpad.net/%7Envidia-vdpau/+archive/ppa/+packages")

on this ppa, what is the ppa line to be placed in software sources
ppa:nvidia-vdpau/ppa

---

### Post by sdowney717 on 2009-10-31
thanks, it also wants the key.

all that information should be on the web site, but i dont see it.

---

### Post by sdowney717 on 2009-10-31
nvidia settings says no to direct rendering, but glxinfo in terminal says yes.

> scott@scott-desktop:~$ sudo glxinfo
[sudo] password for scott: 
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4


---

### Post by sdowney717 on 2009-10-31
after the upgrade to 190, i apparently have no direct rendering, google earth runs very slowly.

---

### Post by sdowney717 on 2009-10-31
mad!
I only get direct rendering now if i run something as root
google earth is zooming as root with direct rendering yes, normal user very very slow

> scott@scott-desktop:~$ glxinfo | grep direct
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
scott@scott-desktop:~$ LIBGL_DEBUG=verbose
scott@scott-desktop:~$ glxinfo | grep direct
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
scott@scott-desktop:~$ LIBGL_DEBUG=verbose
scott@scott-desktop:~$ sudo glxinfo | grep direct
[sudo] password for scott: 
direct rendering: Yes
    GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 
scott@scott-desktop:~$ gksudo googleearth


i got it fixed by doing these two things
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/370249?comments=all](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/370249?comments=all)
edited my group file
[http://www.linuxquestions.org/questions/linux-software-2/nvidia-permission-prblems-in-application-95198/](http://www.linuxquestions.org/questions/linux-software-2/nvidia-permission-prblems-in-application-95198/)
gksudo gedit /etc/group
changed 
video:x:44:vdr,scott
to
video:x:44:scott,vdr

(video colon x colon 44 colon scott,vdr) crazy faces

---

### Post by dbutcher on 2009-10-31
> **sdowney717 said:**
> thanks, it also wants the key.

all that information should be on the web site, but i dont see it.

I think you've "drilled down" too far.  Instead of [https://launchpad.net/~nvidia-vdpau/+archive/ppa/+packages](https://launchpad.net/~nvidia-vdpau/+archive/ppa/+packages), use [https://launchpad.net/~nvidia-vdpau/+archive/ppa/]("https://launchpad.net/~nvidia-vdpau/+archive/ppa/") , then click on "technical details"

Cheers,
Dave

---

### Post by HotShotDJ on 2009-10-31
I upgraded my Nvidia driver using [https://launchpad.net/~nvidia-vdpau/+archive/ppa/](https://launchpad.net/~nvidia-vdpau/+archive/ppa/) but the Upgrade Manager/Synaptic Package Manager kept insisting on "upgrading" to the 185.18.36 drivers.  I'm quite certain I did something wrong whilst upgrading, but I don't know what it was.

---

### Post by sdowney717 on 2009-11-01
i put the ppa in software sources and then used synaptic to remove 185 and install 190 driver. not getting any strange messages.
there are 4 or 5 packages involved with the nvidia driver, one i recall is nvidia settings.

---

### Post by flavouride on 2009-11-02
sudo add-apt-repository ppa:nvidia-vdpau/ppa

sudo apt-get update

sudo apt-get install nvidia-190-modaliases nvidia-glx-190  nvidia-settings-190

were all I did and it is going all well.

---

### Post by HotShotDJ on 2009-11-03
> **flavouride said:**
> sudo add-apt-repository ppa:nvidia-vdpau/ppa
:shock:
I've never seen this one before.  It works beautifully... no hassle of finding and adding the keys!  Is this new to Karmic or just something that I've missed along the way?

EDIT:  Ok, I finished following your instructions -- in the end, it pretty much did the same thing that I had done previously using Synaptic Package Manager -- but far more easily and elegantly. :)

However, I still have the same issue as before... Synaptic wants to upgrade a bunch of multimedia stuff (see below) and downgrade the NVidia driver, while Upgrade Manager and "apt-get upgrade" hold back those packages (Upgrade Manager warning of a "Partial Upgrade").  Here is the output from the command line:```
sudo apt-get upgrade
[sudo] password for jay: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins
  libxine1-x mencoder mplayer-nogui
The following packages will be upgraded:
  libx264-67
1 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
Need to get 0B/304kB of archives.
After this operation, 32.8kB of additional disk space will be used.
Do you want to continue [Y/n]? 
```And a screenshot of Synaptic Manager when I "Mark All Upgrades."  Of course, the solution is to not click on "Mark All Upgrades" in Synaptic. But it is rather off-putting.

---

### Post by autocrosser on 2009-11-03
New with Karmic--Most of the PPA pages have the info on them now...

For anyone interested, the sources I use are:```
deb http://ppa.launchpad.net/thefirstm/karmic-testing/ubuntu karmic main
deb-src http://ppa.launchpad.net/thefirstm/karmic-testing/ubuntu karmic main
```

---

### Post by flavouride on 2009-11-08
> **HotShotDJ said:**
> :shock:

However, I still have the same issue as before... Synaptic wants to upgrade a bunch of multimedia stuff (see below) and downgrade the NVidia driver, while Upgrade Manager and "apt-get upgrade" hold back those packages (Upgrade Manager warning of a "Partial Upgrade").  Here is the output from the command line:```
sudo apt-get upgrade
[sudo] password for jay: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins
  libxine1-x mencoder mplayer-nogui
The following packages will be upgraded:
  libx264-67
1 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
Need to get 0B/304kB of archives.
After this operation, 32.8kB of additional disk space will be used.
Do you want to continue [Y/n]? 
```And a screenshot of Synaptic Manager when I "Mark All Upgrades."  Of course, the solution is to not click on "Mark All Upgrades" in Synaptic. But it is rather off-putting.

Yup its new to Karmic and I got the info from

[http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html)

In relation to the partial upgrade offer I did not come across that but there a partial upgrade is always not recommended for a stable release so I would not encourage a green light unless something is not working smooth enough.

---

### Post by flavouride on 2009-11-08
> **autocrosser said:**
> New with Karmic--Most of the PPA pages have the info on them now...

For anyone interested, the sources I use are:```
deb http://ppa.launchpad.net/thefirstm/karmic-testing/ubuntu karmic main
deb-src http://ppa.launchpad.net/thefirstm/karmic-testing/ubuntu karmic main
```

Thanks for your info, very useful and noted in my diary :p

---

### Post by rajeev1204 on 2009-11-08
nvm

---

### Post by hikaricore on 2009-11-08
> **rajeev1204 said:**
> Iam tired with these threads popping up all the time.

Stop reading them then?

---

### Post by HotShotDJ on 2009-11-08
> **rajeev1204 said:**
> Its useless updating drivers especially linux drivers when there arent any games with bugs to be fixed by the drivers unlike in the windows world where there are documented fixes with gamesPerhaps you were unaware of the fact that there are people out there who use their computers as something more than glorified gaming consoles.  For me, improved power management for the GPU in NVidia's mobile graphics adapter is important.  Perhaps that is not important to you.  But I'm sure there are many of us who are not interested in restricting conversations only to your narrow interests.  As hikaricore said, if the topic of the tread doesn't interest you, then you are free to stay out of the conversation.  But to demand that nobody else be interested either is a bit self-centered, don't you think?

---

### Post by rajeev1204 on 2009-11-09
nvm

---

