---
title: "Blinking cursor after OS install"
date: 2024-01-03
forum: Installation &amp; Upgrades
---

### Post by paul_red2 on 2024-01-03
Hi

Firstly, I'm not an expert with computers..

I was trying to add a Linux OS to an old 32bit laptop running Windows 7.
I divided the hard drive in two partitions and put Linux on the second partition I created.

The computer was not giving me a choice on what OS I wanted when I turned on the laptop :( So I thought I put Grub on the wrong partition (I had 3 options: sda sda1 sda2 or smth like that). I had to reinstall Ubuntu and put Grub on another partition.. but nothing changed: It would always start Windows (still no grub at the start).

I thought maybe if I do a clean install of just Ubuntu on this computer and get rid of Windows, it would fix the problem.. but no luck.
So I launched Ubuntu on live USB and opened Gparted to try to fix it.. And being a total noob I deleted a partition named smth like system files, it was a fat32 one with 100Mb total size..

So now the laptop starts with a blinking cursor and does nothing else.
I might be saying smth stupid but maybe I deleted the bios of the computer or the part that job is to boot (I don't know guys).

I'll add this also that maybe could mean smth: This computer doesn't keep the time (maybe is just the internal battery that has to be changed); 
Also I usually see a screen with checks a computer does when it starts. This laptop doesn't do that.. it just shows VAIO logo and than starts the OS (well, when it was working) :P

Is there a way to recreate the bios uefi boot partition thing that is missing?
Thank you all for helping guys!

---

### Post by yancek on 2024-01-03
Exactly how old is this computer?  Ubuntu doesn't have any 32bit systems but only 64bit and dropped support fo r32bit several years ago.  Which Ubuntu release are you trying to install?  If you are trying to install something other than Ubuntu, what is it?

Installing Grub to a partition will not allow the system to boot.  You need to install it to the device, the MBR on older machines which would probably by /dev/sda and would be the default during an install.

A fat32 partition is most likely an EFI partition which probably won't work or be needed on a computer as old as the one your are using.  When you boot and access the BIOS firmware, do you see any reference to UEFI?

You might post more details on the Sony VAio you are using or do an online search on how to access the BIOS for that specific model.

---

### Post by paul_red2 on 2024-01-03
The OS I'm trying to install is MINT (which they say it's similar to Ubuntu.. don't ask me why I forgot.. from a bit of research it looked the right linux for this machine to me).

No UEFI in the bios (I remember looking for it when I was able to get to the BIOS.

So the partition that I deleted accidentally was not on the hard drive but on the internal memory of the motherboard? Wow.. How can I fix this.

I removed the internal disc and put it on the case of an external drive and hooked it to a workin PC to try to format it (in the hope that it would fix it and make the hard drive visible again) But there was no way to format it (it detects the drive but can't format it.. So now I'm cloning the internal hard drive of the working PC (with Windows 10) on this phantom drive.. But smth tells me I won't be able to use it on a computer with different hardware specs..

here's the laptop in question:
[IMG]https://www.notebookcheck.com/fileadmin/_processed_/csm_sony_vaio_cr21s_specs_f9b9829be1.jpg[/IMG]

---

### Post by MAFoElffen on 2024-01-03
> **paul_red2 said:**
> The OS I'm trying to install is MINT (which they say it's similar to Ubuntu.. don't ask me why I forgot.. from a bit of research it looked the right linux for this machine to me).

<<So this not in any way related to an Ubuntu or Flavor of Ubuntu?>> <-- And you started this thread in an Ubuntu (only) support section. Curious.

Why are you not asking about this problem about Mint 32bit on the Mint Forum? Because the last Mint 32bit OS went end of support almost a year ago?

You probably have Windows 7 installed as 32bit... But you do not realize that your laptop's Intel Core 2 Duo is 64bit right? You could probably run Lubuntu on that laptop as 64bit... Booted a BIOS legacy boot mode.

---

### Post by paul_red2 on 2024-01-03
wow.. you are right.. infact i cloned from a 64bit win10 machine and it runs ok :shock:
Sorry for posting in the wrong section but from what i read when i got mint 32bit they said it is like ubuntu.
So you suggest me to put lubuntu instead of ubuntu? Now i have win10 on this vaio laptop and would like to add lubuntu or ubuntu or whatever you guys suggest me it's better.. but i think i will have the same problem of where to put grub

---

### Post by MAFoElffen on 2024-01-03
Yes I do. Lubuntu.

If it is that old, ran Win 7, BIOS Legacy boot mode only, and Intel Core 2 Duo? It's not a modern screamer with loads of memory and a fast CPU. It needs something minimal. 

I would recommend that you try out Lubuntu on it, and see how that runs. Understand that running from an Installer LiveUSB will be slow, just becaseu of it running from a flash drive and through USB2.0. Try not to hold that against it. Use that as a test that it runs OK on it, And check the resources it is using while running.

---

### Post by paul_red2 on 2024-01-04
thanks! I'll try it

---

### Post by yancek on 2024-01-05
The image you posted in post 3 above shows the laptop came with Vista and had only 2GB of memory so something like Lubuntu would definitely be better in your case.

---

### Post by him610 on 2024-01-07
Here are the specs I found on Intel website about the T7250 processor...
> Intel® Core™2 Duo Processor T7250
2M Cache, 2.00 GHz, 800 MHz FSB

Essentials
Product CollectionLegacy Intel® Core™ Processors
Code NameProducts formerly Merom
Vertical SegmentMobile
Processor Number T7250
Lithography 65 nm

Performance Specifications
Total Cores 2
Processor Base Frequency 2.00 GHz
Cache 2 MB L2 Cache
Bus Speed 800 MHz
FSB Parity No
TDP 35 W
VID Voltage Range 1.075V-1.175V

Supplemental Information
Marketing StatusDiscontinued
Launch Date Q3'07
Servicing Status End of Servicing Updates
Embedded Options Available No

Package Specifications
Sockets Supported PBGA479,PPGA478
TJUNCTION 100°C
Package Size35mm x 35mm
Processing Die Size143 mm2
# of Processing Die Transistors291 million

Advanced Technologies
Intel® Turbo Boost Technology ‡ No
Intel® Hyper-Threading Technology ‡ No
Intel® Virtualization Technology (VT-x) ‡ Yes
[COLOR="#A52A2A"]Intel® 64 ‡ Yes
Instruction Set 64-bit[/COLOR]
Enhanced Intel SpeedStep® Technology Yes
Intel® Demand Based Switching No

Security & Reliability
Intel® Trusted Execution Technology ‡ No
Execute Disable Bit ‡ Yes

---

### Post by MAFoElffen on 2024-01-07
@him610 ---
Thank you. I had looked that up, that's why I told him it would run 64bit Lubuntu in post #6... That, and... I have one system here (for tests on my scripts) that has the same CPU that I run Ubuntu on, though is a bit slow with that heavy an OS.

---

### Post by paul_red2 on 2024-01-26
Sorry guys to bring this back.. but I want to understand why this laptop can't boot a USB. So I'm trying to install an OS I have on a USB.
If I bring up the boot device to start from (with ESC) I see only the internal HDD I can choose. On the USB Flash item, I don't see the content of the flash drive (like usually you get the name of the USB like kingstone or whatever). Ando so when I try to boot from USB, it gives me "Operating System Not Found"
But if I remove the internal 2,5 HDD and put another one where I have Windows 7 on it, it will load the OS (Win 7).
I've already tried the obvious stuff (like: burning ISO as it should, change boot order in BIOS, put legacy not UEFI etc.). It's not the first time I do this things.. I tried different USBs and OSs.. I just tried to boot from a USB with CloneZilla now and yet no way.

So the question is: why this laptop can't boot from a USB (doesn't even show the name of the USB in the boot device menu).

I'm trying to update my BIOS but I find it very difficult to find the file for this old laptop. its BIOS is very old and has very few options (never seen a BIOS so simple). I also read that there are old MOBO/BIOS that do not let you boot from USB (I don't know what to say.. maybe I misunderstood).

What do you guys suggest? Ofc the USB ports work when the OS is running (so it's not an hardware issue).

---

### Post by paul_red2 on 2024-01-26
I had boot from externat drive (in BIOS) disabled.
Whatta moron I am.. sorry guys don't consider the post above

---

### Post by MAFoElffen on 2024-01-26
No problem. No one was born computer literate. We all started as beginners and had to learn at some point.

I still do things from time to time when I am in a hurry, that I just have to own up to, and laugh at myself.

---

