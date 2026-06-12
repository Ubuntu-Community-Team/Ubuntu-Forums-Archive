---
title: "EE PC new install / forgotten Windows Password"
date: 2010-11-22
forum: Installation &amp; Upgrades
---

### Post by Jacob72 on 2010-11-22
Hello all

This is the first time I will be using Ubuntu OS.

I have an Asus Ee PC 4g which has windows XP running on it. I forgot my password, I was using the administrator's account, and tried to use Opcrack to retrive it. I down loaded Opcrack on to my desktop and followed the instructions to put it on to my usb key.

I started up Asus Ee PC and got it to boot from the usb, Opcrack ran OK but came up with the password of my desktop which I had down loaded the programme to?

As I have very little stuff on the Asus I decided I would just try and install Ubuntu and clear Windows off my Asus?

I down loaded Ubuntu and put the it on to my USB OK and got it running. 

I clicked the install folder on the desktop but the install stalled on the second step, the page after language?

I am going to try and down load again using a torrent as I read this may be quicker and prevent from anything going wrong in the process.

Please help as this is all fairly new to me.
Jacob
:)

---

### Post by pawhtiobo on 2010-11-22
Start the instalation directly from the USB Stick, when you start up the computer, choose the USB device as 1st boot device, try it that way :)

see ya...

---

### Post by Jacob72 on 2010-11-22
I downloaded several torents from [Alternative-download]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download") not knowing which one to use. 

I got this one to install: 

ubuntu-10.10-desktop-i386.iso.torrent

I click on the desktop icon and get the Welcome page with Languages (there is no options for 'Try' or 'Install' Ubuntu)?
So I click 'Forward' and get the next page 'Preparing to install' all the boxes are ticked so I click 'Forward'. I waited 10 mins and again it stalls/nothing seems to happen? Yesterday I waited two hours before I 'Quit', not sure how long I should wait?

---

### Post by Jacob72 on 2010-11-22
Just watched a YT video of an install of 'Ubuntu 10.04 Lucid Lynx'. He gets his install box appearing straight off with a blank desktop, and the install steps are done without delay.

I am wondering if my existing windows OS is causing my problem?

---

### Post by Jacob72 on 2010-11-22
I had a look around on the forum, no one else seems to be having the same problem. I did check my RAM though. I have 2 gig.

---

### Post by Jacob72 on 2010-11-22
Just tried to install Xubuntu - had exactly the same problem??
:confused:

---

### Post by pawhtiobo on 2010-11-22
Hi :)

How are you creating your bootable USB stick?? 

Are you using unetbootin?

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

How many GB does your USB stick has? Does it boot directly from BIOS?



see ya....

---

### Post by Jacob72 on 2010-11-22
I am using Universal-USB-Installer-1.8.1.3

The USB has 4g

>  Does it boot directly from BIOS?

Sorry not sure?

Thanks

---

### Post by Jacob72 on 2010-11-22
I am going to try UNetbootin, I am working from my Windows PC (I am locked out of my Asus), Will it matter that I am downloading the Windows version when I go to boot my Asus?

---

### Post by Jacob72 on 2010-11-22
The boot went slightly different, I first got a box with options to check memory, do a trial or install e.t.c. But the install stalled on the second step again (Preparing to install)?

---

### Post by pawhtiobo on 2010-11-23
Thats weird, on my Asus 1001P, everything was simple.

You can try to change the SATA operating mode in the BIOS, to IDE (compatible), AHCI , too see if the setup continues from the freeze point we are now.
Another suggestion, try to install it with an external USB CD/DVD, maybe it's some issue with the USB Stick, you can also check if there is in the BIOS some USB options like, "legacy support", USB 1.1/2.0, etc, and play a little with them, to see what happens. You can also try it with another USB stick.

see ya...

---

### Post by Jacob72 on 2010-11-23
Thanks for the info.

I tried re-formatting the USB, but that did not work: 
I selected 'Install Ubuntu' in the initial boot step, and it stalled at Step 2 of install again. When I hit quit the screen went black and a line of text appeared briefly at the top saying something like 'process 270 glib warning failed due to unknown username'

---

### Post by pawhtiobo on 2010-11-24
Hi :)

I would recommend that you use Gparted (HDD partition software):

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)   (bootable ISO)

Remove all partitions from your HDD, i suspect that for some reason the Windows install, the OEM partition and all the tries to install of Ubuntu have messed up the partition and boot layout, this way you will start a fresh installation on a virgin HDD, maybe this way things will go the right way.

see ya...

---

### Post by Jacob72 on 2010-11-24
That done the trick!

There was only one partition set up for Windows. I deleted it and made one new partition that is using the whole HD.

Sinto bom a ser numa nova comenca. 

Agredeco pelo a ajuda!

Ate :p

---

### Post by pawhtiobo on 2010-11-25
Glad i could help :)

See ya...

---

