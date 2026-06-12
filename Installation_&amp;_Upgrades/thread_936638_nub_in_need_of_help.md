---
title: "nub in need of help"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by klambert on 2008-10-03
cant install it, i just installed it with this same disk on a different computer like 2 days before i tryed on this and so i know the disk is good. but when i put it in my desktop (which is a built one, so that might be my issue?) it tells me it has a revalidation error and i do not know what to do, any advice?

---

### Post by Partyboi2 on 2008-10-03
Try passing all_generic_ide as a boot option. You can do this by pressing F6 at the main menu screen and adding ```
all_generic_ide
``` to the end of the line.

---

### Post by klambert on 2008-10-03
tryed that, it still says rebvalidation failed (errno=-5)

---

### Post by Partyboi2 on 2008-10-03
The only other thing I can think of at the moment is to try```
acpi=off
``` as a another boot option. Add it the same way as you did the last.

---

### Post by klambert on 2008-10-03
ok now im getting a message MP-BIOS bug:8254 timer not connected to IO-APIC

thats without trying anyhting, just a straight run off the cd...i put in the alternate disk to see and it gave me the error long enough to read, its been giving me that for a while on the other disk...

---

### Post by klambert on 2008-10-03
ok i tryed the APIC=off thing, and it got further this time, it got to where it says ubuntu with the bar scrolling accross and the bar goes across 3 times then freezes in the middle and wont move

---

### Post by klambert on 2008-10-03
i;m off to bed, but now i erased the quiet and splash from the boot thingy and now its telling me qc timeout (cmd 0x27(
failed to read natice max address (err_mask=0x4)

and then it repeates that a few times and then says a whole bunch of stuf about IRQ#17 and sayts its dissabling it then a whole bunch more stuff...but never boots

---

### Post by klambert on 2008-10-03
ok so now it seems that any time i turn the acpi off it will goto the screen where the bar goes across the page, but no matter what else i do, it always hangs up

---

### Post by klambert on 2008-10-03
i've even searched the forums and so far people have been able to fix what seems to be my problem by changing their sata thing in bios, but i have no sata in my bios, my computer is almost 6 years old and they didnt have sata back then

---

### Post by klambert on 2008-10-03
anybody have any advice? im completely stumped on this

---

### Post by Sef on 2008-10-03
1) Post your hardware specs.

2) Instead of booting or installing, go down the list to 'Check Disk for Errors', maybe your disk has gone bad since you last used it.

---

### Post by klambert on 2008-10-03
hmmm ok my specs...

motherboard is asus a7v8x
amd athlon 1.7 ghz
ram is cheap *** ram from best buy old ddr...2 sticks of 512 mb
HD 1: WD120 gig
HD 2: WD40 gig

thats all the relavant things i can think of if i missed something, or something doesnt look right let me know and ill run and double check it.

i cant check disk for errors, it wont work, gives same error, and ive tryed the alternate disk, and burned another standard one and they do the exact same thing so its not the disk

---

### Post by Braytok on 2008-10-03
I had a similar issue awhile back. the install worked fine on a number of systems but then on another it didn't. Turns out it was a defective CDROM drive.

I also had reports of bad power supplies causing problems.

Something else you could try is burning the .iso at a slower speed.

---

### Post by klambert on 2008-10-03
ok so heres an update of something i have discovered...using the same disk as with my desktop i put it in my laptop and i am doing this through ubuntu as i type this, so its not the disk i wouldnt think, considering it booted just fine and im able to get on the internet and do everything.  as for a bad cd rom drive, it shouldnt be, i use that disk drive for gaming and some other stuff and it has never given me fits before, so i dont think itss that, and i boot up into windows and it works fine.  as for power supply, just replaced less than 6 months ago...doubt its that.

also, first disk i tryed i burned the iso at 52x and the second one i burned at 24x so it is at a slower speed

my cd rom drive is only about a year or 2 old, and its a top of the line memorex that they offer as far as cd roms/cd burners, so i wouldnt think it would be that

---

### Post by klambert on 2008-10-05
anybody help?

---

### Post by Braytok on 2008-10-06
I can understand your frustration. I have had almost identical experiences. for instance. I have a samsung DVD DL-RW drive that works fine with windows and even installed Ubuntu with it but from time to time it would flake out on me. I swapped it out with an LG drive I had and the disk that wouldn't work previously in the Samsung drive suddenly would in the LG drive.

Also I would recommend burning the ISO at about 16X. I know that seams god awful slow but it just might help. Another thing worth mentioning would be to use the more expensive disk like Sony. I've burnt many coasters using Maxell and Memorex blanks. somthing about the chemicals they use being of lower quality. 

If all else fails check th Ubuntu Hardware compatibility list
[http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)
I could be that Ubuntu just doesn't like your Drive.. :(

and...if that also fails....

Try a big hammer?:lolflag:

---

