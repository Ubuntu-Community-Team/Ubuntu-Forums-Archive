---
title: "Help with gutsy installation please."
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by Dark_Jester on 2008-02-05
I need a little help on how to properly install 32-bit gutsy without messing up my current setup.

My partition is layed out as follows:
Bootloader (PBM) **|** Windows XP **|** Ubuntu 7.10 x64 **|** Linux Swap **|** Free Unpartitioned Space.

The bootloader starts when I boot my PC and lets me select from whatever partitions I've told it are bootable. If I select the Ubuntu partition it loads GRUB from that partition (which is set to simply start ubuntu without pausing). 

***What I need*** are _noob-level_ instructions on how to install the i386 Ubuntu into an ext3 partition in the free space with a seperate GRUB installed (seperate from the currently installed GRUB I mean) on the same partition as this new install, and how to get it configured to start Ubuntu without pausing when I select "Ubuntu i386" from my bootloader (assuming it won't do that bit anyway being on the same partition as the Ubuntu install). 

I've tried to be as straightforward as possible with my description but if it's ambiguous let me know and I'll clarify.
Thanks in advance.

---

### Post by Scavok on 2008-02-05
Does this help?

[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_)

---

### Post by ubutufan on 2008-02-05
I can give you guidance to install gutsy on your free disk space and also install grub on that specific partition. But I cannot help in configuring PBM because I am not familiar with it.

Insert the gutsy cd and boot from it (use bios options to boot from cd drive)
Once the desktop is loaded, click on Install.
When you get to the partitioning part, choose manual.
On the next screen your partitions will be presented. The free disk part, you need to click on it and choose to make new partition as ext3.
I don't know if you are using IDE or SATA hard disk. In all likelihood if it IDE this particular partition will be identified as hda3 or if it is SATA as sda3. Make sure you jot down this information and make no mistake.
When you get to the last part that the installer advises it is ready to install the os to your system, you will notice a box name Advanced on the right down hand corner. Click this and enter the following
/dev/whatever the note about your partition was. It could be /dev/sda3 or /dev/hda3. Remember it was very important to identify this partition. Why? Because you are now telling the installer where to install GRUB.

If anything is not clear, let me know

---

### Post by Dark_Jester on 2008-02-05
Thankyou for the link Scavok, but I'd rather keep PBM as my OS independant partition. Good info though :)

---

### Post by Dark_Jester on 2008-02-05
Thanks  ubutufan, I thought it was something like that but I didn't know where to find the "sda/hda" info for the GRUB options. I'll give it a shot now.

---

### Post by Dark_Jester on 2008-02-05
Oh by Thor's mighty love sack! :mad:

All was going well and then I had to go and accidentally smack [ENTER] while reaching for my coffee and confirm that I had finished installing before getting to select the GRUB partition. How can my sweet beanage betray me so?

Here's what I have now:
Bootloader (PBM) **|** Windows XP ***[sda1]* |** Ubuntu 7.10 x64 ***[sda2]* |** Swap ***[sda3]* |** Ubuntu 7.10 i386 ***[sda4]***

And it all looks great apart from that GRUB has been installed onto sda1 instead of sda4 thanks to my bean-based folly.

How can I fix this one guys?

---

### Post by ubutufan on 2008-02-06
> **Dark_Jester said:**
> Oh by Thor's mighty love sack! :mad:

All was going well and then I had to go and accidentally smack [ENTER] while reaching for my coffee and confirm that I had finished installing before getting to select the GRUB partition. How can my sweet beanage betray me so?

Here's what I have now:
Bootloader (PBM) **|** Windows XP ***[sda1]* |** Ubuntu 7.10 x64 ***[sda2]* |** Swap ***[sda3]* |** Ubuntu 7.10 i386 ***[sda4]***

And it all looks great apart from that GRUB has been installed onto sda1 instead of sda4 thanks to my bean-based folly.

How can I fix this one guys?

Oups. Good lesson for everyone here. Do not drink coffee when installing operating systems.
Now let's see. You still have this PBM.

Then Grub is on sda1. To get back your windows loader you need the XP disk. You need to boot from it and use the R option for repair. Once in the windows prompt you should issue the FIXMBR command. That will (should) reinstall the windows bootloader and remove Grub. Although I should give you a warning here. I am not familiar with PBM and therefore I have no idea how the windows bootloader will interact with PBM.

After doing so, reinstall gutsy (following my previous instructions-no coffee this time)
Hope all is clear.


Judging from your info GRUB must be installed on

/dev/sda4

Make sure you type it like this

---

### Post by Dark_Jester on 2008-02-06
I've read some scary forum posts around about fixmbr messing up when trying to get rid of GRUB, leaving your Windows partition unbootable. As I can get into Windows by simply selecting it from the GRUB that was mistakenly placed there, can I somehow edit the settings for GRUB so that it automatically boots Windows and does not wait for confirmation (currently, it wais a number of seconds and boots Ubuntu i386 on sda4)? Seems the safer option to me.

If I can get that straightened out I could then reinstall i386 on sda4 and make sure GRUB goes where I want it.

- Also my XP CD does not boot properly on my laptop, it goes BSOD because it doesn't like the hardware, so I had to make an unattended disc out of it with some extra SATA drivers and such on there, and for some reason that killed the recovery console option. *sigh*

---

### Post by ubutufan on 2008-02-06
Sure you can edit Grub
Boot into the Gutsy new installation. Then from Terminal run
sudo gedit /boot/grub/menu.lst

Reading through the file you will notice somewhere close to the top
timeout   10
Change this number to 5 (seconds) or anything you like

Next scroll down and after
# # End Default Options ##

you will see your boot order.

To change this you need to have the xp options first, that is before ubuntu.
Just make sure that you have the 
title (for example XPSP2)
root (hdx,y)        Be carefull here - just paste what grub has-no sda's or anything else
makeactive
chainloader     +1

Then you may have the ubuntu boot instructions etc etc

Hope all is clear

---

### Post by Dark_Jester on 2008-02-06
OK, I don't get it:
1. I edited the menu.lst to have Windows at the top, tested it and it worked.

2. I changed the timeout to be "0", tested it and it worked.

3. I installed Gutsy onto sda4, set GRUB to be on /dev/sda4 and tested it, only to find that booting from sda4 gave me a GRUB command prompt and booting sda1 revealed that GRUB has been reset to how it was with the new Ubuntu as the default OS.

I am more stumped than a severely shortened tree.

Probably a stupid question...but, could this be caused by importing my Windows profile?

---

### Post by ubutufan on 2008-02-08
Travelling did not allow me to look into your message.

Sorry I am totally confused now. You need to explain further the situation

---

