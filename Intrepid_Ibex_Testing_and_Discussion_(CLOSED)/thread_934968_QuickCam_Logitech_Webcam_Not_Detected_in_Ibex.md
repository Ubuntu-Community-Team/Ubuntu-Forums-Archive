---
title: "QuickCam Logitech Webcam Not Detected in Ibex"
date: 2008-10-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by wilsong on 2008-10-01
I plugged a trusty old webcam up, hoping to find it working but it doesn't. It doesn't even seem to be detected. I was reading about some bug, or something about HAL not detecting it, and i did download qc-source, and some other qc- programs.  I was reading that someone had found a way to get it working but they had to change the qc-driver.c, and when i tried to follow their directions there were compile warnings so it never really worked, and i think their directions were for an older version of the kernel, because it was written for i think alpha 4, or 5? Anyone please help! Thanks Oh USB btw.

---

### Post by wilsong on 2008-10-01
Anyone?

---

### Post by alphacrucis2 on 2008-10-01
> **wilsong said:**
> Anyone?

What appears in dmesg when you plug it in.

---

### Post by wilsong on 2008-10-01
I didnt know exactly what line you wanted me to view, lots of output, so i put it into a txt file, but i had to tar the txt file because the txt file was 42k and the max upload for txt is 19.5k sorry, just untar, and it should be in there as dmsg.txt i know its inconvenient.  

I made sure it was plugged in before i ran the command.  Anyone that wants to have a look at it, i didnt see anything that i thought looked like quickcam or logitech or anything. 

Any help thanks in advance.

---

### Post by alphacrucis2 on 2008-10-01
> **wilsong said:**
> I didnt know exactly what line you wanted me to view, lots of output, so i put it into a txt file, but i had to tar the txt file because the txt file was 42k and the max upload for txt is 19.5k sorry, just untar, and it should be in there as dmsg.txt i know its inconvenient.  

I made sure it was plugged in before i ran the command.  Anyone that wants to have a look at it, i didnt see anything that i thought looked like quickcam or logitech or anything. 

Any help thanks in advance.

Note the last thing that happened at the end:

[ 3298.772161] usb 4-1: new full speed USB device using uhci_hcd and address 2
[ 3298.972609] usb 4-1: configuration #1 chosen from 1 choice
[ 3299.055158] Linux **video capture interface**: v2.00
[ 3299.075154] gspca: main v2.2.0 registered
[ 3299.083037] gspca: probing 046d:0928
[ 3299.143458] gspca: probe ok
[ 3299.143500] usbcore: registered new interface driver **spca561**
[ 3299.143506] spca561: registered

spca561 is the driver being used to handle your camera. Do:

ls /dev/vid*

That should show the device name of your camera. Should be video0 if it is the only one.

---

### Post by wilsong on 2008-10-01
> **alphacrucis2 said:**
> Note the last thing that happened at the end:

[ 3298.772161] usb 4-1: new full speed USB device using uhci_hcd and address 2
[ 3298.972609] usb 4-1: configuration #1 chosen from 1 choice
[ 3299.055158] Linux **video capture interface**: v2.00
[ 3299.075154] gspca: main v2.2.0 registered
[ 3299.083037] gspca: probing 046d:0928
[ 3299.143458] gspca: probe ok
[ 3299.143500] usbcore: registered new interface driver **spca561**
[ 3299.143506] spca561: registered

spca561 is the driver being used to handle your camera. Do:

ls /dev/vid*

That should show the device name of your camera. Should be video0 if it is the only one.



Well the only problem with this, (i guess its good that its getting noticed) but when I open Cheese, or Camorama or any other program, they dont notice the webcam, Camorama will not open it starts to but says " error cannot capture image"  and cheese opens but it shows a big screen of Color Bars, and a little Picture in Picture window of static... any clues?

---

### Post by alphacrucis2 on 2008-10-01
> **wilsong said:**
> Well the only problem with this, (i guess its good that its getting noticed) but when I open Cheese, or Camorama or any other program, they dont notice the webcam, Camorama will not open it starts to but says " error cannot capture image"  and cheese opens but it shows a big screen of Color Bars, and a little Picture in Picture window of static... any clues?

Try VLC media player. That seems to handle damn near anything. From the VLC menu, select Open Capture Device and enter /dev/video0 in the Video device name field

---

### Post by wilsong on 2008-10-01
> **alphacrucis2 said:**
> Try VLC media player. That seems to handle damn near anything. From the VLC menu, select Open Capture Device and enter /dev/video0 in the Video device name field

I tried VLC, but it accepted that i tried, and there was a counter, (i guess the time since i plugged the device in) but there was not any video coming through 

when i downloaded qc-source there was some code for a driver for it, and i looked at this forum that was going into how to compile it for the alpha 4 but it had a different kernel and when i tried it didnt work well warnings for the code that i didnt fully understand.. 

do you care to read over [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196811](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196811) and see what you think?

---

### Post by alphacrucis2 on 2008-10-01
One simple way to test that you camera is actually streaming video is to type the following command:

cat /dev/video0

Your terminal window will go Nutzoid as it will try and display the camera video output as text. It is a simple way to prove that your camera is actually sending data through the USB port. Just CTRL C to kill it.

---

### Post by wilsong on 2008-10-01
> **alphacrucis2 said:**
> One simple way to test that you camera is actually streaming video is to type the following command:

cat /dev/video0

Your terminal window will go Nutzoid as it will try and display the camera video output as text. It is a simple way to prove that your camera is actually sending data through the USB port. Just CTRL C to kill it.

Wow, Very interesting, I did cat /dev/video0 and I did see all kinds of ODD symbols and characters, I held my finger over the eye, to keep it totally black, and the screen would show clear but still some fragments of characters, then pointing it around the room and at light the whole txt terminal filled up with all kinds of txt and symbol representations of what it saw (which was pretty cool looking) but i dont know why the programs cant use it or aren't working if that is :( ... any ideas ?

---

### Post by alphacrucis2 on 2008-10-01
> **wilsong said:**
> Wow, Very interesting, I did cat /dev/video0 and I did see all kinds of ODD symbols and characters, I held my finger over the eye, to keep it totally black, and the screen would show clear but still some fragments of characters, then pointing it around the room and at light the whole txt terminal filled up with all kinds of txt and symbol representations of what it saw (which was pretty cool looking) but i dont know why the programs cant use it or aren't working if that is :( ... any ideas ?


Well I would say that proves there is no physical problem just that the driver doesn't understand or can't handle the data coming from the camera. My own webcam seems to use the pwc driver which works ok with the current Ibex kernel and apps. I guess you will have to wait and see whether you get a solution via launchpad.

---

### Post by wilsong on 2008-10-01
> **alphacrucis2 said:**
> Well I would say that proves there is no physical problem just that the driver doesn't understand or can't handle the data coming from the camera. My own webcam seems to use the pwc driver which works ok with the current Ibex kernel and apps. I guess you will have to wait and see whether you get a solution via launchpad.

Well thanks for the help so far, If anyone else has seen the launch page site i stated ( [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196811](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196811) ) or has downloaded qc-source and patched qc-driver.c and compiled it for intrepid 8.10 please share ;)

---

### Post by wilsong on 2008-10-02
If anyone else has a quickcam and gets it working please message me.. or post here i just "subscribed now" so i hope we can work on this thanks

---

### Post by dbulante on 2008-10-03
I have the same problem here.  I couldn't get my webcam to work on skype and camorama.  It was working well under hardy.

---

### Post by ameed on 2008-10-03
Hello Guys, 

I have Logitech Camera and am using i did the cat /dev/video0 command and it turned on , but when i open Emesene (MSN) the webcam is not detected.

any idea?

---

### Post by wilsong on 2008-10-04
> **ameed said:**
> Hello Guys, 

I have Logitech Camera and am using i did the cat /dev/video0 command and it turned on , but when i open Emesene (MSN) the webcam is not detected.

any idea?

No to be honest with you i really have no clue, I know we need that QC-Driver, but i dont know if anyone has edited to work with Intrepid.. check out [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196811](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196811)

---

### Post by alphacrucis2 on 2008-10-04
> **wilsong said:**
> No to be honest with you i really have no clue, I know we need that QC-Driver, but i dont know if anyone has edited to work with Intrepid.. check out [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196811](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196811)

Wilsong, I know that is right for your camera but it isn't necessarily the case. It depends on which particular Logitech Camera. The Logitech one I have actually requires the Philips pwc raw driver. The others should check dmesg to see which driver was loaded (if any) when the Camera was plugged in. Here's what happens with mine:

[ 642.976088] usb 1-1: new full speed USB device using uhci_hcd and address 3
[ 643.815761] usb 1-1: configuration #1 chosen from 1 choice
[ 645.561522] Linux video capture interface: v2.00
[ 645.813453] pwc: Philips webcam module version 10.0.13 loaded.
[ 645.813482] pwc: Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
[ 645.813497] pwc: Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
[ 645.813511] pwc: the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
[ 645.817937] pwc: Logitech QuickCam Orbit/Sphere USB webcam detected.
[ 645.846991] pwc: Registered as /dev/video0.
[ 645.857947] usbcore: registered new interface driver Philips webcam
[ 647.662792] usbcore: registered new interface driver snd-usb-audio

---

### Post by wilsong on 2008-10-04
> **alphacrucis2 said:**
> Wilsong, I know that is right for your camera but it isn't necessarily the case. It depends on which particular Logitech Camera. The Logitech one I have actually requires the Philips pwc raw driver. The others should check dmesg to see which driver was loaded (if any) when the Camera was plugged in. Here's what happens with mine:


On this forums post on the first page, I posted my DMESG, which stated the Cam was loaded trying to use spca561 but never did work using Cheese or any other cam program but I could in the console see that the cam was "sending" information to the computer. 

Therefore i still have no cam :(

---

