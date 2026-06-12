---
title: "Screen Dimness/Brightness Problem Ubuntu 13.04 Dell XPS 13 2013"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by rdp1976 on 2013-04-26
I just bought a new Dell XPS 13 Ultrabook and installed Xubuntu 13.04 tonight.

When I boot up, the screen brightness is EXTREMELY dim, to the point where I can barely see anything.

Adjusting the screen brightness doesn't do anything. This is obviously a very new bug with 13.04, but any assistance would be greatly appreciated.

RDP1976

---

### Post by Toz on 2013-04-26
Hello and welcome to the forums.

Have a look at this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/954661]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/954661").
Comment #43 suggests that:
```
echo 0 | sudo tee /sys/class/backlight/intel_backlight/brightness
```
...fixes the problem. Perhaps you can give this a try. 

If it does work, the command posted in post #43:
```
/bin/echo 0 > /sys/class/backlight/intel_backlight/brightness
```
...should be added to /etc/rc.local above the "Exit 0" command. 

The bug report also indicates that its been fixed in 3.8.0-18.28. Which kernel version do you have installed?

---

### Post by rdp1976 on 2013-04-27
Thanks for your response. Unfortunately it didn't fix the issue:


My kernel version is: 3.8.0-19-generic

---

### Post by rdp1976 on 2013-04-27
I tried running the command manually and I also added the following to /etc/rc.local before exit 0:

No change.


/bin/echo 0 > /sys/class/backlight/intel_backlight/brightness

---

### Post by MAFoElffen on 2013-04-28
Idea... You first really need to verify that that directory path exists for you. You need to adapt that command to the directory structure of "your" system. That is the basic structure if your system has an Intel GPU. Go into Nautilus or command line and trace the tree down /sys/class/backlight/ and see what directories ar ender that that would indicate a GPU type name... Different systems with different GPU's have different names under that directory path.

Your going to see something similar to this... with whatever that "_GPU_directory_name_" below backlight, varied to what your gpu is...
```

[COLOR=#333333]/sys/class/backlight/acpi_video0/actual_brightness:10
[/COLOR][COLOR=#333333]/sys/class/backlight/acpi_video0/bl_power:0
[/COLOR][COLOR=#333333]/sys/class/backlight/acpi_video0/brightness:10
[/COLOR][COLOR=#333333]/sys/class/backlight/acpi_video0/max_brightness:10[/COLOR][COLOR=#333333]
[/COLOR]
```
As you can see, after that directory name, you will then see a four registry files named: [COLOR=#333333]actual_brightness, [/COLOR][COLOR=#333333]bl_power, [/COLOR][COLOR=#333333]brightness and [/COLOR][COLOR=#333333]max_brightness... each containing numeric values[/COLOR][COLOR=#333333]
[/COLOR]
First check the value in your registry via (remember to substitute for the directory name on yours):
```

cat /sys/class/backlight/_GPU_directory_name_/backlight

```
The try changing the value and then check that value again to verify that it did change that registry entry...

Play with the values, noting that some laptops (Acer is one) have their values flipped. I have one where the values and controls work in reverse. <Fn><Up> is supposed to get brighter, and on mine <Fn><Down> is brighter...

If it changes the values in the brightness registry file, but does not affect the brightness of the hardware, then report it to launchpad.

Is that enough info?
#Note to Apple users- That won't work for you because of a bug with the ACPI Interface. Change yours in MACX and reboot into Ubuntu. It will read the persistent change from the system hardware.

---

### Post by rdp1976 on 2013-04-28
When I activated Windows 8 (it was not activated for the new SSD I'd installed), the boot records were messed up. I had to do a full re-install of everything.

I used the exact same Xubuntu 13.04 USB I used the first time, and this time around the dimness problem was gone. I don't know what fixed it or how, but the problem is gone.

Thanks for your help.

---

### Post by DakoCwerf on 2013-04-29
Echoing 0 sets my screen to black, so I changed the number to something bigger
```
 echo 4000 > /sys/class/backlight/intel_backlight/brightness
```

That fixed my brightness problem on Dell notebook.

---

### Post by azeem657 on 2013-06-03
Does Ubuntu 13.04 install wifi drivers automatically on dell xps 13 ...

---

### Post by aspiteri on 2013-06-11
Have a look at this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/954661]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/954661").
Comment #43 suggests that:
```
echo 0 | sudo tee /sys/class/backlight/intel_backlight/brightness
```
...fixes the problem. Perhaps you can give this a try. 

If it does work, the command posted in post #43:
```
/bin/echo 0 > /sys/class/backlight/intel_backlight/brightness
```
...should be added to /etc/rc.local above the "Exit 0" command. 

The bug report also indicates that its been fixed in 3.8.0-18.28.

This worked for me thank you @Tos.
Dell XPS 13 Intel® Core&#8482; i7-3537U CPU @ 2.00GHz × 4 
Intel® Ivybridge Mobile 
3.8.0-23-generic #34-Ubuntu SMP Wed May 29 20:22:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by aspiteri on 2013-06-11
@azeem657 re:  
Does Ubuntu 13.04 install wifi drivers automatically on dell xps 13 ...

It did for mine:
Dell XPS 13 Intel® Core&#8482; i7-3537U CPU @ 2.00GHz × 4 
Intel® Ivybridge Mobile 
3.8.0-23-generic #34-Ubuntu SMP Wed May 29 20:22:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by lukas12345luki on 2013-08-21
Hi Toz, I have the same issue  and the first part of code works, however when I try to use the second line  it says: bash: /sys/class/backlight/intel_backlight/brightness: Permission denied

Help would be very appreciated! Thanks in advance!

---

### Post by Toz on 2013-08-21
> **lukas12345luki said:**
> Hi Toz, I have the same issue  and the first part of code works, however when I try to use the second line  it says: bash: /sys/class/backlight/intel_backlight/brightness: Permission denied

Help would be very appreciated! Thanks in advance!

Hi lukas12345luki, welcome to the forums.
The second command:
```
/bin/echo 0 > /sys/class/backlight/intel_backlight/brightness
```
...is meant to be put in the **/etc/rc.local** file (above the "exit 0" command) so that it will be run automatically at boot as the root user, so permissions will not be an issue. Its not meant to be run manually. Its the same command as the first one, only the first one is written to allow a regular user to run it by using sudo (which requires authentication to grant permissions).

---

### Post by lukas12345luki on 2013-08-22
Thanks! But, it still doesn't work, should the **/etc/rc.local **be a text file? Because If I try to open it in the Terminal it asks me for my password and then doesn't do anything though...  

Sorry if this is a stupid question, but I'm really new to this :)

Thank's for welcoming me btw. feels really good to be here! :D Appreciate your help!

---

### Post by Toz on 2013-08-23
> **lukas12345luki said:**
> Thanks! But, it still doesn't work, should the **/etc/rc.local **be a text file? Because If I try to open it in the Terminal it asks me for my password and then doesn't do anything though...  

Sorry if this is a stupid question, but I'm really new to this :)

Thank's for welcoming me btw. feels really good to be here! :D Appreciate your help!

Yes it is a text file, but you need elevated privledges to be able to edit it. Try opening it like this from a terminal window:
```
gksu mousepad /etc/rc.local
```
...you will be asked to enter your password and then you will have access to it.

---

### Post by lukas12345luki on 2013-08-23
Thanks for the quick response, again, but it still doesn't work, I enter the command, and I type in my password, but after that nothing happens, I'm really confused... could it be because of the shell difference between Ubuntu (which I'm running) and  Xubuntu (which you seem to be running), or am I just making some kind of really obvious mistake?...

Thank's a bunch for helping me out!

---

### Post by Toz on 2013-08-23
> Ubuntu (which I'm running) and Xubuntu (which you seem to be running),
Oops, I assumed you were running Xubuntu. In that case, try:
```
gksu gedit /etc/rc.local
```
They have different text editors.

---

