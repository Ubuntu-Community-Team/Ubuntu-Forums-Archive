---
title: "instalation under samsung r70"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by marceli_ossi on 2007-07-06
hi everybody,
please help , I don't know wha should I do.... I get a lot of problems

I bougth notebook samsung r70, during installation I read somewhere that I shoul use Alternate CD cause graphic drivers....so all was in text mode....I installed it ! but..............

the plan was:
1.alternate cd
2. restart and graphic driver instalation from usb (in /media/ I have no information about usb so I burn cd but there was a problem when I open /media/cdrom0/ or /media/cdrom/ it was also empty)
3. recompilation kernel via internet (wlan work also wrong - I mean don't work - I use ARCOR . During instalation ubuntu wanteed to check dhcp - didn't found (maybe the problem with wlan driver))
4.restart and shall be ok (but it isn not so nice / doesn't work at all)

please help me , I'm not so familiar with ubuntu

Best regards
Marceli

---

### Post by marceli_ossi on 2007-07-07
Is anybody know something more than me ???

---

### Post by Pumalite on 2007-07-07
You have to explain better what you want to accomplish so people can help you better.
What's install from USB, why not from CD-ROM
What's recompile kernel, what's wrong with regular kernel?

etc

etc

Whats your comp specs? Whats your drive size? What's your graphics card? How much memory?
Processor?

---

### Post by marceli_ossi on 2007-07-07
For first thx for answer

for 2nd :
I don't want to instal from usb 
I installed it from CDROM but ubuntu has a problem with G8600 (new graphic card)
so after installation I had to install special driver for G8600, so I tried to do it from usb ... but in /media/ is only cdrom.  I burn driver on CD and tried to open itunder ubuntu console (because X doesn't work) .... unfortunately  ubuntu see empty cdrom ??????
I know now what is the next step if you instal this driver you have to have internet connection to recompile kernel !!! 
but there is also the problem with wlan....

you can see some information also here [http://forum.ubuntuusers.de/topic/100113/15/](http://forum.ubuntuusers.de/topic/100113/15/) because I tried to do everything as they described but I got a lot of problem

for 3rd:
comp spec.
proc. T7300 Core duo 2
memory 2gb(ddr2 667MHz/1G*2)
hdd 200GB (4.2 KR SATA)
communic : Intel 802.11ag(AMT/BT)
graphic  nvidia GF8600GS(256MB H)

is it enough

---

### Post by Pumalite on 2007-07-07
You have a nice rig. You should have no problems. First make sure you have a 'working' Live CD. Check iso. Do Md5sum. Then check CD for integrity before install. Are you dual booting? Vista?. How did you partition?. If dual booting with Vista; partition from within Vista. If all that checks OK and you end up without a graphical interface: try this: sudo dpkg-reconfigure xserver-xorg Once you are in you can download a driver for your card from the NVIDIA site.

---

### Post by marceli_ossi on 2007-07-08
yeah thx but there is another problem also , during installation in text mode ubuntu waned search dhcp .... doesn't work ....
so I have no internet... this is also very strange, I can use only wlan via INTEL card but I got problems....

---

### Post by Pumalite on 2007-07-08
Install first and you can configure your connection later from within the OS.

---

### Post by marceli_ossi on 2007-07-08
ok, can you support me because I'm not an eagle with ubuntu :D

I'm checking now the memory I checked already cd if everything is ok(no problems)
So yesterday I installed vista once again (I divide my hdd on two 100gb partition. One for vista one for ubuntu).

It seems that memory checking can take some minutes :D


in xorg.conf 

shell I used this param.
Section "Device"
        Identifier      "NVIDIA Corporation NV34 [GeForce FX 5200]"
        BusID           "PCI:1:0:0"
        Driver          "vesa"
EndSection

---

### Post by Pumalite on 2007-07-08
It looks like you did the right thing according to xorg. Are you in now? Do you have a specific question? Are you stuck somewhere? Did you partition from WITHIN Vista?

---

### Post by marceli_ossi on 2007-07-08
no I'm installing it now and I use the partition divider under ubuntu installer :)

In this installation I omit network configuration I just skipped forward , is it good ?

I have one more question how shall I mount cdrom under console>
I wnat to do it because I want to dwonload the driver for graphic card , but last time I tried to do it I couldn't open any cdrom and also I didn't see any usb. I think that everything can be under /media/ but there was only cdrom. So I put cd and tried to open everytime was empty ....

What time is in your country ? because I have now 00:25 AM :D
last edit :I installed it and I try to do this with xorg ....

I give you feedback what is going soon :)

---

### Post by marceli_ossi on 2007-07-08
this what I get on ubuntu start ....
I don't know what does it mean _?_
Starting up ...
[0.200285] PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:01:00.0
Loading plese wait....

so now I'm going to change xorg

---

### Post by Pumalite on 2007-07-08
Do a mem test:

[http://www.memtest86.com/](http://www.memtest86.com/)

---

### Post by marceli_ossi on 2007-07-08
about memtest I did it from ubuntu-cd , result without any problems....

with x I did it 
after changing I wrote and started with vesa dirver but i doesn't mean that I installed driver properly because  I  change only the driver ....
sudo /etc/init.d/gdm restart

can you support me with wlan - I'm green with that


Shall I install now the right dirver for nvidia and change once again xorg.conf __?__ if it is correct then ca you write the steps how to do it  _?_

when I tried to install from cd I got an error : Dependency is not satisfiable: xserver-xorg-dev

but I got the driver from Nvidia site ?!?!?!

---

### Post by Pumalite on 2007-07-08
If you are in now, don't worry about the driver; do it later. Stick to your plan for wlan first. Unfortunaly  I cannot help you there. Somebody who knows will jump in. Be patient. I can give you this in the meantime to get you started:

[http://ubuntuforums.org/search.php?searchid=23399115](http://ubuntuforums.org/search.php?searchid=23399115)

Posting the output of code: lspci from your console will help others to help you.

---

### Post by marceli_ossi on 2007-07-08
```

00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation Mobile SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0425 (rev a1)
03:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
05:09.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
05:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)
05:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843
05:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 09)
05:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 04)



```

I'm going to sleep now it is 2:00 AM by me ,so .... thx a lot and see you tomorrow

---

### Post by Pumalite on 2007-07-09
This:

[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

and this:

[https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)

Might help you.

---

### Post by marceli_ossi on 2007-07-10
Ok. I read all you sent me .... and I configured the wlan in interfaces 

I had put sudo -s and as root I have written ipdown -a then ipup -a 
and I got ```
wlan0: Error while getting interface flags: no such device
```

maybe ubuntu doesn't recognize my wlan card......
I was there [http://intellinuxwireless.org/index.php?n=downloads&f=releases](http://intellinuxwireless.org/index.php?n=downloads&f=releases)

but as I told I'm not so familiar with ubuntu and how shall I install it now...?

---

### Post by Pumalite on 2007-07-10
Why don't you make a new thread in sub-forum>Networking? They will be able to help you better than I can.

---

