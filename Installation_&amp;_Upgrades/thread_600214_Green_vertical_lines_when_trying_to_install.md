---
title: "Green vertical lines when trying to install"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by randizzle3000 on 2007-11-02
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/16047](https://answers.launchpad.net/ubuntu/+question/16047) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi, 3rd try to get Ubuntu to work, I never fixed the graphics problems with the the last two releases before the next one came out.

When I try to run 7.10 on my comp normally (option 1), the loading screen appears, with the orange bar bouncing left and right. Then I get a screen of vertical lines, green, red, blue, white flashy ones, etc. This stays on for hours (I left it on overnight just to test it). Option 2, Safe Graphics Mode, works beautiously. Internet, network, programs, can't read NTFS but I assume that's something I download, I just don't have any of the fun graphics effects.

When I try to add the graphics effects in the settings, Ubuntu downloads some package and installs that somewhere. Then I have to reboot. Then I start over. If I try to install from safe graphics mode, I get the vertical lines again. Any help would be appreciated. Here are my computer stats:

Ubuntu 7.10 64bit AMD Live CD

ASUS M2N32-SLI Deluxe Wireless Edition
AMD Athlon 64 (AM2) x2 4200+
2 x Corsair XMS DDR2-667 1024MB
Gigabyte GeForce 7600GT 256MB Silent

If there's more info needed let me know.

---

### Post by overdrank on 2007-11-03
> **randizzle3000 said:**
> **This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/16047](https://answers.launchpad.net/ubuntu/+question/16047) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi, 3rd try to get Ubuntu to work, I never fixed the graphics problems with the the last two releases before the next one came out.

When I try to run 7.10 on my comp normally (option 1), the loading screen appears, with the orange bar bouncing left and right. Then I get a screen of vertical lines, green, red, blue, white flashy ones, etc. This stays on for hours (I left it on overnight just to test it). Option 2, Safe Graphics Mode, works beautiously. Internet, network, programs, can't read NTFS but I assume that's something I download, I just don't have any of the fun graphics effects.

When I try to add the graphics effects in the settings, Ubuntu downloads some package and installs that somewhere. Then I have to reboot. Then I start over. If I try to install from safe graphics mode, I get the vertical lines again. Any help would be appreciated. Here are my computer stats:

Ubuntu 7.10 64bit AMD Live CD

ASUS M2N32-SLI Deluxe Wireless Edition
AMD Athlon 64 (AM2) x2 4200+
2 x Corsair XMS DDR2-667 1024MB
Gigabyte GeForce 7600GT 256MB Silent

If there's more info needed let me know.

Hi and welcome, if you can get back to the desktop, have you tried [[COLOR="Red"]Envy[/COLOR]](http://albertomilone.com/nvidia_scripts1.html )

---

### Post by randizzle3000 on 2007-11-05
I don't have anywhere to put the drivers because I'm running Ubuntu off the disc. I just can't run the Ubuntu installer. I'll give envy a shot from safe mode though.

---

### Post by bulldog on 2007-11-05
> **randizzle3000 said:**
> I don't have anywhere to put the drivers because I'm running Ubuntu off the disc. I just can't run the Ubuntu installer. I'll give envy a shot from safe mode though.

Download the alternate cd,this is a non graphical install,envy won't work from the live cd anyway.
Looking for a link :)
Here is one,tik the checkbox for the alternate cd and choose your location.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by PmDematagoda on 2007-11-05
You can get the Alternate CD from here:-

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

simply check the option to download the Alternate CD ISO at the bottom of the page and you can download it.

Edit:- Looks like both bulldog and myself got there at the same time:).

---

### Post by bulldog on 2007-11-05
> **PmDematagoda said:**
> You can get the Alternate CD from here:-

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

simply check the option to download the Alternate CD ISO at the bottom of the page and you can download it.

Edit:- Looks like both bulldog and myself got there at the same time:).

It's better to  help twice as no help at all :)

---

### Post by PmDematagoda on 2007-11-05
> **bulldog said:**
> It's better to  help twice as no help at all :)

Amen bulldog:).

---

### Post by randizzle3000 on 2007-11-05
Thanks holy shnikeys, I'll let you all know what's up later tonight. Downloading...

---

### Post by randizzle3000 on 2007-11-05
All right, text mode installed fine, booted it up, and after the Ubuntu progress bar fills up, it seems as if my video card just shut off. I get "No input signal" on my screen, then it goes to sleep. But I DID hear a logon sound or some funky tone that I think means Ubuntu is running on my system. 

I did manual partitioning because I didn't want to screw my whole hdd (Guided only does a whole disk or the first disk, which has XP on it). I put it on the second hdd (160 GB aka 149 GB) on a 36 GB partition. I made the swap as another 5 GB partition on the same hdd (didn't want to screw up my windows hdd). I left the rest of the second hddas ntfs. I wasn't sure if I should have made the ext partition bootable or not, so I just left it not bootable as the default had it. 

Grub works fine, I tried all the options and they all do what they're supposed to.

I tried recovery mode, read some man, info and help pages, but I have no idea what to type to get things working. I was going to put a youtube video of what happened but I think we all know what "No input detected" means. Thanks for the help so far, I hope we can get all the way through!

---

### Post by PmDematagoda on 2007-11-06
Can you get to a terminal by using Recovery Mode? If so, try:-

```
sudo apt-get install nvidia-glx-new

```

after installation is successful, do:-
 
```

sudo dpkg-reconfigure xserver-xorg
```

and select the driver as Nvidia, you may change other settings based on what you already know about your VGA card or monitor.

---

### Post by GEdWay Ingasia on 2007-11-06
When you install the alternativ  cd .. and it still get like that..

[http://www.youtube.com/watch?v=IS1UTJzAp7E](http://www.youtube.com/watch?v=IS1UTJzAp7E)

there is a video if you have the same problem,,

all you have to do is this:

sudo dpkg-reconfigure xserver-xorg

Choose no to auto detect grafic card (first que) and choose VESA or closest to that 

name not sure whats its called:P

and choose enter the rest of the way. get out agein and

sudo apt-get update

sudo /ect/init.d/gdm start

or kubuntu sudo /ect/init.d/kdm start

and then you will be abel to get into linux

 be sure to have network and  use terminal 

sudo apt-get install nvidia-glx-new 

ctrl + alt + backspace 

Then use

Adept Manager

find nvidia-glx-new  check if installed otherwise install and wolla...

---

### Post by randizzle3000 on 2007-11-06
[FONT=Arial]Cool thanks, I'll try it as soon as I get home tonight!

--------------later that evening...------------------------

Tried both ways, this is what I see, in general:
[/FONT][FONT=Arial]=================[/FONT][FONT=Arial]=================[/FONT]
  [FONT=Arial] Reading package lists...Done
Building dependency tree
Reading state information...Done
Suggested packages:
   nvidia-settings nvidia-new-kernel-source
The following NEW packages will be installed:
   nvidia-glx-new
0 upgraded, 1 newly installed, 0 to remove and 18 not upgraded.
Need to get 8891kB of archives.
After unpacking 26.6MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
   nvidia-glx-new
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted nvidia-glx-new 100.14.19+2.6.22.4-14.9
   Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http:/us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.22/nvidia-glx-new_100.14.19+2.6.22.4-14.9_amd64.deb Could not resolve 'us.archive.ubuntu.com'

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@Randy-Ubuntu: ~#
=================[/FONT][FONT=Arial]=================
[/FONT]
[FONT=Arial]I guess my network didn't start up. Is there a command  for that? I did the suggested apt-get update and tried --fix missing but it gave me similar things, that http:\\whatever could not be resolved, failed to download this, or that, etc. Thanks!
[/FONT]

---

### Post by randizzle3000 on 2007-11-17
HAHA ok so the power went out in my house and now Ubuntu works. I had to install all this stuff but here I am typing from Ubuntu Firefox!!! Can I bring over my winxp extensions to ubuntu firefox? Thanks everyone!!!!

---

### Post by PmDematagoda on 2007-11-17
What a weird way of solving your problem, but still, it was rather effective:D.

---

