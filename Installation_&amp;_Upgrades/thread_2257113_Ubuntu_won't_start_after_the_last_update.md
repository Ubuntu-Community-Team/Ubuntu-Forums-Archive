---
title: "Ubuntu won't start after the last update"
date: 2014-12-17
forum: Installation &amp; Upgrades
---

### Post by sshatery on 2014-12-17
hey guys,

its been a while im using ubuntu gnome without any problem until 4 days ago. as usual the update center informed me for new updates. up on checking it was i think the kernel headers and nvidia drivers. and some other things like chrome. i clicked on install and after reboot the system wont start up anymore. it will stuck on that Gnome logo screen with 3 dots loading thingy. 

tried many things such as:
-removing and reinstalling the nvidia drivers 
-tried different version of drivers
-completely removed the nvidia drivers
-tried to repair the broken packages 
-tried to install the nvidia old drivers

still no good. have the same problem after every single step.

do you have any idea whats going on and how can i fix it?
and please if you give me solution, provide the codes as well coz im not that expert in linux.
thanks guys in advance

---

### Post by schragge on 2014-12-17
What version of ubuntu are you using? Any PPAs you have enabled? Because I don't see any Nvidia or Chrome updates on [http://www.ubuntuupdates.org](http://www.ubuntuupdates.org) for the last week. The latest kernel update was today. The previous kernel update was only for the lowlatency kernel on 12/12 (the updates in the **proposed** repository and PPAs being excluded).

Well, there was a kernel update for *vivid* yesterday, but I suppose you aren't running pre-alpha release? Or are you?

---

### Post by sshatery on 2014-12-17
thanks for your reply but the only PPA i had was for nvidia drivers. since i have nvidia graphic card on my computer. but other than that nothing else and im not using pre-half release kernel. thats why i dont understand whats going on.
i downloaded the ubuntu 14.04.1 and also ubuntu gnome 14.04.1 and tried to have a clean install but when it starts the graphic installation screen after few sec the screen starts to flickering and everything goes crazy but when i try to boot up using 13.10 everything is fine and no problem. seems there is something in 14.04.1 that doesnt match with my system. 
i used 13.10 live to back up my data which i was not able to to using live 14.04.1

i just dont understand it.

---

### Post by sshatery on 2014-12-17
and i forgot to mention that im using 14.04 but i think this happened when it got updated to 14.04.1. but still not so sure

---

### Post by schragge on 2014-12-17
Please post the output of
```
awk '/^2014-12-1/ && $3 == "install"' /var/log/dpkg.log
```
and
```
awk '/^2014-12-1/ && $3 == "upgrade"' /var/log/dpkg.log
```

---

### Post by Gerardo Mendez on 2014-12-17
I have a similar problem: I cannot install any OS and when I can, the installed OS always show any kind of error. Now I have installed Ubuntu 14.04 and it shows lots of errors... I have updated the packages and Libre Office never runs. No Unity at all... What's wrong? I have tried to flash the BIOS and it shows a message: Error reading the file... Is there any virus in the BIOS maybe like a corrupted firmware or something? Please, I need help.

---

### Post by schragge on 2014-12-17
@**Gerardo Mendez**: Please don't hijack this thread. Start another one.

---

### Post by schragge on 2014-12-17
@**sshatery**: Just seen [thread=2257098]this thread[/thread]. Does it ring a bell for you? Do you have similar hardware?

---

### Post by sshatery on 2014-12-17
> **schragge said:**
> @**sshatery**: Just seen [thread=2257098]this thread[/thread]. Does it ring a bell for you? Do you have similar hardware?

well thanks to all of you guys for replies. but my machine is not a a laptop, its an emachine desktop and i never had windows install on it. the only similar thing to that thread is the nvidia graphic adapter and the black screen after the loading screen of ubuntu. might be the same issue but im not sure.

i attached the output of the 2 commands you requested in 2 files. i dont know that the 2nd command will overwrite the whole "dpkg.log" file or not so i ran the 1st command copied the file to my flash drive and ran the 2nd one and copied it with a different name.

hope this will help coz i badly need that machine to be back on track again.

thanks again guys

[ATTACH]258660[/ATTACH]

---

### Post by schragge on 2014-12-17
I repost the logs for the benefit of the others.

**dpkg.log install:**
```

2014-12-15 00:02:42 install linux-headers-3.13.0-43:all <none> 3.13.0-43.72
2014-12-15 00:02:54 install linux-headers-3.13.0-43-generic:amd64 <none> 3.13.0-43.72
2014-12-16 18:08:14 install nvidia-current:amd64 <none> 304.125-0ubuntu1~xedgers14.04.1
2014-12-16 18:37:12 install ppa-purge:all <none> 0.2.8+bzr57+edgers2

```

**dpkg.log upgrade (2014-12-15):**
```

2014-12-15 00:00:54 upgrade libsepol1:amd64 2.2-1 2.2-1ubuntu0.1
2014-12-15 00:00:58 upgrade plymouth-label:amd64 0.8.8-0ubuntu17 0.8.8-0ubuntu17.1
2014-12-15 00:00:59 upgrade plymouth:amd64 0.8.8-0ubuntu17 0.8.8-0ubuntu17.1
2014-12-15 00:01:01 upgrade libplymouth2:amd64 0.8.8-0ubuntu17 0.8.8-0ubuntu17.1
2014-12-15 00:01:02 upgrade google-chrome-stable:amd64 39.0.2171.71-1 39.0.2171.95-1
2014-12-15 00:01:13 upgrade libgtk-3-common:all 3.10.8-0ubuntu1.2 3.10.8-0ubuntu1.3
2014-12-15 00:01:14 upgrade libgail-3-0:amd64 3.10.8-0ubuntu1.2 3.10.8-0ubuntu1.3
2014-12-15 00:01:15 upgrade libgtk-3-0:amd64 3.10.8-0ubuntu1.2 3.10.8-0ubuntu1.3
2014-12-15 00:01:17 upgrade libjasper1:amd64 1.900.1-14ubuntu3 1.900.1-14ubuntu3.1
2014-12-15 00:01:18 upgrade libwebkitgtk-1.0-common:all 2.4.4-1~ubuntu1 2.4.7-1~ubuntu1
2014-12-15 00:01:19 upgrade libwebkitgtk-1.0-0:amd64 2.4.4-1~ubuntu1 2.4.7-1~ubuntu1
2014-12-15 00:01:22 upgrade libjavascriptcoregtk-1.0-0:amd64 2.4.4-1~ubuntu1 2.4.7-1~ubuntu1
2014-12-15 00:01:23 upgrade libwebkitgtk-3.0-common:all 2.4.4-1~ubuntu1 2.4.7-1~ubuntu1
2014-12-15 00:01:25 upgrade libwebkitgtk-3.0-0:amd64 2.4.4-1~ubuntu1 2.4.7-1~ubuntu1
2014-12-15 00:01:28 upgrade libjavascriptcoregtk-3.0-0:amd64 2.4.4-1~ubuntu1 2.4.7-1~ubuntu1
2014-12-15 00:01:29 upgrade libreoffice-calc:amd64 1:4.2.7-0ubuntu1 1:4.2.7-0ubuntu2
2014-12-15 00:01:31 upgrade libreoffice-gnome:amd64 1:4.2.7-0ubuntu1 1:4.2.7-0ubuntu2
2014-12-15 00:01:32 upgrade libreoffice-gtk:amd64 1:4.2.7-0ubuntu1 1:4.2.7-0ubuntu2
2014-12-15 00:01:33 upgrade libreoffice-writer:amd64 1:4.2.7-0ubuntu1 1:4.2.7-0ubuntu2
2014-12-15 00:01:36 upgrade uno-libs3:amd64 4.2.7-0ubuntu1 4.2.7-0ubuntu2
2014-12-15 00:01:37 upgrade libreoffice-ogltrans:amd64 1:4.2.7-0ubuntu1 1:4.2.7-0ubuntu2
2014-12-15 00:01:38 upgrade ure:amd64 4.2.7-0ubuntu1 4.2.7-0ubuntu2
2014-12-15 00:01:40 upgrade python3-uno:amd64 1:4.2.7-0ubuntu1 1:4.2.7-0ubuntu2
2014-12-15 00:01:41 upgrade libreoffice-common:all 1:4.2.7-0ubuntu1 1:4.2.7-0ubuntu2
2014-12-15 00:01:51 upgrade libreoffice-pdfimport:amd64 1:4.2.7-0ubuntu1 1:4.2.7-0ubuntu2
2014-12-15 00:01:52 upgrade libreoffice-math:amd64 1:4.2.7-0ubuntu1 1:4.2.7-0ubuntu2
2014-12-15 00:01:53 upgrade libreoffice-base-core:amd64 1:4.2.7-0ubuntu1 1:4.2.7-0ubuntu2
2014-12-15 00:01:54 upgrade libreoffice-draw:amd64 1:4.2.7-0ubuntu1 1:4.2.7-0ubuntu2
2014-12-15 00:01:56 upgrade libreoffice-impress:amd64 1:4.2.7-0ubuntu1 1:4.2.7-0ubuntu2
2014-12-15 00:01:57 upgrade libreoffice-core:amd64 1:4.2.7-0ubuntu1 1:4.2.7-0ubuntu2
2014-12-15 00:02:04 upgrade fonts-opensymbol:all 2:102.6+LibO4.2.7-0ubuntu1 2:102.6+LibO4.2.7-0ubuntu2
2014-12-15 00:02:05 upgrade libreoffice-style-tango:all 1:4.2.7-0ubuntu1 1:4.2.7-0ubuntu2
2014-12-15 00:02:06 upgrade dnsutils:amd64 1:9.9.5.dfsg-3 1:9.9.5.dfsg-3ubuntu0.1
2014-12-15 00:02:07 upgrade bind9-host:amd64 1:9.9.5.dfsg-3 1:9.9.5.dfsg-3ubuntu0.1
2014-12-15 00:02:08 upgrade libisc95:amd64 1:9.9.5.dfsg-3 1:9.9.5.dfsg-3ubuntu0.1
2014-12-15 00:02:10 upgrade libdns100:amd64 1:9.9.5.dfsg-3 1:9.9.5.dfsg-3ubuntu0.1
2014-12-15 00:02:11 upgrade libisccc90:amd64 1:9.9.5.dfsg-3 1:9.9.5.dfsg-3ubuntu0.1
2014-12-15 00:02:12 upgrade libisccfg90:amd64 1:9.9.5.dfsg-3 1:9.9.5.dfsg-3ubuntu0.1
2014-12-15 00:02:13 upgrade liblwres90:amd64 1:9.9.5.dfsg-3 1:9.9.5.dfsg-3ubuntu0.1
2014-12-15 00:02:14 upgrade libbind9-90:amd64 1:9.9.5.dfsg-3 1:9.9.5.dfsg-3ubuntu0.1
2014-12-15 00:02:15 upgrade plymouth-theme-ubuntu-text:amd64 0.8.8-0ubuntu17 0.8.8-0ubuntu17.1
2014-12-15 00:02:16 upgrade gir1.2-gtk-3.0:amd64 3.10.8-0ubuntu1.2 3.10.8-0ubuntu1.3
2014-12-15 00:02:17 upgrade gir1.2-webkit-3.0:amd64 2.4.4-1~ubuntu1 2.4.7-1~ubuntu1
2014-12-15 00:02:18 upgrade gir1.2-javascriptcoregtk-3.0:amd64 2.4.4-1~ubuntu1 2.4.7-1~ubuntu1
2014-12-15 00:02:19 upgrade ubuntu-release-upgrader-gtk:all 1:0.220.5 1:0.220.6
2014-12-15 00:02:20 upgrade ubuntu-release-upgrader-core:all 1:0.220.5 1:0.220.6
2014-12-15 00:02:22 upgrade python3-distupgrade:all 1:0.220.5 1:0.220.6
2014-12-15 00:02:24 upgrade tcpdump:amd64 4.5.1-2ubuntu1 4.5.1-2ubuntu1.1
2014-12-15 00:02:25 upgrade python3-problem-report:all 2.14.1-0ubuntu3.5 2.14.1-0ubuntu3.6
2014-12-15 00:02:26 upgrade python3-apport:all 2.14.1-0ubuntu3.5 2.14.1-0ubuntu3.6
2014-12-15 00:02:28 upgrade apport:all 2.14.1-0ubuntu3.5 2.14.1-0ubuntu3.6
2014-12-15 00:02:31 upgrade apport-gtk:all 2.14.1-0ubuntu3.5 2.14.1-0ubuntu3.6
2014-12-15 00:02:32 upgrade dkms:all 2.2.0.3-1.1ubuntu5 2.2.0.3-1.1ubuntu5.14.04
2014-12-15 00:02:34 upgrade flashplugin-installer:amd64 11.2.202.424ubuntu0.14.04.1 11.2.202.425ubuntu0.14.04.1
2014-12-15 00:02:36 upgrade libcuda1-304:amd64 304.117-0ubuntu1 304.125-0ubuntu0.0.1
2014-12-15 00:02:38 upgrade libgtk-3-bin:amd64 3.10.8-0ubuntu1.2 3.10.8-0ubuntu1.3
2014-12-15 00:02:39 upgrade liblightdm-gobject-1-0:amd64 1.10.1-0ubuntu1 1.10.3-0ubuntu2
2014-12-15 00:02:40 upgrade libreoffice-avmedia-backend-gstreamer:amd64 1:4.2.7-0ubuntu1 1:4.2.7-0ubuntu2
2014-12-15 00:02:41 upgrade libreoffice-presentation-minimizer:all 1:4.2.7-0ubuntu1 1:4.2.7-0ubuntu2
2014-12-15 00:02:58 upgrade linux-headers-generic:amd64 3.13.0.40.47 3.13.0.43.50
2014-12-15 00:02:59 upgrade linux-libc-dev:amd64 3.13.0-40.69 3.13.0-43.72
2014-12-15 00:03:00 upgrade xserver-common:all 2:1.15.1-0ubuntu2.1 2:1.15.1-0ubuntu2.5
2014-12-15 00:03:01 upgrade xserver-xorg-core:amd64 2:1.15.1-0ubuntu2.1 2:1.15.1-0ubuntu2.5
2014-12-15 00:03:03 upgrade nvidia-304:amd64 304.117-0ubuntu1 304.125-0ubuntu0.0.1
2014-12-15 00:04:11 upgrade nvidia-libopencl1-304:amd64 304.117-0ubuntu1 304.125-0ubuntu0.0.1
2014-12-15 00:04:12 upgrade nvidia-opencl-icd-304:amd64 304.117-0ubuntu1 304.125-0ubuntu0.0.1
2014-12-15 00:04:14 upgrade python-problem-report:all 2.14.1-0ubuntu3.5 2.14.1-0ubuntu3.6
2014-12-15 00:04:15 upgrade python-apport:all 2.14.1-0ubuntu3.5 2.14.1-0ubuntu3.6
2014-12-15 00:04:17 upgrade spamassassin:all 3.4.0-1ubuntu1 3.4.0-1ubuntu2
2014-12-15 00:04:19 upgrade sa-compile:all 3.4.0-1ubuntu1 3.4.0-1ubuntu2
2014-12-15 00:04:20 upgrade spamc:amd64 3.4.0-1ubuntu1 3.4.0-1ubuntu2
2014-12-15 00:04:21 upgrade xserver-xephyr:amd64 2:1.15.1-0ubuntu2.1 2:1.15.1-0ubuntu2.5
2014-12-15 00:04:22 upgrade xvfb:amd64 2:1.15.1-0ubuntu2.1 2:1.15.1-0ubuntu2.5

```

**dpkg.log upgrade (2014-12-16):**
```

2014-12-16 18:21:31 upgrade libdrm2:amd64 2.4.52-1 2.4.58+git20141201.f99522e6-0ubuntu0ricotz~trusty
2014-12-16 18:21:32 upgrade libdrm2:i386 2.4.52-1 2.4.58+git20141201.f99522e6-0ubuntu0ricotz~trusty
2014-12-16 18:21:33 upgrade libdrm-intel1:i386 2.4.52-1 2.4.58+git20141201.f99522e6-0ubuntu0ricotz~trusty
2014-12-16 18:21:34 upgrade libdrm-intel1:amd64 2.4.52-1 2.4.58+git20141201.f99522e6-0ubuntu0ricotz~trusty
2014-12-16 18:21:35 upgrade libdrm-nouveau2:i386 2.4.52-1 2.4.58+git20141201.f99522e6-0ubuntu0ricotz~trusty
2014-12-16 18:21:36 upgrade libdrm-nouveau2:amd64 2.4.52-1 2.4.58+git20141201.f99522e6-0ubuntu0ricotz~trusty
2014-12-16 18:21:37 upgrade libdrm-radeon1:i386 2.4.52-1 2.4.58+git20141201.f99522e6-0ubuntu0ricotz~trusty
2014-12-16 18:21:39 upgrade libdrm-radeon1:amd64 2.4.52-1 2.4.58+git20141201.f99522e6-0ubuntu0ricotz~trusty
2014-12-16 18:21:39 upgrade xserver-xorg-video-glamoregl:amd64 0.6.0-0ubuntu4 0.6.0+git20140801.347ef4f0-0ubuntu0sarvatt~trusty
2014-12-16 18:21:40 upgrade libglamor0:amd64 0.6.0-0ubuntu4 0.6.0+git20140801.347ef4f0-0ubuntu0sarvatt~trusty
2014-12-16 18:21:42 upgrade libllvm3.4:i386 1:3.4-1ubuntu3 1:3.4.2-3ubuntu2~xedgers
2014-12-16 18:21:46 upgrade libllvm3.4:amd64 1:3.4-1ubuntu3 1:3.4.2-3ubuntu2~xedgers
2014-12-16 18:21:49 upgrade libopenvg1-mesa:amd64 10.1.3-0ubuntu0.2 10.4.0~git20141112.7a82961b-0ubuntu0ricotz~trusty
2014-12-16 18:21:51 upgrade libcuda1-304:amd64 304.125-0ubuntu0.0.1 304.125-0ubuntu1~xedgers14.04.1
2014-12-16 18:21:54 upgrade nvidia-304:amd64 304.125-0ubuntu0.0.1 304.125-0ubuntu1~xedgers14.04.1
2014-12-16 18:22:32 upgrade nvidia-libopencl1-304:amd64 304.125-0ubuntu0.0.1 304.125-0ubuntu1~xedgers14.04.1
2014-12-16 18:22:33 upgrade nvidia-opencl-icd-304:amd64 304.125-0ubuntu0.0.1 304.125-0ubuntu1~xedgers14.04.1
2014-12-16 18:22:37 upgrade nvidia-settings:amd64 331.20-0ubuntu8 346.22-0ubuntu1~xedgers14.04.1
2014-12-16 18:22:38 upgrade xserver-xorg-video-radeon:amd64 1:7.3.0-1ubuntu3.1 1:7.4.99+git20140806.fbf575cb-0ubuntu0sarvatt~trusty
2014-12-16 18:22:39 upgrade xserver-xorg-video-ati:amd64 1:7.3.0-1ubuntu3.1 1:7.4.99+git20140806.fbf575cb-0ubuntu0sarvatt~trusty
2014-12-16 18:22:40 upgrade xserver-xorg-video-intel:amd64 2:2.99.910-0ubuntu1.3 2:2.99.916+git20141215.99537089-0ubuntu0sarvatt~trusty
2014-12-16 18:22:42 upgrade xserver-xorg-video-neomagic:amd64 1:1.2.8-1build1 1:1.2.8+git20140806.74a9a343-0ubuntu0sarvatt~trusty
2014-12-16 18:22:42 upgrade xserver-xorg-video-nouveau:amd64 1:1.0.10-1ubuntu2 1:1.0.11+git20141030.3fb97d78-0ubuntu0sarvatt~trusty2
2014-12-16 18:22:43 upgrade xserver-xorg-video-sisusb:amd64 1:0.9.6-2build1 1:0.9.6+git20140806.293d0902-0ubuntu0sarvatt~trusty
2014-12-16 18:22:44 upgrade xserver-xorg-video-trident:amd64 1:1.3.6-0ubuntu5 1:1.3.6+git20140806.562c38ca-0ubuntu0sarvatt~trusty
2014-12-16 18:22:45 upgrade xserver-xorg-video-vmware:amd64 1:13.0.2-2ubuntu1 1:13.0.2+git20140804.0a596fd0-0ubuntu0sarvatt~trusty

```

**dpkg.log remove:**
```

2014-12-16 18:44:24 remove nvidia-current:amd64 304.125-0ubuntu1~xedgers14.04.1 <none>
2014-12-16 18:44:25 remove nvidia-304:amd64 304.125-0ubuntu1~xedgers14.04.1 <none>
2014-12-16 18:44:29 remove nvidia-opencl-icd-304:amd64 304.125-0ubuntu1~xedgers14.04.1 <none>
2014-12-16 18:44:30 remove nvidia-libopencl1-304:amd64 304.125-0ubuntu1~xedgers14.04.1 <none>
2014-12-16 18:44:31 remove nvidia-settings:amd64 346.22-0ubuntu1~xedgers14.04.1 <none>

```

---

### Post by schragge on 2014-12-17
Looks like you're using [ppa:xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa") (or were using if after installing **ppa-purge** you removed the PPA.)

And here is the changelog for the nvidia driver that came with the latest security update that apparently broke your system.

```
nvidia-graphics-drivers-304 (304.125-0ubuntu0.0.1) trusty-security; urgency=medium

  [ Alberto Milone ]
  * New upstream release.
  * debian/substvars:
    - Add support for video ABIs up to 19.
  * debian/templates/dkms_nvidia.conf.in:
     [COLOR=red]- Drop the patches for recent kernels.[/COLOR]
  * SECURITY UPDATE:
    - CVE-2014-8091, CVE-2014-8098, CVE-2014-8298 (LP: #1400673).

 -- Alberto Milone <alberto.milone@canonical.com>  Tue, 09 Dec 2014 18:42:30 +0100
```

I marked in [COLOR=red]red[/COLOR] the part that seems suspicious to me. Actually, it seems [a patch for kernel 3.13 was dropped]("http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/trusty/nvidia-graphics-drivers-304/trusty-updates/revision/23/debian/templates/dkms.conf.in"). I see the package **linux-headers-3.13.0-43-generic** being installed as part of the upgrade, so I assume the kernel you're currently running is 3.13. Maybe try upgrading your kernel? There is **linux-image-generic-lts-utopic** backported to trusty that contains kernel 3.16.0.

Actually, I'm not sure I'm reading the change right. Maybe the reason behind dropping the patch is an assumption that anybody using the driver nvidia-304 is running kernel **older** than 3.13. Then instead of upgrading the kernel you should upgrade to a newer nvidia driver, e.g. **nvidia-331**. Yes, it seems a bit weird that **nvidia-current** still points to **nvidia-304** although **nvidia-331** is also available for trusty.

Obviously, you can attempt upgrading *both* the kernel and the nvidia driver:
```

sudo apt-get install linux-image-generic-lts-utopic

```
Then reboot into the new kernel, and
```

sudo apt-get install nvidia-331

```

---

### Post by oldfred on 2014-12-17
The nvidia 304.xx is a legacy driver, and you probably should not be using the newer driver as it may not work with the older video card?
What video card?

       nVidia driver versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

---

### Post by sshatery on 2014-12-17
thanks for your replies guys.
in fact the latest driver that nvidia website is providing me for linux is 304.88 and thats i was using since long time ago.
my graphic adapter is "GeForce 6150SE nForce 430" on an emachine desktop.
as what i mentioned i tried to remove the current drivers and install the 304.88 and also reinstall the drivers using PPA but none of them worked. seems something is messed up but im not sure what.

and to answer @schragge yes i used purge to remove the nvidia PPA and all of the nvidia drivers and install the driver that i downloaded from nvidia website but it didnt work as well.
i will do what you guys told me and will post the result here ASAP.

---

### Post by sshatery on 2014-12-17
guys i just realized the kernel version i have on the system is "3.11.0-23-generic" not the 3.13

and i get this when i try to install the nvidia driver:
```
First Installation: checking all kernels...
Building only for 3.11.0-23-generic
Building for architecture x86_64
**Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.**
```

---

### Post by sshatery on 2014-12-18
finally i solved the problem. i was feeling the installation of the new 3.13 on last update was not well done. so what i did is "sudo apt-get install --reinstall linux-generic" and after reboot.........
boooom! it worked.

thanks for all of your help guys.

---

### Post by elliot6 on 2014-12-18
I also have the same problem. Only since updating to 3.13.0-43-generic. If I use 3.13.0-40-generic it works fine.

Assuming this issue hasn't been fixed thus far?

Thanks

---

### Post by oldfred on 2014-12-18
@elliot6
This thread is solved, so if the procedure the OP did, redownload kernel, does not work then better to post your own new thread. Users who can help typically do not look at solved threads, only those looking for solutions.

---

