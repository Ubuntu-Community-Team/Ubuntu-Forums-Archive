---
title: "Problem running/installing 10.10"
date: 2011-01-27
forum: Installation &amp; Upgrades
---

### Post by *Kat* on 2011-01-27
So, I just downloaded and put on my USB to install or even just run it is fine. 

I changed the settings in the BIOS to run from USB and I get to the page which asks whether I want to install or just run ubuntu. 

I chose to install it, but it gets as far as...

"ut3
20541793 (something about powerbutton here)
2.542001 ACPI [fan0] (off)
2.542179 ACPI [fan1] (off)
"

and it doesn't move from there? I need to install this for uni work (not used ubuntu since Knoppix 3 years ago)

Any help/advice?
Thanks!!

---

### Post by Rubi1200 on 2011-01-27
Hi and welcome to the forums :-)

How did you put the image on the USB?

Please post the specifications for the computer.

Are you also running other operating systems?

Thanks.

---

### Post by *Kat* on 2011-01-27
Hi, thank you :)

I used the Universal USB thing on the [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download) page...?

I am running Windows 7, but have another partition ready to install ubuntu on which I'm wanting to do...

I have a Samsung R580...

Processor 							Intel® Core™ i3-330M Processor
          - 2.13 GHz
          - 3 MB L3 cache 						 					 									 						 							Operating System 							[Genuine Windows® 7 Home Premium]("http://www.currys.co.uk/gbuk/samsung-r580-refurbished-laptop-09149771-pdt.html?srcid=198&gclid=CMj_w8742qYCFYIlfAodjjIR5w#recommendation-seven") 						 					 									 						 							RAM 							- 4 GB 						 					 									 						 							Graphics card 							nVIDIA GeForce GT 310M 						 					 									 						 							Screen type 							Widescreen LCD/TFT 						 					 									 						 							Screen resolution 							- WXGA
- 1366 x 768 pixels 						 					 									 						 							Screen size 							15.6" 						 					 									 						 							Screen features 							LED backlighting 						 					 									 						 							Hard drive 							500GB 						 					 									 						 							Optical disk drive 							DVD±RW 						 					 									 						 							Memory card reader 							SD/MMC 						 					 									 						 							USB 							4 x USB 2.0 						 					 									 						 							FireWire 							No 						 					 									 						 							Modem/Ethernet 							RJ-45 Ethernet port 						 					 									 						 							Wi-Fi 							802.11b,g,n WLAN 						 					 									 						 							Bluetooth 							Bluetooth 2.1 + EDR 						 					 									 						 							Video interface 							1 x HDMI
1 x VGA 						 					 									 						 							TV output 							1 x HDMI (digital audio/video output)
1 x VGA (analogue video output) 						 					 									 						 							Sound 							3 W Stereo Speakers (1.5 W x 2)
HD Audio 						 					 									 						 							Webcam 							1.3 megapixel webcam 						 					 									 						 							Battery 							- 6-cell lithium-ion battery 						 					 									 						 							Size 							379.8 x 255.5 x 36.7 mm 						 					 									 						 							Weight 							2.6 kg 						 					 							 			  											  	  	  	 					 		 					 	

[LIST]
[*][]("http://www.currys.co.uk/gbuk/dell-inspiron-n5010-refurbished-laptop-07586175-pdt.html") 								 										 										 										 										 										 								 							 													
[/LIST]

---

### Post by Rubi1200 on 2011-01-27
Choose the option to try not install.

At the live desktop, go to Applications > Accessories > Terminal and post the output of the following commands in a new post:

```
sudo parted -l

sudo fdisk -lu
```

Copy/paste for best results.

---

### Post by *Kat* on 2011-01-27
nopies :( still the same thing hmmm

---

### Post by Rubi1200 on 2011-01-27
> ***Kat* said:**
> nopies :( still the same thing hmmm
Meaning...you cannot start the LiveUSB session?

You can try starting the session like this:

As you start the LiveUSB you should see the Ubuntu logo and the select a language screen and the option to try Ubuntu. After this hit F6 and at the lower right-hand you will see a menu with options.

I suggest you try both nomodeset and acpi=off

Let's see if that helps get things started.

---

### Post by *Kat* on 2011-01-27
Ok thanks, ill try that and report back!! :)

---

### Post by *Kat* on 2011-01-27
Ugh, total schoolgirl error, just did it again and realised that in the top menu I just selected Ubuntu and not the specific netbook one *sigh* :)

Ah well, sorted now :) Thank you! x

---

### Post by Rubi1200 on 2011-01-27
You are more than welcome :-)

Glad you got it sorted out.

---

