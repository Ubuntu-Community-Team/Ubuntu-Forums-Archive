---
title: "Graphics fail; ZFS partition &amp; file recovery"
date: 2023-06-22
forum: Installation &amp; Upgrades
---

### Post by gbp00 on 2023-06-22
Had a failed CUDA Install for new GPU and now at a TTY line. No idea how to solve this. (Thanks nvidia). So opting for a fresh install alongside to keep files. 

Open to options that will fix the graphics driver issues from Linux USB. Preferable. 

If not, then could you help me understand options?

 Do I need to transfer ZFS data to HDD then do a erase data install? If so how is this done from USB Linux?

Or explain how I can repartition the ZFS to allow space for the new installation? 

Very new so please put an idiot filter on any answers.

I know how to do None of the above.

Please & thank you. &#128580;

---

### Post by MAFoElffen on 2023-06-23
Pause... Please. Backup a few moments.

What happened and what does it do now?

It sounded like you tried to install nVidia CUDA drivers. The installation of those failed. 
> 
and now at a TTY line.

Did you mean at a command prompt? Does it still boot to that? Do you get a Grub2 boot menu when booting? You said "new GPU"... What is it?

The good news with what you described, is that you just boinked your graphics drivers. I can lead you though fixing that from the command prompt.

If that wasn't what you meant, I can lead you through getting to a command prompt, to fix this.

Either way, it sounds like the Kernel is still booting successfully, and the base system is okay. Which means you really might not have to reinstall.

If not, then I'll lead you through mounting installed ZFS pools to backup your data to do a fresh install. But I don't think you will really need to do that.

---

### Post by gbp00 on 2023-06-23
I am very grateful for your help. 

This is the chain of events


Followed the instructions:

[https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html)

gcc installed

downloaded as instructed by
2.7. Download the NVIDIA CUDA Toolkit&#61633;

Installation Instructions:

wget [https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-keyring_1.0-1_all.deb](https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-keyring_1.0-1_all.deb)

sudo dpkg -i cuda-keyring_1.0-1_all.deb
sudo apt-get update
sudo apt-get -y install cuda

removed Outdated Signing Key: or at least did what it said to do in terms of:
sudo apt-key del xxxxxxx when it instructed

sudo apt-get update

sudo apt-get install cuda

sudo apt-get install nvidia-gds

sudo reboot

system doesnt boot with old or new graphics card now.

The terminal flashes for a half a second on boot and I managed to film some error codes, but the frame rate isn't fast enough to see exactly....

I think I read:
"Failed to start nvidia persistence daemon"

Only "tty" terminal available, so guessing the solution has to be there.



Please help with terminal commands to get CUDA working so I can install new driver? 

Driver is [https://us.download.nvidia.com/XFree86/Linux-x86_64/535.54.03/NVIDIA-Linux-x86_64-535.54.03.run](https://us.download.nvidia.com/XFree86/Linux-x86_64/535.54.03/NVIDIA-Linux-x86_64-535.54.03.run)

---

### Post by MAFoElffen on 2023-06-24
Make things a bit easier on yourself...

Having been a UNIX/Linux user, using high-end nVidia GPU's since 2015... I always set up the Grub2 menu to always 'show' on boot, even if for an instant. Because if we have problems with the graphics driver, that we can boot the system various kinds of ways, to get to either a fall-back safe graphics mode, or a command prompt to remove and/or reinstall graphics drivers. Since you can get to a command prompt, you don't need this immediately, but can do it later. I tell you how later. 

From the command line, do
```

sudo apt-get update
sudo apt-get remove --purge nvidia-gds
sudo apt-get remove --purge cuda
DRIVER=$(apt list nvidia-driver* --installed 2> /dev/null | awk -F '[/]' '{print $1}' | tail -n 1)
echo -e "$DRIVER"
sudo apt remove --purge $DRIVER
sudo apt install $DRIVER

```

EDIT: When you get your graphics back up, are yo planning on trying to get the CUDA toolkit reinstalled? Or where are you with that? Think on those questions. I know your immediate priority is getting graphics working again.

---

