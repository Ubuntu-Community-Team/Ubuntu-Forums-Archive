---
title: "Command to check which videocard driver is installed"
date: 2012-10-08
forum: Installation &amp; Upgrades
---

### Post by GeForce 9500GT on 2012-10-08
What is the correct command to check which VGA driver is installed and loaded/running?

---

### Post by The Cog on 2012-10-08
I use 
```
lspci -v | less
```
and the search for VGA.

---

### Post by TheFu on 2012-10-08
I don't know a single command. Perhaps someone else will chime in with more.

I'd start by determining the hardware:
**$ sudo lshw -c display**

Then it depends on the driver.  nvidia has 1, ATI another, Intel another, virtual machines and F/LOSS versions yet another.

Then I'd use** lsmod** with a **grep** to hone in on the exact driver. For example:
**$ lsmod | grep -i nvidia**
or
**$ lsmod | grep fglrx**
or
**$ lsmod | grep video**
or ... 

Then to find a specific version, I'd ask the package manager which file is owned by which package.
$ dpkg -l | grep fglrx
which shows 2:8.960-0ubuntu1.1 on an ATI machine.
$ dpkg -l | grep nvidia
which returns 290.10-0ubuntu1~lucid~xup1 on an nvidia machine.

I hope there's an easier way.

---

### Post by stinkeye on 2012-10-08
One of many...
```
lspci -nnk | grep -iA2 vga
```

eg
```
[COLOR="Olive"]glen@Quantal:~$[/COLOR] lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: **NVIDIA Corporation G96 [GeForce 9400 GT]** [10de:0641] (rev a1)
	Subsystem: XFX Pine Group Inc. Device [1682:4009]
	Kernel driver in use: **nvidia**
```

---

### Post by GeForce 9500GT on 2012-10-09
Okay, thanks everybody! I can work with this.
 
I was just curious if the driver of x-swat is running on my system. When i go to Additional Drivers i see that the Nvidia driver current is not enabled although the nvidia-current driver of x-swat is installed. Can i asume that i have the driver installed?

---

### Post by bogan on 2012-10-09
Hi!, **GeForce 9500GT**,
```
sudo apt-cache policy nvidia-current
```Will tell you which version is installed and available, as well as its source.

Though it will not work for drivers not installed with dpkg, for example the nvidia.com downloaded versions.

For those run: ```
cat  /sys/module/nvidia/version
```

Chao!, **bogan**.

Reason for editing: version note added

---

### Post by GeForce 9500GT on 2012-10-09
> **bogan said:**
> .....
 
Thanks! =D>
 
That first command is what i was looking for!

---

### Post by bogan on 2012-10-09
> **GeForce 9500GT said:**
> Thanks! =D>
 
That first command is what i was looking for!
Hi!,

Great, glad to help- Please mark the thread as Solved - 'Thread Tools' above.

Enjoy! Chao!, **bogan.**

---

### Post by varunendra on 2012-10-11
Just wanted to add something..
> **TheFu said:**
> I don't know a single command. Perhaps someone else will chime in with more.

I'd start by determining the hardware:
**$ sudo lshw -c display**
@TheFu, have you observed the entire output of lshw command? It also (always, if used with sudo) lists the driver (driver=..) currently loaded for the listed device.
[COLOR=DarkRed][**Edit :** I should add that this driver name may not be same as the actual module name in some cases (for example, rtxxxx drivers are shown as "RALINK" in lshw output). So the 'lspci -nnk' method suggested below is more promising for finding the actual module name which can be used with 'modinfo' command][/COLOR]

The 'lspci -nnk' method suggested by *stinkeye* is the next most commonly used method to figure that out.

Once the driver in use is determined, you can use modinfo command to check the details (including source version) of that particular module (i.e., driver). For example-
```
modinfo nvidiafb
```It gives all the important details about a module and is not dependent on how the module (driver) was built or installed.

Hope it adds some value to the thread.

---

