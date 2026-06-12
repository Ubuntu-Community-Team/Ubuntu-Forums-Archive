---
title: "epson 3170 not working ubuntu 18.04"
date: 2020-05-04
forum: Installation &amp; Upgrades
---

### Post by mikeprosceo-frontiernet on 2020-05-04
I have been researching and trying for a year to get my epson 3170 scanner to work with any scanner program in ubuntu 18.04. I can't seem to find the answer.  I have tried:
  	 	 	 	   sane-find-scanner
 found USB scanner (vendor=0x04b8 [EPSON], product=0x0116 [EPSON Scanner]) at libusb:001:004
   	 	 	 	   Xsane
 no devices available
 
 
 lsusb
 Bus 001 Device 004: ID 04b8:0116 Seiko Epson Corp. GT-9400UF [Perfection 3170]
 
 
 sudo gedit /etc/sane.d/dll.conf uncommented epson and epson2
 
 
 sudo gedit /etc/sane.d/epson.conf added  line usb 0x04b8  0x0116
 
 
 scanimage -L
 device `epson:libusb:001:004' is a Epson  flatbed scanner

  	 	 	 	   
scanimage --list-devices

 device `epson:libusb:001:004' is a Epson  flatbed scanner
 
 
 Simple Scan – epson
 unable to start scanner

  	 	 	 	   
scanimage -T
Output format is not set, using pnm as a default.
scanimage: rounded value of br-x from -32768 to -32768
scanimage: rounded value of br-y from -32768 to -32768
scanimage: sane_start: Invalid argument

scanimage -V
scanimage (sane-backends) 1.0.28git; backend version 1.0.28

cat /etc/sane.d/dll.conf
epson
epson2  neither commented out
 These are some of the things I've tried with no luck.  Skanlite sees the scanner but gives an Invalid argument error.  I've tried image scan, simple scan, Vuescan, and Xsane as well.  None work.  I need help, please.

---

### Post by brian_p on 2020-05-04
Please give the outputs of ```
avahi-browse -rt _ipp._tcp
``` ```
avahi-browse -rt _uscan._tcp
```

when the device is connected to the network.

---

### Post by plucky on 2020-05-05
Have you installed sane-utils? ```
sudo apt install sane-utils
```

---

### Post by mikeprosceo-frontiernet on 2020-05-06
I don't connect the scanner to the network, just through USB.

---

### Post by mikeprosceo-frontiernet on 2020-05-06
Yes sane-utils installed

---

### Post by brian_p on 2020-05-06
> **mikeprosceo-frontiernet said:**
> I don't connect the scanner to the network, just through USB.

To clarify: your intention is to remain with a USB connection?

---

### Post by mikeprosceo-frontiernet on 2020-05-07
yes I would like to stay with a usb connection, if that is possible. Otherwise I could try a network connection if you think that would work.

---

### Post by brian_p on 2020-05-07
> **mikeprosceo-frontiernet said:**
> yes I would like to stay with a usb connection, if that is possible. Otherwise I could try a network connection if you think that would work.

The network technique I would recommend depends on what the the two *avahi-browse* commands give.

You give a lot of useful information in your first post, especially the *scanimage -L* result. I am not keen on debugging a USB connection. What I would point out is that, when you say

> cat /etc/sane.d/dll.conf
epson
epson2 neither commented out

then SANE will use the first driver found (epson). I think this line needs to be commented to see how epson2 does.

---

### Post by mikeprosceo-frontiernet on 2020-05-07
I have tried it with epson commented out and then with epson 2 commented out.  Neither way worked.

---

### Post by brian_p on 2020-05-07
If you are not going to provide suficient information to investigate a network connection, my final contribution is [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX).

---

### Post by mikeprosceo-frontiernet on 2020-05-08
What other documentation do you need from me to help me with trying to use network for the scanner?  I have already downloaded all the epson drivers available including the network drivers.  I am not sure where to go from here.

---

### Post by brian_p on 2020-05-08
> **mikeprosceo-frontiernet said:**
> What other documentation do you need from me to help me with trying to use network for the scanner?  I have already downloaded all the epson drivers available including the network drivers.  I am not sure where to go from here.

I will repeat the earlier request:

Please give the outputs of

```
avahi-browse -rt _ipp._tcp
```

```
avahi-browse -rt _uscan._tcp
```

when the device is connected to the network.

---

### Post by mikeprosceo-frontiernet on 2020-05-09
avahi-browse -rt _ipp._tcp
+ enp2s0 IPv4 Brother HL-2270DW series                      Internet Printer     local
+ enp2s0 IPv4 Brother HL-5370DW series                      Internet Printer     local
= enp2s0 IPv4 Brother HL-5370DW series                      Internet Printer     local
   hostname = [BRN001BA9439F67.local]
   address = [169.254.153.250]
   port = [631]
   txt = ["TBCP=F" "Transparent=T" "Binary=T" "PaperCustom=T" "Duplex=T" "Copies=T" "Color=F" "usb_MDL=HL-5370DW series" "usb_MFG=Brother" "priority=50" "adminurl=http://BRN001BA9439F67.local./" "product=(Brother HL-5370DW series)" "ty=Brother HL-5370DW series" "rp=duerqxesz5090" "pdl=application/vnd.hp-PCL" "qtotal=1" "txtvers=1"]
= enp2s0 IPv4 Brother HL-2270DW series                      Internet Printer     local
   hostname = [BRN001BA9A25EB6.local]
   address = [192.168.254.13]
   port = [631]
   txt = ["TBCP=F" "Transparent=T" "Binary=T" "PaperCustom=T" "Duplex=T" "Copies=T" "Color=F" "usb_MDL=HL-2270DW series" "usb_MFG=Brother" "priority=50" "adminurl=http://BRN001BA9A25EB6.local./" "product=(Brother HL-2270DW series)" "ty=Brother HL-2270DW series" "rp=duerqxesz5090" "pdl=application/vnd.hp-PCL" "qtotal=1" "txtvers=1"]

I got no reply to the avahi-browse -rt _uscan._tcp

---

### Post by mikeprosceo-frontiernet on 2020-05-09
Hi Brian,  
   I am giving up on this.  I do appreciate your time and help.  It is not solved but I have wasted enough time with this.  Thank you

---

### Post by marweis34549 on 2020-05-15
I am sad to read this. 
I am here, because the scan function of the Epson  ET-2600 isn't supported by Ubuntu 16.04 anymore. It always worked  together -- but it stopped working, and xsane 0.999 says -----  ET-2600_series:
Error during save: Could not create secure file (maybe a link does exist): /home/scann0082.jpg
What does this mean? I'm not native English...
Installed the latest drivers. Epson support won't help.
Thank you.

---

### Post by mikeprosceo-frontiernet on 2020-06-10
I posted this once and finally gave up because nothing seemed to work.  I would like to get this scanner to work on  usb. I have been researching and trying for a year to get my epson 3170  scanner to work with any scanner program in ubuntu 18.04. I can't seem  to find the answer.  I have tried:
  	 	 	 	   sane-find-scanner
 found USB scanner (vendor=0x04b8 [EPSON], product=0x0116 [EPSON Scanner]) at libusb:001:004
   	 	 	 	   Xsane
 no devices available
 
 
 lsusb
 Bus 001 Device 004: ID 04b8:0116 Seiko Epson Corp. GT-9400UF [Perfection 3170]
 
 
 sudo gedit /etc/sane.d/dll.conf uncommented epson and epson2
 
 
 sudo gedit /etc/sane.d/epson.conf added  line usb 0x04b8  0x0116
 
 
 scanimage -L
 device `epson:libusb:001:004' is a Epson  flatbed scanner

  	 	 	 	   
scanimage --list-devices

 device `epson:libusb:001:004' is a Epson  flatbed scanner
 
 
 Simple Scan – epson
 unable to start scanner

  	 	 	 	   
scanimage -T
Output format is not set, using pnm as a default.
scanimage: rounded value of br-x from -32768 to -32768
scanimage: rounded value of br-y from -32768 to -32768
scanimage: sane_start: Invalid argument

scanimage -V
scanimage (sane-backends) 1.0.28git; backend version 1.0.28

cat /etc/sane.d/dll.conf
epson
epson2 commented out
 Withe epson not commented out skanlite sees the scanner but gives a Failed to Start invalid arguement error.
 These are some of the things I've tried with no luck. .  I've tried image scan,  simple scan, Vuescan, and Xsane as well.  None work. I do not want to try to get this to work via network.  I need help,  please.

---

### Post by QIII on 2020-06-10
Threads merged.

Rather that giving up and marking a thread "Solved" (which is very unhelpful to others who are looking for a solution) and later starting a duplicate thread, please bump your thread if you do not receive a response in about 12 hours.  Simply add a new post with the word "Bump".  This will bring your thread back to the top where it might better be noticed.

---

### Post by mikeprosceo-frontiernet on 2020-06-10
I'm sorry, I am not real familiar with the forum protocols.  Do I put the word "Bump" in the title or at the beginning of the new post?  I will wait 12 hours to do this.  If I get responses do I just leave it?

---

### Post by kurt18947 on 2020-06-10
Mike, I would download VueScan. I don't think you've tried VueScan have you? The trial version will put watermarks on the scanned image but at least you'll know that VieScan recognizes your scanner. If it works there are two purchase options.

[https://www.hamrick.com/](https://www.hamrick.com/)

---

### Post by QIII on 2020-06-10
Just reply to your own thread with a new post with the single word "Bump".

---

### Post by mikeprosceo-frontiernet on 2020-06-12
Bump

---

### Post by mikeprosceo-frontiernet on 2020-06-12
Vue scan does not see the scanner.  This is so frustrating

---

### Post by kurt18947 on 2020-06-12
> **mikeprosceo-frontiernet said:**
> Vue scan does not see the scanner.  This is so frustrating

I don't blame you for being frustrated. Have you tried a different USB cable? Beyond that, I hope someone has a thought.

---

### Post by mikeprosceo-frontiernet on 2020-06-14
The usb cable works when I plug it into  my wife's mac.  The computers are next to each other so I just unplug it from one and put it into the other.

---

