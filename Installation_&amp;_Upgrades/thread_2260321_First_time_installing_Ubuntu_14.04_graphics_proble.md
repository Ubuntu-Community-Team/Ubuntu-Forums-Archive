---
title: "First time installing Ubuntu 14.04 graphics problem, not a blank screen"
date: 2015-01-10
forum: Installation &amp; Upgrades
---

### Post by konrad5 on 2015-01-10
I am in the process of installing Ubuntu for the first time on a partitioned hard drive with Windows 7 already installed. I've already created a live USB to install the OS and verified that it works on a different machine. In addition, I have already partitioned my hard drive and have plenty of space for both systems.

Here is my problem:

When booting through USB, the first image is coherent and includes an outline of a usb at the bottom center of the screen. The next image includes the word ubuntu displayed at the center with loading dots underneath it, however, there is already a graphics problem that appears in the form of a pattern of colored columns in the background. Once ubuntu has finished loading, I'm suppose to be able to choose a language and whether or not to run ubuntu installed or from the live usb. Instead though, the entire screen is covered in randomly colored pixels.

Clearly I have a graphics problem and I want to make sure I fix it the right way. I'm thinking that I need to install drivers specifically for ubuntu. The drivers currently installed for the AMD Radeon HD 6670 work well for the Windows 7 OS. 

If I were to install new graphics drivers while running Windows, would my display stop working when I run Windows? Is there a way to have my graphics card be able to work for both operating systems?

---

### Post by mooreted on 2015-01-10
Everything about your Linux install will be completely separate from the Windows install. Natively, Linux drivers and software don't run in Windows and vise versa. 

You will have to install the AMD video driver once you are booted into Linux. You may have to add "nomodeset" to the boot options to get to a working desktop so that you can install the graphics drivers once Linux is installed. There are instructions here in the forums for doing that if needed.

---

### Post by MAFoElffen on 2015-01-11
Did you do a md5checksum on the ISO to check to see that it was a good download?

What did you create your LiveUSB with?

That may alter how to start the advanced install mode... But usually, when you see the aubergine (purplish) panel with the icon at the bottom... Press escape to get to the advanced install menu (prefaced by that language selection). Sounds like you at least read something to prepare yourself...

At that menu, press F6, select nomodeset. Press escape. Below the menu and above the F-keys at the bottom, you will see a text bootline that appeared, ending with nomodeset. edit that to delete nomodeset, and replace it with "radeon.modeset=0"...

Before I tell you anything esle, try that and lets see how that goes for you...

---

### Post by konrad5 on 2015-01-11
I got it! Thanks!

For other noobs like myself who need help finding the nomodeset option, here is what I did:

1. After passing though the BIOS, I had to press shift when the Ubuntu boot image appeared. This led me to a display of options and asked for a language to work with.
2. In order to find "nomodeset", I pressed F6 for more options. 
3. After selecting the "nomodeset" option and hitting enter, I pressed escape to return to the previous menu.
4. At that point, I selected to proceed in persistence mode to make sure it worked.
5. Once I verified that the Ubuntu home screen displayed correctly, I restarted the computer and repeated the same process but chose the install option instead of persistence.
6. After following through the installation guide, I was left with a working desktop all but in a temporary mode before installing additional drivers for Ubuntu. 

If this doesn't help, you'll have to continue searching for a solution :/ 

Good luck!

Edit: I didn't see the other reply with similar instructions. I downloaded the 64 bit iso and used Lili USB Creator to build the LiveUSB. I tested it on another computer and it worked. That's how I knew I had to do something with my computer. Thanks for the help!

---

### Post by mörgæs on 2015-01-11
Thanks for posting. Please mark the thread 'solved'.

---

