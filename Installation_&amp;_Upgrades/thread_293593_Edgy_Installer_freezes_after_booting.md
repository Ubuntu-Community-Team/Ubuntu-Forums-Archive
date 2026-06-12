---
title: "Edgy Installer freezes after booting"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by psanta on 2006-11-05
Hi All,

I am trying to install EDGY on my Dell Inspiron 5160:

Processor: P IV HT 3.06 GHz
Memory: 1 Gbyte
NIC: Integrated Broadcom 440x 10/100
Wireless NIC: Dell Wireless 1350
Video Carg: Onboard XGI Volari-XP5

The thing is, I insert the CD and try to boot the installer. It apparently runs OK since I get to see UBUNTU LOGO and a couple of progress bars.

But after that, I get a black screen and a total FREEZE.

I tried booting with different resolutions, all with the same result. 

Any ideas? ](*,) 

Thanks a lot.

---

### Post by lordmaple on 2006-11-08
I have this exact same problem with both Edgy and Dapper Drake. I have no idea what is going on and am subsequently infuriated especially since I've installed other Linux makes and Ubuntu on other machines, but while trying the same on my home computer I fail miserably. Here are my specs:

Dual G5 Tower w/Apple Superdrive (DVD-RW/CD-RW)
Twin 2 GHZ Processors (one core)
ATI 800XP Mac Edition (256MB)
Apple 30" Cinema Display
160GB Apple Internal Hard Drive
Airport Extreme

I partitioned my drive , installed OSX on the larger partition, and left 20MB of Free Space available for Ubuntu to play with, but it freezes after the splash screen finishes and 'pbb' (whatever) fails. I searched the forums and I found out that it probably wasn't the problem. I ran the installer with 'nosplash' and the only thing I got that sounded slightly disconcerting was the following(an error message)

firmware_helper: bcm43xx_microcode4.fw for device 0001:02:01.0

Something along the lines of it couldn't load it. It then tells me its about to start up GNOME, I see a flashing cursor in the NW corner of the screen, and then (whizzt), black screen forevermore. I've tried basically every install option available but I'm still missing something: can anyone help?

---

### Post by lordmaple on 2006-11-08
The following "options" don't work eaither:

napic nolapic

I'm not using any PCI cards so I don't understand why that would be a problem..

---

### Post by psanta on 2006-11-09
Defintely Lordmapler. I have the samme issue with my wireless NIC on booting:

firmware_helper: bcm43xx_microcode4.fw for device 0001:02:01.0

I will go ahead and disable my NIC before installation and see if it works.

I will let you know if it worked.

Regards.

---

### Post by psanta on 2006-11-09
Ok. I've tried disabling my Wireless NIC: No Luck.

Still the same problem at booting.

I've also downloaded and tried KUBUNTU 6.10: same problem. Installation would hang, even with WIRELESS BIOSENABLED/BIOSDISABLED and with different screen resolutions.
Could have something to do the fact that, during booting, I have an external USB disk attached? I didn't try disabling that. Previously, I installed Ubuntu 5.10 straightforwardly in the exact same LAPTOP.

What do you guy recommend now? Should I download older UBUNTU installers or something like that?

Best regards.

---

### Post by psanta on 2006-11-09
Ok. I had to go with Ubuntu 6.06.

This LIVECD/installer works just fine with my Inspiron 5160.

Please let me know if anybody find a solution since I would like to give 6.10 (edgy) a try!

Best regards.

---

### Post by lordmaple on 2006-11-09
It seems then that the problem isn't the wireless card, its my ATI card... however, I can't use the console to edit the .conf as specified in several walkthroughs. I can't even hear the Ubuntu Music, and I waited for many different time intervals before typing "Ctrl -Alt-F4" (or whichever it was, I also tried F1 and F7 i forget now, away from notes) , and no console popped up after specifying live-nosplash vga=771 ( i think?) nopic noalpic video=ofonly as the boot command...

Any ideas?

BTW: I'm getting the same problem for both 6.06 AND 6.10...go figure! Both desktop CD's hate me.

---

