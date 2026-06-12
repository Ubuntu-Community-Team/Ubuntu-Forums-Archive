---
title: "Intel GMA 950 sluggish poor performance in Jaunty 9.04"
date: 2009-03-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by llib1234 on 2009-03-23
If you use an Intel GMA 950 or similar integrated video card, I think you'll experience very poor video performance with and without Compiz or compositing running. That's exactly what's happening with me. I believe the new intel driver version 2.4 (xserver-xorg-video-intel) and up are causing this problem but I'm not sure. I know that the version 2.2 of the driver that Im using on 8.04 is very good, with smooth animations and video performance.

Is the final version of Jaunty 9.04 going to ship with an option to go back to much better version 2.2 of this intel driver?
I hope it does, and does anyone know newer versions will fix these problems.

---

### Post by binbash on 2009-03-23
I have a similar card, now i am upgrading from intrepid to jaunty.I will post about the card performance

---

### Post by olskar on 2009-03-23
Inteldriver 2.6.3 should be in Jaunty now? Are you sure about the version? However its a well known problem still with that version;

[https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/303011](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/303011)

---

### Post by scaine on 2009-03-23
If you're experiencing poor performance with an Intel 9 series, you should seriously consider enabling UXA support in your xorg.conf.

[https://wiki.ubuntu.com/X/UxaTesting](https://wiki.ubuntu.com/X/UxaTesting)

Pretty dramatic effect on my little MacMini.

---

### Post by Mindless Automata on 2009-03-23
UXA causes some machines to lock-up, however.

---

### Post by binbash on 2009-03-23
I upgraded from intrepid.It is terrible slow if you activate cube expo etc.Otherwise it is ok

---

### Post by binbash on 2009-03-23
I upgraded to kernel Linux nyn-laptop 2.6.28-11-generic #36-Ubuntu SMP Fri Mar 20 19:40:40 UTC 2009 i686 GNU/Linux

and expo etc everything works fast now

---

### Post by Starks on 2009-03-23
> **llib1234 said:**
> If you use an Intel GMA 950 or similar integrated video card, I think you'll experience very poor video performance with and without Compiz or compositing running. That's exactly what's happening with me. I believe the new intel driver version 2.4 (xserver-xorg-video-intel) and up are causing this problem but I'm not sure. I know that the version 2.2 of the driver that Im using on 8.04 is very good, with smooth animations and video performance.

Is the final version of Jaunty 9.04 going to ship with an option to go back to much better version 2.2 of this intel driver?
I hope it does, and does anyone know newer versions will fix these problems.
Did you try 2.6.3 yet?

---

### Post by binbash on 2009-03-23
I enabled UXA and it is the fastest Ubuntu version i have ever used, here is my card details : 

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)

And i blogged about it : 

[http://www.ubuntu-inside.me/2009/03/how-to-enable-uxa-at-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/03/how-to-enable-uxa-at-ubuntu-jaunty.html)

---

### Post by tahina on 2009-03-23
The command "lspci -nn | grep VGA" outputs the following for this eeepc 701:
> 00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 04)

...but xorg.conf says:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection
```

That feels fishy to me...

---

### Post by scaine on 2009-03-23
Well, here's my entire xorg.conf :

```
Section "Device"
    Identifier    "Configured Video Device"
        Option        "AccelMethod" "uxa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```

Massive, eh?  :p  I don't know why your device section has vesa in it.  But I have to admit, I have no idea what Intel cards *should* use...

---

### Post by nwadams on 2009-03-23
i'm using hardy...so yes its older drivers but i tried the uxa thing in xorg.conf and I notice a huge improvement too. Going to try it with my jaunty test box tonight and see what happens. I will play with it a bit and post any issues i'm having. Note i'm using gam x3100 rather than 950

---

### Post by Asham on 2009-03-23
For me performance is much better without the "uxa" fix applied. 

Using a Samsung NC10 netbook here is my output:
adam@adm-netbook:~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
adam@adm-netbook:~$

---

### Post by DeeZiD on 2009-03-23
> **Asham said:**
> For me performance is much better without the "uxa" fix applied. 

Using a Samsung NC10 netbook here is my output:
adam@adm-netbook:~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
adam@adm-netbook:~$

Same Netbook, same VGA, same opinion ;)

Dennis

---

### Post by scaine on 2009-03-23
> **Asham said:**
> For me performance is much better without the "uxa" fix applied. 

Using a Samsung NC10 netbook here is my output:
adam@adm-netbook:~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
adam@adm-netbook:~$

My MacMini has a similar (but apparently not identical) chip and UXA is very much better here :

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)

I wonder if it's CPU related?

---

### Post by llib1234 on 2009-03-23
Here's my lspci output:

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

its the GMA 950 video card.
I've tried UXA with apha 6 of jaunty and x crashes with UXA enabled.
but I haven't tried the newest version of the intel driver.
im busy so i can't reinstall jaunty and test the new driver.
maybe someone else with the same video card and chipset can try it, and compare it to hardy 8.04
thanks

---

### Post by Taiebot65 on 2009-03-25
I have to say i ve stopped using any compositing i think my video card acceleration is totally disabled. I had problems with applications freezing when i was trying to see them or taking ages to close. Since i ve stopped compiz and metacity everything is all-right but i can not use GIMP and totem as they freeze easily i think it s all related to my graphic card.. 
[http://ubuntuforums.org/showthread.php?t=1104561]("http://ubuntuforums.org/showthread.php?t=1104561")
I'm tempted to report a bug...


00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by Stetzen on 2009-03-25
> **Asham said:**
> For me performance is much better without the "uxa" fix applied. 

Using a Samsung NC10 netbook here is my output:
adam@adm-netbook:~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
adam@adm-netbook:~$

Well... I have similar card in my Thinkpad R61i laptop, 

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

and the problem of performance has two aspects.

With EXA compiz is really laggy, especially minimize effect. It shows about 2 fps, but I'm unable to actually measure it, because benchmark ihows quit high values, which are far from real. It actually looks more like short freezes than like low performance.

On the other hand, UXA shows relatively smooth compiz, but has lower performance at 3d applications. glxgears is an app, which shows up to 2-fold decrease, but it may not be related to rendering performance. tux racer shows decrease at about 10-20%, which is not painful at all. Anyway, I'm not using 3d apps in everyday life, so at the moment UXA seems to be a better choice.

---

### Post by llib1234 on 2009-04-15
I have just tried the UXA mode on latest 13 April daily image of 9.04

It is much better than before, but still only on par with 8.10 Intrepid.

I hope the final gets better as 8.04 Hardy is much smoother all round. Especially the Zoom function is much slower and laggy in 9.04 and 8.10
Don't know why?

Hope u can help me

---

### Post by olskar on 2009-04-15
In Intrepid I got 683FPS on my Asus EEE PC 900 running Intel 915GM and in Jaunty I get ~115. With the great amount of people using intelcards I am beginning to feel that Jaunty should not be released until this has been taken care of.

---

### Post by canesalato on 2009-04-15
uxa for me was slower than exa (eeepc 901 i945gme) and way buggy.
Upgrading to 2.6.99.903 solved a lot of bugs and made uxa quite stable to use but still slow.
Upgrading kernel to 2.6.29.1 (+intel 2.6.99.903) made uxa also very fast (faster than exa) so the "right" combination seems to be kernel >= 2.6.29.1 + intel >=2.6.99.903.
That's what fedora and mandriva will be using in a few days with their new releases... :(

---

### Post by FFuser on 2009-04-15
> **canesalato said:**
> uxa for me was slower than exa (eeepc 901 i945gme) and way buggy.
Upgrading to 2.6.99.903 solved a lot of bugs and made uxa quite stable to use but still slow.
Upgrading kernel to 2.6.29.1 (+intel 2.6.99.903) made uxa also very fast (faster than exa) so the "right" combination seems to be kernel >= 2.6.29.1 + intel >=2.6.99.903.
That's what fedora and mandriva will be using in a few days with their new releases... :(

I get good results with intel 2:2.6.99.1.... (from [https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)) and kernel 2.6.30-rc2 (from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)) (Without uxa, uxa is still very unstable)
What are good results/framerates:
glxgears (I know, not a real test): 1200-1500 fps (with normal jaunty only 200-300)
/usr/lib/xscreensaver/glblur -fps: 45 (stock jaunty, less than 5)
openbve (cool game by the way): 30 (with low settings), stock: 3-7 (unplayable)

[COLOR="Red"]***_[FONT="Arial Black"]Only use at your own risk![/FONT]_***[/COLOR]

So it seems that good progress is being made, we just have to wait another 6 months...


But since this kernel seems to have trouble with sound, I installed the 2.6.29.1 version, but then the framerates are like a stock jaunty.
(Their are a lot of improvements for intel in the 2.6.30-rc2)

---

### Post by binbash on 2009-04-15
> **FFuser said:**
> I get good results with intel 2:2.6.99.1.... (from [https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)) and kernel 2.6.30-rc2 (from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)) (Without uxa, uxa is still very unstable)
What are good results/framerates:
glxgears (I know, not a real test): 1200-1500 fps (with normal jaunty only 200-300)
/usr/lib/xscreensaver/glblur -fps: 45 (stock jaunty, less than 5)
openbve (cool game by the way): 30 (with low settings), stock: 3-7 (unplayable)

[COLOR="Red"]***_[FONT="Arial Black"]Only use at your own risk![/FONT]_***[/COLOR]

So it seems that good progress is being made, we just have to wait another 6 months...


But since this kernel seems to have trouble with sound, I installed the 2.6.29.1 version, but then the framerates are like a stock jaunty.
(Their are a lot of improvements for intel in the 2.6.30-rc2)


I am getting double performance with 29.1 kernel and 2:2.6.99.1.I am gonna try 30.rc2 now.

---

### Post by asuastrophysics on 2009-04-16
> **binbash said:**
> I enabled UXA and it is the fastest Ubuntu version i have ever used, here is my card details : 

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)

And i blogged about it : 

[http://www.ubuntu-inside.me/2009/03/how-to-enable-uxa-at-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/03/how-to-enable-uxa-at-ubuntu-jaunty.html)

really?

i have the **exact** same card and configuration you do, and when i enabled UXA it turned my laptop into a brick.
wow. it doesn't even matter if we have the same hardware. 
seems UXA is about as consistent as politicians.

---

### Post by s6dalane on 2009-04-16
I installed the same kernel as FFuser and my glxgears score improved about 3 times (with UXA enabled before and after)!

The only problem is, my network is not working with this kernel, is there something I could have missed installing or configurating?

---

### Post by binbash on 2009-04-16
> **s6dalane said:**
> I installed the same kernel as FFuser and my glxgears score improved about 3 times (with UXA enabled before and after)!

The only problem is, my network is not working with this kernel, is there something I could have missed installing or configurating?

Glxgears is not a benchmark tool but i jumped from 800 to 2500  :) If you write the lspci output maybe we can get your network working

---

### Post by s6dalane on 2009-04-16
Thanks for the response, here's the lspci output:
> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

BTW, no network devices were shown in the 2.6.29.1 kernel also, but everything works with Jaunty's default kernel.

Might it be that there is no restricted-modules package for mainline kernels, which is needed for the network device?

---

### Post by llib1234 on 2009-04-16
Yes you are right.

I got better improvements when I upgrade to 2.6.30-rc2 kernel and latest intel drivers as shown above. Screen movements are smoother.

However I can't use it because Vmware Workstation 6.5.1 doesn't compile modules in this kernel.

---

### Post by llib1234 on 2009-04-17
I've gone back to using Ubuntu 8.04 Hardy. The intel graphics driver is much better and smoother. 
I installed intrepid's 2.6.27 kernel on hardy today and now multitasking is greatly improved. the vmware workstation runs smoothly alongside other apps whereas before it slowed down everything.
If you guys notice any improvements to intel drivers in jaunty please let me know. anyways i'll keep 9.04 on my machine and wait for new versions.

---

### Post by 00b00nt00 on 2009-04-17
With UXA I get this message in the console running glxgears:

"Running synchronized to the vertical refresh. The framerate should be
approximately 1/63 the monitor refresh rate."

I get around 350 fps. With EXA it's around 900.

I've also noted a slight cursor lag when using the arrow keys. Otherwise, everything seems okay.

---

### Post by Jim March on 2009-04-18
Um...are you sure we need to go all the way to (pre-release) kernel 2.6.30 to get results here? 2.6.29.1 is stable and has the kernel-level modesetting and other goodies for the Intel 945/965 chipsets. 2.6.30 just ain't done yet, right? Why not stick with .29.1 for now?

---

### Post by wigren on 2009-04-19
> **FFuser said:**
> So it seems that good progress is being made, we just have to wait another 6 months...


But since this kernel seems to have trouble with sound, I installed the 2.6.29.1 version, but then the framerates are like a stock jaunty.
(Their are a lot of improvements for intel in the 2.6.30-rc2)


Lots of improvements is right. I've upgraded to the packages you listed and the difference is immediately noticeable. :D

```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
```

---

### Post by olskar on 2009-04-19
> **wigren said:**
> Lots of improvements is right. I've upgraded to the packages you listed and the difference is immediately noticeable. :D

```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
```

I get bad performance in both 2.6.28, 2.6.29 and 2.6.30rc..what could I be doing wrong? Its with a 915 card

---

