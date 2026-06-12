---
title: "Anydesk install in 20.04 64bit on a Pi 4"
date: 2020-06-05
forum: Installation &amp; Upgrades
---

### Post by netwarrior2 on 2020-06-05
I am a new user of Ubuntu (less than 24hrs in) and failed to install my first app on this OS. After some effort i have managed to install a 64bit OS on my Raspberry Pi 4 4GB using a Ubuntu Server 20.04 for Raspberry Pi image and installed lubuntu (sudo apt-get install lubuntu-desktop).
In the OS, Settings -> About

Processor: blank
Graphics: llvmpipe (LLVM 9.0.1, 128 bits)
Disk Capacity: Unknown
OS Name: Ubuntu 20.04 LTS
OS Type: 64-bit

Which i find confusing because i think it is an ARM processor but requires DEB install files right? So i head over to Anydesk but the Debian/Ubuntu/Mint (64bit)* file gives the error:
Error: Wrong architecture 'amd64'

So i head to the Anydesk for Raspberry Pi download** this time but get the error:
Error: Wrong architecture 'armhf'

I feel silly since there is something obvious i am missing. I just don't know what. I will need to install many apps and I'm stuck at my first hurdle. Any help would be appreciated.

*  [URL="https://anydesk.com/en/downloads/linux"]https://anydesk.com/en/downloads/linux
[/URL]** [https://anydesk.com/en/downloads/raspberry-pi](https://anydesk.com/en/downloads/raspberry-pi)

[[ATTACH=CONFIG]286101[/ATTACH][ATTACH=CONFIG]286102[/ATTACH][ATTACH=CONFIG]286103[/ATTACH]]("https://anydesk.com/en/downloads/raspberry-pi")

---

### Post by bijayalaxmi1808 on 2020-06-05
armhf arm hard-float is the name given to the Debian port for ARM 32-bit versions (someone please correct me if I am wrong).
At least this [link]("https://www.debian.org/ports/arm/") clearly mentions the same:
> The newer [ARM hard-float]("https://wiki.debian.org/ArmHardFloatPort") (armhf) port supports newer, more powerful 32-bit devices using version 7 of the ARM architecture specification.

If this is true, you can try a 32-bit deb file and see if it installs.

I am not sure, but, should there be an ARM variant of the binary file?

---

### Post by CelticWarrior on 2020-06-05
> **bijayalaxmi1808 said:**
> 
I am not sure, but, should there be an ARM variant of the binary file?

Yes, it should and that's the problem. 'i384' or 'amd64' packages cannot be installed in ARM devices.

---

### Post by netwarrior2 on 2020-06-05
Thanks bijayalaxmi1808 and CelticWarrior.

> **CelticWarrior said:**
> Yes, it should and that's the problem. 'i384' or 'amd64' packages cannot be installed in ARM devices.

Yep, i found the i384 package for 32bit deb but that failed too. So if I'm reading this right, i need an arm64 package (64-bit ARM) for my 64bit quad-core ARM Cortex-A72 processor.
I can only find amd64, armhf, and i386. 

Hmm....anyone know how to get the arm64 file?

---

### Post by deadflowr on 2020-06-05
Have you tried adding the armhf architecture to dpkg?
```
sudo dpkg --add-architecture armhf
```

---

### Post by netwarrior2 on 2020-06-05
> **deadflowr said:**
> Have you tried adding the armhf architecture to dpkg?
```
sudo dpkg --add-architecture armhf
```

Thanks deadflowr. So this is what i did:

```
wget -qO - https://keys.anydesk.com/repos/DEB-GPG-KEY | apt-key add -
echo "deb http://deb.anydesk.com/ all main" > /etc/apt/sources.list.d/anydesk-stable.list
apt update
sudo dpkg --add-architecture armhf
apt install anydesk
```

Which seemed to go ok. Now it appears in my Show Applications (see pic) but nothing happens when i click on it. Did i break it? I am a Windows user after all :(
[ATTACH=CONFIG]286108[/ATTACH][ATTACH=CONFIG]286109[/ATTACH]

---

### Post by netwarrior2 on 2020-06-07
Ok, I'm still looking into this issue and I'll reach out to Anydesk and others to solve it. But in the mean time, is there a workaround that can remote access my lubuntu system remotely using my android tablet and occasionally my Win10 PC? I need to be able to see the screen while the lubuntu system is headless.

---

### Post by grahammechanical on 2020-06-07
Are you trying to install Anydesk on the raspberry PI 4? I am guessing that if you want the Raspberry Pi version of Anydesk on the Raspberry Pi then you would need to be running Raspbian OS on the Raspberry PI.

The Debian version of Anydesk might be meant for Debian and Debian based OS running on an AMD64 compatible CPU. Which excludes the Raspberry PI with its ARM CPU. The Ubuntu server for the Raspberry PI is modified to run on the ARM cortex CPU. That is why deb files such as Lubuntu desktop can be installed. I cannot say for sure but Ubuntu server for Raspberry PI may have its own set of Ubuntu repositories with deb files modified not to reject being installed on an ARM cortex CPU.

This might help to over come the problem. It is a PPA and it is uptodate for 20.04

[https://launchpad.net/~rpi-distro/+archive/ubuntu/ppa](https://launchpad.net/~rpi-distro/+archive/ubuntu/ppa)

Regards..

---

### Post by netwarrior2 on 2020-06-07
Ok grahammechanical. Not sure what that means but i gave it a go:


```
sudo add-apt-repository ppa:rpi-distro/ppa
sudo apt-get update
```

It gave an error. Something about not having a Release file so its not safe and therefore disabled by default (see pic). I'm guessing that's not good. 

It feels like I'm forcing a red square block though a yellow circular hole while thinking: why doesn't this work!


[ATTACH=CONFIG]286149[/ATTACH]

---

### Post by deadflowr on 2020-06-08
The ppa has no packages.
Probably best to disable it.

You can try running the application's command to launch from a terminal
that should tell something about what's happening.
For anydesk that is the command
```
anydesk
```
or if needed you can run the full file path name
```
/usr/bin/anydesk
```

---

### Post by netwarrior2 on 2020-06-08
Ok. I removed the ppa

```
sudo add-apt-repository --remove ppa:rpi-distro/ppa
```

then launched anydesk via terminal.

```
anydesk
```

```
/usr/bin/anydesk
```

In both cases it said: 
[B]error while loading shared libraries: libpolkit-gobject-1.so.0: cannot open shared object file: No such file or directory

[ATTACH=CONFIG]286154[/ATTACH][/B]

---

### Post by deadflowr on 2020-06-08
Try installing the libpolkit-gobject package
```
sudo apt-get install libpolkit-gobject-1-0
```

---

### Post by netwarrior2 on 2020-06-08
I did a search and found this:
[https://stackoverflow.com/questions/59585500/ubuntu-on-raspberry-pi-4-anydesk-error-while-loading-shared-libraries-libpolk](https://stackoverflow.com/questions/59585500/ubuntu-on-raspberry-pi-4-anydesk-error-while-loading-shared-libraries-libpolk)

So i did this:
```
apt-get install libpolkit-gobject-1.so.0
```

but got this for my trouble:

[B]E: Unable to locate package libpolkit-gobject-1.so.0
E: Couldn't find any package by glob 'libpolkit-gobject-1.so.0'
E: Couldn't find any package by regex 'libpolkit-gobject-1.so.0'[/B]

I thought i was onto something there for a moment :(

[ATTACH=CONFIG]286155[/ATTACH]

---

### Post by netwarrior2 on 2020-06-08
> **deadflowr said:**
> Try installing the libpolkit-gobject package
```
sudo apt-get install libpolkit-gobject-1-0
```

Ok, tired this too and it said:

**ibpolkit-gobject-1-0 is already the newest version (0.105-26ubuntu1).**

Still no joy.

[ATTACH=CONFIG]286156[/ATTACH]

---

### Post by deadflowr on 2020-06-08
Might be it needs the armhf version.
Try
```
sudo apt-get install libpolkit-gobject-1-0:armhf
```

---

### Post by ActionParsnip on 2020-06-08
To access the files on your pi from your tablet etc you can install openssh-server and you will get an SFTP service. You can connect to this from Windows and tablets and use your Raspberry Pi credentials to authenticate. You can also use SSH (like PuTTY) to connect to the server and manipulate the OS in CLI (Software updates are dead handy here).

---

### Post by netwarrior2 on 2020-06-08
> **deadflowr said:**
> Might be it needs the armhf version.
Try
```
sudo apt-get install libpolkit-gobject-1-0:armhf
```

Ok, this time it did something:

The following NEW packages will be installed:
[B]  libpolkit-gobject-1-0:armhf
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
[/B]
But still failed to open:
```
anydesk
```

as it gave this new error:
**anydesk: error while loading shared libraries: libbcm_host.so: cannot open shared object file: No such file or directory**

[ATTACH=CONFIG]286157[/ATTACH]

---

### Post by ActionParsnip on 2020-06-08
[https://raspberrypi.stackexchange.com/questions/78719/missing-libbcm-host-so-when-running-chromium-browser](https://raspberrypi.stackexchange.com/questions/78719/missing-libbcm-host-so-when-running-chromium-browser)
[https://github.com/bamarni/pi64/issues/26](https://github.com/bamarni/pi64/issues/26)

---

### Post by netwarrior2 on 2020-06-08
> **ActionParsnip said:**
> [https://raspberrypi.stackexchange.com/questions/78719/missing-libbcm-host-so-when-running-chromium-browser](https://raspberrypi.stackexchange.com/questions/78719/missing-libbcm-host-so-when-running-chromium-browser)
[https://github.com/bamarni/pi64/issues/26](https://github.com/bamarni/pi64/issues/26)

after reading these i tired this but it didn't work.
```
sudo apt-get update
sudo apt-get install --reinstall libraspberrypi0 libraspberrypi-dev libraspberrypi-doc libraspberrypi-bin
```


[ATTACH=CONFIG]286163[/ATTACH]

---

### Post by netwarrior2 on 2020-06-08
and found my way to this page:
[https://github.com/raspberrypi/firmware/releases](https://github.com/raspberrypi/firmware/releases)

Since my Opt/vc folder is empty i  tried to get Ark to extract the Opt/vc folder from the archive  (firmware-1.20200601-arm64.tar.gz) but i don't have sufficient  permissions.

[ATTACH=CONFIG]286164[/ATTACH]

---

### Post by kabir18 on 2020-11-25
Yepp did everything above, but got this error:
anydesk: error while loading shared libraries: libpolkit-gobject-1.so.0: cannot open shared object file: No such file or directory

tried to check everywhere, even did necessary installs. Put files on desired locations, but same error everytime.
Files:

/usr/lib/aarch64-linux-gnu/libpolkit-gobject-1.so.0
/usr/lib/aarch64-linux-gnu/libpolkit-gobject-1.so.0.0.0
/usr/share/doc/libpolkit-gobject-1-0/changelog.Debian.gz
/usr/share/doc/libpolkit-gobject-1-0/copyright

---

### Post by wildmanne39 on 2020-11-25
Hello and welcome to the forum kabir18, please start your own thread instead of posting in someone else's so you can get the individual help you need.

Thanks

---

### Post by ActionParsnip on 2020-11-25
Seems the PPA is dead
[https://launchpad.net/~rpi-distro/+archive/ubuntu/ppa](https://launchpad.net/~rpi-distro/+archive/ubuntu/ppa)

---

