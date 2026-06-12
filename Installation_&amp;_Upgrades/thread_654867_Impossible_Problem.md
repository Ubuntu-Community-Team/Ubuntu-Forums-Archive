---
title: "Impossible Problem"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by AaronCW on 2007-12-31
Hi! 

Here's my problem... I have a Seagate Freeagent Desktop USB 500GB External HD. I cannot boot up my PC with the USB drive plugged in. It just won't boot... goes to a black screen. I have discovered, through much trial and error, that the problem is in my PC BIOS. There is absolutely no option to disable USB Boot. I've tried everything! So, I thought I'd work around it by installing Linux (Ubuntu) into a 100GB partition on the USB Drive... that way, I could have Ubuntu (which I've been wanting to play with anyway) and there would be a Boot Manager on my USB drive... hopefully allowing me to boot up the PC off the USB drive! Am I asking to much? 

I've tried downloading the ISO and installing from CD, but again the CD won't run with the USB drive plugged in. If I unplug the USB drive, I can load Ubuntu but then when I plug the USB drive in, it is not recognized at all. 

I also tried with SLAX and was able to load the OS and then get it to recognize the USB drive but I have no idea where to go from there. (May be a little off topic for this forum, sorry! But I need help bad!) 

I guess I could live with having to plug this drive in EVERY time I load up my OS (Primary OS is Windows XP SP2) but it's just such a pain! 

Anyone have any advice?? I've been living this way for 1+ year now! 

Thanks in advance! Aaron

---

### Post by Herman on 2007-12-31
Hello AaronCW,
Why not begin with [Super Grub Disk]("http://supergrub.forjamari.linex.org/?section=download#usb") for USB? 
You can install that in your USB drive first and then you can boot just about anything.
You can also make your own customized edits to your Super Grub Disk menu and personalize it to your own tastes and behaviour.
Once you have Super Grub Disk to begin with you will probably easy to do everything else.

Are the USB ports at the back of your computer? Would a USB extension cord help? 
I have one of those and it's great for flash memory disks but for some reason doesn't seem to have the power for my 2.5" external hard drives. The 2.5" laptop hard drive cases are great because they fit in my pocket and I only have to take one USB cord with me.  They rely on power from the USB socket to spin the drive up though, and I had trouble getting those to work on my extension cord. There good for computers with USB ports in front.

The bulkier external USB drive enclosures for regular desktop 3.5" hard drives like you probably have, come with a separate power cable to plug into the wall  or better, into a UPS unit.  Those don't need to draw power from the computer's USB port for the hard drive motor either, so those should run okay if you get a USb extension lead.
...Yup! Mine does, I just tested it as I'm typing this to make sure.

Probably you will be able to buy a USB extension cord from your nearest computer shop for a very modest sum, then you'll find it a lot easier to plug in or unplug any USB device you may have when they are in easy reach.

USB drives are best for storing data and hard drives inside your computer are best for operating systems. It is possinble to install Ubuntu in a USB device though, and there are a few different way to do it.
Why not install Ubuntu inside instead first?

Regards, Herman  :)

---

### Post by Craigus on 2007-12-31
> There is absolutely no option to disable USB Boot

That sounds ... unlikely. What hardware do you have ?

---

### Post by wpshooter on 2007-12-31
First have you tried updating your BIOS, if there is a newer one available.

Second, are you sure that you have all of your drives situated on the best motherboard connector arrangement and that your jumpers, if any, are set most properly ?

Good luck.

---

### Post by AaronCW on 2007-12-31
I'm running a Compaq Celeron S5200NX ... mostly original except for a generic NVIDIA card. 

I'm pretty sure my jumpers are set right.. I have one HD, it's set as Primary Master, the jumper is set correct on the HD. (At least, according to the diagram on the label) - I have 2 CD drives, DVD and CDRW that are both on the Secondary channel. I have six USB ports, and currently the USB Drive is plugged into one of the front ports for easy access while troubleshooting. 

I'm running version 3.17 of the BIOS that comes with the PC. I checked today and this was the latest version, although I noted it was released in 2004. :( 

There are two options inside the BIOS that I have looked at pretty much up and down. The first is the USB Legacy support, the options are to Disable, Enable, and Auto. I've tried them all to no effect. Anytime I boot up the PC with the USB Drive plugged in, no matter what Legacy Support is set to... it doesnt work.

The second option is the Boot Order. I have four Boot "slots" .. the first is Floppy, the second is CDRW, the third is my Internal HD (WindowsXP) and the fourth is Network Boot. -- I have tried enabling/disabling the Floppy, nothing. The Network Boot is disabled. 

Nowhere in the BIOS can I find anything that directly says USB Boot or similar.. ?! I'm stumped

Here's a link to my Original System Specs on the HP Website... 
[http://h10025.www1.hp.com/ewfrf/wc/product?product=363430&lc=en&cc=us&dlc=en&submit.y=0&submit.x=0&lang=en&cc=us](http://h10025.www1.hp.com/ewfrf/wc/product?product=363430&lc=en&cc=us&dlc=en&submit.y=0&submit.x=0&lang=en&cc=us)

---

### Post by AaronCW on 2007-12-31
Herman, Thx for the Information. I'm going to try that right now, in fact I already downloaded the software. 

Another question... I already have the USB Drive partitioned... thanks to PartionMagic 8. I have a 500MB Swap, a 100GB Linux Ext2 Partition, and the rest is NTFS for Storage. Is there no was to just manually copy files to those partitions so that it will boot Linux? 

Remember the good ole days when all you needed was Command.com !! :D

---

### Post by Craigus on 2007-12-31
> the second is CDRW

I don't suppose that the BIOS thinks that the USB HD is a USB optical drive and therefore boots from that ?

What happens if you make the HD higher in the boot priority than the CDRW ?

---

### Post by Herman on 2007-12-31
> Is there no was to just manually copy files to those partitions so that it will boot Linux?  There is a way for USB flash memory sticks to just copy the files from either a CD or an .iso for a CD that can be mounted using a  Linux command. (That saves the work of burning a CD first and there's less chance of corruption). I haven't tried that method in a real hard disk yet, it might work., It's not such a simple procedure though, and will likely take you some time and patience. I know it works for flash memory. [LiveCDPersistence - Community Ubuntu Documentation]("https://help.ubuntu.com/community/LiveCDPersistence")
> I've tried downloading the ISO and installing from CD, but again the CD won't run with the USB drive plugged in. If I unplug the USB drive, I can load Ubuntu but then when I plug the USB drive in, it is not recognized at all. 
 You could try booting up the Ubuntu Live CD first, then plugging in the external USB drive, and manually mounting the USB drive, since it isn't being mounted automatically, here's a link about how to mount file systems just in case you need it, [File Systems and Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm").

Another idea is to try making a small partition somewhere, (in either your internal hard drive or in your USB external drive, and copying the files from the .iso or the CD into it and booting it so it will run as a Live CD and you can install from it. Here's are the links, 
[Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick") - Installing from a USB memory stick.
[Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux") - Installing using a spare partition from an existing Linux system to house the Ubuntu CD image.
[Installation/FromWindows]("https://help.ubuntu.com/community/Installation/FromWindows") - Installing from Windows without using floppies, a CD, or any other removable media.

---

