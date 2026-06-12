---
title: "Is dual boot possible?  (windows on RAID, ubuntu on normal HDD)"
date: 2005-08-04
forum: Installation &amp; Upgrades
---

### Post by snoochems on 2005-08-04
Hi all.

I am looking for some help and advice.

First, allow me to explain my PC:

CPU:     Athlon64 3200+
Mobo:   Abit AV8 
RAM:    1 GB RAM (dual channel)
Current OS:  Windows XP x64
HDD:     2x WBJB 120GB in RAID0 (using mobo VIA 8237 controller)
            1x Seagate 40GB.

Okay.  I want to set up a dual boot with Ubuntu.

I’m guessing the easiest way to do this is to just install Ubuntu onto my 40GB drive right?
I’ve done a little asking around, and no one is really willing to help me install it on my RAID0 array.  So, I probably haven’t got a choice.

So, what happens if I install Ubuntu on my 40GB HDD?  I mean, I have windows x64 installed on my RAID0 drives, and I understand Ubuntu can’t ‘see’ RAID0 drives.  So will Ubuntu detect Windows when installing so it can give me the option to ‘dual boot’.

If not, what do I need to do?

---

### Post by neilbain on 2005-08-04
I have no experience of RAID but I would have thought it safe to give it a try.  As part of the installation, Ubuntu setup will show all the partitions it can see and ask where you want to install it to.  If you are not happy that it will end up on your 40GB drive at that point you can abort without damage.

If you are happy, continue.  The problem is more likely to come towards the end of the install.  If Ubuntu detects another operating system it will ask if you want the GRUB boot loader installed.  You will need this to provide the choice of O/S at boot up.  However, if it cannot see Windows (as you say, if it cannot see RAID devices) then the boot loader will not be installed.

I would be inclined to take a good backup and give it a try.

Neil

---

### Post by snoochems on 2005-08-07
Is anyone else willing to share?

---

### Post by heart_reaver on 2005-08-07
Humm..


Buddy you can use grub boot loader,  well for dual booting it is asked at the time of installation. you can still make your system dual boot by installing GRUB BOOTLOADER.

Do read and then install grub from 

[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/) 


or you can try

sudo apt-get grub

or use synaptics

---

### Post by Gav-UK on 2005-08-10
this is exactly the same situation that i am in at the moment.

The ubuntu install went fine and Grub detected the XP install on the Raid setup. Now when i boot it goes straight into windows without giving me any other options. 


Would it be possible to edit the boot.ini file in windows to include the ubuntu install? Or is there a way to get this all to work using grub ?

---

### Post by Gav-UK on 2005-08-10
after spending most of the day trying to get linux/grub to work on my system i have finally given up. Its a pity that so many people are trying to do the same thing here without much success. Maybe in the future there will be a way to get it all to work.

---

