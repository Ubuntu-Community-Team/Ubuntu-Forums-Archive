---
title: "Input Not Supported While Installation"
date: 2022-08-13
forum: Installation &amp; Upgrades
---

### Post by varsima on 2022-08-13
Hello, I wanted to install Ubuntu on my pc. when i try to boot from USB drive it gives me options to: try or install ubuntu, and others. when i select "Try or install Ubuntu" i see Ubuntu logo spining (Loading) but after that screen goes black and it says that "Input is not supported" any solution? how can i fix this problem? i am using DVI to VGA conveter, could it be a problem? my monitor does't have DVI or HDMI port, that's why i have to use VGA cable.
My specs:
Cpu: I3 2th gen.
Gpu: Nvidia gtx 760
Ram: 8gb

---

### Post by TheFu on 2022-08-13
Input typically means the keyboard or mouse aren't supported.  Are those standard?  Is the BIOS configured correctly for them?  Often, the settings required for MSFT aren't correct for what Linux needs.  Also, if they are bluetooth, I've heard that those drivers may not work initially, so get a wired keyboard until after the install and you are 100% certain the non-wired keyboard is working.

---

### Post by guiverc on 2022-08-14
I don't know, but to I read your "*Input is not supported*" as being a video mode your display cannot handle (ie. I'm betting it's not the OS that's saying that, but your monitor/screen not getting any input it can understand).

You're using a DVI to VGA convertor; some can handle both analog & digital, some only handle one of those (they use different pins on the DVI side) thus your issue maybe your DVI-VGA convertor itself not converting the correct output as your graphics card changes mode as the system boots.

Have you tried *safe graphics* or nomodeset option?  The `plymouth` screen is usually lower resolution so is less of an issue (*why it works I'm betting*) and if you are talking about the desktop system (*you didn't say*) your issue maybe when it switches to higher resolution on your video card & a mode that your DVI-VGA cannot handle.

Is your DVI cable digital? or analog? or what is being converted? ie. is it DVI-A, DVI-I or DVI-D? as can your VGA monitor handle that type of input?  This link may help - [https://itm-components.co.uk/blogs/news/what-are-the-differences-between-dvi-connectors-and-signals](https://itm-components.co.uk/blogs/news/what-are-the-differences-between-dvi-connectors-and-signals)

I'm NO expert in this area though; and when I have issues I usually grab another DVI-VGA conversion plug (*looking for one that looks slightly differently pin wise*), or a different monitor & resolve it that way. 

I'd try the `nomodeset` or *safe graphics* options though, as I don't know your graphics card, nor media you tried to use (ie. *which Ubuntu product/ISO*) which are very important details.

You didn't say if trying to install Ubuntu Desktop, Ubuntu Server etc or what media.

---

### Post by yancek on 2022-08-14
I'd agree that is an error related to the monitor/graphics and I see you have Nvidia.  If you can't solve this with the suggestions posted above, you may need to reinstall.  If so, check the 2nd post at the thread below.

 [https://ubuntuforums.org/showthread.php?t=2451824](https://ubuntuforums.org/showthread.php?t=2451824)

---

### Post by TheFu on 2022-08-14
I have a DVI -to- VGA converter, but stopped using it a few months ago after 2 yrs of working fine.  It required all sorts of manual setup to get the EDID information through the adapter into the xorg config file.  In my case, I had a 1200p monitor, but the VGA adapter refused to report 1200p. Instead it only reported 1024p, which I considered unacceptable.  My fix was to use a different computer, connected directly to the monitor where I could get the binary EDID information direct, save that to a file, then using the xorg-conf, feed that correct EDID data into the X/Server so it ignored what any adapter sent.

**get-edid** and **parse-edid** are the main commands.

Then, inside the /etc/X11/xorg.conf.d/ directory, I setup a file: 20-nvidia.conf
Here's an example of the change related to EDID:
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName "GeForce GT 1030"
    # Option "UseEDID" "False"
    Option "UseDisplayDevice" "DFP-0"
    Option "CustomEDID" "DFP-0:/etc/X11/xorg-monitor.dell-2412m.edid.raw"
    # Option      "ModeDebug"
EndSection
```

See the CustomEDID line?  That points to the location of the binary EDID for the monitor.  You'll need a section like that and probably other sections in the file.  I doubt the DFP-0 will be correct for your situation too.

It should go without saying that this only works for X11, not Wayland.  For Wayland, I haven't any clue.  Also, the driver used is very important, since the CustomEDID is tied to the driver actually supporting it.  It is possible that GT 7xx cards have lost support in newer kernels. IDK.  My GT 7200 lost support after 16.04. Nvidia doesn't support older GPUs  with drivers indefinitely.  I have a GT 430 which is dying, but since it is in a non-desktop system, that isn't very important. It only works long enough to boot and only from a cold boot, not a reboot. That system could use any basic GPU. I have an old Ti 4400 PCI card around here somewhere. That would be fine.

---

