---
title: "[SOLVED] Login screen problem"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by UncleBark on 2008-04-22
Well, my first issue is my login screen.  I do not know how to resize it.  Right now it is so large I cannot see the area where I need to login.  How do I improve the resolution?

---

### Post by UncleBark on 2008-04-22
Update.....
I noticed this particular problem AFTER I started using the restricted driver for my graphic card.  I'm kinda hesitant about switching back.....

---

### Post by uhhuhuhhuh on 2008-04-22
I'm having the same problem--I've just been typing in my login info without being able to see any of the boxes--I changed the resolution once I logged in, but that didn't impact the login screen.

I'm working on getting my internet back, first..

---

### Post by theophiles on 2008-04-23
same problem here. I've wondered if changing something in my xorg.conf would help, but I am still too green to know what to change. Here are the portions where I *think* something might need to be changed:
```
Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Sony"
	Modelname	"Sony SDM-HS73"
	Horizsync	28.0-65.0
	Vertrefresh	48.0-65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1400	1050
		Modes		"800x600@60"	"1024x768@60"	"800x600@56"	"1280x960@60"	"640x480@60"	"1280x1024@60"	"1400x1050@60"
	EndSubSection
EndSection
```

My screen resolution once I log in is 1024x768

Thanks for any help!

---

### Post by theophiles on 2008-04-23
I am considering erasing every resolution size above the resolution size that I am using, but I am worried that their might be side effects that might be hard to correct.

Is that the right thing to do?

---

### Post by UncleBark on 2008-04-24
> **theophiles said:**
> I am considering erasing every resolution size above the resolution size that I am using, but I am worried that their might be side effects that might be hard to correct.

Is that the right thing to do?

I thought about that but don't want to mess with those settings.  I did remove the restricted driver but that didn't change anything.

---

### Post by Creptic on 2008-04-24
Try commenting out: #Virtual	1400	1050

In Modes add only the mode you want (or blank). Then try one at a time after its working.

Uncomment if you wish afterwards: Virtual	1400	1050

---

### Post by Peter09 on 2008-04-24
install the startup manager - its in the repos

or

```
sudo apt-get install startup-manager
```

this allows you to change your startup configuration.

PC

---

### Post by theophiles on 2008-04-24
Thanks for the idea, unfortunately it didn't work so far, but maybe with some help we can still figure this out.

First, to get startup manager you actually need to type:```
sudo apt-get install startupmanager
``` there is no hyphen. Or, in all honesty I found it in synaptic when typing it with the hyphen didn't work. Then I tried to run it, but it said I needed to be root. So, I became root and ran it. The program ran, and I chose my new screen resolution, but nothing changed. I think that the reason nothing changed is that "splashy" was "not detected" here is the complete readout from the startup manager open to close:
```
Grub2 not detected
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-16-rt
Found kernel: /vmlinuz-2.6.24-16-generic
Found kernel: /vmlinuz-2.6.24-15-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Grub Legacy detected
Usplash detected
Splashy not detected
/usr/share/startupmanager/gtk_frontend.py:193: GtkWarning: gtk_window_realize_icon: assertion `info->icon_pixmap == NULL' failed
  self.main_window.show()
update-initramfs: Generating /boot/initrd.img-2.6.24-16-rt
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
update-initramfs: Generating /boot/initrd.img-2.6.24-15-generic
update-initramfs: Generating /boot/initrd.img-2.6.24-14-generic
update-initramfs: Generating /boot/initrd.img-2.6.24-10-generic
update-initramfs: Generating /boot/initrd.img-2.6.24-8-generic
update-initramfs: Generating /boot/initrd.img-2.6.24-7-generic
update-initramfs: Generating /boot/initrd.img-2.6.24-5-generic
update-initramfs: Generating /boot/initrd.img-2.6.24-5-386
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-16-rt
Found kernel: /vmlinuz-2.6.24-16-generic
Found kernel: /vmlinuz-2.6.24-15-generic
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done
```

---

### Post by Fire_Chief on 2008-04-24
There is a Launchpad Bug report on this issue.[#214704]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/214704")

Two users resolved the issue by applying all the latest updates to their Hardy install and then running```
sudo dpkg-reconfigure xserver-xorg
sudo nvidia-xconfig
```
I have not yet been able to try this as my Hardy machine is at home but I'll try it this week and let you know.

This is assuming you have an Nvidia graphics card.

Cheers!

---

### Post by theophiles on 2008-04-25
Many thanks Fire_Chief, that worked!

---

### Post by UncleBark on 2008-04-25
No luck here.  I read the bug report and most seem to be having luck with this.  I'm missing something so the digging continues.

---

### Post by UncleBark on 2008-04-25
> **UncleBark said:**
> No luck here.  I read the bug report and most seem to be having luck with this.  I'm missing something so the digging continues.

Never mind!  I just need to learn how to type.....I rechecked everything and now the problem is solved.  Thanks all!

---

### Post by Fire_Chief on 2008-04-25
I too got this to work this morning on my HH system :D

Though I did have to set the resolution via the Nvidia-X-Settings control panel but after that it was all good.

UncleBark, would you please mark the thread [SOLVED].

Cheers!

---

### Post by UncleBark on 2008-04-25
> **Fire_Chief said:**
> I too got this to work this morning on my HH system :D

Though I did have to set the resolution via the Nvidia-X-Settings control panel but after that it was all good.

UncleBark, would you please mark the thread [SOLVED].

Cheers!

Ummm, I can't seem to change it to [solved].:confused:

---

### Post by ggallin08 on 2008-05-10
> **Fire_Chief said:**
> There is a Launchpad Bug report on this issue.[#214704]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/214704")

Two users resolved the issue by applying all the latest updates to their Hardy install and then running```
sudo dpkg-reconfigure xserver-xorg
sudo nvidia-xconfig
```
I have not yet been able to try this as my Hardy machine is at home but I'll try it this week and let you know.

This is assuming you have an Nvidia graphics card.

Cheers!

This worked for me in Hardy Heron. Thanks!

---

