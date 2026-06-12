---
title: "Nvidia driver installation leads to black screen (of death) on Hardy Heron"
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by NTBao on 2008-08-20
I know, I know... It has been posted like a milion times already, but where can I find the right solution to this problem specificly? I will try to explain my situation as detailed as possible. 

**The problem:**
Once I reboot the machine, GRUB shows up 4 choices I can boot from:
[LIST]
[*]Ubuntu 8.04.1, kernel 2.6.24-19-generic
[*]Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
[*]Ubuntu 8.04.1, memtest86+
[*]Windows Vista
[/LIST]

When booting the first choice (by default), the system starts loading. Even the Ubuntu loading screen shows up. Then once its done, screen goes blank. Stays black, no welcome sounds no reaction to CTRL+ALT+F1 or F-whatever, CTRL+ALT+BACKSPACE does pretty much the same: nothing. Even CTRL+ALT+DEL isnt working. Only way to reboot or shut down is the power on/off button.

**The cause**
From the point where I first ran Ubuntu, one of the things that I did was giving my OS a couple of updates that it was requesting me to download. Once thats complete, it asks me to reboot. Which I did. At the same time I notice the machine asking me about the graphical hardware detection. Ignoring that I continued rebooting. Which is fine, the machine still ran except the updates are not asked this time. But the graphical hardware are there. I assumed that it wanted to be clicked, so I did .. enabled the hardware and it was asking for a reboot again. No suprise I thought, but thats when "The problem" appeared.

Btw, I DO want to have the driver installed.

**The specs**
This is a new laptop machine from [http://www.xxodd.nl/](http://www.xxodd.nl/)

XXODD XNi762tu
Intel Core 2 Duo P9500 (2,53GHz, 1066Mhz FSB, 6Mb cache) Power Optimized
4GB DDR2 800MHz (2x 2GB)
nVidia GeForce 9300m GS 256MB 
ClearView TFT screen 1280x800
320GB 7200RPM Serial-ATA (not like it matters)

Pre-installed Windows Vista Business 32-bit
Self installed Ubuntu Hardy Heron (8.04) from downloaded ISO

Side note: Machine required acpi=off in order to run it at all (both Ubuntu-installation and the operation system).

Quite detailed enough I hope? But just so I dont sound like I havent tried anything yet to solve this problem, I present to you:

**(Attempted) Solutions that has been floating around the net**
One way to get pass the issue and into the GUI, was to run Recovery Mode. From here on I could run Terminal and enter
> sudo dpkg-reconfigure xserver-xorg
Finishing this setup will get my GUI back. But also back to where I was before; no graphical acceleration. Turning this back on will lead to the same results (on reboot): black screen of death. 

Another way to install is downloading the driver from NVIDIA website: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
For me it was Linux AMD64/EM64T Version: 173.14.12
Downloaded and followed the instruction on the website
> STEP 3: Install 
Type "sh NVIDIA-Linux-x86_64-173.14.12-pkg2.run" to install the driver. 

Ofcourse this requires turning of X with 
> sudo /etc/init.d/gdm stop

Before that I needed(because I didnt had it):
> sudo apt-get install build-essential pkg-config

Once I'm done building it, 
> sudo /etc/init.d/gdm start

Appearently, I did get the stuff installed right. Now I am asked to configure the graphics, saying 
> Ubuntu is running in low-graphics mode

Your screen and graphics card could not be detected correctly. To use higher resolutions, visual effects or multiple screens, you have to configure the display yourself.

| Configure... | Shut Down | Continue |
 Not sure where I am but I'm given the options to change my Screen and Graphics Card settings when I choose Configure. By default, the model of my laptop screen is "Plug 'n' Play. resolution of 800x600 at 73 Hz. Its blurry by the way. The Graphics card by default says: vesa - Generic VESA-compilant video cards
What? what? I can change this into nVidia because that is what I have... so I did. I chose nvidia once, didnt work. Next try nv (nVidia riva 128, riva tnt, geforce, etc etc) cards. Also no go.
What exactly happened, is I just get logged in and my drivers are still not yet enabled. However, the only progress is that its saying that my driver is "in use" but again, not enabled. Enabling it wont do anything new. After being this far I think I almost done it... Only problem is that the download driver couldnt detect my hardwares. Perhaps I'm installing too soon? They dont have the drivers yet? And should there be any work around at all?


It's a lot of reading I know, but I hope I at least made it easy to read and understand. Most importantly, clearly explained. Also, I'm also a newbie when it comes to linux of any kind of distro. Been using OpenSUSE in the past but I want ubuntu to be my joint from now on. Any reaction will be appreciated. And if I have anything new, I'll certainly update.

Peace

[COLOR="Blue"]Update:
I think I was right. I was too soon to expect the drivers to be out there already. 
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) does not show the 9300M
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html) does not have it listed in the supported products either.

Can anyone confirm that 9300M is in fact not yet supported for Ubuntu? or Linux for that matter.

Thank you in advance.[/COLOR]

---

### Post by Pumalite on 2008-08-20
Have you booted in Recovery Mode and tried the 'xfix' command?

---

### Post by NTBao on 2008-08-21
To do what? Get the driver to work? Yup, but when I select xfix, it shows:

> The X server reconfigration is now running. Your screen may flicker during hardware autodetection.

Then, approxametely 3 seconds later this appears:

> xserver-xorg postinst warning: overwrting possibly-costumized configuration file; backup in /etc/X11/xorg.conf.20080822040732

FATAL: Error inserting battery (/lib/modules/2.6.24-19-generic/kernel/drivers/acpi/battery.ko: No such device

Then I get back to the Recovery Menu. This might have anything to do with the fact that I turn my acpi=off during recovery mode? Cuz I cant seem to get Recovery mode running when I leave it on. Btw, I have tried this xfix many many times .. it always showed me that message. 

Thanks for your reply

---

### Post by Pumalite on 2008-08-21
Try making your backup the actual usable xorg.conf

---

### Post by NTBao on 2008-08-22
Sorry,
But what do I need to do? I'm quite new with these things so not sure what you mean. Very unfamiliar terms...
You want me to backup the xorg.conf?
Or do you want me to use a usable backup of xorg.conf? Also ... how the heck do I do all that? :P

Thanks

[COLOR="Blue"]Edit:
My acpi=off so that I can boot into Ubuntu. Maybe it has something to do with the acpi thats off that could have affected my driver installation and the xfix thing?[/COLOR]

---

### Post by Pumalite on 2008-08-22
At your own risk:
sudo cp /etc/X11/xorg.conf.20080822040732 /etc/X11/xorg.conf

---

### Post by NTBao on 2008-08-24
No luck. xfix gives me the same message.

I tried to install EvnyNG eventhough I promised myself not to use that, appearently, it didnt work either. Same results, no luck.

---

### Post by nbayiha on 2008-08-24
Did you follow this thread ?

[http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver](http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver)

Read carefully all the thread and you should have your problem fixed.

---

### Post by bobojijio on 2008-08-24
Sorry was a double post by accident

---

### Post by NTBao on 2008-08-24
Thank you for providing me the link. As I explained however, it is I think more GeForce 9M series specificly. Not just Geforce 9 series; the mobile version (which by the way could not be found at [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) ). I read it very carefully and I saw quite a few common things that I had indeed already tried. Especially the first two methods, number 3 and 4. Number 5 did come familiar but not quite precise as what I tried in the past. However, I didnt think this would do the trick either (See my Attempted Solutions that has been floating around the net). 

Sorry for not trying, but eventually, along the way I learned that OpenSuse was what I needed after all. Too quick on giving up; or so I would judge myself that way, I ran back to OpenSuse. In fact, i'm installing it right now over Ubuntu. Not saying this will solve my graphical problem at all, cuz I really think the driver just isnt released yet.

I guess we can leave this thread dead now.

---

### Post by Pumalite on 2008-08-24
Re: nvidia drivers for 9600GT
You will need the Nvidia driver found here:-
[http://www.nvidia.com/object/linux_d...32_173.08.html](http://www.nvidia.com/object/linux_d...32_173.08.html)

---

### Post by NTBao on 2008-08-24
First off, I was talking about Geforce 9300M.

Secondly, the URL isnt really working.. or is it me? I mean it literally links to [http://www.nvidia.com/object/linux_d...32_173.08.html](http://www.nvidia.com/object/linux_d...32_173.08.html)

Thanks

Update:
Found the link you meant with google power.
[http://www.nvidia.com/object/linux_display_ia32_173.08.html](http://www.nvidia.com/object/linux_display_ia32_173.08.html)

And again ofcourse, issues
1. 32-bit processors installation, which my ubuntu is not
2. 173.08 is older version, the one I'm using is 173.14, should have more driver support.

Truth is I never installed 173.08 version before. I might try that.

Update again:
Looks like its not going to work anytime soon. I already installed OpenSUSE anyway so I guess i'll leave this one behind. Like I said, its because OpenSUSE has some goods that I might need. Besides, even in OpenSUSE I cant get my 3D acceleration working. Its unfortunate, but I'm not in a hurry.

---

### Post by theojepsen on 2009-02-01
I am having EXACTLY the same problems that you are having - or had had. I HAVE to boot with "acpi=off noacpi" if I want to do anything at all. None of the howtos I can find around on the net apply to this problem because this is different as acpi is disabled. Is there anyone out there that has a solution to this problem?

I am really surprised and disappointed that Ubuntu does fully not support my hardware. I think that if linux is to grow they will have to fix all these problems because an average user will find it unacceptable that just installing it on a computer is so problematic.

---

