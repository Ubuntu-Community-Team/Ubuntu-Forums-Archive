---
title: "Dual Boot, two hard drives."
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by johniv on 2008-07-02
Hey Everyone!

I need to set up Dual Boot for Ubuntu and Windows Vista.

Ubuntu is on an IDE drive and vista is on a SATA drive. If i set the IDE to boot first, Grub loads and starts Ubuntu but Ubuntu tries to load itself from the sata drive (presumably, just trying some self diagnosis. To my knowledge computers prefer SATA over IDE. also, when i unplug the SATA things work great.) so, i'm stuck on that front (but i assume there's a file to edit in ubuntu to fix this?).

I changed the boot order to SATA first, vista loads fine but i have no option to start ubuntu properly.

So, can someone tell me what to edit in ubuntu to get it to boot properly. OR, if possible, can i get vista to recognize ubuntu.. and will that work properly?

THANK YOU - i know that was a lot to read,
John

---

### Post by tsger on 2008-07-02
I found this link helpful:

[http://linuxmint.com/wiki/index.php/How_to_repair_your_grub](http://linuxmint.com/wiki/index.php/How_to_repair_your_grub)

---

### Post by bondo101 on 2008-07-02
Tried to install 2nd hard drive with vista on first drive so i could use ubuntu on second drive. No vista software to install hd from western digital. Don't want to partion vista drive . Using old machine dual drives with xp and eide drives . Works like a champ. Do not like vista slowly working up to ubuntu 8.04 does rock, better than vista.

---

### Post by johniv on 2008-07-02
I don't know if my grub is broken.. I don't know. 
maybe i'm just not looking in the proper direction.

---

### Post by confused57 on 2008-07-02
> **johniv said:**
> I don't know if my grub is broken.. I don't know. 
maybe i'm just not looking in the proper direction.
When your computer boots into the grub boot menu, highlight your first Ubuntu entry, press "e", highlight the line with root, press "e" again, change root from (hdx,y) to (hd0,y), press "enter", then "b" to boot...this is temporary if it works, but you can make it permanent in your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
you would also need to change the line with #groot to the correct value.

---

### Post by johniv on 2008-07-02
Hey confused57!

I've got alot of experience with variables, so i need to ask if you actually want me to write (hd0,y) or whether you meant to have me leave the current number. 

currently in menu.lst i have (i haven't changed anything):
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5c165038-b674-485d-917a-c46856542209 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

under the first entry

Thank you

---

### Post by DeaconBlues on 2008-07-02
johniv: it is a very good idea to burn a copy of the Ubuntu live CD and keep it for when something goes wrong. It will let you boot Ubuntu and fix your master boot record. You can even surf these forums with the disc to look for advice. It has saved my installation a couple of times. :lolflag:

Maybe you knew that already but I just thought I'd mention it incase you didn't.

Im also experiencing problems with dual-boot, but my setup is a bit more complicated because I wanna get RAID-0 working. Here is my thread:

[http://ubuntuforums.org/showthread.php?t=842386](http://ubuntuforums.org/showthread.php?t=842386)

---

### Post by confused57 on 2008-07-02
> **johniv said:**
> Hey confused57!

I've got alot of experience with variables, so i need to ask if you actually want me to write (hd0,y) or whether you meant to have me leave the current number. 

currently in menu.lst i have (i haven't changed anything):
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5c165038-b674-485d-917a-c46856542209 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

under the first entry

Thank you

Sorry, I should have clarified that y means to leave the current number as it is, e.g. (hd0,0).

Also, as was mentioned, you can try reinstalling grub's IPL to the mbr, using the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Added:  Another possiblity is to boot Ubuntu from Vista, using EasyBCD, however grub's IPL needs to be installed to Ubuntu's root partition, using the Ubuntu live cd.  From the link I gave you above, you'd need to do something like:
```
root (hd0,0)
setup (hd0,0)
```

If you decide to try using Vista to boot Ubuntu, when Vista hands off to grub, you may need to use the "e" method I described earlier & change root from (hd0,0) to (hd1,0).

Link to EasyBCD:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

