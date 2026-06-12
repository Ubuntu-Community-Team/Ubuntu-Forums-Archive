---
title: "First Time"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by COLiNx86 on 2007-07-24
Well I've never installed Ubuntu I've used it as a live cd only and a few other distros.
So i download 7.04 AMD 64bit iso and burned it to a cd and i restarted and it came up with the install and all of the other options i clicked the first one it was like start/install or something. then a bunch of white writing came up and went on for a minute or so maybe less but then it gave me a black screen and it's just been sitting there.
does anyone have any idea what's wrong or how to fix this. 

btw i have a 
Compaq presario v6000 with 
1gig of ram
AMD turion 64
 80 gig hdd
nvidia GeForce Go 6150 w/ shared mem

---

### Post by SinoDave on 2007-07-24
Some PCs have problems with initiating the screen with the default options. Try adding the boot option "vga=791" without "" when you first try to boot.

The liveCD startup screen should have an option (an F key maybe?) that lets you add or change the kernel boot options. I had this problem with an old laptop that I tried to install Edgy to.

Hope this helps!

-SinoDave

---

### Post by COLiNx86 on 2007-07-24
> **SinoDave said:**
> Some PCs have problems with initiating the screen with the default options. Try adding the boot option "vga=791" without "" when you first try to boot.

The liveCD startup screen should have an option (an F key maybe?) that lets you add or change the kernel boot options. I had this problem with an old laptop that I tried to install Edgy to.

Hope this helps!

-SinoDave
how would i add the boot option?

---

### Post by ErusGuleilmus on 2007-07-24
on the live CD? Push F6 to edit the script, and e on the middle one that pops up. add the vga=792 and noapic. that will get it to boot once. To permenantely makee it so it boot like this, run gksudo gedit /boot/grub/menu.lst add those to to the end of the document and save. You are good to go.

---

### Post by COLiNx86 on 2007-07-24
ok thanks i got it installed

---

### Post by soapytheclown on 2007-07-24
> **COLiNx86 said:**
> Well I've never installed Ubuntu I've used it as a live cd only and a few other distros.
So i download 7.04 AMD 64bit iso and burned it to a cd and i restarted and it came up with the install and all of the other options i clicked the first one it was like start/install or something. then a bunch of white writing came up and went on for a minute or so maybe less but then it gave me a black screen and it's just been sitting there.
does anyone have any idea what's wrong or how to fix this. 

btw i have a 
Compaq presario v6000 with 
1gig of ram
AMD turion 64
 80 gig hdd
nvidia GeForce Go 6150 w/ shared mem

should have just searched the forums for v6000 ;) 

[http://ubuntuforums.org/showthread.php?t=458164&highlight=v6000](http://ubuntuforums.org/showthread.php?t=458164&highlight=v6000)

to help you with the other problems you might / probbably will have

---

