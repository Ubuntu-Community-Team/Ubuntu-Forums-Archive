---
title: "WPA Enterprise giving me the run-around &amp; 43xx"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by dracule on 2008-10-18
First let me tell you the wireless situation where i am at.

It is WPA enterprise, you need a user name and password, and it filters out mac addresses not associated with your user name.



so Today I upgraded to Ibex. My built in wireless is not working, so i got my USB wireless adapter to try and get internet to my laptop to update all the packages and get the nvidia drivers and what not. 

so i spoofed the mac address w/ "ifconfig wlan1 hw ether xx:xx:xx..." (ive done this loads of times for other computers with the same wifi module)

and then selected my ssid from the drop down menu. It pulls up a dialog saying it needs security information.

I have NO idea what to do.  before in 8.04 all i did was select WPA enterprise and then put in my username and password. but now the only option is "WPA & WPA2 Enterprise". Then it gives me options for all types of security (PEAP, TLS, TLS Tunnel, LEAP). i dont know what to choose. i never had to do this for 8.04 

i tried all 4 of them, but none work.
in windows you have to supply a CA certificate to get on wireless, but i never had to in ubuntu for the last 3 years. why should i have to start now? it prompts me saying that a CA certificate maybe necassary, but i just ignore it. The only CA i have is a *.cer, but it doest have that file extension available. I even renamed the file extension  to what was available (#.der) and it didnt work. 

--------------------------------

As to why i had to use the adapter. On 8.04 i had to use B43 driver. Now in 8.10 it says that the 'wl' driver is installed, however no ssid's appear in nmapplet. i then do the "connect to other network" and that doesnt work either. In "network tools" under system, it just says "unrecognized wireless device" but in nmapplet it says "HP wireless Broadcom 4311" (it only displays the name when i have another wireless adapter plugged in).

---

### Post by quazi on 2008-10-18
I would try checking with the wireless provider to see what security type is most appropriate.  I know in my case, I use PEAP (no clue what version it should be, both seem to work) and MSCHAPv2 inner authentication.

There's a .cer file for Windows on my network as well, but it doesn't seem to be necessary.

I have noticed that in Intrepid, my connection seems to drop a lot more (it never did in Hardy) and I have to jump through more hoops to get it set up properly.

---

### Post by Ayuthia on 2008-10-18
I have not played too much with Intrepid, but you could always go back to the b43 driver.  You will need to disable the wl driver (Broadcom STA) and enable the b43 driver.

I have seen that the wl module does not always play too well with WPA yet.  I think that it does work with some versions of WPA, but I cannot recall which.

---

### Post by dracule on 2008-10-19
eh, damn...

B43 driver was WAY too slow. i havent used linux in 2 months because b43 is around 10-20x slower than in windows. i was hoping the new kernel/'wl' would help it and i could get back to using linux.

---

### Post by Cuppa-Chino on 2008-10-19
@ dracule, have you tried using ndiswrapper & windows driver -- seems to give same performance as windows for me

---

### Post by Cuppa-Chino on 2008-10-19
sorry double post

---

### Post by sdowney717 on 2008-10-19
ndiswrapper-gtk is a gui that makes this painless. At least for me.

---

### Post by dracule on 2008-10-19
Ok, here is an update.




First off, i thought i would go ahead and give ndiswrapper a try. 
so i download the 8.4 ndiswrapper .deb, intalled it, then then installed my firmware. It showed "hardware present".
So I then "rmmod wl" and then "modprobe ndiswrapper" and rebooted. 
Still no access points were showing up in the drop down menu of nm-applet. 

So I rmmod wl and modprobe ndiswrapper one more time for good measure, but still nothing. i look in network tools, and only 'eth0 and lo' were showing.


so i thought, hmmm, wtf why isnt this working?! so i installed 'b43-cutter' (eww... but i guess slow is better than nothing) so i extracted my firmware to the appropriate directories, rmmod ndiswrapper and modprobe b43.  and rebooted. still no ssid's in the drop down nm-applet. I then modrpobe b43 once more, and look in network tools, only eth0 and lo are listed. 

so i think that is odd. and so i rmmod b43 and modprobe wl. 

So basically it seems as though nothing is working :/

---

### Post by quazi on 2008-10-19
Have you tried using the B43 driver that comes with intrepid?  Under System -> Administration -> Hardware Drivers is Broadcom B43 Wireless driver listed?  Supposedly it is an improvement from the one included in Hardy.

---

### Post by dracule on 2008-10-20
> **quazi said:**
> Have you tried using the B43 driver that comes with intrepid?  Under System -> Administration -> Hardware Drivers is Broadcom B43 Wireless driver listed?  Supposedly it is an improvement from the one included in Hardy.

for somereason it is not listed in restricted drivers (but it was listed when i was on the live CD and peeked in restricted drivers). 

I had to 'sudo apt-get install b43-fwcutter' from the Intrepid CD. however i used the same wl_alpsa.o (or whatever the file name is) from my 8.04 install since i dont have internert in linux, that was all i had available.

---

### Post by dracule on 2008-10-20
OK

so i just reinstalled. 

Now B43 appears under "Hardware Drivers"

However, i have the CD in, and when i try to install it, it just instantly goes to the "restart to use" icon. so i restart, check under "hardware drivers" and it has the red circle next to it. 


When i was in the live cd mode, i decided to see if i could install it, and so i said "activate" and it downlaoded something off of the CD but said i needed to restart, but i couldnt restart because i was on the Live CD. 

I added the CD as a repository for software sources also btw before i said "activate"

Is the B43 driver on the CD? under synaptic it says that "b43-fwcutter" is installed, however like i said, under hardware drivers it has a red cicle next to it.

---

### Post by Ayuthia on 2008-10-20
> **dracule said:**
> OK

so i just reinstalled. 

Now B43 appears under "Hardware Drivers"

However, i have the CD in, and when i try to install it, it just instantly goes to the "restart to use" icon. so i restart, check under "hardware drivers" and it has the red circle next to it. 


When i was in the live cd mode, i decided to see if i could install it, and so i said "activate" and it downlaoded something off of the CD but said i needed to restart, but i couldnt restart because i was on the Live CD. 

I added the CD as a repository for software sources also btw before i said "activate"

Is the B43 driver on the CD? under synaptic it says that "b43-fwcutter" is installed, however like i said, under hardware drivers it has a red cicle next to it.

The driver is on the CD, but the firmware portion needed to make it work is not included in the CD because the firmware is proprietary.  If you want to install it on the Live CD, you should not really have to restart the computer.  If you do, you will lose the firmware that it just downloaded and cut to make it work.  What you could try after you install b43-fwcutter is do the following:
```
sudo modprobe -r b43 ssb wl
sudo modprobe b43
sudo ifconfig wlan0 up
```
I am guessing that your wireless card is labeled as wlan0.  However, if you don't do the ifconfig command, I think that network manager will pick it up after a few seconds and hopefully wireless sites will be visible.  If you have a 4311 rev 02 card, you might have to run the updates just to get it up to 2.6.24-21 so that the b43 module will work.  

Some people have had speed issues with the b43 driver in Ubuntu.  It looks like the 2.6.27 kernel (one used in Intrepid) does work better.  I am using the b43 module in Arch with a 2.6.27 kernel and the speeds I have seen with it in comparison to the wl and ndiswrapper module have all been the same.  I was able to copy a 700Mb file over my network in about 3 minutes.

If you want to try the wl driver, you will also need to update the Hardy CD so that it will be at 2.6.24-21 and then enable the Broadcom STA driver from System->Administration->Hardware Drivers and disable the b43.  You will then need to do the following:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo ifconfig eth1 up
```
Once again, I am not for sure if yours is going to show up as wlan0 or eth1.

---

### Post by dracule on 2008-10-20
> **Ayuthia said:**
> The driver is on the CD, but the firmware portion needed to make it work is not included in the CD because the firmware is proprietary.  If you want to install it on the Live CD, you should not really have to restart the computer.  If you do, you will lose the firmware that it just downloaded and cut to make it work.  What you could try after you install b43-fwcutter is do the following:
```
sudo modprobe -r b43 ssb wl
sudo modprobe b43
sudo ifconfig wlan0 up
```
I am guessing that your wireless card is labeled as wlan0.  However, if you don't do the ifconfig command, I think that network manager will pick it up after a few seconds and hopefully wireless sites will be visible.  If you have a 4311 rev 02 card, you might have to run the updates just to get it up to 2.6.24-21 so that the b43 module will work.  

Some people have had speed issues with the b43 driver in Ubuntu.  It looks like the 2.6.27 kernel (one used in Intrepid) does work better.  I am using the b43 module in Arch with a 2.6.27 kernel and the speeds I have seen with it in comparison to the wl and ndiswrapper module have all been the same.  I was able to copy a 700Mb file over my network in about 3 minutes.

If you want to try the wl driver, you will also need to update the Hardy CD so that it will be at 2.6.24-21 and then enable the Broadcom STA driver from System->Administration->Hardware Drivers and disable the b43.  You will then need to do the following:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo ifconfig eth1 up
```
Once again, I am not for sure if yours is going to show up as wlan0 or eth1.
I guess i will just wait until I go home this weekend... :|

---

### Post by dracule on 2008-10-25
Just an update:

I finally got home where i had ethernet, i then updated all available packages on my system. 

Then i went into "Hardware Drivers" and saw that there was no "wl" listed anymore, and Nvidia v76 driver wasnted listed. Then i scrolled down, And saw "Broadcom STA", so i installed it then downloaded something from the internet and now i am happy to say that i am finally posting in Linux again :)

---

### Post by dracule on 2008-10-26
This should be my last post, 

but let me just say that the new Broadcom driver is WONDERFUL it is a complete turnaround from b43 on hardy. I just cant believe how fast it is in linux now! just as fast as windows. I think i can now delete my windows partition, and move to a VM for my window's tasks.

---

