---
title: "Boot priority is ignored! (sony vaio vpceb32fm)"
date: 2013-08-25
forum: Installation &amp; Upgrades
---

### Post by meathdeath on 2013-08-25
When trying to boot form CD/DVD my computer ignores it and attempts to boot strait away to the HDD.. any thoughts? Thanks:D

-Meathdeath[RIGHT][/RIGHT]

---

### Post by Crusty Old Fart on 2013-08-26
Check the boot order in your BIOS. If the CD drive is set as the top priority, and the system still boots from HDD, you may need to disable booting from HDD to remove it from the list of available bootable drives.
Also, some BIOS versions, when set to boot from CD, will throw a message to your screen notifying that you must press [Enter], or maybe [Spacebar], to continue booting from CD. If you miss it, it may boot from the next available bootable drive in the boot order.

---

### Post by meathdeath on 2013-08-27
How would I go about skipping the HDD? I am using the r1100y8 bios.

---

### Post by Crusty Old Fart on 2013-08-27
> **meathdeath said:**
> How would I go about skipping the HDD? I am using the r1100y8 bios.
I don't know. All BIOS versions are not the same. The boot options in my BIOS allow me to either enable or disable each of my drives. It also allows me to arrange the bootable drives in order of whatever priority I choose. Any drive for which I've marked as disabled does not show up in the priority list.

---

### Post by meathdeath on 2013-08-27
Hmmm i tried removing the hdd and it still skipped optical

---

### Post by Crusty Old Fart on 2013-08-27
> **meathdeath said:**
> Hmmm i tried removing the hdd and it still skipped optical
By that, do you mean physically unplugging it?

Is the disk in the CD drive really a bootable disk? Can you test it in another computer?

Can you test a different disk that you KNOW to be bootable, like perhaps a Windows installation disk?

I have a really weird feeling about this. It just doesn't make much sense. I would be surprised if the cause of the problem doesn't end up being something really simple.

---

### Post by meathdeath on 2013-08-28
Yeah I physically unplugged it. I know for a fact it has to be something with my DVD drive because when I attempt to boot something else I know is bootable it doesnt boot either.

---

### Post by Crusty Old Fart on 2013-08-28
Does your DVD drive perform as it should when it isn't set as a boot drive--meaning: can you access files on it, or play music from it?
Do you have an extra CD/DVD drive that you could swap in and see if the replacement drive will boot with a bootable disk in it?

---

### Post by meathdeath on 2013-08-28
I'm not sure... can you find a link to an XP driver for my DVD drive? I cant find one anywhere to test it out with... my model number is VPCEB32FM (sony VAIO)

---

### Post by Crusty Old Fart on 2013-08-28
I'll look for an XP driver for it.
In the meantime, just to help me understand what's happening, are you saying that you are running Windows XP and you cannot access anything on a disk you put in that drive, which is leading you to look for a driver for it?

---

### Post by meathdeath on 2013-08-28
Yes I am running windows XP, but the only reason I really require a driver for it is for testing purposes, (like in this case) let me check online for a driver...

---

### Post by Crusty Old Fart on 2013-08-28
> **meathdeath said:**
> Yes I am running windows XP, but the only reason I really require a driver for it is for testing purposes, (like in this case) let me check online for a driver...
The official Sony support page for drivers and downloads for your computer is --> [Here]("http://esupport.sony.com/US/p/model-home.pl?mdl=VPCEB32FM&template_id=1&region_id=1&tab=download#/downloadTab")
I saw some software for your DVD, but no driver there.
In XP, you should be able to look at the properties for the drive in "device manager" and find out if the installed driver is working properly.
With regard to reinstalling the driver, you should be able to do it from the "utilities" disk (sometimes called: "software and utilities" or "drivers and utilities" or something else similar) that may have come with your computer if you kept it.

So, by writing that you only require a driver for testing purposes, are you implying that you are able to access disks that are in the drive, for example: read files from them and play music from them? < Please answer this question. If the answer is yes, then you shouldn't need to install a driver. If the answer is no, then maybe you do, or maybe the drive is physically damaged.

---

### Post by meathdeath on 2013-08-29
i see your point but still worth a shot did u find a driver?

---

### Post by Crusty Old Fart on 2013-08-29
I can't take anymore of this.
Good luck.

---

