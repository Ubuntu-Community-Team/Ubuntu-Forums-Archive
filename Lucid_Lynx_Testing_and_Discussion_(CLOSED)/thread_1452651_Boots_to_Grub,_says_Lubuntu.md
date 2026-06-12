---
title: "Boots to Grub, says Lubuntu"
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by teejay17 on 2010-04-12
Hi all,
I think there's a bug somewhere. Upon reboot after the updates last night, my Ubuntu 10.04 setup boots directly into Grub and says Grub 1.98 and also "Lubuntu."
This is strange as I've not, nor have I ever, installed Lubuntu on this machine. My system is 100% updated as of 9:30 pm EST, April 11th. 
Now my question is: what do you do when you are faced with Grub and all it says is "grub"? 
The command line does not seem to work in this area. 
I would just like to boot back into my system. 
Cheers.

---

### Post by QLee on 2010-04-12
Is this the same system?

[http://ubuntuforums.org/showthread.php?t=1451965](http://ubuntuforums.org/showthread.php?t=1451965)

---

### Post by kansasnoob on 2010-04-12
I'm not quite sure I understand so bear with me. Do you get a boot menu? If so does it display a list of available kernels to boot?

If "no" so far, then try rebooting and hold the Space bar down immediately after the System/BIOS screen passes. If that brings up the boot menu try selecting the older kernel (2.6.32-19). Does that boot?

Regarding the Lubuntu thing, is it part of the boot menu or just a logo type image?

Also how many operating systems do you have on this machine?

---

### Post by kansasnoob on 2010-04-12
> **QLee said:**
> Is this the same system?

[http://ubuntuforums.org/showthread.php?t=1451965](http://ubuntuforums.org/showthread.php?t=1451965)

I hadn't seen that but Ubuntu is not going to run on 128MB of RAM! Lubuntu might if installed from a minimal install.

But I had trouble with the minimal image about one week ago.

---

### Post by teejay17 on 2010-04-12
> **kansasnoob said:**
> I'm not quite sure I understand so bear with me. Do you get a boot menu? If so does it display a list of available kernels to boot?

If "no" so far, then try rebooting and hold the Space bar down immediately after the System/BIOS screen passes. If that brings up the boot menu try selecting the older kernel (2.6.32-19). Does that boot?

Regarding the Lubuntu thing, is it part of the boot menu or just a logo type image?

Also how many operating systems do you have on this machine?
I will try booting while holding the spacebar and will post the results (must wait 'till I get home from work first). 
Ubuntu is the only installed o/s. Things went wonky after the kernel update last night. 
Just goes straight to grub screen, with "Grub" and a blinking cursor. At the top it says it is grub version 1.98.

---

### Post by QLee on 2010-04-12
tejay17,
It's probably a good idea to post this here too, not just in the other thread. It's good information to have.

[QUOTE=teejay17]No, it is my other test machine, this one being a ThinkPad T41, with 30 gig hard drive, 1 gig of ram, and a Celeron Processor.[/QUOTE]

I see also that kansasnoob has experience with a minimal Lubuntu, perhaps he could help with the other system too, the one you want Lubuntu on.

---

### Post by QLee on 2010-04-12
[QUOTE=teejay17]... Things went wonky after the kernel update last night. 
Just goes straight to grub screen, with "Grub" and a blinking cursor. At the top it says it is grub version 1.98.[/QUOTE]

I've seen some other reports of trouble on thinkpad after a recent kernel upgrade, see if there is a new kernel available by the time you get home.

---

### Post by teejay17 on 2010-04-12
Well, it was definitely messed up, and nothing was working, so I reinstalled Ubuntu. Now all is well.

---

