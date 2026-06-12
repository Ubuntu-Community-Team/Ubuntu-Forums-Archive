---
title: "Ububtu 10.10 no desktop after login!"
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by illuminate42 on 2010-12-05
Hi, I'm quite new to Ubuntu but have been using 10.04 on my Compaq Presario 2100 laptop for a while now and decided to try v10.10. Rather than just installing 10.10 and hoping for the best I decided to boot the v10.10 LiveCD to check it would run ok... it did. I then decided to try installing 10.10 using the option to install using the entire disk. Everything seemed to go ok until I tried to log in. After entering my password and hitting enter, I am left with the desktop wallpaper and a mouse pointer!! If I hit <Ctrl><Alt><F1> I can get to the command prompt which reports:

AC'97 1 access is not valid [0xffffffff], removing mixer
ali mixer 1 creating error.

I don't know if this has anything to do with the problem but sound seems to work ok and it runs fine in "Safemode". I have used the same disk to successfully install a different PC and have tried reinstalling the laptop but same problem. |I don't know that much about linux and would like to have a go at troubleshooting but don't really know where to start. Can anyone guide me through this?

Many thanks.

---

### Post by sikander3786 on 2010-12-05
Welcome to the forums :-)

We need to know more about your hardware. Please post the output of these commands.

```
lspci | grep VGA
```

```
free -m
```

```
sudo lshw | grep Processor
```

And in the mean time, try reconfiguring your graphics.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

It might throw an error like file not found. Ignore it and proceed to the next one.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot.

```
sudo shutdown -r now
```

Lets see if it is able to boot properly now. If not, post the output of first 3 commands.

---

### Post by illuminate42 on 2010-12-05
[FONT=Arial]Thanks for your response. [/FONT]

[FONT=Fixedsys][COLOR=DimGray]lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility u1[/COLOR][/FONT][FONT=Fixedsys]

[/FONT][FONT=Fixedsys][COLOR=DimGray]free -m
total: 937 used: 310 free: 627 shared: 0 buffers: 19 cached: 137
-/+ buffers/cache: used: 153 free: 784 free
Swap: total: 839 used: 0 free: 839[/COLOR][/FONT][FONT=Fixedsys]

[/FONT][FONT=Fixedsys][COLOR=DimGray]sudo lshw | grep Processor
PCI(sysfs)[/COLOR][/FONT]

I assume you are looking for the CPU which is:
[COLOR=DimGray]product: mobile AMD Athlon(tm) XP 2200+
physical id: 4
version: 6.8.1
size: 1788MHz[/COLOR]
[FONT=Fixedsys][COLOR=DimGray]
mv /etx/X11/xorg.conf[/COLOR][/FONT] [FONT=Arial]resulted in an error, No such file.[/FONT]
[FONT=Fixedsys]
[/FONT][FONT=monospace][FONT=Fixedsys][COLOR=DimGray]sudo dpkg-reconfigure -phigh xserver-xorg[/COLOR][/FONT] [FONT=Arial]no errors[/FONT]

[FONT=Arial]Rebooted with the same issue.[/FONT]
[/FONT]

---

### Post by efflandt on 2010-12-05
It sounds like an audio conflict which could be because Winmodems are basically a sound device and laptops often use the same AC'97 chip for both.  What shows for **aplay -l** (small L)?  For example my laptop (which I thought used AC'97 driver in Windows) shows:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```See if System > Administration > Additional Drivers, offers a driver for your modem. You may need to reboot after activating it.  In some cases that helps and other cases not.  But I am not sure what to do if that does not help.

Hint: When pasting formatted or long text, wrap it in code tags to preserve formatting (easier to read and follow columns).  To do that, highlight the text and click **#** at top of message window.

---

### Post by illuminate42 on 2010-12-05
Opening a terminal window under "safemode" gives:

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card0: A5454 [ALI 5451], device 0: ALI 5451 [ALI 5451]
  Subdevices: 32/32
  Subdevice #0: Subdevice #0
  ...
  Subdevice #31: Subdevice #31
```I get the login sounds and when in "safemode" can playback audio files. Additional Drivers does not find any drivers.

---

### Post by illuminate42 on 2010-12-06
This seems to be a graphics driver problem. Installing ATI propriety driver for Linux seems to have resolved this problem.

---

### Post by Gillette on 2010-12-09
> **illuminate42 said:**
> This seems to be a graphics driver problem. Installing ATI propriety driver for Linux seems to have resolved this problem.

I just installed 10.10 on my Compaq Presario 2100 laptop this morning twice and got the same problem as you. So how do I install the ATI proprietary driver for Linux?

---

### Post by sikander3786 on 2010-12-10
> **Gillette said:**
> I just installed 10.10 on my Compaq Presario 2100 laptop this morning twice and got the same problem as you. So how do I install the ATI proprietary driver for Linux?
If the drivers for your Graphics card are available, they might pop up under System > Administration > Additional Drivers when you are connected to the internet.

If not available there, post the output of this command.

```
lspci | grep VGA
```

---

### Post by Gillette on 2010-12-10
There is no option to login with the safe mode at the bottom of my login screen. There are only the Shutdown options, clock, and Universal Access Preferences.

---

### Post by Bruno^_^ on 2010-12-12
Hi all,

to Gillette:
 at the startup when you click on your user name,
at the bottom of the page (next to keyboard layout)
select "Desktop safe mode" from the list.
Now insert password of the user then login.

To All
I have Presario 2100 too, I installed Ubuntu 10.10 and I have the same issue,
this is my Video card [FONT=Fixedsys][COLOR=DimGray]
lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility u1[/COLOR][/FONT][FONT=Fixedsys]
[/FONT]in this 3d I read to install ATI driver to solve the problem, 
but I don't know the correct procedure, can you help me?

Thanks

---

### Post by Quackers on 2010-12-12
System > Administration > Additional Drivers

As previously stated by sikander3786 in post #8

---

### Post by Bruno^_^ on 2010-12-12
I'm sorry but the first part of post #8 was not good for me. 
If I'm connected to Internet and I search additional drivers I don't find nothing (screenshot in attachment).

For this reason in the previous post I wrote the output of lspci, as sikander3786 told in his post.
[FONT=Fixedsys][COLOR=DimGray]
lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility u1[/COLOR][/FONT][FONT=Fixedsys]
[/FONT]
Can you help me?
Thanks

---

### Post by illuminate42 on 2010-12-13
Additional Drivers did not work for me either. It was one of the first things I tried.

---

### Post by illuminate42 on 2010-12-13
It seems that there is a problem with the VGA driver that is installed by the Ubuntu 10.10 installation CD onto an HP Compaq Presario 2100 laptop with ATI Radeon Mobility U1 graphics chip set. I have found a work around that works for my laptop but I can't guarantee this is the best solution or even one that will work for you. I am sharing it here in the hope that it may help other people with the same problem. 
  
 Symptoms: 
 Following log-on you are left with only the desktop wallpaper and nothing else. 
 Changing the session to "safemode" before logging on allows the laptop to boot to a working state. 

Work around: 
 Following a clean install booting into "safemode" and installing ATI's proprietary driver will enable to the laptop to boot normally. This is done as follows: 

Switch on your laptop and boot to the log-in screen. 

Select your user name. You should now see several options at the bottom of the screen.

Change the session from "Ubuntu Desktop Edition" to "Ubuntu Desktop Edition (Safe Mode)". 

Enter you password and log-in. 

You should then be presented with a functional destop environment. Open firefox and go to: 
  [http://support.amd.com/us/gpudownload/linux/10-4/Pages/radeon_linux.aspx ]("http://support.amd.com/us/gpudownload/linux/10-4/Pages/radeon_linux.aspx")
  and download the ATI Catalyst Proprietary Display Driver - Linux. N.B. if this link doesn't work don't e-mail me it's not my website, do a serch for the driver or e-mail AMD!! 
  
 You should now have a file called "ati-driver-installer-10-4-x86.x86_64.run" or something similar, which may be in your "Downloads" folder ( "Places" > "Downloads" ) if you didn't specify a different location. 
  
 Run "ati-driver-installer-10-4-x86.x86_64.run". This should open a window with some folders in it but just sit back and be patient! After a little while you should be prompted for you root password then the driver installer will guide you through installation. 
  
 Once the driver installer has finished you will need to re-boot your laptop. In theory you should now be able to log-in normally.

---

### Post by rrsodl on 2010-12-14
> **illuminate42 said:**
> It seems that there is a problem with the VGA driver that is installed by the Ubuntu 10.10 installation CD onto an HP Compaq Presario 2100 laptop with ATI Radeon Mobility U1 graphics chip set. I have found a work around that works for my laptop but I can't guarantee this is the best solution or even one that will work for you. I am sharing it here in the hope that it may help other people with the same problem. 
  
 Symptoms: 
 Following log-on you are left with only the desktop wallpaper and nothing else. 
 Changing the session to "safemode" before logging on allows the laptop to boot to a working state. 

Work around: 
 Following a clean install booting into "safemode" and installing ATI's proprietary driver will enable to the laptop to boot normally. This is done as follows: 

Switch on your laptop and boot to the log-in screen. 

Select your user name. You should now see several options at the bottom of the screen.

Change the session from "Ubuntu Desktop Edition" to "Ubuntu Desktop Edition (Safe Mode)". 

Enter you password and log-in. 

You should then be presented with a functional destop environment. Open firefox and go to: 
  [http://support.amd.com/us/gpudownload/linux/10-4/Pages/radeon_linux.aspx ]("http://support.amd.com/us/gpudownload/linux/10-4/Pages/radeon_linux.aspx")
  and download the ATI Catalyst Proprietary Display Driver - Linux. N.B. if this link doesn't work don't e-mail me it's not my website, do a serch for the driver or e-mail AMD!! 
  
 You should now have a file called "ati-driver-installer-10-4-x86.x86_64.run" or something similar, which may be in your "Downloads" folder ( "Places" > "Downloads" ) if you didn't specify a different location. 
  
 Run "ati-driver-installer-10-4-x86.x86_64.run". This should open a window with some folders in it but just sit back and be patient! After a little while you should be prompted for you root password then the driver installer will guide you through installation. 
  
 Once the driver installer has finished you will need to re-boot your laptop. In theory you should now be able to log-in normally.



Thanks illuminate42. This solved my problem.

I have an old HP Pavillion ze4800 model and experienced exactly the same symptoms. 

I'm so grateful to you for posting this information here.

If it is any help for other newbies..... once the file is downloaded and in my case it would not run. I looked at the file's property and changed it so that it could be executed.

---

### Post by Bruno^_^ on 2010-12-14
Hi all,

I executed your instructions, but when I ran "ati-driver-installer-10-4-x86.x86_64.run" I received this error:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

$ ./ati-driver-installer-10-4-x86.x86_64.run 
Created directory fglrx-install.MkmrNm
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.723.........................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.35-22-generic:; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.MkmrNm
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

After that I ran this command:

./ati-driver-installer-10-4-x86.x86_64.run --buildpkg Ubuntu/maverick

The installation started, and it took some minutes.
If finished correctly, but when I rebooted the notebook and I tried to login in Desktop Edition, 
it didn't work...the same problem, the screen is empty :(

Illuminate42 thank you for your instructions, but I didn't solve this issue.
Can you help me?

Thanks

---

### Post by rrsodl on 2010-12-16
> **Bruno^_^ said:**
> Hi all,

I executed your instructions, but when I ran "ati-driver-installer-10-4-x86.x86_64.run" I received this error:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

$ ./ati-driver-installer-10-4-x86.x86_64.run 
Created directory fglrx-install.MkmrNm
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.723.........................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.35-22-generic:; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.MkmrNm
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

After that I ran this command:

./ati-driver-installer-10-4-x86.x86_64.run --buildpkg Ubuntu/maverick

The installation started, and it took some minutes.
If finished correctly, but when I rebooted the notebook and I tried to login in Desktop Edition, 
it didn't work...the same problem, the screen is empty :(

Illuminate42 thank you for your instructions, but I didn't solve this issue.
Can you help me?

Thanks


Very frustrating all this, isn't it? No wonder why so many people wont try Linux at all...... I've had a few problems but likely this forum is here otherwise Ubuntu will be in the bin by now :D - not sure how much more I can take of this before I go back to my trusted XP :lol

anyway, to fix your problem I think you want to download the version 10.10 from [http://support.amd.com/us/gpudownload/windows/previous/10/Pages/radeon_linux.aspx?os=Linux%20x86&rev=10.10](http://support.amd.com/us/gpudownload/windows/previous/10/Pages/radeon_linux.aspx?os=Linux%20x86&rev=10.10)

The other version stopped working for me and when I tried to re-installed the driver I found the same problem as you did. I managed to fix it with the version 10.10 of the driver.

Hopefully that works for you.

---

