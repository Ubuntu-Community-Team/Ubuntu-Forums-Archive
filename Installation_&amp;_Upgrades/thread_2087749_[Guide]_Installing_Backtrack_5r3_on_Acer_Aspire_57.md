---
title: "[Guide] Installing Backtrack 5r3 on Acer Aspire 5742zg (Nvidia Optimus)"
date: 2012-11-24
forum: Installation &amp; Upgrades
---

### Post by Hellcivilian on 2012-11-24
<<This guide was originally written by me for Backtrack 5r3 which is based on ubuntu 10.04 LTS, so some of the following steps might not be needed for the latest release, still you might find some helpful instructions here during the installation of latest Ubuntu.>>

First of all let me clarify that there are some "weird" problems for people trying to install BT5 on Acer Aspire 5742zg and the whole line of those notebooks in general because of their hardware.
They use nvidia optimus system (one integrated gpu and one discrete) whose support is still experimental in linux as well as some Broadcom WIFI adapter which needs you to download and patch the  closed source blob from their site, as the opensource driver doesn't work.

So here is the guide to troubleshoot all those problems and install BT5 on similar notebooks, because as we already said it doesn't work right off the bat as in most notebooks.

1) Boot Backtrack 5 R3 as usual after you burn your iso to dvd or usb and choose the appropriate option on BIOS boot menu.

2) Afterwards when presented with the backtrack Boot Option Menu press TAB and append the following kernel option:
```
text splash vga=791 i915.modeset=1 nomodeset
```Note: "i915.modeset=1 nomodest" is for Optimus only. If nVidia GeForce, just need "nomodeset".

If you miss this step you won't be able to startx and will get a black screen instead.

3) Then startx (it will work because of step 2) and run the backtrack install script as usual to install BT5 on your system. Reboot and remove disc.

4) Boot to your newly installed system but DON'T startx as you will get a black screen (again).
To fix that permanently now do the following:

nano -w /etc/default/grub

Change the GRUB_CMDLINE_LINUX_DEFAULT= parameter to: GRUB_CMDLINE_LINUX_DEFAULT="text splash vga=791 i915.modeset=1 nomodeset"
Press ctrl+o to save and ctrl+x to exit.

Then run "update-grub" for the changes to become permanent and you be able to startx normally without having to press tab and edit the kernel line again.

Also if you wish to have that cool graphic that you saw in the livecd during boot, that shows a small terminal screen surrounded by the backtrack dragon logo do:
"fix-splash"

5) Reboot again, login to your new system and type "startx". Now it works by default. At this point the black screen problem (not being able to startx) is resolved and we will proceed fixing the wifi adapter.

6) You will need to grab a binary file and a patch file from the internet. So if you connect via ethernet you are good to go, BUT if you connect to the internet only via WIFI you will have to download those files from another computer and burn them in a cd or flash usb to transfer them at your network-less notebook.

The first file is Broadcom 802.11 Linux STA driver (proprietary) which you can grab from this site:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
Make sure to get 32bit or 64bit version depending on which ISO you selected for Backtrack (must be same architecture as your system)

Then download this patch (the driver need to be patched for the kernel backtrack 5r3 uses: 
[http://www.mindwerks.net/wp-content/uploads/2011/11/bc_wl_abiupdate.patch](http://www.mindwerks.net/wp-content/uploads/2011/11/bc_wl_abiupdate.patch)

7) Move those files in your home directory and do:

mkdir -p wl; mv bc_wl_abiupdate.patch wl; cd wl; tar xf ../hybrid-portsrc*-v5_100_82_38.tar.gz  (To create wl directory and extract the driver)

Then do: patch -p0 src/wl/sys/wl_linux.c < bc_wl_abiupdate.patch  (To apply the patch)

And finally: make; make install; depmod; modprobe wl  (To compile, install and load the wl module which operates the wifi)

Normally this will also make your wl module to be run automatically at boot, otherwise you will have to run "modprobe wl" everytime or make the module autostart. The file to put wl in that case is /etc/modules.

8) Afterwards run: "rfkill unblock all"  without the " to make sure your wireless devices are not software or hardware blocked.
Then run "iwconfig" and check which device HAS wireless extensions. It probably won't be wlan0 which is the usual but something like eth1, so pay extra attention here.
IF it is eth1 lets say our widi device with wireless extension (appears in iwconfig) you will need to open Wicd network manager (do the same in whatever manager you may use) and go "Preferences" and afterwards set at Wireless Interface "eth1", OTHERWISE it will check on wlan0 and the list will be empty, while you think the driver/WIFI doesn't work.
So make sure you select the correct interface there cause it won't work by default as usual.

At last reboot again and startx to make sure WIFI starts correctly automatically. You should be able to see "wl" module loaded if you type "lsmod".

9) Now that we resolved the weird problems its time to continue installing the software needed for our peculiar hardware that is nvidia optimus (2 gpus).
After you connect to the internet via wifi or ethernet and you have run the usual system upgrade commands (apt-get update; apt-get upgrade; apt-get dist-upgrade) do the following:

add-apt-repository ppa:ubuntu-x-swat/x-updates (To add the repo that contains the latest nvidia driver)
apt-get update
apt-get install nvidia-current nvidia-current-modaliases nvidia-settings

Now proceed to install CUDA toolkit which you will need if you plan to have GPU support in Pyrit, which will need you to compile cpyrit.
IF you don't use Pyrit and use cudahashcat-plus which doesn't require the toolkit you don't need the toolkit.

ln -s /usr/lib/x86_64-linux-gnu/libglut.so /usr/lib/libglut.so (ONLY IF YOU HAVE AN 64BIT SYSTEM otherwise you get an error installing cuda samples)

wget [http://developer.download.nvidia.com/compute/cuda/5_0/rel-update-1/installers/cuda_5.0.35_linux_64_ubuntu10.04-1.run](http://developer.download.nvidia.com/compute/cuda/5_0/rel-update-1/installers/cuda_5.0.35_linux_64_ubuntu10.04-1.run)    (64BIT SYSTEMS)
OR
wget [http://developer.download.nvidia.com/compute/cuda/5_0/rel-update-1/installers/cuda_5.0.35_linux_32_ubuntu10.04-1.run](http://developer.download.nvidia.com/compute/cuda/5_0/rel-update-1/installers/cuda_5.0.35_linux_32_ubuntu10.04-1.run)    (32BIT SYSTEMS)

chmod +x cuda_5.0.35_linux_64_ubuntu10.04-1.run   OR   chmod +x cuda_5.0.35_linux_32_ubuntu10.04-1.run

then

./chmod +x cuda_5.0.35_linux_64_ubuntu10.04-1.run   OR   ./chmod +x cuda_5.0.35_linux_32_ubuntu10.04-1.run

NOTE: When asked about the eula type accept, when asked about nvidia driver type NO you already have the latest driver package installed, when asked about cuda toolkit type yes and enter for defautl destination, say yes or no to cuda samples if you need them and press enter for default destination.

Afterwards:  nano /root/.bashrc

Append the following :

PATH=$PATH:/usr/local/cuda-5.0/bin
LIBRARY_PATH=$LIBRARY_PATH:/usr/lib/nvidia-current
LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-5.0/lib:/usr/local/cuda-5.0/lib64:/lib
export PATH
export LIBRARY_PATH
export LD_LIBRARY_PATH

Save and exit .bashrc

Now to install the bumblebee software which is needed to switch from GPU to GPU using the optimus technology do:

add-apt-repository ppa:bumblebee/stable
apt-get update
apt-get install bumblebee bumblebee-nvidia

Then reboot your system, login and startx again.

10) To test if nvidia optimus works do:
glxspheres (this uses the embedded gpu and you should have low fps) and then:
optirun glxspheres (this uses nvidia discrete and you should have high fps)

In general remember when you need to use nvidia for high performances gpu applications or cuda write "optirun" before the command.

11) To install the latest Pyrit and use it along with Cuda Toolkit (if you don't use pyrit or don't need GPU support, skip this step)

apt-get purge pyrit  (remove the old version)
apt-get install subversion python-dev libssl-dev libpcap-dev (install required apps for pyrit to compile)
cd ~; svn checkout [http://pyrit.googlecode.com/svn/trunk/](http://pyrit.googlecode.com/svn/trunk/) pyrit_svn  (to grab the latest svn source of pyrit)
cd pyrit_svn/pyrit; python setup.py build; python setup.py install  (compile and install pyrit)
cd ~/pyrit_svn/cpyrit_cuda; python setup.py build; python setup.py install   (compile and install cpyrit addon which enables cuda support)

To test our setup do:
optirun pyrit list_cores  (Here check to see if gpu is detected, normally you will have your cuda gpu in place of one of your cpu cores)
optirun pyrit benchmark or optirun pyrit benchmark_long  (Benchmark your performance)

REMEMBER: If you don't use "optirun" before all your pyrit commands or even in cudahashcat-plus (which you can use too) you won't be able to use your Nvidia GPU and your "cracking" speed will be low.

At this point you should have your startx starting normally, your wifi enabled, your drivers for nvidia-current and optimus system installed as well as Pyrit with GPU support (if you use that).

Thanks for viewing this guide, and remember to share this info with other people as i have found that those problems are common to many, who decide they can't troubleshoot them and proceed to installing plain ubuntu or even windows 7 out of frustration.

Happy cracking. :)

---

