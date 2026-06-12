---
title: "Problems with Ubuntu installation on HP notebook"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by knighthawks on 2010-03-23
Hi all,

Okay. I have a problem here and I have spent a couple of days searching for a solution. None of them worked so far! So, I am requesting some help from the experts here. A step by step solution would be greatly appreciated as I have already tried out the stuff available in those zillion links out there.

Here is the problem!

I got a brand new HP Notebook dv4 2101TU and I am desperately trying to get ubuntu installed and working on that. So, far I have downloaded the iso file, burnt it onto a CD and tried installing from that ( I am aware that I need to alter the boot options in BIOS which I already did :) )

That did not work. It simply comes up with a black screen with a cursor blinking and gets stuck there. I have to remove the disc and restart the notebook to get it back to normal.

I have also tried the USB way by putting the iso there and making it a bootable drive but no go.

Being a system admin myself, I have checked the common things but no use. I am at my wit's end now :(

I am suspecting that this is a compatibility issue with HP notebooks or atleast this model. Please note that I still have the factory bundled Win 7 and other softwares on the notebook and I do not want to part with them. Can someone here suggets a working solution for this problem ?

Thanks in advance!

---

### Post by hoppa2k6 on 2010-03-23
I have the same issue with the HTPC I just built.  I did a fresh install off the Ubuntu install disc and when I reboot, I see my ASUS system splashscreen and then goes to a black screen with a flashing cursor for a split second.  Then it goes to a black scree with white text saying:

Marvell 88SE61xx Adapter Bios Version 1.1.0..L73
Initalizing.

Then it goes to a black screen with white text staying:

Marvell 88SE61xx Adapter Bios Version 1.1.0..L73
Adapter 1
Disk Information:
Port        Disk Name                                        Size            Speed
0            PATA: Samsung CD-ROM SC-148A                         UDMA-2

And unfortunately, it then it goes to a black screen with a flashing white cursor at the top left of the screen.  

I've combed the web for the solution but all the other people that mention a "blinking cursor" issue seem to have it after they are in the system...far after they have completed the install and started using their system.

Helping us find a solution would be great!

---

### Post by Mighty_Joe on 2010-03-23
> **knighthawks said:**
> 
I have also tried the USB way by putting the iso there and making it a bootable drive but no go.


Did you just copy the ISO or did you actually use the [Live USB Creator]("http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator")?  You have to jump through a couple of hoops to get the live file system working so just copying the ISO doesn't work.  
I have two HP laptops.  The first, a 8510p,  had no problem with Ubuntu.  The second, a 8530p, would not boot from a Live CD.  I found a post that said to switch the bios setting "CPU Fan Always On When Connected To AC" to "off" (some sort of ACPI workaround).  That didn't help.  I made a Live USB drive and it worked.  I have no idea why.

---

### Post by hoppa2k6 on 2010-03-23
SOLVED!!!

So I played around with the settings while trying to re-install.  In the options when going thru the installation setup, you can choose which hard drive to point it to.  By default it was pointing to HD0,0 (or something along those lines).  I have a serial ATA drive and the one I was trying to install on was labeled SDA1 (or something along those lines) so I selected that hard drive and voila!  Installation completed, asked for a reboot, asked to take the disc out, rebooted, hit my ASUS splashscreen, then went to the wonderful UBUNTU login screen!  YAY!!!

Hopefully that will solve your issue too!  If you need a better description of where exactly I found that screen, let me know and I'll run thru the installation again and find exactly where you access it, but it is really easy to find considering there are only 5 or so screens to go thru to install Ubuntu!

---

