---
title: "After install: Black Screen"
date: 2007-07-18
forum: Installation &amp; Upgrades
---

### Post by RavynX on 2007-07-18
Hi all, I've been a windows user for as long as I can remember and I've decided to take the plunge and try Linux out w/ Ubuntu.  I downloaded the ubuntu-7.04-desktop-amd64.iso file, burned it as an image and rebooted to start the install.  I got to the first screen and selected Start/Install Ubuntu where it then proceeded to show me the kernel was loading and then I got a black screen with the cd churning for a little while.

So I booted back to Windows, downloaded the alternate version, ubuntu-7.04-alternate-amd64.iso, burned that and rebooted to install.  The install went flawlessly up until I rebooted to go into the Ubuntu desktop.  After the POST and loading the kernel the screen went black as if it was about to load a splash screen (if Ubuntu does that, I dont' know... yet).  So it just sits there w/ a black screen.  I hit Ctrl-Alt-Del (not sure if that's a valid Linux command, but I gave it a shot anyways).  About 10 or so seconds after the Ctrl-Alt-Del it will reboot.

Dell 22" Widescreen (using the DVI connector) (1680x1050)
Intell e6600 Core 2 Duo 2.4Ghz 
eVGA 680i motherboard  ( model: 122-CK-NF68 )
2 GB Cosair XMS DDR2 400Mhz (PC-3200) @ 4-4-4-12-2T
eVGA 8800 GTS 640MB PCI-e video card
Audigy 2 sound card
40 GB Maxtor Harddrive ATA 133 (my other 120GB SATA drive has Windows XP on it still)

I plan on Dual-booting once I get Ubuntu up and running.


I'm a little lost on what to do from here.  Do I need to plug my monitor into the VGA connector on the 8800 card using a DVI-to-VGA or should I try something else first?

---

### Post by ReaderRat on 2007-07-18
> Dell 22" Widescreen (using the DVI connector) (1680x1050)
Intell e6600 Core 2 Duo 2.4Ghz
eVGA 680i motherboard ( model: 122-CK-NF68 )
2 GB Cosair XMS DDR2 400Mhz (PC-3200) @ 4-4-4-12-2T
[COLOR="Red"]eVGA 8800 GTS 640MB PCI-e video card[/COLOR]
Audigy 2 sound card
40 GB Maxtor Harddrive ATA 133 (my other 120GB SATA drive has Windows XP on it still)

Have you loaded the driver for the video card?

---

### Post by ReaderRat on 2007-07-18
Here is a site on nVidia Drivers:

[https://help.ubuntu.com/community/RestrictedDrivers/NVIDIA](https://help.ubuntu.com/community/RestrictedDrivers/NVIDIA)

---

### Post by ReaderRat on 2007-07-18
You need the[COLOR="Blue"] nvidia-glx[/COLOR] driver. I don't know how to install it.

---

### Post by alfarin on 2007-07-18
Check my thread, might help.

[http://ubuntuforums.org/showthread.php?t=502920&page=2]("http://ubuntuforums.org/showthread.php?t=502920&page=2")

---

### Post by RavynX on 2007-07-18
> **ReaderRat said:**
> Here is a site on nVidia Drivers:

[https://help.ubuntu.com/community/RestrictedDrivers/NVIDIA](https://help.ubuntu.com/community/RestrictedDrivers/NVIDIA)
I can't really load the drivers before installing Ubuntu, but I will definitely look at those once I get the screen to show.  Thanks!


> **alfarin said:**
> Check my thread, might help.

[http://ubuntuforums.org/showthread.php?t=502920&page=2]("http://ubuntuforums.org/showthread.php?t=502920&page=2")
I saw another post and saw you reference your thread.  I just read it and found my thread again.  I will try those solutions when I get home and will get back to you on it.  Thank you very much.  :)

---

### Post by cprofitt on 2007-07-18
I was having the same issue and removed the splash from my menu.lst file:

see this thread for details: [http://ubuntuforums.org/search.php?searchid=23911977](http://ubuntuforums.org/search.php?searchid=23911977)

It is now able to boot... but still curious why the splash screen causes the issue.

---

### Post by RavynX on 2007-07-18
> **PrivateVoid said:**
> I was having the same issue and removed the splash from my menu.lst file:

see this thread for details: [http://ubuntuforums.org/search.php?searchid=23911977](http://ubuntuforums.org/search.php?searchid=23911977)

It is now able to boot... but still curious why the splash screen causes the issue.

Says it couldn't find the thread.

---

### Post by RavynX on 2007-07-19
> **alfarin said:**
> Check my thread, might help.

[http://ubuntuforums.org/showthread.php?t=502920&page=2]("http://ubuntuforums.org/showthread.php?t=502920&page=2")

Ok, so as I type this, I'm currently running in Ubuntu Live CD.  What happened was that I tried booting up again w/o either CD and when it black-screen after the kernel load I tried the CTRL-ALT-F1 and that didn't work.  So what I did was put the Ubuntu Live CD back in, booted it, Pressed F4 and changed VGA to 1280x1024 @ 32.  Then I selected the first option to Install/Start Ubuntu and then I got the loading screen.

It booted up, I double clicked the Install icon on the desktop and went through the whole she-bang.  Then it asked me to reboot and make sure I took out the CD.  So when it was starting to reboot it went back to that Ubuntu splash screen w/ the loading bar, but this time the orange bar was disappearing on the right hand side rather than appearing on the left hand side like it was when it was loading.

Now, my current issue is that it pops the CD out when I have 1.5 orange bars remaining on the right hand side.  A message in smaller text says "Make sure you take the CD out and press ENTER to reboot."  I do that, and nothing happens.  Here, I can press CTRL-ALT-F1 and I get the CLI, but I don't know what to type in order for it to reboot properly.  If I just shut it down it just boots up again (I have to do the F4 thing again for the video to work) and I still have that install icon on the screen.

Any suggestions?  I think this is past where your thread ended up, Alfarin.

---

### Post by RavynX on 2007-07-19
I'm thinking there might be an issue since I though I successfully installed it using the Alternate disk the first time and then I tried installing it again using the Live CD.  Anyways, kind of acting as a bump for this thread.

Anyone having similar issues after trying to reboot after installing it via Live CD?

---

### Post by Herman on 2007-07-19
One of my computers has a new monitor with 1680 x 1050 resolution, and neither Ubuntu nor Debian will install and have a working monitor. It's because it doesn't set the right resolutions in /etc/X11/xorg.conf.

Whenever I install in that computer, I get a black screen.

Then I just boot up the LiveCD and mount the new install, paste in the right resolutions in /etc/X11/xorg.conf, reboot, and everything is fine, no problem! :)

I'm not sure if you're having that exact problem, but I thought I'd post that in as a tip anyway.

Regards, Herman :)

---

### Post by RavynX on 2007-07-19
So I went back and booted to Ubuntu again but this time I did the CTRL-ALT-F1 while it was on the desktop and an error message came up in the prompt window...

```

ubuntu@ubuntu:~$[235.605788]bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
ubuntu@ubuntu:~$

```

I could still type so I typed in 

```
sudo dpkg-reconfigure xserver-xorg
```

and I was able to reconfigure.  But I wasn't able to get back to the desktop using...

```
serverx
```

I ran the CD check from the Ubuntu splash screen and it came up with no errors.  Any ideas?

---

### Post by bail_w on 2007-07-20
Well, i was experiencing black screen also, no matterr what VGA resolution i chose during the boot up Disc, i will get black screen afterward but after i change my monitor it fixed every thing. Here are my spec:

Intel Pentium Dual E2140 @ 3.6Ghz
Asus P5B Motherboard
2GB DDR2 Ram
ATI X800XL Video card
Dell 2405 FPW --> Change to AOC 19" widescreen (fixed the black screen)

Therefore, you may try to boot it up with another monitor.


Edit: btw, i set the screen resoultion to 1280 x 1024 32

---

### Post by rillip on 2007-07-20
> **RavynX said:**
> So I went back and booted to Ubuntu again but this time I did the CTRL-ALT-F1 while it was on the desktop and an error message came up in the prompt window...

```

ubuntu@ubuntu:~$[235.605788]bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
ubuntu@ubuntu:~$

```

I could still type so I typed in 

```
sudo dpkg-reconfigure xserver-xorg
```

and I was able to reconfigure.  But I wasn't able to get back to the desktop using...

```
serverx
```

I ran the CD check from the Ubuntu splash screen and it came up with no errors.  Any ideas?

Typically you would start the gui with ```
sudo startx
```  

In regards to how to shutdown properly from a command line, type
```
 sudo shutdown -r now
```  This reboots immediately.  Leaving off -r is an imediate shutdown.  You can also do ```
 sudo init 6
``` to reboot, or ```
sudo init 0
``` for shut down.

---

### Post by Herman on 2007-07-20
You should try mounting your Ubuntu install in your Ubuntu LiveCD and take a look at your /etc/X11/xorg.conf file.
Does it have mod lines like this?
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV280 [Radeon 9200 SE]"
        Monitor         "AL2016W"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1360x850" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200" "1360x850" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200" "1360x850" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1600x1200" "1360x850" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1360x850" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1360x850" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

```


... or do they look more like this,
```
Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc RV280 [Radeon 9200 SE]"
    Monitor        "AL2016W"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1920x1200" "1680x1050" "1280x800" "1152x720" "800x500"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1920x1200" "1680x1050" "1280x800" "1152x720" "800x500" 
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1920x1200" "1680x1050" "1280x800" "1152x720" "800x500"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1920x1200" "1680x1050" "1280x800" "1152x720" "800x500"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1920x1200" "1680x1050" "1280x800" "1152x720" "800x500"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1920x1200" "1680x1050" "1280x800" "1152x720" "800x500"
    EndSubSection
EndSection
```

You may need to edit your mod lines.

You can follow the instructions in the following link to mount your installed Ubuntu system in your LiveCD and get your /etc/X11/xorg.conf file. [                                  Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD").
Maybe you should post a copy of that file here so someone can help you better. Your problem and solution will both probably have something to do with that file.

Regards, Herman :)

---

### Post by RavynX on 2007-07-20
> **Herman said:**
> You should try mounting your Ubuntu install in your Ubuntu LiveCD and take a look at your /etc/X11/xorg.conf file.
Does it have mod lines like this?

....

You may need to edit your mod lines.

You can follow the instructions in the following link to mount your installed Ubuntu system in your LiveCD and get your /etc/X11/xorg.conf file. [                                  Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD").
Maybe you should post a copy of that file here so someone can help you better. Your problem and solution will both probably have something to do with that file.

Regards, Herman :)

The lines look like this...

```

Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8800 GTS]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8800 GTS]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```


It's not letting me edit the file even though I'm under ubuntu@ubuntu.

---

### Post by RavynX on 2007-07-20
Alright, I'm back home again and tried mounting the drive...

```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    74878964    37439451   83  Linux
/dev/hda2        74878965    78172289     1646662+   5  Extended
/dev/hda5        74879028    78172289     1646631   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

```

ubuntu@ubuntu:~$ ls
Desktop
ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu

```

```

ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda1/media/ubuntu
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
ubuntu@ubuntu:~$ 

```

---

### Post by Herman on 2007-07-21
```
sudo mount -t ext3 /dev/hda1/media/ubuntu
```
It looks to me as if you made a small syntax error, you just need to make a space in between /dev/hda1 and /media/ubuntu and it should work then,
```
sudo mount -t ext3 /dev/hda1 /media/ubuntu
```
Regards, Herman :)

---

### Post by Evans132 on 2007-07-21
Try this:

When the machine first reboots hit ESC key to go into grub menu and boot the machine into recovery mode.
Next, login as your user, then install your video drivers
I believe for NVidia it's 
```
sudo apt-get install nvidia-glx
```
Next, make a backup of xorg.conf file
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Then, edit the xorg.conf file 
```
sudo nano /etc/X11/xorg.conf
```
Under the "Module" section, replace "nv" with "glx"
Under the "Device" section, make sure that "Driver" says “nvidia”
Under the "Screen" section, add the following line:
```
Option "RenderAccel" "true"
```
Save the new xorg.conf  (CTRL+O to save, then CTRL+X to exit nano)
Next reconfigure the xserver settings
```
sudo dpkg-reconfigure xserver-xorg
```
Set the driver to nvidia then plug in all the refresh rate ranges for your monitor.

After that reboot the machine and see if smoke comes out of it...j/k 

If the system is still flakey just blow it all away and reinstall then repeat the video driver install. Good luck

---

### Post by RavynX on 2007-07-21
> **Herman said:**
> 
It looks to me as if you made a small syntax error, you just need to make a space in between /dev/hda1 and /media/ubuntu and it should work then,

Whoops!  Thanks, I'll give that a go.


> **Evans132 said:**
> Try this:

When the machine first reboots 

That's the issue I'm having...  I run LiveCD, get into the desktop, run the install icon, everything goes peachy and then when it asks me to reboot I hit the button and it starts to shutdown, pops the CD out & asks me to press ENTER.  I do so, and it just sits there with a little bit of orange bar left.  I'm not sure if just turning off the system is okay or if it will mess up the install process.

---

### Post by Herman on 2007-07-21
RavynX,
Theres a high probability that  Evans132's solution will be the more appropriate one.
I have the experience of installing in one of my own computers that has a nice Acer AL2016W 20" 1680x1050 LCD monitor, but I have an ATI 9200 graphics card in mine. I don't know anything about Nvidia.
Evans132 probably knows more than me about this subject, so pay more attention to Evans132. :)


About shutting down your computer or rebooting when it hangs like that and gets stuck in between, (either frozen, or half shut down but still running), I normally use the keyboard sequence they call 'raising skinny elephants' , which normally gets me out of that kind of situation reasonably gracefully.
Here's a nice link about that from 'Tips For Linux Explorers' links: [Skinny Elephants ( if all else fails )]("http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html").Turning off the power switch won't harm your computer physically, but if there happens to be information still in the RAM that's half written to disk it can mess up a Linux file system a little.

If that happens it's normally easy enough to fix by running a file system check. It's a good precaution to [run a file system check]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem") immediately if you know the computer has had a hard shutdown. Occasionally you may lose a file or two under those circumstances, but usually not.  If there is any damage it gets fixed that way while it's still insignificant.

It's a good idea to learn ways to escape from those rare times when your Linux computer stops responding to stimulus. Here's my link about that, it doesn't happen very often so not too many people know what to do,  [                 Proper techniques (in the event of a frozen system ) to prevent filesystem damage]("http://users.bigpond.net.au/hermanzone/p10.htm#to_prevent_filesystem_damage").

I'm just trying to be helpful, I hope that's not bothering you with too much information at this stage. You probably won't need to know much of that for a long time anyway. :)

Regards, Herman :)

---

### Post by Evans132 on 2007-07-21
If you have installed to your hard drive, which is what I understand you've done, just remove the CD when prompted, then either hit the reset button or power cycle the machine. 

When it restarts press the ESC key to enter the grub menu and then try

---

### Post by dabl on 2007-07-21
Written for Kubuntu, but applies equally to Ubuntu: [http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

:popcorn:

---

### Post by RavynX on 2007-07-22
> **Evans132 said:**
> Try this:

When the machine first reboots hit ESC key to go into grub menu and boot the machine into recovery mode.
Next, login as your user, then install your video drivers
I believe for NVidia it's 
```
sudo apt-get install nvidia-glx
```
Next, make a backup of xorg.conf file
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Then, edit the xorg.conf file 
```
sudo nano /etc/X11/xorg.conf
```
Under the "Module" section, replace "nv" with "glx"
Under the "Device" section, make sure that "Driver" says &#8220;nvidia&#8221;
Under the "Screen" section, add the following line:
```
Option "RenderAccel" "true"
```
Save the new xorg.conf  (CTRL+O to save, then CTRL+X to exit nano)
Next reconfigure the xserver settings
```
sudo dpkg-reconfigure xserver-xorg
```
Set the driver to nvidia then plug in all the refresh rate ranges for your monitor.

After that reboot the machine and see if smoke comes out of it...j/k 

If the system is still flakey just blow it all away and reinstall then repeat the video driver install. Good luck

Alrighty, so I reloaded Ubuntu and rebooted but had to do a hard power cycle to get it out of that stuck progress bar.  I booted back up w/o the CD and hit ESC to go into Safe Graphics mode.  I logged in as myself and I mounted the drive

```

sudo fdisk -lu
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hda1  /media/ubuntu

```

That was successful, then I ran Evans132's code.

```

sudo apt-get install nvidia-glx
sudo cp /etc/X11/Xorg.conf   /etc/X11/Xorg.conf.bak
sudo nano /etc/X11/Xorg.conf
sudo dpkg-reconfigure xserver-xorg
startx

```

I had made sure under Module that I replaced "nv" with "glx", under Device I made sure Driver said "nvidia" and the Option under Screen said Option "RenderAccel" "true".  I saved that file, ran the dpk-reconfigure and when that was done I tried to start with startx and it gave me an error in the log file @ [http://ravynx.net/lj/Xorg.0.log](http://ravynx.net/lj/Xorg.0.log) (I put it on my site since it was too long) but the very end of it said...

[http://ravynx.net/lj/xorg.conf](http://ravynx.net/lj/xorg.conf)

```

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0. 
(EE) NVIDIA(0):     Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0):     additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

So I power cycled it and it still came up w/ just a black screen.

---

### Post by Evans132 on 2007-07-22
Sorry to hear that RavynX.  I dug around and found that you are not the only one having problems with the 8800GTS in Feisty.

Check out at this thread:
[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=496103[/COLOR]]("http://ubuntuforums.org/showthread.php?t=496103")

There may be a solution in there for you.

If all else fails I suppose you could use the "vesa" driver temporarily until an official update or solution presents itself. 

How to set the driver to vesa:
1. Revert back to your old xorg.conf. 
2. Edit the xorg.conf Device section and set the driver to "vesa" 
3. Run dpkg-reconfigure xserver-xorg and select "vesa" as the driver.
4. Reboot

---

### Post by RavynX on 2007-07-22
> **Evans132 said:**
> Sorry to hear that RavynX.  I dug around and found that you are not the only one having problems with the 8800GTS in Feisty.

Check out at this thread:
[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=496103[/COLOR]]("http://ubuntuforums.org/showthread.php?t=496103")

There may be a solution in there for you.

If all else fails I suppose you could use the "vesa" driver temporarily until an official update or solution presents itself. 

How to set the driver to vesa:
1. Revert back to your old xorg.conf. 
2. Edit the xorg.conf Device section and set the driver to "vesa" 
3. Run dpkg-reconfigure xserver-xorg and select "vesa" as the driver.
4. Reboot

I've tried using the Vesa driver as well via the dpkg-reconfigure command and still no worky.  I'm going to look in that forum post that you just posted.  Thanks for all your help, would it help if I tried Dapper (6.06) instead of Ubuntu 7.04?

---

### Post by RavynX on 2007-07-23
Okay, so I tried the instructions in that thread and I wasn't able to get it working because I believe his instructions are for when you've actually booted up into Ubuntu (not LiveCD) but just don't have the proper graphics drivers/settings yet.

I tried installing 6.06 and barely got past the opening splash screen w/ the options.  I got...

```

<0> Kernel panic - not syncing Attempted to kill init!

```

*shrug*  Does that ' "bcm43xx: Error: Microcode5.fw ' error have anything to do with this or is it just part of my graphics problem?  I can try and redownload and reburn in the 7.04 64-bit version.  I'm out of ideas.

---

### Post by Evans132 on 2007-07-23
> because I believe his instructions are for when you've actually booted up into Ubuntu (not LiveCD) but just don't have the proper graphics drivers/settings yet.

Just to clarify, you have installed ubuntu to your hard drive and are trying to boot from that - not the liveCD, correct? 

One last thing to try if you haven't already - get the alternate-install iso and see if that works. If not, well, you could try out Fedora, Suse, or some other distro and see how that goes.

---

### Post by RavynX on 2007-07-23
> **Evans132 said:**
> Just to clarify, you have installed ubuntu to your hard drive and are trying to boot from that - not the liveCD, correct? 

One last thing to try if you haven't already - get the alternate-install iso and see if that works. If not, well, you could try out Fedora, Suse, or some other distro and see how that goes.

For the clarification, yes I've been trying to boot from the harddrive and I get a blackscreen for that.  Anytime I'm able to get to the Ubuntu desktop is when I use LiveCD.  It sounds like from that guy's tutorial that he's able to boot from his harddrive, logs in and uses the CLI there.  I'm trying to do it from the LiveCD and when I logout of the desktop, press CTRL-ALT-F1 to get the CLI and login there, it won't let me.

I tried the alternate CD already, unfortunately.  I'll try it one more time just for kicks when I get home from work.  Other than that... I'll see what other systems are compatible w/ my 8800gts card.  =/

---

### Post by Evans132 on 2007-07-23
Another quick question, were you able to get into the GRUB menu and boot using the "Recovery Mode" option? You wouldn't need the CD at all for that as it boots directly into command mode.

the Grub menu prompt appears just afer system post and before ubuntu boots up (its easy to miss if your not looking for it as it can flash by pretty quick)

[IMG]http://images.howtoforge.com/images/kernel_compilation_ubuntu/4.png[/IMG]

 then after you hit ESC the menu looks like this:

[IMG]http://images.howtoforge.com/images/kernel_compilation_ubuntu/5.png[/IMG]

If you have then disregard this - just double checking.

---

### Post by RavynX on 2007-07-23
> **Evans132 said:**
> Another quick question, were you able to get into the GRUB menu and boot using the "Recovery Mode" option? You wouldn't need the CD at all for that as it boots directly into command mode.

the Grub menu prompt appears just afer system post and before ubuntu boots up (its easy to miss if your not looking for it as it can flash by pretty quick)

[IMG]http://images.howtoforge.com/images/kernel_compilation_ubuntu/4.png[/IMG]

 then after you hit ESC the menu looks like this:

[IMG]http://images.howtoforge.com/images/kernel_compilation_ubuntu/5.png[/IMG]

If you have then disregard this - just double checking.

I am able to get into the Grub menu and boot into the Recovery Mode and I can log in as my user account through that.  I could try downloading that graphic driver package that he has you download in the tutorial but save it to my /home or something I could access in Recovery Mode (he has you download it to the desktop).  He then has you enter the following command below to see what version your kernel is.  Mine shows up as 2.6.20-**15**-generic.  He states that if it's not 2.6.20-**16**-generic, then it's a different kernel than the default 64-bit Ubuntu.  So, did I download an incorrect version?  I got it directly off of the Ubuntu.com website unless he made a typo on the 15-16 number.

```

Step 5: Enter the following command to see which kernel version you are using:
Code:

[CODE]
uname -r

```

If the output is not "2.6.20-16-generic" then you're using a different kernel than the default 64-bit Ubuntu 7.04 kernel and my pre-compiled package won't work for you (don't despair though, it will just require more work. check out this thread on nvnews: [http://www.nvnews.net/vbulletin/showthread.php?t=94072](http://www.nvnews.net/vbulletin/showthread.php?t=94072)). If the output IS "2.6.20-16-generic" then all is good and you can continue to the next step.
[/CODE]

---

### Post by Evans132 on 2007-07-23
Ok. One last try then I'll leave you be

While you are in "Recovery Mode" try re-doing the video card driver install process that I listed earlier (somewhere on page 2 of this thread I think). 

Remember to only install the drivers after you have booted into "Recovery Mode" via the Grub Menu.

Who knows, maybe something didn't install correctly.

---

### Post by RavynX on 2007-07-23
> **Evans132 said:**
> Ok. One last try then I'll leave you be

While you are in "Recovery Mode" try re-doing the video card driver install process that I listed earlier (somewhere on page 2 of this thread I think). 

Remember to only install the drivers after you have booted into "Recovery Mode" via the Grub Menu.

Who knows, maybe something didn't install correctly.

:(  No good.  =/

Thanks again for all your help guys.  I will wait till Ubuntu 7.10 (Gusty Gibbon) sometime in October.  =)

---

### Post by Karail on 2007-08-02
Sorry if this reply is too late however I just resolved a very simlar sounding problem on my computer and thought i would share the solution.

For me the problem was with the splash screen that tries to fire up after GRUB loads. To resolve the problem i did the following

1. Startup in Recovery Mode (Option in the GRUB menu)
2. Type the following once logged in:

```
sudo vi /boot/grub/menu.lst
```

3. Scroll down till you see a section "## ## End Default Options ##"
4. A few lines below this you will see something like 

```
title		Ubuntu 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=aa5decf1-4785-4eba-9433-6d7b3fc6c1c1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault
```

On the line starting with "kernel" remove the word "splash", so it looks like:

```
title		Ubuntu 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=aa5decf1-4785-4eba-9433-6d7b3fc6c1c1 ro quiet
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault
```

5. Save your changes by typing the following and then pressing return.

```
:x
```

6. Reboot

```
sudo reboot
```

Hope this helps.

---

### Post by RavynX on 2007-08-14
> **Karail said:**
> Sorry if this reply is too late however I just resolved a very simlar sounding problem on my computer and thought i would share the solution.

For me the problem was with the splash screen that tries to fire up after GRUB loads. To resolve the problem i did the following


Nothing is ever too late.  :biggrin: I will try this when I get home today.

---

### Post by RavynX on 2007-08-14
On a side note, could this be a hardware issue?  I read another post ([http://ubuntuforums.org/showthread.php?t=497264](http://ubuntuforums.org/showthread.php?t=497264)) where he swapped out motherboards, reinstalled, and it came up.

Is there anything special I need to set in the BIOS for Linux to function properly?

Reminder: Currently using an eVGA 680i motherboard ( model: 122-CK-NF68 ) & an 
eVGA 8800 GTS 640MB PCI-e video card.

---

### Post by Karail on 2007-08-14
> **RavynX said:**
> On a side note, could this be a hardware issue?  I read another post ([http://ubuntuforums.org/showthread.php?t=497264](http://ubuntuforums.org/showthread.php?t=497264)) where he swapped out motherboards, reinstalled, and it came up.

Is there anything special I need to set in the BIOS for Linux to function properly?

Reminder: Currently using an eVGA 680i motherboard ( model: 122-CK-NF68 ) & an 
eVGA 8800 GTS 640MB PCI-e video card.

Quite possibly. My machine is of a very similar specification:

eVga 680i Motherboard
Intel Core2 X6800
nVidia 8800 GTX
2GB DDR II RAM
Creative X-Fi Sound Card

I think the problem here might be the graphics card as the reason the splash program failed on my computer was the resolution it was trying to run at by default (I think!). I found that if I forced the system to boot up at a higher resolution than normal the splash screen appeared and would eventually load into linux. Although even then the splash screen still did not display correctly. 

Edit:

Did a quick search on google and I think this may be the issue reported here:

[https://bugs.launchpad.net/ubuntu/+bug/86666](https://bugs.launchpad.net/ubuntu/+bug/86666)

---

### Post by RavynX on 2007-08-19
Ok, so I finally got some time to try what Karail suggested and it didn't work.  So in a desperation attempt I redownloaded the ISO for the 64-bit version and also downloaded the 32-bit version.  I tried reinstalling the 64-bit and it locked up when it was trying to reboot after installing.   So I tried the 32-bit version, that also locked up when it was trying to reboot.  But this time I tried different keys just incase "Enter" wasn't the so-called right key.  I ended up pressing Ctrl-J and that completed the reboot and it booted up into Ubuntu w/o the Live CD in the drive with no problems at all.  I'm currently typing this up in the 32-bit install as we speak (I did try to reload the 64-bit version and used Ctrl-J to reboot, but it never booted up from there so I just stuck w/ the 32-bit version for now).

So, from here I'm going to try to install the nVidia drivers using the methods everyone has posted here and hopefully we'll get some more positive results.  \\:D/

By the way, when I was trying all the recommended fixes on the 64-bit version, it always came up as 2.6.20-15-generic instead of 2.6.20-16-generic.  Is that an issue with what I'm downloading or am I missing something?  2.6.20-15-generic is also showing up on the 32-bit version I'm using now when I type "uname -r"

---

### Post by gummih on 2007-08-20
Ok, I just went through this and am writing you from my spanking new Ubuntu installation :)

Ubuntu 7.04 **64bit**
q6600
**nvidia** 8600GT
Acer AL2423W 24" **widescreen**

Installed from liveCD and restarted but all I got was the black screen, monitor found no signal and dozed off. 
But although there is no signal, there is something lurking in the darkness - a shell. 
```
 <enter>
exit <enter> 
``` 
(or just press enter to get out of the prompt, then you can do other stuff, but blind as a kitten)
and then ubuntu came to life and I was greeted with the gui login - everything seems to work but now I'm taking measures so that this won't happen every time

---

### Post by amplogik on 2007-10-03
I too suffered from the same black screen of death after upgrading my video card from a 7900 GTX to an 8800 GTX.    Realizing that I could log in in single user mode without trouble, it became apparent that the new card was fundamentally incompatible with the ubuntu splash screen.  The splash screen was either locking up or disabling video on boot.

so, here's what I did to fix the problem:


**Step One:**

Use the nVidia drivers, not the supplied ones from ubuntu.  I won't go into detail here, as this step is well documented elsewhere on the forums.  If this is a bit beyond you, consider using [envy to set them up for you]("http://lunapark6.com/envy-easy-way-to-install-nvidia-drivers-in-ubuntu.html").

**Step Two:**

open a terminal.

type:

sudo gedit /boot/grub/menu.lst

Now, find the boot argument for your kernel, mine looks like this:

[FONT="Courier New"]title           Ubuntu  kernel 2.6.22-12-rt
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-12-rt root=UUID=6b0fa2a3-53da-4059-bffa-24fe8360c245 ro quiet
initrd          /boot/initrd.img-2.6.22-12-rt
quiet[/FONT]

Add the nosplash=y option to the kernel argument:
[FONT="Courier New"]title           Ubuntu gutsy (development branch), kernel 2.6.22-12-rt
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-12-rt root=UUID=6b0fa2a3-53da-4059-bffa-24fe8360c245 ro quiet **[COLOR="Red"]nosplash=y[/COLOR]**
initrd          /boot/initrd.img-2.6.22-12-rt
quiet[/FONT]

Now, save the file, and reboot.

The next time you boot up, ubuntu will skp the splash screen, and thereby avoid the evil splash screen lockup.

Good luck!

---

