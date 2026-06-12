---
title: "Installing NVIDIA dev drivers."
date: 2011-08-19
forum: Installation &amp; Upgrades
---

### Post by jatoo on 2011-08-19
Hi all,

I'm currently trying to install the latest NVIDIA dev drivers (270) but i'm running into problems.  

Basically it installs ok, and then if i restart X everything works until i restart the computer, then i have to install it all over again.  There seems to still be references to the old driver after i install the new one.  

Here are the details:
[LIST=1]
[*] Go to a terminal and make sure gdm is not running.
[*] Run the nvidia installer (devdriver_4.0_linux_64_270.41.19.run) as root.  I accept all the options, update xorg.conf etc.
[*] Start X with ```
sudo service gdm start
```
[*] Everything seems to be working fine! (CUDA programs run ok)
[*] Restart the system - X fails to start, it goes tty1 (with a bit of a flicker of the screen)
[*] It appears a process called "gdm-binary" is running.
[*] ctrl+alt F7 or F8 result in just a cursor. 
[*] ```
sudo gdm restart
``` gives:
 ```
** (gdm-binary:1578): WARNING **: Failed to acquire org.gnome.DisplayManager

** (gdm-binary:1578): WARNING **: Could not acquire name; bailing out
```
and i'm back to my prompt. 
```
sudo gdm restart
``` has the same result.
So basically, i can't get an X session going. 

[*] If i kill gdm-binary, and then run ```
sudo service gdm start
``` the screen flickers and nothing else happens.  
[*]**BUT if i kill gdm-binary, and then run **```
sudo startx
```** i get a lot of output including: **
```
Error: API mismatch: the NVIDIA kernel module has version 260.19.06,
but this NVIDIA driver component has version 270.41.19.  Please make 
sure that the kernel module and all NVIDIA driver components 
have the same version.
```

So it seems like something about the installer isn't really working.  I don't really know anything about kernel modules, i'm just going by the fact that it still has a reference to version 260 in there.

[*] At this point, i can repeat it all again (i.e., i can reinstall the driver, and then get into a gdm session, but when i restart it's once again broken.

[/LIST]

Any help would be greatly appreciated!

---

### Post by zero244 on 2011-08-19
Have you updated your kernel after installing the drivers.
Sometimes after doing the binary install a kernel upgrade will break them.
I installed the same drivers as you did and they worked fine.
Based on your post I would say you did everything right.

---

### Post by jatoo on 2011-08-19
Nope, updated to the latest kernel, then installed the drivers (multiple times).

---

### Post by Hakunka-Matata on 2011-08-19
System > Administration > Additional drivers doesn't do that automatically?   Excuse if I'm being too simplistic, or missed something here.  But that works for me on NVidia machines.

---

### Post by jatoo on 2011-08-19
Hi Hakunka-Matata,

If i use that method, then everything works, but i don't have a new enough version of the driver to use CUDA.  That gets me version 260 of the driver, and CUDA needs 270.

---

### Post by cbowman57 on 2011-08-19
Haven't tried the smxi script on Ubuntu, should work fine. [http://smxi.org/site/install.htm](http://smxi.org/site/install.htm)

It does a great job of cleaning up prior to video driver installations.  If you choose current it will pull in 280.13, beta is 285.03.  They should both work with CUDA.

---

### Post by Duncan Williams on 2011-08-19
270 should be in standard repository.
280 is in unofficial repository:
Ubuntu-X-Swat PPA

This PPA is basically only providing updated proprietary Nvidia and ATI/AMD drivers, and since Natty Narwhal in fact restricted to them. If you are using a prop. driver, this PPA is -at least as of now- the best choice, and it also shouldn't break your system or reduce the performance of the used driver.

To upgrade using this PPA, run these commands in the Terminal:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade

If you need/want to remove those PPA and downgrade the concerning packages again, run these:

sudo apt-get install ppa-purge
sudo ppa-purge ppa:ubuntu-x-swat/x-updates

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

