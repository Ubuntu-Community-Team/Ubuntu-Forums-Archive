---
title: "Help me please"
date: 2005-10-10
forum: Installation &amp; Upgrades
---

### Post by sinistermilk on 2005-10-10
I long to be unfettered from the vile system of windows but alas i can't seem to install Ubuntu onto My computer. my first error when attempting to install hoary was a problem with the discover.1 ???? which instrycytied me to burn at a lower speed when i had burnt the CD at 4x.

And today when attempting to install BREEZY it was confronted with some debootstraplog error

both cases have left me unable to install the base system.

Help me please what can i do????? 

if you like to contact me 
AIM winstnsmith6079

---

### Post by wylfing on 2005-10-10
I don't have any good answers, but a few possibilities: 

(1) You have a bad ISO. Re-download the ISO from a reliable source and check the md5sum to make sure you didn't get something corrupted. (OpenOffice.org has a nice explanation of how to check md5sums under Windows at [http://www.openoffice.org/dev_docs/using_md5sums.html)](http://www.openoffice.org/dev_docs/using_md5sums.html)).

(2) You have a bad burn. Can you reliably burn discs? Is your burner a cheap-o burner or a good one? What software did you use?

(3) You have some bad RAM. Does your BIOS do a RAM check at startup time? Do you regularly have "bizarre" system instability?

---

### Post by sinistermilk on 2005-10-10
thats the thing
i've downloaded both twice on to two different comps and used different burners

is ther anywhere else to get an iso

and it still wont work on this thing

but both lives run fine

---

### Post by wylfing on 2005-10-11
You didn't exactly answer any of the questions I asked :) 

Did you check the md5sum of the ISO? This is pretty important, because it will show if the ISO itself is corrupted somehow.

---

### Post by sinistermilk on 2005-10-11
b9b73ed7aebdd0fdf5bfdfe26d6679de *cd.iso (i did rename it)

what does this mean?

---

### Post by wylfing on 2005-10-11
That's the correct md5sum value for the Breezy i386 ISO. So we know you've got a good image, that's a start. I wonder if you have the drive chipset issues that were discussed in [this thread](http://www.ubuntuforums.org/showthread.php?t=71401). The workaround there is to try to install with a different CD drive if you can.

---

