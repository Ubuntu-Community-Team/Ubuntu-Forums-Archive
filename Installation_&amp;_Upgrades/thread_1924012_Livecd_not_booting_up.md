---
title: "Livecd not booting up"
date: 2012-02-11
forum: Installation &amp; Upgrades
---

### Post by Stuartambient on 2012-02-11
I've been trying for a few days to get Ubuntu 11.10 64bits  up to try it out just off the cd.  I've gone through all the options (F6) one at a time or in combination.  A few times I got to "setting live session user" and then it stopped.  CD stopped spinning. I pressed key, waited bur nothing.  Most the time it doesn't even get that far.

This is for a system rebuild.  New hard drive.  My system consists of an Asus p5e3 motherboard (775), quad core, 4gigs of DDR memory, an ATI 4870 ( I use the option radeon.modest=0, no difference),  a few storage drives.  There is an EMU sound card (pci) in the system.  A USB hub for my keyboard and mouse). 

I can run mem check off the cd, it also confirms the disk integrity but no love.  Is there a way to slow the messages coming across the screen. Perhaps I'm missing something.  I've tried the sata as sata, ahci, ide in the bios andnhave even shut off apic in it with no improvement.  

I had an easier go with Red Hat 1 :o

Not sure at this point what I need to do. 

Help appreciated.

Stuartambient

---

### Post by MAFoElffen on 2012-02-11
> **Stuartambient said:**
> I've been trying for a few days to get Ubuntu 11.10 64bits  up to try it out just off the cd.  I've gone through all the options (F6) one at a time or in combination.  A few times I got to "setting live session user" and then it stopped.  CD stopped spinning. I pressed key, waited bur nothing.  Most the time it doesn't even get that far.

This is for a system rebuild.  New hard drive.  My system consists of an Asus p5e3 motherboard (775), quad core, 4gigs of DDR memory, an ATI 4870 ( I use the option radeon.modest=0, no difference),  a few storage drives.  There is an EMU sound card (pci) in the system.  A USB hub for my keyboard and mouse). 

I can run mem check off the cd, it also confirms the disk integrity but no love.  Is there a way to slow the messages coming across the screen. Perhaps I'm missing something.  I've tried the sata as sata, ahci, ide in the bios andnhave even shut off apic in it with no improvement.  

I had an easier go with Red Hat 1 :o

Not sure at this point what I need to do. 

Help appreciated.

Stuartambient
When you get to the advanced install menu (like you said you've getting to)... Press <F6> and without selecting any of the options, press <Esc>...

That will get back to the menu with the kerel boot line added to the screen between the menu and the bottom bar.  Move the cursor left to "quiet" and replace it with "--verbose".  Look at the line where it may have a vga switch, possibly "vga=791".  If it does, change it to "vga=264". If it is not there, add "vga=264" somewhere at the end...

Press <Enter> to "try"... 264 is not a valid Linux VESA mode.  Using it will trick the Live Image to display an error, with a text menu to select a low res graphics mode.  Select one and continue.

During the boot process, it now will display verbose messages, then graphics, in tty1... shifting to tty7 as it gets closer to the desktop.  System messages will be in tty4.  

To scroll through these messages- <Shift><PgUp> and <Shift><PgDn>. On customer's and rebuilt PC's, I go to the desktop first to see that everything is going to run. Then I start the install from there. If error, I can get to the other virtual terminals via <Cntrl><Alt><F1 through F7> to see the background messages or look at the syslog to look for errors.

Hope this info helps.

---

### Post by Stuartambient on 2012-02-12
The  VESA resolution thing worked in so far as it came up with options.   

I am confused about the TTY's and am not able to scroll.  Again I got to "Begin: Adding live session user... ..." and the things stop.  I did add the --verbose.

I'm wondering if my system is having hardware issues.  Perhaps something with thE DVD drive.

Thank you
Stuart

---

### Post by MAFoElffen on 2012-02-12
> **Stuartambient said:**
> The  VESA resolution thing worked in so far as it came up with options.   

I am confused about the TTY's and am not able to scroll.  Again I got to "Begin: Adding live session user... ..." and the things stop.  I did add the --verbose.

I'm wondering if my system is having hardware issues.  Perhaps something with thE DVD drive.

Thank you
Stuart
As far as you know, what is your hardware specs?

---

### Post by Stuartambient on 2012-02-12
> **MAFoElffen said:**
> As far as you know, what is your hardware specs?

Motherboard is a P5E3 LGA 775 with an Intel quad core ( the one above or after the Yorkville)
PSU a Coolermaster multiple rail GX series 750 w
Memory is 2 2 gig sticks (corsair) total 4 gigs DDR 3
Video card is ATI 4870 
Sound card installed is an EMU 1212 which also has a "sync" card for digital I/o
5 sata drives with the first being a 7200rpm
USB keyboard and mouse

CPU and video have good aftermarket hsf's
Hard rive have cooling fan in hd cage
1 120mm fan in rear
Coolermaster cm stacker case, plenty or ventilation though right now it's open (panels off)

I've changed the sata type in the bios
Lowered the USB to 1.2 
I suppose I could / should disconnect the drives outside of the one for the OS

Weird thing is I tried installing Win 7 last night and even that froze 

I have wondered about the DVD drive but it seems with Ubuntu to stop spinning at that last line
"adding live session user"

Thank you for the help, very much appreciated

Stuart

---

### Post by MAFoElffen on 2012-02-12
> **Stuartambient said:**
> Motherboard is a P5E3 LGA 775 with an Intel quad core ( the one above or after the Yorkville)
PSU a Coolermaster multiple rail GX series 750 w
Memory is 2 2 gig sticks (corsair) total 4 gigs DDR 3
Video card is ATI 4870 
Sound card installed is an EMU 1212 which also has a "sync" card for digital I/o
5 sata drives with the first being a 7200rpm
USB keyboard and mouse

CPU and video have good aftermarket hsf's
Hard rive have cooling fan in hd cage
1 120mm fan in rear
Coolermaster cm stacker case, plenty or ventilation though right now it's open (panels off)

I've changed the sata type in the bios
Lowered the USB to 1.2 
I suppose I could / should disconnect the drives outside of the one for the OS

Weird thing is I tried installing Win 7 last night and even that froze 

I have wondered about the DVD drive but it seems with Ubuntu to stop spinning at that last line
"adding live session user"

Thank you for the help, very much appreciated

Stuart
On the LiveCD... are you burning from Win7? And if so, with what utility and at what speed?

From the LiveCD, can you use "Try" and get to the Live Image's desktop and does it run properly?

Your mobo's South Bridge is an Intel ICH9R chipset... You wouldn't happen to be using ICH/ISW Intel Storage Matrix RAID and/or the Intel Storage Matrix Manager? 

What version BIOS?

---

### Post by Stuartambient on 2012-02-12
> **MAFoElffen said:**
> On the LiveCD... are you burning from Win7? And if so, with what utility and at what speed?

Nope, I have no Win7 installed.  The disk I've been trying was burned on a Mac airbook.  Now I can in the Ubuntu boot menu run the disk check and that comes out successful.
I am going to burn another disk here under XP using ImgBurn.

> **MAFoElffen said:**
> From the LiveCD, can you use "Try" and get to the Live Image's desktop and does it run properly?

Right, that is the option I've been choosing, as opposed to install.  Now I removed everything on the system, hardware wise, all the other storage drives, 2 gigs of memory. 
Whether or not that made a difference, I can't get as far as live session user.

What I'm seeing now is 
system 00:10[mem: some address] could not be reserved.  (Some addresses were reserved some not) I did run  mem check though off the disk as well.

Then:
pnp: Pnp ACPI found 17 devices
ACPI: ACPI bus type pnp unregistered

And then things stop loading.


> **MAFoElffen said:**
> Your mobo's South Bridge is an Intel ICH9R chipset... You wouldn't happen to be using ICH/ISW Intel Storage Matrix RAID and/or the Intel Storage Matrix Manager? 

Nope I checked, I never installed Intel SMM.  I have the  JMicron drivers or did because really all I have is a blank hard drive at this point.

So it's basically a system rebuild. Brand new hard drive.

> **MAFoElffen said:**
> What version BIOS?

8.0.3 which is the last for the "premium" board, there are others into 15.x for other editions but from what I read on the Asus forums they were problematic in some instances.

---

### Post by MAFoElffen on 2012-02-13
> **Stuartambient said:**
> Nope, I have no Win7 installed.  The disk I've been trying was burned on a Mac airbook.  Now I can in the Ubuntu boot menu run the disk check and that comes out successful.
I am going to burn another disk here under XP using ImgBurn.

Right, that is the option I've been choosing, as opposed to install.  Now I removed everything on the system, hardware wise, all the other storage drives, 2 gigs of memory. 
Whether or not that made a difference, I can't get as far as live session user.

What I'm seeing now is 
system 00:10[mem: some address] could not be reserved.  (Some addresses were reserved some not) I did run  mem check though off the disk as well.

Then:
pnp: Pnp ACPI found 17 devices
ACPI: ACPI bus type pnp unregistered

And then things stop loading.

Nope I checked, I never installed Intel SMM.  I have the  JMicron drivers or did because really all I have is a blank hard drive at this point.

So it's basically a system rebuild. Brand new hard drive.

8.0.3 which is the last for the "premium" board, there are others into 15.x for other editions but from what I read on the Asus forums they were problematic in some instances.
Hmm. Usually, that error (Hung at "Begin: Adding live session user") is on a LiveUSB or a USB w/ persistence. It's not really a hardware error, rather a problem adding the user for the Live Image, which for the LiveCD is "ubuntu" with a blank password.  That is usually hidden in the scripts, so no-one really/usually needs to know that. That 3 things that might cause that is an error reading the scripts by a bad CD image, a dirty CD Drive... A big difference between the drive it was burned on and the drive it's reading from.

Trying to burn off another OS or off another PC would be the next step. (Remember to burn at the lowest speed). A step after that would be to try installing with the Ubuntu Alternate Install CD?

---

### Post by Stuartambient on 2012-02-13
> **MAFoElffen said:**
> Hmm. Usually, that error (Hung at "Begin: Adding live session user") is on a LiveUSB or a USB w/ persistence. It's not really a hardware error, rather a problem adding the user for the Live Image, which for the LiveCD is "ubuntu" with a blank password.  That is usually hidden in the scripts, so no-one really/usually needs to know that. That 3 things that might cause that is an error reading the scripts by a bad CD image, a dirty CD Drive... A big difference between the drive it was burned on and the drive it's reading from.

Trying to burn off another OS or off another PC would be the next step. (Remember to burn at the lowest speed). A step after that would be to try installing with the Ubuntu Alternate Install CD?

I did make a flash drive.  I did not set persistence on it though.  Not sure if it was necessary.  I couldn't find information on the penrose site explaining.  Noacpi seems to end the boot early on.  Without it I get an acpi pnp unregistered and then nothing else. 

I will try an alternate version.

Stuart

---

### Post by Stuartambient on 2012-02-14
I've made the USB drive 3x now closely following the instructions and the output of the process.  I set my bios to boot from the drive (flash drive).  I even formatted first fat32.  Things seem to go well and then I hit some odd messages:
Umount: can't umount /cdrom Device or resource busy
/init: line 7: can't open /dev/sr0 no medium found
Warning: unable to find the persistent home medium
(it repeats the top two lines twice) then-
Warning: impossible to include the Caspar-sn Snapshot

Then the drive stops spinning and nothing.

Why if I created a USB flash drive for booting am i getting messages like this?

Please help.

Stuart

---

### Post by MAFoElffen on 2012-02-15
> **Stuartambient said:**
> I've made the USB drive 3x now closely following the instructions and the output of the process.  I set my bios to boot from the drive (flash drive).  I even formatted first fat32.  Things seem to go well and then I hit some odd messages:
Umount: can't umount /cdrom Device or resource busy
/init: line 7: can't open /dev/sr0 no medium found
Warning: unable to find the persistent home medium
(it repeats the top two lines twice) then-
Warning: impossible to include the Caspar-sn Snapshot

Then the drive stops spinning and nothing.

Why if I created a USB flash drive for booting am i getting messages like this?

Please help.

Stuart
Which/who's instruction and directions are you using to create your LiveUSB?

What are you using to make your LiveUSB? I think I asked this before, but got no answer on that...

I used to use USB Creator from PenDriveLinux.com under Windows... Then I used LinuxLive USB Creator under Windows... Then I switched to UNetbootin under Windows. That's what we use at the shop.  At home I use DD... but have to re-figure out the options each time I do it that way. I have it in a document on my server, which I have to find each time. That way is from a Linux host.

---

### Post by Stuartambient on 2012-02-15
> **MAFoElffen said:**
> Which/who's instruction and directions are you using to create your LiveUSB?

What are you using to make your LiveUSB? I think I asked this before, but got no answer on that...

I used to use USB Creator from PenDriveLinux.com under Windows... Then I used LinuxLive USB Creator under Windows... Then I switched to UNetbootin under Windows. That's what we use at the shop.  At home I use DD... but have to re-figure out the options each time I do it that way. I have it in a document on my server, which I have to find each time. That way is from a Linux host.

I used pendrivelinix on a 4 gig flash drive. I followed both their instructions and the Ubuntu instructions.  I believe it came out correct.  

Anyway I will need to post back in a few days as I brought the system to a repair shop.  Some odd behavior on the computer.  It is not loading anything so right now I'm waiting for a diagnosis.  I'll update the thread when I know more.

Thank you,
Stuart

---

### Post by MAFoElffen on 2012-02-15
> **Stuartambient said:**
> I used pendrivelinix on a 4 gig flash drive. I followed both their instructions and the Ubuntu instructions.  I believe it came out correct.  

Anyway I will need to post back in a few days as I brought the system to a repair shop.  Some odd behavior on the computer.  It is not loading anything so right now I'm waiting for a diagnosis.  I'll update the thread when I know more.

Thank you,
Stuart
Will be here waiting. I'll leave this thread up in my browser.  

I'm really curious to see what they find... and if it is in any way connected to this.

Mike

---

### Post by Stuartambient on 2012-02-19
> **MAFoElffen said:**
> Will be here waiting. I'll leave this thread up in my browser.  

I'm really curious to see what they find... and if it is in any way connected to this.

Mike

Turned out to be something stupid but lead to a series of errors.  Basically my video card was really caked up with dust and was not getting proper cooling.  It had shut down during my Windows install which I believe corrupted the disk and perhaps that is why Ubuntu wouldn't finish loading.  

The tech also adjusted my memory timings though I tend to not believe they were causing problems as i had auto settings for over 3 years.

Anyway, downloaded an 11.10 64 bit version, burned to DVD and it booted up quickly.  Things worked fine inside the desktop and I'm just considering all my options for install.

Thank you for all your help.  
Stuart

---

