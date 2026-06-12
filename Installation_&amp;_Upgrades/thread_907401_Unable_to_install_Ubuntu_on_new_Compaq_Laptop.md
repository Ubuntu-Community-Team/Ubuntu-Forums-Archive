---
title: "Unable to install Ubuntu on new Compaq Laptop"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by troach on 2008-09-01
Hi,

I tried installing Ubuntu on a brand new Compaq laptop. I have tried many flags including acpi=off and noapic, and apm=off. 

These are the ones I tried and various combinations.

vga=normal ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off single pci=off.

I basically get an "Kernel panic - not syncing: Aiee, killing interrupt handler!" error. I have tried the alternative CD (both AMD 64 bit) and it installed but on the first boot, I got the same issue. if I don't pass in any parameters and accept the default boot for the regular CD, it starts to load and freezes with the caps lock and numlock key flashing. I have to do a hard shutdown. It is an AMD X2 with 2GB of Ram. It has the atheros wireless card.

I had the same isue with CentOS 5.2. However, when I passed in the acpi=off and all-generic_ide the ahci sata driver worked and it installed. It still did not detect my wireless. I installed the madwifi driver (and the hal file) and I did a modprobe ath_pci and it just froze. Upon reboot I got Kernel panics. 

I then proceeded to put Vista back on it and everything worked flawlessly. I am thinking this might be newer hardware than their are drivers for Linux and what tries to control the atheros wireless card causes the whole machine to just lock up.

Does anyone have any other ideas I can try? Would the 32 bit CD be worth a shot to just see if I can get the LiveCD to work? Since my memory is not over 4GB, I think I should be fine with the 32 bit if it works. 

All ideas are appreciated. I would love to get the 64 bit version of Ubuntu desktop working (I am downloading the Intrepid Ibex beta to see if I have any luck there).

Thanks!

T

---

### Post by cmat on 2008-09-01
What particular model are you using. I'm also having problems with my compaq laptop. Seems that the nvidia chipset is not currently supported by the kernel.

---

### Post by troach on 2008-09-01
> **cmat said:**
> What particular model are you using. I'm also having problems with my compaq laptop. Seems that the nvidia chipset is not currently supported by the kernel.

I picked it up at Best Buy yesterday. It was $379 for a dual core, 2gb ram, 160gb hd, 15.4 inch screen with a light scribe DVD burner. The model is CQ50-105NR.

I got the NVIDIA chipset SATA to work by issuing a "linux acpi=off all-generic-ide" on the CentOS/RedHat 5.2. It at least boots up and install with no sound or wireless/networking support. I can add those but when I did it crashed. I think I read that Ubuntu uses madwifi too?

---

### Post by troach on 2008-09-01
This is the hardware on the system.

Atheros AR5007 802.11b/g Wireless LAN Driver
Broadcom Wireless LAN Driver for Microsoft Windows Vista 

(I think I have the atheros based on lspci -vv that I did in CentOS once installed)

NVIDIA nForce Chipset Driver 
NVIDIA GeForce 8200M G 
Conexant High-Definition (HD) SmartAudio Driver 
Conexant HDAUDIO Soft Data Fax Modem with SmartCP Driver 
Software Support for HP Integrated Module with Bluetooth Wireless Technology for Microsoft Windows Vista 
Realtek USB 2.0 Card Reader Driver 


Some HP launch buttons

---

### Post by cmat on 2008-09-01
Yep, that's my laptop. I certainly hope someone has a solution since I'm stumped. I got my installation working without wireless and sound. Video was fine after I used envy to install the drivers. Without wireless I'm pretty much dead in the water. I'm suprised HP has such poor linux support, this isn't like them.

---

### Post by troach on 2008-09-01
> **cmat said:**
> Yep, that's my laptop. I certainly hope someone has a solution since I'm stumped. I got my installation working without wireless and sound. Video was fine after I used envy to install the drivers. Without wireless I'm pretty much dead in the water. I'm suprised HP has such poor linux support, this isn't like them.

How did you get it to install? What CD's did you use? What boot parameters?

---

### Post by cmat on 2008-09-01
I downloaded the latest Ubuntu installation ISO. There are bugfixes on it that enabled me to install it as usual with not boot params. Video "worked" but stuff was really distorted. When I scrolled down in text editors it distorted the text. Also when I shutdown the display gets messed up. I compiled the latest madwifi and it didn't work. Not to mention the sound was nasty. 

What I discovered was that the nVidia chipset isn't fully supported yet on other linux forums.

---

### Post by troach on 2008-09-01
> **cmat said:**
> I downloaded the latest Ubuntu installation ISO. There are bugfixes on it that enabled me to install it as usual with not boot params. Video "worked" but stuff was really distorted. When I scrolled down in text editors it distorted the text. Also when I shutdown the display gets messed up. I compiled the latest madwifi and it didn't work. Not to mention the sound was nasty. 

What I discovered was that the nVidia chipset isn't fully supported yet on other linux forums.

I downloaded the latest 64 bit CD for Hardy Heron and it still failed. Did you try 32 bit? Did you try the Ibex beta?

---

### Post by chanfle on 2008-09-01
> **troach said:**
> I downloaded the latest 64 bit CD for Hardy Heron and it still failed. Did you try 32 bit? Did you try the Ibex beta?


Hello troach....
I have the same issue with Ubuntu 8.04....but I can installed the next way...
when boot with CD press F6 and then appear the little menu and select acpi=off noapic nolapic
then you can install the OS....
but i can appear the FAN work 100%....this is one issue on this laptops brand....
I have Acer aspire 5050 AMD Turion 64, 1 RAM, Atheros Wireless....on this moment y use Ubuntu 7.10, I'm waiting the next ubuntu version
I hope that my help is useful.

Regards...

---

### Post by troach on 2008-09-01
> **chanfle said:**
> Hello troach....
I have the same issue with Ubuntu 8.04....but I can installed the next way...
when boot with CD press F6 and then appear the little menu and select acpi=off noapic nolapic
then you can install the OS....
but i can appear the FAN work 100%....this is one issue on this laptops brand....
I have Acer aspire 5050 AMD Turion 64, 1 RAM, Atheros Wireless....on this moment y use Ubuntu 7.10, I'm waiting the next ubuntu version
I hope that my help is useful.

Regards...

Thanks, I tried and no luck.

It gets to loading drivers and the last driver it tries to load and hangs on is ath_pci.

I get a wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)

Then I get the Kernel panic about it not syncing.

---

### Post by cmat on 2008-09-01
I only use 32-bit OSes since Vista installed with the laptop was 32-bit. 

I'm activly browsing the internet for the solution. I'll post any developments.

---

### Post by troach on 2008-09-01
> **cmat said:**
> I only use 32-bit OSes since Vista installed with the laptop was 32-bit. 

I'm activly browsing the internet for the solution. I'll post any developments.

Maybe I will try with that. I know the 64 bit of CentOS works with some tweaking. I bet if we wait 2 months, drivers might be out? I am going to try the Intrepid Ibex beta. I'll see if that looks anywhere near close to promising.

---

### Post by troach on 2008-09-02
I'm still stuck. Does anyone have any other ideas? Any other boot options I can try?

---

### Post by cmat on 2008-09-02
Not really sure and anything else. Seems we need to wait for new drivers to appear.

---

### Post by troach on 2008-09-02
> **cmat said:**
> Not really sure and anything else. Seems we need to wait for new drivers to appear.

You mean I have to use Vista? UGH YUCK!

Ok.... I got CentOS to install. I just can't get the wireless to work. What I might do is get Vista working. Find the driver files and pull them off on a thumb drive and label them. I then will put CentOS on it and then attempt to use wrappers around the Vista drivers to see if I can get them working in CentOS. If I do, I will let you know!

---

### Post by cus4fun on 2008-09-15
Success!

Ok, 32 bit success, but success none the less.

I have a CQ50-105NR that I just bought at Best Buy. About 8 hours of my noob fumbling and here's what I found.

I d/l'd and burned 8.04.1 and booted the live CD. Let the whole thing settle until it tossed the restricted driver notice at me, then I clicked Install.

By the way, this is a dual (duel) boot with Vista.

Installation went without a hitch.

I had minimal graphics and no wireless.

Graphics: [http://ubuntuforums.org/showthread.php?t=880787](http://ubuntuforums.org/showthread.php?t=880787) Scroll down to the "Tricky Tricky Way After Mainly attempt" section. That's the one that worked for me.

Wireless: [http://ubuntuforums.org/showthread.php?t=865971](http://ubuntuforums.org/showthread.php?t=865971) Scroll down to the #4 post by chilli555. Very simple, and that latest driver seems to do the trick. I still use Network Manager and it gives me no grief, seems to do a great job.

Sometime during all this, I think it was during the Nvidia driver install, my xorg.conf got goofed up and my touchpad was nearly featureless, no scrolling, no double-click-and-drag... so I had to re-edit xorg.conf, both the touchpad section and the server layout section. Just make sure there IS a section for "Synaptics Touchpad" with "synaptics" as the driver and make certain that "Synaptics Touchpad" is the default in the server layout section.

System .wav sounds are still crackly sounding, but music and movies play fine. 

Hope this helps someone. Happy day.

---

### Post by Safado7 on 2008-09-20
Hey guys,
I got the exact same lap top that you guys did(killer deal!! If you take a look at the system specs, it says it has the AMD Athlon Dual-Core processor, but then under CPU's, it lists 2. Does that mean we have two dual core processors? If so, that's not what they advertised).
When I installed ubuntu 8.04, everything was working for me except for the Wireless card and the Graphics card. Even enabling the restricted driver's didn't help. I believe I ended up using madwifi to get the wireless working and drivers straight from NVIDIA's page for the graphics card. Sound card worked, although the speakers sound awful! It's bad enough that I want to return it, but I spent too much time setting up a dual boot and getting the wifi and graphics card working, that I said screw it.  The *ONLY* problem I still have is that when I enable advanced desktop effects, it screws up the text when I scroll up and down.
I don't remember everything I did to get everything working(it was a whole lot of trial and error, so I kind of forgot which solution ended up making it work), but feel free to ask me any questions about the specifics,  cause I have the proof, you can get Ubuntu working on this Compaq

---

