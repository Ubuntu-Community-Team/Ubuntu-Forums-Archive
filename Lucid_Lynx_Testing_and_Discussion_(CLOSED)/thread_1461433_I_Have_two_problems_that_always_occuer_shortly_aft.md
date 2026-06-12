---
title: "I Have two problems that always occuer shortly after install"
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-04-24
Plymouth logo disappear and empathy disappears from nautilus-sent-to i think that the second problem is caused by the telepathy ppa i add from ubuntu-tweak but as for  Plymouth i have no idea i don't think it's caused by the binary ati fglrx driver i install from jockey but who knows.

any ideas?

maybe the information here might help:
[https://bugs.launchpad.net/bugs/569325]("https://bugs.launchpad.net/bugs/563878")

thanks in advance.

---

### Post by BrokeMahPC on 2010-04-24
Whats wrong with the radeon driver and the fglrx that installs from System->Admin->Hardware Drivers?
If you manually install from ATI don't you have to manually update as well?

Yes could be related to the bug you mention - I have experienced that with fglrx and eventually decided to ignore it till it was fixed. Looks like most who responded to the bug agree.

If you use the radeon driver with the "radeon.modeset=0" Grub option you should have a normal looking plymouth?

---

### Post by aviramof on 2010-04-24
i use the driver from System->Admin->Hardware Drivers but this problem also occure without this driver i don't understand why Plymouth logo disappears all the time.

---

### Post by nystire on 2010-04-24
MovieManiac explains it in a rather clear and concise manner here: [http://ubuntuforums.org/showpost.php?p=9167460&postcount=209](http://ubuntuforums.org/showpost.php?p=9167460&postcount=209)

---

### Post by BrokeMahPC on 2010-04-24
> If you use the radeon driver with the "radeon.modeset=0" Grub option you  should have a normal looking plymouth?So yes - switch over to the radeon driver that is the default install and don't use fglrx. Did you uninstall and purge fglrx? As shown below?

[http://ubuntuforums.org/showthread.php?p=7996934](http://ubuntuforums.org/showthread.php?p=7996934)
First, uninstall the old ATI drivers:
NOTE: Please, please, please be careful with the "rm -rf" command - if  you get this wrong, it could break your system!! Proceed with caution.
     Code:
     ```
cd /usr/share/ati/
sudo sh ./fglrx-uninstall.sh
cd ~
sudo rm -rf /etc/ati/
sudo apt-get remove -purge xorg-driver-fglrx fglrx-amdcccle
```

---

### Post by nystire on 2010-04-24
Aviramof, I don't know if the radeon driver will play too well with your video card. You may need to add the xorg-edgers PPA (see the link below) and then run 'apt-get update' and 'apt-get dist-upgrade' or however else you check for and install updates.

[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

---

### Post by aviramof on 2010-04-24
the driver from jockey is working for me but i have at least three problems with it

1.Plymouth  logo don't work 

2.movies and compiz don't go together i have to switch to metacity to see movies.

3.dual view don't work via catalyst he asks me to restart ubuntu and then it still doesn't work.

and i can not use fglrx because i don't have all the resolutions i need like 1920x1080.

as for xorg-edgers PPA i think i would wait ati to release there official 10.04 driver and the subsequents fglrx driver updates that would follow before i try that.

---

### Post by BrokeMahPC on 2010-04-24
The resolutions you get depend on your monitor/ graphics card not the driver - what card do you have - can't see it mentioned.
I have used 1920x1080 in both fglrx and radeon. It's the native resolution of my monitor and my graphics card supports it.

---

### Post by aviramof on 2010-04-24
HD3650 AGP 512MB DDR2 SHAPPIRE and i'm pretty sure i don't have this resolution without the fglrx driver maybe on my own computer screen but not for the two tv's 
i have here who use this resolutions and with fglrx i do have that option and also in windows with the windows ati driver.

---

### Post by BrokeMahPC on 2010-04-24
Ahhh so the monitor is ok - it's the TV's that are not displaying correctly.
Now getting the correct resolution to display on TV's can be problematic - I suggest you start a different thread about that.

---

### Post by cariboo on 2010-04-24
What resolution you get on the TV's really depends on what their native resolutions is. I have a Samsung 32" HD LCD TV, using the VGA input I get a resolution of 1360X768, I haven't tried HDMI yet as the local price for a 3 meter cable is over $150.00. but I assume using the HDMI input I should get 1920X1080, as that's the resolution I get with my HD PVR connected to an HDMI input.

---

### Post by aviramof on 2010-04-25
i have too tv's one Toshiba Lcd 32 who is half HD and can reach 1080i and the other is Samsung 37 Lcd which is Full HD and can reach 1080p but with xorg driver and not fglrx i can only use 1280x720 as the max resolution. 

with fglrx driver i can use 15 different resolution while with xorg i only have half of this number or even less then that.

(by the i was trying to create a picture of the resolutions using print screen and shutter and detected that it doesn't work in this sort of menus.)

---

### Post by cariboo on 2010-04-25
How are you connecting to the two tvs? VGA, HDMI, DVI, S-Video, Component video or Composite video, the way you connect can have an affect on the resolution. Almost any HD LCD tv will do 1080i, most HD television broadcast are 720p.

---

### Post by aviramof on 2010-04-25
My card has DVI connection so for the half HD tv i bought five meter DVI HDMI cable but for the Full HD i was smarter and bought 15 Meter HQ HDMI HDMI with HDMI 1.3 support cable with DVI HDMI 18 or 19 pins adapter.

with Fglrx driver i have all the resolutions with xorg not not for the tv's and not for my screen when i think about it there are no fifteen resolutions there that for sure.

---

