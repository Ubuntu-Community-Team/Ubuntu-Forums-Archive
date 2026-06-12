---
title: "nvidia Geforce 7150m/ nForce 630 - Problem with driver"
date: 2012-07-18
forum: Installation &amp; Upgrades
---

### Post by jalo on 2012-07-18
Hi.
How are you?

I've recently installed Ubuntu 12.04. However I'm having some problems with the graphic drivers. My graphic card is GeForce 7150m / nForce 630. I've installed a lot of updates, however I can only run Ubuntu in 2D and most applications are very slow(e.g. google earth, or pressing alt+tab).

Does anyone has any idea how I can solve this problem? I'd be very grateful.
Thanks.
Daniel.

---

### Post by bogan on 2012-07-18
Hi!,** jalo,**  Welcome to the Forums.

Have you got 'Intel Integrated graphics' as well?

Have you tried the drivers offered by Addition Drivers - from Dash or System settings? or the Downloaded nvidia one?

Please Post:```
 lspci -nnk | grep  -iA3 vga
sudo apt-cache policy nvidia-current
cat /sys/module/nvidia/version
/usr/lib/nux/unity_support_test -p
```Chao!**, bogan.**

---

### Post by jalo on 2012-07-18
Have you got 'Intel Integrated graphics' as well?
I don't know to be honest...

Have you tried the drivers offered by Addition Drivers - from Dash or System settings? or the Downloaded nvidia one?
I can't download the drivers from nvidia because they're only available for windows. I only tried to download using the usual commands:
    sudo apt-get update
    sudo apt-get install nvidia

No luck tho.

Here it is. Hope it helps.

**lspci -nnk | grep  -iA3 vga**
00:12.0 VGA compatible controller [0300]: NVIDIA Corporation C67 [GeForce 7150M / nForce 630M] [10de:0531] (rev a2)
	Subsystem: Hewlett-Packard Company Device [103c:30cf]
	Kernel driver in use: nvidia
	Kernel modules: nvidia_current, nouveau, nvidiafb

**apt-cache policy nvidia-current**
nvidia-current:
  Installed: 295.40-0ubuntu1
  Candidate: 295.40-0ubuntu1
  Version table:
 *** 295.40-0ubuntu1 0
        500 [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) precise/restricted i386 Packages
        100 /var/lib/dpkg/status


**cat /sys/module/nvidia/version**
295.40

**/usr/lib/nux/unity_support_test -p**
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7150M / nForce 630M/integrated/SSE2/3DNOW!
OpenGL version string:  2.1.2 NVIDIA 295.40

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Thanks.
Daniel

---

### Post by bogan on 2012-07-19
Hi!,** jalo,**

Well, lspci shows you do not have Intel integrated graphics, and you have nvidia-current v.295.40 installed.

However, that is the bugged version, and I suggest you try the other driver, ie not the 'recommended' one, but:'  (version current-updates)'. 
From System Settings>Hardware>Additional Drivers, Deactivate the current one and Activate the other, then reboot.

The rest of the Posting shows all OK and it should run unity 3D correctly.
[ It is just possible you may need to blacklist nouveau. It used to be needed, but not usually with the latest version.]

You Posted:>  I can't download the drivers from nvidia because they're only available for windows. Try nvidia.com/downloads and select GeForce>7 series>Linux 32bit{or 64bit] and Search will recommend 295.59 .
[http://www.nvidia.co.uk/object/linux-display-ia32-295.59-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-295.59-driver-uk.html)

If the current-updates driver does not work for you, and you need more instructions to install the nvidia download, Post here.

The command you used : ```
sudo apt-get update
sudo apt-get install nvidia
```would not have worked, you would have needed: ```
sudo apt-get update
sudo apt-get install nvidia-current
```But you have it installed, anyway.

One 'simple' thing worth trying:

Ensure you are logged in to 'ubuntu' .
In a Terminal run:```
 echo $DESKTOP_SESSION # Shows "ubuntu","ubuntu-2D, or gnome
```Press 'Crtl+Alt+F1' [or F2-F6].
Login & enter password.
Run  ```
sudo service lightdm stop
sudo service lightdm restart
```You may need to press  'Crtl+Alt+F7'to return to the GUI screen, though you should not need to.
Run again: ```
 echo $DESKTOP_SESSION
```Chao!, **bogan.**

---

### Post by jalo on 2012-07-19
> **bogan said:**
> Hi!,** jalo,**

Well, lspci shows you do not have Intel integrated graphics, and you have nvidia-current v.295.40 installed.

However, that is the bugged version, and I suggest you try the other driver, ie not the 'recommended' one, but:'  (version current-updates)'. 
From System Settings>Hardware>Additional Drivers, Deactivate the current one and Activate the other, then reboot.

The rest of the Posting shows all OK and it should run unity 3D correctly.
[ It is just possible you may need to blacklist nouveau. It used to be needed, but not usually with the latest version.]

You Posted:Try nvidia.com/downloads and select GeForce>7 series>Linux 32bit{or 64bit] and Search will recommend 295.59 .
[http://www.nvidia.co.uk/object/linux-display-ia32-295.59-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-295.59-driver-uk.html)

If the current-updates driver does not work for you, and you need more instructions to install the nvidia download, Post here.

The command you used : ```
sudo apt-get update
sudo apt-get install nvidia
```would not have worked, you would have needed: ```
sudo apt-get update
sudo apt-get install nvidia-current
```But you have it installed, anyway.

One 'simple' thing worth trying:

Ensure you are logged in to 'ubuntu' .
In a Terminal run:```
 echo $DESKTOP_SESSION # Shows "ubuntu","ubuntu-2D, or gnome
```Press 'Crtl+Alt+F1' [or F2-F6].
Login & enter password.
Run  ```
sudo service lightdm stop
sudo service lightdm restart
```You may need to press  'Crtl+Alt+F7'to return to the GUI screen, though you should not need to.
Run again: ```
 echo $DESKTOP_SESSION
```Chao!, **bogan.**

I activated the current version and Unity 3D runs now! Thank you very much. :)
As to the noveau, how am I supposed to blacklist it? and is it necessary if the unity 3D already works?

Again, thanks!
Daniel.

---

### Post by bogan on 2012-07-19
Hi!,** jalo**,

Great, glad you got it running OK.

I am a great believer in the sayings: " If it aint broke, why fix it?, and: "If it works for you, don't worry about it".

According to the cognoscenti, including Nvidia, the nvidia drivers [ prior to 12.04 release] were incompatible with the then existing nouveau driver.

However, the version of nouveau that comes with 12.04, is greatly altered, much more functional and efficient.

My personal experience is that nvidia v.295.49 and later run perfectly happily in 12.04, with nouveau also installed, without blacklisting it. [v.295.40 is dubious for other reasons as well,  especially with the 5 & 6 series cards].

To blacklist nouveau,  you need to edit or add a file called blacklist.conf in/to the /etc/modprobe.d folder:```
gksu gedit /etc/modprobe.d/blacklist.conf # add the lines:
# Added for nvidia
blacklist nouveau 
``` Save and exit gedit, and reboot.

Chao!, [B]bogan.
[/B]

---

### Post by clinkletter on 2012-12-12
Note that if you install nvidia-current, you will need to install linux-headers-generic first.

If you missed it, you can
$ sudo apt-get install linux-headers-generic
$ sudo apt-get install --reinstall nvidia-current nvidia-settings
$ sudo reboot

If you don't, all your menu's will go away.

Peter L.

---

