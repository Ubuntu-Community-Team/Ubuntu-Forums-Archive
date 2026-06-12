---
title: "External HDD quick question."
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by Enlightened Shadow on 2009-12-06
Hi, I just had a quick question. 

I am looking to buy a external hdd. I want to be able to install Ubuntu 9.10 on it and boot my computers from it. 

For example: When I want to load into Ubuntu rather than Windows (which is on the internal hdd) I could just plug in the external hdd and turn on the PC (or restart). From there I want my BIOs to detect the external hdd and boot Ubuntu from it. 

I have read that there is usually a good number of problems with this and I'm not completely sure it is possible. Could someone let me know if it is possible and if so, how I go about it.

Thanks in advance.
-Mike

---

### Post by Enlightened Shadow on 2009-12-06
Bump

---

### Post by darkod on 2009-12-06
It's possible. The main hurdle is your computer BIOS to support booting from usb, usually in the option called USB HDD or similar. Most newer BIOSes would be able to do that.
Other than that, just select ext hdd you like and that it. When installing Ubuntu on the last step before clicking Install click on Advanced, that will open advanced options and double check that grub2 will be installed on the external hdd and not the internal. Earlier during setup remember the name of the external drive, usually the internal will be /dev/sda and the external /dev/sdb.
So double check where will grub2 be installed and change if necessary. That should be it.

Also, before starting decide if you want the whole external hdd for ubuntu or you want to leave one part for ntfs partition that you can use for windows data too. It is very bad practice to give all the hdd to ubuntu, and then decide you want to use some of the space for ntfs and shrink the ubuntu. It can corrupt it.

---

### Post by Bartender on 2009-12-06
Actually, it's really easy as long as you don't make any mistakes.

That was helpful, wasn't it?

Regarding your BIOS, you have to be competent at making changes in BIOS.  Most people don't know a thing about BIOS or what it does, and they certainly don't want to mess with it.

So, first question: does your BIOS support boot from USB?  Most modern BIOS'es in at least the last five years or so do.

Second question: does your BIOS have what I call the "quick-boot" option, and do you know how to access it?  By "quick-boot" I mean a key that you tap on a few times as the PC first starts to boot up.  It's F12 on a Dell 470.  It's F8 on another PC with an ASUS motherboard.  There are probly at least two or three other keys that'll get you to quick-boot.  Quick-boot is a simple menu that pops up.  BIOS lists the bootable devices that it can detect and asks "Which one do you want to use?"  You pick and that's the one it'll try to boot from.  Quick-boot is a one-time thing.  You're not making changes to your BIOS.  The next time the PC is started up, it'll go right back to the default boot list.

Which brings us to the other obvious option in BIOS.  In this case, you go into BIOS and you do change a setting.  You find your boot device priority, and set USB first, before the HDD.  I think this may be the most convenient.  With a USB device plugged in, BIOS will try to boot from it.  If no USB device is plugged in, BIOS takes a quick look for a USB device, finds nothing, and moves on to the next device, your HDD.  It only takes a fraction of a second for BIOS to look for USB and then move on to the HDD, so it's a seamless experience for the operator.

The next trick is installing ALL of Ubuntu to the external USB device.  I'll tell you what I did, and explain why I like this method.  I bought a Vantec HDD Dock.  It has its own laptop-style power "brick".  I can plug any SATA HDD (under 1TB; for some reason the Vantec I bought doesn't support HDD's over 1TB) into the Vantec dock so it's a neat tool for massive storage products, helping other people out with their PC's, etc.  I'd rather have a dock than a pre-built external HDD.  But that's just me.

I'm a bit more hardware-oriented than some.  If I had the choice between somewhat complicated GRUB menu.lst editing, or opening up the PC and moving a few cables around, I'll go with the cables approach.  So here's what I did.  I opened up a desktop PC and plugged in a test HDD.  There were no other drives connected to this PC.  I installed Ubuntu to the HDD.  With Ubuntu seeing only one drive, there were no questions about GRUB.  GRUB installed completely to that drive.  

When done, I unplugged that drive and dropped it into the Vantec dock.  The dock was connected to my laptop.  I'd already gone into the laptop's BIOS and changed it to boot from USB.  I started the Vantec dock up, then started up the laptop.  It booted from the external HDD no problem.  

This, by the way, cannot be done with Windows.  I tried it.  Windows sees that it's outside of its normal environment and refuses to go.

The above was done with the "old" GRUB.  I'm not sure how GRUB2 might be different.  Pretty sure it'd work out the same.

You can also install Ubuntu directly to an external drive instead of the way I described above, as long as you're sure you're not getting mixed up with your internal drives and GRUB doesn't put Stage 1 on the internal drive.  

If you allow GRUB to install Stage 1 to the internal drive, your PC will only function properly with the external plugged in and spinning and I'm guessing you don't want that.

---

### Post by efflandt on 2009-12-06
I put 64-bit Ubuntu 9.10 on a WD Passport.  First I shrunk the vfat partition with gparted-live CD and created swap and Linux partitions.

One of the most important things is to make sure you pay attention to the **Advanced** button at the summary, just before it proceeds with the install.  You need that to put grub2 in the mbr of the USB drive (instead of default to mbr of your main hard drive).

If you boot on different computers with DVI/HDMI monitors with different resolutions (that do not match /etc/usplash.conf) you might have trouble with "spash" during boot after the grub menu (blinking cursor, then blank screen with no disk activity).  You could always press Ctrl-Alt-Del if that happens, then "e" during the grub menu to edit out splash from boot parameters.  Or you could edit /etc/default/grub from:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

to:

#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=true

The last line avoids grub2 menu listings that may not exist or may differ on another computer.  Then **sudo update-grub** to update grub.cfg.

It works booting to my Athlon64 3200+ desktop with ATI graphics and DVI 1280x720 HDTV, Toshiba dual-core 1280x800 laptop with Intel video, and Dell dual-core 1280x800 laptop with ATI Mobility video.  Fortunately they all work with default kernel and X modules, except wireless driver for the Dell.  But its wireless is weak and works better with Linksys WUSB54GSC recognized automatically.

---

### Post by Enlightened Shadow on 2009-12-07
Thanks for the replies.

My Desktop PC is a Dell inspiron 531, I do not know what the processor is. It is pretty much factory default as far as hardware goes. When I boot the computer I can press F12 to access what it calls Boot menu. From there I can select a device to boot from. I'm pretty sure that this is the quick boot option that was mentioned above.

If I enter setup with F2 then I can select the device boot order. They are Internal HDD, CD ROM, and Removable. I have already set these up before so that It Boots from the CD if possible (mostly for Live CDs).

I really think that this will work and just to make sure I'm going to make a live cd on my flash drive so that I can test it out.

If any of the this could pose any problems then please let me know.

Thanks again.
-Mike

---

### Post by Enlightened Shadow on 2009-12-07
Update:

I just made live CD on my 4gb flash drive. I tried to boot from it on this computer along with my laptop. It worked for both so I am happy to say that I can indeed boot from a flash drive on both machines. This really makes me excited because now it seems that I will be able to buy an external HDD, install ubuntu, and then boot from it on both my Desktop and Laptop!

If I am mistaken in any way then please let me know before I go spend $80 on a external HDD.

---

### Post by presence1960 on 2009-12-07
Go for it. Darkod & bartender laid it out quite well for you. The only thing I have to add is a picture which will show you the Advanced button you need to click to insure you put GRUB to MBR of external HDD. make sure you select /dev/sdx (where x is your external HDD) not a partition such as /dev/sdx1

---

### Post by Bartender on 2009-12-07
Thanks, presence -
A picture's worth a thousand words.  Seems to me that old saying has never been more true than when trying to communicate on a forum!

I suggested physically unplugging internal HDD's and such just to make sure that GRUB installs Stage 1 to the external.  That's not really necessary.  As mentioned above, you can go into the "Advanced" section and tell GRUB where to install Stage 1.  Just make sure it's the root of the external drive, as presence mentioned.

Right, the F12 button gets you to the menu that I reffered to as "quick-boot".

I think it's more convenient to just go into the BIOS and set the boot priority to USB first.  That way the external will boot if it's plugged in when you start the PC, and the internal will boot if the external isn't plugged in.

I just wanted to make sure you knew about both methods.  It sounds like you're ready to give it a whirl.  That was good thinking to make a bootable USB thumb drive.

---

### Post by Enlightened Shadow on 2009-12-07
Thanks Bartender. I will go and purchase a HDD as soon as I get a chance. I now have one question. How do you attach images in a post such as the one above?

---

### Post by darkod on 2009-12-07
When you are writing the post scroll little bit down and there is a button Manage Attachments. That will open new window to attach them, you'll figure it out from there. :) Basically, Browse to select the file(s), Upload button to upload them once done selecting.

---

### Post by Enlightened Shadow on 2009-12-07
LOL, it figures that it would be something simple I just didn't see it before. Thanks.

---

