---
title: "ubuntu studio in existing ubuntu installation"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by ZeldaFan on 2008-08-22
How do I install Ubuntu Studio in an existing Ubuntu Hardy Heron installation? (Along with the RT kernel)

---

### Post by kinetek on 2008-08-22
It's quite easy.

Go to System-> Administration-> Software Sources 
and enable the 'universe repository.

Then go to a terminal (default is called Terminal, located in Accessories), and run the following command :

sudo apt-get install ubuntustudio-desktop && sudo apt-get install ubuntustudio-icon-theme && sudo apt-get install ubuntustudio-look && sudo apt-get install ubuntustudio-theme && sudo apt-get install ubuntustudio-wallpapers && sudo apt-get install usplash-theme-ubuntustudio

If you are worried about the cut and paste, here they are on individual lines :

sudo apt-get install ubuntustudio-desktop
sudo apt-get install ubuntustudio-icon-theme
sudo apt-get install ubuntustudio-look
sudo apt-get install ubuntustudio-theme
sudo apt-get install ubuntustudio-wallpapers
sudo apt-get install usplash-theme-ubuntustudio

All of the other packages can be installed from the Update manager, or using Synaptic.

But those are the key packages that gives Ubuntu Studio its overall look and feel.

---

### Post by ZeldaFan on 2008-08-22
I am not interested in the appearance aspect of ubuntu studio. I just want the performance aspects, such as the RT kernel and the applications. In that case would I only need to install the first package you mentioned?

---

### Post by logos34 on 2008-08-22
> **ZeldaFan said:**
> I am not interested in the appearance aspect of ubuntu studio. I just want the performance aspects, such as the RT kernel and the applications. In that case would I only need to install the first package you mentioned?

You want the [**linux-rt**]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy") package (low-latency kernel).

[Read this]("https://help.ubuntu.com/community/UbuntuStudioPreparation") for settings, etc.

good luck

---

### Post by snowpine on 2008-08-22
> **ZeldaFan said:**
> I am not interested in the appearance aspect of ubuntu studio. I just want the performance aspects, such as the RT kernel and the applications. In that case would I only need to install the first package you mentioned?

```
sudo apt-get install ubuntustudio-audio ubuntustudio-audio-plugins linux-rt
```

That's if you just want the audio applications and real-time kernel. The video I believe is 'ubuntustudio-video' (I've never personally used video, just the audio).

---

### Post by ZeldaFan on 2008-08-25
Just a quick question, I installed the real time linux kernel, but how do I get it to show up as a boot option in my kernel. I've installed it, but I only have the option to boot into my generic kernel in grub.

---

### Post by logos34 on 2008-08-25
> **ZeldaFan said:**
> Just a quick question, I installed the real time linux kernel, but how do I get it to show up as a boot option in my kernel. I've installed it, but I only have the option to boot into my generic kernel in grub.


sudo grub-install /dev/sda

(or whatever your drive is)

---

### Post by ZeldaFan on 2008-08-26
That command makes me slightly nervous. I have a dual hard drive system set up, one hard drive loading only windows, the other loading ubuntu. I have grub installed on my linux hard drive and I manually added an entry for my windows partition. I feel like that command will screw with my current config, is that true?

---

### Post by logos34 on 2008-08-26
> **ZeldaFan said:**
> That command makes me slightly nervous. I have a dual hard drive system set up, one hard drive loading only windows, the other loading ubuntu. I have grub installed on my linux hard drive and I manually added an entry for my windows partition. I feel like that command will screw with my current config, is that true?

well then check 

sudo fdisk -l

to verify the drive letter of the linux drive.

grub-install command will search /boot for all kernel images and add them to menu.lst, then write stage1 to the MBR of the indicated drive.  Note I used the '/dev/sdx' format rather than '(hd0)' to avoid any confusion

---

### Post by ZeldaFan on 2008-09-01
Have any of you guys got both the linux-rt kernel and generic kernel working? I am using Envy's nvidia drivers, and when the drivers are installed in the generic kernel, but linux-rt kernel gives me a Xorg error claiming a mismatch between the nvidia driver number in the x server and kernel module. I have a feeling that the kernel module in linux-rt is outdated, but I dont know how to change it. Could it be a DKMS issue as to why its not updating?

---

### Post by logos34 on 2008-09-01
> **ZeldaFan said:**
> Have any of you guys got both the linux-rt kernel and generic kernel working? I am using Envy's nvidia drivers, and when the drivers are installed in the generic kernel, but linux-rt kernel gives me a Xorg error claiming a mismatch between the nvidia driver number in the x server and kernel module. I have a feeling that the kernel module in linux-rt is outdated, but I dont know how to change it. Could it be a DKMS issue as to why its not updating?

currently I just have -rt installed, but I used to have the -generic too.

Sounds like envy is building the nvidia kernel interface module against the -generic source, which is why it doesn't work with the real-time kernel.

Try reinstalling envy with this pkg:

sudo apt-get install **linux-headers-rt**

If that doesn't work you can always try installing the driver (NVIDIA-Linux-...run) manually, but you'll have to point the interactive installer to the source ('--kernel-source-path=/usr/src/linux-headers-2.6.24-rt')

---

### Post by ZeldaFan on 2008-09-01
Thanks for the reply, I was thinking about install headers too for my kernel because I heard somewhere they were required for updating the kernel modules, but I didn't want to do anything without really knowing what I was doing. I'll try installing and then reinstalling envy's drivers.

---

### Post by ZeldaFan on 2008-09-01
Installing the linux-rt headers didn't help, but I was wondering. Is there a way to point the driver to multiple kernels (rt and generic). Because linux-rt does work if I install the drivers in that kernel, but then the drivers do not work in the generic kernel. There seems to be a problem with having nvidia drivers installed on both kernels simultaneously.

---

### Post by koobies97 on 2009-05-19
I am trying to do the same thing, but under what panel is the Universal repository?
And when i install the packages it seems it apparently has problems with /var/lib/dpkg/lock. any help?

---

### Post by ZeldaFan on 2009-05-19
Do you have another package manager running? It will not let you install if you have update manager or synaptic running.

---

### Post by koobies97 on 2009-05-19
yay! thank you now it works i just closed all other windows. :D

---

