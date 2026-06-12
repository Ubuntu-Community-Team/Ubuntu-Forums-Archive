---
title: "Toshiba Satelite l300-110, install Ubuntu"
date: 2015-02-11
forum: Installation &amp; Upgrades
---

### Post by jhay2 on 2015-02-11
Hi anyone here has a same laptop as mine ? Toshiba Satelite l300-110 
dual core 2.0GHZ 
160GB
2GB ram 

im trying to install ubuntu to this kind of laptop but it doesnt install 

whether i select Install ubuntu / Try Ubuntu /Check disk for defects  

it goes black screen and hangs .. 

anyone here successfully installed ubuntu on this kind of laptop ? 
how did you install it ?

Thanks

---

### Post by mörgæs on 2015-02-11
You don't say which graphics processor it has, which is important to know. 

Anyway, without knowing it I suggest that you try the **nomodeset** boot option.

---

### Post by jhay2 on 2015-02-11
thank you for the quick reply . according to the website about the specs of my laptop 

my graphic card detail is as follow
[COLOR=#666666][FONT=arial]type : Intel® GMA X3100 [/FONT][/COLOR]
[COLOR=#666666][FONT=arial]memory amount : up to 358 MB total available graphics memory with 2 GB system memory [/FONT][/COLOR]
[COLOR=#666666][FONT=arial]memory type : shared 


ok i will try to set nomodeset and give you a feedback thank you[/FONT][/COLOR]

---

### Post by jhay2 on 2015-02-12
still not working ..

---

### Post by mörgæs on 2015-02-12
It seems like the hardware information was found by googling. Don't trust that, the only real information is what you can dig out of this particular computer.

Are you able to install a [minimal]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") / text only Buntu?

---

### Post by oldfred on 2015-02-12
Are you installing Ubuntu?
My Toshiba is slightly older with only 1.5GB of RAM. I had to install fallback/gnome-panel as Unity was way too slow. 
Others would suggest Lubuntu or Xubuntu as they also are lighter weight gui.

I have different Intel Video and have not needed any settings. But with Intel nomodeset does not work, but other similar settings may.

  Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1

   Some other Intel boot options Each line is one that may work
acpi_osi=Linux  acpi_backlight=vendor

---

### Post by jhay2 on 2015-02-14
i already fix this by removing my extra ram which is 512mb ram and leaving my 2gb ram , and this work and already installed ubuntu . but i have a problem 

toshiba l300-100 and other old toshiba model have a known factory defects which is when the ac adapter is plugged in , the system or computer autoreboot without warning  or sometimes hang . this problem fix on windows os by booting safemode then device manager and disabling the processor drivers then reboot . 


i want to do this on ubuntu , i want to disable both processor drivers like what i did on windows os .  but i dont know . , does anyone here know how to do this .. so that i can just plugged my ad adapter when im on ubuntu os  ?

---

### Post by oldfred on 2015-02-14
Linux uses totally different drivers, so are you having the same issue with Linux?

---

### Post by jhay2 on 2015-02-14
yes im having the same issue , and the only fix for this is to disable the processor drivers like what i have done on windows, right now im on windows because booting on ubuntu makes my system autoshutdown in 5 or 10 mins , before or after i login

---

### Post by ubfan1 on 2015-02-14
Sounds an awful lot like a thermal shutdown, maybe caused by dust?  Have you ever cleaned the dust out of the machine?

---

### Post by jhay2 on 2015-02-14
yes i already done with that , but i read the google and this is common issue of toshiba laptop manufactured 2008-2009 , its capacitor problem the nikon-tokin , and very expensive to buy and go to technician to repair it, so the only things that i can use for now is to disable the processor driver

---

### Post by jhay2 on 2015-02-16
Gotcha. i finally got it work and completely disable my cpu core , by adding maxcpus=0 on the grub boot . actually only cpu0 messed my system not cpu1 so i only need to disable cpu0 which is imposible on ubuntu :(  because on the folder /sys/devices/system/cpu/cpu0 theres has no "online" file only on cpu1 folder has that file , so the only thing that i can make is to disable the 2 cores instead .. but if there is anyone here know how to disable cpu0 please tell me , thank you . :)

---

