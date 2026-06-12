---
title: "Nvidia 195 won't install via apt-get on 9.10"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by nvidiasucks on 2010-02-18
```
debox@debox-htpc:~$ sudo apt-get install nvidia-glx-195
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed
  nvidia-glx-195
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/19.8MB of archives.
After this operation, 61.2MB of additional disk space will be used.
(Reading database ... 129752 files and directories currently installed.)
Unpacking nvidia-glx-195 (from .../nvidia-glx-195_195.36.03-0ubuntu1~karmic~nvidiavdpauppa2_i386.deb) ...
dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-195' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-185'
dpkg: error processing /var/cache/apt/archives/nvidia-glx-195_195.36.03-0ubuntu1~karmic~nvidiavdpauppa2_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-195_195.36.03-0ubuntu1~karmic~nvidiavdpauppa2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
debox@debox-htpc:~$
```

No idea what's going on here, dpkg is broken? :/ halp

---

### Post by 2hot6ft2 on 2010-02-18
Have you tried installing the driver using hardware drivers?
System > Administration > Hardware Drivers

---

### Post by nvidiasucks on 2010-02-18
> **2hot6ft2 said:**
> Have you tried installing the driver using hardware drivers?
System > Administration > Hardware Drivers

Yes, The last time I did that when I had X screen access I got an error about archives or something.

I can't get back into X so I'm having to go by what the command line (putty) is telling me.

---

### Post by 2hot6ft2 on 2010-02-18
> **nvidiasucks said:**
> Yes, The last time I did that when I had X screen access I got an error about archives or something.

I can't get back into X so I'm having to go by what the command line (putty) is telling me.
Ouch, I would try going to the nvidia web site and getting the right driver for your graphics card and putting it on the machines desktop
/home/username/Desktop
and running it from the command line with their installer then.
I have used the nvidia drivers from their site and installed them that way in the past and they seem to resolve conflicts during the install process very well. Not sure how that would work doing it thru PuTTy though.

The "dpkg returned an error" isn't saying anything is broken it seems to just be a conflict between the 185 that's installed and the 195 you're trying to install.

---

### Post by 2hot6ft2 on 2010-02-18
Here's their instructions for running the installer from their website.
Naturally the package name will be different for yours.
> Starting the Installer

After you have downloaded the file NVIDIA-Linux-x86-190.53-pkg#.run, change to the directory containing the downloaded file, and as the root user run the executable:

    # cd yourdirectory
    # sh NVIDIA-Linux-x86-190.53-pkg#.run


---

### Post by nvidiasucks on 2010-02-18
Okay, doing that gives me X back thanks. However its now completely wiped out VDAPU support for XBMC...

What VDAPU do I need for that driver you've linked to me?

And also my llirc config has disappered.. What the hell has apt-get update been doing lol :/

---

### Post by pbrane on 2010-02-18
You should have a backup of your original xorg.conf in /etc/X11/. The nvidia driver install should have made a backup. Next time you need to upgrade your nvidia driver don't let it configure X for you. Your existing xorg.conf will work fine.
also this link has some good info on how to have the driver re-install itself for kernel updates.
[http://ubuntuforums.org/showthread.php?t=1125400]("http://ubuntuforums.org/showthread.php?t=1125400")

---

### Post by nvidiasucks on 2010-02-18
X is not the problem, It's that theres no VDAPU for this new driver? Nvidia haven't included it? I'm not sure what vdapu I need to ask apt-get to install :/

vdpauinfo or nvidia-vdpau or heck maybe even vdapu1 or whatever its called.

:confused:

---

### Post by 2hot6ft2 on 2010-02-18
> **nvidiasucks said:**
> Okay, doing that gives me X back thanks. However its now completely wiped out VDAPU support for XBMC...

What VDAPU do I need for that driver you've linked to me?

And also my llirc config has disappered.. What the hell has apt-get update been doing lol :/

I have no idea about the VDAPU, and I didn't link to any driver.:confused:

---

### Post by nvidiasucks on 2010-02-18
> **2hot6ft2 said:**
> I have no idea about the VDAPU, and I didn't link to any driver.:confused:

I mean this : NVIDIA-Linux-x86-190.53... I'm wondering what VDAPU I need to use for 190.53? :/

I gave this a go :

```
debox@debox-htpc:~$ sudo apt-get install nvidia-libvdpau-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting nvidia-185-libvdpau-dev instead of nvidia-libvdpau-dev
The following packages were automatically installed and are no longer required:
  nvidia-settings
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  nvidia-185-libvdpau nvidia-185-libvdpau-dev
The following NEW packages will be installed
  nvidia-185-libvdpau nvidia-185-libvdpau-dev
0 upgraded, 2 newly installed, 0 to remove and 12 not upgraded.
Need to get 813kB of archives.
After this operation, 1,786kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
debox@debox-htpc:~$ sudo apt-get install nvidia-195-libvdpau-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package nvidia-195-libvdpau-dev
debox@debox-htpc:~$

```Why is it picking 185? I assumed that was uninstalled.. So confusing :(

---

### Post by 2hot6ft2 on 2010-02-18
> **nvidiasucks said:**
> I mean this : NVIDIA-Linux-x86-190.53... I'm wondering what VDAPU I need to use for 190.53? :/
Only one I'm seeing with that version number is 64bit
[http://www.nvidia.com/object/linux_display_amd64_190.53.html](http://www.nvidia.com/object/linux_display_amd64_190.53.html)

[The NVIDIA VDPAU search page is here]("http://www.nvidia.com/object/nv_search_us.html?cx=009029091075083507105%3A9leknaf7r_8&cof=FORID%3A11%3BNB%3A1&ie=UTF-8&hl=en&gl=us&q=VDAPU#881")

[And the closest x86 one is 190.42 here]("http://www.nvidia.com/object/linux_display_ia32_190.42.html")

---

### Post by nvidiasucks on 2010-02-18
Edited my other post.. Hm. I think i'll try asking around on the XBMC forums about this issue since its more specific towards that.

I'll still be keeping an eye out on this thread if anyone has any ideas about VDPAU.

Thanks again.

---

### Post by 2hot6ft2 on 2010-02-18
Check that last link I gave and click on the "Supported Products" tab

---

### Post by nvidiasucks on 2010-02-18
> **2hot6ft2 said:**
> Check that last link I gave and click on the "Supported Products" tab

I'm using the ION, all the recent drivers (>185) seem to have support for it I think.

---

### Post by motsteve on 2010-02-20
When installing the 190.53 drivers or any of their drivers, you have to stop the Xserver first.  I've tried all the suggestions for this from cntl-alt-backspace to gdm stop.  I've tried the hardware driver menu, all that gives you is the out of date 185 drivers.  I've tried Envy and that gives you the 185 drivers again.  There is absolutely nothing on the nVidia site as far as I can tell.  Now one here in this forum seems to know what to do, so what am I to do.  I've got a big fancy controller and standard graphics.  No wonder the average person doesn't want to switch Linux.

Before I get flamed I've done everything from recovery mode to virtual console which only gives me hash from cntl-alt-F1 to cntl-alt-F6.  /etc/init.d/gdm stop is deprecated.  You're supposed to use gdm stop, but that gives you a "Failed to acquire org.gnome.DisplayManager error message.  I tried some other suggestion using a Xserver command and Bash said the command didn't exist even using sudo, but there's a man page for it.  There was also a way to install it via apt, but the package was missing or removed from the repository.  Now what? #-o

---

### Post by oldos2er on 2010-02-20
> **nvidiasucks said:**
> I'll still be keeping an eye out on this thread if anyone has any ideas about VDPAU.


[https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=jaunty](https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=jaunty)

---

