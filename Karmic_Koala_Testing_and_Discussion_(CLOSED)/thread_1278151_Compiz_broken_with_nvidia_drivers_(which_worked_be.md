---
title: "Compiz broken with nvidia drivers (which worked before)"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ernstblaauw on 2009-09-29
Hi,

This morning, I noticed Compiz was not working anymore. I have the nvidia 190.36 drivers installed (manually). [Compiz-check]("http://forlong.blogage.de/entries/pages/Compiz-Check") gives the following info:
```
$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size

```
I have the drivers installed for some time now, and earlier this driver was able to do compiz. I think the problem lies somewhere else. Do other people here have this problem?

---

### Post by alexmurray on 2009-09-29
Perhaps you should try with the current stable driver rather than the beta?

---

### Post by ernstblaauw on 2009-09-29
> **alexmurray said:**
> Perhaps you should try with the current stable driver rather than the beta?
Well, due to [this bug]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/391461"), I cannot install the driver from the Ubuntu repositories.
Furthermore, this driver has been worked correctly earlier on Karmic. I think a recent update of the kernel or Compzi has broken some thinks. Maybe [this bug report]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/437805") is related?

---

### Post by ernstblaauw on 2009-09-30
Reinstalling fixed the problem... I guess the kernel has been updated, but I did not notice. So, the problem is fixed!
I hope the previous mentioned bug is solved soon, because I don't have to install my drivers manually.

---

### Post by dinxter on 2009-09-30
thers a few ppas with the packaged nvidia 190 driver in them so avoiding manual kernel upating.

i'm using
[https://launchpad.net/~sevenmachines/+archive/nvidia]("https://launchpad.net/%7Esevenmachines/+archive/nvidia")

theres also this one with adds vdpau support to some video players as well
[https://launchpad.net/~nvidia-vdpau/+archive/ppa]("https://launchpad.net/%7Envidia-vdpau/+archive/ppa")

full list below
[https://launchpad.net/ubuntu/+ppas?name_filter=nvidia+190](https://launchpad.net/ubuntu/+ppas?name_filter=nvidia+190)

---

### Post by ernstblaauw on 2009-09-30
> **dinxter said:**
> thers a few ppas with the packaged nvidia 190 driver in them so avoiding manual kernel upating.

i'm using
[https://launchpad.net/~sevenmachines/+archive/nvidia]("https://launchpad.net/%7Esevenmachines/+archive/nvidia")

theres also this one with adds vdpau support to some video players as well
[https://launchpad.net/~nvidia-vdpau/+archive/ppa]("https://launchpad.net/%7Envidia-vdpau/+archive/ppa")

full list below
[https://launchpad.net/ubuntu/+ppas?name_filter=nvidia+190](https://launchpad.net/ubuntu/+ppas?name_filter=nvidia+190)

Thanks for those links. On Jaunty, with the 2,6,28 kernel, I already used such ppa. However, due to [this bug which describes a problem with the nvidia driver, some mobile chipsets and kernel 2.6.30+]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/391461"), I have to apply a patch to the driver before installing. So, I cannot use ppa's until this bug has been resolved (Ubuntu incorporates the patch or nvidia fixes the bug).

---

### Post by lithorus on 2009-09-30
> **ernstblaauw said:**
> Thanks for those links. On Jaunty, with the 2,6,28 kernel, I already used such ppa. However, due to [this bug which describes a problem with the nvidia driver, some mobile chipsets and kernel 2.6.30+]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/391461"), I have to apply a patch to the driver before installing. So, I cannot use ppa's until this bug has been resolved (Ubuntu incorporates the patch or nvidia fixes the bug).
You could also just include the patch through dkms...

After you have installed the ppa package and compiled the module, put in your own patch and include it. You can read up on it here :
[http://linux.dell.com/dkms/manpage.html](http://linux.dell.com/dkms/manpage.html)

Look for PATCH[#]=

It's fairly simple actually and one more reason why dkms is so lovely :)

---

### Post by dinxter on 2009-09-30
> **lithorus said:**
> You could also just include the patch through dkms...

After you have installed the ppa package and compiled the module, put in your own patch and include it. You can read up on it here :
[http://linux.dell.com/dkms/manpage.html](http://linux.dell.com/dkms/manpage.html)

Look for PATCH[#]=

It's fairly simple actually and one more reason why dkms is so lovely :)
yes dkms is very handy. the simple explanation of how to add a patch to an installed dkms package, using the 190 driver as an example.

1. copy patch to driver patches directory
$cp my_fix.patch /usr/src/nvidia-190.36/patches/

2. add patch to /usr/src/nvidia-190.36/dkms.conf by adding the line
PATCH[0]="my_fix.patch"

3. rebuild driver either using the dkms command or even easier
$dpkg-reconfigure nvidia-190-kernel-source

its that easy! (if your patch is a working one :) )

Note you can optionally use PATCH_MATCH[0] in dkms.conf to limit your patch to certain kernels using a regular expression. also note , if theres a patch already using 0, then just use a higher number for your patch

---

### Post by ernstblaauw on 2009-09-30
This is a wonderful solution!
However, I'm not sure if I can apply this to my situation. Now, I have to apply the patch with <nvidia-installer> --apply-patch <patch>. So, I guess the file does not have the patch p1 format (see attachment).

Last but not least: As the package is linked to the package nvidia-190.36, the next driver update (maybe called nvidia-190.40) won't be patched. Or am I wrong? (Of course next kernel updates before a driver update will be patched correctly.)

Hopefully, you can clarify those points :-). Thanks for the help!

---

### Post by dinxter on 2009-09-30
it looks fine but if it doesnt work,its a simple patch i'll check in in the next hour and repost, if needed patches that work with dkms 185 (karmic version) and 190.36, unless anyone would like to do that before then :)
and , yes, a new updated driver would need you to put a patch in the dkms directory for that driver, unless the update actually properly fixes the issue obviously!

[EDIT] The delay because its dinner time :)

---

### Post by dinxter on 2009-09-30
your patch applies and builds fine on 185.18.36 and 190.36, just needs all but one of the leading directories stripped out, see attachment for reference, its unchanged (thank you patch offsets! ) except for the p1 format as you mentioned

---

### Post by ernstblaauw on 2009-10-01
Thanks for all your help! I've made a simpel shell script to update the dkms.conf if a new driver is installed:
```
#!/bin/sh
for file in `ls -1 /usr/src|grep nvidia`
do
        sudo cp ./dkms_nvidiacompiz.patch /usr/src/$file/patches
        if [ `cat /usr/src/$file/dkms.conf| grep dkms_nvidiacompiz.patch|wc -l` = 0 ]
        then
                cp /usr/src/$file/dkms.conf ./tempdkms.conf
                aantalpatch=`cat ./tempdkms.conf|grep "PATCH\[" |wc -l`
                echo "PATCH[$aantalpatch]=\"dkms_nvidiacompiz.patch\"" >>  ./tempdkms.conf
                sudo cp ./tempdkms.conf /usr/src/$file/dkms.conf
                rm ./tempdkms.conf
        fi
done
sudo dpkg-reconfigure nvidia-190-kernel-source

```
Comment is welcome! (And of course, this script comes without any warranties :-) )

---

