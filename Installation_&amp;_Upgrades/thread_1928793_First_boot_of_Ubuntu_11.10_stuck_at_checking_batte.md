---
title: "First boot of Ubuntu 11.10 stuck at checking battery using Wubi"
date: 2012-02-20
forum: Installation &amp; Upgrades
---

### Post by aamir147 on 2012-02-20
I am trying to install Ubuntu 11.10 using wubi on my laptop. I set aside 20 gb for the process and it finishes successfully in windows. After reboot it continues the process, finishes then reboots. This is when I get stuck at picking the kernel. I pick the first choice and get stuck at a blank/black screen. So then I reboot and pick the same kernel again but this time I edit replacing quick splash with nomodeset. The kernel looks like its loading until I get stuck at checking battery status... [ok]. At this point I've tried various fixes found on this forum but to no avail. I have an AMD A4 with ATI Radeon graphics. Can someone please help me get this up?

---

### Post by MAFoElffen on 2012-02-20
> **aamir147 said:**
> I am trying to install Ubuntu 11.10 using wubi on my laptop. I set aside 20 gb for the process and it finishes successfully in windows. After reboot it continues the process, finishes then reboots. This is when I get stuck at picking the kernel. I pick the first choice and get stuck at a blank/black screen. So then I reboot and pick the same kernel again but this time I edit replacing quick splash with nomodeset. The kernel looks like its loading until I get stuck at checking battery status... [ok]. At this point I've tried various fixes found on this forum but to no avail. I have an AMD A4 with ATI Radeon graphics. Can someone please help me get this up?
You said you "tried various fixes on this forum"... Did you try any of mine in my Sticky: Graphics Resolution? No matter. 

First let me warn you that I don't do WUBI... But I do test and help support OS and Graphics layers in Unix and Linux, especially with Ubuntu.

Hung at "Checking battery State" indicates that the boot process has booted the kernel successfully, started booting the XServer... and tried to boot graphics driver, where it hung.  The layer where XServer resides is hung, but the layer where the kernel (Linux) resides, the kernel should be running fine.

This is a good thing.  If at that point, you press <Cntrl><F2>, it should get you to the virtual terminal tty2. Log in. Install your ATI driver using these directions:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][**Installing ATI Packaged Drivers**]("http://ubuntuforums.org/showpost.php?p=11467052&postcount=798")[/SIZE][/COLOR][/SIZE][/COLOR]

Tell me how it goes.

---

### Post by aamir147 on 2012-02-20
> **MAFoElffen said:**
> You said you "tried various fixes on this forum"... Did you try any of mine in my Sticky: Graphics Resolution? No matter. 

First let me warn you that I don't do WUBI... But I do test and help support OS and Graphics layers in Unix and Linux, especially with Ubuntu.

Hung at "Checking battery State" indicates that the boot process has booted the kernel successfully, started booting the XServer... and tried to boot graphics driver, where it hung.  The layer where XServer resides is hung, but the layer where the kernel (Linux) resides, the kernel should be running fine.

This is a good thing.  If at that point, you press <Cntrl><F2>, it should get you to the virtual terminal tty2. Log in. Install your ATI driver using these directions:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][**Installing ATI Packaged Drivers**]("http://ubuntuforums.org/showpost.php?p=11467052&postcount=798")[/SIZE][/COLOR][/SIZE][/COLOR]

Tell me how it goes.


I tried your process above and it didn't work. I remember trying this before also. the first line in the ATI driver install guide does not fetch any results. I have attached a picture with the error. Also the install fglrx command doesn't complete properly either. Idk what to do. Thanks for helping! Also contro f2 did not work I used alt f2 instead. Maybe thats a reason why?

---

### Post by bcbc on 2012-02-21
Try booting with [nomodeset]("http://ubuntuforums.org/showthread.php?t=1613132") first. Then install the graphics driver? From that picture you're not connected to the internet so you cannot download and install something in that manner.

---

### Post by aamir147 on 2012-02-21
> **bcbc said:**
> Try booting with [nomodeset]("http://ubuntuforums.org/showthread.php?t=1613132") first. Then install the graphics driver? From that picture you're not connected to the internet so you cannot download and install something in that manner.

All this is after nomodeset. How would I go about connecting to the internet? The physical switch is on and the wifi is turned on in windows before I restart. How do I start wifi in ubuntu recovery?
Thanks for your help

Also it may help that since Im using wubi and this doesn't seem like a wubi problem, I may be able to add drivers manually to the root system?

---

### Post by MAFoElffen on 2012-02-21
> **aamir147 said:**
> All this is after nomodeset. How would I go about connecting to the internet? The physical switch is on and the wifi is turned on in windows before I restart. How do I start wifi in ubuntu recovery?
Thanks for your help

Also it may help that since Im using wubi and this doesn't seem like a wubi problem, I may be able to add drivers manually to the root system?
Yes, no Internet is a problem. I saw you had no connection to the outside world in your picture in post 3, you finally mentioned it in post 5. (I was offline through that)

You had to have had Internet for Install, right?  So from a LiveCD you have a connection?  Did you do a traditional install or WUBI?

If you use "recovery" and root:
```

lspci -v | grep Ethernet

```
Post the results of that...

---

### Post by aamir147 on 2012-02-21
> **MAFoElffen said:**
> Yes, no Internet is a problem. I saw you had no connection to the outside world in your picture in post 3, you finally mentioned it in post 5. (I was offline through that)

You had to have had Internet for Install, right?  So from a LiveCD you have a connection?  Did you do a traditional install or WUBI?

If you use "recovery" and root:
```

lspci -v | grep Ethernet

```
Post the results of that...

Sorry I didn't realize until right before the post above mine. I also noticed that the wifi was not working during install, it just didn't occur to me. I used wifi to download and wubi to install. But this problem seems to be out of wubi issues. Also I don't exactly have a ethernet connection, any way to get wifi on in recovery? In the mean time I will try to get ethernet from somewhere. I downloaded at school and at home my building has a universal wifi.
Thanks again!

---

### Post by bcbc on 2012-02-21
You can download the  .deb files from windows and save in the \ubuntu folder. Then you can access them from Ubuntu recover mode as /host/ubuntu/*.deb

Just not sure which you need. :)

---

### Post by MAFoElffen on 2012-02-21
> **bcbc said:**
> You can download the  .deb files from windows and save in the \ubuntu folder. Then you can access them from Ubuntu recover mode as /host/ubuntu/*.deb

Just not sure which you need. :)
+1 You could also dl the fglrx.deb file that way also (then install all w/ dpkg)

On "Ethernet"... That will show both your Wired and Wifi PCI devices... such as on the current box I am on:
```

mafoelffen@maf-ubuntu-01:~$ lspci -v | grep Ethernet
00:13.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
    Subsystem: ASUSTeK Computer Inc. Marvell 88E8053 Gigabit Ethernet controller PCIe (Asus)
[COLOR=Red]04:07.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)[/COLOR]

```That will tell all here trying to help you- which Wifi device you have... To be able to determine the driver you should have to make it work.  That is why I asked for the results of that. Sorry if I left out the "between the lines" details. If you had a specific make and model of laptop, stating that would also let someone look up the spec's or let someone who owns that same laptop let you know how they made their's work...

Still waiting patiently.

---

### Post by aamir147 on 2012-02-21
> **MAFoElffen said:**
> +1 You could also dl the fglrx.deb file that way also (then install all w/ dpkg)

On "Ethernet"... That will show both your Wired and Wifi PCI devices... such as on the current box I am on:
```

mafoelffen@maf-ubuntu-01:~$ lspci -v | grep Ethernet
00:13.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
    Subsystem: ASUSTeK Computer Inc. Marvell 88E8053 Gigabit Ethernet controller PCIe (Asus)
[COLOR=Red]04:07.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)[/COLOR]

```That will tell all here trying to help you- which Wifi device you have... To be able to determine the driver you should have to make it work.  That is why I asked for the results of that. Sorry if I left out the "between the lines" details. If you had a specific make and model of laptop, stating that would also let someone look up the spec's or let someone who owns that same laptop let you know how they made their's work...

Still waiting patiently.

Laptop I have is the Lenovo Z575 model 129922u
Processor = amd a4 with radeon 6480G
wifi adapter = ralink rt3090 802.11n
ethernet = virtualbox host-only ethernet adapter 
I will try to run that line a little later (in school now) and post details, I thought it enabled ethernet not give me my system config. Thanks again.


Edit: I was able to download the wifi drivers, gonna try them now and see if I can get radeon drivers while im at it. Will update as soon as I find out.

---

### Post by aamir147 on 2012-02-21
Ok I tried installing but I keep getting unable to find errors. Also wubi  installs Ubuntu in a .disk file. Maybe I need a step by step guide? I already have the wifi driver. 
If you can give me a step by step guide in how to access my windows partition?

---

### Post by bcbc on 2012-02-21
You can access anything on the Windows partition through the /host i.e. if you install Ubuntu on the C: 'drive', then you access C:\ubuntu as /host/ubuntu

So to install all packages you saved on in C:\ubuntu you could run:
```
sudo dpkg -i /host/ubuntu/*.deb
```
If you're in a recovery mode root prompt you can drop the sudo:
```
dpkg -i /host/ubuntu/*.deb
```

---

### Post by aamir147 on 2012-02-21
> **bcbc said:**
> You can access anything on the Windows partition through the /host i.e. if you install Ubuntu on the C: 'drive', then you access C:\ubuntu as /host/ubuntu

So to install all packages you saved on in C:\ubuntu you could run:
```
sudo dpkg -i /host/ubuntu/*.deb
```
If you're in a recovery mode root prompt you can drop the sudo:
```
dpkg -i /host/ubuntu/*.deb
```

I tried using the code above however ran into some problems concerning dkms. I downloaded a dkms.deb from the official site and was having problems installing that too. which might be a good thing considering it has something to do with the kernel. So the question now is what do I do? I attached a pic of the error. I confirmed with my system info in windows as well as the lenovo website with which version of wifi adaptor I have. Also when I tried installing dkms.deb it said something about patch missing.


Edit: I also tried the solutions listed here:
[http://ubuntuforums.org/showpost.php?p=10627767&postcount=6](http://ubuntuforums.org/showpost.php?p=10627767&postcount=6)
needless to say it didn't work.

---

### Post by MAFoElffen on 2012-02-23
> **aamir147 said:**
> I tried using the code above however ran into some problems concerning dkms. I downloaded a dkms.deb from the official site and was having problems installing that too. which might be a good thing considering it has something to do with the kernel. So the question now is what do I do? I attached a pic of the error. I confirmed with my system info in windows as well as the lenovo website with which version of wifi adaptor I have. Also when I tried installing dkms.deb it said something about patch missing.


Edit: I also tried the solutions listed here:
[http://ubuntuforums.org/showpost.php?p=10627767&postcount=6](http://ubuntuforums.org/showpost.php?p=10627767&postcount=6)
needless to say it didn't work.
DKMS = Dynamic Kernel Module Support Framework
It is one of many depends for fglrx, a very important one.


The depends for fglrx are here:
[http://packages.ubuntu.com/oneiric/fglrx](http://packages.ubuntu.com/oneiric/fglrx)

Did you say you got your wifi working yet?  If not, I guess the thing to do is to start up Synaptic and see what of those depends are there and which ones you need to get installed.

If you have an internet connection, then installing would assess what if there and install the package along with any of the missing dependencies.

EDIT== Synaptic is not going to help you because it is graphical... Unless you could go through recovery and strt in failsafe graphics.

---

### Post by aamir147 on 2012-02-23
> **MAFoElffen said:**
> DKMS = Dynamic Kernel Module Support Framework
It is one of many depends for fglrx, a very important one.


The depends for fglrx are here:
[http://packages.ubuntu.com/oneiric/fglrx](http://packages.ubuntu.com/oneiric/fglrx)

Did you say you got your wifi working yet?  If not, I guess the thing to do is to start up Synaptic and see what of those depends are there and which ones you need to get installed.

If you have an internet connection, then installing would assess what if there and install the package along with any of the missing dependencies.

EDIT== Synaptic is not going to help you because it is graphical... Unless you could go through recovery and strt in failsafe graphics.

Failsafe graphics doesn't work, however, I was able to get an ethernet connection for a little while yesterday and was unable to get fglrx working using the initial directions you gave me. I may be able to hop on the ethernet again for a little while on friday morning so I will try what I can then if you have any suggestions. also when I try installing the wifi drivers.deb I get errors with dependency issues. I may give it a try again tonight in order to find out what I need to fix my dependency issues.
Thanks again!

---

### Post by MAFoElffen on 2012-02-23
> **aamir147 said:**
> Failsafe graphics doesn't work, however, I was able to get an ethernet connection for a little while yesterday and was unable to get fglrx working using the initial directions you gave me. I may be able to hop on the ethernet again for a little while on friday morning so I will try what I can then if you have any suggestions. also when I try installing the wifi drivers.deb I get errors with dependency issues. I may give it a try again tonight in order to find out what I need to fix my dependency issues.
Thanks again!
I don't usually help with WIFI support even though I've done over a 1000 customer installs. What the heck.  Which Driver are you trying to install -- I'll look at it's dependencies and list them.

So you are using this one right?
[rt3090-dkms_2.4.0.4-0ubuntu0~ppa0_all.deb]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.4.0.4-0ubuntu0%7Eppa0_all.deb") 

At least from the install discussions, I don't see that one having any outside dependencies.

---

### Post by aamir147 on 2012-02-23
> **MAFoElffen said:**
> I don't usually help with WIFI support even though I've done over a 1000 customer installs. What the heck.  Which Driver are you trying to install -- I'll look at it's dependencies and list them.

So you are using this one right?
[rt3090-dkms_2.4.0.4-0ubuntu0~ppa0_all.deb]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.4.0.4-0ubuntu0%7Eppa0_all.deb") 

At least from the install discussions, I don't see that one having any outside dependencies.

Im using this post to download:
[http://ubuntuforums.org/showpost.php?p=10701593&postcount=3](http://ubuntuforums.org/showpost.php?p=10701593&postcount=3)
Also the package you showed me is the dkms.deb that I try to install but fail at. Also thanks for making an exception with me on this wifi issue. However, this seems to be a dependency issue that im not sure how to fix.

---

### Post by MAFoElffen on 2012-02-23
> **aamir147 said:**
> Im using this post to download:
[http://ubuntuforums.org/showpost.php?p=10701593&postcount=3](http://ubuntuforums.org/showpost.php?p=10701593&postcount=3)
Also the package you showed me is the dkms.deb that I try to install but fail at. Also thanks for making an exception with me on this wifi issue. However, this seems to be a dependency issue that im not sure how to fix.
What I posted is the same driver, from the same author (Markus Heberling), from his own PPA and 2 years of changes/updates newer than the Lucid version in that post... You are using Onieric, which his ppa stops at Natty... but network change wise between Natty and Onieric, that should work.

His PPA is:
[https://launchpad.net/~markus-tisoft/+archive/rt3090](https://launchpad.net/~markus-tisoft/+archive/rt3090)

His caution to people is that you need to reinstall with each distribution upgrade.  (Uninstall/reinstall.)  I suspect that since Oneiric and Precise are going through so many upstream changes with Linux Kernel, that rule of thumb is going to change to more often.

---

### Post by aamir147 on 2012-02-23
> **MAFoElffen said:**
> What I posted is the same driver, from the same author (Markus Heberling), from his own PPA and 2 years of changes/updates newer than the Lucid version in that post... You are using Onieric, which his ppa stops at Natty... but network change wise between Natty and Onieric, that should work.

His PPA is:
[https://launchpad.net/~markus-tisoft/+archive/rt3090](https://launchpad.net/~markus-tisoft/+archive/rt3090)

His caution to people is that you need to reinstall with each distribution upgrade.  (Uninstall/reinstall.)  I suspect that since Oneiric and Precise are going through so many upstream changes with Linux Kernel, that rule of thumb is going to change to more often.

Ok Ill try that but it says I have to change ppa first? Do I just run that code in step 2 of his website?

---

### Post by MAFoElffen on 2012-02-24
> **aamir147 said:**
> Ok Ill try that but it says I have to change ppa first? Do I just run that code in step 2 of his website?
No, Since you have no internet connection through Ubuntu yet, that's not going to help you. 

But you could download from inside that ppa manually:
[https://launchpad.net/~markus-tisoft/+archive/rt3090/+packages](https://launchpad.net/~markus-tisoft/+archive/rt3090/+packages)

Would that help you?

---

### Post by aamir147 on 2012-02-25
> **MAFoElffen said:**
> No, Since you have no internet connection through Ubuntu yet, that's not going to help you. 

But you could download from inside that ppa manually:
[https://launchpad.net/~markus-tisoft/+archive/rt3090/+packages](https://launchpad.net/~markus-tisoft/+archive/rt3090/+packages)

Would that help you?

Ok I was able to get Ubuntu to boot, I downloaded the ati drivers directly from the Sri website using recovery using another threads discussion. Also thanks for helping me thru this, however now I have wifi issues which I will work on. also I was considering learning a language and was told to puck between debian and python. Which duo you think I should go with? Also know any good tutorials? I want to make apps.

---

### Post by MAFoElffen on 2012-02-25
> **aamir147 said:**
> Ok I was able to get Ubuntu to boot, I downloaded the ati drivers directly from the Sri website using recovery using another threads discussion. Also thanks for helping me thru this, however now I have wifi issues which I will work on. also I was considering learning a language and was told to puck between debian and python. Which duo you think I should go with? Also know any good tutorials? I want to make apps.
Debian is not a language. It is a Linux distribution base. Ubuntu is a Linux Distribution derived from Debian. All Linux has scripting. You do you mean that?

Python... "is" a language and seems to be the new "in demand" skillset for companies hiring new programmers.  I guess it all depends where you live and what you really want to and/or need to do.

[****The *Python Tutorial* — Python v2.7.2 documentation]("http://www.google.com/url?sa=t&rct=j&q=python+tutorial&source=web&cd=1&ved=0CDgQFjAA&url=http%3A%2F%2Fdocs.python.org%2Ftutorial%2F&ei=RzJJT5zSFamNigKnlOzaDQ&usg=AFQjCNGHgDIQyUXe76XiQvHhM6kr8-qTAA&cad=rja")

[*Python Tutorials*]("http://www.google.com/url?sa=t&rct=j&q=python+tutorial&source=web&cd=6&ved=0CF8QFjAF&url=http%3A%2F%2Fwww.awaretek.com%2Ftutorials.html&ei=RzJJT5zSFamNigKnlOzaDQ&usg=AFQjCNGhLcWBkHH1cyvcaLRO82E82y-MGw&cad=rja")

If interested in Python, something you might want to look into is IPython...

---

### Post by aamir147 on 2012-02-25
> **MAFoElffen said:**
> Debian is not a language. It is a Linux distribution base. Ubuntu is a Linux Distribution derived from Debian. All Linux has scripting. You do you mean that?

Python... "is" a language and seems to be the new "in demand" skillset for companies hiring new programmers.  I guess it all depends where you live and what you really want to and/or need to do.

[****The *Python Tutorial* — Python v2.7.2 documentation]("http://www.google.com/url?sa=t&rct=j&q=python+tutorial&source=web&cd=1&ved=0CDgQFjAA&url=http%3A%2F%2Fdocs.python.org%2Ftutorial%2F&ei=RzJJT5zSFamNigKnlOzaDQ&usg=AFQjCNGHgDIQyUXe76XiQvHhM6kr8-qTAA&cad=rja")

[*Python Tutorials*]("http://www.google.com/url?sa=t&rct=j&q=python+tutorial&source=web&cd=6&ved=0CF8QFjAF&url=http%3A%2F%2Fwww.awaretek.com%2Ftutorials.html&ei=RzJJT5zSFamNigKnlOzaDQ&usg=AFQjCNGhLcWBkHH1cyvcaLRO82E82y-MGw&cad=rja")

If interested in Python, something you might want to look into is IPython...

Thanks I want to makean application to run on most oses, preferably Linux and windows though. I may just go with the python. What language is used by Linux?

---

### Post by MAFoElffen on 2012-02-25
> **aamir147 said:**
> Thanks I want to makean application to run on most oses, preferably Linux and windows though. I may just go with the python. What language is used by Linux?
C++ and python in the OS. 

Cross Platform applications-- QT Framework or Java.

---

### Post by aamir147 on 2012-02-26
> **MAFoElffen said:**
> C++ and python in the OS. 

Cross Platform applications-- QT Framework or Java.

thanks I guess phython it is. Also thanks for the links and all the help.

---

