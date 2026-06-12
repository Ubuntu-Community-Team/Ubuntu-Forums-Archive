---
title: "A boot loader question... so very confused!!"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by NateDogg on 2008-07-20
All, 

this may be a simple question for the gurus out there.

I have a happy XP/Vista dual boot. i saved extra room for Ubuntu as i really want to get into it. i'm doing the install, and have set up the partitions ready to go.

my question: 

in the Advanced button on the "Ready to install" page it has a tick next to Install boot loader, and has hd0 for the device.

I have 2 HDs. one is used just for data, the other is my triple boot HD. hd0 i assume corresponds to sda in the drop down list, and this is the DATA HD. i want the boot loader on the triple boot HD.

My options are as follows:

/dev/sda          ATA blahblahblah (465 GB) <-my data drive
/dev/sda5
/dev/sda2
/dev/sdb          ATA MAXTOR blahbl (232.9 GB) <- my triple boot
/dev/sdb1          Windows Vista/Longhorn (loader)
/dev/sdb2
/dev/sdb3
/dev/sdb-1

The question is simple. Which one do i select? I'm really confused... Is it /dev/sdb, /dev/sdb1 or /dev/sbd3 (the one where i am installing the ubuntu OS)...

So confused...

---

### Post by logos34 on 2008-07-20
'(hd0)' is whatever the Bios boot drive is--in your case sdb. 

When in doubt you can also replace it with the '/dev/sdx' format.  

So the default or /dev/sdb should put grub on the MBR of the 232 gb drive

---

### Post by NateDogg on 2008-07-20
hmmm... this didn't end well... i selected /dev/sdb. grub loads ok, and gives the Ubuntu options plus the Windows/Longhorn loader. based on instructions i have read i expected it then to load the Vista loader and present my dual boot windows options. Instead i get

Starting up ...

and it just sits there.

any troubleshooting thoughts? i was sensible enough to image my machine, so i'm not overly concerned about the rebuild, but i'd rather have it working and start playing with Ubuntu than rebuild it...

If i clikc the Ubuntu kernel to load i get 

Error 22: No such partition
Press any key to continue.

something sure didn't work right :P

---

### Post by logos34 on 2008-07-20
Reboot to the grub menu, press 'e' to edit highlighted ubuntu selection, 'e' again on the 'root' line and change from (hd1,2) to (hd**0**,2) [assuming root = sdb3].  Then 'b' to boot.  If successful, make the change permanent:

gksudo gedit /boot/grub/menu.lst

-change all root lines + 'groot' (near the top)

windows should be root (hd0,0)

---

### Post by NateDogg on 2008-07-20
this mainly works now! sure is better than where i was.

i think it may have done something funky to the windows loader though...

Ubuntu boots fine.
If i select vista/lonhorn that goes to the loader fine
Vista boots fine from in the loader
But... XP doesnt boot at all, it just reboots the machine back to grub each time...

damn! so close!

---

### Post by logos34 on 2008-07-20
> **NateDogg said:**
> this mainly works now! sure is better than where i was.

i think it may have done something funky to the windows loader though...

Ubuntu boots fine.
If i select vista/lonhorn that goes to the loader fine
Vista boots fine from in the loader
But... XP doesnt boot at all, it just reboots the machine back to grub each time...

damn! so close!


Glad to hear it worked.  

Are you choosing XP from the Vista bootloader menu or are you trying to boot directly into it from a separate XP entry in grub?

---

### Post by NateDogg on 2008-07-20
vista boot loader. the instructinos i found on various reputable sites for triple boot talk about it that way. one thing is clear, it does mess with the Vista Bootloader.

after i got into Vista, i fired up VistaBootPro (a free utility to help modify BCDEdit in a GUI, as that really sucks on it's own in windows). it stated that the bcd registry was corrupt.

not only that, but reinstalling the backup errored out and didn't work.

the strange thing is i had already modified it to default to XP, and changed the timeout. those settings remain even though proboot says the BCD is corrupt...

i'm posting on the proboot forums to see if anybody there has a solution, as the FAQs and manual's described fix doesn't work in my case.

so close... 

do you have any other thoughts logos? a different way i might be able to get it going perhaps?

---

