---
title: "Feisty install hangs with black screen"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by LandRover on 2007-09-22
Hey,
I've been try all posible solutions that I could find there at the forum without any luck.
I keep getting black screens right after "Start and/or Install screen".

My system specs:
[list]
[*]CPU: Intel Q6600 
[*]RAM: Cellshock 4GB 800MHz
[*]MOBO: Gigabyte p35 DQ6 (LAN onboard)
[*]HDD: 6x500GB YS WD - RAID0 (via mobo's controller)
[*]GFX: BFG 8800GTX OC2
[*]Monitors: [list]
[*] Samsung SyncMaster 226BW = Native res: 1680x1050 (cable: DVI -> DVI)
[*] Samsung M81 40" - Native res: 1920x1080 (cable: DVI-> HDMI)
[/list]
[*]Other OS': Vista x64, WinXP x64
[/list]

I've even managed to view the splash screen by hiting F4 at the boot menu and selecting resolution 1024x468x32 but after a while the splash gone and the monitor loses the signal.   At this point if I hit enter few times it prolly logs in and the monitor lakes a driver.

via VMware at winXP I've managed to install ubuntu without any problem but I would like a clean setup.

Any tips are welcome :)

Thanks!

---

### Post by rsambuca on 2007-09-22
It is probably due to the 8800 video card (quite new).  If you are going to install it, you should be fine if you use the alternate installer.  If you are just going to test run the liveCD, I think some people have been having success using different boot options, but I am afraid I don't know what they are offhand (perhaps try adding 'nosplash' as a boot option.

---

### Post by Pumalite on 2007-09-22
Try:

At the LiveCD initial boot screen:
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

---

### Post by LandRover on 2007-09-22
> **rsambuca said:**
> It is probably due to the 8800 video card (quite new).  If you are going to install it, you should be fine if you use the alternate installer.  If you are just going to test run the liveCD, I think some people have been having success using different boot options, but I am afraid I don't know what they are offhand (perhaps try adding 'nosplash' as a boot option.

Well, I'm sure someone outta there using 8800 regardless its being new card.
btw, for 'nosplash' I removed 'splash' from the F6 but its not a solution, the login still hangs with black screen.


> **Pumalite said:**
> Try:

At the LiveCD initial boot screen:
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

First of all, break=top, when I do that it shows me totaly black screen but it seems I can type blindly.
I wrote blindly 
modprobe piix and exit.
it continued but when it got to the part I need to login, it lost the signal again.

tried with both break=top, break=bottom same result.

:(

---

### Post by Pumalite on 2007-09-22
I agree with rsambuca; your problem is this:

# GFX: BFG 8800GTX OC2
# Monitors:

    * Samsung SyncMaster 226BW = Native res: 1680x1050 (cable: DVI -> DVI)
    * Samsung M81 40" - Native res: 1920x1080 (cable: DVI-> HDMI)
 Try Gutsy Alternate CD if you don't depend on the OS for your living. It's in testing. Stable comes out in October. I'm writing to you from Tribe5. Better at recognizing newer hardware.

---

### Post by dashaun on 2007-10-09
I was struggling with Feisty install.

I was getting to the blank screen with just flashing "_".

I followed the instructions above and added "break=bottom" to boot settings.  Then I edited my xorg.conf.  

I have an nVidia Quadro NVS 440.  It was recognizing multiple GPU and multiple monitors, but the it had the first BusID address wrong.

I changed:

```

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nv"
        BusID           "PCI:6:0:0"
EndSection

```

to

```

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nv"
        BusID           "PCI:7:0:0"
EndSection

```

then "exit" and everything worked!

I'm sure this won't work for everybody.  YMMV

---

### Post by DDuong on 2007-10-09
Not sure if this issue has been resolved or not but have you tried using the alternative cd instead of the live cd?  I've read that helped if the live cd is failing.

---

