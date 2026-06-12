---
title: "Boot Help - Invalid keyboard code specified"
date: 2005-11-22
forum: Installation &amp; Upgrades
---

### Post by PizzaLover on 2005-11-22
Hi there. I am trying to get Ubuntu5.10 to work on my computer. I have burnt both a LiveCD and an Install CD and both have the same problem when I try to boot via CD-ROM. 

This is what happens on boot:

A:\> mode con codepage prepare=((850)ega.cpi)

MODE prepare code function completed

A:\> mode con codepage select=850

MODE prepare code function completed

A:\> keyb cf,,keybrd3.sys
Invalid keyboard code specified


Please help me out. I'm completely new to Ubuntu and I'm sure it's a very minor issue. Thank you!! :)

---

### Post by oskude on 2005-11-22
hmm,

"A:\" aint linux :) (take your MS boot floppy out!)

have you activated "boot from cdrom" in your bios ?

---

### Post by PizzaLover on 2005-11-22
I was wondering why it was reading the Floppy Directory but there is no floppy in the drive. And yes, I tried setting my boot sequence to CD-ROM - IDE - Floppy but still no luck. 

Any suggestions??:confused:

---

### Post by yesplease on 2005-11-22
Did you burn the iso as an image? (I ask this because it seems like the CD does not boot)

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2455487](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2455487)

---

### Post by PizzaLover on 2005-11-22
Hey man, I have no idea I just burnt it as a BootCD... I'll research burning an .iso as an image and get back to you... Thanx

---

### Post by oskude on 2005-11-23
your burn program should have a menu option something like "burn image"...

---

### Post by PizzaLover on 2005-11-23
Yea. I found out how to burn the images now... rather than just put them on bootable CDs :). But now there is another problem. On the LiveCD, I get to the point where it loads a long list of things. It gets to the point where its loading the Hotplugs and then just freezes. I then try running the install cd and I get to the point of partitioning the drive and then it tells me it needs 24gb or 65% of my HD, how is it needing that much space?

I'd rather get the LiveCD to work that get another HDD....

---

### Post by yesplease on 2005-11-23
There is an option to partition manually. You can select the partition you want to resize and tell it how far you want to resize it. Then you select the empty space and let ubuntu partition it (or partition it yourself. Did you defragment windows? Did you check how much space is left?

---

### Post by PizzaLover on 2005-11-23
I tried doign it manually but it still said I have not enough space... I HAVE 14gb FREE... I'm not trying to install windows XP professional 6 times, all I want is linux :| 

Thanks for all the help you guys offer though, we are getting somewhere.

---

### Post by yesplease on 2005-11-23
14 BG is enough. Can you select that during install and let ubuntu partition it?

---

### Post by PizzaLover on 2005-11-23
Yeah, I'll give it a try later on but right now I gotta head off to school. 

Thanks again, have a good day!

---

### Post by PizzaLover on 2005-11-23
For now I just want to get the LiveCD to work before I try install the OS on my computer. I am still getting to the point where it goes:

xxxxxxxxxx.... OK
xxxxxxxxx... OK
xxxxxxxxxxxxxx...OK
etc.
Starting Hotplug Subsystems... **And then it just hangs up**

Does it regularly take more than 10 minutes to do that step? Or is something wrong with the .iso or CD?

---

### Post by yesplease on 2005-11-23
Could be something wrong with the CD. There are ways to verify your CD. 

However, you have 16GB free, and I would just install. It wont break your system if that goes wrong. Did you backup your files?

---

