---
title: "Problem Regarding Updating to ubuntu 10.04 LTS"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by shahzadah on 2010-05-02
Hi,
       
    Last n8 i upgraded my PC from ubuntu 9.10 to ubuntu 10.04.... after completing installation and restarting PC... I select ''Ubuntu 10.04 LTS, kernel 2.6.32-21-generic'' from grub menu...after selecting a black screen shows boot from (hd0, hd7)........just after that the monitor screen goes on standby shows blank and play ubuntu sound as system is booted. but its complete blank n monitor is on standby. i tried several time by restarting again n again but nothing happened... then i turn off my PC and start it again.... this time i select ubuntu "10.04 LTS. kernel 2.6.31-20-generic"... with this kernel everything is working fine and perfect... only its booting speed is competitively slow... and the same ubuntu 9.10's silver glowing icon appears on screen when the computer is booting.... though i realy wana get rid of this glowing icon...how can i bring the orginal ubuntu 10.04 booting screen ? and secondly how should i able to run the latest kernel ? is there any problem using the same old kernel 2.6.31-20 ? ? ... please help....

---

### Post by P4man on 2010-05-02
the kernel that works is not ubuntu 10.04 its a karnc (9.10) kernel and the "glowing" splash is also for 9.04, not 10.04. I think you have a problem with grub.

Also, what videocard do you have ? Is it possible its an intel 8xx gpu? It doesnt work well (if at all) with lucid at the moment.

---

### Post by shahzadah on 2010-05-02
I have dell optiplex 760 having core 2 duo processor and the graphics card is "Intel corporation 4 series chipset Integrated Graphics Controller"... How should I know this video card is supported or not by ubuntu 10.04? Please any one suggest me what should I do in this circumstances..... should i keep using this old kernel with view of 10.04 ? and if please someone let me knows why actually this happing to me ? I am w8ing...

---

### Post by terabyte1 on 2010-05-02
Most of my LUG on Tyneside are 'down' and can't raise the new 10.04 version of Lucid Lynx and some of these people are more adept at fixing problems with Linux Ubuntu than I am.


the general consensus of opinion of the Tyneside LUG is that if there is a problem with a new System upgrade then - it shouldn't have gone out 'wild' in the first place. To my mind it is like following Microsoft in releasing faulty software.

For my part, I've tried loading (several attempts at downloading the correct Kubuntu ISO) and burning to a new CD resulted in a complete failure of Kubuntu loading from Grub issues to the desktop looking like the 'skin' has been removed and you can see coloured blocks where a desktop should be. I'm a bit non-plussed with this one as it is worse that the 8.4 version that also failed when upgraded.

Cheers!

Terabyte:guitar:

---

### Post by shahzadah on 2010-05-02
Thanks for the reply terabite. but please don't mind If someone can really help here...

---

### Post by P4man on 2010-05-02
I think the best course of action would be to make a 10.04 livecd or usb, and see if you can boot that. That will confirm your machine is compatible or not, and we can use it troubleshoot your install.

---

### Post by shahzadah on 2010-05-02
Thanks P4Man.... I'll download 10.04 burn it and then let you know.... thanks for the help man

---

### Post by shahzadah on 2010-05-03
I downloaded the ubuntu 10.04 LTS iso file and burn it on cd as P4man told me to do and I tried to boot from the CD... and alas its the same result... the monitor went to standby shows blank screen in middle of booting from live cd.... please anyone tell me how to troubleshot My problem ? Can I hope that a new kernel release for 10.04 LTS shall resolve my problem ?.....On the other hand my PC is working fine with "10.04 LTS kernel 2.6.31-20-generic".. just That glowing silver icon really irritating and I think karmic's kernel is competitively slow as I heard that new 10.04 LTS release have sharp boot time...  Thanks A lot... And buddies I am having lots of fun choosing Ubuntu life style.... :)

---

### Post by texaswriter on 2010-05-03
I would recommend you display detailed stats of your system, including as detailed as mobo, cpu, memory, video card, sound card, etc: manufacturer, model #, revision, etc... if you've "flashed" the bios... or anything else pertinent like that. 

If you can't even boot from the livecd, that's not encouraging, but better for people to see if it's just incompatibility with say, a mobo, or what have you. 

Than you can start searching the thread for your hardware, one at a time I would recommend. 

Hope this helps. I'll be taking the plunge sometime this week or next on my home computer.

---

### Post by P4man on 2010-05-03
Yes some information would be useful, especially what videocard you have.

You might also want to try this: when you boot the cd, the moment you see the purple splash with the keyboard logo, press escape. Then in the menu at the bottom (I think F4 or F6) select nomodeset. See if that helps. 
[SIZE="1"]
(canonical i hate you for hiding those menus and making me type this every time!)[/SIZE]

---

### Post by Elinor on 2010-05-03
I have had the same problem with the ...21 kernel. I have #'ed this out in the grub/menu file and use .20 or .16 as both of these work. However, I suspect from the above that this hasn't completely solved the problem!?

I use a Samsung X05 with an Intel graphics card...

I'm not great on the technical stuff so if some info on the hardware of my computer would help please be specific ;)

---

### Post by Elinor on 2010-05-03
> **P4man said:**
> Yes some information would be useful, especially what videocard you have.


Sorry for hijacking these answers!

Is this of any interest re my laptop specs...

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
02:03.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
02:03.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
02:03.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)
02:07.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)

It looks like I have the Intel 8... incompatible video card...?

> **P4man said:**
> 
You might also want to try this: when you boot the cd, the moment you see the purple splash with the keyboard logo, press escape. Then in the menu at the bottom (I think F4 or F6) select nomodeset. See if that helps. 
[/SIZE]

I don't have my laptop on me but will try your advice later.

---

### Post by Elinor on 2010-05-04
Hello,

I followed the first solution here

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

which worked - although it is still very slow to start up and now it refuses to turn off if I restart! Getting there... maybe...

---

