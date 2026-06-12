---
title: "load kernel"
date: 2011-09-27
forum: Installation &amp; Upgrades
---

### Post by vas75 on 2011-09-27
i have instal ubuntu 11.04 in my laptop and when i boot to the ubuntu it becames the following message. ( YOU HAVE TO LOAD KERNEL FIRST)what i must do ?

If anone now please contact.

---

### Post by MAFoElffen on 2011-09-27
> **vas75 said:**
> i have instal ubuntu 11.04 in my laptop and when i boot to the ubuntu it becames the following message. ( YOU HAVE TO LOAD KERNEL FIRST)what i must do ?

If anone now please contact.
Welcome to Ubuntu Forums!

Can you get to a Grub Boot Menu?

Is Ubuntu the only OS on that laptop?

Did you install from a LiveCD or LiveUSB?  Did you use the "TRY" menu option to verify that your laptop ran Ubuntu?

---

### Post by vas75 on 2011-09-27
i use windows xp sp3 
how can i get to grub boot menu?

---

### Post by collisionystm on 2011-09-27
> **vas75 said:**
> i use windows xp sp3 
how can i get to grub boot menu?

Keep tapping the up arrow key as the system boots. It will interrupt the boot process at the grub menu.

---

### Post by drs305 on 2011-09-27
Normally you can get to it by holding down the SHIFT key during boot. But you have a problem with the Grub menu so even after you see the menu you probably won't know how to fix it (unless you have more than one Ubuntu kernel option to try).

The best way for us to help is to download and run the Boot Info Script after booting the Ubuntu LiveCD. Then post the contents of RESULTS.txt  This file will contain a lot of information about the status of your boot files and let us see where the problem is.

You can get the script by clicking on the "BIS" link in my signature line.

---

### Post by MAFoElffen on 2011-09-27
If you can run Ubuntu from a LiveCD image:

Instructions quoted from oldfred:
> 
If not post this from liveCD:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file  and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New  Reply Edit toolbar and then paste the contents between the generated [  code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible.  New Version is a zip file that you have to extract to get .sh to run.
That will give us an idea of what is there, installed how and the general layout...

EDIT- LOl, drs305 beat me to it... +1

---

### Post by vas75 on 2011-09-27
i will try it and let you know . thanks for help.

---

