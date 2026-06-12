---
title: "X server problems installing NVIDIA 8600 gs"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by Arvidgp on 2008-04-27
Hi
I'm having some problems installing my graphic card, NVIDIA 8600M GS, i get the following error message:

ERROR: You appear to be running an X server; please exit X before installing. For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com)

1) I don't know what the "X Server" is, and how can i stop this? (Or is it called "x server" because ubuntu was installed in windows?) 
2) Do you have any clue of how to solve my problem?

Arvid

---

### Post by James- on 2008-04-27
X server is basically what gives linux the visual aspect. It's the application that is used by all desktop environments(i.e. Gnome, KDE, E17, blackbox,etc) 

to stop xserver press ctrl+alt+F1

login.. and:

If you are using Kubuntu:
```
sudo /etc/init.d/kdm stop
```

if you are using Ubuntu:
```
sudo /etc/init.d/gdm stop
```

as for fixing it try:
```
sudo dpkg-reconfigure xserver-xorg
```

it will reset all your visual interface

---

### Post by NickPheas on 2008-04-27
I am having similar problems, but I've got a bit further.

If I understand things properly X-Server is the GUI, or perhaps a core component of the GUI. There's something here on how to shut the X-Server down

[http://ubuntuforums.org/archive/index.php/t-309787.html](http://ubuntuforums.org/archive/index.php/t-309787.html)

When I ran the install after doing this it said that it would need to generate something for my particular kernel, which it wouldn't do at first because I didn't have any libc-headers, whatever they might be.

Another page says that 

sudo apt-get install build-essential

will install these things, and it seems to do so.

I now try to install the drivers again. Lots of messages flashing past too quick to read. Asks be if I want X configures to use this.

When I reboot I get a red box in the middle of the screen saying 'Out of Range'. I can get to a command line only environment, but don't have a clue what's gone wrong to be able to fix from there.

Any ideas?

---

### Post by James- on 2008-04-27
You can install the drivers with the "restricted drivers"

first restore your visual with:
```
sudo dpkg-reconfigure xserver-xorg
```

and then you can install the drivers with by fallowing this little guide:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NVidia_Driver](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NVidia_Driver)

basically type:
```
sudo apt-get install linux-restricted-modules-generic
```

then you will have a new menu item under 
System > Administration > Restricted Drivers Manager

check the checkbox in near the nvidia driver and it's all set(need reboot to take effect ctrl+alt+bksp usually works)

---

### Post by Exakun on 2008-04-27
I followed all of the instructions from Nvidia's website and the installation went just fine. However, every time I boot it tells me (as it did before I installed the driver) that it could not identify my video card (an 8800 GTS) and proceeds to load in low-graphic mode. I already have the restricted modules manager installed but when I run it it tells me I have no Nvidia hardware. The link you posted just reiterates what has already been said, so it was no help. This is getting extremely frustrating; the card works phenomenally under Windows, so obviously it's recognized by my system and working properly. I'm tired of straining my eyes on this computer to read through non-working tutorials. Any help would be very appreciated.

---

### Post by NickPheas on 2008-04-27
OK, that's got me a GUI again, though I don't see a 
System>Administration>Restricted...

There is a System>Administration>Hardware Drivers item, which gives me the option of turning on non-OGL drivers for NVIDIA Accelerated Graphics Drivers (latest cards)

If I do so the screen is fuzzier than without, so I'm going it without. In either mode the best display I'm getting is 640*480, which is worse than the initial install gave me.

---

### Post by Arvidgp on 2008-04-27
Thanks a lot for the help James-, i followed your steps, and now it's working smooth :)

---

### Post by Exakun on 2008-05-17
I just checked my PMs and someone asked me three days ago if I ever fixed my problem. I did, actually, and just less than an hour ago. Here's how I did it (note: my system is running Ubuntu 8.04 i386 with an nvidia 8800 GTS 512).

I uninstalled the nvidia driver I downloaded from the nvidia website by running:```
sudo sh NVIDIA-Linux-x86-169.12-pkg1.run --uninstall
```Note: substitute the above for the installer you downloaded.
Then, I installed envy using:```
sudo apt-get install envyng-core
```
Once installed, I ran envy as follows (using -t uses the text mode interface).```
envyng -t
<selected option 1: install NVIDIA driver>
```
...and let it do it's thing. It then asked me to reboot, which I did, and now everything seems to be working properly. Hope this helps everyone.

---

