---
title: "Ubuntu 11.04 Installation Problems"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by thesource01 on 2011-05-01
Hi

i have tried to install Ubuntu 11.04 but everytime i try i get a black screen when the system starts up. i have tried to install via cd and the upgrade option.

I am currently using Ubuntu 10.04 and this has no problems.

I have also tried the esc key when i insert the disc and this brings the option to install but after this i get a black screen again.

Please can someone help me?

Thanks

---

### Post by kansasnoob on 2011-05-01
This sounds like a graphics issue. Please post the output of:

```
lspci | grep VGA
```

That will show the specific make & model of the graphics chip. Maybe you'll find notes about it here:

[https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes#Graphics%20and%20display](https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes#Graphics%20and%20display)

---

### Post by mistamidget on 2011-05-01
do you get to the splash screen which gives the options to use live, install mem test etc?
If so press f6 and select the option to disable switching modes on start (second from the bottom) and see if you can then proceed.

---

### Post by thesource01 on 2011-05-01
Hi

Thanks for your help

Here is the output

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)

---

### Post by jdgkunst on 2011-05-05
The solution provided by unknown47 on [http://ubuntuforums.org/showthread.php?t=1743301](http://ubuntuforums.org/showthread.php?t=1743301) worked for me, to be able to edit the files I could get into the system by choosing in grub a previous version, otherwise you should be able to get there using a live cd.

---

### Post by thesource01 on 2011-05-07
Ok thanks i will try that and report back

---

### Post by sevenflo on 2011-05-07
After I clean install 11.04, I get stuck at a black screen, specifically the Verifying DMI... thing....

is this where you're getting stuck? Basically right after POST?

Also, I was going to start a thread of my own but I saw yours. Maybe we can find this solution together.

I just want to note that I was running 10.04 as well. Then I did a FRESH install of 11.04. It worked perfectly. Then I formatted and fresh installed again. This time, the system stalled at a purple screen. So I tried installing once again and found that at the end of the installation, I'd get a message saying that the bootloader could not be installed. This happened on another 2 fresh install retries. One checked "download updates from the web" and one without. 

I suspect it was my video drivers not loading. 

Motherboard I'm using is an EVGA FTW3
Nvidia GT430 by EVGA
OCZ Revodrive 120GB <---- Still brand new but arrived with 896 bad sectors. I'm sending it for RMA on monday. I feel like the SSD drive may be the culprit but it DID install properly before.

LASTLY, all installs were off the same USB drive. I tested for errors and found none.

SO, any similarities with you? Or does anyone see anything I/we are missing?
I will try the posted suggestions tomorrow, need some sleep.
Thanks

---

### Post by thesource01 on 2011-05-07
well i have installed 11.04 as instructed but when it restarts it happens again the black screen. what i did is when you see the purple screen just increase brightness and it works but surely i should have to do this all the time?

How to i enter the grub and change the settings so that this will not happen again?

thanks

---

### Post by dino99 on 2011-05-07
hold "shift" key down at bios end process to see the grub menu, maybe remove "splash" to see if that help

then of course look at errors logged into .xsession-errors & /var/log (system admin logviewer); its easier if you you log as "classic" not "unity"

---

### Post by tadaskr on 2011-05-07
For me it worse. I can't boot from cd at all. I tried with "acpi_osi = Linux" but that doesn't work. Blank screen after I press start Kubuntu. I'm using tohsiba satallite a300 laptop. any ideas?

---

### Post by thesource01 on 2011-05-09
What do you mean you can't boot from cd? Do you have the installation coming up at all?

---

### Post by tadaskr on 2011-05-09
No, Kubuntu showing install meniu, but when I press install kubuntu there comes black screen and my laptop freezes. When I try ubuntu same happening, but there freezes after loaading thing in bottom of the screen. Now i'm using 10.10 it works great. 10.04 working too

---

### Post by thesource01 on 2011-05-10
Hi

Does anyone have a fix on this?

---

