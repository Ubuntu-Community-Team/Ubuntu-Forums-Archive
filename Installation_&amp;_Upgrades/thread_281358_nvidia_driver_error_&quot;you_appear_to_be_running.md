---
title: "nvidia driver error &quot;you appear to be running an x server&quot;"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by at0mic on 2006-10-20
trying to install the new nvidia driver that fixes the hole but getting the error You appear to be runing an X server; please exit X before installing. When I hit 'Ok' to that, I get to a next screen with the message, "Installation has failed. Please see the file '/var/log/nvidia-installer.log' for details"

changing to the telinit to 5 didnt werk for me. not much on this one yet

---

### Post by hanzomon4 on 2006-10-20
Do this... 
1.Switch to ctrl+alt+F2 
2.Kill X... Type this command ```
sudo /etc/init.d/gdm stop
```
3.Install the driver
4.Restart X... Type this command ```
sudo /etc/init.d/gdm restart
```
5.Let me know if it works

---

### Post by at0mic on 2006-10-20
thnx for ur help.

got me one step further but now it says i need the package gcc... going to do that.

---

### Post by at0mic on 2006-10-20
now it wants package make.... why wont it ask which ones it wants all at once! lol

---

### Post by at0mic on 2006-10-21
now it wants libc development package... when will it end...

this ones not as obvious. too many libc dev packs.

same prob here:
 [http://www.linuxquestions.org/questions/showthread.php?p=2417451](http://www.linuxquestions.org/questions/showthread.php?p=2417451)

said installing libc6-dev did the trick...

off i go.... not a very good intro to linux? or is it?

---

### Post by at0mic on 2006-10-21
now it says it cant find the kernel-source tree / package... good lord.

big download this one is...

---

### Post by at0mic on 2006-10-21
downloaded the source and the tree source. no good.

this problem is everywhere...

[http://www.google.ca/search?hl=en&q=source+tree+ubuntu+nvidia&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=source+tree+ubuntu+nvidia&btnG=Search&meta=)

DOes this look like the correct solution to get the latest driver with the hole fix ? can the repository version be compared to nvidia current release?

[http://ubuntuforums.org/archive/index.php/t-79568.html](http://ubuntuforums.org/archive/index.php/t-79568.html)

---

### Post by hanzomon4 on 2006-10-21
You need to install build-essentias ```
sudo apt-get install build-essential
```

And install the linux-headers for your kernel version.

---

### Post by tseliot on 2006-10-21
Try Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

or this driver from my testing repos (ONLY for DAPPER):
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by at0mic on 2006-10-21
got the build essential... it still needed more packages to do with kernel.

tried envy... WAS VERY IMPRESSED! downloaded a ton of tiny packages that were needed and then proceeded to download the actual latest 64bit driver package direct from nvidia... unfortunately at that stage i got a md5 error... twice so i lauched the one i already had downloaded and install went perfect. thanks guys!

---

### Post by franpa on 2006-10-21
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

that tells you exactly what to type... i also tried doing stuff with drivers from nvidias site but it was to painfull... it tells you how to install them and takes a couple of minutes.

---

### Post by tseliot on 2006-10-23
> **at0mic said:**
> got the build essential... it still needed more packages to do with kernel.

tried envy... WAS VERY IMPRESSED! downloaded a ton of tiny packages that were needed and then proceeded to download the actual latest 64bit driver package direct from nvidia... unfortunately at that stage i got a md5 error... twice so i lauched the one i already had downloaded and install went perfect. thanks guys!

my bad. I'll fix it soon

---

### Post by tseliot on 2006-10-23
Ok, it's fixed now

---

### Post by accel on 2006-11-13
The Bleeding Edge drivers (9626)for my nVidia GeForce 6800XT works great!
I've used your repository for it, perfect.
In SUSE there was a NVidia control panel called "NVIDIA X Server Settings"
In Edgy I can't find this anymore, can you tell me where I can find this.
TIA!

---

### Post by at0mic on 2006-11-13
hi,

its in the regular menu. the one on the farthest left under system stuff.

---

### Post by magickmoon on 2006-12-15
Hi, my first post here. I found this posting from google, looking for a fix for nvidia fx5700 AGP card that came with my system. Thanks for all the ones before me, mainly atOmic, who had to do this first but especially to that great Italian Alberto who makes configuring the card so easy. It's an excellent work and the graphics are now incredible :KS :KS :KS :KS :KS 
 [http://albertomilone.com/index.html](http://albertomilone.com/index.html) 

I got sick of windoze and love the new system of ubuntu is how I got started, sound familiar? lol

---

