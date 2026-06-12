---
title: "How to install nivida drivers on ubuntu 22.04"
date: 2023-09-18
forum: Installation &amp; Upgrades
---

### Post by d3vestator on 2023-09-18
am having bootinig errors as well as errors when shutting down
from the previous thread, i was told it might be the NVIDIA drivers affecting it


[https://paste.ubuntu.com/p/4mpybdHFqj/](https://paste.ubuntu.com/p/4mpybdHFqj/)

---

### Post by TheFu on 2023-09-19
```
sudo apt update
sudo apt upgrade
reboot              # if needed
sudo ubuntu-drivers autoinstall
```

This does it, assuming the nvidia GPU is still supported.  If not, you are out of luck.

The pastebin requires a login, so I didn't review it. Sorry.

---

### Post by MAFoElffen on 2023-09-19
From 'system-info' report:
```

NVidia GA107M [GeForce RTX 3050 Mobile]

```
Do this...
```

sudo apt update
sudo apt remove --purge nvidia*  ## to remove anything that was there before, for the just-in-cases
sudo unbuntu-drivers list

```
That should show you what drivers are recommended for your GPU. The format of the name will be: nvidia-drivers-XXX, with XXX being the driver version.

I have been currently using nvidia-driver-535 with no problems.

To install one from the list, then do (example shown for 535)
```

sudo apt install nvidia-driver-535 nvidia-dkms-535
sudo reboot

```
Test it. There may be up to a 20 second pause between the Graphical login and the Desktop, wait for it before deciding it doesn't work. 

If there are problems: wash, rinse, repeat all the steps above, to try another driver, until you find one that your system is happy with. 

If it goes dark, and loses the Graphics for trying a driver, press the keys <Cntrl><Alt><F4>, log in to VTTY4 with your credentials and do the steps above again with another driver.

You can also do it via the GUI, in the "Software & Updates" app > Alternate Drivers Tab > Select a driver > Install... But (in the past) it sometimes left fragments of old drivers on the system, so I do not recommend that to people as one of my solutions.

Tell us how that goes for you.

---

### Post by d3vestator on 2023-09-28
i was trying different Nvidia drivers and i must done something, becasue whenever i log in, it says


failed to start Samba NMB Daemon, i through that if i were to plug a removable drive instead and download the drivers from there in "try ubuntu" it worked but, i cant reboot it without getting that error

any suggestions?

---

### Post by TheFu on 2023-09-29
> **d3vestator said:**
>  
any suggestions?

What follows is a bit ranty. Sorry.  Probably not of any use to anyone. **Don't read what follows.**

Driver issues is why I started avoiding nvidia GPUs after preferring them for about 15 yrs.  Late last year, I replaced a 3 yr old CPU+ nVidia GPU with a new CPU that had integrated GPU for about $120. Socket compatible, thanks to Ryzen.  The newer iGPU is actually faster than the 3 yr old nVidia GPU AND well supported, without hassles, by Ubuntu/Linux.  Plus the system uses less power now too while the CPU can be 40% faster.

Having a GPU that *just works*, priceless.  nVidia seems to finally be trying to work in the F/LOSS way, but they are still making it harder for reasons only they understand, internally, [https://videocardz.com/press-release/nvidia-releases-open-source-gpu-kernel-for-linux](https://videocardz.com/press-release/nvidia-releases-open-source-gpu-kernel-for-linux)

And Samba isn't doing you any favors either, but sometimes we need something that works. Only use Samba when there is MSFT computers involved. Otherwise, avoid.  Samba isn't the core issue. nvidia drivers have caused network problems previously, which makes no sense, except that the code is crap if it is so bad that it harms other subsystems.

---

### Post by SeijiSensei on 2023-09-29
> **d3vestator said:**
> failed to start Samba NMB Daemon
Did you run 
```
sudo systemctl enable samba
sudo systemctl start samba

```

You need to use "enable" to have the server started automatically at boot time. Otherwise you'll always have to start it manually.

NVIDIA drivers have nothing to do with this.

---

### Post by d3vestator on 2023-10-07
when i use the command: sudo systemctl enable samba or smbd
answer: Failed to enable unit: Unit file smbd.service does not exist

---

### Post by #&amp;thj^% on 2023-10-09
Samba has been renamed ie:
```
systemctl status smbd 
```
Mine:
```
&#9679; smbd.service - Samba SMB Daemon
     Loaded: loaded (/lib/systemd/system/smbd.service; enabled; vendor preset: enabled)
     Active: active (running) since Mon 2023-10-09 10:05:57 MDT; 27s ago
       Docs: man:smbd(8)
             man:samba(7)
             man:smb.conf(5)
    Process: 433531 ExecCondition=/usr/share/samba/is-configured smb (code=exited, status=0/SUCCESS)
    Process: 433533 ExecStartPre=/usr/share/samba/update-apparmor-samba-profile (code=exited, status=0/SUCCESS)
   Main PID: 433542 (smbd)
     Status: "smbd: ready to serve connections..."
      Tasks: 3 (limit: 18247)
     Memory: 6.8M
        CPU: 128ms
     CGroup: /system.slice/smbd.service
             &#9500;&#9472;433542 /usr/sbin/smbd --foreground --no-process-group
             &#9500;&#9472;433545 /usr/sbin/smbd --foreground --no-process-group
             &#9492;&#9472;433546 /usr/sbin/smbd --foreground --no-process-group

Oct 09 10:05:57 zfs-home systemd[1]: Starting Samba SMB Daemon...
Oct 09 10:05:57 zfs-home systemd[1]: Started Samba SMB Daemon.

```
If you look at:
```
systemctl status samba
&#9675; samba-ad-dc.service - Samba AD Daemon
     Loaded: loaded (/lib/systemd/system/samba-ad-dc.service; enabled; vendor preset: enabled)
     Active: inactive (dead) (Result: exec-condition) since Mon 2023-10-09 10:04:22 MDT; 5min ago
  Condition: start condition failed at Mon 2023-10-09 10:04:22 MDT; 5min ago
       Docs: man:samba(8)
             man:samba(7)
             man:smb.conf(5)
    Process: 428302 ExecCondition=/usr/share/samba/is-configured samba (code=exited, status=1/FAILURE)
        CPU: 52ms

Oct 09 10:04:22 zfs-home systemd[1]: Starting Samba AD Daemon...
Oct 09 10:04:22 zfs-home systemd[1]: samba-ad-dc.service: Skipped due to 'exec-condition'.
Oct 09 10:04:22 zfs-home systemd[1]: Condition check resulted in Samba AD Daemon being skipped.

```
I just don't see how samba and nVidia would interfere with each other.?
EDIT: Also see oldfred's post below:
```
dkms status
8812au/5.6.4.2_35491.20191025, 5.15.0-86-generic, x86_64: installed
8812au/5.6.4.2_35491.20191025, 6.2.0-34-generic, x86_64: installed
nvidia/535.113.01, 6.2.0-34-generic, x86_64: installed

```

---

### Post by oldfred on 2023-10-09
If you have installed nVidia drivers, you must purge before installing a different one. Also never install directly from nVidia with its .run file.

This will show if it is correctly installed:
#What is installed
dkms status

Then as posted above install driver.
sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you can manually choose any in list.
sudo apt-get install nvidia-XXX 

I agree with TheFu on video.
I used to always install nVidia card, but had bit older video card with newer CPU that included GPU. Found Intel CPU had better graphics performance than old nVidia card. And I do not game, so do not need expensive high performance video.

This was my older system and still using Skylake system.
[https://www.videocardbenchmark.net/low_end_gpus.html](https://www.videocardbenchmark.net/low_end_gpus.html) 

```

GeForce GT 620                    430
Intel® HD Graphics 4600           712  Haswell
Intel HD Graphics 620             927  Skylake

```

---

### Post by d3vestator on 2023-10-22
```


[COLOR=#000000]ubuntu@ubuntu:~$ systemctl status smbd[/COLOR]
[COLOR=#000000]Unit smbd.service could not be found.[/COLOR]
[COLOR=#000000]ubuntu@ubuntu:~$ dkms status[/COLOR]
[COLOR=#000000]ubuntu@ubuntu:~$ sudo-get remove --purge nvidia-*[/COLOR]
[COLOR=#000000]sudo-get: command not found[/COLOR]
[COLOR=#000000]ubuntu@ubuntu:~$ sudo apt-get remove --purge nvidia-*[/COLOR]
[COLOR=#000000]Reading package lists... Done[/COLOR]
[COLOR=#000000]Building dependency tree... Done[/COLOR]
[COLOR=#000000]Reading state information... Done[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-opencl-icd' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-compute-utils-390' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-utils' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-compute-utils-470' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-dkms-390' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-compute-utils-510' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-compute-utils-515' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-dkms-470' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-dkms-510' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-dkms-515' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-driver-390' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-driver-418' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-driver-430' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-driver-435' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-driver-440' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-driver-450' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-driver-455' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-driver-460' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-driver-465' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-driver-470' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-driver-495' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-driver-510' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-driver-515' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-utils-390' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-utils-470' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-utils-510' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-utils-515' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-egl-wayland-common' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-kernel-common-390' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-kernel-common-470' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-prebuilt-kernel' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-kernel-common-510' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-kernel-common-515' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-compute-utils' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-kernel-common' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-prime' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-384' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-390' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-settings' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-kernel-source-390' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-kernel-source-470' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-kernel-source-510' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-kernel-source-515' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-settings-binary' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-kernel-source' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-common' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-persistenced' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-driver-binary' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-smi' for glob 'nvidia-*'[/COLOR]
[COLOR=#000000]Package 'nvidia-egl-wayland-common' is not installed, so not removed[/COLOR]
[COLOR=#000000]Note, selecting 'nvidia-settings' instead of 'nvidia-settings-binary'[/COLOR]
[COLOR=#000000]Package 'nvidia-384' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-390' is not installed, so not removed[/COLOR]
[COLOR=#000000]Note, selecting 'ubuntu-drivers-common' instead of 'nvidia-common'[/COLOR]
[COLOR=#000000]Package 'nvidia-prime' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-settings' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-compute-utils-390' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-driver-390' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-kernel-common-390' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-kernel-source-390' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-utils-390' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-driver-418' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-driver-430' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-driver-440' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-driver-435' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-driver-450' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-driver-455' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-compute-utils-470' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-driver-460' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-driver-465' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-driver-470' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-kernel-common-470' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-kernel-source-470' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-utils-470' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-compute-utils-510' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-driver-495' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-driver-510' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-kernel-common-510' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-kernel-source-510' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-utils-510' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-compute-utils-515' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-driver-515' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-kernel-common-515' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-kernel-source-515' is not installed, so not removed[/COLOR]
[COLOR=#000000]Package 'nvidia-utils-515' is not installed, so not removed[/COLOR]
[COLOR=#000000]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/COLOR]
[COLOR=#000000]ubuntu@ubuntu:~$ sudo ubuntu-drivers devices[/COLOR]
[COLOR=#000000]== /sys/devices/pci0000:00/0000:00:01.1/0000:01:00.0 ==[/COLOR]
[COLOR=#000000]modalias : pci:v000010DEd000025A2sv00001043sd0000186Cbc03sc02 i00[/COLOR]
[COLOR=#000000]vendor : NVIDIA Corporation[/COLOR]
[COLOR=#000000]model : GA107M [GeForce RTX 3050 Mobile][/COLOR]
[COLOR=#000000]driver : nvidia-driver-515 - distro non-free recommended[/COLOR]
[COLOR=#000000]driver : nvidia-driver-510 - distro non-free[/COLOR]
[COLOR=#000000]driver : nvidia-driver-470 - distro non-free[/COLOR]
[COLOR=#000000]driver : xserver-xorg-video-nouveau - distro free builtin[/COLOR]

[COLOR=#000000]ubuntu@ubuntu:~$ sudo ubuntu-drivers autoinstall[/COLOR]
[COLOR=#000000]Reading package lists... Done[/COLOR]
[COLOR=#000000]Building dependency tree... Done[/COLOR]
[COLOR=#000000]Reading state information... Done[/COLOR]
[COLOR=#000000]The following additional packages will be installed:[/COLOR]
[COLOR=#000000]libnvidia-cfg1-515 libnvidia-common-515 libnvidia-compute-515 libnvidia-decode-515 libnvidia-egl-wayland1 libnvidia-encode-515 libnvidia-extra-515 libnvidia-fbc1-515 libnvidia-gl-515 libvdpau1[/COLOR]
[COLOR=#000000]libxnvctrl0 linux-modules-nvidia-515-5.15.0-43-generic linux-objects-nvidia-515-5.15.0-43-generic linux-signatures-nvidia-5.15.0-43-generic mesa-vdpau-drivers nvidia-compute-utils-515[/COLOR]
[COLOR=#000000]nvidia-kernel-common-515 nvidia-kernel-source-515 nvidia-prime nvidia-settings nvidia-utils-515 pkg-config screen-resolution-extra vdpau-driver-all xserver-xorg-video-nvidia-515[/COLOR]
[COLOR=#000000]Suggested packages:[/COLOR]
[COLOR=#000000]libvdpau-va-gl1[/COLOR]
[COLOR=#000000]Recommended packages:[/COLOR]
[COLOR=#000000]libnvidia-compute-515:i386 libnvidia-decode-515:i386 libnvidia-encode-515:i386 libnvidia-fbc1-515:i386 libnvidia-gl-515:i386[/COLOR]
[COLOR=#000000]The following NEW packages will be installed:[/COLOR]
[COLOR=#000000]libnvidia-cfg1-515 libnvidia-common-515 libnvidia-compute-515 libnvidia-decode-515 libnvidia-egl-wayland1 libnvidia-encode-515 libnvidia-extra-515 libnvidia-fbc1-515 libnvidia-gl-515 libvdpau1[/COLOR]
[COLOR=#000000]libxnvctrl0 linux-modules-nvidia-515-5.15.0-43-generic linux-modules-nvidia-515-generic-hwe-22.04 linux-objects-nvidia-515-5.15.0-43-generic linux-signatures-nvidia-5.15.0-43-generic[/COLOR]
[COLOR=#000000]mesa-vdpau-drivers nvidia-compute-utils-515 nvidia-driver-515 nvidia-kernel-common-515 nvidia-kernel-source-515 nvidia-prime nvidia-settings nvidia-utils-515 pkg-config screen-resolution-extra[/COLOR]
[COLOR=#000000]vdpau-driver-all xserver-xorg-video-nvidia-515[/COLOR]
[COLOR=#000000]0 upgraded, 27 newly installed, 0 to remove and 0 not upgraded.[/COLOR]
[COLOR=#000000]Need to get 0 B/346 MB of archives.[/COLOR]
[COLOR=#000000]After this operation, 810 MB of additional disk space will be used.[/COLOR]
[COLOR=#000000]Get:1 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/restricted amd64 libnvidia-cfg1-515 amd64 515.65.01-0ubuntu0.22.04.1 [94.0 kB][/COLOR]
[COLOR=#000000]Get:2 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/restricted amd64 libnvidia-common-515 all 515.65.01-0ubuntu0.22.04.1 [9,778 B][/COLOR]
[COLOR=#000000]Get:3 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/restricted amd64 libnvidia-compute-515 amd64 515.65.01-0ubuntu0.22.04.1 [49.9 MB][/COLOR]
[COLOR=#000000]Get:4 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/restricted amd64 libnvidia-decode-515 amd64 515.65.01-0ubuntu0.22.04.1 [1,449 kB][/COLOR]
[COLOR=#000000]Get:5 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 libnvidia-egl-wayland1 amd64 1:1.1.9-1.1 [26.1 kB][/COLOR]
[COLOR=#000000]Get:6 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/restricted amd64 libnvidia-encode-515 amd64 515.65.01-0ubuntu0.22.04.1 [45.3 kB][/COLOR]
[COLOR=#000000]Get:7 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/restricted amd64 libnvidia-extra-515 amd64 515.65.01-0ubuntu0.22.04.1 [60.9 kB][/COLOR]
[COLOR=#000000]Get:8 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/restricted amd64 libnvidia-fbc1-515 amd64 515.65.01-0ubuntu0.22.04.1 [50.6 kB][/COLOR]
[COLOR=#000000]Get:9 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/restricted amd64 libnvidia-gl-515 amd64 515.65.01-0ubuntu0.22.04.1 [189 MB][/COLOR]
[COLOR=#000000]Get:10 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 libvdpau1 amd64 1.4-3build2 [27.0 kB][/COLOR]
[COLOR=#000000]Get:11 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 libxnvctrl0 amd64 510.47.03-0ubuntu1 [11.5 kB][/COLOR]
[COLOR=#000000]Get:12 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/restricted amd64 linux-signatures-nvidia-5.15.0-43-generic amd64 5.15.0-43.46+1 [36.7 kB][/COLOR]
[COLOR=#000000]Get:13 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/restricted amd64 linux-objects-nvidia-515-5.15.0-43-generic amd64 5.15.0-43.46+1 [42.8 MB][/COLOR]
[COLOR=#000000]Get:14 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/restricted amd64 nvidia-kernel-common-515 amd64 515.65.01-0ubuntu0.22.04.1 [25.2 MB][/COLOR]
[COLOR=#000000]Get:15 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/restricted amd64 linux-modules-nvidia-515-5.15.0-43-generic amd64 5.15.0-43.46+1 [7,024 B][/COLOR]
[COLOR=#000000]Get:16 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/restricted amd64 linux-modules-nvidia-515-generic-hwe-22.04 amd64 5.15.0-43.46+1 [5,370 B][/COLOR]
[COLOR=#000000]Get:17 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 mesa-vdpau-drivers amd64 22.0.5-0ubuntu0.1 [3,247 kB][/COLOR]
[COLOR=#000000]Get:18 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/restricted amd64 nvidia-compute-utils-515 amd64 515.65.01-0ubuntu0.22.04.1 [114 kB][/COLOR]
[COLOR=#000000]Get:19 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/restricted amd64 nvidia-kernel-source-515 amd64 515.65.01-0ubuntu0.22.04.1 [31.3 MB][/COLOR]
[COLOR=#000000]Get:20 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/restricted amd64 nvidia-utils-515 amd64 515.65.01-0ubuntu0.22.04.1 [366 kB][/COLOR]
[COLOR=#000000]Get:21 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/restricted amd64 xserver-xorg-video-nvidia-515 amd64 515.65.01-0ubuntu0.22.04.1 [1,483 kB][/COLOR]
[COLOR=#000000]Get:22 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/restricted amd64 nvidia-driver-515 amd64 515.65.01-0ubuntu0.22.04.1 [467 kB][/COLOR]
[COLOR=#000000]Get:23 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 nvidia-prime all 0.8.17.1 [9,956 B][/COLOR]
[COLOR=#000000]Get:24 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 pkg-config amd64 0.29.2-1ubuntu3 [48.2 kB][/COLOR]
[COLOR=#000000]Get:25 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 screen-resolution-extra all 0.18.2 [4,396 B][/COLOR]
[COLOR=#000000]Get:26 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 nvidia-settings amd64 510.47.03-0ubuntu1 [960 kB][/COLOR]
[COLOR=#000000]Get:27 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 vdpau-driver-all amd64 1.4-3build2 [4,510 B][/COLOR]
[COLOR=#000000]Preconfiguring packages ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package libnvidia-cfg1-515:amd64.[/COLOR]
[COLOR=#000000](Reading database ... 212578 files and directories currently installed.)[/COLOR]
[COLOR=#000000]Preparing to unpack .../00-libnvidia-cfg1-515_515.65.01-0ubuntu0.22.04.1_amd64.deb ...[/COLOR]
[COLOR=#000000]Unpacking libnvidia-cfg1-515:amd64 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package libnvidia-common-515.[/COLOR]
[COLOR=#000000]Preparing to unpack .../01-libnvidia-common-515_515.65.01-0ubuntu0.22.04.1_all.deb ...[/COLOR]
[COLOR=#000000]Unpacking libnvidia-common-515 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package libnvidia-compute-515:amd64.[/COLOR]
[COLOR=#000000]Preparing to unpack .../02-libnvidia-compute-515_515.65.01-0ubuntu0.22.04.1_amd64.deb ...[/COLOR]
[COLOR=#000000]Unpacking libnvidia-compute-515:amd64 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package libnvidia-decode-515:amd64.[/COLOR]
[COLOR=#000000]Preparing to unpack .../03-libnvidia-decode-515_515.65.01-0ubuntu0.22.04.1_amd64.deb ...[/COLOR]
[COLOR=#000000]Unpacking libnvidia-decode-515:amd64 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package libnvidia-egl-wayland1:amd64.[/COLOR]
[COLOR=#000000]Preparing to unpack .../04-libnvidia-egl-wayland1_1.1.9-1.1_amd64.deb ...[/COLOR]
[COLOR=#000000]Unpacking libnvidia-egl-wayland1:amd64 (1:1.1.9-1.1) ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package libnvidia-encode-515:amd64.[/COLOR]
[COLOR=#000000]Preparing to unpack .../05-libnvidia-encode-515_515.65.01-0ubuntu0.22.04.1_amd64.deb ...[/COLOR]
[COLOR=#000000]Unpacking libnvidia-encode-515:amd64 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package libnvidia-extra-515:amd64.[/COLOR]
[COLOR=#000000]Preparing to unpack .../06-libnvidia-extra-515_515.65.01-0ubuntu0.22.04.1_amd64.deb ...[/COLOR]
[COLOR=#000000]Unpacking libnvidia-extra-515:amd64 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package libnvidia-fbc1-515:amd64.[/COLOR]
[COLOR=#000000]Preparing to unpack .../07-libnvidia-fbc1-515_515.65.01-0ubuntu0.22.04.1_amd64.deb ...[/COLOR]
[COLOR=#000000]Unpacking libnvidia-fbc1-515:amd64 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package libnvidia-gl-515:amd64.[/COLOR]
[COLOR=#000000]Preparing to unpack .../08-libnvidia-gl-515_515.65.01-0ubuntu0.22.04.1_amd64.deb ...[/COLOR]
[COLOR=#000000]dpkg-query: no packages found matching libnvidia-gl-510[/COLOR]
[COLOR=#000000]Unpacking libnvidia-gl-515:amd64 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package libvdpau1:amd64.[/COLOR]
[COLOR=#000000]Preparing to unpack .../09-libvdpau1_1.4-3build2_amd64.deb ...[/COLOR]
[COLOR=#000000]Unpacking libvdpau1:amd64 (1.4-3build2) ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package libxnvctrl0:amd64.[/COLOR]
[COLOR=#000000]Preparing to unpack .../10-libxnvctrl0_510.47.03-0ubuntu1_amd64.deb ...[/COLOR]
[COLOR=#000000]Unpacking libxnvctrl0:amd64 (510.47.03-0ubuntu1) ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package linux-signatures-nvidia-5.15.0-43-generic.[/COLOR]
[COLOR=#000000]Preparing to unpack .../11-linux-signatures-nvidia-5.15.0-43-generic_5.15.0-43.46+1_amd64.deb ...[/COLOR]
[COLOR=#000000]Unpacking linux-signatures-nvidia-5.15.0-43-generic (5.15.0-43.46+1) ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package linux-objects-nvidia-515-5.15.0-43-generic.[/COLOR]
[COLOR=#000000]Preparing to unpack .../12-linux-objects-nvidia-515-5.15.0-43-generic_5.15.0-43.46+1_amd64.deb ...[/COLOR]
[COLOR=#000000]Unpacking linux-objects-nvidia-515-5.15.0-43-generic (5.15.0-43.46+1) ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package nvidia-kernel-common-515.[/COLOR]
[COLOR=#000000]Preparing to unpack .../13-nvidia-kernel-common-515_515.65.01-0ubuntu0.22.04.1_amd64.deb ...[/COLOR]
[COLOR=#000000]Unpacking nvidia-kernel-common-515 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package linux-modules-nvidia-515-5.15.0-43-generic.[/COLOR]
[COLOR=#000000]Preparing to unpack .../14-linux-modules-nvidia-515-5.15.0-43-generic_5.15.0-43.46+1_amd64.deb ...[/COLOR]
[COLOR=#000000]Unpacking linux-modules-nvidia-515-5.15.0-43-generic (5.15.0-43.46+1) ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package linux-modules-nvidia-515-generic-hwe-22.04.[/COLOR]
[COLOR=#000000]Preparing to unpack .../15-linux-modules-nvidia-515-generic-hwe-22.04_5.15.0-43.46+1_amd64.deb ...[/COLOR]
[COLOR=#000000]Unpacking linux-modules-nvidia-515-generic-hwe-22.04 (5.15.0-43.46+1) ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package mesa-vdpau-drivers:amd64.[/COLOR]
[COLOR=#000000]Preparing to unpack .../16-mesa-vdpau-drivers_22.0.5-0ubuntu0.1_amd64.deb ...[/COLOR]
[COLOR=#000000]Unpacking mesa-vdpau-drivers:amd64 (22.0.5-0ubuntu0.1) ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package nvidia-compute-utils-515.[/COLOR]
[COLOR=#000000]Preparing to unpack .../17-nvidia-compute-utils-515_515.65.01-0ubuntu0.22.04.1_amd64.deb ...[/COLOR]
[COLOR=#000000]Unpacking nvidia-compute-utils-515 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package nvidia-kernel-source-515.[/COLOR]
[COLOR=#000000]Preparing to unpack .../18-nvidia-kernel-source-515_515.65.01-0ubuntu0.22.04.1_amd64.deb ...[/COLOR]
[COLOR=#000000]Unpacking nvidia-kernel-source-515 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package nvidia-utils-515.[/COLOR]
[COLOR=#000000]Preparing to unpack .../19-nvidia-utils-515_515.65.01-0ubuntu0.22.04.1_amd64.deb ...[/COLOR]
[COLOR=#000000]Unpacking nvidia-utils-515 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package xserver-xorg-video-nvidia-515.[/COLOR]
[COLOR=#000000]Preparing to unpack .../20-xserver-xorg-video-nvidia-515_515.65.01-0ubuntu0.22.04.1_amd64.deb ...[/COLOR]
[COLOR=#000000]Unpacking xserver-xorg-video-nvidia-515 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package nvidia-driver-515.[/COLOR]
[COLOR=#000000]Preparing to unpack .../21-nvidia-driver-515_515.65.01-0ubuntu0.22.04.1_amd64.deb ...[/COLOR]
[COLOR=#000000]Unpacking nvidia-driver-515 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package nvidia-prime.[/COLOR]
[COLOR=#000000]Preparing to unpack .../22-nvidia-prime_0.8.17.1_all.deb ...[/COLOR]
[COLOR=#000000]Unpacking nvidia-prime (0.8.17.1) ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package pkg-config.[/COLOR]
[COLOR=#000000]Preparing to unpack .../23-pkg-config_0.29.2-1ubuntu3_amd64.deb ...[/COLOR]
[COLOR=#000000]Unpacking pkg-config (0.29.2-1ubuntu3) ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package screen-resolution-extra.[/COLOR]
[COLOR=#000000]Preparing to unpack .../24-screen-resolution-extra_0.18.2_all.deb ...[/COLOR]
[COLOR=#000000]Unpacking screen-resolution-extra (0.18.2) ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package nvidia-settings.[/COLOR]
[COLOR=#000000]Preparing to unpack .../25-nvidia-settings_510.47.03-0ubuntu1_amd64.deb ...[/COLOR]
[COLOR=#000000]Unpacking nvidia-settings (510.47.03-0ubuntu1) ...[/COLOR]
[COLOR=#000000]Selecting previously unselected package vdpau-driver-all:amd64.[/COLOR]
[COLOR=#000000]Preparing to unpack .../26-vdpau-driver-all_1.4-3build2_amd64.deb ...[/COLOR]
[COLOR=#000000]Unpacking vdpau-driver-all:amd64 (1.4-3build2) ...[/COLOR]
[COLOR=#000000]Setting up libnvidia-compute-515:amd64 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Setting up libnvidia-extra-515:amd64 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Setting up nvidia-kernel-common-515 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]update-initramfs is disabled since running on read-only media[/COLOR]
[COLOR=#000000]Created symlink /etc/systemd/system/systemd-hibernate.service.wants/nvidia-hibernate.service &#8594; /lib/systemd/system/nvidia-hibernate.service.[/COLOR]
[COLOR=#000000]Created symlink /etc/systemd/system/systemd-suspend.service.wants/nvidia-resume.service &#8594; /lib/systemd/system/nvidia-resume.service.[/COLOR]
[COLOR=#000000]Created symlink /etc/systemd/system/systemd-hibernate.service.wants/nvidia-resume.service &#8594; /lib/systemd/system/nvidia-resume.service.[/COLOR]
[COLOR=#000000]Created symlink /etc/systemd/system/systemd-suspend.service.wants/nvidia-suspend.service &#8594; /lib/systemd/system/nvidia-suspend.service.[/COLOR]
[COLOR=#000000]Setting up nvidia-prime (0.8.17.1) ...[/COLOR]
[COLOR=#000000]Setting up nvidia-kernel-source-515 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Setting up libxnvctrl0:amd64 (510.47.03-0ubuntu1) ...[/COLOR]
[COLOR=#000000]Setting up linux-objects-nvidia-515-5.15.0-43-generic (5.15.0-43.46+1) ...[/COLOR]
[COLOR=#000000]Setting up libnvidia-egl-wayland1:amd64 (1:1.1.9-1.1) ...[/COLOR]
[COLOR=#000000]Setting up libnvidia-decode-515:amd64 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Setting up pkg-config (0.29.2-1ubuntu3) ...[/COLOR]
[COLOR=#000000]Setting up screen-resolution-extra (0.18.2) ...[/COLOR]
[COLOR=#000000]Setting up libvdpau1:amd64 (1.4-3build2) ...[/COLOR]
[COLOR=#000000]Setting up nvidia-utils-515 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Setting up linux-signatures-nvidia-5.15.0-43-generic (5.15.0-43.46+1) ...[/COLOR]
[COLOR=#000000]Setting up nvidia-settings (510.47.03-0ubuntu1) ...[/COLOR]
[COLOR=#000000]Setting up libnvidia-common-515 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Setting up libnvidia-fbc1-515:amd64 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Setting up nvidia-compute-utils-515 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Warning: The home dir /nonexistent you specified can't be accessed: No such file or directory[/COLOR]
[COLOR=#000000]Adding system user `nvidia-persistenced' (UID 128) ...[/COLOR]
[COLOR=#000000]Adding new group `nvidia-persistenced' (GID 136) ...[/COLOR]
[COLOR=#000000]Adding new user `nvidia-persistenced' (UID 128) with group `nvidia-persistenced' ...[/COLOR]
[COLOR=#000000]Not creating home directory `/nonexistent'.[/COLOR]
[COLOR=#000000]Setting up libnvidia-cfg1-515:amd64 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Setting up mesa-vdpau-drivers:amd64 (22.0.5-0ubuntu0.1) ...[/COLOR]
[COLOR=#000000]Setting up linux-modules-nvidia-515-5.15.0-43-generic (5.15.0-43.46+1) ...[/COLOR]
[COLOR=#000000]linux-image-nvidia-5.15.0-43-generic: constructing .ko files[/COLOR]
[COLOR=#000000]nvidia-drm.ko: OK[/COLOR]
[COLOR=#000000]nvidia-modeset.ko: OK[/COLOR]
[COLOR=#000000]nvidia-peermem.ko: OK[/COLOR]
[COLOR=#000000]nvidia-uvm.ko: OK[/COLOR]
[COLOR=#000000]nvidia.ko: OK[/COLOR]
[COLOR=#000000]Setting up xserver-xorg-video-nvidia-515 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Setting up libnvidia-encode-515:amd64 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Setting up linux-modules-nvidia-515-generic-hwe-22.04 (5.15.0-43.46+1) ...[/COLOR]
[COLOR=#000000]Setting up vdpau-driver-all:amd64 (1.4-3build2) ...[/COLOR]
[COLOR=#000000]Setting up libnvidia-gl-515:amd64 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Setting up nvidia-driver-515 (515.65.01-0ubuntu0.22.04.1) ...[/COLOR]
[COLOR=#000000]Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...[/COLOR]
[COLOR=#000000]Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...[/COLOR]
[COLOR=#000000]Processing triggers for libc-bin (2.35-0ubuntu3.1) ...[/COLOR]
[COLOR=#000000]Processing triggers for man-db (2.10.2-1) ...[/COLOR]
[COLOR=#000000]Processing triggers for mailcap (3.70+nmu1ubuntu1) ...[/COLOR]
[COLOR=#000000]Processing triggers for linux-image-5.15.0-43-generic (5.15.0-43.46) ...[/COLOR]
[COLOR=#000000]/etc/kernel/postinst.d/dkms:[/COLOR]
[COLOR=#000000]* dkms: running auto installation service for kernel 5.15.0-43-generic[/COLOR]
[COLOR=#000000]...done.[/COLOR]
[COLOR=#000000]/etc/kernel/postinst.d/initramfs-tools:[/COLOR]
[COLOR=#000000]update-initramfs is disabled since running on read-only media[/COLOR]
[COLOR=#000000]Info: selecting the on-demand profile[/COLOR]
[COLOR=#000000]Writing /lib/modprobe.d/nvidia-runtimepm.conf[/COLOR]
[COLOR=#000000]Updating the initramfs. Please wait for the operation to complete:[/COLOR]
[COLOR=#000000]Donev[/COLOR]





```

---

### Post by MAFoElffen on 2023-10-22
I see the problem, BUT... I will not answer.

Sorry. I really get tired of reminding people to follow the Forums Policy of only posting commands and raw output within CODE Tags.

Please read: [Posting Guidelines]("https://ubuntuforums.org/showthread.php?t=2158945"): #3. (Also now in my "Signature" Block)

Then edit your last post to get it into a format that follows those guidelines. I do Linux Graphics Layer support, but I will stop with this support with this issue right here until you do that.

I will not, nor can I easily read what is there in that post. I will continue with this, after you edit that post accordingly. I will not ask the Moderators to format that for you, but to rather leave it for you to correct yourself... I personally know from having been a Moderator here in the past, that it burns up their time (when they have so many other things to manage and do), and that you really need to learn how to do that.

If you need instruction on how to do that (I and others here have re-posted those instructions many times, in many places on the Forum), please ask.

Thank you for your effort in correcting that.

---

### Post by oldfred on 2023-10-22
While I agree with MAFoElffen on use of code tags, we really do not need your entire log that says it is not doing anything.
Only the issues.

update-initramfs is disabled since running on read-only media
Did you run the install of nVidia on the live media or from recovery mode without enabling the system?

---

### Post by MAFoElffen on 2023-10-22
@oldfred --Correct. 

He did that from a Live Image Environment, not on a live installed persistent image. Not by chrooted into that image. So made no changes to the installed system at all.
```

update-initramfs is disabled since running on read-only media

```
After these
```

Get:1 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/restricted amd64 libnvidia-cfg1-515 amd64 515.65.01-0ubuntu0.22.04.1 [94.0 kB]

```
Which is getting the package from the CDROM repo of the Ubuntu 22.04.1 Installer Live USB offline in "Try" Mode...

The first clue was the system prompt of "ubuntu@ubuntu"... This is why he cannot find the Samba service on that system.

He needs to being doing thse things from one of the following 'first' to either: 

[LIST]
[*]Boot from Grub using nomodeset to get into a safe-graphics mode.
[*]Boot into init mode 3 to a text only console
[*]Get to the root prompt in a rescue mode menu
[*]Let the system boot the kernel to a black screen and toggle over to vtty session to log into the system or
[*]chroot into the installed system...
[/LIST]
 
So that the commands he does is "on" and "affects" the installed system he is trying to work on.

This is why, after 4 weeks, the commands we give him are not working and are not getting any expected results. I'm sorry, but that makes sense now. We can give him instructions for any of those. "Things" just need to be clearer between us and him, both ways.

---

### Post by d3vestator on 2023-10-23
first of all, ill apologize for the confusion and miscommunication that has been caused as well not ethically following the guidelines. i know how to implement code properly within the code boxes. if you need i will resubmit the code properly however i wont as of now

---

### Post by d3vestator on 2023-10-23
i start to understand the issue which is the fact that smba is not working that because im using a removeable boot os [ apologize for not emphasizing a couple times that i was using a removeable boot, as i only said it once]

---

### Post by MAFoElffen on 2023-10-23
Let be a little more clear in our instructions. Communication is the mutual understanding between both parties. It goes both ways. That is why we were also confused by your answers.

You do not have to resubmit anything. If yo go back to the post, select the "Edit Post" > Then select the "Go Advanced" button. That will bring up the Advanced Editor, with the extended toolbar. Select the text of the output to highlight it. > Select the "#" Icon to wrap the high lighted selected text witt CODE Tags. Then select "Save Edits" button to save the edits...

[hr][/hr]
Let's back up and try to resolve this.

On a cold boot(without any plugin external media plugged in), do you get a Grub2 menu? If not does it just continue to the Graphical Boot Menu where you log in? Or does it just go to a black screen from there?

Tell us what it does...

---

### Post by d3vestator on 2023-10-23
on a cold boot, it boots up the grub and without interfering with it, it automatically goes to the ubuntu os, where it will try to startup but then will start spit error commands like
[failed] NVidia persistence storage
and then it will be a blacked screen for a bit with a flashing white underline typer, and then it will say
[failed] failed to start Samba NMB Daemon. it will sit there after that

---

### Post by #&amp;thj^% on 2023-10-23
There is other things going on then, and I still see no ties with samba and nVidia ie:
```
systemctl status nvidia-persistenced.service
&#9679; nvidia-persistenced.service - NVIDIA Persistence Daemon
     Loaded: loaded (/lib/systemd/system/nvidia-persistenced.service; static)
     Active: active (running) since Mon 2023-10-23 14:42:46 MDT; 2min 5s ago
    Process: 51325 ExecStart=/usr/bin/nvidia-persistenced --user nvidia-persistenced --no-persistence-mode --verbose (code=exited, status=0/SUCCESS)
   Main PID: 51327 (nvidia-persiste)
      Tasks: 1 (limit: 18881)
     Memory: 776.0K
        CPU: 6ms
     CGroup: /system.slice/nvidia-persistenced.service
             &#9492;&#9472;51327 /usr/bin/nvidia-persistenced --user nvidia-persistenced --no-persistence-mode --verbose

Oct 23 14:42:46 lvm-linux systemd[1]: Starting nvidia-persistenced.service - NVIDIA Persistence Daemon...
Oct 23 14:42:46 lvm-linux nvidia-persistenced[51327]: Verbose syslog connection opened
Oct 23 14:42:46 lvm-linux nvidia-persistenced[51327]: Now running with user ID 126 and group ID 139
Oct 23 14:42:46 lvm-linux nvidia-persistenced[51327]: Started (51327)
Oct 23 14:42:46 lvm-linux nvidia-persistenced[51327]: device 0000:01:00.0 - registered
Oct 23 14:42:46 lvm-linux nvidia-persistenced[51327]: Local RPC services initialized
Oct 23 14:42:46 lvm-linux systemd[1]: Started nvidia-persistenced.service - NVIDIA Persistence Daemon.

```
And samba
```
systemctl status smbd
&#9679; smbd.service - Samba SMB Daemon
     Loaded: loaded (/lib/systemd/system/smbd.service; enabled; preset: enabled)
     Active: active (running) since Mon 2023-10-23 08:13:51 MDT; 6h ago
       Docs: man:smbd(8)
             man:samba(7)
             man:smb.conf(5)
    Process: 3814 ExecCondition=/usr/share/samba/is-configured smb (code=exited>
    Process: 3816 ExecStartPre=/usr/share/samba/update-apparmor-samba-profile (>
   Main PID: 3820 (smbd)
     Status: "smbd: ready to serve connections..."
      Tasks: 3 (limit: 18881)
     Memory: 12.2M
        CPU: 122ms
     CGroup: /system.slice/smbd.service
             &#9500;&#9472;3820 /usr/sbin/smbd --foreground --no-process-group
             &#9500;&#9472;3822 "smbd: notifyd" .
             &#9492;&#9472;3823 "smbd: cleanupd "

Oct 23 08:13:51 lvm-linux systemd[1]: Starting smbd.service - Samba SMB Daemon.>
Oct 23 08:13:51 lvm-linux smbd[3820]: [2023/10/23 08:13:51.756172,  0] ../../so>
Oct 23 08:13:51 lvm-linux smbd[3820]:   smbd version 4.18.6-Ubuntu started.
Oct 23 08:13:51 lvm-linux smbd[3820]:   Copyright Andrew Tridgell and the Samba>
Oct 23 08:13:51 lvm-linux systemd[1]: Started smbd.service - Samba SMB Daemon.

```
To help us to help you faster please run the system-info script fond in my signature and add the flag "--details " to the end of that script.
Post the link back here in your thread so we can see whats what

---

### Post by MAFoElffen on 2023-10-23
@1fallen -- His pastebin link for his 'system-info script" was in Post #1 (it's still active there): [https://paste.ubuntu.com/p/4mpybdHFqj/](https://paste.ubuntu.com/p/4mpybdHFqj/)

Line #260:
> product: GA107M [GeForce RTX 3050 Mobile]

@D3vastator --
At the Grub2 menu, press the <E> key to get into an edit mode. > <Arrow-Down> to the line that starts with the word "linux". > <Arrow-Right> to the words "quiet splash". > Replace the word with "--- 3". > Pres the keys <Cntrl><X> to boot...

It will boot without graphics trying to start, to a console login prompt. > Log in with your UserName and Password.

Enter the following commands
```

sudo apt update
sudo apt remove --purge nvidia-*
sudo apt install nvidia-driver-535 nvidia-dkms-535
sudo reboot

```
Test it and tell us what it does then...

---

### Post by d3vestator on 2023-10-23
so i switched 
Linux /???????????????/?????????/??????/??/ ro  quiet splash $vt_handoff
with
Linux /???????????????/?????????/??????/??/ ro  ---3 $vt_handoff

is this correct? 
want to make sure this is correct before i say, that i cant get in

---

### Post by MAFoElffen on 2023-10-23
> **d3vestator said:**
> so i switched 
Linux /???????????????/?????????/??????/??/ ro  quiet splash $vt_handoff
with
Linux /???????????????/?????????/??????/??/ ro  ---3 $vt_handoff

is this correct? 
want to make sure this is correct before i say, that i cant get in
Yes. You, but delete $vt_handoff also. Sorry. Forgot that might be there.

---

### Post by d3vestator on 2023-10-23
it still doesent work, it willl go through the startup commands. on the first black screeen, the nvidia persistence storage will fail, and then on the next screen the Samba NMB Dameon will fail, and these the line of commands will display after

```


[failed] failed to start samba nmb daemon
see Systemctl status nmbd.service for details
    starting Samba SMB daemon
[OK] started Samba SMB daemon
[OK] reached targer muti-user system
[OK] reached target graphical interface
 starting record runlevel change in UTMP
[OK] finished record runlevel change in UTMP



```

---

### Post by MAFoElffen on 2023-10-23
Error messages about NVidia persistent storage failures are usually from a mismatch of Cuda toolset versions causing corruption. Do you need and use Cuda? Even if you do, the way to fix that would be to uninstall them and reinstall. If not, the fix is to still remove them.
```

sudo apt remove --purge cuda-*

```
If you need to reinstall, the timing of that is after you have working NVidia drivers. So not yet.

What do these say?
```

sudo ubuntu-drivers list
sudo systemctl status nmbd.service --no-pager
journalctl -b2 --unit=nmbd.service

```

---

### Post by #&amp;thj^% on 2023-10-24
> **MAFoElffen said:**
> @1fallen -- His pastebin link for his 'system-info script" was in Post #1 (it's still active there): [https://paste.ubuntu.com/p/4mpybdHFqj/](https://paste.ubuntu.com/p/4mpybdHFqj/)


So it is...:)

> **MAFoElffen said:**
> Error messages about NVidia persistent storage failures are usually from a mismatch of Cuda toolset versions causing corruption. Do you need and use Cuda? Even if you do, the way to fix that would be to uninstall them and reinstall. If not, the fix is to still remove them.

+1
I had seen where the poster had some fun with various drivers, which is OK, but purge the old before installing new or different drivers always.
And Now back to you. ;)

---

### Post by d3vestator on 2023-10-24
this was done on a removeable usb which would make sense why most the commands woulubuntu@ubuntu:~$ sudo ubuntu-drivers list



```

ubuntu@ubuntu:~$ sudo ubuntu-drivers list
nvidia-driver-470, (kernel modules provided by linux-modules-nvidia-470-generic-hwe-22.04)
nvidia-driver-510, (kernel modules provided by linux-modules-nvidia-510-generic-hwe-22.04)
nvidia-driver-515, (kernel modules provided by linux-modules-nvidia-515-generic-hwe-22.04)
ubuntu@ubuntu:~$ sudo systemctl status nmbd.service --no-pager
Unit nmbd.service could not be found.
ubuntu@ubuntu:~$ journalctl -b2 --unit=nmbd.service
Data from the specified boot (+2) is not available: No such boot ID in journal


```

---

### Post by MAFoElffen on 2023-10-24
You need to run those commands from the installed system itself. We want to see why the service failed, and what errors are in the journal when you try to run it on its own. That, and any changes you make booted from LiveUSB will not directly have any effect on the installed system, so will not repair it... Unless you were chrooted into that installed system, which you are not.

You need to think about where things are that you need information from, and how to make changes on your computer, where those changes matter. Otherwise you are just spinning yourself in circles, right?

You know how to edit the grub menu now to do that. 

To try to boot into a 'safe graphics" mode, now you can try to do, instead of adding "-- 3", instead add "nomodeset" and boot. That will try to use the neuveau driver.

---

### Post by d3vestator on 2023-10-24
still does not work

---

### Post by MAFoElffen on 2023-10-24
> **d3vestator said:**
> still does not work
*"Just the facts Ma'am..."*
Did you "mean" that it would not boot into a "safe graphics" mode? I'm not surprised. Only because the neuveau driver had been broken for kernels 6.0 through 6.4 or so... So you go back to using "--- 3" as a boot parameter to fix this right?

*"Show me the data."* Where's the data? Please show me the output of the commands I asked for, "from" your installed system.

---

### Post by MAFoElffen on 2023-10-24
I've been expanding my search on answers for you... from a "console"
```

sudo nano /etc/default/grub

```
At the GRUB_CMDLINE_LINUX_DEFAULT= line, edit it to this
```

GRUB_CMDLINE_LINUX_DEFAULT="--- splash radeon.modeset=1 amd_gpu.modeset=1"

```
Save and exit the editor...
```

sudo update-grub
sudo apt-update
sudo apt remove --purge nvidia* cuda*
sudo apt install nvidia-driver-470

```
NVidia, if i do a driver search say that the card is an RTX3050, which it says that driver 535 supports. There are many support problems filed for this GPU in laptops bundled with an AMD Ryzen 7 5800H, with an iGPU AMD Cezanne... Therefore seeing what happens if I turn that off.

But if I search on GA107M, which is what Linux sees the NVidia device as, whenI do a search at NVidia, it only goes directly to driver 460...

That's my reasoning behind this "try". Filter out any distractions, and try something they says worked, and is still available.

---

### Post by d3vestator on 2023-10-24
lets back up here. i am trying to do what you said. going back to the conversation a couple hours ago, you said goto the gnu grub, click "E" to edit the grub in which you said, change the line where it says Linux ????/ quiet splash to    "--3", correct? after booting it what is suppose to pop up?. Is it a graphical interface?, or is it some kind of text interface?. I literally edit the grub, click f10 and it will go through a bunch of startup commands that i cant control and it just stays there, and never changes.  if you need a picture of what i am talking about, i can send one

you tell me to execute commands ,however where will they be executed, because the startup commands do not disappear after booting after grub.

i am very new Linux, and i have never dealt with any of this before, and the termonology like "neuveau" or "---3" i never heard of, so im trying to understand what is suppose to happen. Want to be very clear with you

---

### Post by MAFoElffen on 2023-10-24
> **d3vestator said:**
> lets back up here. i am trying to do what you said. going back to the conversation a couple hours ago, you said goto the gnu grub, click "E" to edit the grub in which you said, change the line where it says Linux ????/ quiet splash to    "--3", correct? after booting it what is suppose to pop up?. Is it a graphical interface?, or is it some kind of text interface?. 

A text console interface should have appeared, asking you to log in with your credentials. That would log in on your installed system without the graphics (that is having issues), where you do commands to get answers on what is going on with your installed system and to make changes to that installed system.
> **d3vestator said:**
> I literally edit the grub, click f10 and it will go through a bunch of startup commands that i cant control and it just stays there, and never changes.  if you need a picture of what i am talking about, i can send oneYes. Add the picture as an attachment to a post.
> **d3vestator said:**
> you tell me to execute commands ,however where will they be executed, because the startup commands do not disappear after booting after grub.What do you mean, when you say the commands do not go away?
> **d3vestator said:**
> i am very new Linux, and i have never dealt with any of this before, and the termonology like "neuveau" or "---3" i never heard of, so im trying to understand what is suppose to happen. Want to be very clear with you
And I am trying to explain things to you and be clear with you. Some things are going to be very specific, especially when we are asking you to enter a specific command. This does not seem to be working for you. Trying to think of other ways to take any translation problems out of this equation. Some things just can't be changed (like specific commands entered in the right place) as an interpretation of.

Let's put it another way. I have been very patient. I am not being paid for this. I am a volunteer, just like everyone else here. I don't "have" to help you. I chose to out of wanting to help you. If you do not want help with this, that is your choice. I told you that if there was something that you did not understand, or had a question about, to stop right there before doing anything, and ask us. That is much better than frustrating yourself with things going wrong, right?

I am sort of known here for having a lot of patience with people, and going "beyond the normal" to help someone in need. 

My last post did change gears, because things were not working out for you. I felt we needed to try something different.

I know you are not comfortable typing commands we post here... I have some particular "skills." If you want, I can post a script for you, where you can boot from an Ubuntu Installer LiveCD, to start a browser and graphical terminal session, being booted from that Live Environment, copy and paste that script into a file, and make it executable... The purpose of that script would to chroot into your installed system in that graphical terminal session. Having that graphical terminal session open like that, and having a browser open to this thread, then you could cut-and-paste commands into that, and be able to cut-and-paste whatever output back into a post for here. Understand that doing that in the Live Environment, would mean "that script" would disappear when it shut down or you rebooted... Every time you shutdown or rebooted, you would have to repeat that process.

But being chrooted into your installed system would be like being booted on your system, but you could use the graphics of that Live Environment, to at least make a few things easier on you. No offense intended, but I don't think you would understand how to do that on your own, from just the commands to get there.

Yes, you are learning new things and this is technical. Would something like that be easier for you? 

If not, I honestly do not know at the moment what else I can do to make things easier for you.

---

### Post by d3vestator on 2023-10-24
alright so i got back into my ubuntu machine i did the commands you told me to do, it turns that when editing the Linux line in grub it was "3" after the _$vt_handoff piece of line that was able to get me into my machine.
however i still know that there things wrong. i still get bunch of startup commands and whenever i reboot the machine the smba service is still in the failed position[  might because i have not enabled it, which im unsure of the command to enable it]

i tried to enable samma with 

```

sudo systemctl enable samba
password for ????
Failed to enable unit:Unit file samba.service does not exist


```

Note: my laptop touchpad doesn't work

---

### Post by MAFoElffen on 2023-10-24
While you are into your system... Let's temporarily edit your grub config file so that you do not need to do that ever time you boot...
```

sudo cp /etc/default/grub /etc/default/grub.bak
sudo nano /etc/default/grub

```
That will open the configuration file for Grub... Please make these changes
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=[COLOR=#ff0000]menu[/COLOR]
GRUB_TIMEOUT=[COLOR=#ff0000]5[/COLOR]
[COLOR=#ff0000]GRUB_RECORDFAIL_TIMEOUT=5
[/COLOR]GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="[COLOR=#ff0000]--- 3 --verbose debug drm.debug=0xe plymouth:debug[/COLOR]"
GRUB_CMDLINE_LINUX="[COLOR=#ff0000]radeon.cik_support=1 amdgpu.cik_support=1 amdgpu.dc=1[/COLOR]"
# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console
[COLOR=#ff0000]GRUB_TERMINAL=console[/COLOR]
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=1920x1080x32
GRUB_GFX_MODE=1280x1024x32
#GRUB_GFXMODE=auto
# Set to true if you want to disable OS_Prober, false to turn on 
GRUB_DISABLE_OS_PROBER=false
# UncommentE if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true
# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"
# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```
To save, press <Cntrl><O>, the <Enter>. To close <Cntr><X>.

To pick up those changes, then do
```

sudo update-grub

```
The next time you reboot, with those option, there is going to be a lot of messages. Please try to pay attention to them whizzing by, for any that stand out.

Next do this.
```

sudo apt update
sudo apt remove nvidia* cuda*
sudo apt install nvidia-driver-470
sudo reboot

```
It should reboot, but go to a text console. We just are looking to see if that "nvidia persistence" error has gone away... I don't really care about anything else at this point... Lets see where that gets us, then we'll continue...

---

### Post by d3vestator on 2023-10-25
when i edited the /etc/defualt/grub and changed some of the lines,why does it bring me to a tty1 line console instead of the actual home ubuntu page?

---

### Post by MAFoElffen on 2023-10-25
Because you still need to check and fix some things... So a step at a time.

Your title just says NVidia drivers... But you keep saying it has several problems. Some of those tied in with NVidia. Some not.

---

### Post by d3vestator on 2023-10-25
i was asking, because before i changed it was working fine and booting to the os home screen, and i also dont noticed a [failed] NVidia persistence error


```

GRUB_CMDLINE_LINUX_DEFAULT TO [FONT=Ubuntu Mono, monospace][COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="--- splash radeon.modeset=1 amd_gpu.modeset=1"[ changing this to [/COLOR][/FONT][COLOR=#ff0000][FONT=&quot]--- 3 --verbose debug drm.debug=0xe plymouth:debug[/FONT][/COLOR][COLOR=#000000][FONT=&quot]" is what causes it to boot to tty1 console, not the homescreen][/FONT][/COLOR][FONT=Ubuntu Mono, monospace][COLOR=#000000]


```[/COLOR][/FONT]

---

### Post by MAFoElffen on 2023-10-25
Yes. Exactly what we wanted at that time... Now...
```

sudo nano /etc/default/grub

```
Change this line
```

GRUB_CMDLINE_LINUX_DEFAULT="--- 3 --verbose debug drm.debug=0xe plymouth:debug"

```
To this
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```
Leave this line as this
```

GRUB_CMDLINE_LINUX="radeon.cik_support=1 amdgpu.cik_support=1 amdgpu.dc=1"

```
change this line
```

GRUB_TERMINAL=console

```
To this
```

#GRUB_TERMINAL=console

```
Save and exit. Then do this
```

sudo update-grub
sudo reboot

```

---

### Post by d3vestator on 2023-10-25
all startup commands have disappeared except for

```

/dev/nvmeon1p5 clean, 281039/14942208 files, 6587656/59756800 blocks


```

---

### Post by #&amp;thj^% on 2023-10-25
That would be expected after these changes you've now made,
And that's normal to see that "/dev/nvmeon1p5 clean, 281039/14942208 files, 6587656/59756800 blocks"

---

### Post by d3vestator on 2023-10-25
well then, the only things that dont work is my touchpad and wifi doesnt show

---

### Post by MAFoElffen on 2023-10-25
Now the only thing left to figure out is why your samba server is not starting right?
```

apt list samba* --installed

```
Since the daemons for Samba vary, based on how it was installed and where you got the package from, we will just expand a command to a "multiple choice" question:
```

for unit in 'smbd.service nmbd.service smb.service'; do sudo systemctl status $unit --no-pager; done

```

---

### Post by d3vestator on 2023-10-25
my smbd is running, i checked the status. it fixed itself when i reconfigured the grub commands.

thanks for your help @MAFoElffen and all the others, appreciate the patience and troubleshooting tips on how to fix the command.

just going to have to figure out why my WIFI doesn't show up as well as why my touchpad doesn't work, but i'll see if i can figure it out before i create another thread

what was the main issue. was it the NVidia 535 drivers?

---

### Post by MAFoElffen on 2023-10-25
Yes... I think NVidia themselves are a little misleading about which driver really works for your GPU. Something was also mismatched with a corrupted Cuda tools installation, which you do not even use.

That, and for some reason your machine is really "picky" about the version of the CPU's internal iGPU (amg_gpu) being turned off before the NVidia drivers load. That seems to be a common problem with that specific model of CPU and that same specific NVidia GPU. The perfect storm kind of match up. Not just for Ubuntu or Debian branch, but for all Linux itself. 

The reasons you started this "thread" have been resolved. I am happy that they got fixed for you. 

Please go back to the first page of this thread, use the "Thread Tools" and mark your thread as "Solved". That will help others find what worked for you.

As for your Wifi and TouchPad problems, I would start a new thread for each of them. That way they can be dealt with as separate problems (which they are). To help members help you, please repost the link to your 'system-info' report (In Post #1 of this thread) in your first post of each of them, so they know what they are recommending solutions for. That information will help them greatly.

---

### Post by d3vestator on 2023-10-25
before i change the thread, i assume its fine that the NVidia drivers stay set to nouveau, because i have no internet to switch to 470

---

### Post by MAFoElffen on 2023-10-25
You can leave it open... 

Get your Wifi working in the other thread, 

Then you have the commands (here) to install that driver once you get your Wifi working... Then return here to report how that worked for you... 

Then close it.

---

### Post by MAFoElffen on 2023-10-30
Now that your wifi is working:
```

sudo apt update
sudo apt remove nvidia*
sudo apt install nvidia-driver-470
sudo reboot

```

---

