---
title: "Getting black screen after installation of 15.10 ran boot-repair"
date: 2016-03-28
forum: Installation &amp; Upgrades
---

### Post by vsiege2 on 2016-03-28
Getting black screen after installation of server 15.10. I cna only see the manufactures logo then it goes to a black screen, skipping grub2. I reinstalled the system 3 times to no avail. 

I ran boot-repair. Here's my results: [http://paste.ubuntu.com/15547723](http://paste.ubuntu.com/15547723)  . I'd appreciate any help you can offer. 

I cannot access grub2 (used ESC and shift and right shift too). The only way I can boot ubuntu was by pressing ENTER.

[http://paste.ubuntu.com/15547723](http://paste.ubuntu.com/15547723)

---

### Post by T.J. on 2016-03-29
> **vsiege2 said:**
> Getting black screen after installation of server 15.10. I cna only see the manufactures logo then it goes to a black screen, skipping grub2. I reinstalled the system 3 times to no avail. 

I ran boot-repair. Here's my results: [http://paste.ubuntu.com/15547723](http://paste.ubuntu.com/15547723)  . I'd appreciate any help you can offer. 

I cannot access grub2 (used ESC and shift and right shift too). The only way I can boot ubuntu was by pressing ENTER.

[http://paste.ubuntu.com/15547723](http://paste.ubuntu.com/15547723)

15.10 is a short term release that is intended for developers or enthusiasts willing to handle bugs. Long term releases like 14.04 or the future 16.04 are intended for everyday use.You might get a black screen if your video driver is not configured. Can you provide specifications for your equipment, please?  I don't have enough information to help you.

---

### Post by vsiege2 on 2016-03-29
Thanks for the response. I picked a non LTS version for just that reason. The machine it's installed on is from about 2003 with an integrated video card from Sony. I can reach and see ubuntu only if I hit Enter (luck that I found this) a bunch, but Grub doesn't appear on screen. By now, I'd hope this Sony had a driver. Now, is there a way for me to adjust how the Grub video layer is working with the video? I'm guessing /etc/defaults/grub  

Grub is not my expertise.

---

### Post by oldfred on 2016-03-29
You show a SIS video in script.
>  *******lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter [1039:6325]
Subsystem: Sony Corporation Device [104d:811c] 



Do not know if this is still true. Your system is pretty old.
You may need to add a ppa to get correct driver.
[http://ubuntuforums.org/showthread.php?t=2215422](http://ubuntuforums.org/showthread.php?t=2215422)

---

### Post by vsiege2 on 2016-03-29
Thank you. I feel we're getting closer&#8230;Yes, I have checked the BIOS as well to confirm. As well, I have also checked the SONY specs for this workstation.

Here's the result of the command:
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo lshw -C video[/FONT][/COLOR]
``````
  *-display UNCLAIMED            description: VGA compatible controller
       product: 65x/M650/740 PCI/AGP VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller cap_list
       configuration: latency=0

       resources: memory:f0000000-f7ffffff memory:eb800000-eb81ffff ioport:d800(size=128)
```

Should I proceed with this code:
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-add-repository ppa: xorg-edgers
[/FONT][/COLOR]sudo apt-get update 
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install xserver-xorg-video-sis[/FONT][/COLOR]
```

---

### Post by oldfred on 2016-03-29
I believe that is the solution.
Can you get to a terminal in install. Not sure if that works any other way.

Or perhaps if a live Desktop installer works, then a chroot into your install?

---

### Post by vsiege2 on 2016-03-29
I can SSH into the box, that should do right? Or is this something that can only be done during installation?

---

### Post by oldfred on 2016-03-29
As long as you have some way to get into it, it should be ok.

---

### Post by vsiege2 on 2016-03-29
I get this error on install
```
E: Unable to locate package xserver-xorg-video-sis
```

---

### Post by oldfred on 2016-03-29
Did you enable ppa?
It seems SIS video driver not in Ubuntu repository anymore.

---

### Post by vsiege2 on 2016-03-30
Yes, I added it. And you're right, seems as though it's not in there anymore. I scanned around for people who kept the PPA alive but couldn't find any that installed. I guess I could purchase a separate ATI based card. Or would nvdia be a better choice?

---

### Post by oldfred on 2016-03-30
Did not notice exact ppa. 
Most of the video ppa have been consolidated into a semi-offical Ubuntu ppa for video drivers.
But yours is so old that it did not get copied over.

I image their is a way to directly download from one of the older repositories that still has it.
[http://packages.ubuntu.com/search?keywords=xserver-xorg-video-sis](http://packages.ubuntu.com/search?keywords=xserver-xorg-video-sis)

I would doubt spending much on that old of a system is worth doing. Better to save for newer system.

I only know nVidia. Older drivers are still available for older cards.
What little I understand about AMD is that driver changes are not as well organized.
But all users seem to have favorites, both AMD & nVidia.

Looks like you can click on link above and choose. Then you can download a package. But no idea if it will just install and work or not.

---

### Post by T.J. on 2016-04-14
Sorry I haven't gotten back to you - been very busy.

Wow, I have not seen an Silicon Systems (SiS) adapter in at least 10 years.  They are so old or uncommon, that you might have to compile special kernel support for them to function.  It is usually possible to get them working if you have knowledge of how to do so.  Linux does contain an SiS video driver last I checked, but it is very old, seldom used, and is probably AGP only.  It is possible I could help you to try if you feel brave enough.

On the other hand, if you chose replacement, I'd go with Nvidia.  Nvidia's driver quality is VASTLY superior to AMD's, although it appears AMD might start catching up in a year or two.

---

