---
title: "Can't get ubuntu to boot"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by Chris2691 on 2007-09-26
I am just starting on ubuntu and can't grt pass the first step. I have downloaded ubuntu and burned it to a cd. I have set up my windows XP PC to boot from the cd drive.
When I start the PC with the unbutu cd in the drive I get the message that no bootable disk was found.
I have a single partition on my harddisk c:.

Any help will be appreciated.

Chris

---

### Post by pxwpxw on 2007-09-26
You may have just burned a copy of the single iso image, instead of the contents of the image as a bootable cd. Check from XP what is on the cd.

---

### Post by Pumalite on 2007-09-26
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by Chris2691 on 2007-09-26
Thanks pxwpxw you are correct: I have a single file on the cd rather than all the individual files.

Thanks for your help

Regards

Chris

---

### Post by Chris2691 on 2007-09-26
Great guide Pumalite

thanks heaps

Chris

---

### Post by Pumalite on 2007-09-26
You are welcome. Glad you enjoyed it.

---

### Post by vanguy on 2007-09-27
I too, have the same problem except that it IS burnt properly, and I CAN get to the boot menu, but when I try starting it, only a blinking cursor is left in the top left of the screen, and nothing happens....

---

### Post by Pumalite on 2007-09-27
Post your specs.

---

### Post by vanguy on 2007-09-27
Windows XP5.1 (Build 2600) Service Pack 1
Memory (RAM):       	1023 MB DDRII
CPU:                	Intel(R) Pentium(R) D CPU 2.80GHz
CPU Speed:          	2735.9 MHz
Sound card:         	Realtek AC97 Audio
Display Adapters:   	AGP Radeon X1650 Series | Radeon X1650 Series Secondary
 Network Adapters:   	Realtek RTL8139 Family PCI Fast Ethernet NIC - Packet Scheduler Miniport
CD / DVD Drives:    	HL-DT-STDVDRAM GSA-4120B                	
BIOS Info:          	ATAT COMPATIBLE  022806  P4M80P  42302e31
Motherboard:        	MICRO-STAR INTERNATIONAL CO., LTD MS-7222
VIA VT8237R Plus Chipset : ATI display adapter AGP (0x71C6)

---

### Post by Pumalite on 2007-09-27
>>Display Adapters: AGP Radeon X1650 Series | Radeon X1650 Series Secondary

Try this:
Ctrl+Alt+F1 to get command line. then:
sudo dpkg-reconfigure xserver-xorg, accept most defaoults, choose 'vesa' as the driver, then: startx

---

### Post by vanguy on 2007-09-27
may I ask what this accomplishes, and how after I try Ubuntu will this affect my rebooting into XP as per normal?

---

### Post by Pumalite on 2007-09-27
I'm assuming you finished your installation of Ubuntu and you installed Grub to the MBR. If that is so, we are solving an xserver problem and at the end you will have the possibility of booting either OS.

---

### Post by vanguy on 2007-09-27
no, I have not installed, I am merely "*trying*" it out from a downloaded LiveCD. In other words, booting from LiveCD.

---

### Post by Pumalite on 2007-09-27
Well, then try this:

At the LiveCD initial boot screen:
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

---

### Post by rodriguezmf on 2007-09-28
so i had the same problem, did what you said, and it just went to the black screen with the blinking cursor in the top left. says kernel alive at the bottom, i think its trying to install but it just wont, i get that if i try to install the regular way also... is there any way to get ubuntu to work for me.

---

### Post by Pumalite on 2007-09-28
Try the Alternate CD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below green sign 'Start Download'

---

### Post by psusi on 2007-09-28
Instead of the break parameter, try adding noacpi nosplash noquiet

---

### Post by dabl on 2007-09-28
> **rodriguezmf said:**
> so i had the same problem, did what you said, and it just went to the black screen with the blinking cursor in the top left. says kernel alive at the bottom, i think its trying to install but it just wont, i get that if i try to install the regular way also... is there any way to get ubuntu to work for me.


This is the classic video chip not auto-detected problem.

As Pumalite wrote earlier, you can get around it with a temporary GUI by doing the following:

Alt-F1 or Ctrl-Alt-F1 to the CLI (aka "text prompt") and log in. Then run

```
sudo dpkg-reconfigure xserver-xorg 
```
on the first screen choose "NO" to auto-detect, and on the second screen choose "VESA" as the display type.  Accept the defaults until you get to "screen resolution", where you only need to "x" one resolution that you can work with for awhile -- 1024x768 or something pretty common.  In the refresh rates, make sure you stay inside your vertical and horizontal specs for your display.  After that, the script will dump you back to the CLI.  At that point you can do ```
startx
``` and you should have a decent GUI, in which to install Firefox and otherwise continue your adventure.  Then you can research which driver is right for your graphics chip, and install it to replace the VESA display.

:guitar:

---

### Post by jwilli1489 on 2008-06-08
> **Chris2691 said:**
> I am just starting on ubuntu and can't grt pass the first step. I have downloaded ubuntu and burned it to a cd. I have set up my windows XP PC to boot from the cd drive.
When I start the PC with the unbutu cd in the drive I get the message that no bootable disk was found.
I have a single partition on my harddisk c:.

Any help will be appreciated.

Chris
i have slightly different problem --new computer witout os --when itry to user server version [or install] version] it asks for boot disc  but there is only one cd  and a floppy  --so thats as far asi get.?

---

