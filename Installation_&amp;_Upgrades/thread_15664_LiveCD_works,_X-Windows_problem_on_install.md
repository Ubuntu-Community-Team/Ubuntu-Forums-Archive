---
title: "LiveCD works, X-Windows problem on install"
date: 2005-02-15
forum: Installation &amp; Upgrades
---

### Post by pasmith on 2005-02-15
Someone gave me a Live copy of Ubuntu (hope I have the terminology right...the version that you can boot and run off a CD to check things out). It worked flawlessly so I decided maybe it was time to give Linux another go as a Desktop OS.

So I installed a 2nd hard drive in the machine and burned the latest stable Warty copy of Ubuntu and installed it. Everything seemed to go fine, until I tried to log in, when I got a problem starting the X-Windows system. 

I have a Flatron L1920P hooked up via DVI interface to an nVidia GeForce 6800 GT. I wouldn't have been surprised to encounter errors, frankly, but after the LiveCD version worked, I assumed the installed version would too.

The only error I see during boot is a problem with my bios PNP, and a suggestion to boot with nobiospnp option, but I'm not sure where to put that line in the boot script.

Anyway, can anyone get me started on figuring out why booting off the CD would work, but booting off a hard drive wouldn't? Are the two versions not quite the same, or something?

Thanks in advance for any suggestions.

---

### Post by pasmith on 2005-02-16
OK, found some more info on this:

*One difference we can't improve at this stage is the way the Live CD and Install CD handle their auto-detection. Because they use slightly different systems for auto-detection, things that work perfectly on one might not work on the other, like sound or X resolution guessing. In general, the installation system gives you more room to tweak your config to work exactly the way you want it.* 
[https://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2004-09-15.8537444623](https://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2004-09-15.8537444623)

So I guess the thing to do is boot from the LiveCD, check the settings there, then set things the same in the installed version.

Can someone point me at where these config files are?

---

### Post by Cyhatch on 2005-02-16
[QUOTE=pasmith]
Can someone point me at where these config files are?[/QUOTE]
The name of your XFree config can be found on the first page of the XFree86 log (*/var/log/XFree86.0.log*), which starts with "*Using config file:*", if that's what you were asking about. Or on *man XFree86*, *man XF86Config*.

If it's a blue screen (of Ubuntu death, ha-ha) saying "I can't start X now, try later", [try](http://www.ubuntuforums.org/showthread.php?t=13219) this thread.

---

### Post by pasmith on 2005-02-16
Thanks for the link to that thread. I've got some more data now.

lspci reports

*VGA compatible controller: nVidia Corporation: Unknown device 0045 (rev a1)* 

Which doesn't sound good.

startx reports

[I](EE) No devices detected.

Fatal server error:
no screens found[I]

Looking at the log file, it lists a bunch of cards that the "nv" driver supports, but mine isn't in there. I'm wondering if I need an updated version of the "nv" driver, and if so, how do I update that?

Also during the configuring of xserver, I get to a screen that says users of computers with multiple video devices should specify the BusID of the card. I only have 1 card, but it does have 2 interfaces (one DVI, one VGA). So would this line apply to me? And if so, how do I know what the BusID ("in an accepted bus-specific format") would be?

It seems like the LiveCD maybe uses x.org instead of XFree, but I'm just guessing that from the files in /etc/X11.  Should I try to update to x.org (am I even calling it the right thing?)

Thanks for the help!

---

### Post by Cyhatch on 2005-02-16
**Driver**: This [page](http://www.nvidia.com/object/linux_display_ia32_1.0-6111.html) has *some*; your video card is listed in the readme.

**BusID**: dunno :-). Mine was "PCI:1:0:0" by default. Let's wait for a guru dude.

**LiveCD**: I couldn't start the xserver, too, until copied LiveCD's */etc/X11/XFree86Config-4* to the HD version of Ubuntu. I suggest you try getting that LiveCD again and doing it this way (if you haven't already, of course; don't forget to *back up*).

**Disclaimer**: I'm no pro; all links (hey, [another](http://www.nvnews.net/vbulletin/archive/index.php/t-1081.html) one!) are from the top of my google pile. Hardware is a tricky *, and if... bla-bla-bla. You know.

---

### Post by pasmith on 2005-02-16
Problem is, my LiveCD doesn't have an */etc/X11/XFree86Config-4*. Instead it has an xorg.conf, which I think is doing more or less the same thing. It seems to be using the same driver, and in fact lspci reports the same Unknown Device 0045, even though the LiveCD works like a charm.

Maybe I'll try installing the nVidia drivers... wish me luck. And thanks a bunch for the links.

....

Well, I can't do that because I don't have the source files for my kernal and the installer needs to compile the new module. Or if I have them, neither I nor the nVidia installer can find them. 

*sigh*

Maybe I'll just wait for the next release and hope for the best...

---

### Post by pasmith on 2005-02-17
Success!!!

I actually got disgusted and downloaded a Mepis distro and installed it. It worked, but it just didn't feel as 'comfortable' as ubuntu does. Made its a Gnome vs KDE thing, but whatever...

I reinstalled ubuntu and then found this thread:
[Help with Nvidia Drivers](http://www.ubuntuforums.org/showthread.php?p=65340) 

And from there, this great page: [Unofficial Ubuntu 4.10 Starter Guide](http://www.ubuntuguide.org/#installnvidiadriver) 

With the help of these resources, I installed a later nVidia driver and voila! I have an Xwindows desktop!!!

---

