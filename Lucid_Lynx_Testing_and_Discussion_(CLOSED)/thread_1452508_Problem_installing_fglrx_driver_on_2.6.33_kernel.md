---
title: "Problem installing fglrx driver on 2.6.33 kernel"
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-04-12
i have posted here a bug report:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/560759](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/560759)

according to what it said there it's a problem with headers but i did installed headers
as i said there i installed all three files:
linux-headers-2.6.33-020633_2.6.33-020633_all.deb
linux-image-2.6.33-020633-generic_2.6.33-020633_i386.deb
linux-source-2.6.33_2.6.33-020633_all.deb


in any case i now understand that there is a new version 2.6.33.2 i downloaded the file 

linux-2.6.33.2.tar.bz2 and the file patch-2.6.33.2.bz2 but i'm not sure how to install either of them how can i do that?


and are there new debs files for the new versions some where?


thanks in advance.

---

### Post by fluteflute on 2010-04-12
Ubuntu is using 2.6.32 for Lucid, and will not support 2.6.33

---

### Post by aviramof on 2010-04-12
in any case it should support 33 and by the way i can't get compiz to work in latest 32 now any ideas as to why?

and how can i install the 33 using linux-2.6.33.2.tar.bz2 or are there any debs file out there of this new version?

---

### Post by fluteflute on 2010-04-12
I wouldn't recommend trying to install 2.6.33 unless you have a specific reason to?

---

### Post by aviramof on 2010-04-12
this annoying unknown screen is one reason two kernel 33 don't have that annoying white line at boot process at the top of the screen and basicly he's more stable then 32 who continues to release new kernels all the time.

---

### Post by dino99 on 2010-04-12
i've tried to install 2.6.33-020633-generic, but it fail with kms and update-manager uninstall other nvidia drivers. The problem is known and we will have a new jockey package soon (already released).

---

### Post by aviramof on 2010-04-12
thanks i'm hopping that it would help and by the way to you know how to install the 2.6.33.2 kernel for the 2.6.33 i use debs file but for 33.2 i need to use the source and i am heaving problems installing it.

---

### Post by lukeiamyourfather on 2010-04-12
Its kind of a moot point if you're using something newer than Ubuntu 9.10 because the fglrx driver doesn't support the latest X.org Server (yet).

---

### Post by aviramof on 2010-04-12
@dino99 i just updated jocky and it still not working i still can't install fglrx driver from /usr/bin/jockey-gtk maybe in a few hours there would be an update it would work better.

@lukeiamyourfather in kernel 32 this driver is working i have compiz for instance but it freezes from time to time i have a problem with unknown screen and with catalyst asking me to restart just for dual view and then it doesn't work at all so i know it can take some time for it to fix everything but for the moment i just want it to work in 2.6.33 as good as 
in 2.6.32 and the chances are that once i could install it in 2.6.33 that it would work much better then in 2.6.32

in any case i downloaded linux-2.6.33.2.tar.bz2 and patch-2.6.33.1.bz2 patch-2.6.33.2.bz2 how can i use them to update my current kernel?

thanks in advance.

---

### Post by glasen on 2010-04-12
If you've never compiled a kernel by yourself then you should read the following URLs :

[http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html](http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html)
[http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835)

Compiling your own kernel is normally not necessary, unless you need some special patches (e.g.  Linux-PHC, BFS-Scheduler). The kernel-packages in the Ubuntu-mainline-archive should work perfectly for 99% of all users :

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33)

---

### Post by aviramof on 2010-04-12
thanks for the info.

i still have a problem with fglrx and jockey in 2.6.33

---

### Post by aviramof on 2010-04-12
and by the way nice going 2.6.32-20 i barely did anything and i mean anything when i restarted last time everything was fine and i only installed it a few hours ago and now it stopped working all i get is a blue bright line at the top of the screen and it doesn't work 2.6.33 is still working so now you wonder why i use 2.6.33 and not 2.6.32.:)

---

### Post by BrokeMahPC on 2010-04-12
What hardware do you have?

I am using 2.6.32-20 and FGLRX and have no problems. Check your video card is supported by the drivers - older cards are not. I would be cautious of using unsupported kernels - you might not get all the updates.
ATI Radeon HD 4670
ATI proprietary fglrx driver

I installed the above driver with System - Admin - Hardware Drivers.
Did you do this after activating the driver?
```
sudo aticonfig --initial -f
```

Then reboot?
```
sudo reboot
```

---

### Post by aviramof on 2010-04-12
my screen card is hd3650 agp shappire 512mb ddr2 it should be supported and as for the 
kernel i just installed 2.6.32-20 today and he didn't last even a day before he crashed when i last restarted he was fine compiz fglrx all was fine but then he didn't wanted to boot again so i removed it completly now maybe i'll install it again later but i don't think 2.6.32 kernels are very stable right now but gflrx does work there my only problem now with 2.6.33 that i can't install the driver via jockey it has some sort of error that you can see 
in the bug report i posted in the attached jockey.log file so i don't have compiz and every mouse movement refresh the entire screen.

your command didn't helped by the way:
```
Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

---

### Post by BrokeMahPC on 2010-04-12
In theory your card is supported as the Catalyst driver supports the HD3650. Your xorg.conf looks fine - the card appears configured properly.  You have the AGP model tho - the AGP model of the HD3650 is? / was very buggy and had many driver problems did it work ok with Windows? Other Ubuntu versions? see this - read the reviews: [http://www.newegg.com/Product/ProductReview.aspx?Item=14-102-762&SortField=0&SummaryType=0&Pagesize=10&SelectedRating=-1&PurchaseMark=&VideoOnlyMark=False&VendorMark=&Page=1&Keywords=%28keywords%29](http://www.newegg.com/Product/ProductReview.aspx?Item=14-102-762&SortField=0&SummaryType=0&Pagesize=10&SelectedRating=-1&PurchaseMark=&VideoOnlyMark=False&VendorMark=&Page=1&Keywords=%28keywords%29)  How much RAM do you have - this card requires 1GB plus. How is your PSU - 500w plus?  Hope you solve it - this is all I know.

---

### Post by BrokeMahPC on 2010-04-12
Just to check - what does this do, code: 
```
fglrxinfo
```

should give something like this:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4600 Series
OpenGL version string: 3.2.9756 Compatibility Profile Context
```

---

### Post by aviramof on 2010-04-12
this card is working fine with windows xp seven and 2008 and he worked fine with ubuntu 8.10 9.04 and 9.10 and resonably well with 10.04 2.6.32-19 and 2.6.32-20 but the kernel  20 itself is not so good i only installed it several ago and it already crashed and i had to enter to 2.6.33 and remove 2.6.32 here are the results of fglrxinfo in 2.6.33

```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  156 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  15

```so fgrlrx is not working so well with 2.6.33 for now and by the i have 2GB DDR2 800MHZ and 500W PSU so this is not the problem.

---

### Post by BrokeMahPC on 2010-04-12
Well something isn't right somewhere! The fglrxinfo is wrong.

---

### Post by aviramof on 2010-04-12
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/560759](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/560759)

i am fully aware of it any time i move the wheel of the mouse it refresh the entire screen and i have no compiz and most likely movies want work so well here.

---

### Post by BrokeMahPC on 2010-04-12
I went back to your bug report and looked at your jockey.log. Although you did attempt to install the linux headers - something went wrong and the install process aborted. The log has many "aborted" messages refering to linux headers - some shown below.

The FGLRX driver requires the linux headers to be installed or it will not work properly. It states this in the release notes. Go back and try again?
I would read the FGLRX release notes and make sure everything it requires is installed.

> 2010-04-11 20:57:51,119 DEBUG: Installing package: linux-headers-2.6.33-020633-generic 2010-04-11 20:57:51,503 DEBUG: Package linux-headers-2.6.33-020633-generic does not exist, aborting  > 2010-04-11 21:02:21,294 DEBUG: Installing package: linux-headers-2.6.33-020633-generic 2010-04-11 21:02:21,712 DEBUG: Package linux-headers-2.6.33-020633-generic does not exist, aborting 2010-04-11 21:02:22,146 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx 

---

### Post by aviramof on 2010-04-12
i tried to reinstall the headers several times today and when i do it does not show any problem is said install is finishe and i can choose to reinstall again just like any other deb.

i tried to reinstall all three debs:
linux-headers-2.6.33-020633_2.6.33-020633_all.deb
linux-image-2.6.33-020633-generic_2.6.33-020633_i386.deb
linux-source-2.6.33_2.6.33-020633_all.deb

and it didn't helped.

i thought maybe installing 2.6.33.2 would help but i have not been able to understand how to install it from source.
i downloaded linux-2.6.33.2.tar.bz2 and this two patches patch-2.6.33.1.bz2 patch-2.6.33.2.bz2 how can i use them to update the kernel and it's headers

---

### Post by moviemaniac on 2010-04-12
I guess the problem lies somehwere within the fglrx install-scripts for Ubuntu which may be custom tailored to fit Ubuntu's standard -32 kernel. I'm running on 2.6.34-rc3 here (self-compiled as I normally do to perfectly fit my machines and needs) and I can't install fglrx either because of the installer complaining about missing headers - which by the way are installed correctly (so is source-package) as other kernel modules like virtualbox can be built...

---

### Post by aviramof on 2010-04-12
well i'm hopping that they would fix it soon or some other solution be released because i'm sure there are a lot of people with ati cards and unsupported kernels.

---

### Post by BrokeMahPC on 2010-04-12
Why not just use 2.6.32-20 like everyone suggests? Someone has responded to you in another thread saying they are using the same graphics card as you and it's working fine in 2.6.32-20.
At the moment it's only you that is having this problem.

look at your bug:
[https://bugs.launchpad.net/ubuntu/+s...er/+bug/560759]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/560759")
Bug only affects 1 person

---

### Post by aviramof on 2010-04-12
first of all 2.6.32-20 is not good kernel you can see that he was pulled from synaptic and it was reported in chroot as a staf member wrote in one of my other threads and the fact is that 2.6.32 kernels are still not so stable this 20 kernel crashed for me today after just a few hours lucky i had 33 installed or i would have to format again maybe when they release the next one i would try it.

and my bug don't effect just me take a look at moviemaniac reply in this thread and it's a new bug so it could take some time before people would reply to it.

---

### Post by BrokeMahPC on 2010-04-12
Yes, I agree some people have had problems with 2.6.32-20
Did you have any problems with:
2.6.32-16
2.6.32-17
2.6.32-18
2.6.32-19

If not, why jump to an unsupported kernel just because of 20? If it were me I would revert to 19 while they fix the problem and wait till 21? Going to 2.6.33-xx just creates additional problems as FGLRX isn't supported. Your logic doesn't follow?

---

### Post by moviemaniac on 2010-04-12
> **aviramof said:**
> and my bug don't effect just me take a look at moviemaniac reply in this thread and it's a new bug so it could take some time before people would reply to it.

Well, I don't really see this as a bug in Ubuntu. The fglrx installer works for the kernels officially supplied by Ubuntu for use with Lucid Lynx and that's what really matters. If the package doesn't install on kernels it's not made for that's, well, not so cool but also to be expected. It would be great if it worked but we can't hold the Ubuntu devs responsible if something doesn't work for a job it's not designed for. If you need fglrx then I suggest you wait for a few weeks until Catalyst 10.4 officially arrives from ATI with (hopefully) support for the -33 kernel series.
By the way: If you don't play games on your machine then I'd suggest using the open source drivers and not the proprietary ones (unless you're on R800 hardware...)

//edit: I guess the best way for you to handle the problem would be to file bugreports against the fglrx-driver and possibly the kernel lucid is using. That'd be more effective than trying to get fglrx to run on an unsupported kernel ;)

---

### Post by aviramof on 2010-04-13
i didn't try 2.6.32-16 2.6.32-17 2.6.32-18 but 2.6.32-19 works fine but i already removed it thinking that 2.6.32-20 is fine and i didn't jumped to 2.6.33 i used it all this time with xorg not fglrx and because 2.6.33 is a stable kernel it's also a good backup from all the 2.6.32 kernels who are maybe supported but unstable it did save my ubuntu from the 2.6.32-20 as you can see for your self.

the only problem i now have with him is the fglrx driver that basicly should support all kernels in the end.

---

### Post by questioning on 2010-04-13
fglrx only supports 2.6.32

so, try to find a patch to make it work on higher kernels, ubuntu cant help you with that.

---

### Post by moviemaniac on 2010-04-13
look if you still have the debs for 2.6.32-19 in your /var/cache/apt/archive and reinstall them if -19 worked for you.

---

### Post by aviramof on 2010-04-13
i already installed 2.6.32-20 again today and it's working fine except maybe a problem with plymoute i had in this thread:
[http://ubuntuforums.org/showthread.php?t=1453275](http://ubuntuforums.org/showthread.php?t=1453275)

and again i had to save it using 2.6.33 kernel which as far as i know don't have problems with plymoute.

---

