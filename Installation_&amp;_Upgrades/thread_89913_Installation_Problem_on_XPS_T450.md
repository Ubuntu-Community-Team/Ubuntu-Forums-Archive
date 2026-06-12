---
title: "Installation Problem on XPS T450"
date: 2005-11-13
forum: Installation &amp; Upgrades
---

### Post by xozdude on 2005-11-13
I downloaded the LiveCD ISO of Ubuntu, and burned it to a CD using Windows XP CD burner.  When I put the CD-R into the XPS, and try to boot, it completely ignores the CD Drive even though i configured the CD drive as the first boot device in setup.  How can i run LiveCD???? (NOTE: I know almost nothing about Linux.)
I downloaded the i386 version.

---

### Post by xozdude on 2005-11-13
Can someone please help me?????

---

### Post by xozdude on 2005-11-23
UPDATE: I tried burning it to a CD-RW using Sonic RecordNow! and it still won't work. :mad:

---

### Post by yesplease on 2005-11-23
Did you burn your CD as an image? See [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2455487](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2455487)

It also may help to burn slow.

---

### Post by xozdude on 2005-11-24
There is no Burn Image button in RecordNow.  There's a "Make this CD/DVD bootable button, but Sonic Tech support said i didn't need this when burning an ISO.  I will try a slower burn speed.

---

### Post by xtacocorex on 2005-11-24
[http://www.cdburnerxp.se/](http://www.cdburnerxp.se/)

This is a free Windows CD Burner that supports writing .iso image files.

When the program opens up, there will be an option window, select the top option, then go to file, then click 'write cd from image' (or something to that affect, I have the program at work) and then when the burning window opens up, browse to the cd image. Don't worry about making it a bootable cd.

Hope this helps.

Edit: This method has worked for me burning Kubuntu Hoary, FC4, and the Live CD for Symphony OS Beta 1 Preview 1.
I also use the boot menu from the bios to get it to boot from a cd on my laptop.

---

### Post by yesplease on 2005-11-24
You need a bootable install CD, so the make bootable option seems logical to me. However, I do not have the manual for this program, but perhaps the manual can give you pointers on how to proceed :)

---

### Post by veloct on 2005-11-24
google burning iso's with windows.  MS has a free powertool that burns iso images.  That's how I burned my CD's when I switched to Ubuntu.

---

### Post by tokyovigilante on 2005-11-24
There is an important difference between burning an ISO image and the bootable CD option in Nero/Sonic etc. Burning an ISO creates an exact copy of the original CD the image was taken from, and if that CD contained boot code then you'd be away without further ado. 
The bootable CD option just copies the files without any additional filesystem or boot code, then creates a separate partition which pretends to be a 1.44Mb MS-DOS boot floppy, which tends to not be compatible with a linux installer ;)

The [ISO Recorder Powertoy]("http://isorecorder.alexfeinman.com/isorecorder.htm") for XP by Alex Feinman is the easiest (free!) option assuming you have XP, once its installed a right-click on the .iso gives you a Copy to CD option and you'll be sorted.

---

