---
title: "Problem with the bootable USB key: can't start the pc without it"
date: 2013-05-04
forum: Installation &amp; Upgrades
---

### Post by seulava on 2013-05-04
Hi, 
I have installed Lubuntu on my netbook (Samsung N150, I used to have windows seven) and everything is working good when my bootable key is connected  The problem is  I can't start the netbook if the key is disconnected. In Disk Utiliy when I want to do "safe removal", I get an error message: An error occurred while performing and operation on "pny USB 2.0 FD (pny USB 2.0 USB FD): the device is busy. 
In details there is: One or more partitions are busy on /dev/sdb.
When I installed Lubuntu I choose to install, not to try without install, so I don't understand why my netbook needs the bootable USB key! 
If I start my computer without the key, it starts normally (I see the samsung's logo) and then, the screen stays dark with a little flashing line in the left corner. In the BIOS I put the HDD on first position.
So, I really don't understand what is happening, I need help!
Thanks
Seulava

---

### Post by TheFu on 2013-05-04
Run the boot info script and post the output/link here.  This should provide all the information we need to diagnose the issue. 
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) explains more.

---

### Post by seulava on 2013-05-04
Thanks you for helpinf me
I read the tutorial you indicated me, but
I can't go to "try lubuntu" cuz when I start th netbook with the kyr connected, it start immediatly (like I it should normally does when the pc is starting)

---

### Post by C.S.Cameron on 2013-05-04
Once you are running from the internal drive open terminal and try:

```
update-grub
```

---

### Post by oldfred on 2013-05-04
Some computers promote a flash drive to sda when installing. That creates a problem with auto install as grub is installed to sda by default. So you probably overwrote the installers boot loader with grub from your actual install.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

---

### Post by TheFu on 2013-05-04
> **seulava said:**
> Thanks you for helpinf me
I read the tutorial you indicated me, but
I can't go to "try lubuntu" cuz when I start th netbook with the kyr connected, it start immediatly (like I it should normally does when the pc is starting)

You can run that script on any *ubuntu OS that runs.  I suspected what the others are saying above, but wasn't certain since there are all sorts of strange ways that people can setup Ubuntu these days. The bootinfo script would provide facts necessary to know exactly what happened.

---

### Post by seulava on 2013-05-16
Hi 
I'm sorry i didn't reply before. Actually, im french, i'm on that english forum cuz nobody could help on the french one. So have some problem to understand you. And I know a little bit ubuntu, i installed it with a cd, but that's all. So I don't really understand  your advises.I did [COLOR=#000000]sudo grub-install /dev/sda[/COLOR]Ubun it wrote "no error reported", and now?[COLOR=#000000]
[/COLOR]
[COLOR=#000000]Thanks[/COLOR]

---

### Post by oldfred on 2013-05-16
Download and run this:

 LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

### Post by TheFu on 2013-05-16
> **seulava said:**
> Hi 
I'm sorry i didn't reply before. Actually, im french, i'm on that english forum cuz nobody could help on the french one. So have some problem to understand you. And I know a little bit ubuntu, i installed it with a cd, but that's all. So I don't really understand  your advises.I did [COLOR=#000000]sudo grub-install /dev/sda[/COLOR]Ubun it wrote "no error reported", and now?[COLOR=#000000]
[/COLOR]
[COLOR=#000000]Thanks[/COLOR]

Well, in theory, that should solve the issue. Did you try to boot?

I'm confused still.  If you installed using a CDROM, where did the USB-flash drive come into this setup and how did that become necessary for booting?

---

### Post by seulava on 2013-05-17
Sorry, I'm not clear. I installed it on an other computer using CD but on my nebook i can't do the same: there is no CD reader. 
I tried something. I disconnected the USB although it was busy by a partition. And nothing special happends, i can still access to my files. So the pc just needs the USB for starting?

---

### Post by seulava on 2013-05-17
finally i can reboot too I shutdown it and start again. I don't know why now it's works. Maybe cuz i did [COLOR=#000000]sudo grub-install /dev/sda[/COLOR]Ubun , that's really strange. 
Any way, thank you very much for your help !! Have a good day
Seulava

---

