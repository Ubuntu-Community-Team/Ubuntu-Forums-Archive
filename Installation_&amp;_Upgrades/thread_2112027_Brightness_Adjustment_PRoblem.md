---
title: "Brightness Adjustment PRoblem"
date: 2013-02-03
forum: Installation &amp; Upgrades
---

### Post by carkaci on 2013-02-03
I have Intel Imac 11,3 (27" LED, purchased in 2009) with Radeon HD 5750 graphic card. When I installed Ubuntu 12.04 LTS, everything works fine except brigthness control. I want to mention that I didn't install any additional driver.

I tried "sudo update-grub" after changing /etc/default/grub by acpi_backlight=vendor with/without acpi_osi=Linux. Nothing changes.

What can I do to fix this issue?

---

### Post by MAFoElffen on 2013-02-03
> **carkaci said:**
> I have Intel Imac 11,3 (27" LED, purchased in 2009) with Radeon HD 5750 graphic card. When I installed Ubuntu 12.04 LTS, everything works fine except brigthness control. I want to mention that I didn't install any additional driver.

I tried "sudo update-grub" after changing /etc/default/grub by acpi_backlight=vendor with/without acpi_osi=Linux. Nothing changes.

What can I do to fix this issue?

If you go to a terminal session <cntrl-alt-T> or to a command prompt <cntrl-alt-F2> (then log in) can you:
```

setpci -s 00:02.0 F4.B=00

```
--OR--
While in a session try <function-right arrow> or <function-left arrow>, does it vary your brightness settings?

---

### Post by carkaci on 2013-02-03
I tried 
setpci -s 00:02.0 F4.B=00

Here is the result 
setpci: Warning: No devices selected for "F4.B=00"

I cannot try function-right/left arrow because, I use Microsoft Wireless Keyboard rather than Imac's default. 

(Note: Excuse me, my machine was pucheased in 2011, not in 2009)

---

### Post by MAFoElffen on 2013-02-03
Ipad... Okay

Please post the results of 
```

lspci | grep VGA

```
That will tell us the video info.

Then
```

ls /sys/class/backlight/*

```
Look for any directory name that resembles the video you have.

Then 
```

echo -n 50 | sudo tee /sys/class/backlight/video_name/brightness

```
Where the variable "n", substitute 0 to 127. 
0 should be the brightest setting. 
At variable "video_name" substitute the directory name.

If that works, play with "n" until you find a usable brightness setting. Post what that setting is and I'll tell you what to change to make that setting resident on bootup.

---

### Post by carkaci on 2013-02-03
>lspci | grep VGA

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Broadway PRO [Mobility Radeon HD 5800 Series]

>ls /sys/class/backlight/*

actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power           device      power           type


>echo -127 50 | sudo tee /sys/class/backlight/acpi_video0/brightness 
-127 50
tee: /sys/class/backlight/acpi_video0/brightness: Invalid argument

---

### Post by MAFoElffen on 2013-02-03
Hmm... invalid value.

Please post:
```

grep . /sys/class/backlight/acpi_video0/*

```
It should have output similar to this:
```

/sys/class/backlight/acpi_video0/actual_brightness:10
/sys/class/backlight/acpi_video0/bl_power:0
/sys/class/backlight/acpi_video0/brightness:10
/sys/class/backlight/acpi_video0/max_brightness:10
```
That should tell us the values it has set now.

---

### Post by carkaci on 2013-02-03
> grep . /sys/class/backlight/acpi_video0/*

/sys/class/backlight/acpi_video0/actual_brightness:8
/sys/class/backlight/acpi_video0/bl_power:0
/sys/class/backlight/acpi_video0/brightness:8
/sys/class/backlight/acpi_video0/max_brightness:16
/sys/class/backlight/acpi_video0/type:firmware

---

### Post by MAFoElffen on 2013-02-03
"brightness" is the current-setting "file".

Okay, seems values to be from 16 to 0, where 16 would be max brightness and 0 would be turned off.

Please try:
```

echo 16 | sudo tee /sys/class/backlight/acpi_video0/brightness

```
Or whatever number you think may be what you want between 0 and 16...
Lets see if that works.

---

### Post by carkaci on 2013-02-03
echo 0 | sudo tee /sys/class/backlight/acpi_video0/brightness
0


But nothing changes. Brightness is the same.

---

### Post by MAFoElffen on 2013-02-03
> **carkaci said:**
> echo 0 | sudo tee /sys/class/backlight/acpi_video0/brightness
0


But nothing changes. Brightness is the same.

Let's try this in a different format than what Ubuntu's Wiki says to follow... by tweaking it in from a different perspective.

Please try it this way:
```

sudo echo 0 | tee /sys/class/backlight/acpi_video0/brightness

```

---

### Post by carkaci on 2013-02-03
> sudo echo 0 | tee /sys/class/backlight/acpi_video0/brightness
tee: /sys/class/backlight/acpi_video0/brightness: Permission denied
0

---

### Post by MAFoElffen on 2013-02-03
Okay... ???

Go back to using the format:
```

echo 0 | sudo tee /sys/class/acpi_video0/backlight

```
Then afterwards:
```

grep . /sys/class/backlight/acpi_video0/*

```
To see if the backlight setting is actually getting changed or not.

If the backlight setting is getting changed in that system file, but nothing happens hardware wise, then I suspect that there may be an underlying  reason why the system is either ignoring it or doesn't understand it. If so, then this probably needs to escalate to a launchpad backlight bug. 

If that setting is not getting changed, then we just need to find another way to change it.

---

### Post by carkaci on 2013-02-03
> echo 0 | sudo tee /sys/class/acpi_video0/backlight
tee: /sys/class/acpi_video0/backlight: No such file or directory
0


>grep . /sys/class/backlight/acpi_video0/*
/sys/class/backlight/acpi_video0/actual_brightness:0
/sys/class/backlight/acpi_video0/bl_power:0
/sys/class/backlight/acpi_video0/brightness:0
/sys/class/backlight/acpi_video0/max_brightness:16
/sys/class/backlight/acpi_video0/type:firmware

and I also try
echo 0 | sudo tee /sys/class/backlight/acpi_video0/brightness
0

then 

> grep . /sys/class/backlight/acpi_video0/*
/sys/class/backlight/acpi_video0/actual_brightness:0
/sys/class/backlight/acpi_video0/bl_power:0
/sys/class/backlight/acpi_video0/brightness:0
/sys/class/backlight/acpi_video0/max_brightness:16
/sys/class/backlight/acpi_video0/type:firmware

---

### Post by carkaci on 2013-02-03
> **carkaci said:**
> > echo 0 | sudo tee /sys/class/acpi_video0/backlight
tee: /sys/class/acpi_video0/backlight: No such file or directory
0


>grep . /sys/class/backlight/acpi_video0/*
/sys/class/backlight/acpi_video0/actual_brightness:0
/sys/class/backlight/acpi_video0/bl_power:0
/sys/class/backlight/acpi_video0/brightness:0
/sys/class/backlight/acpi_video0/max_brightness:16
/sys/class/backlight/acpi_video0/type:firmware

and I also try
echo 0 | sudo tee /sys/class/backlight/acpi_video0/brightness
0

then 

> grep . /sys/class/backlight/acpi_video0/*
/sys/class/backlight/acpi_video0/actual_brightness:0
/sys/class/backlight/acpi_video0/bl_power:0
/sys/class/backlight/acpi_video0/brightness:0
/sys/class/backlight/acpi_video0/max_brightness:16
/sys/class/backlight/acpi_video0/type:firmware

Nothing changed in the screen brightness.

---

### Post by carkaci on 2013-02-03
Maybe, I am wrong, and sounds nonsense but
when i reboot the system and start with MAC OS, then changing brigtness in the MACOS then restart the UBUNTU brigtness decreases.

I will try it again, but now it is too late for me, I must sleep :)

---

### Post by MAFoElffen on 2013-02-04
Will catch you tomorrow then.

Sorry for the misspelling. You caught that and corrected. Hey, I did notice in your last posts that it had changed from a value of 8 to 0... That was after the mispaelling and before you changed it to correct, so it did not take it from there. It was already set from 8 to 0.

So changing that value from 0 to 0, you will not see a change. Tomorrow try 5? Funny that something should stay resident after a reboot from one OS to another... Who would think, eh?

---

### Post by carkaci on 2013-02-04
Hi,  here are the results.

> echo 5 | sudo tee /sys/class/backlight/acpi_video0/brightness
5
then 
> grep . /sys/class/backlight/acpi_video0/*
/sys/class/backlight/acpi_video0/actual_brightness:5
/sys/class/backlight/acpi_video0/bl_power:0
/sys/class/backlight/acpi_video0/brightness:5
/sys/class/backlight/acpi_video0/max_brightness:16
/sys/class/backlight/acpi_video0/type:firmware

Nothing changed.

I also wanted to mention that in UBUNTU "System Settings"/"Brightness and Lock" Menu when I change the Brightness bar, the above values are also changed, without doing that in the terminal.

By the way, I changed brightness to low level in MACOS, then reboot it with UBUNTU, screen brightness is low. I changed it to High level in MACOS, then reboot it with UBUNTU screen brightness is high. Without regarding the above values. It sounds crazy but I am very serious. 

I realized that, when I change brightness level in MACOS, then after rebooting the system, in the beginning even REFit menu (before selecting an OS to be loaded) brightness level is also changed.

Please, forgive me if I am wrong but I think this may happen beacuse of the EFI properties of the Intel IMACs. I think we can focus on REFit, Ubuntu installation, and ~200MB EFI Partitions (where firmwares & booting programs are stored). I guess that brightness level may be stored in somewhere in  EFI partition. Although these may be true, we have another problem still stand that UBUNTU cannot actually change the level of brightness whatever the current system brightness level.

Best Regards.

---

### Post by MAFoElffen on 2013-02-04
Yes. I searched on the Launchpad bugs and this does seem to be a new unique bug that needs to be addressed.

It show be reported in this class:
> 
Backlight control does not work, but there are entries in /sys/class/backlight.

This may require the ACPI backlight driver to not take control so that a vendor specific driver will have a chance to register.

But you need to stress that this goes beyond just the applet not working. Your data does change in Ubuntu for those entries and the acpi interface to the Linux Kernel is not able to use that changed data to change the hardware brightness setting.

You have found a workaround, but that workaround is outside of the Ubuntu system or to Linux itself.

Please report this bug using this format in a terminal session:
```

sudo ubuntu-bug linux 

```

They are going to ask you to submit data and dumps. The instructions for those are in this Wiki entry:
[Ubuntu Wiki- /Kernel/Debugging/Backlight]("https://wiki.ubuntu.com/Kernel/Debugging/Backlight")
The instructions are for Ubuntu Desktop on a regular laptop, but will crossover to your IPad.

Curious to see how this resolves. Please post here with the Launchpad bug ID so other users later searching on this problem can refer to it or add themselves to it.

Please mark this thread as solved after Lauchpad gets a fix for it.

---

### Post by carkaci on 2013-02-04
Here is the reported Bug Address

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1115555](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1115555)

---

### Post by MAFoElffen on 2013-02-04
Thanks.

Subscribed to the bug. Linked the bug to this thread for reference. Added comments to the bug report to clarify it as something new and unique.

---

### Post by carkaci on 2013-02-05
Thank you for support.

---

### Post by lehcen on 2013-02-14
Hi guys, i have the exact same problem as Carkaci on my mac. cant adjust brightness and when i go on macos and go back to ubuntu the brightness changes again. have you guys figured it out?

---

### Post by MAFoElffen on 2013-02-14
> **lehcen said:**
> Hi guys, i have the exact same problem as Carkaci on my mac. cant adjust brightness and when i go on macos and go back to ubuntu the brightness changes again. have you guys figured it out?
lehcen-

Please goto:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1115555](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1115555)

Create a launchpad ID (register) and where that bug says:
"This bug affects 1 person. Does this bug affect you?"  

After logged in, click on that link to join that bug.

Remember, the more members/users that join it as affecting them, the more emphasis they will put into correcting it. As it stands, they only "know" that it affects Carkaci so far... Please help yourselves and him. This is how this works for you.

---

### Post by lehcen on 2013-02-14
I did thanks :D

---

