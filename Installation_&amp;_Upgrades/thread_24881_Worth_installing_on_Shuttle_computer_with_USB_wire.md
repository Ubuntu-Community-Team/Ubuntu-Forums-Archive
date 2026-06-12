---
title: "Worth installing on Shuttle computer with USB wireless and ATI card?"
date: 2005-04-08
forum: Installation &amp; Upgrades
---

### Post by JHolmes763 on 2005-04-08
I've got a USB wireless setup that built into my Shuttle computer that works quite well under windows. Does anyone know if I will run into big issues trying to run Ubuntu on this computer? I'd like to try it out and have something I can play around in to learn a couple things. 

Also, I've got an ATI graphics card, 9600XT, I think. I've heard drivers for ATI cards were hard to come by, non-existent, buggy? 

Can anyone give me any advice and/or warnings on whether I should even pursue installing Ubuntu and how much headache I'm looking at to get things working? Or should I just try the Live CD?

Thanks. 

---John Holmes...

---

### Post by kiddo on 2005-04-08
For the wlan, I don't know, please provide some details (about the hardware and such), and you may look at linuxcompatible.org too.

For the ATI: yes, it's going to be tough I think, feasible, but tough ^^ that is if you want 3D accel.

And.. yes, try the Live CD before installing, that will give you a better idea of what it looks/behave like. And if you got spare bandwidth.. leave a torrent open to counter-slashdot!:-D

---

### Post by JHolmes763 on 2005-04-08
The wireless setup is a PN15 by Shuttle. Specs can be found [here](http://www.shuttle.com/share/product_data/spec/PN15_DM.pdf) (pdf).  It doesn't say what chipset is being used, though, and I could never get a concrete answer from Shuttle regarding it (if that's applicable). linuxcompatible didn't have any entries for it, though.

I can do without the 3D acceleration for a while. I don't think I'll be playing any 3D games. I'll be doing more programming, installing and testing aps, etc than gaming. :)

Thanks for the info. I'll test out the live CD first. 

---John Holmes...

---

### Post by JHolmes763 on 2005-04-10
I tried the Live CD and it did not recognize the PN15. Looking through the device manager, though (or whatever it's called), it did now an "unrecognized USB device", though. I assume that's the PN15 since everything else I had was recognized and listed. 

Any idea where I should go from here? Is this a driver issues from shuttle or just something I'll need to enable/add/fix in my configuration? Thanks for any help. 

---John Holmes...

---

### Post by az on 2005-04-10
You should try ndiswrapper for your wlan device.  It uses the windows drivers to make the card work.

[http://ndiswrapper.sourceforge.net/wiki/index.php?Installation](http://ndiswrapper.sourceforge.net/wiki/index.php?Installation)

You shoudl have the ndiswrapper module present and you shouldinstall ndiswrapper-utils.

---

### Post by wildtiger23 on 2005-05-03
I found a beta linux driver for your PN15G.... [http://global.shuttle.com/Download/Download_File.asp?Item=PN15g](global.shuttle.com/Download/Download_File.asp?Item=PN15g) Can you try it? I will by one of this for my shuttle. Good luck.

---

### Post by vitko on 2005-07-14
Did someone succeeded with PN15G? I'm planning to use it with my just to be ordered SN95G5.

According both the driver code and Windows .inf file it is ZD1211 USB 802.11b+g Wireless LAN card. (ZD1211), kernel module is called zd1211,  device vendor id 0x07B8, product id 6001.

---

### Post by brousch on 2005-08-02
I put up a wiki with ubuntu-specific instructions for the zd1211
[https://wiki.ubuntu.com/zd1211wifi](https://wiki.ubuntu.com/zd1211wifi)

---

### Post by Martyn on 2005-09-16
If you have the PN15 it uses a slightly different chipset to the PN15G...

PN15 = AirVast (WM-168gi) 

Possible support via the prism54 project

[http://prism54.org](http://prism54.org)

PN15G = Zydas (ZD1211)

[http://sourceforge.net/projects/zd1211](http://sourceforge.net/projects/zd1211)

I hope this helps...

Cheers,

Martyn

---

### Post by Fabruccio on 2005-09-18
Martyn is right, the Shuttle PN15 is built on a AirVast WM168G.
I managed to set it up thanks to this [procedure](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation), using ndiswrapper, as suggested by azz, version 1.3rc1 and [this driver for WinXP](http://sourceforge.net/projects/ndiswrapper/).
My Shutle SN41G2 is now wave-connected to the world! Good luck JHolmes.
-- Edit --
My connection did not last too much: I stay connected for 7h00, not more. Then, I have to reboot and reinstall ndiswrapper and the driver and to load the module. Still working on.

---

### Post by marzer on 2005-10-23
Hi,

As a new user of Ubuntu Linux (which is my favorite distro now), here's my experience in getting the PN15g (zd1211 chipset) to work under Ubuntu on my Shuttle SN41G2:

- Ubuntu 5.10 has the device driver installed for the zd1211.
- Activate the device using "sudo ifconfig wlan0 up".
- Open "Networking" (System>Administration>Networking), you will now see an entry for "Wireless"
- Under properties, enable the connection and set network settings (key, IP, etc.)
- Accept the changes (activation takes a long time to complete)
- After activation is complete it appears to be ready for action, however, it will not set an IP address until you REBOOT.  WLAN0 should come up fine with an IP address.
 
Mark

---

