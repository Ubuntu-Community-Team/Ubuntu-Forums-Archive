---
title: "I Just Want Nvidia Drivers"
date: 2007-03-11
forum: Installation &amp; Upgrades
---

### Post by qbical on 2007-03-11
so my book tells me to type @ the prompt $ sudo apt-get nvidia-glx nvidia-settings
and it responds to me E: invalid operation nvidia-glx
i just found a thread that told me to install nvidia-glx-dev in the synaptic packet manager, so i did that and then had to type this $ sudo nvidia-xconfig 
it did some stuff, seemed all good and restarted. after the reboot I STILL didnt see any nvidia stuff. 
now im just getting pissed off, i followed my book step by step as well as online help and still havent goten crap to work yet. can someone please help me b4 i just totally ditch this OS
thanks

---

### Post by x64Jimbo on 2007-03-11
Your book is missing a very crucial part of the software installation command. However, it's much easier to use Synaptic to install things on your system. 
System > Administration > Synaptic Package Manager
type in your password, then search for the word "nvidia"
You should see a list of packages appear, and two of them will be the ones you're looking for. Simply right click on them and mark them for installation, then hit the Apply button.
Ok, then you shouldn't necessarily see any "nVidia stuff" since it doesn't install it in a place where you can see it. The way you can tell if the drivers are working is to run the following command: 
glxgears -printfps
This will run a small 3D test. If your FPS is anywhere below 500, you're probably not running the 3D drivers. Otherwise, it's probably good to go.

---

### Post by yabbadabbadont on 2007-03-11
Should have been: sudo apt-get **install** nvidia-glx

---

### Post by x64Jimbo on 2007-03-12
> **yabbadabbadont said:**
> Should have been: sudo apt-get **install** nvidia-glx
I recommend using aptitude rather than apt-get because it has better dependency management.

---

