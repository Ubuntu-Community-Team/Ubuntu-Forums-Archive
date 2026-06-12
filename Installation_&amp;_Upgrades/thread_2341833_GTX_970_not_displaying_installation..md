---
title: "GTX 970 not displaying installation."
date: 2016-11-01
forum: Installation &amp; Upgrades
---

### Post by Blix775 on 2016-11-01
Hi! I was trying to install Ubuntu Mate 16.10 and later Lubuntu 16.10 into my machine and noticed they both did the same thing. After cchoosing to install (or try without installing)the screen would just go black. I tried the same USB on my other machine which has an AM1 integrated graphics driver and it worked nicely there. I think the problem is the Noveau driver is not able to configure my gpu at boot up. Can anyone tell me how to graphically install the OS and keep it configured to work after installation? Thanks in advanced.

---

### Post by oldfred on 2016-11-01
Usually you need nomodeset for installer & first boot or until you install nVidia driver from Ubuntu's repository.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 


 NVIDIA 970  with 14.04 - Bucky Ball
[https://ubuntuforums.org/showthread.php?t=2336142&p=13540433#post13540433](https://ubuntuforums.org/showthread.php?t=2336142&p=13540433#post13540433) 
      
 Install with Asrock Z97 & nVidia 970
[http://ubuntuforums.org/showthread.php?t=2257406](http://ubuntuforums.org/showthread.php?t=2257406)
[http://ubuntuforums.org/showthread.php?t=2259210](http://ubuntuforums.org/showthread.php?t=2259210) 
            Gigabyte Z170 Nvidia 970 16.04   UEFI Settings required                         
[http://askubuntu.com/questions/792012/nvidia-geforce-gtx970-problem-ubuntu-16-04](http://askubuntu.com/questions/792012/nvidia-geforce-gtx970-problem-ubuntu-16-04)
[https://ubuntuforums.org/showthread.php?t=2341704](https://ubuntuforums.org/showthread.php?t=2341704)

---

### Post by Bucky Ball on 2016-11-01
Just to add that I'm currently using the GTX 970 with 16.04 LTS and, though I have no recollection of using it myself, the 'nomodeset' option is known to have worked for others with this card. Once the OS is installed, just install the appropriate driver for the GTX 970 from 'Additional Drivers'. Good luck. :)

---

### Post by Blix775 on 2016-11-02
> **oldfred said:**
> Usually you need nomodeset for installer & first boot or until you install nVidia driver from Ubuntu's repository.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 


 NVIDIA 970  with 14.04 - Bucky Ball
[https://ubuntuforums.org/showthread.php?t=2336142&p=13540433#post13540433](https://ubuntuforums.org/showthread.php?t=2336142&p=13540433#post13540433) 
      
 Install with Asrock Z97 & nVidia 970
[http://ubuntuforums.org/showthread.php?t=2257406](http://ubuntuforums.org/showthread.php?t=2257406)
[http://ubuntuforums.org/showthread.php?t=2259210](http://ubuntuforums.org/showthread.php?t=2259210) 
            Gigabyte Z170 Nvidia 970 16.04   UEFI Settings required                         
[http://askubuntu.com/questions/792012/nvidia-geforce-gtx970-problem-ubuntu-16-04](http://askubuntu.com/questions/792012/nvidia-geforce-gtx970-problem-ubuntu-16-04)
[https://ubuntuforums.org/showthread.php?t=2341704](https://ubuntuforums.org/showthread.php?t=2341704)
I got the installation boot up process started and displaying on my screen. I edited the /etc/default/grub file with pluma, saved it and got to the last part. When I tried the sudo update-grub command it said the following message. 
```
/usr/sbin/grub-probe: error: failed to get canonical path of 'aufs'.
```
I thought I was done. The grub page did not address that problem and the other links seem irrelevant it. Thanks a whole lot for the help, btw.

---

### Post by oldfred on 2016-11-02
Are you trying to edit live installer's copy of grub.cfg by running sudo update-grub. You cannot do that. 
Only after install can you then update grub settings.

---

### Post by Blix775 on 2016-11-02
I was following the instructions on the pages. But will it keep my settings once it is installed?

---

### Post by oldfred on 2016-11-02
You have to boot once into new install with nomodeset added to grub replacing quiet splash.
You then should be able to go into System Settings, Software & Updates, and drivers tab.

If graphics does not load, you can try recovery mode and use command line to install nVidia driver.

---

### Post by Blix775 on 2016-11-03
I'm going to try it now. Thanks!

---

### Post by Blix775 on 2016-11-03
It is not showing the grub menu at bootup. I just installed Lubuntu and it won't let me use the menu to select nomodeset.

---

### Post by Bucky Ball on 2016-11-03
Is it booting directly to a black screen, no grub? Try hitting shift after boot and see if that brings it up (could be escape, but pretty sure it's shift).

---

### Post by oldfred on 2016-11-03
It is shift if a BIOS based install and Escape if an UEFI install.
Shift you seem to have to hold, and escape just press, but perhaps more than once to catch the correct point between UEFI/BIOS and grub loading.

Also if new computer with UEFI, it will have a fast boot setting. (not same as Windows fast start up.)
Best to have that off, as when on there is no time from UEFI to grub to starting to boot.
Fast boot assumes no changes to configuration and UEFI jumps immediately to booting. Normal boot UEFI/BIOS checks all hardware configuration & writes that to drive for operating system to know what is where. May need normal boot to get into UEFI to change settings to normal boot.
Usually systems will use one normal boot from a cold boot or total power start up, but then not from warm or reboot.

---

### Post by Bucky Ball on 2016-11-03
> **oldfred said:**
> It is shift if a BIOS based install and Escape if an UEFI install.

Thanks, oldfred. I never remember which and perhaps that's why. It's both!

---

### Post by Blix775 on 2016-11-03
> **Bucky Ball said:**
> Is it booting directly to a black screen, no grub? Try hitting shift after boot and see if that brings it up (could be escape, but pretty sure it's shift).
OK. It is escape and if you land by mistake on the grub terminal thing you can just type exit and you go back to the boot options. After that, I just selected nomodeset again and then proceeded to install the nvidia drivers which took care of everything. No need to update grub after that. Thanks a whole lot for all of the help. How do I change the status to solved?

---

### Post by Bucky Ball on 2016-11-03
Great news and well fiddled! :)

You can use 'Thread Tools' at the top right of the page to mark as 'solved' or see the last link in my signature at the bottom of this post. Thanks and good luck. :)

(This will not close the thread to further posting.)

PS: You should also find the 'Nvidia X Server Settings' GUI available in the apps menu for further tweaking. Happy with my card which I use for HD video rendering and editing. ASUS Strix Nvidia GTX 970.

---

### Post by blarney77 on 2017-10-23
I am also using the same ASUS card you have, but I cannot get 16.04 to actually USE one of the two identical Samsung 28" 4K monitors.  I DID have to use the "nomodeset" to get it going and after several updates to the Nvidia drivers ONE monitor (HDMI) looks great using the 2K resolution.  but the other (DP) is black.  Nothing will get it to light up.  Both work just fine in Windows and under Mint 18.2.  But Ubuntu really doesn't seem to like my video setup.   Maybe it's not liking the Display Port??  These monitors have ONLY HDMI and DP, no VGA or DVI.

---

### Post by QIII on 2017-10-23
Old thread.  RIP.

Closed.

---

