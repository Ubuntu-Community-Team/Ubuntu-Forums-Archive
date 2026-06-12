---
title: "How do I make folder icons I assigned persist after upgrade from 10.04 to 12.04?"
date: 2013-08-15
forum: Installation &amp; Upgrades
---

### Post by suomalainen on 2013-08-15
Hello,

I'm upgrading from 10.04 to 12.04. I have an external usb hard drive into which I store folders. Each folder has it's own png or jpeg icon that I created for it.

In past experience after an upgrade I always needed to reasign the icons to the folders.

Is there another way to make these icons persist after an o/s upgrade?

Thank you

---

### Post by Frogs Hair on 2013-08-15
If you are referring to emblems the feature was removed by Gnome starting with Nautilus 3 (11.10) . There were or are some program and PPA options  ,but the Blog posts I find go back to 2011/12. The Nautilus emblems package works only in Gnome 2 according the description in synaptic.

---

### Post by suomalainen on 2013-08-16
Thanks for the response Frogs Hair!

Here is what I'm talking about. I have an external usb HDD onto which I save folders. When I right click any folder and choose "properties" I can change the image that is associted to a specific folder. I have made images I can choose from and associate to such folders. The formats of these images can be anything like gif, jpeg or png.

Each time I open the directory on the external HDD I see folders displayed with the images I want.

If I do an o/s upgrade, it has been my experience that the images associated to these folders are lost.

Additionally, if I unplug the usb hdd and go to another ubuntu machine the images also do not persisit.

My question is how I can make them persisit when either changing machines or doing a o/s upgrade?

Thank you very much!

---

### Post by ibjsb4 on 2013-08-16
The only way I have been able to do this is to change the image in the theme folder I am running and then transfer that theme folder to my new install.

/usr/share/icons

I guess to do it right, you need to build your own theme.  I wonder how hard that is.

---

### Post by Frogs Hair on 2013-08-16
> [COLOR=#000000]I right click any folder and choose "properties" I can change the image that is associated to a specific folder.[/COLOR] That description fits an emblem exactly. The feature isn't included by default in Nautilus 3 +.

---

### Post by ibjsb4 on 2013-08-16
> **Frogs Hair said:**
> That description fits an emblem exactly. The feature isn't included by default in Nautilus 3 +.

Got it in nautilus 3.4.2

---

### Post by Frogs Hair on 2013-08-16
Emblems must have come back in 3.4 . There were removed 11.10 and are not present in 12.10 or 13.04 (3.6) by default , but there is a patch for some 3.4 features available for 12.10 & 13.04 . [http://www.webupd8.org/2012/10/how-to-install-nautilus-36-or-patched.html](http://www.webupd8.org/2012/10/how-to-install-nautilus-36-or-patched.html)

12.04 Patch :[http://www.webupd8.org/2012/08/install-solusos-patched-nautilus-in-ubuntu-1204.html](http://www.webupd8.org/2012/08/install-solusos-patched-nautilus-in-ubuntu-1204.html)

So the question stands. I don't know of a way to save the emblem setting during the upgrade and the distribution upgrade from Gnome 2 to Gnome 3 complicates the matter , not to mention an entire replacement of Nautilus.

---

### Post by suomalainen on 2013-08-18
I have an external usb HDD onto which I save folders. When I right click any folder and choose "properties" I can change the image that is associted to a specific folder. I have made images I can choose from and associate to such folders. The formats of these images can be anything like gif, jpeg or png.

Each time I open the directory on the external HDD I see folders displayed with the images I want.

If I do an o/s upgrade, it has been my experience that the images associated to these folders are lost.

Additionally, if I unplug the usb hdd and go to another ubuntu machine the images also do not persisit.
[B][COLOR="#008000"]
Certainly there has to be some file that tells ubuntu what images to associate with what folder each time I bootup?

It might become complicated when un plugging the usb and moving to another Ubuntu machine but I don't see why a set of instructions counldn't be here as well?

How can we make this happen?[/COLOR][/B]

---

### Post by Frogs Hair on 2013-08-18
The video link explains what I meant by emblems  . Changing  folder icon via properties is slightly different and the  images at installation come from usr/share/icons. If a custom image is used _either_ for an emblem or icon the path to the image is established when the user navigates to the folder via properties.

 It is the file path which file manager uses to locate the image , I use some custom Icons and  example might be as follows . home/david/pictures/custom icons/(image name) When upgrading path reverts to default. 

It may be possible to write a script that restores the path/s to a directory/s after the file manager has been upgraded ,but I can't comment on difficulty or complexity . 
[http://www.youtube.com/watch?v=Twz5TUlhtSA](http://www.youtube.com/watch?v=Twz5TUlhtSA)

---

### Post by suomalainen on 2013-08-22
I used gksu nautilus to copy my icons folder into /usr/share/icons and via properties reset the icon for the folder then rebooted but this did not work.

Is having a script writen the only alternative?

---

### Post by suomalainen on 2013-09-26
Hi all,

I'm still trying to find a way in which I can assign an image to a folder and enable that image to stick/persist to that folder forever! I don't like the fact that when I upgrade or re-install o/s over 500+ folders for each machine need to be manually re-assigned.

There has to be a way for the image to stick????

Any ideas?

Thanks

---

### Post by suomalainen on 2013-10-10
bump...

---

### Post by suomalainen on 2013-10-17
bump...

---

### Post by suomalainen on 2013-10-21
I found this link:

[http://ubuntuforums.org/showthread.php?t=1466565](http://ubuntuforums.org/showthread.php?t=1466565)

Which shows a way to save the file/custom icon information but what I want to be able to also do is to disconect the external usd hard drive and carry it to another Ubuntu machine and still have the associated custom icons that I assigned to each folder intact.

It seems that Windows XP, as an example, excels in this area because Microsoft Windows actually creates a file called "Thumbs.db" which is placed in the folder and the icons persists from machine to machine.

Is there a way to tell Ubuntu 12.04 to use the "thumbs.db" file Microsoft windows creates if assigned?

Thank you!

---

### Post by suomalainen on 2013-10-21
I found this link:

[http://ubuntuforums.org/showthread.php?t=1466565](http://ubuntuforums.org/showthread.php?t=1466565)

Which shows a way to save the file/custom icon information but what I want to be able to also do is to disconect the external usd hard drive and carry it to another Ubuntu machine and still have the associated custom icons that I assigned to each folder intact.

It seems that Windows XP, as an example, excels in this area because Microsoft Windows actually creates a file called "Thumbs.db" which is placed in the folder and the icons persists from machine to machine.

Is there a way to tell Ubuntu 12.04 to use the "thumbs.db" file Microsoft windows creates if assigned?

Thank you!

---

### Post by suomalainen on 2013-10-26
bump...

---

