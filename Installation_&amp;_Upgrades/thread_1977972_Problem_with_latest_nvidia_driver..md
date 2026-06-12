---
title: "Problem with latest nvidia driver."
date: 2012-05-11
forum: Installation &amp; Upgrades
---

### Post by bedford4x4 on 2012-05-11
Hi all,

I don't know much about Ubuntu, first of all.  I tried Mandriva 2010 and then 2011 but I didn't really like either of them.  I now have Ubuntu running on 3 machines - 2 PCs and a Sony Vaio M netbook.

I updated Ubuntu to 12.04 this week.  The netbook loved it, as did my son's computer.  However, the 3rd machine has a Pentium 4 processor, nvidia GX5400 video card and the monitor is a 42" TV connected via DVI.

When Ubuntu 11.10 was running on this machine, I initially had trouble getting the desktop to display.  After installing the nvidia proprietory driver, I was able to adjust settings so that I got a decent screen resolution.  The driver recognized the LG 42" TV as a Samsung 32" TV.

I had the same problem with 12.04, but after installing the latest driver from the restricted repository via PPA, I have very low screen resolution and am restricted to 800x600 or 1024 x 768.  The TV is now recognized as Laptop.

Doe anyone know if using a previous driver would give me back the ability to choose a higher resolution? The way it is now is horrible.

Cheers,

Harry

---

### Post by bogan on 2012-05-11
Hi! **bedford4x4,**

According to Nvidia Downloads the driver for your FX5400 card is 173.xxx, Later versions do not support it.

In theory it is available in Synaptic Package Manager, but I am told that will give a missing dependencies message; so you need to install it manually from the downloaded .run file.

Edit:
Before you attempt that, I suggest you disable the drivers in 'Additional Drivers', and see how it goes using the default Nouveau drivers, [if they have not been blacklisted.]

Chao!, **bogan**.

---

### Post by keithwwalker on 2012-05-11
Hi Bogan, I am still working on my problem as well.  The latest nvidia driver is installed and I need to downgrade to the 173.xx driver.

I have downloaded the 173 driver from here, but I need help on how to manually install the file:
[http://www.nvidia.com/object/linux-display-ia32-173.14.31-driver.html]("http://www.nvidia.com/object/linux-display-ia32-173.14.31-driver.html")

I have gotten this far (the package was on my desktop):

```
cd /home/keithwwalker/Desktop
```

I tried to installed, but got permission denied, then I went to root:

```
sudo bash
```

Then remembered the correct command(!) sudo sh:
```
sudo sh NVIDIA-Linux-x86-173.14.31-pkg1.run
```

Terminal then displayed:
[I]
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 173.14.31[/I]

Then I got the error message in a sub window that the x server must be shut down:
[I]ERROR: You appear to be running an X server; please exit X before installing.  For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).
[/I]

followed by another error message:
*ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).*

Problem is that I open the nVidia X Server settings program and it states another error message:

*You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.*

I think to run as root the command is(?):
```
sudo nvidia-xconfig
```
but I run that command and still get the same error message above.

How can I disable the x server and install the new driver?
With the 173.xx driver, I am confident that users like bedford4x4 and myself can get back to the resolutions we need for our monitors.

I too am restricted to 800x600 or 1024 x 768.  If I get the new driver I should be able to get the desired 1280 x 768!

It's so close I can taste it!

KWW

---

### Post by bogan on 2012-05-11
Hi!,**Keithwalker,** & also **Bedford4x4,**

There are several ways to achieve this depending on what your problem of access is.

FIRST: with a grub menu highlight the entry you want to boot into, press 'e', move cursor down to the Linux line and along to 'ro', delete "quiet splash" and alter to "ro text ", press 'Ctrl+x' to boot to a tty terminal log-in prompt.

OR:
SECOND:From a GUI screen terminal enter:```
 sudo service lightdm stop
```You are likely to get a black screen with or without some text, if there is no prompt, press 'Ctrl+Alt+F1' [or F2-F6] to get a tty terminal log-in prompt.

OR:
THIRD: Select the recovery boot mode and in the menu choose "Drop to root terminal with network".

Log-in & enter your password if requested.

Now CD to where your downloaded NVIDIA-......run file is and run it with ```
ls
sudo sh <filename>  # 1st enter 'ls' to check exact spelling or press 'Tab' to auto complete.
```If you have problems, or it does not work, refer to Post #280 in the 'Blank Screen' Sticky at the top of this Forum's listing, for the full version including purging the previous installation and blacklisting - note that, of course, you do not want to have 'blacklist nvidia-173' in the /etc/modprobe.d/blacklist.conf file.

There are suggestions that the 173 driver is not at present compatible with the 12.04 Xserver, so the best of luck. You might do better to try the default Nouveau driver first, by disabling it in 'ADDITIONAL DRIVERS'.

Chao! **bogan.**

---

### Post by keithwwalker on 2012-05-11
Well I tried the 173.xx driver installation by first disabling x server and when I reboot, I don't get any gui screen at all now.  Luckily, GRUB2 is fixed (rescatux) and i can dual boot into winXP to continue to work the issue.

Here is the code I entered into terminal:

```
sudo service lightdm stop
```

As Bogan predicted, the screen goes black and then you have to ctrl-alt-f1 to get to a tty terminal where I entered the following:

```
cd /home/keithwwalker/Desktop
```
```
sudo bash
```
```
sudo sh NVIDIA-Linux-x86-173.14.31-pkg1.run
```

I think my next step is to do as Bogan stated:
> FIRST: with a grub menu highlight the entry you want to boot into, press 'e', move cursor down to the Linux line and along to 'ro', delete "quiet splash" and alter to "ro text ", press 'Ctrl+x' to boot to a tty terminal log-in prompt.


Is this the right track?  The GRUB2 and boot splash screens are ok when it is booting up, it is only after boot is complete that the gui screen goes completely black.

---

### Post by bogan on 2012-05-11
Hi!, **Keithwalker**,

You Posted:>  I think my next step is to do as Bogan stated:[QUOTE]FIRST: with a grub menu highlight the entry you want to boot into,  press 'e', move cursor down to the Linux line and along to 'ro', delete  "quiet splash" and alter to "ro text ", press 'Ctrl+x' to boot to a tty  terminal log-in prompt.Is this the right track?  The GRUB2 and boot splash screens are ok  when it is booting up, it is only after boot is complete that the gui  screen goes completely black.[/QUOTE]Have you tried editing the grub menu to add ' nomodeset ', but leave off the 'text'?

Edit: Afterthought: Try logging in at the tty prompt and enter ```
sudo service lightdm start
``` Note any messages and press Ctrl+Alt+F7, again note any messages, and what happens.

Apart from that; as to what the next step should be, the only suggestions I can offer - apart from hoping nvidia will produce a revised version of 173 for 12.04 - are to follow MAFoElffen's detailed instructions in Post #280 to purge the existing installation and reinstall 173 , or fall back on the default Nouveau driver.

If you want to try the last, after logging in to the tty, run: ```
sudo nvidia-installer --uninstall 
sudo apt-get remove --purge nvidia-*
sudo apt-get update
sudo apt-get autoremove
sudo reboot
``` It would appear that is  unlikely to make things worse.

Otherwise, a fresh re-install of either 12.04 or an earlier version is the obvious remedy.

Chao!, **bogan**.

---

### Post by keithwwalker on 2012-05-14
Bogan,

I have purged everything and reloaded the latest nvidia drivers.  I first got the grey screen and then I loaded:

```
sudo apt-get install nvidia-current
```

Now I am back at 800x600, no option for anything higher.
I wish there was a way out of this MESS.  Will never upgrade to a xx.04 version again...

On my nVidia xserver settings I get the following message:
*You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.*

How do I edit the X configuration file?

kww

---

### Post by bogan on 2012-05-14
Hi!, **keithwalker,**

You Posted:>  How do I edit the X configuration file? From a terminal run: ```
gksu nvidia-settings
``` You can run 'NVIDIA XServer Settings' from Dash; which is the same thing, but you need to be su to save the settings to Xconfig.

Chao!, **bogan.**

---

### Post by keithwwalker on 2012-05-14
I found a thread on another forum with the same issue - legacy drivers 96 and 173 not working with 12.04.
[nvidia-96 and nvidia-173 uninstallable on Precise]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/948053")
Just will have to wait until it gets fixed?!?

---

### Post by bogan on 2012-05-14
Hi!, **keithwalker**,

> Just will have to wait until it gets fixed?!?Yeah! If Only!

I fixed mine by getting a GT520, only cost £25, about $40, a GT210 would not work.

Chao!, **bogan**.

---

### Post by keithwwalker on 2012-05-14
If I could upgrade I would!  It is an all-in-one pc, with an AGP card - can not find a card to replace it...looking to buy a replacement pc later this year.

> **bogan said:**
> Hi!, **keithwalker**,

Yeah! If Only!

I fixed mine by getting a GT520, only cost £25, about $40, a GT210 would not work.

Chao!, **bogan**.

---

### Post by bogan on 2012-05-17
Hi!,** All**.

[COLOR=Blue]There is a new nvidia driver version 295.53 available [/COLOR]from nvidia downloads.  This Link is for the 32 bit version, check you get the correct one.
[http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html)

[COLOR=RoyalBlue]**Edit: Updated Thursday May 17th; **[/COLOR]     

     ```
nvidia-installer --latest
``` now returns: v295.53 and the currently installed version, without altering anything.
     

     ```
nvidia-installer -f
``` will install 295.53 after un-installing the previous version.

NVNews says of version 295.53:
QUOTE:
**Please note:** This [NVIDIA]("http://www.nvidia.com/") Linux graphics driver release supports **GeForce 6xxx and newer [NVIDIA]("http://www.nvidia.com/") GPUs**,
 [GeForce4]("http://viglink.pgpartner.com/rd.php?r=10313&m=878281881&q=o&priceret=87.73&pg=%7E%7E3&k=2b6229593608c3c1fb499d0ca9880634&source=feed&url=http%3A%2F%2Fmicropartsusa%2Ecom%2F31p6953%2Dibm%2Dnvidia%2Dgeforce4%2Dmx440%2D64mb%2Dagp8x%2Datx%2Dgraphics%2Dcard%2Dw%2Do%2Dcable%2Dnew%2Dbulk%2Din%2Dstock%2Ehtml&st=feed&mt=%7E%7E%7E%7E%7E%7E%7E%7En%7E%7E%7E") and older GPUs are supported through the **96.43.xx** and **71.86.xx** [NVIDIA]("http://www.nvidia.com/") legacy graphics drivers.
 GeForce FX GPUs are supported through the **173.14.xx** NVIDIA legacy graphics drivers.

[B]
bogan.[/B]

---

### Post by keithwwalker on 2012-05-20
Bogan, the newest nVidia 295 driver does not work with my card!  My video card requires a legacy driver.  The Legacy drivers for some reason were not working with the x driver.

Luckily in the last day or so, nVidia released a new driver that solved the problem:
[173.14.34 (legacy prerelease) for Linux x86/x86_64 released]("http://www.nvnews.net/vbulletin/showthread.php?t=181248")

I used the following code, very simple(!):

```
cd /home/keithwwalker/Desktop
```
then you must stop your x driver for the nVidia package to install!!!!
```
sudo service lightdm stop
```
your screen goes black and hit **ctrl-alt-f1** to get back to terminal, and then type in:
```
sudo sh NVIDIA-Linux-x86-173.14.34-pkg#.run
```

Once the installer installs the driver, it asks to update the x driver settings, say ok then the installation procedure finishes.

Once that is done, press **ctrl-alt-delete** to reboot.  No need to restart lightdm, it is automatically done.

So now I have full resolution back!  Thank you Bogan, you helped with coding and helped narrow down the source of the problem.

There is bad news though, I hear that nVidia will not support legacy drivers that run off the 96 driver.  Only the 173 driver is being updated.  I hope it is not true, only time will tell.  The old 71 driver is apparently not being updated.

To see a list of which nVidia graphics cards must use the legacy drivers, see here:
[The following GPUs are no longer supported in the regular NVIDIA Unified UNIX Graphics Driver.]("http://www.nvidia.com/object/IO_32667.html")

---

### Post by ahso4271 on 2012-05-20
I gave up and installed ExTiX[]("http://linux.exton.net/forums/extix") as this comes with the latest driver installed. Very happy with it for now. (there's was something very broken in my Ubuntu 12.04...)

---

### Post by bogan on 2012-05-20
Hi!, **keithwalker**.

Great, glad you got it fixed OK.

Thanks for Posting the details of the nvidia legacy 173 driver update.

Please mark the Thread as 'Solved' in 'Thread Tools' at top of display.

Chao!, **bogan**.

---

### Post by haresear on 2012-05-20
Word of caution -- a bug report has been filed against the new (pre-release) legacy drivers 173.14.34.
[http://http://www.nvnews.net/vbulletin/showthread.php?t=181386]("http://http://www.nvnews.net/vbulletin/showthread.php?t=181386")
I experienced the same problem using these drivers in Ubuntu 12.04. The 'glx' module fails to load, so there are no GLX extensions available.
```
~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

---

### Post by bogan on 2012-05-20
Hi!, **haresear**

Thanks for your warning.

Unfortunately the Link you gave is unobtainable. Would you please check it?

Edit:  It has a double 'http//' which makes it invalid, you need to delete the one in the string box before pasting the url.

EDIT2: This seems to be the correct Link: [http://www.nvnews.net/vbulletin/showthread.php?t=181386](http://www.nvnews.net/vbulletin/showthread.php?t=181386)
 


Chao!,  **bogan**.

---

### Post by haresear on 2012-05-20
@bogan - Thanks for correcting the link. I can't edit that post any longer.

---

### Post by keithwwalker on 2012-05-20
I should add that I am getting error messages upon start up, but the video still works.  

I also decided to updgrade the system using 'Update Manager' and it just totally destroyed my GUI and put me in ctrl-alt-f1 terminal.

The recourse is to just reinstall in the nVidia driver from the ftp site using the instructions I posted above.  Luckily the file was still on my desktop.  After the driver reloads, the package applies nVidia settings and my GUI was restored.

Something in the official Ubuntu download is not compatible with the nVidia driver package, update at your own risk for now.

Here are the error messages generated during bootup of the GUI (with the new nVidia .34 driver and settings:
```
none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 137
CRTC 137: trying mode 1280x768@50Hz with output at 1024x768@0Hz (pass 0)
CRTC 137: trying mode 800x600@51Hz with output at 1024x768@0Hz (pass 0)
CRTC 137: trying mode 800x600@52Hz with output at 1024x768@0Hz (pass 0)
CRTC 137: trying mode 680x384@53Hz with output at 1024x768@0Hz (pass 0)
CRTC 137: trying mode 640x480@54Hz with output at 1024x768@0Hz (pass 0)
CRTC 137: trying mode 400x300@55Hz with output at 1024x768@0Hz (pass 0)
CRTC 137: trying mode 400x300@56Hz with output at 1024x768@0Hz (pass 0)
CRTC 137: trying mode 320x240@57Hz with output at 1024x768@0Hz (pass 0)
CRTC 137: trying mode 1280x768@50Hz with output at 1024x768@0Hz (pass 1)
CRTC 137: trying mode 800x600@51Hz with output at 1024x768@0Hz (pass 1)
CRTC 137: trying mode 800x600@52Hz with output at 1024x768@0Hz (pass 1)
CRTC 137: trying mode 680x384@53Hz with output at 1024x768@0Hz (pass 1)
CRTC 137: trying mode 640x480@54Hz with output at 1024x768@0Hz (pass 1)
CRTC 137: trying mode 400x300@55Hz with output at 1024x768@0Hz (pass 1)
CRTC 137: trying mode 400x300@56Hz with output at 1024x768@0Hz (pass 1)
CRTC 137: trying mode 320x240@57Hz with output at 1024x768@0Hz (pass 1)

```

kww

---

### Post by Bersam on 2012-05-22
Hi everybody,
I installed new driver and work like a charm!
the only problem i have with ubuntu  is that ubuntu doesn't know new driver so just show it as "Unknown", then every time i login is just load unity 2d instead of normal unity. any idea?

---

### Post by bogan on 2012-05-22
Hi!, **Bersam**,

Please Post the output of: ```
/usr/lib/nux/unity_support_test --print
```That will tell us the video card and driver in use.

Chao!,** bogan**.

---

### Post by Bersam on 2012-05-22
> **bogan said:**
> Hi!, **Bersam**,

Please Post the output of: ```
/usr/lib/nux/unity_support_test --print
```That will tell us the video card and driver in use.

Chao!,** bogan**.
```
bersi@bersam-desktop ~ % /usr/lib/nux/unity_support_test --print
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce FX 5500/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 173.14.34

Not software rendered:    yes
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no
```

---

### Post by bogan on 2012-05-22
Hi!, **Bersam**,

Your Post shows you have the latest version of the correct video driver for your FX5500 nvidia video card, but that it is not able to support unity 3d.

{ The failure to list it correctly is a known bug of no importance, it identifies my driver as the video card itself.}

So your options would seem to be:

Log-in to ubuntu 2d,
Log-in to Gnome Classic or Gnome,
Buy a more modern video card [ if it is a Desktop model.]

Chao!, **bogan.**

---

### Post by alezflute on 2012-05-22
> **bogan said:**
> Hi!, **Bersam**,

Your Post shows you have the latest version of the correct video driver for your FX5500 nvidia video card, but that it is not able to support unity 3d.

{ The failure to list it correctly is a known bug of no importance, it identifies my driver as the video card itself.}

So your options would seem to be:

Log-in to ubuntu 2d,
Log-in to Gnome Classic or Gnome,
Buy a more modern video card [ if it is a Desktop model.]

Chao!, **bogan.**

So there's no hope at all for the owners of such a card to ever have Unity-3d? It's curious given that it was able on its time to run full Compiz without trouble.

---

### Post by haresear on 2012-05-22
In previous versions of Unity 3D, it was possible to force it to ignore the video card blacklist. Not sure if that is still possible with 12.04. Even if you can force Unity 3D to run, it may not run well.

[http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity/37686#37686]("http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity/37686#37686")

---

### Post by Bersam on 2012-05-23
> **haresear said:**
> In previous versions of Unity 3D, it was possible to force it to ignore the video card blacklist. Not sure if that is still possible with 12.04. Even if you can force Unity 3D to run, it may not run well.

[http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity/37686#37686](http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity/37686#37686)
it worked, but very bad!also i tried GNOME shell, the result is very bad! (but it's on ubuntu, maybe archlinux has better performance!).

> **alezflute said:**
> So there's no hope at all for the owners of  such a card to ever have Unity-3d? It's curious given that it was able  on its time to run full Compiz without trouble.
i suggest to try GNOME Fallback with compiz (and not 0.9.7, downgrade to 0.8.8, new version are REALLY BUGGY!) Old Fashioned but gooood :) (with nouveau or official driver)

---

