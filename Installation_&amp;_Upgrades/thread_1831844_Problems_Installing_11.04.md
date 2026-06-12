---
title: "Problems Installing 11.04"
date: 2011-08-23
forum: Installation &amp; Upgrades
---

### Post by cmh0114 on 2011-08-23
I created a boot disc (USB drive) with Ubuntu 11.04 and tried to install it on my Gateway GT5012 desktop running Windows XP.  It gets to the part where I can "Run Ubuntu from this USB," and I select it.  The screen shows "loading vm/linuz..." or something like that, and then the entire screen turns into dots.

One time, when trying to boot from the drive, it brought up 
"CHS: Error 0201 reading sector 1418005 (88/68/3)  
EDD: Error 4200 reading sector 1418006"

I ran this same USB drive on another computer (also running XP), and it worked just fine, so I really have no idea what's going on.  If it matters, the computer it worked on had Internet access, this one didn't.  Any help would be appreciated.

EDIT: It says "Loading /casper/vmlinuz..." and then goes to the screen of flashing dots.

---

### Post by mikewhatever on 2011-08-24
Can you post the computer specs. If not, is it an old computer? If so, about how old? Any additional info you can provide would be welcome, because so far, the problem is rather vague.

---

### Post by cmh0114 on 2011-08-24
The computer isn't that old (maybe four years?).  It runs a Pentium D processor, Intel® Graphics Media Accelerator 900 video card, and an Intel 945G chipset.  It had a 250GB hard drive (that failed to run Ubuntu), then I switched to an unformatted 1TB hard drive (also failed), then formatted the 1TB into NTFS (which also failed to run Ubuntu).  The 250GB hard drive has Windows XP  SP3 installed. 

I'm not sure exactly what specs you're looking for that would affect the installation, so if you need any more information, let me know and I'll try to get it for you.

---

### Post by maizuddin35 on 2011-08-24
how bout try the lighter version like xubuntu or lubuntu

---

### Post by Sef on 2011-08-24
> I'm not sure exactly what specs you're looking for that would affect the  installation, so if you need any more information, let me know and I'll  try to get it for you. 	


How much ram do you have?

Read [System Requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements").


> maizuddin35 	 		 		how bout try the lighter version like xubuntu or lubuntu 	

Please first verify if amount of ram is adequate or not.

---

### Post by jringoot on 2012-11-30
I had similar errors after:
cloning a centos 6.3 system with clonezilla. 
(which coincidently is installed on SATA solid state drive, is this related? I think not)
(changing hostname)
doing a kernel-update

I tried a grub-install to resolve this, unsuccessfully. even not with livecd of centos nor livecd of ubuntu.

For whoever may benefit:

I got it finally fixed with this nifty tool:
[http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/)
and live assistance of adrian15 (yes there is a supportchat included in the livecd)

---

### Post by howefield on 2012-11-30
Old thread closed.

---

