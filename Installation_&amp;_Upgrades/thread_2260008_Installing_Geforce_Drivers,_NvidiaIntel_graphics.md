---
title: "Installing Geforce Drivers, Nvidia/Intel graphics"
date: 2015-01-08
forum: Installation &amp; Upgrades
---

### Post by jrdobelmann on 2015-01-08
I have a laptop with a Nvidia Geforce graphics card.  I was able to install Ubuntu Studio to my hard drive, and it worked fine, but then I encountered problems when I tried installing the drivers.  I tried installing the drivers from Nvidia's website, but then it prevented programs like Blender from starting.  I tinkered with it a little longer, and then it completely failed to start X Windows.  I decided to just reinstall Ubuntu Studio, so everything is working now.  Before I try installing the Geforce drivers again, does anyone have any tips on how to properly install them so I don't have to install Ubuntu Studio a third time?

---

### Post by ibjsb4 on 2015-01-09
I do not run studio, but I think that the same method applies.  Open 'Software and updates' or in terminal:
```
software-properties-gtk
```
And go to 'Additional Drivers'.
You should get a list of available drivers and the ability to switch back.

---

### Post by jrdobelmann on 2015-01-09
I tried it, and it says "No additional drivers available."  Basically what I want to know is which drivers I should get.  Should I get open-source or proprietary?  Where should I download the drivers from?  How should I install the drivers without completely breaking X Windows?

---

### Post by mörgæs on 2015-01-10
Please run ```
sudo lshw -C video
``` and post the results in CODE tags.

---

### Post by efflandt on 2015-01-10
What does **lspci** (which means list pci devices) show for any video devices like VGA or 3D? Usually the best way to get everything working and cooperating in Ubuntu is to install Ubuntu (or at least Debian) packages. Installing things from other scripts might not install everything you need to interact with other things and might not automatically update or work after other updates. In some cases if you have newer hardware than is supported by mainstream packages you can add ppa repos that have additional packages or newer packages that have not gotten into the mainstream yet (some possibly not fully tested). Also which Ubuntu Studio version are you installing?

Many laptops have dual graphics, integrated Intel graphics for low power (slow) use and something else like Nvidia for gaming (hotter and uses more power). For example the power LED on my laptop is cool blue when using Intel graphics and hotter looking amber while using faster Nvidia graphics. If you have dual graphics installing only drivers from an nvidia script may not have what you need for the Intel/Nvidia switching or interacting. For example during install, you may need to use **nomodeset** boot parameter which will carry over into install so that modules can be used instead of 1 fixed driver in the kernel (especially for nvidia or dual graphics). Usually installing one of the Ubuntu nvidia driver packages will also install what you need for the dual graphics if you have that (unless an older Ubuntu version from before such hardware became popular). Once we know what graphics you have from lshw or lspci, someone will likely be able to suggest which drivers you need.

For example I recently replaced my video card with Nvidia GTX 750 Ti for my desktop and the rather old 304 driver in nvidia-current package of 14.04 would not work at all with it because that did not support the new Maxwell chip. So I needed to use a different package with newer nvidia driver version. But I have not updated my laptop from Ubuntu 13.10 yet (no longer supported I think), which was the first version that included much support for the dual graphics. I want to get an mSATA SSD for that for a fresh Ubuntu install.

---

### Post by grahammechanical on 2015-01-10
I am running Ubuntu Studio right now and in my opinion the best method for changing video drivers with least risk of failure is to use the Addtional Drivers utility. In Ubuntu Studio we find Addittional Drivers in the Settings Manager which is in the drop down menu that we get when we click the Ubuntu Studio icon at the top left of the screen. We need to allow the utility time to search for proprietary video drivers and we also need an internet connection.

We should be offered a choice of 5 drivers, including an open source video driver. With Nvidia we get version 331 (tested); 331-updates; version 304 and 304-updates. These are the latest available in Ubuntu Studio 14.10.

When we install Ubuntu or any of its flavours and we tick the box "Install third party software" we automatically get a proprietary video driver installed. For Nvidia this most likely will be 331 (tested). Ubuntu does not offer the latest from the manufacturer's web site because stability is preferable to experimentation.

While we are in the Software and Updates utility we can go to the Ubuntu software tab and make sure that there is a tick against the box labelled "Proprietary drivers for devices (restricted). Then we will get any updates to proprietary video drivers.

We can also use the command line. To find out what video drviers are available run

```
ubuntu-drivers list
```

to find out what video adapter we have and what drivers are available for it run

```
ubuntu-drivers devices
```

to install the tested proprietary video driver run

```
sudo ubuntu-drivers autoinstall
```

We must allow time for all these commands to do their work. If we already have a proprietary video driver installed, then the autoinstall command only read the packages lists and rebuild the dependencies.

Regards.

---

### Post by jrdobelmann on 2015-01-10
sudo lshw -C video outputs
```
  *-display               
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0b
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:59 memory:b5000000-b53fffff memory:c0000000-cfffffff ioport:6000(size=64)
  *-display UNCLAIMED
       description: 3D controller
       product: GM108M [GeForce 840M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:0a:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:b3000000-b3ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:3000(size=128)


```
lspci has VGA and 3D controller:
```
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
0a:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 840M] (rev a2)

```
ubuntu-drivers list and ubuntu-drivers devices don't output anything, and sudo ubuntu-drivers autoistall says
```
No drivers found for automatic installation.
```
When I installed Ubuntu Studio, I'm pretty sure I checked the "Install 3rd party" option, and my Ubuntu Software tab has the "Proprietary drivers for devices (restricted)" checked, but it still can't find the drivers.  I am running Ubuntu Studio 14.04 64bit.

---

### Post by efflandt on 2015-01-11
Was this after you reinstalled Ubuntu Studio, or still the previous system? Because if you still have the driver installed from nvidia.com, I don't know how remove that so the Ubuntu packages would work.

I have not installed 14.04 on my year old laptop yet (want to put it on mSATA, currently has 13.10 on sda4). But from 64-but Ubuntu 14.04.1 live/install I used set **nomodeset** option during boot and **ubuntu-drivers devices** returns:```
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
model    : GK106M [GeForce GTX 765M]
modalias : pci:v000010DEd000011E2sv00001462sd000010E0bc03sc02i00
vendor   : NVIDIA Corporation
driver   : nvidia-331-updates - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-331 - distro non-free recommended
```

So I would think that either nvidia-331 or nvidia-331-updates package should work for your newer system, which for a dual graphics should include whatever hooks for cooperation between the two. In 13.10 my laptop uses Intel graphics by default unless I use "optirun " prefix for a program or game (plus additional launch options for Steam Source games). On that system I had not gotten "primus run" to work. But it looks like they make that easier in 14.04 or newer. For more details see [https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics) and [http://xmodulo.com/install-configure-nvidia-optimus-driver-ubuntu.html](http://xmodulo.com/install-configure-nvidia-optimus-driver-ubuntu.html) or web search "ubuntu intel nvidia hybrid".

---

### Post by MAFoElffen on 2015-01-11
Looking up at nVidia, it looks like their driver support for your card started with v337.x. I think what is up in Main right not is nvidia-graphics-driver-331.

Two alternatives:
- Add the edgers PPA and install a driver from there at version 340 or higher.
```

sudo apt-get update
sudo nvidia-installer --uninstall  # this may return not found, but do it just in case it is there. 
sudo apt-get remove nvidia-* 
sudo apt-get install linux-headers-('uname -r') 
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-graphics-driver-340 nvidia-settings nvidia-prime
sudo nvidia-xconfig

```
Or follow the directions linked from Post #2 of my sticky (link in my signature line) to install the binary drivers directly from nVidia...

---

### Post by jrdobelmann on 2015-01-11
I was able to install the Nvidia 340 drivers, but now my laptop's  monitor is glitching out and has a horrible refresh rate.  My second  monitor still works, and I'm able to use Nvidia-settings to switch back  to Intel Graphics where everything's normal.  Additionally (this might  be the wrong place to ask), but when I'm in Geforce mode, programs like  Blender still don't detect the graphics card.  My question now is: How  do I fix the monitor issue, and how do I use the graphics card with  programs like Blender?
I completely overwrote the old Ubuntu installation, so everything I'm doing now is in the new install, efflandt.

---

### Post by jrdobelmann on 2015-01-15
It looks like the Screen glitch problem went away, but Blender still doesn't recognize my graphics card.  Any tips on getting my programs to work with the card?

---

### Post by jrdobelmann on 2015-01-15
Also, sudo nvidia-xconfig outputs:
```
WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'
```
and then running it again says
```
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```

The contents of the file are
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 340.65  (buildmeister@swio-display-x64-rhel04-11)  Tue Dec  2 09:59:38 PST 2014


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```
Does this have anything to do with my problem?

---

### Post by gasdia73 on 2015-05-14
This thread is marked as SOLVED but how did you solve it if i may ask ?

---

### Post by jrdobelmann on 2015-05-15
My original problem was that Blender failed to start when the Geforce graphics were in use.  In all honesty, I don't remember how I fixed it since I basically just kept uninstalling and reinstalling Ubuntu Studio to try and get the drivers to work.  I ran into another problem where Blender would start up when the drivers were in use, but it wouldn't recognize the graphics card.  I realized since then that I needed to install CUDA in addition to installing the drivers, so that was just me being stupid.  Now, I'm running into a problem where trying to use the drivers and CUDA will cause X Window to fail to start, which means I have to go into a terminal and uninstall the drivers.

Simply put, I thought I solved the problem, but it just led to more problems, so I might change this to UNSOLVED to see if I can get more some new answers.

---

### Post by jrdobelmann on 2015-05-15
Like I said early, I am now running into a new problem where I can't use my graphics card without X Window breaking.  Originally, simply installing the drivers would cause X Window to crash, but I tinkered around with it for a while and eventually got it to work.  Now, when I try to install CUDA, the same thing happens, and I have to go into a terminal to uninstall the drivers in order to get X Window to work.  Keep in mind that I've been running off of Intel Graphics for the past several months, and I haven't experimented with this since then, so I'm sorry if I'm sounding a little vague right now since I don't really remember too many of the details.  If any of you guys have troubleshooting tips, I'll keep you guys informed and hopefully find an answer to this.  Thanks.

---

