---
title: "Alienware m17x problems"
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by masanasj on 2011-10-30
> **datman said:**
> Hey all, another M17x Ubuntu user here. Thought I would put my experiences here to help other M17x users up and running.

[B]Graphics
[/B]
I have dual Nvidia GTX260M, ATI installs will be different.

To get graphics working:

First disable integrated and hybrid graphics in the BIOS.

Now install prerequisites:

sudo apt-get install linux-headers-`uname -r` binutils pkg-config build-essential  xserver-xorg-dev

Now you can download the NVIDIA driver from here:

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Select the latest version of **Linux AMD64/EM64T** drivers, and then install like this:

chmod +x NVIDIA-Linux-x86_64-190.42-pkg2.run
./NVIDIA-Linux-x86_64-190.42-pkg2

Reboot and your X should be working.[B] Note that if you boot up while on battery, Integrated graphics will be automatically enabled in BIOS and then X will fail to start properly.
[/B]
**Sound**

I followed niite's suggestion to get sound working, which worked OK, but I could only get sound from the headphone socket and not the internal speakers. To fix, I changed the line:

options snd-hda-intel model=dell-m6 enable=1 index=0

to 

options snd-hda-intel model=laptop enable=1 index=0

also i updated ALSA to latest version, see here:

[http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)

Now sound works correctly from the speakers and mutes them when i plug in the headphones.

[B]WiFi

[/B]And to get wifi working took the following steps:

**1. Download and build the STA driver module:**

System > Administration > Hardware Drivers should be able to download and install the modue for you, but it would not work for me. 

So manually download the STA 64 bit driver from here:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

then build and install it like this:

cd <path_where_you_downloaded>
sudo cp hybrid-portsrc-x86_64-v5.10.91.9.3.tar.gz /usr/local/src
# you might need to change the version above if it does not match your download
cd /usr/local/src
sudo mkdir hybrid_wl
cd hybrid_wl
sudo tar xzf <path>/hybrid-portsrc-x86_64-v5.10.91.9.3.tar.gz
sudo make

You should now have a wl.ko file successfully built. You should now copy it to your kernel modules lib folder (substitute your kernel version)

sudo cp wl.ko /lib/modules/<kernel-version>/kernel/net/wireless 

**2. Disable other conflicting modules**

Now you have to remove any conflicting modules. To see if any are loaded, type:

lsmod  | grep "b43\|ssb\|wl"

If any of these are installed, remove them:
sudo rmmod b43
sudo rmmod ssb
sudo rmmod wl

To blacklist these drivers and prevent them from loading in the future:
sudo echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
sudo echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf

Even though they are blacklisted, ssb will still be loaded in the initramfs. This will prevent wl.ko from loading after booting. To fix this, type:

sudo update-initramfs -u

**3. Enable the new module at boot**

and finally to start the wl module automatically at boot:

sudo echo "wl" >> /etc/modules

Now reboot and set up your wireless password etc in NetworkManager. If you upgrade your kernel in future, you will have to rebuild the module and copy it into the new kernel's lib directory.


Simpli i cant install on my alienware M17x-r2 ubuntu; imposible:confused: 

Thanks to help me

---

### Post by afbase on 2011-10-30
> **masanasj said:**
> Simpli i cant install on my alienware M17x-r2 ubuntu; imposible:confused: 

Thanks to help me

Sorry.  What is your question?

---

### Post by oldos2er on 2011-10-30
Moved to new thread.

---

