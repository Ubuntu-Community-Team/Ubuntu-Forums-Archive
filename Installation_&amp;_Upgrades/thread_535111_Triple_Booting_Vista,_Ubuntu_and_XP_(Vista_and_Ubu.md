---
title: "Triple Booting Vista, Ubuntu and XP (Vista and Ubuntu Installed First)"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by PeEkAB0o on 2007-08-26
Hey, I've installed Vista and Ubuntu on my Computer... and everything is running great. But I miss my XP. Is there a way to add XP to the GRUB and install it 3rd, or do I have to earse everything and start over ?

Please, any help would be great!

---

### Post by logos34 on 2007-08-26
If you install XP it will overwrite Grub on the MBR and you will only be able to get into XP.

Recommended install order:

1. XP
2. Vista
3. Ubuntu

This way grub becomes your boot loader (chainloads vista bootloader).

---

### Post by Dark Star on 2007-08-26
Yep same order. Else if you face any problem do edit the grub.lst :)

---

### Post by PeEkAB0o on 2007-08-26
So there is no other way, no tricks or anything... I have to start all over again ?

---

### Post by Snoopyowns on 2007-08-26
Well, you can probably install XP, then use the Ubuntu Live cd to reinstall the GRUB and modify the menu.lst as necessary. The link below may help.

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by logos34 on 2007-08-26
Other than putting XP on another drive, I don't know of a workaround...AFAIK Vista has to be the master boot loader for any other windows versions installed (just like XP does for previous versions), and I don't think there is a way to, say, install XP without the ntldr (boot loader) overwriting the MBR...you can't install just the OS and then manually add it to vista boot loader (BCD), and then reinstall grub to the MBR to chainload vista.  You CAN, however, use Vista boot loader to boot linux, but that really doesn't help in your case.

---

### Post by logos34 on 2007-08-26
> **Snoopyowns said:**
> Well, you can probably install XP, then use the Ubuntu Live cd to reinstall the GRUB and modify the menu.lst as necessary. The link below may help.

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

Yes, you can reinstall grub to the mbr but won't xp install cause a problem with Vista--won't it try to add the vista bootloader to it's own (unsuccessfully because ntldr can't boot vista)??

---

### Post by Snoopyowns on 2007-08-26
Yeah, you're right, that will probably cause Vista to be unable to boot up.

---

### Post by logos34 on 2007-08-26
I was just thinking, there is a feature to 'hide' the vista partition from XP during install...so basically when install xp it overwrites the mbr but doesn't try to usurp the bootloading function from vista (because it can't see it), then you restore grub to the mbr, add entry for xp to menu.lst and then you might be able to boot each version of windows directly without going through a master windows bootloader

PeEkAB0o, 
full dislosure: I don't have vista but I do multiboot (multidisk too) XP with various linux distros

---

### Post by logos34 on 2007-08-26
here's a link on triple booting that talks a little about 'hide' and 'unhide' but it's not really what I had in mind to tell you the truth.  

[http://my.opera.com/holamay/blog/show.dml/1216019](http://my.opera.com/holamay/blog/show.dml/1216019)

---

### Post by PeEkAB0o on 2007-08-26
ok, so there might be hope or no... because I'm ready, I'd love to be able to just install XP now (3rd) and be able to use it and have my vista in tact as well as my Ubuntu. So if there is any way, ANY way, I'll try it out... if it doesn't work, oh well. I'll just reinstall all three all over again.

---

### Post by logos34 on 2007-08-26
this is what makes me wish I had kept my downloaded copy of the Vista RC1 last year...like an idiot I got rid of it thinking that I didn't the specs anyway to run Aero properly, but I should of kept it for troubleshooting and learning at the very least about boot issues with other OS's.,,Because I refuse on principle to buy a copy of it!  

But what I'm basically thinking is you could try using Gparted to 'hide' Vista from XP during install, because otherwise it will put the boot files on the 'active' (vista) partition...what you want is for XP boot files (boot.ini, NTDETECT, NTLDR, etc) to be on the XP drive/partition, not sda1 or whatever vista is on.  Then grub wiill be able to boot into each separately

---

