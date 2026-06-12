---
title: "[SOLVED] 7.10 Successfull installation won't boot after starting GRUB"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by cmnorton on 2008-02-25
I am stuck, and need advice for getting Ubuntu 7.10 installed on a brand-new T61 Thinkpad laptop. This laptop came though with XP, and I've imaged the disk, so I can restore if necessary.

Ubuntu 7.10 successfully installed from a 7.10 live CD (no errors perceived). When prompted to remove the installation CD and allow the system to reboot, the system never got past starting . The system failed to reboot, so I powered off, and started over.

I switched the boot display on (ALT+F1), and right after GRUB starts, the screen goes blank; disk activity stops; and I'm forced to power off. The recovery option for booting does boot me to a command line.

I am interested in debugging this for the learning process, but I don't know where to start.

---

### Post by Pumalite on 2008-02-25
What are your specs?

---

### Post by cmnorton on 2008-02-25
I don't have formal specs for the machine. What's the best thing to output and post here? I'll output tomorrow morning, when I get back to work.

What I am also going to try tomorrow is to change default run level to 3 (booting in recovery mode), and see if I can boot fully into run level 3. This system has nvdia graphics, and everything I've tried, including running the live CD in safemode and having that fail leads me to believe this is a graphics problem. Even Knoppix had to restart X a few times, but it was able to boot, both 5.1 and 5.1.1.

Edit:
-----
I want to add this may be the "blank screen" problem described at [http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_T61)
but, as I stated earlier, safe mode does not work.

---

### Post by Pumalite on 2008-02-25
You probably have integrated Nvidia Graphics. Post lspc
Memory?

---

### Post by cmnorton on 2008-02-26
2GB RAM. Intel Dual CORE 2.43 GHz. I am not sure what you are asking me to post lspc

Also, I mis-stated in my original post. The install failed on the reboot. I had entered my username (admin) and password, but had not configured the network.  So, from what I can tell, the install did not complete all the way. I got confused by the end of the first phase of the install.

If you had blank hardware -- I do -- what steps would you take to install Ubuntu 7.10 successfully?

Here are the specs for the system:

[SIZE=2]Product Line:  ThinkPad  [/SIZE]

[SIZE=2]Product Series:  T61  [/SIZE]

[SIZE=2]Product Name:  ThinkPad T61 Notebook  [/SIZE]

[SIZE=2]Marketing Information:  ThinkPad T61 Notebook is the ideal solution for frequent travelers requiring full functionality without a heavy load.  [/SIZE]

[SIZE=2]Mobile Technology:  Intel Centrino Duo  [/SIZE]

[SIZE=2]Product Type:  Notebook  [/SIZE]



[SIZE=2]Processor & Chipset[/SIZE]

**_[SIZE=2]Processor:  Intel Core 2 Duo T7700 2.4GHz  [/SIZE]_**

[SIZE=2]Processor Technology:  Enhanced SpeedStep Technology[/SIZE]

[SIZE=2]Virtualization Technology[/SIZE]

[SIZE=2]EM64T[/SIZE]



**_[SIZE=2]Bus Speed:  800MHz  [/SIZE]_**

**_[SIZE=2]Cache:  4MB L2  [/SIZE]_**

[SIZE=2]Chipset:  Intel PM965 Express  [/SIZE]



[SIZE=2]Memory[/SIZE]

[SIZE=2]Standard Memory:  2GB  [/SIZE]

[SIZE=2]Maximum Memory:  4GB  [/SIZE]

[SIZE=2]Memory Technology:  DDR2 SDRAM  [/SIZE]

[SIZE=2]Memory Standard:  DDR2-667/PC2-5300  [/SIZE]

[SIZE=2]Error Checking:  Non-parity  [/SIZE]

[SIZE=2]Memory Slots:  200-pin SoDIMM (2 Total/0 Free)  [/SIZE]

[SIZE=2]Memory Cards Support:  Secure Digital (SD) Card[/SIZE]

[SIZE=2]MultiMedia Card (MMC)[/SIZE]

[SIZE=2]Memory Stick PRO[/SIZE]

[SIZE=2]xD-Picture Card[/SIZE]





**_[SIZE=2]Storage[/SIZE]_**

**_[SIZE=2]Hard Drive:  160GB 7200 rpm  [/SIZE]_**

**_[SIZE=2]Optical Drive:  DVD-Writer - DVD-RAM/-R/-RW (Plug-in Module)  [/SIZE]_**



[SIZE=2]Display & Graphics[/SIZE]

**[SIZE=2]Display Screen:  15.4" WUXGA Ultra Widescreen Active Matrix TFT Color LCD  [/SIZE]**

[SIZE=2]Graphics Controller:  nVIDIA Quadro FX 570M  [/SIZE]

[SIZE=2]Display Resolution:  1920 x 1200 (Internal)  [/SIZE]



[SIZE=2]Network & Communication[/SIZE]

[SIZE=2]Network:  10/100/1000Mbps Gigabit Ethernet IEEE 802.3ab Integrated[/SIZE]

[SIZE=2]Intel Wireless Wi-Fi Link 4965AGN Wi-Fi IEEE 802.11n [/SIZE]

[SIZE=2]Bluetooth [/SIZE]



[SIZE=2]Modem:  56Kbps V.92 Data/Fax Modem Integrated  [/SIZE]



[SIZE=2]I/O Expansions[/SIZE]

[SIZE=2]Expansion Bays:  1 x Ultrabay Slim  [/SIZE]

[SIZE=2]Expansion Slots:  1 x CardBus Type II[/SIZE]

[SIZE=2]1 x ExpressCard[/SIZE]





[SIZE=2]Input Devices[/SIZE]

[SIZE=2]Keyboard:  Standard Size  [/SIZE]

[SIZE=2]Pointing Device:  TouchPad[/SIZE]

[SIZE=2]Trackpoint[/SIZE]





[SIZE=2]Interfaces/Ports[/SIZE]

[SIZE=2]Ports:  1 x Docking [/SIZE]

[SIZE=2]1 x 15-pin D-Sub (HD-15) Display [/SIZE]

[SIZE=2]1 x Mini-phone Microphone [/SIZE]

[SIZE=2]1 x Mini-phone Stereo Headphone [/SIZE]

[SIZE=2]1 x IEEE 1394 - FireWire [/SIZE]

[SIZE=2]1 x RJ-45 Network [/SIZE]

[SIZE=2]1 x RJ-11 Modem [/SIZE]

[SIZE=2]3 x 4-pin Type A USB 2.0 - USB [/SIZE]

[SIZE=2]1 x DC Power Input [/SIZE]

---

### Post by Pumalite on 2008-02-26
Check your chipset and Graphics controller in the Ubuntu site for compatibility.
Also Google 'Ubuntu and 965 chipset'
You'll get lots of hits.

---

### Post by cmnorton on 2008-02-26
I've gotten as far as booting into recovery mode; running dhclient; using aptitude to update and upgrade; and then running dpkg-reconfigure xserver-xorg; and selecting the vesa driver instead of the nv driver; and taking the rest of the settings as defaults. I still cannot boot due to graphics problems.

---

### Post by confused57 on 2008-02-26
Maybe this will help:
[http://www.thinkwiki.org/wiki/Install_Ubuntu_Gutsy_Gibbon_on_a_T61p](http://www.thinkwiki.org/wiki/Install_Ubuntu_Gutsy_Gibbon_on_a_T61p)

---

### Post by Mustard on 2008-02-26
Can you describe the 'graphical problems'?

---

### Post by cmnorton on 2008-02-28
Instead of writing "graphical problems", I should have been more specific. Basically, x was restarted more than 6 times, and I got an error to that effect. I went back in recovery mode; ran xconfig; selected the vga driver; rebooted, and came up in low-res mode. 

I did not configure at the point, but waited until the login completed. Then, using the restricted drivers manager, I was able to configure to a higher resolution.

---

