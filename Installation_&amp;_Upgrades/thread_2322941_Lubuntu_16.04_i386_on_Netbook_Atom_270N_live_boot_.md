---
title: "Lubuntu 16.04 i386 on Netbook Atom 270N live boot failure."
date: 2016-05-01
forum: Installation &amp; Upgrades
---

### Post by ajgreeny on 2016-05-01
I am trying to clean install Lubuntu 16.04 i386 on a fairly old netbook which runs 14.04 very well.

The spec is as follows in the current 14.04:-
> CPU:       Single core Intel Atom CPU N270 (-HT-) cache: 512 KB flags: (nx pae sse sse2 sse3 ssse3) 
           Clock Speeds: 1: 1600.00 MHz 2: 1067.00 MHz
Graphics:  Card: Intel Mobile 945GSE Express Integrated Graphics Controller 
           X.Org: 1.17.1 drivers: intel (unloaded: fbdev,vesa) Resolution: 1024x600@60.0hz 
           GLX Renderer: Mesa DRI Intel 945GME x86/MMX/SSE2 GLX Version: 1.4 Mesa 10.5.9
I can not get the machine to boot to a live desktop but only a blank screen with blinking cursor top left.  I have tried many of the possible boot options by booting from a multiboot USB with grub 2 installed, but so far no real luck.

I have tried using the mini CD version of 16.04 and that does exactly the same after installing.  I can not even get to a text boot or use Ctrl+Alt+F1 as it momentarily shows a command line but immediately goes back to the blank desktop with blinking cursor.

Anybody got any clues, or am I destined to keep to 14.04 for now, and when that loses support move to some other distro, eg Debian 8, which does run, though I prefer Lubuntu.  Could this possibly be a systemd vs upstart problem and if so how do I boot a live system using upstart?

---

### Post by RobGoss on 2016-05-01
How did you get [COLOR=#000000]14.04 on that netbook?

[/COLOR]Can you access the bios for your netbook and choose to boot from a UBS drive

[COLOR=#000000]I currently have a HP mini netbook with 16.04 on it I was able to boot-up from a USB drive it took some doing but them i was able to install it[/COLOR]

---

### Post by ajgreeny on 2016-05-02
No, you misunderstood my meaning.

I have no problem booting the USB on the netbook and have done it many times; it is just that 16.04 will never get to a desktop or even a command-line screen.  The same USB boots fine on another laptop and gets to a full desktop; it is simply the old netbook that refuses to get to that point, so I imagine that it is a boot option that is needed.

Thanks for trying, however; I appreciate the thought.

---

### Post by RobGoss on 2016-05-02
> **ajgreeny said:**
> No, you misunderstood my meaning.

I have no problem booting the USB on the netbook and have done it many times; it is just that 16.04 will never get to a desktop or even a command-line screen.  The same USB boots fine on another laptop and gets to a full desktop; it is simply the old netbook that refuses to get to that point, so I imagine that it is a boot option that is needed.

Thanks for trying, however; I appreciate the thought.


Oh sorry for over looking that, Yea I would have to say my netbook is also about 10-plus years or even older but it's running 16.04 so far, strange you're unable to get the desktop loaded

---

### Post by sudodus on 2016-05-02
I think this is the problem:

> Graphics: Card: Intel Mobile 945GSE Express Integrated Graphics Controller

Maybe it is the same problem as described here:

[Lubuntu 16.04 flashing cursor with certain Intel video drivers](http://ubuntuforums.org/showthread.php?t=2321734)

In that case Xubuntu Core might be a working alternative.

I have also heard the UXA acceleration might help with some old Intel graphics. (I have heard the opposite too.) So I think it will be trial and error.

Good luck :-)

---

### Post by ajgreeny on 2016-05-02
Thanks sudodus; I'll look into that a bit further.  I did search but must have not used the correct search-terms; typical!

Obviously, I can not boot and then install any thing by command-line as I can not even get to that point which seems strange, nor can I create an xorg.conf to make the system use UXA as, again, I can not even get to a command-line.

I'll try Xubuntu-core to see if that is any better.

Interestingly, I have just booted to a live Debian 8.4 and though that will boot it will give me only a very low screen resolution which is not really usable.

I wonder if this is caused by the use of new kernels in the 4.# series.

EDIT:
I have just tried the full version of Xubuntu 16.04 on this machine and that boots to a live system perfectly, and runs fine as far as I can tell.  I may move to that even though Lubuntu would be my preferred version on this old machine.

---

### Post by sudodus on 2016-05-02
I think it is the driver for your graphics chip. There are bug reports about it. If we are lucky, there will be an upgrade from Intel, that can fix several current problems with old hardware.

-o-

Maybe you can install a compressed image file into a USB 3 pendrive in another computer and while there install Xubuntu Core and / or UXA acceleration. After that you can try booting your netbook with it.

See these links

64-bit system:
[Installation/UEFI-and-BIOS/stable-alternative](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative), dd_text_16.04-UEFI-n-BIOS-4-pendrive-7.8GB.img.xz

32-bit system:
from tarball
[/OBI/Xenial-32-txt](https://help.ubuntu.com/community/OBI/Xenial-32-txt)

can also be installed from a compressed image file from:
[http://phillw.net/isos/linux-tools/compressed-images/](http://phillw.net/isos/linux-tools/compressed-images/), dd_Xenial-32-txt.img.xz (7.8 GB, so should fit in an 8 GB pendrive)

---

### Post by ivo.kovacic.sk on 2016-06-17
Look here
[http://askubuntu.com/questions/766402/i-cant-access-to-the-login-screen-in-lubuntu-16-04-lts-2](http://askubuntu.com/questions/766402/i-cant-access-to-the-login-screen-in-lubuntu-16-04-lts-2)

It seems to be similar. There is no firm solution available.

---

