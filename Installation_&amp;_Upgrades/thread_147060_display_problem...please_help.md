---
title: "display problem...please help"
date: 2006-03-19
forum: Installation &amp; Upgrades
---

### Post by ashik ahamed on 2006-03-19
I am new to linux and i have installed ubuntu and i couldn't change my screen resolution.i have only one choice 640*480.This is my details about my moniter and graphics hardware
Monitor Type : Plug and Play Monitor
    >> General Information
      Manufacturer : Samsung
      Product ID : SAM0025
      Model : SyncMaster
      Serial Number : HHAW650914
      Manufacture : Week 27 of 2003
      Video Input Type : Analogic
      Max. Horiz./Vert. Size : 28 cm / 21 cm
      Monitor Size : 14 inchs (estimated)
      Gamma Factor : 1.8
      DPMS Active-Off : Yes
      DPMS Suspend : No
      DPMS Standby : No
      EDID version : 1.3     
    >> Features
      Maximum Resolution : 800 x 600 @ 85 Hz
      Horizontal frame rate : 30 - 55 kHz
      Vertical frame rate : 50 - 120 Hz
      Bandwidth : 70 MHz
    >> Video Modes Supported
      Mode : 640 x 480 @ 60 Hz
      Mode : 640 x 480 @ 75 Hz
      Mode : 800 x 600 @ 60 Hz
    >> Video Modes Standard
      Mode : 640 x 480 @ 60 Hz
      Mode : 640 x 480 @ 85 Hz
      Mode : 800 x 600 @ 85 Hz
      Mode : 1024 x 768 @ 60 Hz
      Mode : 1152 x 864 @ 60 Hz

  > Video Card : Intel(R) 82845G Graphics Controller
    >> General Information
      Model : 82845G/GL/GV/GE/PE Integrated Graphics Device
      Manufacturer : Intel Corporation
      Bus Type : PCI
      Manufacturer : Intel Corporation
      Total Memory : 1 MB
      Texture Memory : 49 MB
      Processor : Intel(R) 82845G/GL Chip
      Converter : Internal
      Refresh Rate (min/max) : 60/85 Hz
    >> Video Bios Information
      Date : 03/03/20
      Version : Hardware Version 0.0

---

### Post by aarbear26 on 2006-05-13
you need to run:

sudo dpkg-reconfigure xserver-xorg

Most of the blanks you can breeze through becuase you probably won't understand them, but when it gets to the moniter settings, put and asterik next to the modes that you state above.  
Then you'll get another screen about moniter stuff, answer no to the auto detect and then use advanced when the Simple, medium, advanced prompt comes up.   
Input the refresh rates that you posted there.  

then type

sudo /etc/init.d/gdm restart

(you may have to login in text mode, if it doesn't start the GUI environment, just type gdm at the prompt again)

If it doesn't give you an option of refresh rates when you go through the GUI,  after you do that, then run the command again and this time set the refresh rates to the specific ones you want by the number seperated by a comma method.

hope that helps

---

