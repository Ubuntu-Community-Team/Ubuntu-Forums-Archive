---
title: "can't install ubuntu 8.04 on sony laptop"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by yanghua on 2008-06-06
I got a Sony VAIO laptop PCG-FX150K.
I been trying to install the latest ubuntu 8.04 for past few days but with no luck.
I tried the Desktop version and the alternate version CD.
When the cd boots I can see the install menu and chose the language but after I chose Install then all I get is a blank screen with a courser blinking on top left of the blank screen. I tried to wait for couple hours on that but still stay the same.
Anyone has any idea what could cause this?

When I runt he memory test I got the following information:
Pentium III 745.3MHz.
L1 cache 32K
L2 cache 256K
Memory 254M
Chipset Intel i815
Thanks

---

### Post by PmDematagoda on 2008-06-06
With the amount of RAM you have, your Ubuntu experience may not be that great. If you want to use Ubuntu with no problems then you should increase the amount of RAM to about 512Mb, or use another, lighter flavour of Ubuntu such as [Xubuntu]("http://www.xubuntu.org/get").

---

### Post by yanghua on 2008-06-06
Well, The things is I can't even get pass the first step of the install.

As far as what I am going to do is simple, all I need is for it to run open office and internet.

Thanks

---

### Post by balaknair on 2008-06-06
The issue about the RAM aside(min 256 MB to install via Live CD, 512 MB recommended), I think you'll have better luck with Ubuntu 7.10 Gutsy. There seems to be some bug(perhaps related to the 2.6.24 kernel, since aomeone said that compiling and installing 2.6.25 fixed things) where it fails to load with some hardware configurations. I had the same issue with the CD when I tried a fresh install on my desktop, and a distro upgrade trashed my install. I reinstalled Gutsy and will probably wait out Hardy and go for Intrepid Ibex(Ubuntu 8.10) if they use kernel 2.6.25. I had no issues on my laptop though, Hardy installed like a dream. I'll be wiping the Vista installed on it and replacing it with XP home this weekend, so the first one was just a trial to see how Wubi works, and I have to say it was a great experience- easy and effortless. If only it worked on my desktop too.

In the meantime, my advice to you would be to opt for a lightweight version like Xubuntu 7.10(lacks the bells and whistles of Gnome but runs like a dream on low spec hardware, though open office might prove to be a drag). You can also install the Xubuntu desktop after trying out gnome(Ubuntu). Extremely easy instructions are available in this excellent guide
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

You might also want to check this page
[http://www.psychocats.net/ubuntu/whichbuntu](http://www.psychocats.net/ubuntu/whichbuntu)
to help decide which version to choose.
I'd suggest Xubuntu though.

All the best

---

### Post by yanghua on 2008-06-06
Hi,
I tried to go through the website looking for the 7 version of the xubuntu but without luck.
Any idea where I can download it?
Thanks

---

### Post by avtolle on 2008-06-06
> **yanghua said:**
> Hi,
I tried to go through the website looking for the 7 version of the xubuntu but without luck.
Any idea where I can download it?
Thanks
[http://cdimage.ubuntu.com/xubuntu/releases/gutsy/release/](http://cdimage.ubuntu.com/xubuntu/releases/gutsy/release/) should get you what you are looking for.

---

### Post by yanghua on 2008-06-07
Hi,
STill the same with the 7.1 version.
Also tried the X version and come to a same result.
Any other ideas?
Thanks

---

### Post by yanghua on 2008-06-08
I did finally managed to install by remove  splash and quiet from kernel and append linux acpi=off at install screen, and was able to finish the install but once its done and rebooted it basicly went into the same problem again. But I have non idea where to go to modify the same information in order to make it boot.
Any one has any ideas?
Thanks

---

### Post by PmDematagoda on 2008-06-08
> **yanghua said:**
> I did finally managed to install by remove  splash and quiet from kernel and append linux acpi=off at install screen, and was able to finish the install but once its done and rebooted it basicly went into the same problem again. But I have non idea where to go to modify the same information in order to make it boot.
Any one has any ideas?
Thanks

Once you reach the GRUB menu, press E at the Ubuntu entry, press E at the kernel entry and add the required additions at the end of the entry and press Enter. Then boot Ubuntu by pressing B.

---

### Post by yanghua on 2008-06-09
Hi,
Just wondering once I modified the line will it be saved? or each time i had to do the same?

Also if its possible to change the screen size of the desktop? right now it only displays in the center of the screen.
Thanks

---

### Post by Partyboi2 on 2008-06-09
Once you have booted to the desktop, open a terminal (Applications>Accessories>Terminal) and type
```
gksudo gedit /boot/grub/menu.lst
```(Replace gedit with mousepad if you are using xubuntu) look for this part:
> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=c61e113a-1e75-40cc-8051-bcceeb33acff ro splash
Add the boot option or make changes to this line:
 # kopt=root=UUID=c61e113a-1e75-40cc-8051-bcceeb33acff ro splas[COLOR=Red][COLOR=Black]h[COLOR=Red] acpi=off[/COLOR]
save the changes then back in the terminal
[/COLOR][/COLOR]```
sudo update-grub
```[COLOR=Red][COLOR=Black]
[/COLOR]
[/COLOR]

---

