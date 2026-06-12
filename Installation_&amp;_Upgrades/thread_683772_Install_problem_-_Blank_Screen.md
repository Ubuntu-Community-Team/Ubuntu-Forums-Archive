---
title: "Install problem - Blank Screen"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by Zefal on 2008-01-31
Hi Everyone,

Looked at all other simlilar threads but can't find a solution. Downloaded and burnt DVD that works as tried on laptop, but when I put it in PC I want it on I get first menu like 'start or instal'l Kubuntu and VGA safe mode install, but either way I get a blank screen - no error messages or anything.

Had SuSe 10.3 running but can't get Xfi working - even though I managed to finally compile drivers - but this is another story.

64 bit Linux

PC Specs
Intel Core 2 Duo E6600
Asus P5B Deluxe
BGF Nvidia 8800GTS 640Mb OC
4Gb Corsair DDR6400 800Mhz
Soundblaster XFI (one of main reasons why I want to switch to Ubuntu)
RAID 0 160Gb XP, RAID 0 500Gb Vista 64bit, 500Gb no OS storage drive, and 160Gb Sata 2 HDD (Ubuntu)

If anyone can help - it would be much appreciated.

THanks,

Paul

---

### Post by Siyfion on 2008-01-31
Press F6 on the bootup menu and change the last bit of the line from:

"splash --" to "nosplash --"

---

### Post by PmDematagoda on 2008-01-31
With your VGA card, I think it is best if you download the [Alternate CD]("https://help.ubuntu.com/community/Installation"), it can be found [here]("http://releases.ubuntu.com/7.10/").

After you finish installing Ubuntu, you can then configure it to work with your VGA card by installing the driver from Nvidia and configuring the X-Server, all of which we can help you with:).

---

### Post by Siyfion on 2008-01-31
I have EXACTLY that card.. :)

Like I said, just take the splash bit out or change it to nosplash. Then once installed you will have to edit the GRUB startup line and do the same, just stop GRUB booting normally and follow the prompts to edit the line (the first time), then once your into the OS, type "sudo nano /boot/grub/boot.lst" and edit the line there and save it.

---

### Post by Zefal on 2008-02-01
AAAAAAAAHHHHHHHHHH :confused:

Ok firstly thanks to GLobal_Inferno - worked a treat with the nosplash. But now please someone help!!! My computer is completely messed up!!

Ok its a really long story but  but here goes:

I have 6 sata 2 HDDs in my machine, 

Port 0) Western Digital 250Gb sata 2 (RAID 0 Vista)
port 1) Western Digital 250Gb sata 2 (RAID 0 Vista)
Port 2) Samsung Spinpoint 500Gb (no OS - storage drive) 
Port 3 Maxtor 80Gb sata 2 (RAID 0 XP)
Port 4) Maxtor 80Gb sata 2 (RAID 0 XP)
Port 5) Maxtor 160Gb Sata 2 (Kubuntu)

Live CD booted after Global_Inferno's help - all devices worked except Xfi card which I expected.

Installed to HDD through Live OS and performed guided install onto Maxtor 160Gb sata 2 drive port 5. Install went fine but I forgot to change bootloader (GRUB) location as it defaulted to install it on Vista RAID drive as this is first boot drive in BIOS. THis messed up my vista bootloader so couldn't boot anything - but this wasn't a big issue as I just changed boot drive in BIOS to XP drive and used EasyBCD to restore the vista bootloader.

Ok so I booted with vista bootloader again but obviously I had to grub loader for Kubuntu now. Before on SuSe 10.3 I used NeoGrub and put vmlinux and initrd settings in that to boot into it. I managed to fiddle with Kubuntu and NeoGrub to get it to boot, which is a pain as Kubuntu needs complete path to image and kernel unlike SuSe which seems to have shortcut files of some description so all that is needed in NeoGrub is vmlinux and initrd rather than vmlinux-7.6.22.10- blah blah blah.

Anyway I manged to get Kubuntu booting with neoGrub and proceeded to try and install Xfi driver. This failed and needed a complete kernel rebuild as per instructions on these forums. But this obviously changes the path in NeoGrub to get Kubuntu booting. I couldn't find out what the new paths were and failed to get it to boot again. So I decided to re-install Kubuntu but this time point the bootloader to be installed on the same hard drive itself so I could just point vista bootloader to the HDD to boot grub and start Kubuntu from there.

Hope you can follow me here:

In the install process I requested the bootloader to be installed on HD3 instead of HD0 that I put before. I did this as in NeoGrub you need to put down that Kubuntu is on HDD(3,1) i.e 4th Hard Drive 2nd partition.

BUT NOW....

upon reboot my BIOS checks each sata port on boot but hang on port 3!!!! Can't even get into the BIOS as it checks the drives before that! What has Kubuntu done to my machine.

The only thing I can think of is that it counts differently and sees HD3 where I want bootloader as port 3 and ignores the fact that 4 of my HDDs are in RAID 0 config, meaning they are really seen as 2 HDD collectively, leaving me with 4 HDDs in total. Meaning (I think) its tried to install GRUB to 4th HDD on sata port 3 treating it as a single drive and destroyed it!!

Anyone have any ideas?????

PLEASE HELP

Many Thanks, :(

Paul

---

