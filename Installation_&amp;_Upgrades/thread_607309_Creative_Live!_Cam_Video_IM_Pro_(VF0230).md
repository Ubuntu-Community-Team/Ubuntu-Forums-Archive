---
title: "Creative Live! Cam Video IM Pro (VF0230)"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by judsona on 2007-11-08
Creative Live! Cam Video IM Pro (VF0230)

I am new to Linux   and need driver for Creative Live! Cam Video IM Pro (VF0230).

Help please :(

---

### Post by linuxwizard on 2007-11-09
From here 
[http://opensource.creative.com/webcam.html](http://opensource.creative.com/webcam.html)

Looks like you need this driver
[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

Also you could install EasyCam
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by ddoxey on 2007-11-14
I have a webcam with the same model number, but uses a different chipset than what is supported by Michael Xhaards GSPCA.

To be certain of the exact webcam that you have, with the webcam connected, execute lspci.

If the device ID is: 0x041e:0x4055
Then you need to wait for the M560x driver to be completed.
[https://sourceforge.net/projects/m560x-driver/](https://sourceforge.net/projects/m560x-driver/)

---

### Post by kendic on 2007-11-18
I am having the same problem. Any more information would be helpful. I tried WebCam link in Ubuntu, but despite adding the directory and running sudo apt-get update I couldn't bet EasyCam to run (via lauchcam2 or through System->Administration)

I also tried this the link LinuxWizard offered 'gspcav1-20070508.tar.gz' What do I do with this file? I am a newbe in Linux and I would appreciate a little more detail
Thanks,

---

### Post by ddoxey on 2007-12-01
Hello Newbies,

Bravo for staying the course despite the complications with things that you used to take for granted.

In Ubuntu the general practice for the typical user is to open up Synaptic to download and install software. This is easy and reliable ( see: [https://help.ubuntu.com/community/SynapticHowto]("https://help.ubuntu.com/community/SynapticHowto") ). Sometimes just browsing Synaptic is fun. 

To eliminate the guess work, here is what you do.
[LIST]
[*]Plug your Creative webcam into a USB port.
[*]Open up a terminal window and enter the command:
[/LIST]
**[INDENT]lsusb | grep Creative[/INDENT]**
Here's what it looks like on my machine:
> ddoxey@AM2xub:~/Desktop/gspcav1-20070508$ lsusb | grep Creative
Bus 001 Device 005: ID **041e:4055** Creative Technology, Ltd 
ddoxey@AM2xub:~/Desktop/gspcav1-20070508$ 

The string **041e:4055** is the unique identifier which made up of an identifier for the manufacturer (041e) and the model (4055) of my webcam.
So, the real question is, what is the chipset used in 0x041e:0x4055, and what driver supports it.

Creative Live Cam Video IM Pro (0x041e:0x4055) on **LiNUX-USB device overview**:
[http://www.qbik.ch/usb/devices/showdev.php?id=3970]("http://www.qbik.ch/usb/devices/showdev.php?id=3970")

This website claims there is no known driver. 
However, I happen to know that this webcam is based on the M560x chipset.
There is a driver in work on SourceForge:
[https://sourceforge.net/projects/m560x-driver/]("https://sourceforge.net/projects/m560x-driver/")

The short version of this post is this:
**If your webcam has the USB device id of 0x041e:0x4055, be patient.**

If your webcam is on this list:
0x041e:0x4013
0x041e:0x401d
0x041e:0x401f
0x041e:0x4017
0x041e:0x401e
0x041e:0x403a
0x041e:0x4036
0x041e:0x401c
0x041e:0x4034
0x041e:0x4035
0x041e:0x4012
0x041e:0x4051
0x041e:0x4053
Then you need to use Michael Xhaard's GSPCA driver which you install via the Synaptic package manager.

My advice to anyone who must have their webcam working pronto without headaches, get one that's supported by GSPCA. 
Here is the compatibility chart:
[http://mxhaard.free.fr/spca5xx.html]("http://mxhaard.free.fr/spca5xx.html")

Here is an article about Michael Xhaard which I recommend that Linux newbies read:
[http://www.theinquirer.net/en/inquirer/news/2007/04/30/one-man-writes-linux-drivers-for-235-usb-webcams]("http://www.theinquirer.net/en/inquirer/news/2007/04/30/one-man-writes-linux-drivers-for-235-usb-webcams")

A quick update here. 
This is a link to the Creative Labs open source driver list for their webcams:
[http://connect.creativelabs.com/opensource/Lists/Webcam%20Support/AllItems.aspx](http://connect.creativelabs.com/opensource/Lists/Webcam%20Support/AllItems.aspx)

An interesting observation is that there are multiple models with the same marketing name "Live! Video Cam Pro", each with a different chipset.


Happy computing!

---

### Post by galvheim on 2007-12-13
Well, I did as you said and after the lsub command it generated a code wich was found on the list you posted. After that I installed Michael Xhaard's GSPCA driver through the synaptic installer and everything was going smooth. 

But here's my problem. My cam was also working before this installation, but it was not working according to my wishes. Mainly because the picture shown is very dark, because the hardware default seems to be in daylight mode, which doesn't work at all in my indoor environment and lighting. 

So, how do I force it to use this new driver and will I get the option to set the same settings that I could in Windows which made it working fine indoor? 

If so, how do I do this? 

This is the Creative Live! cam IM VF0220 type. But as mentioned it was found in your list. 

Thanks for all help so far. If you search on VF0220 you will see my other post regarding this cam.

---

### Post by ddoxey on 2007-12-15
I think those types of adjustments are a function of the software which is using the webcam. When I was using Kopete, I just poked around in the preferences and settings menus to find adjustment controls. You can change color hues, contrast, brightness, etc.

---

### Post by galvheim on 2007-12-19
No-no,it's not that basic. This is something else, and others have reported the same problem. It is really dark, so when setting the controls mentioned by you, one have to slide them on full just to bareley see something and then it's very bad and unrealistic colours. 
This cam is working similarly in Windows by default, but in the cam-specific controls you can turn the cam from daylight to inddor settings and adjusting from PAL and NTSC and by this getting correct light into the CCD. So this is something the driver is missing: setting the cam from outdoor to indoor mode. If not it is not possible to use in a normal lit indoor environment. None of the programs I've tried that supports using a webcam have these setting since it's specific to this cam. 

Hope you understand that this is something else.

Any suggestions is highly appreciated.

---

### Post by ddoxey on 2007-12-20
My experience was that the open driver didn't provide the same degree of quality or configurability as the commercial driver on Windows. 

I could only speculate as to why, being that I have never written a camera driver myself. Perhaps you can find some answers if you approach the driver developers?

---

