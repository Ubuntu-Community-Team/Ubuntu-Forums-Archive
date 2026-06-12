---
title: "problems with acpi"
date: 2005-02-10
forum: Installation &amp; Upgrades
---

### Post by xaptux on 2005-02-10
i was trying to install ubuntu for a while  ln my laptop.well , i finally was able to do it by turning acpi=off  from grub , otherwise the installer wouldn't start.  after installing and updating the entire system. I wan't to enable acpi because my laptop turns off when it gets hot... and it gets hot fast. i tried deleting acpi=off from grub but the system hangs when trying to load acpi...

any help will be greatly appreciated..

---

### Post by Jspired on 2005-02-10
What are your system specs?  Does your notebook use APM or ACPI by default?

---

### Post by xaptux on 2005-02-10
i'm not really  sure if which of the two uses. but where can i check... the same thing happens when after i install mandrake 10.1 and gentoo 

compaq presario 2105us


Battery Technology 	Lithium ion
Brand 	Hewlett Packard
CD / DVD Type 	CD-RW/DVD-ROM
Display Max. Resolution 	1024 x 768
Display Tech 	TFT Active Matrix
Installed Cache Memory 	256 KB
Manufacturer Part Number 	DB381AR#ABA
Modem Type 	Fax / Modem
Notebook Type 	Notebook

Processor Manufacturer 	AMD
Processor Speed 	1.6 - 2.0 GHz
Processor Type 	Athlon XP-M
RAM Technology 	DDR SDRAM
Storage Controller Type (List) 	IDE
Warranty 	1 Year
Audio
Audio Output Type 	Sound card
CD / DVD
Optical Drive Read Speed 	24x (CD), 8x (DVD)
Optical Drive ReWrite Speed 	8x (CD-RW)
Optical Drive Write Speed 	8x (DVD)
Dimensions
Depth 	10.72 in.
Height 	1.58 in.
Width 	13 in.
Display
Display Size 	14.1 in.
Hard Drive
Hard Drive Capacity 	40 GB
Key Features
Display 	14.1 in. TFT Active Matrix
Installed Memory 	512 MB (DDR SDRAM)
Operating System 	Microsoft Windows XP Home Edition
Processor 	AMD Athlon XP-M 1.5 GHz
Recommended Use 	Home Use
Memory
Installed RAM 	512 MB
Input Method 	Keyboard, Mouse, Scroll Button, Touchpad
MPN 	DB381AR#ABA
Platform 	PC
Product ID 	21268013
Modem
Analog Modulation Protocol 	ITU V.90, ITU V.92
Networking
Data Link Protocol 	Ethernet, Fast Ethernet
Networking Type 	Integrated Network Card
Processor
Processor Speed 	1.5 GHz • 1500 MHz
Video
Installed Video Memory 	64 MB

---

### Post by Jspired on 2005-02-10
For starters, you may want to look [here. ](http://www.linux-on-laptops.com/compaq.html)  Your notebook is listed (multiple times) and may provide some of the answers you need.

---

### Post by xaptux on 2005-02-10
still confused... just one question in what directory can i find grub.conf

---

### Post by spider7378 on 2005-02-10
I have exactly the same problem and don't know why my laptop won't start with ACPI turned on. On other Linux Systems I never had this problem.

---

### Post by flyingfrog on 2005-02-10
Me too... Same problem on my laptop

Compaq presario 2156EA

---

### Post by shmonkey on 2005-02-10
[QUOTE=xaptux]still confused... just one question in what directory can i find grub.conf[/QUOTE]

grub.conf does not exist in Ubuntu, instead it's

/boot/grub/menu.lst

---

### Post by xaptux on 2005-02-11
was able to continue with the installation by typing  nolapic in the
boot/grub/menu.lst

---

