---
title: "Black screen after booting Ubuntu 11.10 from USB"
date: 2012-04-20
forum: Installation &amp; Upgrades
---

### Post by Idealistic22 on 2012-04-20
I'm trying to install ubuntu 11.10 x64 onto my laptop and replace windows. I saved the ubuntu 11.10 DVD iso to my fat32 USB stick and ran the Universal USB installer. I resarted my computer and hit esc then F9 to access the boot menu. From there I was able to boot from my USB. Next, a black menu screen with grey font appeared.
 
It had 5 or 6 different options to select from, including: Run ubuntu from usb; install ubuntu to hard disk; advanced options; and help. The first two options gave me the same issue. Everything appeared to be fine for about 5 seconds but after many strings of code had appeared on the screen, it flashed once and went completely black. However, I was surprised to hear "chimes" or something (seemingly implying some measure of success) only moments after the screen had gone black. Each time I was forced to restart because I had no idea what was going on with the screen black and all.
 
Here are my specs:
 
2.5GHz AMD Dual-Core A4-3305M Accelerated, 6GB RAM, 640GB HDD (G6-1D40CA)
 
1) Does it matter if I choose "ubuntu 11.10 DVD iso" vs. "Ubuntu 11.10 Desktop iso" when running the Universal USB installer? I selected the former. 
 
2) Should I register my laptop with HP? I'd rather not since im planning on going with Ubuntu anyways.
 
3) is there anything else I need to do with my laptop to prepare it for installation?
 
I'm not sure exactly how to tackle this issue; I have no experience installing linux. I'm hoping someone can help me out.

---

### Post by MonkeyPaw on 2012-04-20
The blank screen issue is likely due to your Llano-based APU. It's not uncommon to have issues booting the installer with these APUs, as that is what I found trying to install it on an FM1 desktop. You may have some success by connecting it to an external display using the HDMI. Once you get it installed, you will need to install the AMD proprietary drivers before trying to run on your laptop screen.

Unfortunately, you may not have much luck running anything newer than 11.04, unless 12.04 final has the bug fixes needed to boot to the installer on Llano-based machines.

I suggest searching the forums for "Llano" notebooks/laptops and see what others have done.

Before you attempt to install, make sure you have recovery discs. That way if you ever want to sell your machine, you have the ability to restore it to factory settings. These days you often have to make them yourself by running a program on the laptop and feeding it DVDrs.

Lastly, it's not a bad idea to register with the vendor. It's often necessary for warranty service in the event of a hardware failure.

---

### Post by Idealistic22 on 2012-04-20
> **MonkeyPaw said:**
> it's not a bad idea to register with the vendor.
 
Okay, First thing I'll do is register with HP. If I manage to successfully install ubuntu, will I/should I have to reinstall/register with HP?
 
> **MonkeyPaw said:**
> Before you attempt to install, make sure you have recovery discs.
 
Next, I'll make a recovery disc. If I do replace windows with unbuntu, can't I still restore my laptop to factory settings via the "system restore" option available from the start up/boot menu, or will this feature be removed after installing Ubuntu?
 
> **MonkeyPaw said:**
> You may have some success by connecting it to an external display using the HDMI.
 
Alright, I'll try hooking it up to my TV via HDMI next time I boot from USB. And if all goes well, I'll install the AMD drivers whilst still on my TV. I imagine I'll still have to install any other relevant drivers as well ..sound etc? will they be Linux compatible?
 
Thanks for your help

---

### Post by Idealistic22 on 2012-04-21
For anyone intereseted:
**The problem was due to the absense of Linux/AMD drivers on my latop. I connected it to my TV via HDMI and installed Ubunutu that way. Once I aquired the drivers (which Ubuntu found automatically) I was able to run it entirely on my laptop**

---

### Post by MonkeyPaw on 2012-04-21
Glad it worked out for you. And to answer your question about the restore partitions for Windows, it just depends on your install and what GRUB sets up for a repair. If you're dual booting, then I think you'll be okay. If you completely wipe windows off and let Ubuntu install on the whole drive, it will probably take the restore partition with it. With the recovery DVDs, you'll be all set to restore, even if you need to replace the hard drive later. As with all things, backups, backups, backups. :)

---

