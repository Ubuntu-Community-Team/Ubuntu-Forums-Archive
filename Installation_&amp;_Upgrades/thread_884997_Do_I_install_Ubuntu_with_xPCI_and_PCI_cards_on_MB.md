---
title: "Do I install Ubuntu with xPCI and PCI cards on MB?"
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by Oortism on 2008-08-09
Can I or do I or not install Ubuntu with the cards already installed on the motherboard?  I know with XP you have to not install the cards until after the XP installation.
    Any help would be appreciated.

Thank you very much--Oortism

---

### Post by Pumalite on 2008-08-09
What kind of cards? In general; yes

---

### Post by Oortism on 2008-08-09
Xpci- ATI HD 2600 Pro Super
PCI - Broadlogic 2030 card
PCI - Vision Plus 1020a Digital Satellite TV card
PCI - Firewire / USB card and
USB - Genpix board

Thank you--Oortism

---

### Post by Pumalite on 2008-08-09
Try installing with them on first.

---

### Post by Oortism on 2008-08-09
Will do and will get back if need to?

Thank you so much for the quick responds

Oortism

---

### Post by Pumalite on 2008-08-09
Somebody will help you here.

---

### Post by Oortism on 2008-08-10
Went ahead and chose to install mythbuntu and checked my system with PCIe and PCI card installed and took me to this:

Busybox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in Sheull (ash)
Enter 'help' for a list of built-in commands.

(initramfs)



I shut down the computer thinking that the cards were the problem and took them out.  I restarted and the same screen came up.  I re-booted and started with "Live CD" and after a few minutes came up with the same screen again. (no cards on Computer just the video card as the MB does not have a built in video card. 

What do I do next?

Want to install 'Mythbuntu' on a new fresh MB.

Motherboard: Asus A8V-XE

Memory: 2 gigs

Hard Drive: 

80 gig-7200rpm  (This drive has got Windows xp and want to erase and install fresh'Mythbuntu' system)
            
500 gig-7200rpm (New)

If you need more info, I will try to comply.

Thank you very much---Oortism

---

### Post by Pumalite on 2008-08-10
Give me a link to your complete specs. It could be graphics or some hardware incompatibility. You might have to try some boot parameters.

---

### Post by Oortism on 2008-08-10
Do you mean the complete spec's of my system? ex. Name of HD, memory,etc.

What do you mean by "Give me a link to your complete specs"?

Thank you and please excuse my ignorance as Linux is completely new to me--

Oortism

---

### Post by Pumalite on 2008-08-10
If your computer is anywhere in the Internet; you can give me a link. Otherwise descrive it in detail

---

### Post by Oortism on 2008-08-10
Ok, here it is.  Am I missing anything else that you might need?

Thank you so much for your help and patience...

Oortism


Motherboard: Asus A8V-XE

Memory: Rosewill DDR400 512mb  model: RW 400/512 (4 x 512 = 2 gigs) 

Hard Drive:

80 gig-7200rpm Western Digital #WDC WD800JD-(This drive has got Windows xp and want to erase and install fresh'Mythbuntu' system)

500 gig-7200rpm Western Digital #WDC WD5000KS (New)

Video Card: Palit Radeon HD 2600 Pro Super

DVD/CD:  Samsung DVD Writer (BG68-01353A Rev. 02)
         Artec   DVD Writer (Vom-12E48X)

---

### Post by Pumalite on 2008-08-10
This might be the culprit:
'Video Card: Palit Radeon HD 2600 Pro Super
'
Try the Alternate CD.

---

### Post by Oortism on 2008-08-10
I rebooted and when the screen comes up, it shows the options:

         mythbuntu
     
    Mythbuntu Live Enviroment
       Install Mythbuntu
       Check CD for Defects
       Test Memory
    Boot from first hard disk

Press F4 to select alternative start-up and installation modes.

F1 help F2 Language F3 Keymap F4 Modes F5 Accessibility F6 Other Options

I pressed F4 and it gave me the options:
     
     Normal
     Safe graphics mode
     Use driver update CD
     OEM install (for manufactures)

I pressed 'Safe Graphics mode' and nothing happens.

What next?

Thank you---Oortism

---

### Post by Oortism on 2008-08-10
I have another card, a ATI Radeon 9100 PCI 128 mg video card.

Do you think that this card might work?

Thanks---Oortism

---

### Post by Pumalite on 2008-08-10
It might, but I have only NVIDIA in my computers. ATI does not support Linux. Anyway the Alternate CD is something you have to try.

---

### Post by Oortism on 2008-08-10
Did you read the reply for the 'Alternate CD'?  It is the one before the ATI reply.  I did that and this is what happened:

I rebooted and when the screen comes up, it shows the options:

mythbuntu

Mythbuntu Live Enviroment
Install Mythbuntu
Check CD for Defects
Test Memory
Boot from first hard disk

Press F4 to select alternative start-up and installation modes.

F1 help F2 Language F3 Keymap F4 Modes F5 Accessibility F6 Other Options

I pressed F4 and it gave me the options:

Normal
Safe graphics mode
Use driver update CD
OEM install (for manufactures)

I pressed 'Safe Graphics mode' and nothing happens.

What next?

Thank you---Oortism

---

### Post by Pumalite on 2008-08-10
Download the iso from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Check the box below the sign 'Start Download'

---

### Post by Oortism on 2008-08-10
Please excuse my stupidity and ignorance.  I went back to the dowload page and found the 'Alternate CD' dowload you were talking about.  I am downloading it now.  Will get back if I have to once I download it and try to install.

Thank you very much for your patience---Oortism

---

### Post by markbuntu on 2008-08-10
The first thing you should do is choose check cd for defects. If that is Ok you should choose Mythbuntu Live Environment. If mythbuntu live runs OK then you can install it on your computer. If it has problems it will give you messages. post them here and you will get help.

Always run the check cd for defects before installing. ALways run the live environment if you are not absolutely positive that it will work on your computer.

Also, you should have no problems with that ati card, it is fully supported in linux and will work far better than your old one.

---

### Post by Oortism on 2008-08-10
It did not dect disks and it is asking me to select a driver for my Disk drives-- Western Digital #WDC WD800JD 80 gig drive and a Western Digital #WDC WD5000KS (New), 500 gigs.  It's got a lot of driver names in a column and asked me to choose one of them. I choose a few and they didn't work.

Thank you---Oortism

---

### Post by Oortism on 2008-08-11
Ok, I finally got Mythbuntu "Alternate CD" to open up and started installing.  When it got to detecting or looking for my 2 disk drives, it couldn't find them.  It gave me options to select drivers for the hd but as I tried several of them, genric ide or other IDE options, It still wouldn't detect them  I can't continue on forward with the rest of the installation.  I'm I suppose to format these drives in Dos before I attempt to install the Mythbuntu OP system? 
    My 2 drives are a Western Digital #WDC WD800JD 80 gig drive and a Western Digital #WDC WD5000KS (New), 500 gigs.  These drives require an SATA interface.  So in the Bios, it reads them as a 3rd Master and Slave.  
    The Primary Master and Secondary Masters with EIDE Ribbons are my 2 DVD burners: 
    DVD/CD: Samsung DVD Writer (BG68-01353A Rev. 02)
    Artec DVD Writer (Vom-12E48X)

Any help would be deeply appreciated--Oortism

---

