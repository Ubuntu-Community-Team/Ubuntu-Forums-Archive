---
title: "Video driver problems"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by JoeWheeler on 2010-04-23
I upgraded to 10.04 via update manaer and now my compiz is broken, I go to visual effects in appearances but whenever I click any of the options it says "searching for drivers". The screen then flickers for a few seconds and it says "desktop effects could not be enabled".

Im using an ibm x40 thinkpad

---

### Post by BrokeMahPC on 2010-04-23
Can we have info about your hardware and driver, please type these in a terminal:
     Code:
     ```
lspci | grep VGA 
```     Code:
     ```
sudo lshw -C video 
```The 2nd command also lists the driver you are using under  configuration. Please post the outputs.

It will be intel graphics of some kind.

---

### Post by JoeWheeler on 2010-04-23
> **BrokeMahPC said:**
> Can we have info about your hardware and driver, please type these in a terminal:
     Code:
     ```
lspci | grep VGA 
```     Code:
     ```
sudo lshw -C video 
```The 2nd command also lists the driver you are using under  configuration. Please post the outputs.
I've done a fresh install and the problems still there. I think it's something to do with the intel video drivers

This is the first command: 
```
VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```This is the second(although ive had to boot in failsafe and i dont know if that affects it):
```
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:e0000000-e7ffffff(prefetchable) memory:d0000000-d007ffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
       resources: memory:e8000000-efffffff(prefetchable) memory:d0080000-d00fffff

```

---

### Post by BrokeMahPC on 2010-04-23
Found this mentioned here:
[https://wiki.ubuntu.com/X/Drivers](https://wiki.ubuntu.com/X/Drivers)
About intel drivers under Lucid
> For the older **8xx** cards, upstream support has been  spotty, and there have been numerous bugs reported.  Our primary  objective is to give users a stable out-of-the-box experience, so this  means turning off features (including KMS and 3D) to minimize the  frequency of the problems.  Part of the problem (both in Ubuntu and  upstream) has been lack of hardware for testing.  We're a bit worried  that some hardware is so obscure that no one is testing it, and issues  will only become visible post-release. Is 3D turned off by default for your 8xx card? Is it therefore possible to enable it?
Can I also have the output of this:
```
cat /etc/X11/xorg.conf
```
should tell us what modules it is loading

---

### Post by JoeWheeler on 2010-04-23
> **BrokeMahPC said:**
> Found this mentioned here:
[https://wiki.ubuntu.com/X/Drivers](https://wiki.ubuntu.com/X/Drivers)
About intel drivers under Lucid
Is 3D turned off by default for your 8xx card? Is it therefore possible to enable it?
Can I also have the output of this:
```
cat /etc/X11/xorg.conf
```should tell us what modules it is loading
Im not sure about 3d being turned off by default

```
cat: /etc/X11/xorg.conf: No such file or directory

```

---

### Post by BrokeMahPC on 2010-04-23
That is probably normal as you don't always need an xorg.conf. 
I am at my limits with this, I'm an ATI man, but try this troubleshooting guide:
[https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance)
The part on "falling back to opengl sofware rendering"
You will find there is some problem with glx or that 3d rendering is disabled for your card and/or it isn't loading the correct modules.
try:
```
glxinfo | grep render
```
as it suggests and have a look at this web page:
[http://ubuntuforums.org/archive/index.php/t-97317.html](http://ubuntuforums.org/archive/index.php/t-97317.html)
It's old but likely to be the same problem - good luck!

---

### Post by JoeWheeler on 2010-04-23
Thanks for all your help!

Ill try following those guides

Edit: Well I can't get it working so I guess I'll just stick with it in failsafe for a few weeks and if it's not fixed by then I'll just have to switch distro

---

### Post by BrokeMahPC on 2010-04-23
To get more info try this:
Install hwinfo:
```
sudo apt-get hwinfo
```
then:
```
hwinfo --gfxcard
```

May be something in that output that can help - post that too.

usefull tool for getting all sorts of hardware info see:
```
man hwinfo
```
for the many options

---

### Post by davidmohammed on 2010-04-23
Intel drivers for your card 855GM are broken - this is the same situation for most of the new distros out.  Its going to take weeks to get this fixed.

I've  got the same card in my laptop.  This is what I've done to get a working solution:

make sure you boot with i915.modeset=1 in your grub.

download and install the xserver-xorg-video-intel_2.9.1-3ubuntu1_i386.deb  package from [this link]("https://launchpad.net/ubuntu/+archive/primary/+sourcepub/1015446/+listing-archive-extra").  

This is an older package than the current driver.  When you use update-manager remember to deselect the offer to upgrade to the newer driver.

---

### Post by JoeWheeler on 2010-04-23
Well I've downloaded the deb but im not sure how i can uninstall the new xorg to install that one without screwing things up?

---

### Post by glasen on 2010-04-23
You can also try a newer version of the intel-driver :

```
sudo add-apt-repository ppa:glasen/libdrm
sudo add-apt-repository ppa:glasen/intel-driver
sudo apt-get update
sudo apt-get upgrade
```

**Warning :**

You must activate KMS. Otherwise the driver will not work! There is no non-KMS-mode (aka UMS-mode) since driver-version 2.10!

You can activate KMS by adding the line "i915.modeset=1" to GRUB2 or by editing/generating the file "/etc/modprobe/i915.modeset=1" and changing/adding the following line :

```
options i915 modeset=1
```

---

### Post by JoeWheeler on 2010-04-23
> **glasen said:**
> You can also try a newer version of the intel-driver :

```
sudo add-apt-repository ppa:glasen/libdrm
sudo add-apt-repository ppa:glasen/intel-driver
sudo apt-get update
sudo apt-get upgrade
```**Warning :**

You must activate KMS. Otherwise the driver will not work! There is no non-KMS-mode (aka UMS-mode) since driver-version 2.10!

You can activate KMS by adding the line "i915.modeset=1" to GRUB2 
where do i put i915.modeset=1 in my grub file?

---

### Post by glasen on 2010-04-23
You must edit the file "/etc/default/grub". Just add the option to the line "GRUB_CMDLINE_LINUX". After this you must execute "sudo update-grub" to apply the changes.

---

### Post by davidmohammed on 2010-04-23
> **davidmohammed said:**
> Intel drivers for your card 855GM are broken - this is the same situation for most of the new distros out.  Its going to take weeks to get this fixed.

I've  got the same card in my laptop.  This is what I've done to get a working solution:

make sure you boot with i915.modeset=1 in your grub.

download and install the xserver-xorg-video-intel_2.9.1-3ubuntu1_i386.deb  package from [this link]("https://launchpad.net/ubuntu/+archive/primary/+sourcepub/1015446/+listing-archive-extra").  

This is an older package than the current driver.  When you use update-manager remember to deselect the offer to upgrade to the newer driver.
you can install the above package via

sudo dpkg -i intel_2.9.1-3ubuntu1_i386.deb

to edit your grub

gksudo gedit /etc/default/grub


then make sure the following line looks something like
GRUB_CMDLINE_LINUX="i915.modeset=1"

finally update grub

sudo update-grub

---

### Post by JoeWheeler on 2010-04-23
Hmmm, enabling the i915.modeset=1 option has allowed me to boot but without desktop effects, 
Oh well, just have to cross my fingers that this'll get sorted in a future update

---

### Post by davidmohammed on 2010-04-23
you need to either downgrade your intel driver as I have described, or upgrade the driver via the glasen ppa.

If you dont do either of the above you cannot have compiz effects etc.

---

### Post by JoeWheeler on 2010-04-23
Ah I managed to dowgrade, and it's all good, thank you davidmohammed!

---

