---
title: "Install failure on Dell OptiPlex - I get the desktop but it's totally unresponsive"
date: 2021-03-19
forum: Installation &amp; Upgrades
---

### Post by Sour Mash on 2021-03-19
I'm trying to install 20.04 LTS as a dual boot on an Optiplex which is currently on a clean Windows install, so I'm trying to create a dual boot machine.

I've tried a few times with new download and USB stick image - it will boot OK into the try before you buy desktop but as it starts up the picture is incomplete, if I move the mouse around more of the image appears, enough to click "Try Ubuntu" - then it all seems to install OK and shows a desktop but it's unresponsive, can't select or click anything, including shut down or accessing the terminal.

I've run Speccy on the Windows build (typing this from the machine now) and I get the following info on the General tab

CPU
	Intel Pentium G3440T @ 2.80GHz	50 °C
	Haswell 22nm Technology
RAM
	8.00GB Dual-Channel DDR3 @ 665MHz (9-9-9-24)
Motherboard
	Dell Inc. 0VRWRC (SOCKET 0)
Graphics
	T23d-10 (1920x1200@59Hz)
	Intel HD Graphics (Dell)
Storage
	119GB SAMSUNG SSD PM871 2.5 7mm 128GB (SATA (SSD))

As it feels like a graphics issue (I am guessing) here is the graphics info
Graphics
		Monitor
			Name	T23d-10 on Intel HD Graphics
			Current Resolution	1920x1200 pixels
			Work Resolution	1920x1160 pixels
			State	Enabled, Primary
			Monitor Width	1920
			Monitor Height	1200
			Monitor BPP	32 bits per pixel
			Monitor Frequency	59 Hz
			Device	\\.\DISPLAY1\Monitor0
		Intel HD Graphics
			Manufacturer	Intel
			Model	HD Graphics
			Device ID	8086-0402
			Revision	7
			Subvendor	Dell (1028)
			Current Performance Level	Level 0
			Current GPU Clock	598 MHz
			Driver version	20.19.15.5063
				Count of performance levels : 1
						Level 1 - "Perf Level 0"
							GPU Clock	600 MHz

Any suggestions? Am I doing something wrong or attempting the impossible? It feels like what I'm trying is mundane and I should be able to do it without drama.

Thanks

J

---

### Post by Sour Mash on 2021-03-19
Quick update, I'm posting this on the target machine having tried and failed to get Ubuntu or Kubuntu running from a USB stick. I am now running on Lubuntu! So far it's gone like it should, unremarkable. 
I'm going to see if I can get  it to install now! Can't say I like it but it's just a phase to go through!

---

### Post by Autodave on 2021-03-19
What version of Windows are you running?  What version of 'buntu are you trying to install? Fast boot disabled in BIOS?

---

### Post by Sour Mash on 2021-03-19
Thanks for the response Auyodave.

It's Windows 10, has all updates installed

See original post, I was trying to install 20.04 LTS 

I've got Lubuntu installed and running now. Bit strange but it won't connect using the wired connection, never had this issue but it won't connect through the network cable (as Windows does on the same machine). Plugged in a WiFi dongle and it's happy - weird

---

