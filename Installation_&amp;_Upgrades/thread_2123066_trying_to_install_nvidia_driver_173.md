---
title: "trying to install nvidia driver 173"
date: 2013-03-07
forum: Installation &amp; Upgrades
---

### Post by rkonrad on 2013-03-07
I am having difficulty installing the proprietary driver, 173 on my system.  Under synaptic pkg manager - additional drivers, the driver is listed (the nouveau is currently installed) but when I select it and "apply" it stalls.  I've googled this, [http://namakutux.blogspot.ca/2012/11/solved-how-to-install-nvidia-173-on.html](http://namakutux.blogspot.ca/2012/11/solved-how-to-install-nvidia-173-on.html) but when I am instructed to > 3. Create two pin addresses to specify a version of a Debian package
sudo /etc/apt/preferences.d/xorg-xserver-pin-1050 I get > command not found.  I'm honestly not sure what to do at this point.  If I must, I'll install it manually but would prefer not to because of repeating the process when the kernel is upgraded.  Thanks in advance.

Richard

---

### Post by rkonrad on 2013-03-07
I didn't mention I'm using lubuntu 12.10

---

### Post by bogan on 2013-03-07
Hi!,** rkonrad**,

If you **need** the 173 driver, ie for an nvidia GPU prior to 6xxx series you may need to backport to 12.04.

Please Post:```
 uname -r
lspci -nnk | grep -iA3 vga
glxinfo | grep -i opengl
```You could try: 'Ctrl+Alt+F1', login & Password,```
sudo service lightdm stop
sudo apt-get update
sudo apt-get remove --purge nvidia-173
sudo apt-get remove --purge nvidia*
sudo apt-get install -f
sudo apt-get install linux-headers-generic
sudo apt-get install nvidia-173
sudo service lightdm restart
sudo reboot
```If needed:'Ctrl+Alt+F7', should return you to a GUI.

Chao!, **bogan**.

---

### Post by rkonrad on 2013-03-07
uname -r  3.5.0-25-generic

lspci -nnk | grep -iA3 vga
00:0d.0 VGA compatible controller [0300]: NVIDIA Corporation C61 [GeForce 6100 nForce 405] [10de:03d1] (rev a2)
	Subsystem: Elitegroup Computer Systems Device [1019:2609]
	Kernel driver in use: nouveau
	Kernel modules: nouveau, nvidiafb

glxinfo | grep -i opengl
OpenGL vendor string: nouveau
OpenGL renderer string: Gallium 0.4 on NV4C
OpenGL version string: 2.1 Mesa 9.0.2
OpenGL shading language version string: 1.20
OpenGL extensions:

Thanks

---

### Post by bogan on 2013-03-07
Hi!, **rkonrad**,

Nvidia.com drivers shows the 304.84 driver as recommended for the "NVIDIA Corporation C61 [GeForce 6100 nForce 405]"card, which is also listed as supported for the 304.51 driver, which is  available from Ubuntu sources.

So you should have no need to go to a legacy driver like the 173; but make sure not to get the 310.xx or later drivers which no longer support the 6xxx series.

In my suggested code of the previous Post, substitute 'nvidia-current' for 'nvidia-173' in: ```
sudo apt-get install nvidia-173
```Chao!, **bogan**.

---

### Post by rkonrad on 2013-03-08
> **bogan said:**
> Hi!, **rkonrad**,

Nvidia.com drivers shows the 304.84 driver as recommended for the "NVIDIA Corporation C61 [GeForce 6100 nForce 405]"card, which is also listed as supported for the 304.51 driver, which is  available from Ubuntu sources.

So you should have no need to go to a legacy driver like the 173; but make sure not to get the 310.xx or later drivers which no longer support the 6xxx series.

In my suggested code of the previous Post, substitute 'nvidia-current' for 'nvidia-173' in: ```
sudo apt-get install nvidia-173
```Chao!, **bogan**.

Sorry but I can't get past "sudo service lightdm stop".  It get "buffer I/O error on device Fd0, logical block 0" I never get a prompt.

---

### Post by rkonrad on 2013-03-08
> **rkonrad said:**
> Sorry but I can't get past "sudo service lightdm stop".  It get "buffer I/O error on device Fd0, logical block 0" I never get a prompt.
Ahh..you are assuming I'm using a 64 bit system.  I have just less that 1 gb of RAM so I have been advised to run a 32 bit system.  In light of this I think the 173 driver is correct?

---

### Post by bogan on 2013-03-08
> **rkonrad said:**
> Ahh..you are assuming I'm using a 64 bit system.  I have just less that 1 gb of RAM so I have been advised to run a 32 bit system.  In light of this I think the 173 driver is correct?No!, I was not assuming a 64 bit system; the nvidia.com recommendation of the 304.84, or 304.51 drivers is for Linux 32 bit. And they should run OK on 1GB of ram.

I do not understand the:> Sorry but I can't get past "sudo service lightdm stop".  It get "buffer  I/O error on device Fd0, logical block 0" I never get a prompt.Are you pressing 'Ctrl+Alt+F1' and logging in, before entering: 'sudo service lightdm stop' ??

Try booting from grub menu with 'single' added to the 'linux /boot line', where it says: "ro quiet splash ".[ Press 'e' to get into edit mode, & after adding single, press 'Ctrl+x' ].

That should get you direct to a root prompt without the Xserver being activated, nor a need to login- but be careful!! you will not need to use 'sudo'. as you will already be root.

Chao!, **bogan**.

---

### Post by rkonrad on 2013-03-09
Well thanks for your time....yeah, I missed the Ctrl+Alt+F1.  I did the installation and what do you know...the display is poorer than with the nouveau driver.  It's overly bright and slightly washed out.  I don't know how to test the driver except by how it looks though.  I tried the 173 driver as well and it was similar but with font problems and the odd flicker.  I wouldn't mind getting back to the original nvidia-nouveau to see if my eyes are not playing tricks.  Would I do "sudo apt-get install nvidia-nouveau?  

Thanks again

---

### Post by bogan on 2013-03-10
Hi!, **rkonrad**,

You Posted;> I wouldn't mind getting back to the original nvidia-nouveau to see if  my eyes are not playing tricks.  Would I do "sudo apt-get install  nvidia-nouveau?No!, you would need to use ```
sudo apt-get install --reinstall xserver-xorg-video-nouveau
```But first you need to remove the installed nvidia drivers by name, eg.: ```
sudo apt-get remove --purge nvidia-current # change packagename to suit
sudo apt-get remove --purge nvidia* 
```And delete or comment out, any nouveau blacklist files in /etc/modprobe.d, or entries in /etc/modprobe.d/blacklist.conf, from rooot; then reboot.

Edit: The file in modprobe.d may be called "nvidia-graphics-drivers.conf" or "nouveau-graphics....conf". Incidentally, such a file may have nvidia-173 blacklisted, which may have messed up that driver when you tried it.

Chao!, **bogan**.

---

### Post by mirearts KING SUNNY on 2013-03-10
DOWNLOAD:

[http://packages.ubuntu.com/lucid/amd64/nvidia-173/download](http://packages.ubuntu.com/lucid/amd64/nvidia-173/download)

---

### Post by rkonrad on 2013-03-11
Success with the reinitialisation of nvidia-nouveau - thanks.  Eyes were not playing tricks as the display is definitely better.  Also, nothing was blacklisted,  not nouveau or 173.  Any thoughts on why this might be?  I would like to have the best driver that I can have for performance reasons of course.  I"ve ordered some more ram and so should be up to just under 4 gigs when installed.  Perhaps I will try lubuntu 64 and see how that goes with the new driver.  Thanks for your help.

Richard

---

### Post by rkonrad on 2013-03-11
Sorry I was not clear - any thoughts on why the display is poorer when I installed the correct driver?

---

### Post by bogan on 2013-03-11
> **rkonrad said:**
> Sorry I was not clear - any thoughts on why the display is poorer when I installed the correct driver?**Hi!,**

If the nouveau driver was not blacklisted - nvidia.com or nvidia-current will normally do this - then the two drivers were probably in conflict. But in any case, it is not unusual for some drivers to work better than others depending on the hardware and firmware.

It could also be a matter of some configuration being needed, or a monitor in need of adjustment.

It is necessarily a matter of trial and error to find the best for your particular system and requirements.

Chao!,** bogan.**

---

