---
title: "Desktop displays in pieces"
date: 2011-07-07
forum: Installation &amp; Upgrades
---

### Post by LenK on 2011-07-07
I am completely new to (L)ubuntu. I have a Sager laptop with an ATI Rage Mobility M3 AGP 2X. I booted 10.10 and 11.04 from the live CD. In both cases I get the message "base address not set - upgrade bios or use force_addr=0xaddr". The desktop displays in pieces, with vertical overlays repeating parts of it, slightly different between the 2 versions. I am guessing that this is related to the error message? I am also guessing that "force_addr..." is a config entry, and that I cannot access it without an install? I would rather not mess with bios, unless it is the only solution. I went ahead with an install, since the laptop was too slow to be useful with Windoze Xtra Pathetic, and thinking that I might have more success with an installed system. I did some more searching - found references to my error message which were related to running on a virtual machine. I tried "vga=771" as a boot parm with the live disc - no change. 

It appears that "vga=nnn" affects the display only until the desktop loads. I tried various values. The screen with Lubuntu and the progress dots was affected, but the desktop did not change.

I then tried connecting an old Viewsonic G790 19" monitor and BINGO - the desktop displayed properly, on both the G790 and the laptop screen. While I had the problem, the largest resolution value in monitor preferences was 1024x768. With the "fix", the default setting is 1280x1024.

I concluded that the "vga=" is not used by the (gnome?) display manager. It must get its values elsewhere, but WHERE? With some manual searching of files, I found something in /etc/vga/libvga.config under "Monitor type". The active setting there was for a 1024x768 monitor, which agrees with the problem state. There is one example for a 1280x1024 monitor, but it has a refresh of 60, whereas monitor preferences showed 85. Also, the values are not obvious, and I haven't taken the time to tinker yet. I can't change anything until I find out how to log in as admin.

Conclusion...I am writing this in Chromium on my laptop, which would have been impossible with the display problem. So I have a usable lubuntu install, but my laptop is not very portable if it needs a 30-pound CRT attached to boot. There must be someone out there who is familiar enough with this situation to provide a solution, or at least know where to look?

Thanks in advance - Len

---

### Post by SteveDee on 2011-07-08
> **LenK said:**
> ...then tried connecting an old Viewsonic G790 19" monitor and BINGO - the desktop displayed properly, on both the G790 and the laptop screen....

This is good news, as it shows you can get a stable display on your laptop screen. I don't know what your problem is, but here are a few ideas.
Open LXTerminal and type:-
```

xrandr -q

```
This will give info on your current display and range of settings. Maybe do this twice, once with the external monitor connected, then again with the screen all messed up. If you can't read the screen clearly enough, try typing:-
```

xrandr -q > myscreen

```
This will save the output to a file called myscreen in your home directory. You can view this later, when you reconnect the other monitor.

If you need to manually set the screen resolution (because you need 1280x1024 rather than 1024x768 ) then type something like this:-
```

xrandr -s 1280x1024

```

Re-admin login, you basically run in your own account and just enter your own password again (when asked to do so) to run special tasks.

If you are new to Ubuntu/Lubuntu you may want to start here: [http://ubuntuguide.org/wiki/Ubuntu:Natty](http://ubuntuguide.org/wiki/Ubuntu:Natty)

---

### Post by LenK on 2011-07-08
Steve, thanks for your reply.

> **SteveDee said:**
> 
If you need to manually set the screen resolution (because you need 1280x1024 rather than 1024x768 ) then type something like this:-
```

xrandr -s 1280x1024

```


When I tried this, the response was that that size was not available, which agrees with what monitor preferences displayed. Somewhere along the boot process, code must be checking attached displays. That's the only way I can see that explains the behaviour. I found the following in the documentation that you referred to...
[I]Any background image can be used for Grub2 by placing the image in the /boot/grub folder and then reconfiguring Grub2:
The image ought to be the same size as the **Grub2 startup resolution specified in /etc/default/grub (e.g. 1024x768 )** [/I]
When I looked at this file, the default resolution was commented. Anyway, I'm getting in way over my head, so maybe it's time to wait for further input, before I cause other problems.

Here are the results of the xrandr queries:

bad screen...
[FONT="Lucida Console"]Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       60.0* 
   800x600        60.0     56.0  
   640x480        60.0[/FONT]

good screen...
[FONT="Lucida Console"]Screen 0: minimum 640 x 350, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      85.0*    75.0     60.0  
   1024x768       85.0     75.0     70.0     60.0  
   800x600        85.0     75.0     72.0     60.0     56.0  
   640x480        85.0     75.0     73.0     67.0     60.0  
   640x400        85.0  
   640x350        85.0 [/FONT]

> **SteveDee said:**
> 
Re-admin login, you basically run in your own account and just enter your own password again (when asked to do so) to run special tasks.


I have encountered what you described, but there are other situations, such as
1. modifying a config file and saving it - I want to try changing /etc/vga/libvga.config
2. when I tried to download flash player, and selected "APT for Ubuntu 10.4+", a window popped up saying Chromium needs to launch an external application...proceeding just resulted in a blank (Google) page. I am guessing this is because of permissions, but it really is time for me to look at some documentation, so I will start with...

> **SteveDee said:**
> 
If you are new to Ubuntu/Lubuntu you may want to start here: [http://ubuntuguide.org/wiki/Ubuntu:Natty](http://ubuntuguide.org/wiki/Ubuntu:Natty)

---

### Post by dino99 on 2011-07-08
into a terminal:

sudo rm /etc/X11/xorg.conf
sudo apt-get install xserver-xorg-video-r128


sudo aticonfig --initial

---

### Post by LenK on 2011-07-08
len@Lenux:~$ sudo rm /etc/X11/xorg.conf
[sudo] password for len: 
rm: cannot remove `/etc/X11/xorg.conf': No such file or directory
len@Lenux:~$ sudo apt-get install xserver-xorg-video-r128
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-r128 is already the newest version.
xserver-xorg-video-r128 set to manually installed.
The following packages were automatically installed and are no longer required:
  ndiswrapper-common libdmraid1.0.0.rc16 archdetect-deb python-pyicu
  libdebian-installer4 cryptsetup reiserfsprogs rdate libcairomm-1.0-1
  libglibmm-2.4-1c2a python-webkit libatkmm-1.6-1 libsigc++-2.0-0c2a
  libpangomm-1.4-1 btrfs-tools libgtkmm-2.4-1c2a localechooser-data apt-clone
  dpkg-repack libcheese-gtk18 libdebconfclient0 dmraid libgnome-desktop-2-17
  hwdata
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
len@Lenux:~$ sudo aticonfig --initial
sudo: aticonfig: command not found

---

### Post by SteveDee on 2011-07-08
> **LenK said:**
> ...startup resolution specified in /etc/default/grub (e.g. 1024x768 )[/B] [/I]
When I looked at this file, the default resolution was commented... 

...I have encountered what you described, but there are other situations, such as
1. modifying a config file and saving it - I want to try changing /etc/vga/libvga.config...

1. The startup resolution is probably not an issue if the login screen is OK, and the problem starts when you log into Lubuntu (maybe you can confirm that).

2. To modify this kind of file in Lubuntu:-
 - Open the file manager (PCManFM) and navigate to /etc
 - Highlight the vga folder then select menu "Tools" > "Open current folder as Root"
 - Enter your normal password in the dialog box when requested.
 - Now double click on libvga.config file
This will open the editor (Leafpad) and you will be able to make changes and save the file.


PS: I forgot to suggest you also look at this: [https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

However, I still have no idea why connecting an external monitor fixes your laptop screen...

---

### Post by LenK on 2011-07-08
> 
PS: I forgot to suggest you also look at this: [https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

There was some material in this documentation that appeared to be right on the money, but unfortunately I could not find the files referred to, that run scripts for GDM and/or KDM. I am guessing that this is because I am dealing with Lubuntu, not Ubuntu, so I am going to try dynamically.

Update

Tried adding a new mode dynamically as described in the above doc. The format for the modeline (and the resulting mode entry) looked completely different from the rest...

   1280x1024      85.0*    75.0     60.0  <=== this the one that works
   1024x768       85.0     75.0     70.0     60.0  
   800x600        85.0     75.0     72.0     60.0     56.0  
   640x480        85.0     75.0     73.0     67.0     60.0  
   640x400        85.0  
   640x350        85.0
This one is added by the modeline  
  [COLOR="Red"]1280x1024_85.00 (0x95)  159.4MHz
        h: width  1280 start 1376 end 1512 total 1744 skew    0 clock   91.4KHz
        v: height 1024 start 1025 end 1028 total 1075           clock   85.0Hz[/COLOR]

selecting the new mode had no effect, so I doubt that including it in a script would have worked.

Running out of options.

---

### Post by SteveDee on 2011-07-09
I'd still like to know if your login screen is OK (i.e. does the problem only appear when you reach the desktop after loggin in).

Also, when its running OK with 2nd monitor connected, if you simply unplug 2nd monitor (without powering down, log out & so on) does the laptop screen continue to run OK?

In the absence of anyone else chipping in with ideas, I would be inclined to create an xorg.conf file and experiment with monitor & driver settings written into this file. Start with something very basic like this:-
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection


Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync 31.5-48.5
	VertRefresh 50-70
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 24
	SubSection "Display"
	Depth 24
	Modes "800x600"
	EndSubSection
EndSection


```

---

### Post by LenK on 2011-07-09
> **SteveDee said:**
> I'd still like to know if your login screen is OK (i.e. does the problem only appear when you reach the desktop after loggin in).

The problem in answering this question is that I chose to have me logged in automatically, and I don't know how to change that.

> **SteveDee said:**
> Also, when its running OK with 2nd monitor connected, if you simply unplug 2nd monitor (without powering down, log out & so on) does the laptop screen continue to run OK?

Yes, it continues.

I thought myself that configuring the monitor would be the next step, but I did not know what values to use. I will give your code a try.

Again, many thanks for all your help.

---

### Post by LenK on 2011-07-09
Steve, **[COLOR="Red"][SIZE="4"]your code worked[/SIZE][/COLOR]** - thanks muchly.

I then tried adding "1024x768" and "1280x1024" to modes. The 1024x768 works, but not the 1280x1024. I would not be disappointed at all if this is the final solution; any further tweaking can wait.

I hope others can benefit from this thread.

Update...

It didn't take much tweaking - I just had to find the correct horizsync values. I knew I had seen them before, but had to search a bit before I found them in /etc/vga/libvga.config

This is the updated version of the xorg.conf that you provided

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync 31.5-**64.3**
	VertRefresh 50-**85**
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 24
	SubSection "Display"
	Depth 24
	Modes "**1280x1024**"
	EndSubSection
EndSection
```

Once again, Steve, I owe you. I hope I can return the favour. Thanks so much for you perseverance.

---

