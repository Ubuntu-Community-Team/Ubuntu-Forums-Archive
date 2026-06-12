---
title: "Getting latest BIOS driver"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by Inder on 2010-08-01
Hello all,

I just got off the phone with an ACER support technician and he says I should make sure I have the latest BIOS driver (the installation of which could solve my overheating problems...) He helped me find [the driver]("http://global-download.acer.com/GDFiles/BIOS/BIOS/BIOS_Acer_1.11_A_A.zip?acerid=633942220264081504&Step1=Notebook&Step2=Aspire&Step3=Aspire%205536&OS=V10&LC=en&BC=Acer&SC=PA_7") and I have it downloaded as a .zip file. Now I need to know which driver I have installed for the BIOS. How do I check that on Ubuntu 9.10 - Karmic Koala?

And as if that wasn't hard enough for me, I'll have to install the new BIOS driver. I really don't have a clue how to do that. I don't even know if the driver the support technician found will work with Ubuntu or if it's strictly for Windows.. Anyways, any help would be quite appreciated!

Thanks in advance,

Shawn

---

### Post by Pumalite on 2010-08-01
You can see your BIOS and it's version at start. Get a hold of a Manual of your computer to know how to 'Flash' your BIOS

---

### Post by Inder on 2010-08-01
All right! I got two pieces of information from the BIOS page:
System BIOS Version: V1.05
VGA BIOS Version: BK-ATI VER010.044.001.008.031366

The driver the acer tech support guy found for me seems to be version 1.11, so it is more recent. Can I be sure that it will not mess anything up if I install the newer version? And then.. how do I install it?

---

### Post by Inder on 2010-08-03
Update on the issue:

I got answers from [a question on superuser]("http://superuser.com/questions/170624/how-do-i-install-a-new-bios-driver-on-ubuntu-9-10-karmic-koala/170629#170629") which tell me I'll need a live Windows CD to install the new version of the driver.  Now I'm trying to figure out whether there are any risks associated with this procedure. I also have no clue how to make a live windows CD (I do have access to legal versions of Windows XP, 7, Vista, probably all of them, through my school). Nor do I have any clue on what to do once I've got the live CD. How do I get the driver on that CD? And how do I install it once Windows is running?

Can anyone here help me further? Please note that all this BIOS driver, live CDs and the such are totally new to me. I'm just following acer's technician's advice to try to get running temperatures down and wireless connection working better.. By the way, is it reasonable to think these issues could be affected by the BIOS driver being out of date?

Thank you all so much in advance

---

### Post by brokenromeo on 2010-08-03
Definitely easiest to update the Acer bios if you have an operational windows partition...I think most Acer bios utils are also available as a dos application, you can probably use UNetbootin to create a bootable dos usb drive and run the dos version of the bios utility from there...

---

### Post by Elmer Fudd on 2010-08-03
Just a note on the BIOS and overheating.

HP had an overheating problem with their pavillion laptops. They would shut down after reaching a cirtain temperature. The "FIX" was an updated BIOS. All the new BIOS did was to not shut down the computer at that temp. As a result the computer ran but ultimately cooked the motherboard so that it failed - just out of waranty. HP would not do anything.

The BIOS can change the fan settings to come on earlier and stay on longer. That could help at the expense of battery life.

---

### Post by libssd on 2010-08-03
As others have suggested, updating an Acer BIOS from Windows is trivial, but much less intuitive from Linux. Assuming you can find someone else with the same model Acer with Windows installed, you could borrow their HDD, and upgrade your BIOS that way. A 2.5" form factor SATA drive should be plug and play swappable.

BUT... a BIOS update that goes wrong can leave you with a bricked machine. Before attempting to upgrade your BIOS, you should have a  disaster recovery strategy in place. 
**See:** [http://macles.blogspot.com/p/crisis.html](http://macles.blogspot.com/p/crisis.html)

---

### Post by Inder on 2010-08-04
What do you guys think about using a live CD with FreeDOS and using that to install the new BIOS driver? Would that be a safe way to do it? Also, libssd, I find these crisis disks very interesting, but I can't find one for my computer (acer aspire 5536-5519). Is there any other way to handle the eventual crisis situation?

---

