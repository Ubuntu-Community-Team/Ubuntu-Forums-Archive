---
title: "Problem Running Mint - very newbie"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by a.nu.leif on 2010-04-27
I can't tell whether I'm having a problem with the DVDs, my software, or the DVD drives. 

I burned Mint 8 64bit version at 8x from Windows and it had a problem running from disc on my Linux pc. (I would get the green Mint screen, but nothing I selected would work.) So, I burned it at 2x, and the problem is the same.  

I decided to burn it from within Ubuntu 10.8, but this will not work either. No matter which drive I use, I get a message telling me there's no recordable disc inserted. However, when I have the Mint disc inserted, the computer recognizes it, showing the name, but showing the disc as blank.  Does it matter if I use DVD-R or DVD+R discs?  Is this a software issue? Hardware issue? Any ideas?  Thanks!

---

### Post by P4man on 2010-04-27
Did you verify the iso image before burning ? Might be a bad download. Anyway, stop wasting DVDs and make a bootable USB stick. [unetbootin]("http://unetbootin.sourceforge.net/") is what you are looking for.

---

### Post by a.nu.leif on 2010-04-27
> **P4man said:**
> Did you verify the iso image before burning ? Might be a bad download. Anyway, stop wasting DVDs and make a bootable USB stick. [unetbootin]("http://unetbootin.sourceforge.net/") is what you are looking for.

Thanks very much for the link! I've always wondered how to do that. :-) 

Yes, it is an iso, and burned as an image, was verified, etc.  I just ran the disc on my windows laptop. So I'm guessing the problem is the DVD drives? Does DVD- or + for the disc have anything to do with the type of dvd drive? The disc it self seems to be fine.

I installed Ubuntu not so long ago. The drives aren't even that old. :confused: Or, could it be something in BIOS?

Thanks again!

---

### Post by P4man on 2010-04-27
Well TBH, its not entirely clear to me what exactly you did, if you tried all your burning attempts on the same PC or not? 

There is indeed a difference between DVD+R and -R and some drives will only read (and write) one or the other format, but thats gotta be pretty old drives. Almost all somewhat recent drives should have no problem with either I think.  

edit: misread. So you can read the dvd from the pc you made it on?

I dont know mint livecd, but does it have a menu to check the disk for errors when you boot from it? If so, try it, on both machines.

---

### Post by subcook on 2010-04-27
....And just in case you want to go down the road of booting from USB,  but don't have BIOS support,  use this [http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)    its a nice tool
 
 
 
-cheers

---

### Post by a.nu.leif on 2010-04-27
> **P4man said:**
> Well TBH, its not entirely clear to me what exactly you did, if you tried all your burning attempts on the same PC or not? 

There is indeed a difference between DVD+R and -R and some drives will only read (and write) one or the other format, but thats gotta be pretty old drives. Almost all somewhat recent drives should have no problem with either I think.  

edit: misread. So you can read the dvd from the pc you made it on?

I dont know mint livecd, but does it have a menu to check the disk for errors when you boot from it? If so, try it, on both machines.

I was not able to burn the disc at all from my Ubuntu machine (it has 2 dvd drives). I'm getting a message saying that there is no recordable disc installed. I'm using DVD+R discs. When I tried to boot from disc it would not work. The most I get is the Mint screen with a list of selections (check disc OEM installation etc). However, no matter what I select booting from the disc does not work. After a long wait I always get some error message.

I've tried booting from USB on the Ubuntu machine, but it's not working so far. However, I was able to get the USB boot to work on a Compaq with a blank HD, but it didn't work on the other computers.

I was able to boot from the discs on my Windows Laptop, but not from USB.

The discs were all burned on a Windows laptop running Vista.

---

### Post by RedRat on 2010-04-28
How old is this machine and how old are the DVD or CD drives? They can and do crap out. I had a rather top of the line Plextor DVD drive that crapped out after about 3 years and not many burns on it. It does happen. Sometimes dirt and other gunk can get into the drive and read/write head.

Definitely check the md5sum for both the iso download. It sounds as if the image is not written correctly. I have downloaded Mint 8 and it works fine as a live CD. The idea of a usb stick is good one, make sure that your machine can boot from the usb stick. Some can and some can't. Some machines during the boot up allow you to hit ESC or F-X (one of the function keys) to get to the boot order menu and they may be able to do the usb stick there.

---

### Post by a.nu.leif on 2010-04-28
I never would have imagined that and entire OS would fit on a mini SD card. I accidentally sent Mint 64bit to a card that I didn't know was in my laptop instead of to the USB. :) It took awhile before I realized that my computer really wasn't possessed.  The USB boot still won't work on one computer (nor will the discs), but it seems that it too may need another DVD drive anyway. I'll pick up DVD-R discs tomorrow to see if it makes any difference. I know the burns were good because they ran on the Windows laptop. We'll see.  Thanks for all the help, guys!

---

### Post by P4man on 2010-04-28
Its not necessarily a hardware fault; it could be a compatibility issue. I got a server here which will not boot ubuntu from CD, even if the cd is good and the drive works fine. Its the controller which is not supported.

You can try going in to the bios of the machine and see if there is an option to change your DVD drive settings (I think its called ehci or something? or "compatibility mode" , something along those lines).

However, this would have no impact on booting from usb or CF.

---

### Post by a.nu.leif on 2010-04-28
Thanks for the suggestion! I'll try it out today. I always use USB on the Linux machines, so the dvd drives are rarely ever used. I'll certainly check them out more today, and follow your suggestions.

Thanks for taking the time to help me out! :)

---

