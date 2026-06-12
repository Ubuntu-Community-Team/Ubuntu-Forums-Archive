---
title: "Xorg locks up with Nvidia card"
date: 2009-12-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Jordanwb on 2009-12-12
The desktop amd64 copy works great on my laptop, but not on my desktop machine. My laptop has an ATI chip, my desktop has an 9500GT. When I boot the LiveCD on my desktop pc, xorg starts and that's as far as I go. I've tried adding "noload=nv,nvidia" to the grub paramaters (booting iso via grub2 on a flash drive) but still no soap. I read that the Nvidia drivers aren't working with 10.04 but I can't get that far. Any ideas?

[http://ubuntuforums.org/showpost.php?p=8474982&postcount=3](http://ubuntuforums.org/showpost.php?p=8474982&postcount=3) Huh

---

### Post by kevpan815 on 2009-12-12
Use The Alternate CD Instead, I Have No Problems 2 Report While Using The NVIDIA 195.22 Beta Device Driver With The Alpha 1 Alternate CD, Just FYI!

---

### Post by Jordanwb on 2009-12-12
I may give that a try. Was the driver easy to install? As in install a deb or run a sh file.

---

### Post by ronacc on 2009-12-12
it is listed as a known issue in the release notes that the default nv driver has problems , you can either use the vesa driver ( safe mode) or install the 195.22 nvidia driver , you can get it from sevenmachines PPA on launchpad . not on that machine right now so I can't post a link .

---

### Post by paul_in_london on 2009-12-12
Here you go:

[https://launchpad.net/~sevenmachines...s_filter=lucid](https://launchpad.net/~sevenmachines...s_filter=lucid)

---

### Post by autocrosser on 2009-12-13
I verify that it works here with a SLI 9800GT dual setup......

---

### Post by jppr on 2009-12-13
> **ronacc said:**
> it is listed as a known issue in the release notes that the default nv driver has problems , you can either use the vesa driver ( safe mode) or install the 195.22 nvidia driver , you can get it from sevenmachines PPA on launchpad . not on that machine right now so I can't post a link .

How can i install vesa driver when i try do fresh alternate installation? i mean... how install vesa driver in recovery mode? sudo aptitude install... ? or... how can i change /etc/x11/xorg.conf that vesa driver in recovery mode? after alternate installation, system boot black and empty screen and i can do nothing.
Now i have pre alpha installation with 185 driver and i can´t update new X

---

### Post by dino99 on 2009-12-13
have some problems with 195 (sevenmachines): boot process hang after upstart logo come up, gdm don't start and the keyboard is locked.

As a workaround, i'm able to boot if i unplug the keyboard during first part of booting; when gdm is loaded, i plug it back and everything goes fine.

See what happen next time i reboot.  :P

---

### Post by autark on 2009-12-13
I never got Karmic to work satisfactorily on my laptop, so I though I'd follow the Lucid Lynx tests from early on. However, I ran into this nvidia problem.

Following the suggestions in this thread I tried enabling the sevenmachines PPA and ran straight into dependency hell:

```
root@barbaren:/# apt-get install nvidia-glx-195
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  nvidia-195-libvdpau
The following NEW packages will be installed:
  nvidia-195-libvdpau nvidia-glx-195
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/23,7MB of archives.
After this operation, 76,9MB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 286208 files and directories currently installed.)
Unpacking nvidia-195-libvdpau (from .../nvidia-195-libvdpau_195.22-0ubuntu0~sevenmachines2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/nvidia-195-libvdpau_195.22-0ubuntu0~sevenmachines2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libvdpau.so', which is also in package nvidia-190-libvdpau 0:190.42-0ubuntu1~karmic~nvidiavdpauppa4
Selecting previously deselected package nvidia-glx-195.
Unpacking nvidia-glx-195 (from .../nvidia-glx-195_195.22-0ubuntu0~sevenmachines2_amd64.deb) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for python-support ...
WARNING: WARNING: /usr/share/pyshared/lsb_release.py is linked but does not belong to any package.
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-195-libvdpau_195.22-0ubuntu0~sevenmachines2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

``````
root@barbaren:/# apt-get remove nvidia-190-libvdpau
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libxine1-bin: Depends: nvidia-190-libvdpau but it is not going to be installed
  nvidia-glx-195: Depends: nvidia-195-libvdpau (>= 195.22) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```'apt-get -f install' gives the same result as the first attempt. And libxine1-bin has too many important dependencies. What am I to do? Is there any chance this will be fixed soon?

---

### Post by paul_in_london on 2009-12-13
Try this:

```
cd /var/cache/apt/archives/
sudo dpkg -i --force-overwrite nvidia-195-libvdpau_195.22-0ubuntu0~ppa0_i386.deb
sudo aptitude install nvidia-glx-195 nvidia-195-kernel-source
```

---

### Post by ronacc on 2009-12-13
> **jppr said:**
> How can i install vesa driver when i try do fresh alternate installation? i mean... how install vesa driver in recovery mode? sudo aptitude install... ? or... how can i change /etc/x11/xorg.conf that vesa driver in recovery mode? after alternate installation, system boot black and empty screen and i can do nothing.
Now i have pre alpha installation with 185 driver and i can´t update new X

for a one time boot , while the grub menu is up hit e for edit and add xforcevesa after ro quiet splash . then hit b to boot . if this is a fresh install and you havent installed one of the nvidia drivers you don't yet have an xorg.conf . see above in this thread and install 195.22 from sevenmachines PPA .

---

### Post by SevenMachines on 2009-12-13
[autark]("http://ubuntuforums.org/member.php?u=910393"): if you also have the nvidia vdpau teams ppa activated, this is bound to lead to dependency problems. when using ppa's i would suggest less is more, use as few as possible and only with great care :)  Certainly I would say that the ones i'm responsible for are very much for playing purposes only

---

### Post by autark on 2009-12-13
> **paul_in_london said:**
> Try this:

```
cd /var/cache/apt/archives/
sudo dpkg -i --force-overwrite nvidia-195-libvdpau_195.22-0ubuntu0~ppa0_i386.deb
sudo aptitude install nvidia-glx-195 nvidia-195-kernel-source
```

Thanks, that worked! I had to change the "386" part since I'm 64-bit. I also had to reinstall the two packages, but after that I got nvidia working again.  But there is something wrong with gdm on my machine. I never really got gdm to run after it broke in Jaunty alpha and it's the same in Lucid. However kdm works fine. I have upgraded this installation from Jaunty but I guess I ought to start all over from scratch instead.

---

### Post by autark on 2009-12-13
> **SevenMachines said:**
> [autark]("http://ubuntuforums.org/member.php?u=910393"): if you also have the nvidia vdpau teams ppa activated, this is bound to lead to dependency problems. when using ppa's i would suggest less is more, use as few as possible and only with great care :)  Certainly I would say that the ones i'm responsible for are very much for playing purposes only

Thanks for the reminder! I'll try not to get addicted. ;-)

---

### Post by Jordanwb on 2009-12-13
> **paul_in_london said:**
> Here you go:

[https://launchpad.net/~sevenmachines...s_filter=lucid](https://launchpad.net/~sevenmachines...s_filter=lucid)

I suppose the forum mangled the URL: [https://launchpad.net/~sevenmachines/+archive/nvidia](https://launchpad.net/~sevenmachines/+archive/nvidia)

---

### Post by kevpan815 on 2009-12-13
When Using The .Run File From NVIDIA.com, You First Need 2 Terminate X Server (Control+Alternate+Function 1, Then sudo stop gdm), Next sudo sh NVIDIA-Linux-x86-195.22-pkg1.run), Finally sudo start gdm.

---

### Post by Jordanwb on 2009-12-13
Sounds easy enough. I'll try it tommorow.

---

### Post by rv65 on 2009-12-17
I got it working by using sevenmachines PPA.

---

### Post by Jordanwb on 2009-12-17
^ So did I. Now if I could get my laptop's cpu governor to stay set to performance like I told it to in that script I wrote and told update-rc.d to enable.

---

### Post by fcuk112 on 2009-12-22
> **autark said:**
> Thanks, that worked! I had to change the "386" part since I'm 64-bit. I also had to reinstall the two packages, but after that I got nvidia working again.  But there is something wrong with gdm on my machine. I never really got gdm to run after it broke in Jaunty alpha and it's the same in Lucid. However kdm works fine. I have upgraded this installation from Jaunty but I guess I ought to start all over from scratch instead.

i am getting the following when i run the last line...  anybody got any idea?

Unpacking nvidia-glx-195 (from .../nvidia-glx-195_195.22-0ubuntu0~sevenmachines2_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-195' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-185'
dpkg: error processing /var/cache/apt/archives/nvidia-glx-195_195.22-0ubuntu0~sevenmachines2_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2

---

### Post by Jordanwb on 2009-12-22
Do you have the old nvidia driver installed? Try uninstalling it.

---

### Post by songochain on 2009-12-22
Try dpkg -i --force-all 

I have not tty and I have not xsplash when booting. Anyone?

---

### Post by Jordanwb on 2009-12-22
I installed 10.04 to a different drive and added seven machine's repo and key. But I can't find his packages in the list when I "aptitude search nvidia" :confused:

*Edit*

I'm stupid sometimes. I got the wrong repo.

---

### Post by tad1073 on 2009-12-22
use update manager, that is the easiest way.

---

### Post by Jordanwb on 2009-12-22
Hell no that program is such a pain in the butt. I tell it never to check for updates and guess what it does? Checks for updates and hijacks focus. [-X It also does this when I start up my laptop.

*Edit*

Oh great, I got a failing hard drive. And it's a 500 gig drive too.

---

### Post by Gina on 2009-12-22
> **Jordanwb said:**
> Oh great, I got a failing hard drive. And it's a 500 gig drive too.:( :(

I've got a failing monitor and it's a 22" LCD 1680x1050 :( :(

---

### Post by Jordanwb on 2009-12-22
I'm gonna run that extended test on the drive overnight to see if it's a false positive or not.

---

