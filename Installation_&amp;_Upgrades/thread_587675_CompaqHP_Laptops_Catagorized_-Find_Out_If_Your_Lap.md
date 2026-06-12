---
title: "Compaq/HP Laptops Catagorized -Find Out If Your Laptop Likes Gutsy!"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by BoardDWorld on 2007-10-22
There are many that are not finding the transition to Gutsy at all easy with unresolved and critical issues. There are those like myself that found it very straight forward and problem free. 

[COLOR="Red"]Please note that many problems are caused by upgrading rather than a fresh install.[/COLOR]

I have made this thread to simply gather the various models and categorize them according to everyones experience. Please note you may find your model in 2 sections as everyones experience is different. As mentioned previously it will highly depends on whether they did an upgrade (which I never do) or if they installed a fresh copy.

**Installs Well:**
_HP_
DV2000T
DV4000
DV6017EA
DV6324
DV6426
DV8000 (3 reports of it working perfectly)
DV9224TX
DV9207US
ZE4500
ZE4600
ZX5000


_Compaq_
6710B (1 report of it working perfectly)
NX6125
V2000 -Slow Booting


**Installs Well, minor issues to resolve:**
_HP_
DV2000 -No Sound, known fix by starting laptop without mains power (1 report of this problem).
DV6000 -No Sound
DV8000 -Broadcom won't work with ndiswrapper. (1 report of this problem)
ZV6000 -Prolonged boot times, Boot Splash missing 


_Compaq_
V6000 -No Sound
6710B -Compiz not working after Feisty upgrade (1 report of this problem)
NX9420 -Cannot suspend/hibernate

**Critical Issue's, steer clear of Gutsy for now:**
_HP_
DV2108EA
DV2310CA
DV2570
DV9000T
DV9000Z
ZD7229EA
ZE5400 -Fuzzy Display Issue
ZT1130

_Compaq_
NX9010 -Fuzzy Display Issue
NX9600
V6000Z 

For critical issues please search your model number in the Ubuntu forums search.


**Drivers:**
[HP Pavilion Webcam]("http://www.arakhne.org/spip.php?article50")

[LightScribe]("http://www.lacie.com/products/product.htm?pid=10803")


**Fixes:**
[No Sound]("http://ubuntuforums.org/showthread.php?p=3589977#post3589977")

[Display Post #47]("http://ubuntuforums.org/showthread.php?t=582220&page=5")


Please note there are some large steps forward in the release of Gutsy Gibbon. Consider Vista that had billions of dollars pumped into it and it still came out half digested. Give the Ubuntu team some time and revert back to Feisty if you're having unresolvable problems.
[COLOR="Red"]
Please feel free to contribute any information you can. Please specify your **exact** model clearly, not the series but the model. Example DV9000 can be either a model or the general name used for the DV9000 series. If there were problems let us know what they were,** if you installed or upgraded to Gutsy** and how you went about resolving the problems if you managed too.[/COLOR]

This thread will be updated regularly...

---

### Post by s_raghu20 on 2007-10-24
Hi

Thats a very useful list. But I want to suggest a little change.

HP 6710b is not 100% fine. I did an upgrade from feisty and the Compiz effects just dont turn on.

I mentioned that in another post as well, but when I saw your list here, felt like mentioning it.

hth
regards
raghav..

---

### Post by Shiva88 on 2007-10-24
My HP dv2000t took Gutsy almost perfectly.  Few issues, none critical.

---

### Post by ra300z on 2007-10-25
The HP DV2000 should be moved down in my opinion.  The NVidia driver sometimes locks up for a few seconds every now and again.  The upper title bar sometimes disappears.  The laptop runs very hot and the battery lasts about 30-40% less time than with Feisty.  I can get 2h30m under Feisty and 1h30m in Gutsy.

I'm not sure if the hot issue should bring it down to the "steer clear" section.  But if the laptop runs this hot, it will probably die due to overheating.  I'd rather protect my laptop and run Feisty.

My laptop is a DV2310CA with 1.5GB of memory.

---

### Post by KevinCLovesU on 2007-10-25
ze4600 user here (only for a few more days, this thing's getting old), soon to be dv6500z user... the ze4600 works perfectly. We'll see about the new machine once I receive it.

---

### Post by BoardDWorld on 2007-10-26
@ra300z
Did you perform an upgrade or fresh install?


Thanks for your input guys.

---

### Post by ra300z on 2007-10-26
> **BoardDWorld said:**
> @ra300z
Did you perform an upgrade or fresh install?


Thanks for your input guys.

The answer:  fresh install.

Three partitions:
(1) Windows Vista
(2)  Feisty
(3)  Test partition for testing whatever Linux distro I need to.

Currently #3 is a fresh install of Gutsy.  It runs incredibly hot.  Now it did have RC1 installed, but I'm pretty sure I did a fresh install to that partition... not an upgrade.  I didn't see any programs consuming CPU out of the ordinary on Gutsy.  So here's what I think it is... the NVidia drivers are doing a lot of interrupts and that is causing an increase in temperature.

When Gnome/Compiz locks up for a few seconds, to me that's unusable...for my tastes.

As for the sound, just unplug your laptop after using Windows.

I'm not aware of other problems with this laptop.

---

### Post by shane.reid on 2007-11-11
dv9207us

Installed perfectly - closed source nvidia drivers work with compiz perfectly.

Webcam works after driver install (including in the new skype beta)

---

### Post by $igmund on 2007-11-11
I have a DV6426 Gutsy seems to work so far. I'm having trouble getting Compiz to work right, but I would but more blame on my lack of experience with linux (this is my first install)

The system is functional, but I am still using my vista partition primarily.

EDIT 11/12/07: I got Compiz-fusion working!!!

---

### Post by tavasti on 2007-11-14
Compaq nx9420 cannot suspend/hibernate, fglrx issue

Even tried notes found here: [https://wiki.ubuntu.com/LaptopTestingTeam/HPnx9420](https://wiki.ubuntu.com/LaptopTestingTeam/HPnx9420)

---

### Post by qrprat77 on 2007-11-26
Hey I'm using an hp zv6123cl I picked up at Sam's club just over two years ago.  I use 7.10-AMD64 Ubuntu and so far, only have the long boot prollum...

---

### Post by YoungPastor on 2007-11-28
my Compaq 2000 series laptop runs very well but suffers the long load. This is what your initial post indicates, I just want to let you know I found it true.
 
Compaq Presario 2100 intel Celeron 1.6GHz

---

### Post by taistelutipu on 2007-11-28
I posted a detailed account of the problems my sister encountered when upgrading from Feisty to Gutsy on her COMPAQ Evo N610c 
[http://ubuntuforums.org/showthread.php?p=3856349#post3856349]("http://ubuntuforums.org/showthread.php?p=3856349#post3856349")

So my vote was a clear unsuccessful upgrade.

---

### Post by ag65151 on 2007-12-05
HP Pavillion ze5500 laptop.
Broadcom 4306 wireless card
ATI IGP 340M video card

On a fresh install, I had the fuzzy display issue. I worked around it by switching the driver to "vesa" long enough to get on the forums and fix it.

Wireless was a problem, but I have been using ndiswrapper since I switched to Linux, so I was able to get it going fairly quickly. 

All in all, a fairly successful experience. I am now up and running on Gutsy (7.10) with only the suspend/hibernate issues remaining.

---

### Post by vishnuhari on 2007-12-12
hi
I've a Compaq Presario V3424AU model laptop. its too difficult to install Ubuntu 7.1 into it. initially when i just followed the instructions in the graphical interface(start or install Ubuntu), the system freezes even before going on to the live desktop that we get. 

I just changed the boot option to "live acpi=off" and then i could proceed to install it.
(NOTE PLEASE: i don't know what that command is for, i just tried out what ever was given in the help menu and luckily, this one worked)

but it was not without problems. during start up, it shows a big list of errors and messages. Like....

   "PnPBIOS unable to get node information; Aborting"
   "reboot using pnpbios=off option"

   "dev_node_info unexpected status 0x37"
   "check with your vendor for an updated BIOS"

It doesnt end here. the usb mouse stops responding at times. even then the touchpad works fine. 

But anyhow, unlike Ubuntu 6.1, the advantage for 7.1 is that the display is perfectly OK. As for 6.1, the screen resolution was very low(as like in windows prior to the installation of the Driver software).
i tried many Nvidia-glx Drivers, but it didnt work. (If anyone knows the method to fix it, do inform me please)

And finally, there is the big problem of shutting down. it doesn't shut down and shows the following messages...

      "Network Manager:<WARN>nm_hal_deinit():libhal shutdown failed-connection is closed."
      "Network Manager:nm_dbus_signal_device_status_chang:assertion 'cb_data->data->dbas_    
                                                                                                                                   connection failed"   

What are all these things? Can anyone please help me what to do........... Please..

The system configuration  is
                AMD Turion 64 , 2.21 GHz processor                
                512 MB RAM, 
                NVIDIA GeForce Go 6150 graphics

---

### Post by deathwithafireinside on 2008-01-20
works great on my v6000

---

### Post by xxrealmsxx on 2008-01-22
> **qrprat77 said:**
> Hey I'm using an hp zv6123cl I picked up at Sam's club just over two years ago.  I use 7.10-AMD64 Ubuntu and so far, only have the long boot prollum...

[http://ubuntuforums.org/showthread.php?t=581075](http://ubuntuforums.org/showthread.php?t=581075)

solution for your problem.

Now tell me this, does your hibernate/suspend work? Mine doesn't on my zv6k.

Lastly on my zv6000 my screen shows artifacts (an ati driver issue I believe). But hey wireless works for the first time EVER in 7.10.

---

### Post by slarrabe on 2008-01-23
I was able to install Gutsy just fine despite low resolution preventing me from seeing the buttons at the bottom of the windows.  I managed to resolve this problem.  Now my Compaq Presario F756NR works flawlessy.  Hopefully I won't encounter any more problems.

---

### Post by darrentownsend on 2008-02-05
Compaq Presario 2509 - fuzzy resolution both on upgrade and fresh install.

---

### Post by KingWilliam on 2008-02-16
for my HP dv8378 from the dv8000 series:

Installed perfectly out of the box. except for two things:

-the "Texas Instruments 5-in1 card reader" can only read SD-cards. I have been trying to solve this without success.
-I can not hibernate nor suspend. When I do try I get very strange artifacts all over my screen.

---

### Post by ApOgEEs on 2008-03-21
mine is, HP Compaq nx9010. Successfully installed fresh copy. 

some issue on usplash, wireless network, modem... uh i don't remember, there is many more.

---

### Post by gasparov on 2008-03-21
As said in another thread:
7.04 to 7.10 smoothless
7.10 fresh install sucked big...regression?

---

