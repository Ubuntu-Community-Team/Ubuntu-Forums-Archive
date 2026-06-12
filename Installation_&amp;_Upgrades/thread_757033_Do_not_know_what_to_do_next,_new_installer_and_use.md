---
title: "Do not know what to do next, new installer and user of Ubuntu"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by agrab0ekim on 2008-04-16
I have come up to a brick wall right away in my attempt to add ubutnu to my computer. After downloading the ISO i have atempted time and time again to burn it as an image to disc, all the times, the disc is not a bottable one nor is it one i can load from the computer panel (shows up like it was a data disc, even though i know i burned it as an image)
i am at a loss and am about ready to give up on linux because it is too hard. How can i fix this?

---

### Post by pytheas22 on 2008-04-16
Windows XP (maybe Vista too?) doesn't know how to properly burn an ISO file to a disc, so you need to use a third-party tool.  I would suspect that this is what the problem is.

A good free program is [http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm) .  After installing it, you can simply right-click on the ISO file and select burn to CD.

---

### Post by agrab0ekim on 2008-04-16
> **pytheas22 said:**
> Windows XP (maybe Vista too?) doesn't know how to properly burn an ISO file to a disc, so you need to use a third-party tool.  I would suspect that this is what the problem is.

A good free program is [http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm) .  After installing it, you can simply right-click on the ISO file and select burn to CD.

ISO recorder would not recognize my CDdrive, did it using IMGBURN

---

### Post by pytheas22 on 2008-04-16
> ISO recorder would not recognize my CDdrive, did it using IMGBURN

So you made sure to burn CD as an image, not data, and it still doesn't work?  The only suggestion I have is to try burning the CD on another computer; maybe there's some problem with your configuration.  When I still used Windows, I never had problems creating bootable CDs using ISO Recorder; unfortunately I have no experience with IMGBURN.

Also, another option is to use wubi, [http://wubi-installer.org/](http://wubi-installer.org/)  It allows you to install Ubuntu from Windows without needing to burn an Ubuntu CD.  It's still sort of beta so don't be surprised if it doesn't go perfectly smoothly, but it's worth a try.

---

### Post by agrab0ekim on 2008-04-16
> **pytheas22 said:**
> So you made sure to burn CD as an image, not data, and it still doesn't work?  The only suggestion I have is to try burning the CD on another computer; maybe there's some problem with your configuration.  When I still used Windows, I never had problems creating bootable CDs using ISO Recorder; unfortunately I have no experience with IMGBURN.

Also, another option is to use wubi, [http://wubi-installer.org/](http://wubi-installer.org/)  It allows you to install Ubuntu from Windows without needing to burn an Ubuntu CD.  It's still sort of beta so don't be surprised if it doesn't go perfectly smoothly, but it's worth a try.

how does that one work exactly (the instal without CD)

the problem is, my other computers dont have burners that work anymore (old computer, kept as data storage, servers, and backups if need be)



actually, side not... upon looking at it, i was using Infrarecorder that wouldnt find my CD drive... I downloaded ISO last night, installed it, and it is now nowhere to be found on my computer... what folder would it hide in

---

### Post by pytheas22 on 2008-04-16
Also, a second option to install Ubuntu without burning a CD is [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)  This is different than wubi, which doesn't actually install Ubuntu to a separate partition; UNebootin will, so your installation will be exactly like one from a regular Ubuntu CD.  Either way, both programs should give you a working Ubuntu system.

---

### Post by pytheas22 on 2008-04-16
>  I downloaded ISO last night, installed it, and it is now nowhere to be found on my computer... what folder would it hide in

I don't know where it actually installs--I can't find it here on my machine at work, which runs Windows--but if you right-click on the icon for the ISO file, the first item in the list should say "Copy image to CD."  Does it?

As for wubi, I've never used it so I'm not sure exactly how it works, but basically I think it creates a disk image on a disk inside Windows and installs Ubuntu to that, by automatically downloading all of the packages you need.  I'm not sure how exactly it runs, but it should all be explained on the project's website.

EDIT: actually I did find ISO Recorder; apparently it's under C:\Program Files\Alex Feinman\ISO Recorder.  However there's no executable there so I guess the only way to actually run the program is by right-clicking on the ISO image icon.

---

### Post by tj111 on 2008-04-16
I use [CDBurnerXP]("http://cdburnerxp.se") (free as in beer) for all my cd burning on windows.  It has native ISO support, and by default will burn the image to the disc, not the image file.  Don't check the "make bootable" option though, as that information is already contained in the image file.  It has an interface very similar to K3b.

---

### Post by agrab0ekim on 2008-04-16
GOT IT WORKING

turns out that it does not burn properly to DVDs... put in a CD (ran out of DVDs... wasted money) and it is working


WOOOOT

sorry to bug you all

---

