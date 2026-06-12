---
title: "Simple way of moving a full linux install to a new HDD?"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by BastardNamban on 2010-02-22
I have a nice setup of 8.04 with a lot of programs and custom settings it took a while to assemble, and I don't remember how I even pulled off some of it, so I'm worried about this, which is why I'm asking.

Installing linux is was no problem, but I've ordered a new 120GB harddrive for my Inspiron 9300 laptop, the 60 GB 7200 rpm drive wasn't cutting it spacewise. I was hoping someone could point me to the simplest way to "move" my OS and all it's settings to the new HDD. I will be doing dual boot with XP for the first time in years, as I need Autodesk Inventor to work now, so Ext3 will be the new drive's format to keep XP working.

Can anyone help, even just point to a good guide? I can't seem to find much searching. I want to keep my 8.04 install (waiting for the next LTS) Thanks.

---

### Post by ubunterooster on 2010-02-22
go CLONEZILLA! woot. 

Ahem...Clonezilla copies the entire Hdd OS and all to another HDD

---

### Post by BastardNamban on 2010-02-22
Clonezilla, eh? Thanks for a good first lead. I have a PATA external enclosure than runs over USB, and I was thinking of hooking it up with the new 2.5" drive connected in it to do this. Would Clonezilla support such a setup? I only have one PATA port on my laptop, so I can't natively connect 2 HDDs at once.

---

### Post by ubunterooster on 2010-02-22
As long as you are not "upgrading" to a smaller HDD, obviously you are not, I see no problem w/ your setup.

---

### Post by Baneblade on 2010-02-22
+1 for Clonezilla. Great tool.

Other options are to use Remastersys or restore from backups on a fresh install. (You do keep backups right?)

---

### Post by BastardNamban on 2010-02-22
Blade, so Clonezilla can handle an extenal USB connected HDD to do this?

Yes, I backup my stuff. I only backup my actual files, however- pics, music, docs, bookmarks in firefox. I don't backup any OS files.

---

### Post by ubunterooster on 2010-02-22
I have done this to USB drives. If Linux can read the drive, Clonezilla, based on Linux can write to it. 
 But(!!) stick the old drive in the external bay and new in the internal bay. This is to speed up the copy speed; USB drives write sooo slowly.

---

### Post by BastardNamban on 2010-02-22
If I do that, how will I load my OS to run Clonezilla in the first place? I assume I'd have to boot from a USB device. My version of Ubuntu should support this, correct?

Forgive me, I haven't used Clonezilla before, I just need basic usage questions answered before I try it- as long as I know it will work, I'll spend the time to read the usage FAQ before I attempt anything.

---

### Post by cdEWoozy on 2010-02-23
> **BastardNamban said:**
> If I do that, how will I load my OS to run Clonezilla in the first place? I assume I'd have to boot from a USB device. My version of Ubuntu should support this, correct

I have never used Clonezilla, but apparently they offer iso images for Clonezilla live which are bootable from CD or USB flash drive:
[http://clonezilla.org/clonezilla-live/](http://clonezilla.org/clonezilla-live/)

---

### Post by ubunterooster on 2010-02-23
actually clonezilla is a live CD/USB.
you can copy between any 2 drives (ata/ide, sata1, sata2, sata3, usb1, usb2, usb3, firewire) even if you are copying from one kind to another, say usb1 to sata3 or sata3 to ida/ata or.....

Also, you can use clonezilla to have a backup to restore your system to a previous state.

---

### Post by BastardNamban on 2010-02-23
Wow, that sounds really useful! Thanks everyone for the help- I will be using Clonezilla to take care of this. If I run into any problems I'll let you know.

I especially like that it can back up my system, too- despite the fact I will probably never see a virus, trojan, or others again, it's nice to know I can backup simply if I need to.

---

### Post by ubunterooster on 2010-02-23
Just read what it says, making sure to select the proper drives. It is relatively simple. [I still have a perfect backup of vista {w/ most bloatware removed and much added functionality(multiple workspaces, faster than regular install boot, faster programs) that made it a work of art that I could not destroy} copied to an old HDD]

---

### Post by BastardNamban on 2010-02-24
The new drive came today, and I realized a HUGE problem- my external PATA enclosure is for 3.5" internal drives, but I figured "same interface, ok!".

I figured wrong.

The drive will indeed fit the laptop, but not the external enclosure! I figured the interface would still let it connect, just taking up less space inside- but the layout is different. As such, I have no way to copy to either drive directly, as I can only put 1 drive in my laptop at a time.

Is there a way to do this now? I assume I'll have to install the new HDD in the laptop, but from there, I'm not clear how clonezilla would copy the data off when the original drive can't be connected.

Ideas? I'll keep reading the Clonezilla FAQ to see what I can learn on my own.

---

### Post by bpalone on 2010-02-24
Do you know anybody with a USB to IDE interface.  You know the kind that you don't mount the drive in hardware, just hook it up?   If so, then sweet talk them into loaning it to you for a few hours.

If you don't know of one, I think you can find them for around $20 or so.

Once you get that solved, another easy method is use GParted Live and copy the partitions over to the new drive.  I have used this method several times.  The worst that has happened is having to reinstall Grub or make it fix itself.  And that doesn't happen everytime.

Good luck.

---

### Post by BastardNamban on 2010-02-24
I see. So there is no way to do this without both drives physically connected then, is there? Can anyone comment on this?

Maybe there's a way to create a custom live disk of my install, with everything intact?

I have someone who might have one of those USB to IDE interface cables. I'll have to ask them tomorrow.

---

### Post by Palanthas on 2010-02-24
+1 on the USB to IDE (in my case, SATA, IDE - both 2.5" and 3.5") adapter.

Very handy to have around should you ever need to connect a HDD but don't want multiple external HDD cases lying about...

Edit: As bpalone stated, you can find these around $20 give or take...

---

### Post by dmizer on 2010-02-24
Just go out and buy a (very cheap) usb enclosure like this: [http://www.newegg.com/Product/Product.aspx?Item=N82E16817392019](http://www.newegg.com/Product/Product.aspx?Item=N82E16817392019) My experience with the IDE to USB adapters has not been positive. It has worked on a few occasions, but has also messed things up.

I use HDClone: [http://www.miray.de/products/sat.hdclone.html](http://www.miray.de/products/sat.hdclone.html) it supports drives connected via USB as with the above product.

---

### Post by bpalone on 2010-02-24
I don't remember the program name but there is one that allows you to make your own custom distro/intallation disk.  So, that may be another option.  I just remember reading about it, so do a search.  That might get you upgraded a day earlier.

---

### Post by ubunterooster on 2010-02-24
you need to have two drives hooked up at once, yes :(
Laptop PATA is nastily annoying, go for the proper enclosure.

---

### Post by BastardNamban on 2010-02-28
I've looked into external 2.5" enclosures- I've noticed all of them are either ridiculously expensive, or shoddily made and have data integrity problems for large data transfer.

I *THINK* I found the solution. I found Remastersys, a program that lets you make complete iso backups of your whole system, user data and all. I don't need 2 drives plugged in- just burn an image of my system to dvd without all my media.

It seems to work, but I keep getting data verification errors in both Brasero and K3b. That's another thread.

I'll call this solved- I think Remastersys is the best option for me- just a disk clone of my install. I need to get it working, though. Thanks everyone for the help!

---

### Post by ubunterooster on 2010-02-28
:) here's hoping all works out. [remastersys is not on my list of knowledgability]

---

