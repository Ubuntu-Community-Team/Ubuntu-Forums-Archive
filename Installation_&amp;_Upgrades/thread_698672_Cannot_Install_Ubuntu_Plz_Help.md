---
title: "Cannot Install Ubuntu Plz Help"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by hduong01 on 2008-02-16
Hi Everyone, I'm currently new to Ubunto.  

I downloaded the ubuntu 7.10, burned it onto a cd and had a successful run on my hp dv2120ca.  However, when I tried to install it on my desktop errors occurs.

The screen pops up, with option, so i select start and install.
Ubuntu load but than comes errors it say.

(initramfs) [150.555266] ata2.00: exception Emask 0x0 sAct 0x0 SErr 0x0 action 0x2 Frozen

[IMG]http://i210.photobucket.com/albums/bb9/run8888/IMG00055.jpg[/IMG]
[IMG]http://i210.photobucket.com/albums/bb9/run8888/IMG00054.jpg[/IMG]

Can someone plz help me out, thanks

---

### Post by Pumalite on 2008-02-16
Did you do an md5sum on the iso, burn at 4x or less in good quality CD-R media and check CD integrity before install?

---

### Post by hduong01 on 2008-02-16
i'm using the same cd that's been used to install on my laptop, but i'll try to burn it with 4x to see if it work

---

### Post by Pumalite on 2008-02-16
If that's the case; check your burner too. Clean the lens, etc.

---

### Post by hduong01 on 2008-02-16
i'm using nero to burn the cd, i'm redownloading and reburning it with 4x let see if it works.

when i boot up with ubuntu, I checked the cd and it gave me the same errors, what can be problem to this?

---

### Post by Pumalite on 2008-02-16
Get ImgBurn: [http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Install, go to Mode>ISO>Burn.
Here is a guide for the matter of the md5sum:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by hduong01 on 2008-02-16
Ty i'm going to try to redo this, with your instruction let see if i can escape window :)

cross figure

---

### Post by hduong01 on 2008-02-16
it did not work, i don't know whats wrong with it. I used your method and check the cd for defect and all these errors came up.  It's the same errors

[IMG]http://i210.photobucket.com/albums/bb9/run8888/IMG00047.jpg[/IMG]

[IMG]http://i210.photobucket.com/albums/bb9/run8888/IMG00056.jpg[/IMG]

---

### Post by Pumalite on 2008-02-16
You could try the Alternate CD (text based; avoids graphics and other hardware problems). Download from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Check the box below the sign 'Start Download'

---

### Post by hduong01 on 2008-02-16
what are those errors?  um.. the alternative cd, i did download it but it's the same errors.  Is there a way i can fix those errors?

---

### Post by zinnsser on 2008-02-16
The errors you are showing usually come from an overloaded hard disk channel.  Do you have two hard disks attached to one channel (in other words on one cable)??

or do you have  a cd or dvd drive attached to the same cable as your hard drive.  The cd or dvd may be trying to copy to a hard drive on the same cable causing data overload.  

Use one disk per channel and if you need more add an expansion card.

Hope this helps

---

### Post by hduong01 on 2008-02-16
I have 2 cd/dvd rw on one cable (primary and secondary) should i disconnect one and try it out?

---

### Post by lewac on 2008-02-16
you've indicated that you previously installed using a specified CD to a laptop. that would rule out the install CD I'd think (unless your reader is kaput which is probably not likely). something within  the box you're attempting to install to looks to be having a hardware issue. are your bios settings ok? something that can REALLY mess any install up is improperly matched video... say you actually got onboard video but you're telling the bios you got AGP?? note that with some motherboards you may actually obtain video in this situation! but try loading ANY OS and you get "strange" anomalies showing up.

do things seem to work okay off the liveCD? can you load firefox for example and access the internet from there? can you load any of the other apps from same? if this is balky it could be main memory. if possible try swapping that out with known good (if not that rule memory out using a good memory test utility). check the hardware compatibility list (go here: [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)). yeah there's something amiss within the hardware I'm certain of it.

---

### Post by hduong01 on 2008-02-18
well nothing seems to work so thanks for everyones help :), but i think i'm stuck with window untill i get a new computer lol.  

Greatly appreciated!
Henry

---

