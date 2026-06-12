---
title: "Can't install Lucid (monitor switches to standby)"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by denBosch on 2010-05-05
I cannot install Ubuntu 10.04, or even boot into the live CD. I'm not an expert, but I've used Ubuntu for several years, and I'm pretty sure I'm not doing anything stupid...

Here's what happens when I boot with the Ubuntu 10.04 live CD:

[LIST=1]
[*]I get a purple screen with just an accessibility(?) symbol at the bottom (this lasts 15 seconds).
[*]The screen goes black, with a flashing cursor, then changes back to purple, this time with an Ubuntu logo, with 5 dots acting as a progress indicator (this lasts about 1 minute).
[*]The screen switches to standby. The CD drive continues to make noises for another minute or so, then stops.
[/LIST]

I physically removed my graphics card (ATI Radeon HD 5770), and plugged the monitor straight into the VGA port on the motherboard. Now the CD boots up fine.

I could try installing Ubuntu at this point, while my graphics card is unplugged, and then plug my graphics card back in, and see if it starts working then... But I'm not sure if this is a good idea?

Any advice greatly appreciated.

---

### Post by v79 on 2010-05-08
Did you ever manage to resolve this while using your ATI card? I'm having exactly the same problem on a HD 5670. Really don't want to have to open up the PC.

---

### Post by denBosch on 2010-05-10
> **v79 said:**
> Did you ever manage to resolve this while using your ATI card? I'm having exactly the same problem on a HD 5670. Really don't want to have to open up the PC.

After my first post here, I did go ahead and install Lucid (alongside my existing Karmic installation) while the graphics card was removed. Then, after plugging the card back in, I couldn't boot into the new system without the graphics turning off, but I found a way to get it working: I booted into Karmic, mounted the new Lucid partition, and then copied over a config file (following advice from a forum) from Karmic to Lucid. Then I could restart and boot into Lucid, and it worked fine. At first it was in low graphics mode, but at least it worked, so I could run the automatic Hardware Drivers installer, and now it's working perfectly.

If you really don't want to open up your PC, you might be able to use the alternative setup CD to install Lucid without full graphics, and then replace the config like I did. But it all depends on your current setup -- do you already have an old Ubuntu working with your graphics card? Could you install Lucid alongside it?

Post here and let me know if you still need help with this, and tell me about your current setup. I'm at work at the moment, but when I get home (in about 10 hours from this post) I'll check here again and post instructions if you need them. Can't promise they'll work, but I'll try.

---

### Post by o0moe0o on 2010-05-13
Hi denbosch...
i got the same problem like you -.-'
pls can you tell me, what you did?

moe

---

### Post by denBosch on 2010-05-13
OK, here's what I did...

(These steps assume you have a working copy of Karmic, with your ATI graphics card already set up on it. If you haven't, then see note below.)

[LIST=1]
[*] Removed graphics card, then installed Lucid alongside my previous installation of Karmic.
[*] Put graphics card back in. If you boot, then choose the new (Lucid) installation at startup, the monitor switches off. So restart and boot into Karmic.
[*] Open a Nautilus window as root (press Alt+F2, then enter [FONT="Courier New"]gksudo nautilus[/FONT] ). Find the new (Lucid) partition, and mount it.
[*] Now, you can copy the file [FONT="Courier New"]/etc/X11/xorg.conf[/FONT] from your Karmic to your Lucid. 
[*] Restart. This time, at the boot menu, choose Lucid. If all went well, then hopefully the screen will *not* turn off this time, and instead you'll get a dialogue warning that your graphics drivers aren't configured properly (or something like that). I chose the option to run in low graphics for "this session only". 
[*] Hopefully you're now able to log in. The graphics look pretty awful, but that's OK for now. Now you could probably just skip to the next step, but if you want to do exactly what I did (it worked for me), then you should run the automatic Update Manager (in the system menu) to install general updates. And then restart when it asks you to, and boot into Lucid again (same warning about graphics; give the same answer, "this session only").
[*] Now, I went to System > Administration > Hardware drivers, and used this to automatically install the proprietary ATI drivers. Restart.
[*] If it worked, then Lucid will now boot up with perfect graphics. (Incidentally, when I installed Karmic last year, the automatic hardware driver installer thing didn't work, and I had to manually download and run files from ATI, plus a load of manual configuring. But this time the automatic thing worked perfectly.)
[/LIST]

**What if you don't have a working copy of Karmic?** In this case, you could manually create the [FONT="Courier New"]/etc/X11/xorg.conf[/FONT] file, using the content from my one. I don't know if it varies from system to system, so I've given instructions above for copying your own one over from Karmic to Lucid. But if you want to give this a try, here is the content of my file:
```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

I guess the simplest thing would be to boot into the Karmic live CD (or any previous version of Ubuntu, or any Linux), mount the Lucid partition that you've just installed, create the file [FONT="Courier New"]/etc/X11/xorg.conf[/FONT] , and paste the above content into it. Then proceed from step 5 above.

And let me know if this works or not. Good luck.

---

### Post by o0moe0o on 2010-05-13
Thanks for your very quick answer!

I installed Lucid on my Win partition. I got a perfect working Karmic and the Lucid. :P
But in the Lucid there is no xorg.conf, so that would be the problem. But I'm not able to copy it from Karmic :confused:
Maybe it's because I choose to crypt the my home-folder :-k

So I will have to reinstall Lucid....
I will post the result

moe

---

### Post by wojox on 2010-05-13
> **o0moe0o said:**
> Thanks for your very quick answer!

I installed Lucid on my Win partition. I got a perfect working Karmic and the Lucid. :P
But in the Lucid there is no xorg.conf, so that would be the problem. But I'm not able to copy it from Karmic :confused:
Maybe it's because I choose to crypt the my home-folder :-k

So I will have to reinstall Lucid....
I will post the result

moe

What graphics card/chip do you have?

---

### Post by o0moe0o on 2010-05-13
> **wojox said:**
> What graphics card/chip do you have?

NVidia Geforce 9500 GT

---

### Post by denBosch on 2010-05-13
My problem was with an ATI graphics card, so I'm not sure my solution is going to work for you.

---

### Post by wojox on 2010-05-13
> **o0moe0o said:**
> NVidia Geforce 9500 GT

So run

```
sudo nvidia-xconfig
```

That will install a xorg.conf in /etc/X11/

---

### Post by o0moe0o on 2010-05-13
> **denBosch said:**
> My problem was with an ATI graphics card, so I'm not sure my solution is going to work for you.     

Yes, but on that way I found out, that there is no xorg.conf what causes the issue :P

> **wojox said:**
> That will install a xorg.conf in /etc/X11/

but I'm not able to do anything because the Monitor is in standby :P

---

### Post by wojox on 2010-05-13
> **o0moe0o said:**
> 

but I'm not able to do anything because the Monitor is in standby :P


#Boot Live cd
#Open a terminal:
sudo fdisk -l
#Determine what partition
sudo mount /dev/sda1 /mnt
#Open nautilus as root
gksudo nautilus
#Navigate to /etc/default/grub
#Change this to 
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset quiet splash"

---

### Post by Eli88 on 2010-08-14
hi all 

I had the same problem with my nvidia 9600GT graphics card, it was connected to my 23" screen with a DVI connection.
My graphics card doesn't support VGA so I just used a DVI to VGA converter, and plugged a VGA cable to my screen and it just worked.

hope I helped someone :)

---

### Post by huckleberry999 on 2011-05-11
I have the same problem with 11.04 and gforce 8500.

Monitor goes to standby and cannot use Ubuntu!

Oh well, theres always windows....!

---

