---
title: "Nvidia Drivers"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by lilu_lilis on 2007-11-30
Hello there, i am a quite new user in Ubuntu and in Linux in general. I recently installed the last version of it Gutsy Gibbon. I also have an NVidia 8500GT card, which i have installed through the restricted hardware manager and it works just fine.

Is there any other method to istall a graphic driver? Can we download and install the drivers from the nvidia site and if yes how? Is there a howto for doing this? And is it safe?

---

### Post by Mze on 2007-11-30
Installing Nvidia drivers: [forum thread]("http://ubuntuforums.org/showthread.php?t=139264")

---

### Post by chewearn on 2007-11-30
If there is no burning need to get the latest nvidia driver, I suggest you keep as it is.

The nividia driver in the ubuntu repository is quite recent (current nvidia-glx-new version is 100.14.19):
[http://packages.ubuntu.com/gutsy/misc/nvidia-glx-new](http://packages.ubuntu.com/gutsy/misc/nvidia-glx-new)

Just last weekend, I install nvidia driver (via envy, see below).  The version I got was 100.14.23; only slightly newer that what we have in the repository.

If you really must have the latest driver, then I recommend using envy:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Pumalite on 2007-11-30
For 8600-8800 GT 

When grub comes up select the second ubuntu option. 

When its finished you should now have a terminal. 

login 

run sudo passwd 

setup your 'root' password 

now run 

sudo apt-get install nvidia-glx-new 

sudo nvidia-xconfig 

sudo shutdown -r now 

Then use the normal option to boot ubuntu. 


Hopefully you'll have an xserver

---

