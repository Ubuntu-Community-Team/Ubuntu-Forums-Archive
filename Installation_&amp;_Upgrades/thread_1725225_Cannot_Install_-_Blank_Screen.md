---
title: "Cannot Install - Blank Screen"
date: 2011-04-09
forum: Installation &amp; Upgrades
---

### Post by arry487 on 2011-04-09
Hello,

I am trying to install Ubuntu 64 bit on the following hardware

AMD Phenom X4 925
Asrock a780gm-le 780g + SB710 chipset
4gb ddr2
500gb hard drive

I have tried 10.10 and 11.04 using the usb and cd, both fail.

When I try to install or boot either 10.10 or 11.04 from the cd I get a keyboard icon at the bottom of the screen and then the screen goes blank, at this point there is a lot of disk acivity for about 10 mins but then it stops.

When trying to install or boot from the usb the white text with hardware info etc will flash though quickly then the screen will go blank with no signal.  

I have tried various things such as disabling devices achi hpet etc which have not helped, not sure what to try next.

Thanks

---

### Post by Dutch70 on 2011-04-09
Try choosing nomodeset...
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by arry487 on 2011-04-09
Try choosing nomodeset...

How? The menu is different to the one shown in the thread you linked to.  None of the F keys do anything, there is an advanced options but there is nothing in there to choose, am I missing something?

---

### Post by Jelee8804 on 2011-04-11
Hey,

I have the same problem. I created a LiveUSB of ubuntu 10.10 using a file from pendrivelinux on windows. I changed my bios settings, and get the system to boot off of the liveUSB. First, theres a lot of white text on the screen, then the Ubuntu menu comes up saying Run Ubuntu, install to hard disk, advanced (empty), and help. I want to run it from the USB, then the screen goes blank, and the monitor says that there is no input detected.

It's strange because I successfully ran ubuntu from the same liveusb on a school computer, and I think I successfully got it to run on the system in question too. When I get home I'll try the nomodeset, see if that works, and report back here.

---

### Post by Jelee8804 on 2011-04-12
For me this did not work. When I'm presented with the GRUB menu, I don't have an option to push F6. My GRUB looks different from the GRUB shown in the link from Dutch. I tried pushing TAB on the 'Try without installing', and it gave me a command line at the bottom. I noticed that it ended with quietsplash -- at the end, so i added nomodeset before that. The screen still went black and notified me that there is no input signal.

I reinstalled the ISO on my usb drive using UNETBOOTIN, and it gave me yet another GRUB menu, but still no F6 option. I tried TAB again and added nomodeset before quietsplash, and this gave me a problem. Not only did my screen go blank, when I turned off my computer and turned it back on, it doesn't show anything from BIOS anymore. The screen stays blank until Windows starts up.

Does anyone know how I can first get my BIOS info to show, then how I can install Ubuntu?

---

### Post by Dutch70 on 2011-04-12
> **arry487 said:**
> Try choosing nomodeset...

How? The menu is different to the one shown in the thread you linked to.  None of the F keys do anything, there is an advanced options but there is nothing in there to choose, am I missing something?

I was hoping someone with more knowledge on this would respond, since they haven't...

The menu should be the same, what did you download & what and how are you trying to install it? You'll need to give as much detailed info as possible.

---

### Post by Dutch70 on 2011-04-12
> **Jelee8804 said:**
> Does anyone know how I can first get my BIOS info to show, then how I can install Ubuntu?

Very few people are going to see your problem inside of someone else's thread. 
Please start your own thread with a good title that gives some insight to your problem.

---

### Post by Jelee8804 on 2011-04-13
Dutch70: Sorry for adding additional questions to someone else's thread. 

Arry487: I feel like I made a little bit of progress since I last posted on your thread. Before, I too had a problem with the blank screen (no input detected on my monitor), and I couldn't find the F6 option to add nomodeset. I found out that the problem was my monitor (or graphics card). I'm using an LCD tv as a desktop monitor, and it's connected via HDMI cable. When I connected my old small monitor with an analog cable, the liveUSB ran perfectly and I was able to install Ubuntu 10.10. Didn't need to mess around with nomodeset. This might work for you too, if you're connected with an HDMI cable.

---My new problem---
I got ubuntu to install, but running it normally is a different problem for me. I definitely don't want to keep my little monitor hooked to this PC, so I installed the Proprietary ATI drivers under System>Administration>Additional Drivers. It downloaded and installed my drivers correctly, but after reboot, the system takes me straight to the Terminal TTY1 instead of the GUI. The terminal works for both HDMI and analog monitor connections, but I can't start the GUI. I tried startx but it fails and sends a report about xorg. If I uninstall the drivers, the GUI works on my old monitor, but my TV goes back to the blank screen problem. If I keep the drivers installed, but boot with recovery mode> failsafe in low graphics, the GUI works for both HDMI and analog.
--------------------------

Anyways, in theory, you should be able to connect an old monitor to install ubuntu, download and install your appropriate graphics drivers, then be on your dandy way with your normal monitor. I hope that works for you; if not, you might need to do that nomodeset stuff =S

---edit---
I also tried downloading my graphic drivers manually from ATI. Selected my graphics card (Radeon HD 3200), downloaded the .RUN file and installed it via terminal. Same problem with the auto-installer.

---

### Post by Dutch70 on 2011-04-13
No reason to apologize to me, it's not my thread. I was just advising you on how to get your support questions answered.

Also, you added what may be useful information in your post. I'm sure the OP will appreciate that.

---

