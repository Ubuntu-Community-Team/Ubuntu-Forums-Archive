---
title: "Make Ubuntu take up more space?"
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by II Luis II on 2010-07-19
Hey I just downloaded Wubi to install Ubuntu along side my Vista. I have 2 drives on my computer, C: and D: That was how my laptop came. My D: drive hasnt been touched, I have 111GB free on it and wanted to use that drive to run Ubuntu. As I ran Wubi it asked what the installation size Should be in a drop down menu, it only went up to 17GB but I would like to designate my whole D: drive for it to fill up, can this be done? Do I need to do a different method?

EDIT: Should I install the latest Ubuntu or the version below? Also should I use the latest Wubi? Additionally, should I use Wubi at all and just use a USB to install into my D: drive?

Thanks alot.

---

### Post by cbowman57 on 2010-07-19
The way I understand wubi it creates a virtual system by creating a file that exists on the windows partition. You would be better off installing ubuntu straight to your D: partition IMO.  If you don't want to risk your Vista boot (though it's not a great risk) you can have ubuntu install the grub loader to a usb thumb drive. 

The reason I suggest it is because some people have a difficult time removing grub and restoring the windows boot loader.

---

### Post by ajgreeny on 2010-07-19
You say you have two drives but I suspect you only have one drive, but it is divided into two partitions.  We can check that in a moment.

I would suggest that if you really want to "use" ubuntu rather than just try it, you should not use wubi at all, but should install on to one of the partitions (drives as you called them) and use grub to dual boot between the two OSs at boot time.

Let's see what you really have first.  Boot to the live CD by putting the CD in the drive and re-starting the computer.  You may need to change the BIOS setting to make the CD first boot device by hitting delete or one of the F keys at switch on; there is usually a message flashes on screen to tell you which key you need.  When the CD boots a menu will eventually appear and ask if you want to "Try ubuntu" or "Install ubuntu".  You must use the "Try ubuntu" at this stage.

You will then boot into a Ubuntu OS with gnome desktop, but you will not be affecting your hard disk in any way at this stage.  You can play around with this to see if your hardware is detected etc etc, and you can see what your setup is at the moment by typing ```
sudo fdisk -l
``` in Programs ->Accessories ->Terminal, (that's a lower case L at the end, not figure 1).  Report back here the output of that command.

---

### Post by Linux000 on 2010-07-19
Using the LiveCD(or USB) id the way to go if you have a whole drive to put Ubuntu on. WUBI is used to install Ubuntu on a virtual Hard Drive(which shows as a file in Windows). When you use the LiveCD you can chose to install to entire drive, then select your second drive(It won't show up as drive D:, so be careful) and install it side by side with windows.

---

### Post by Simian Man on 2010-07-19
> **ajgreeny said:**
> You say you have two drives but I suspect you only have one drive, but it is divided into two partitions.  We can check that in a moment.

If his computer came that way, I bet it really does have 2 physical drives in it.  My laptop is that way.

---

### Post by II Luis II on 2010-07-19
Well this is what it looks like when I go to my computer:

[IMG]http://i27.tinypic.com/211vyhk.jpg[/IMG]

Thats what I mean by two drives, the lower part of the picture surrounded by a black box is what is in the DATA (D:) section. I think ill look into making it install off the USB, I take it that info can be found on this site?

---

