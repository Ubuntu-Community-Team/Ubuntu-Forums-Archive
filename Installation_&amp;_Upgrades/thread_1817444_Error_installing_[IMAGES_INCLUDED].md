---
title: "Error installing [IMAGES INCLUDED]"
date: 2011-08-03
forum: Installation &amp; Upgrades
---

### Post by Zero Hack on 2011-08-03
[IMG]http://s4.postimage.org/5dssruh3v/P030811_1557.jpg[/IMG]



I did have Combofix installed I have just uninstalled it. The USB version doesn't seem to boot either. Any ideas?

---

### Post by jerrrys on 2011-08-03
are you set up in bios to boot from usb?

---

### Post by Zero Hack on 2011-08-03
Thats currently being booted via a disk sir.

---

### Post by Blasphemist on 2011-08-03
Try attaching your images using the paperclip icon and through that dialog uploading the image. I can't see any image in your post now.

Also, provide any and all detail of what you experience with this issue.

---

### Post by Zero Hack on 2011-08-03
Attached image is below.

I just made a installation disk and got this. USB wont boot even though USB legacy is enabled.

---

### Post by jerrrys on 2011-08-03
this is a built in cd drive and not a usb port?

---

### Post by Zero Hack on 2011-08-03
It's a built in DVD drive. It works perfectly and has worked with Ubuntu before.

---

### Post by jerrrys on 2011-08-03
your screenshot indicates that your computer is trying to access the HDD and not the CD/DVD

---

### Post by Zero Hack on 2011-08-03
Its on my SATA port 2 since SATA port 1 broke I snapped the socket off the motherboard.

---

### Post by jerrrys on 2011-08-03
would you please post the make and model of your computer

---

### Post by Zero Hack on 2011-08-03
HP **Compaq Presario Media Center** SR2020NX
Is my computer.

---

### Post by jerrrys on 2011-08-03
and you problems started when port 1 broke?

---

### Post by Zero Hack on 2011-08-03
Well my computer worked fine with the Ubuntu disk on port 1 and I never tried it on port 2 so I suppose so.

---

### Post by Blasphemist on 2011-08-03
Does your bios allow you to set your boot to the second hard disc? I think the bios may see sata2 as a hard disc for booting or at least that's worth a try. Your screenshot indicates its trying to boot external drives starting with sdc.

---

### Post by jerrrys on 2011-08-03
this is bringing me back to BIOS again.  can you look thru BIOS and see if any options exist to maybe disable port #1

---

### Post by Zero Hack on 2011-08-03
I can disable SATA 1 controller or somthing around that..

---

### Post by jerrrys on 2011-08-03
ok, go ahead and give it a try.  if this does not work, just go back into bios and change it back to the way it was.

EDIT:  its lunch time here; so see ya after lunch...

---

### Post by Zero Hack on 2011-08-03
Didn't work just says Error finding DISK or something like that.

---

### Post by jerrrys on 2011-08-03
[COLOR=#000000][FONT=Sans Serif]ok; starting to run low on ideas here.[/FONT][/COLOR]
 
 [COLOR=#000000][FONT=Sans Serif]just want to verify that this is the tab on the mother board that is broke and not the connecting cable going to the drive.[/FONT][/COLOR]
 
 [COLOR=#000000][FONT=Sans Serif]from what i can make of your computer specifications you have 1.0 thumb drive (flash drive) plugin. what i cannot determin is if you can boot from flash drive. once again this would be an option in bios, if it exist. if it did exist, you would have to load ubuntu to a flash drive to install.[/FONT][/COLOR]
 
 [COLOR=#000000][FONT=Sans Serif]your hdd also seems to be broke at the moment and of no use in repairing your computer.[/FONT][/COLOR]
 
 [COLOR=#000000][FONT=Sans Serif]one other thought would be to remove the HDD and place it in another computer for repair. however if you are not skilled at this, you could end up with two broke computers.[/FONT][/COLOR]
 
 [COLOR=#000000][FONT=Sans Serif]and last thought, would be to take it to a repair shop.[/FONT][/COLOR]

---

### Post by Zero Hack on 2011-08-03
The hard drive works perfectly fine as I'm on windows right now it's just I need Ubuntu installed along side windows or I can forget windows I mean I don't care I just need to get the dam thing installed.

---

### Post by Zero Hack on 2011-08-03
I can also boot from USB my computer supports it.

---

### Post by jerrrys on 2011-08-03
then do a usb install

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by Zero Hack on 2011-08-03
I tried it doesn't even have anything on the ISO no auto run no .exes or anything. It was just a bunch of folders and like 3 files and then all the folders.

---

### Post by jerrrys on 2011-08-03
unetbootin?

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Zero Hack on 2011-08-03
I have used Netbooting.

This is what my USB looks like

[http://prntscr.com/2il6c](http://prntscr.com/2il6c)

---

### Post by jerrrys on 2011-08-03
is this what the first download window looked like?

[ATTACH]199178[/ATTACH]

---

### Post by Zero Hack on 2011-08-04
Well I build computers for a living and I own a data center I popped down around 3AM to the data center and got out some spare parts I completly rebuilt my computer from scratch with a new motherboard since the old one needs repairing. I also fixed it the disc I was using didn't have all the files successfully burned and the script did not know where to get the hard drive from. I tested it on my old motherboard with a new burnt disk and worked perfectly but still I upgraded my PC so it works fine now.

---

### Post by jerrrys on 2011-08-04
extremely glad to hear that zero hack.  please mark your thread as solved (thread tools)

---

