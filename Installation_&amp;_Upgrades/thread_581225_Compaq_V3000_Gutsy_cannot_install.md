---
title: "Compaq V3000 Gutsy cannot install"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by erniequintero on 2007-10-19
i have a compaq presario V3000(V3218la), i download the Gutsy 7.10 RC on monday it install fine on my desktop, and boots right away from a dell laptop at work. but when i try to boot from that cd on the ubuntu splash with the progress bar moving it locksup randomly. i also try with the options for noapic irqpoll noirqdebug but still the same thing. also download the alternate cd and locks up when is trying to load the modules from the cd to start the setup right away you select the keyboard layout. then i have a feisty disc that i recieve from shipit page and thats boot fine and install right away, then i try to perform the upgrade but that gives me errors. any body can help me out thanks.

System specs:
---------------------------------------------------------------------------------------------------------
Microprocessor   	2.0 GHz AMD Turion™ 64 Mobile Technology MK-36
Memory 	512MB 667MHz DDR2
Video Graphics 	NVIDIA GeForce Go 6150
Hard Drive 	120GB 5400RPM
Multimedia Drive 	SuperMulti 8X DVD±R/RW with Double Layer Support
Display 	14.1” WXGA High-Definition HP BrightView Widescreen Display (1280 x 800)
Fax/Modem 	High speed 56K modem
Network Card 	Integrated 10/100BASE-T Ethernet LAN (RJ-45 connector) 
Wireless Connectivity 	802.11b/g WLAN
 1 ExpressCard/54 Slot (also supports ExpressCard/34)

---

### Post by Nergar on 2007-10-20
Im having the same problem and help would be nice.

I haven't tried alternate cds but tried a lot of boot options without any luck

And feisty works without problems!

---

### Post by logeshnkl2004 on 2007-10-20
I am also facing the above same problem on my HP Compaq Presario V3228au Lappy.


Really i am very upset with this :( :( :(

---

### Post by melkor486 on 2007-10-20
Same problem here on a V3418 laptop trying to boot kubuntu gutsy

---

### Post by josedaniel86 on 2007-10-21
Hi, I got succes installing Gutsy on a Compaq 3418la. 
At first, I have the same issue, but I just download 64bit version and it works.
But now I have a issue: the broadcom wireless card doesn't works... And upon a time, the system goes extreme slowly.
If somebody knows something, it would be nice...
Sorry, bad english. ;)

---

### Post by linfeng on 2007-10-24
Same problem here on a V3239 laptop try to 32bit ubuntu
but install 64bit ubuntu,it's work well.

---

### Post by rozojc on 2007-10-25
I think it actually is a kernel issue (which would be BAD)... I updated my Feisty install, and it stopped working (randomly locking as described by others), but when I booted off the old kernel it still booted fine...

Problem is that it installing Gusty messed up my Nvidia drivers installation, and since the gusty repositories don't have the kernel headers for the old kernel then I can't rebuild it... It seems as if I will have to install Feisty again and keep it...

I also tried to install a few other Distros a few weeks ago, and my laptop (a 3217la) froze randomly, so that's why I think that it may be an issue with newer kernels (since it works fine with Feisty, but any distro with a newer kernel makes it freeze)...

If that is the case it would mean we would pretty much have to stick with Feisty until they fix up whatever issue this laptop has with those kernels...

---

### Post by logeshnkl2004 on 2007-10-27
Today I installed Ubuntu 64-Bit from DVD on my Compaq V3228au laptop. It went very nicely. Even the nVidia Graphics driver also performing well. But yet I can't able to connect to the internet Using my wireless connection. Please help me if anyone of you can. 

Thanks in Advance.....

---

### Post by rozojc on 2007-10-28
> **logeshnkl2004 said:**
> Today I installed Ubuntu 64-Bit from DVD on my Compaq V3228au laptop. It went very nicely. Even the nVidia Graphics driver also performing well. But yet I can't able to connect to the internet Using my wireless connection. Please help me if anyone of you can. 

Thanks in Advance.....

Well, there are two ways. Mine kind or worked using the Restricted Drivers (in the System menu) where Gusty told me it could download the firmware, but it works better with ndiswrapper...

So what I did was: as super user edit /etc/modprobe.d/blacklist and added "bcm43xx" to the list (you can do it from terminal like this: sudo gedit /etc/modprobe.d/blacklist . Once you are in gedit just write bcm43xx at the end of the file).
After that, through synaptic, install the package "ndisgtk" and "ndiswrapper-utils" (which should also install ndiswrapper-common) , and in the System menu, under Administration, there should be an option that says "Windows Wireless Drivers", you use that to install the driver (you need to have the Windows driver, it should be called something like bcmwl5.inf of similar)...

---

### Post by randu on 2007-11-05
today I installed ubuntu 7.10 on compaq v3418 but it doesn't work fine. I try to 64 bits thanks

---

