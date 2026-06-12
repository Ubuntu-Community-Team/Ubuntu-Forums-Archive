---
title: "Feisty install hangs system Intel Core2 64bit"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by mcgd on 2007-06-19
Hi,

Got a new PC today, and tried to install Feisty on it.  It boots off the CD fine, I select the option to install, I can see it unpacking the kernel, then the screen clears and a couple of messages appear on the bottom, then I lose video.

After a minute or so, the CD works again for about 15-20 seconds and then the machine locks up completely.

I have tried in safe graphics mode and get the same result.

I've got an Intel Core2 DUO E6700 CPU, Gigabyte GA-965P-DS3 motherboard, Gigabyte (Nvidiia) NX8500GT video card.  I'm using the AMD 64 Desktop ISO, which should work for Intel 64 bit machines as well from what I can see.

Any help appreciated.  I was hoping I'd get a _bit_ further before I got into trouble!  I don't really know where to go from here except to go back to Fedora or something, but I'd like to get Ubuntu running if I can.

Many thanks

                         -Matthew

---

### Post by dabl on 2007-06-19
I run Feisty (both 32-bit and 64-bit) on an X6800 Core 2 Extreme, so I can assure you it's not the CPU.  With that new Nvidia card, odds are this problem is all about video display.  If you can make the "Alternate Install" CD from the downloaded ISO, I've had better luck with that one -- more user control.  As soon as it boots, I think (working from memory here) that you need to choose F6 "VGA" for the display, for installation purposes.  Don't let it auto-detect your Nvidia card, if that option presents itself ... or you can try it once, but I predict it won't work.  You're going to have to install your system as a VGA (or possibly "VESA) display, and then after the rest of it is working correctly, probably you're going to have to manually install the newest Nvidia Linux driver for your 8500GT.  A search on that card should show you how to set it up.

The latest Nvidia driver for Linux adds the 8500 GT, which means you will have to use their installer to install the driver, as per this: [http://www.nvidia.com/object/linux_display_ia32_100.14.09.html](http://www.nvidia.com/object/linux_display_ia32_100.14.09.html)

  HTH  :)

---

### Post by mcgd on 2007-06-19
Many thanks dabl, downloading it now, and then I'll give it a try.

---

### Post by dabl on 2007-06-19
If it still doesn't work, and all you can get is the text console, post again and I'll tell how to set up a VESA GUI that you can work in while you get your Nvidia driver installed.

---

### Post by mcgd on 2007-06-19
Ok here's what happened.  You're on the mark I think - looks like the video card.
I did a text install - just saw your message now.  The network doesn't seems to work but I got around that.

But now I have a system that I can boot, I have exactly the same problem I had with the original installer.  As soon as it tries to boot, I lose video and the machine hangs.  If I boot in recovery mode, it gets a little further, then prints this message:

aprgart: Detected Intel 965G chipset

and then hangs.

---

### Post by dabl on 2007-06-19
Argh -- that Intel 965 chipset has appeared in numerous previous posts -- you might search on that term and see if you can turn up workarounds.  My rig has the 975 and I'm lucky.

On the "hangs during boot" -- does it end up with a black screen and a blinking white "_" in the upper left corner?  If yes, then Alt-F1 to get a text console, and go ahead and log in, and run the configuration script.  If no then .... I guess it's really hung up.

If you get in via the text console, enter ```
sudo dpkg-reconfigure xserver-xorg
``` to start the script.  On the first screen answer "no" to autodetect, and on the second screen choose "VESA" display.  From there on you can accept defaults until you get to the monitor section.  On the screen resolution page, "x" one that you can live with for awhile, like 1024 x 768, and on the refresh just pick a range that your monitor or LCD can accept. When you're done with the script, it will dump you back to a text prompt.  At that point, type ```
startx
``` and you should get a GUI that you can work in while searching for a more elegant solution.

HTH

---

### Post by mcgd on 2007-06-19
Well I had a search around and finally got the system to boot by adding "agp=off" to the boot options.  Not ideal but I have a somewhat working system now.  Still strange networking problems, but at least I have something to work with.  Many thanks for your prompt help - much appreciated!

---

### Post by mcgd on 2007-06-20
Sadly, installing the NVidia drivers brings on the problem again.  Since I wasn't able to see the console until X had started, I'm locked out of the machine now.  *sigh*  Back to the drawing board.  I'm trying a reinstall with a daily build to see how it goes.

---

### Post by dabl on 2007-06-20
gaahhhh!

Well, you're suffering from "latest hardware" syndrome, I'm afraid -- the hardware builders get ahead of the Linux programmers, and a lot of them don't help the open source community much.  Keep a (Google) eye out for patches and workarounds, and hopefully better results won't be too long in appearing for you. :)

---

