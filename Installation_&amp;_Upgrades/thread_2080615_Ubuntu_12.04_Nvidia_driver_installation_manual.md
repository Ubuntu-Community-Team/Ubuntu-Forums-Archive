---
title: "Ubuntu 12.04 Nvidia driver installation manual"
date: 2012-11-04
forum: Installation &amp; Upgrades
---

### Post by Artpen on 2012-11-04
Hi Guys,

A couple days ago I took office laptop home to install Ubuntu 12.04.
Installation went smooth. But.... I wasn't able to install Nvidia driver.
I am working in Blender and I need 3D acceleration and CUDA.

Laptop: Dell Inspiron 17r se
            Nvidia 650M 2Gb

I was trying to install the driver using [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)
But ended up with low resolution screen and message : you do not appear to be using the nvidia x driver!

I am asking for some advice:

1. Is there a wise installation manual of Nvidia drivers with explanation of each command?
2. Where can I get an understanding what I am actual doing? (not just copy/paste in terminal)
3. How to test video drivers and their performance?
4. Why after installing Ubuntu I don't have xorg file?
Just want to be able install video drivers on different machines with knowledge and understanding.

If you need more information about my system, I can post it....

Cheers

---

### Post by bogan on 2012-11-04
Hi,** Artpen**,

Have a look at this: [it may meet your requirements; Q1 & Q2.]
[http://ubuntuforums.org/showthread.php?t=2075318](http://ubuntuforums.org/showthread.php?t=2075318)

It is easier to give a Link than to copy it here.

Part Answer to Q3. For ubuntu 11.10 and later, run : > /usr/lib/nux/unity_support_test -p 

Answer to Q 4. The xorg.conf file is no longer needed, but is taken into account if it exists.

Chao!, **bogan**.

---

### Post by Artpen on 2012-11-04
Thanks Bogan,
I will try OldFred guide, but I just have found that my problem is Optimus technology??
Will come back after trying you links

Thanks

---

### Post by bogan on 2012-11-04
> ****Artpen** said:**
> Thanks Bogan,
I will try OldFred guide, but I just have found that my problem is Optimus technology??
Will come back after trying you links

Thanks
In that case you will surely need the latest nvidia driver [304] and Bumblebee.

Chao!, **bogan.**

---

### Post by Artpen on 2012-11-04
Do I need to install video driver first , and then Bumblebee?
You made a nice step by step instruction here : [http://ubuntuforums.org/showthread.php?t=2075318&page=4](http://ubuntuforums.org/showthread.php?t=2075318&page=4)

Thanks

---

### Post by bogan on 2012-11-04
Hi!,** Artpe**n,

I am by no means an expert on Optimus or Bumblebee, but I believe Bumblebee prefers to install the nvidia driver itself.

Read all about it here:
[http://bumblebee-project.org/](http://bumblebee-project.org/)

Edit: This is an excerpt, the links probably will not work.
[actually they do]> **Ubuntu linux**

       Currently, you need to open your terminal and enter the commands below. 
```
sudo add-apt-repository ppa:bumblebee/stable 
```If you are on Ubuntu 11.04 or older and want newer drivers (recommended) than the ones available in the official repos, run: ```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
 sudo apt-get update
``` To install Bumblebee using the proprietary nvidia driver: ```
sudo apt-get install bumblebee bumblebee-nvidia
``` Reboot or re-login. [More help and information for Ubuntu can be found here.]("https://wiki.ubuntu.com/Bumblebee#Installation")Chao!, **bogan**.

---

### Post by Artpen on 2012-11-04
You are right, it doesnt work for me (

I have tried :
1. Installed Bumblebee = it says  ERROR Cannot access secondary GPU -error: [XORG] (EE)
2. Removed Bumblebee and installed Nvidia drivers 304 = low resolution and same message : you do not appear to be using the nvidia x driver!

:confused:

---

### Post by bogan on 2012-11-05
Hi!, **Artpen,**

I was hopeful that someone more knowledgeable about Optimus and Bumblebee would come in.

However, in the meantime there are several things you could try, partly depending on how you installed the Nvidia 304 driver, or any previous drivers.

Did you use an NVIDIAxxx.xxx.run file downloaded from nvidia.com, select a driver from Additional Drivers or Synaptic, or use 'apt-get install' directly, or from a ppa such as x-swat?

Have you tried running nvidia-config and re-booting?

Please Post commands and their output from running the following from a terminal: ```
uname-r
lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p
cat /sys/module/nvidia/version
sudo apt-cache policy nvidia-current
```In the last command substitute the package name of the driver you installed , eg 'nvidia-current- experimental-304', or, if in doubt: 'nvidia-current*', this command will not work for an nvidia downloaded driver.

A number of people have reported similar problems due to the absence of 'linux-headers-generic'. So run: ```
sudo apt-get install linux-headers-generic
```If it reports that it is already the latest version, then this is not the cause of your problem.

If it installs it, then you will need to run:```
apt-get remove --purge nvidia*
apt-get install nvidia-experimental-304 # or use the correct package- name if different
sudo dpkg-reconfigure nvidia-experimental-304 # again change if needed
sudo reboot
```Alternatively, after the 'remove --purge' command, run the nvidia downloaded file from a text terminal.

Also: checkout the /etc/modprobe.d  folder, to check if there are files blacklisting nouveau, probably called "nvidia-graphicsxxx' or some-such,  or an entry in the "blacklist.conf" file; if not they will need to be made, but installing an nvidia driver should create one. { I am not sure if the 'remove --purge' command would delete them, I think not.}

Chao!, **bogan.**

---

### Post by bogan on 2012-11-06
Hi!. **Artpen,**

It is probably worth your while checking out this thread:
[http://ubuntuforums.org/showthread.php?t=2073431](http://ubuntuforums.org/showthread.php?t=2073431)

Chao!,** bogan.**

---

### Post by Artpen on 2012-11-10
Hi Bogan,

Thanks for help and links. I have found a solution for my Laptop Dell Inspiron 17SE.
Here are step that helped me:

1. Fresh install of Ubuntu 12.04
2. No Nvidia drivers
3. Installing ppa x swat. should to run sudo apt-get upgrade after installing ppa
4. Installing bumblebee [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
5.Restart
6. Receiving a ERROR message while running optirun glxspheres: 
**[ERROR]Cannot access secondary GPU - error: [XORG] (EE) [drm] failed to open device**

7. Setting Driver=nvidia and KernelDriver=nvidia 

8. Same error :confused:

9. Replacing "ConnecteMonitor" "DFP" by "UseDisplayDevice" "none" in /etc/bumblebee/xorg.conf.nvidia
10. AND FINALLY optirun is working !!!!


Here is a good post:  [https://github.com/Bumblebee-Project/Bumblebee/issues/216](https://github.com/Bumblebee-Project/Bumblebee/issues/216)



Cheers,
Artpen

---

### Post by bogan on 2012-11-10
Hi!, **Artpen**,

Great! Glad you found a solution.

Chao!, **bogan**.

---

### Post by Artpen on 2012-11-11
Do I need to remove x-swat an bumblebee ppa for my system after installation?

---

### Post by bogan on 2012-11-12
> **Artpen said:**
> Do I need to remove x-swat an bumblebee ppa for my system after installation?
It would be advisable to do so before any kernal update.

Chao!, **bogan**.

---

### Post by bogan on 2012-11-15
Hi!, **All,**

 RE:** Warning**! Nvidia beta driver 310 does not support 6xxx series cards, and Nvidia warns it may ignore 7xxx series GPU's.

The same, presumably, applies to the **Additional Drivers 'nvidia-experimental-310' **driver, as well.

I have been running, successfully, the 310.14 driver, with 12.10  Quantal, on an 8GB USB SanDisk, in a computer with a GeForce GT 520  card. That is an nvidia.com downloaded '.run' file.

I transferred the USB to a computer with a GT 7650 card and its graphics  were a total shambles, with a GUI in a very low-res with huge  characters & Mouse cursor, but no launcher or tool bar panel.[  Nouveau was blacklisted.]

When I ran:```
NVIDIA-Linux-x86-310.14.run --latest
``` it listed  310.14 as installed, and 310.16 as the latest available. { Incidently,  310.16 is not listed as an available Beta driver on the nvidia website,  though the whole 7xxx series is listed as supported by 310.14 beta, but  not the 6xxx series}.

However, when I tried to reinstall 310.14, I got a message saying no  graphics card had been detected that was supported by 310.14, and if  installed it would ignore my GPU; ie. the GT 7650. It recommended I  install 304.60.

So if you have a 6000 or 7000 series video card watch out.

Chao!,** bogan**.

---

### Post by blueicewater on 2013-02-12
> **Artpen said:**
> Hi Bogan,

Thanks for help and links. I have found a solution for my Laptop Dell Inspiron 17SE.
Here are step that helped me:

1. Fresh install of Ubuntu 12.04
2. No Nvidia drivers
3. Installing ppa x swat. should to run sudo apt-get upgrade after installing ppa
4. Installing bumblebee [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
5.Restart
6. Receiving a ERROR message while running optirun glxspheres: 
**[ERROR]Cannot access secondary GPU - error: [XORG] (EE) [drm] failed to open device**

7. Setting Driver=nvidia and KernelDriver=nvidia 

8. Same error :confused:

9. Replacing "ConnecteMonitor" "DFP" by "UseDisplayDevice" "none" in /etc/bumblebee/xorg.conf.nvidia
10. AND FINALLY optirun is working !!!!


Here is a good post:  [https://github.com/Bumblebee-Project/Bumblebee/issues/216](https://github.com/Bumblebee-Project/Bumblebee/issues/216)



Cheers,
Artpen

Hi Artpen, I have the same exact laptop as yours and I'm installing Ubuntu for the first time, so please forgive my newbness.

Could you please provide more details for the commands in Step 3 and Step 7?

Much appreciated! :)

---

