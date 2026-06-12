---
title: "Latest NVidia driver installed, yet can't change resolution"
date: 2017-01-07
forum: Installation &amp; Upgrades
---

### Post by ubuntini2 on 2017-01-07
Hi
New ubuntu-mate 16.04 install and have installed the latest nVidia driver via Software7Updates using this ppa [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu)

Under Software & Updates > Other Drivers I see
> 
Using NVIDIA binary driver -  version 375.26 from nvidia-375 (open source)

But under System > Preferences > Hardware > Displays  my monitor is unknown and at a low resolution which can't be changed

A quick google brings me to this page which recommends installing the nVidia driver thru the command line
[https://linuxconfig.org/how-to-install-the-latest-nvidia-drivers-on-ubuntu-16-04-xenial-xerus](https://linuxconfig.org/how-to-install-the-latest-nvidia-drivers-on-ubuntu-16-04-xenial-xerus)

But I am reluctant, since almost ALL my linux problems have been related to nVidia drivers.

Any driver experts able to offer some help here?

If I run
```
$ lspci -vnn | grep VGA
```
I get
[HTML]01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1b00] (rev a1) (prog-if 00 [VGA controller])

[/HTML]

---

### Post by pablosquared on 2017-01-08
I had a smiilar problem when running 15.10 - the smaller of my 2 monitors wouldn't go above a fairly low resolution, even though it was capable of higher - setting the resolution in nVidia settings wouldn't work, not could I change it in system settings. Upgrading to 16.04 fixed it for me. I suspect something to do with xorg but I could never fix it, even by adding new resolutions in xrandr. Have a look here though, might be of some use.

[URL="http://unix.stackexchange.com/questions/227876/how-to-set-custom-resolution-using-xrandr-when-the-resolution-is-not-available-i"]http://unix.stackexchange.com/questions/227876/how-to-set-custom-resolution-using-xrandr-when-the-resolution-is-not-available-i
[/URL]
[https://www.bonusbits.com/wiki/HowTo:Add_Missing_or_Custom_Display_Resolution_on_Ubuntu](https://www.bonusbits.com/wiki/HowTo:Add_Missing_or_Custom_Display_Resolution_on_Ubuntu)

---

### Post by efflandt on 2017-01-08
I wonder why lspci does not show the model of your Titan X (or doesn't mate do that?). For example:```
$ lspci -vnn | grep VGA
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP106 [GeForce GTX 1060 3GB] [10de:1c02] (rev a1) (prog-if 00 [VGA controller])
```What type of cable is your monitor connected with and what is its native resolution?

Look through /var/log/Xorg.0.log for any clues of issues.

---

