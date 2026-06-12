---
title: "cant boot from cd... but should be able to"
date: 2006-07-20
forum: Installation &amp; Upgrades
---

### Post by jmilane on 2006-07-20
I have it set in the bios to boot from cd, but it is just booting in windows like always.

This happens with 2 copies of Ubuntu install that I made (one backup just in case) and the first disk of a Fedora install disk set as well.

The CD drive works. I can see the file on there, just cant boot from it.

Any ideas? I sure didnt get very far without a problem!

Thanks,

J

---

### Post by madmetal on 2006-07-20
if it doesn't boot from cd do it manually.
while booting find something like " press F11 to enter boot menu" then choose cd manually.

---

### Post by az on 2006-07-20
Or edit the bios setting for "boot order" and have it try to boot from cd before the hard drive.

---

### Post by jmilane on 2006-07-20
I did both of those things. It acts like all is well, but then ignores me and Windows comes up.

---

### Post by jmilane on 2006-07-20
I have two machines here. They are both doing the same thing with both copies of Ubuntu as well as the copy of Fedora.

I bring up the boot menu, I tell it to boot from the CD, then Windows 2000 Professional comes up.

I dont get it. I dont know what to do now.

---

### Post by az on 2006-07-20
> **jmilane said:**
> I have it set in the bios to boot from cd, but it is just booting in windows like always.



Sorry, I didn't notice you had already mentioned that.

> **jmilane said:**
> 
The CD drive works. I can see the file on there, just cant boot from it.

Exactly what files do you see?

---

### Post by jmilane on 2006-07-20
On the cd, I see the .iso file.

...desktop-i386.iso

---

### Post by OctopusTwo on 2006-07-20
Try these steps in order.  
First did you ensure it is a bootable disc?  Thier should be more files on the CD beside the ISO.  If you just see the ISO that is your issue.

Is your drive trying to read the CD?  Is your HDD trying to read the disc?  (LED blinking)  You should say an interaction between your CD LED light and HDD light.

Try downloading the alternate (not live) version and install using the OEM or text style.  Which ever you feel more confortable with.

---

### Post by Ptero-4 on 2006-07-20
Hi. Your problem it seems is that you burned the CD as data CD. To burn a bootable install disc you need to access a special option, something like "copy disk image" or something like that, this option brings a dialog box from where you select the iso image you want to burn, then it asks for a blank CD and begin burning. The result wil be a CD with several files and folders in it.

---

### Post by jmilane on 2006-07-20
YES! I see just the .iso...

Now I am excited.

What else should be on there?

It IS seeing the CD. The lights come on during boot. It just doesnt care. 

I dont understand this: 

"Try downloading the alternate (not live) version and install using the OEM or text style. Which ever you feel more confortable with."

But maybe the other files that should be on the cd will help?

---

### Post by jimmygoon on 2006-07-20
It sounds as if you burned the CD incorrectly. If all you see on the disc is the ISO file then you did. You should have burned it as an image with some utility like Nero or Roxio with a Burn ISO command... That way there will be tons of files on the cd..

The ISO file is actually an image of the CD and is does no good to you in that form, and you have to burn it *as an image* to the CD... Its kinda like a ZIP file but the way you get the files out is to burn it in that special way.... What do you use for your CD burning software

---

### Post by jmilane on 2006-07-20
All I did was download that .iso file and burn it to cd. I didnt see instructions that stated otherwise.

---

### Post by jmilane on 2006-07-20
Okay. I needed an .iso burner.

Doing that now.

Im kind of slow.

Sorry.

JD

---

### Post by az on 2006-07-20
This is a very very common hurdle that people have to face.  You are not alone.

Millions of geeks are brought to their knees every day, crying "but it's *free!*  Just *download* it!", frustrated at people who will not give free-libre open-source software a chance, not realising that simple things are not simple things.  

Stuffing them into magazines doesn't work either.  (cds, not geeks...)

Ubuntu was the first distro to provide free cds.  I think that is something very simple that caught a lot of people's attention and helps Ubuntu become very popular very quickly.

---

