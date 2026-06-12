---
title: "Please help restoring nvidia dual monitor after upgrade to feisty"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by plong0 on 2008-01-12
So I finally decided to update to feisty, kept putting it off because of the hassles I was sure to encounter. 

I started by installing all the updates in synaptic, minus the nvidia ones (nvidia, nvidia-glx) because I installed them manually and anytime I update them with package manager my xorg.conf becomes invalid.

After all those, I go into the Update Manager and click the Upgrade Distribution button and let it go though it's little process of downloading and installing everything.

Then I restart and cross my fingers that it boots... which of course it doesn't.

I get an error when xserver is starting up saying my Xorg.conf is looking for a newer version of nvidia drivers than I have installed.

Right now I'm at the point where I can't get to a login screen on that one... I was getting it to crash xserver to give me a console login, but now it's not even doing that... it hangs between the time I press No don't view detailed error log and giving me the console.

The good news is, my machine is dual booted, so I can easily use my ubuntustudio setup to modify any config files on my new feisty setup.  Anyone up to the challenge of helping?  Or any pointers would be nice on even just getting to my console login so I can try reinstalling the nvidia drivers.

I'm at a point now where I'm tired and stressed out from looking through posts trying this and that to no avail.  I just want my computer to work again.

Thanks!

---

### Post by Partyboi2 on 2008-01-12
have you tried to fix xserver by booting into recovery?
or
If you can get to a terminal  (Ctrl+Alt+F1-F6) try reconfiguring the xserver and select "nv" driver 
```
sudo dpkg-reconfigure xserver-xorg
```If you have never done it before just choose the default settings if unsure.
then 
```
startx
```

---

### Post by plong0 on 2008-01-12
hi

Thanks for the reply.  I was able to boot into recovery mode and reconfigure xserver, but still it does not work.

I think now that I can access a terminal, I am just going to get the newest nvidia drivers and make an attempt at following one of the guides for setting up dual screens with it.  I doubt it'll work, but I don't know what else to try right now.

---

### Post by plong0 on 2008-01-12
ok..,. I am having absolutely no luck with this. nothing works. I can't boot xserver no matter what I do. I can reconfig it all I want but it's always some error or another... can't find a screen (even though it is correctly configured) or the nvidia driver version is different from the xserver driver version...  this is really frustrating and annoying when all I want to do is be able to use my computer.

I tried downloading the binary installer off nvidia's website, but like that would install without hassles (can't find the kernel-source, so I point the --kernel-source-path to /usr/src/linux-headers-2.6.20-16  .... of course it doesn't work though. it gets past the part saying it can't find the kernel source but then just ends with an error saying it can't compile the driver.

anyone have any advice what I can do?  I'm thinkin about getting a new hard drive and starting from scratch, but I really don't want to have to do that right now.

---

### Post by PmDematagoda on 2008-01-12
Install the following before installing the driver:-
```
sudo apt-get install build-essential
```

After that is installed, try running the Nvidia installer again.

---

### Post by plong0 on 2008-01-13
Thanks for the reply PmDematagoda... I tried installing build-essential, but apt-get says it's already installed and the latest version.  Anything else I might try?

edit:
note about when I run the NVIDIA installer with --kernel-source-path=/usr/src/linux-headers-2.6.20-16

it gets to 100% on the Building Kernel Module screen, then reports ERROR: unable to build the NVIDIA kernel module

upon inspection of the log file, I see:
> ERROR: Kernel configuration is invalid
include/linux/autoconf.h or include/config/auto.conf are missing
Run make oldconfig && make prepare on kernel src to fix it

I just realized that when I run 
> uname -r
2.6.17-12-386
  ... I'm thinkin that should probably match the 2.6.20-16 on the linux-headers... this means my kernel is old right?  shouldn't apt-get upgrade get the latest version for me?

another note related to the versions, I just tried 
> sudo apt-get install linux-headers-`uname -r` 
...
Couldn't find package linux-headers-2.6.17-12-386

Or maybe I'm just trying to get the wrong thing entirely?

---

### Post by plong0 on 2008-01-13
Friends! I am stoked to report a miracle has occurred!!
I updated my kernel and everything works!

After I thought about it some more I decided that I needed to update my kernel because it didn't make sense that it was 2.6.17 and the sources I just got were 2.6.20, and also my more recently installed fesity ubuntustudio runs 2.6.20... probably wasn't thinking clearly out of frustration and not feeling well

So I start looking into upgrading my kernel and found a couple guides, run the magic command...
> sudo apt-get install linux linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic
I was skeptical thinking that it would say all those were installed and the latest version, but it actually asked if I wanted to install, I enter in 'y' and let it go.

Then I was sure to check my /boot/grub/menu.lst because I knew it was probably modified... sure enough it was and it looked like all the options were pointing at my ubuntustudio drive... so I restore it to my saved custom menu.lst and manually update the kernel version for my main ubuntu entry... cross my fingers and reboot.  Next thing I know it's booted to the gui login screen which appears to have a feisty new polish on it.

After updating the kernel I was half expecting to have to reinstall the nvidia drivers... apparently I didn't have to... guess that new version of X just didn't like my old kernel or something.  But anyway, I am really happy it's working now and appreciate the tips people posted to help out.

---

