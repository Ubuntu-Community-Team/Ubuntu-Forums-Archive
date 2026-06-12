---
title: "Dual boot help"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by shnevdorf on 2006-10-11
I am trying to setup a dual boot. I have searched through
the forum plus many other articles and can't seem to find
the solution I need. I currently have XP installed on a 
RAID 0+1 array with 4 80GB SATA drives on a promise fastrak
S150 TX4. I have a extra 40GB IDE for storage and a 120GB IDE 
I want to install Ubuntu on. When I run through the install it
doesn't recognize the windows partition. It sees the 4 SATA
drives but as 4 seperate drives as they are. I really don't 
want to mess with my XP install so don't want to put grub in 
the MBR there. What I was hoping to do would be set the 120GB 
as the main boot drive in the BIOS and have grub installed 
there and be able to boot both XP and Ubuntu from there. 
From what I have read I think the first thing I need to correct 
is I should be using the alternate install CD, but I'm not 
sure if that is correct. I would appreciate any help or links 
in the right direction. Thanks in advance.

---

### Post by aysiu on 2006-10-11
Installing Grub to the MBR doesn't mess with XP. In fact, that's what helps you choose XP or Ubuntu from the boot menu.

If you install Grub somewhere else, you'll have to do all sorts of virtual backflips to get your dual boot menu working to boot to both OSes.

---

### Post by shnevdorf on 2006-10-11
Well I wasn't aware of that, so then that won't be a problem. The problem is then I don't seem to get the option for grub to install at all. Actually after I install Ubuntu if I try to boot from the drive I just get Error Loading Operating System.

---

### Post by aysiu on 2006-10-11
The Desktop CD assumes you want Grub installed to the MBR and does so.

The Alternate CD should give you options to install it on a partition or floppy drive.

---

### Post by gn2 on 2006-10-11
Does your "Boot Device Selection Menu" show the RAID as a boot device?

If it does you could try this:

[http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

If you get it working using this method please let me know.

.

---

### Post by shnevdorf on 2006-10-11
Thanks for the idea gn2 but that will not work because my board doesn't have that option.
I think I found what my problem is but I'm not sure if I am correct or how to fix it. What I
think the problem is, the install doesn't see my raid array as a single drive but sees each
of them separately. This is where I think the problem lies, I can't install grub into the MBR
if they are seen as separate drives instead of one. If this isn't correct I would appreciate
if someone could explain why. If this is correct if anyone knows how I can correct this I 
would be very greatful. Thanks

---

### Post by shnevdorf on 2006-10-11
Also, can someone please suggest what would be a better install cd to use in this situation?

---

### Post by confused57 on 2006-10-12
You can use the alternate install cd to specify where to install grub.
I'm not familiar with raid configuration, but you might be able to boot first to the IDE drive Ubuntu is installed on...you'd need to add an entry to grub in order to boot Windows, as described in this link:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by shnevdorf on 2006-10-12
Thanks for all the suggestions. I was able to get it working by using my boot.ini to boot 
into Ubuntu instead of grub boot into Windows. In fact I am posting this in Epiphany.

---

