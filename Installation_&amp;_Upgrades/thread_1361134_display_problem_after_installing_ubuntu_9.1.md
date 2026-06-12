---
title: "display problem after installing ubuntu 9.1"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by new lin on 2009-12-21
after moving from XP to UBUNTU  i faced a problem with my display  

  the configure display panel is showing as:

[IMG]http://www14.0zz0.com/2009/12/21/22/384074933.png[/IMG]

my vga card is 

[IMG]http://www14.0zz0.com/2009/12/21/22/417447558.png[/IMG]

my display is : HP w2207h

neither rotation nor refresh rate can be changed

---

### Post by Greenwidth on 2009-12-21
Is the Nvidia driver enabled in:
Admin > Hardware Drivers ?

---

### Post by madmax.santana on 2009-12-21
I am not an expert in Ubuntu though. But I have an nVidia GeForece GT 9600M in my notebook PC. I did this when I installed Ubuntu (8.04 LTS, 9.04, now 9.10).
1- I downloaded the driver binaries form nVidia website (they let you choose your OS and Linux in included in the Menu)
2- I switched to console by Ctrl+Alt+F1
3- I typed
> sudo bash
to enter root shell and then
> /etc/grub.d/gdm stop
in Ubuntu 8.04 and Ubuntu 9.04
and just
> service gdm stop
in Ubuntu 9.10
4- I made the driver binary executable by
> chmod +x path/to/file
5- I ran the file by just typing the file path and followed the instructions on the installer screen. Then rebooted my PC.

This also installed x-server settings. Although Ubuntu had already set my display resolution to a very appropriate one but if you want to change it, you can do that by finding NVIDIA X-Server in System Settings and follow the directions.

---

### Post by new lin on 2009-12-22
> **Greenwidth said:**
> Is the Nvidia driver enabled in:
Admin > Hardware Drivers ?

nothing is listed there

---

### Post by new lin on 2009-12-22
> **madmax.santana said:**
> I am not an expert in Ubuntu though. But I have an nVidia GeForece GT 9600M in my notebook PC. I did this when I installed Ubuntu (8.04 LTS, 9.04, now 9.10).
1- I downloaded the driver binaries form nVidia website (they let you choose your OS and Linux in included in the Menu)
2- I switched to console by Ctrl+Alt+F1
3- I typed

to enter root shell and then

in Ubuntu 8.04 and Ubuntu 9.04
and just

in Ubuntu 9.10
4- I made the driver binary executable by

5- I ran the file by just typing the file path and followed the instructions on the installer screen. Then rebooted my PC.

This also installed x-server settings. Although Ubuntu had already set my display resolution to a very appropriate one but if you want to change it, you can do that by finding NVIDIA X-Server in System Settings and follow the directions.

I tried before and faced the system cannot find driver low resolution only start up !

and then only low resolution available !!

worse than current state 

couldn't resolve without re-installation which I'm afraid to try it again

---

