---
title: "Ubuntu 10.04 desktop - printing problem with HP printer"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by srayju on 2010-05-28
[B]This is to report that Ubuntu 10.04 desktop version has
the identical problem with 
HP P1505n  -   as in ubuntu netbook release.
[/B] 			
 			 			 		   		 		 		It happened with several desktops after upgrading to Ubuntu 10.04.

HP P1505n  Network printer - set up went okay.
But problem while printing.
Error message on screen, and blank output.
Please help.

The printers make a clicking noise (twice in quick succession)
after the print job is submitted. Then does not do anything.
And an error message pops up.

Thanks,
S Ray

---

### Post by wkulecz on 2010-05-28
Similar problem with networked HP LaserJet 4200n  although the Dell 3100-cn and HP P2055dn on the same subnet appear to be working fine (I don't print a lot so there still could be subtle bugs printing things more complicted than a web page).

---

### Post by David006 on 2010-06-08
Have been experiencing similar issues.  Worked intermittently when first installed 'HP LaserJet P1505n' printer (using USB).  Then worked (mostly) after couple of restarts and also Ubuntu updates.  Starts to print after around 12-15 seconds, and print quality made me suspect toner-cartridge was faulty.

Then tried on same PC, cabling, but under XP SP3 - with excellent print quality and near-instant printing.


Have now installed 'HPLIP 3.10.5' (Ubuntu 10.04 has 3.10.2)
  [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

Fairly tedious, and cumbersome.  Still needed to delete and re-created printer to print.  Would fail with:
  **** Unable to open the initial device, quitting.

Works much better, as fast as under XP but (so far) not quite same print quality.

---

### Post by gusul on 2010-09-24
Hi,

I am having a similar problem with a HP printer. Problem started after a system update. Previously worked OK. Do you have a solution?

---

### Post by sten_gn on 2010-09-27
I to have problem with printing:
Fresh install -fully patched
Ubuntu 10.04 - hplip 3.10.2 and 3.10.6 (tryed both)
HP LaserJet 1020 USB

It worked on Ubuntu 9.10 - hplip 3.9.12

At best i could print once from gedit and firefox.
Later printer was only pooling paper in constantly till end of paper in slot.

Or in case of hplip 3.10.2 fail to install plugin 3.10.2.
Or in case of hplip 3.10.6 every time had to install plugin 3.10.6

I tested many ways and variations of installing printer but nothing works. In Win XP it works fine.

I suspect that fault is rather in system than in hplip 3.10.2 and up.
:confused:

---

### Post by foresthill on 2010-09-28
Try this:

[http://ubuntuforums.org/showpost.php?p=9570416&postcount=4](http://ubuntuforums.org/showpost.php?p=9570416&postcount=4)

Or alternatively, you can go back to 9.10 like I did, simply because printing is something I need to do every day without having to endure so much f-ing drama just to print a simple PDF file.

And besides, 10.04 offers very few added features over 9.10, at least as far as I can see. It is slightly prettier though. :)

---

### Post by sten_gn on 2010-10-03
I did some tests and seems to me that HPLIP 3.10.X might be broken.
I installed U 9.10 with hplip 3.9.12 and HP 1020 works.
But i can't use 9.10 because there is an issue with mobo Atom D945 GCLF2
after installing last updates i can't fully switch off PC.

Right now i test U 10.04 with hplip 3.9.12 and so far it seems that hplip does not see usb printer HP 1020. 

No luck jet.

---

