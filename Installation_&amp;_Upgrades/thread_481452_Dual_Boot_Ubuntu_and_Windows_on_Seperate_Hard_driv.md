---
title: "Dual Boot Ubuntu and Windows on Seperate Hard drives"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by Specter043 on 2007-06-22
I have a hard drive with Windows XP and one with Ubuntu.  I primarily use the ubuntu one, but I keep the windows around for when other people use my computer.  I was wondering how to hook up both hard drives correctly.  I just swap the cable out currently, between one and the other, because I don't actually know which one to make slave/master, and where to hook up the cables etc.  Anyone who could help me out would be a big help.  So question is.  

How do I set up my 2 hard drives so I can choose which one to boot from?

---

### Post by jessejazza on 2007-06-22
Not sure about the dual boot. But selecting which drive to make master is straightforward.

Take the drives out; read the notation on the bottom (placing the rubber bit over the relevant pair of pins - there are 5 and the diagram will tell you which way to connect), making one master and the other drive slave.

From the motherboard there are two leads for the drives - each taking a primary and a secondary. You can either have the hard drives on one lead like me or one on each with another device. I have the hard drives on one, and the cdrom and combi on the other.

Then you need to make sure your bios settings are right - i.e. the computer looks first at the floppy (in case of mishap allows a recovery disc in the floppy drive or cdrom) or choose the hard drive.

It is easy to make a mistake with the diagram on some makes of hard drive - but the above has worked for me.

---

### Post by mrphantastic on 2007-06-22
I've got you covered, first of all, no rudeness intended whatsoever, but do you have sufficient space and power in your case for two hard drives...it seems and odd question, but I've overlooked it many an occasion?

---

### Post by Specter043 on 2007-06-22
Well, both drives are installed.  And right now the windows one is just a slave, but I want to be able to boot off of it on occasion.

---

### Post by mrphantastic on 2007-06-22
are you familiar with "jumper settings"  ?

---

### Post by Specter043 on 2007-06-22
I know what they are.  The little pins on the hard drives on the bottom, and you can move them around.  I've never really messed with them before though.

---

### Post by mrphantastic on 2007-06-22
This is the time where they are absolutely critical, I will post a link here in just a few minuts from Rapidshare.com, I am going to make this easy...i'll create a guide in .pdf format that you can just download straight from the net...advantage...screenshots that I make myself, don't worry, no junkware, just a help guide.  Anyway, you will need this [http://www.adobe.com/reader]("http://www.adobe.com/reader") it's just a little program that is great for viewing the documents I make, I asked people to critique this help technique before and they loved it, because they can SEE what I am referring to. Honestly, you'll love it, just gimme a few minutes to throw it on the upload, post the link, and it will be there for you, full picture guide and all, k?  Ill show you the jumper settings, the cable connections the setup, and if you EVER have any questions, I'll always answer PM's...

---

### Post by Specter043 on 2007-06-22
wow, uhhh thank you so much.  I'll sit tight and wait, no rush.

---

### Post by mrphantastic on 2007-06-22
Aight, hopefully I can actually spell everything correctly in this post...lol.  Here is the full, screen shot-loaded guide and I hope it helps, if it does not work the first time, just wait a little bit, I uploaded it like 2 sec ago so....

[http://rapidshare.com/files/38776654/Dual_Booting_Guide_N_mero_Dos.pdf]("http://rapidshare.com/files/38776654/Dual_Booting_Guide_N_mero_Dos.pdf")

good luck by the way :)

---

### Post by Specter043 on 2007-06-22
I read the guide, and have them set up as master and slave.  When I look at Hard drives in the BIOS, the Windows one shows up.  But when I go to the boot menu, it isn't an option.  Only the Ubuntu one is.  And then if I hit f10 for the actual boot menu that's blue, it doesn't show up as an option.  It won't detect the HD as a bootable device, only the Ubuntu one.

---

### Post by logos34 on 2007-06-22
what's the device boot order? (like removable>cdrom>hard drive, or what?)  There should be a subsection specifically listing the boot order of your hard disks.  Is the other drive there?

You might want to double check those jumper settings if you're the least bit unsure.  (check the manufacturer website)

---

### Post by Specter043 on 2007-06-22
The set up is cdrom, then Hard drive.  But I can only pick the Hard drive set as master.  The other one doesn't appear as an option.

---

### Post by mrphantastic on 2007-06-22
So, there's no further option to go in and mess with the "hard drive group", from the menu of, floppy>cdrom>hard drive , etc?

---

### Post by mrphantastic on 2007-06-22
Also, do you see the boot loader I mentioned in the guide that I sent you?  some sort of Linux GRUB loader that comes up after your computer boots, but before either OS, because that would solve this, if we could figure out how to get it to pop up...

---

### Post by Specter043 on 2007-06-22
I gave up, and partitioned one drive.  I'm going to take the smaller one and make it FAT32, to use it to transfer files between windows and Ubuntu.  Thanks for all the help though guys.

---

### Post by mrphantastic on 2007-06-22
Sorry to hear that....I know it can be tough sometimes, glad we were of some help at least... :)

---

### Post by xl_cheese on 2007-06-23
Are they sata drives?  or pata?

If they are SATA then you don't need a jumper for anything at all.  There aren't master/slaves anymore.  You configure the boot order in the bios.

I'm doing the same thing you're trying to do.  When I installed ubuntu Grub configured itself correctly.

---

