---
title: "Ubuntu 17.04"
date: 2017-04-24
forum: Installation &amp; Upgrades
---

### Post by George_Ntavelis on 2017-04-24
[COLOR=#111111][FONT=Ubuntu]I have an hp pavilion 15 (ab141na), it comes with dgpu. I have the latest 17.04 iso burned using rufus (partition scheme mbr with bios and uefi). I have legacy csm enabled in bios. Booted from usb , i select the 'nomodeset' parameter and then enter 'try or install ubuntu'. I waited a few moments and voila i was inside ubuntu![/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
Could you please help me out with the following questions:
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]a.) If i try to install ubuntu on my ssd , how i can get rid of the nomodeset parameter on grub?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
b.) Could you please have a look to lspci results to the following picture. Do you think that i can successfully have my both cards enabled in ubuntu? I dont play games, i need the laptop for libreoffice and browsing nothing more.

[IMG]https://s18.postimg.org/ssrflnk21/lspci.png[/IMG]

[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Also please have a look to the Xorg.0.log file : [https://1drv.ms/u/s!ApxFJA38diF9gd5LcEYA94lUln6Lxw](https://1drv.ms/u/s!ApxFJA38diF9gd5LcEYA94lUln6Lxw)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thank you!

[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]

[/FONT][/COLOR]

---

### Post by oldfred on 2017-04-26
I do not know AMD cards and software versions.
It seems a bit confused as they discontinued an older proprietary driver and open source driver does not support all new cards.
New closed source driver also seems to not support everything.
You need to see if new driver supports your card/chip?

 Trying AMDGPU-PRO 17.10 On Ubuntu 17.04 (does not work directly)
[http://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-PRO-Ubuntu-17.04](http://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-PRO-Ubuntu-17.04)
[https://help.ubuntu.com/community/AMDGPU-PRO-Driver](https://help.ubuntu.com/community/AMDGPU-PRO-Driver)
AMDGPU-PRO 17.10 Released With Ubuntu 16.04.2 Support
[http://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-PRO-17.10](http://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-PRO-17.10)
AMDGPU & Radeon DDX Updated - Better 2D Performance, Tear Free, DRI3 Default Nov 2016 


 AMD driver discussion with 16.04
[http://ubuntuforums.org/showthread.php?t=2321963](http://ubuntuforums.org/showthread.php?t=2321963)
[http://ubuntuforums.org/showthread.php?t=2327075](http://ubuntuforums.org/showthread.php?t=2327075)
[https://ubuntuforums.org/showthread.php?t=2345215](https://ubuntuforums.org/showthread.php?t=2345215) 

I only have Intel and nVidia and those seem a bit easier to follow. 
Old nVidia cards use a supported older (frozen then current) driver.
Open source nVidia drivers generally work on older cards, but have issues with very newest cards and newest nVidia proprietary driver required.

---

### Post by grahammechanical on 2017-04-27
> [COLOR=#111111][FONT=Ubuntu]a.) If i try to install ubuntu on my ssd , how i can get rid of the nomodeset parameter on grub?[/FONT][/COLOR]

It is my understanding that when we set nomodeset as a live session boot parameter it works only with the live session. I do not think that the install process will put nomodeset as a Grub boot parameter.

When we install Ubuntu and if we tick the box "Install third party software" then we will get not only some third party audio & video codecs but also third party (proprietary) video drivers appropriate for our video card. We can install proprietary video drivers after installation by opening System Settings>Software & Updates>Additional Drivers tab. We need to be connected to the internet and allow the utility time to work.

If there is some kind of problem with video drivers Ubuntu will sometimes load a low resolution open source video driver called llvm pipe. It at least gets us to a working desktop where we can access Additional Drivers.

Regards.

---

### Post by George_Ntavelis on 2017-05-07
Thank you guys for you replies!

Sorry that i didnt replied earlier

@oldfred: It will be easier for me to setup amdgpu-pro if i will use 16.04 than 17.10? If yes i dont mind to use the that version.
@grahammechanical: Thank you for the tip. I am a beginner with Linux so please excuse my stupid questions :)

---

### Post by oldfred on 2017-05-07
Do not know about AMD drivers and what works best with what version of Ubuntu.
Links above provide about all I know.

---

