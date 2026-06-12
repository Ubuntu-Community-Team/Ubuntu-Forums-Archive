---
title: "Hardy Instal Disks Hang"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by boomcat on 2008-08-01
I need some help doing a clean install of Hardy. The install disks freeze as soon as they boot.

I have done several installs before this (7.04 and 7.10) so I have burned lots of CDs and I have them available.

I put the 8.04 “alt” install disk into the computer and restart it. It begins to boot from the CD, the opening screen comes up, a half-second later the “Select Language” screen comes up and the computer freezes. No cursor or pointer is visible on the screen; the keyboard “NumLock” light is lit. After that the keyboard and mouse have no effect on the computer. The only solution is to power down. I have done this a dozen times with the same results.

I then tried to boot from the 7.10 disks. The 7.10 “alt” disk did the same thing as the 8.04 “alt” disk. The 7.10 “live” disk booted up to the opening screen and began the 30-second countdown, then froze when it had counted down to zero. So then I tried the 7.04 “alt” disk. This one booted and started the installation program, but when it was finished I had over 200 updates to install! Not a very efficient process, but I went ahead and updated until I had all of the updates. But this process is really not as good as a real “clean install”; that’s what I really want to do. I have serious video driver issues and I think a clean install would resolve them.

This is a new computer, a Dell E320, 3-gig Pentium-D with 1 gig of RAM. I am using onboard video. The motherboard has no provision for mouse and keyboard DIN connectors, so I am using USB keyboard and mouse.

I have verified the MD5 checksum of the 8.04 disk’s ISO file, but since it won’t even reach the first install screen, I can’t run a disk integrity check on it. I burned this disk at the lowest speed (1X) with Infra Recorder. I have burned two other 8.04 disks, one at 4X and one at 16X, and they give the same results.

Any suggestions?

---

### Post by Pumalite on 2008-08-01
Try the Alternate CD

---

### Post by boomcat on 2008-08-01
I tried the Alternate CD; it hangs at the first/second menu screen.

The Live CD counts down from 30 to zero, then hangs.

---

### Post by Pumalite on 2008-08-01
Post your complete specs

---

### Post by boomcat on 2008-08-01
Dell E320
Pentium-D at 3gHz
1 Gig RAM
Intel MB with 965 onboard video
300 Gig SATA drive
SATA DVD drive
USB mouse
USB keyboard
onboard audio
onboard network
Dell P990 monitor (18" CRT)

---

### Post by Pumalite on 2008-08-01
Try some boot parameters. Start with the most common ones:
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off all_generic_ide vga=0x31O
One at the time or in different combinations
(add at the end of the boot line)

---

### Post by boomcat on 2008-08-01
Do you mean add these commands to the end of the boot line in menu.lst?

---

### Post by Pumalite on 2008-08-01
We are talking about Hardy install. Add them to the boot line of the Live CD you are trying to install
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by boomcat on 2008-08-01
Wow! I didn't know that that could be done!

Open up the CD image, edit the boot file and re-burn it? That is too cool!

I will give it a try!

---

### Post by Pumalite on 2008-08-01
That's not it. If you cannot get to the Main Menu; you cannot do it. Better burn a new CD following this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by boomcat on 2008-08-01
OK, I now have a commercial installation disk, a DVD, of 8.04 LTS.

This disk boots to the same place, it jumps past the opening screen and locks up on the language screen. But this time, the 30-second countdown is going on behind it! And when it reaches zero it actually starts the kernel! Hurrah!

But when the desktop appears, the left 25% of the desktop is off the monitor's visible area. So I can't see the "Install" icon. I can't see the three menu items, either.

I have tried changing the resolution (I can guess where the menu item is and I can just see the end of the "Screen Resolutions" menu) but if I change it to 1024x768 it goes black. And if I change it to 800x600 the monitor loses sync lock and the picture rolls horizontally and vertically at the same time!

And I can't Alt-Drag the main screen to the right to make the install icon visible. Is there another way, other than double-clicking, to get installation going?

---

### Post by Pumalite on 2008-08-01
I don't know if this will help, but, it might. Have a good reading:
[http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting)
[http://ubuntuforums.org/showthread.php?t=579881](http://ubuntuforums.org/showthread.php?t=579881)
[http://ubuntuforums.org/showthread.php?t=505249](http://ubuntuforums.org/showthread.php?t=505249)
[http://ubuntuforums.org/showthread.php?t=601775](http://ubuntuforums.org/showthread.php?t=601775)
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
[http://www.linuxforums.org/forum/ubuntu-help/105368-newb-help-everything-too-big.html](http://www.linuxforums.org/forum/ubuntu-help/105368-newb-help-everything-too-big.html)

[http://ubuntuforums.org/showpost.php?p=3484653&postcount=15](http://ubuntuforums.org/showpost.php?p=3484653&postcount=15)

---

### Post by boomcat on 2008-08-01
You're not gonna believe this, but while I was reading those links you posted, I booted the DVD again, and this time it booted into 1024x768 (I guess) and I could see the blasted "Install" Icon, so it is working on a clean install right now!

Unbelievable.

Anyway, I have lots of tools for dealing with troublesome video resolutions once the OS is loaded and running...

---

### Post by boomcat on 2008-08-01
Installation worked fine, video is 1280x768, which looks kinda "squished" on a standard CRT monitor, but at least it is legible! So I started Add/Remove Software, and guess what? There are 252 updates available. I only got the disk from Amazon today!? So, I'm updating. Once more into the breach, dear friends.

One thing that puzzles me is that the manual for the Dell 990 monitor lists 13 different combinations of horizontal, vertical and scan rates. And as for the Intel graphics adapter, "sudo xrandr -q" lists only five combinations that it supports. And the only two combinations that they have in common are 640x480x60 and 1024x768x60. Are these the only two resolutions that I can use?

---

### Post by Pumalite on 2008-08-01
This is the best to choose and the most common...at least to start with
1024x768x60

---

### Post by boomcat on 2008-08-02
Setting the video resolution using the Terminal command:

sudo xrandr -s 1024x768

works like a charm.


And this: before I updated (200+ updates!) I had these resolutions available:

```


dave@server:~$ sudo xrandr -q 
[sudo] password for dave: 
Screen 0: minimum 320 x 200, current 1280 x 768, maximum 1280 x 1280 
VGA connected 1280x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm 
   1280x800       60.0  
   1280x768       60.0* 
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
dave@server:~$ 


```

and AFTER running the updates and rebooting, I get this:

```

dave@server:~$ sudo xrandr 
[sudo] password for dave: 
Screen 0: minimum 320 x 200, current 1600 x 1024, maximum 2048 x 2048 
VGA connected 1600x1024+0+0 (normal left inverted right x axis y axis) 352mm x 264mm 
   2048x1536      60.0  
   1920x1440      60.0  
   1856x1392      60.0  
   1792x1344      60.0  
   1920x1200      72.8     60.0  
   1600x1200      75.0     75.0     70.0     65.0     60.0  
   1600x1200 at 75   75.0  
   1680x1050      60.0  
   1600x1024      60.0* 
   1400x1050      85.3     74.8     70.0     60.0  
   1280x1024      84.8     85.0     75.0     60.0  
   1280x1024 at 85   85.0  
   1280x1024 at 60   60.0  
   1440x900       60.2  
   1280x960       85.0     60.0  
   1280x800       60.0  
   1152x864       85.1     75.0  
   1280x768       60.0  
   1152x768       54.8  
   1024x768 at 85   85.0  
   1024x768       84.9     85.0     75.1     75.0     70.1     60.0  
   1024x768 at 75   75.1  
   1024x768 at 60   60.0  
   832x624        74.6  
   800x600        84.9     85.1     72.2     75.0     60.3     56.2  
   800x600 at 85   85.1  
   800x600 at 75   75.0  
   640x480 at 85   85.0  
   640x480        85.0     84.6     75.0     72.8     75.0     60.0     59.9  
   640x480 at 75   75.0  
   640x480 at 60   60.0  
   720x400        85.0     70.1  
   640x400        85.1  
   720x350        70.1  
   640x350        85.1  
dave@server:~$ 

```

---

