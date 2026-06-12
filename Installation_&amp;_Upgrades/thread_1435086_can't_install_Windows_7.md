---
title: "can't install Windows 7"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by pato wlmc on 2010-03-21
Ok. so i use to have vista and ubuntu on my PC.

Yesterday accidentally i created a new partition ¨table¨ ( jeje, i don't know the the name of this in english, since i'm mexican sorry ) the point is that i erased all my partitions on "MyDisk".

After a while i decided to re-install ubuntu ( 9.10 karmic koala ) and take advantage of the situation and upgrade to Windows7.

Since i already had the ubuntu cd, i installed it first, then downloaded the Win7 cd to install it.

The problem is that Windows7 installer doesn't load.

All i get is:

<<BLACK SCREEN>>

Grub loading.

<<BLACK SCREEN>>

underscore

Ubuntu logo
ubuntu login


So i don't know whats wrong.

Right now my disk looks like this:

 MyDisk >
       MyDisk1 ntfs ( For windows 7 )
       MyDisk2 > extended (using linux with 2 more partitions: ext4 and linux-swap ) 

I'll apreciate any help

THANKS!

---

### Post by NightwishFan on 2010-03-21
I will not give support to an illegal install if you downloaded/burned Windows7. If it is an official CD I will help you.

---

### Post by pato wlmc on 2010-03-21
it's legal, right out of [_mercadolibre_]("http://mercadolibre.com") ( spanish vercion of ebay ) =)

---

### Post by NightwishFan on 2010-03-21
I was just making sure, not trying to be rude, my apologies.

[LIST]
[*]Verify the CD is not damaged. If burned retry at a slower speed.
[*]Ensure your bios is set to boot from CD.
[*]Does any OS detect and view the files on the CD?
[/LIST]

---

### Post by pato wlmc on 2010-03-21
Well, i'll try burning down again the cd, but i don't think, thats the problem since Ubuntu perfectly recognize the dvd, and read all the files within it.

And i've already checked the BIOS, and it's set: CD/DVD - USB - HDD, in that oreder.

So...

The only thing i can think of, is that it's just an upgrade cd, but the vendor published the item like "BOOTABLE", and it does have a BOOT folder on it

---

### Post by NightwishFan on 2010-03-21
That may be the case, however before you continue, try two things. If you have Virtalbox, try to boot the .ISO on there. Just boot not install. If it works then the CD is correct.

If you burn, then burn at the slowest possible speed, or as slow as you have the patience for. That reduces risk of errors. If you are running Windows to burn it, then use this program:
[http://infrarecorder.org/](http://infrarecorder.org/)

---

### Post by pato wlmc on 2010-03-21
****!!

it did boot on wvirtualbox.
So i think, i'm deleting all partitions again ( I have nothing on ubuntu but some programs )  and install it first, then from de ubuntu cd get the disk partitioned.

Thanks,  i'll tell you how it went

---

### Post by NightwishFan on 2010-03-21
Excellent, I am glad that worked. It is always best to install Windows first anyway. Enjoy! Please keep me up to date and forgive my blatant anti-software piracy attitude.

---

### Post by pato wlmc on 2010-03-21
**UPDATE**

For some <snip> reason it still doesn't boot.  So i'm gonna try bootyng my xp cd, and then update to 7  so a'll tell you how it went....

---

### Post by NightwishFan on 2010-03-21
Good luck. I doubt it not booting is a Linux related issue since grub takes control after the BIOS. Who can say though.

---

### Post by pato wlmc on 2010-03-22
DONE!!
 
This is what i did.
 
[LIST]
[*]Booted ubuntu Live cd.
[*]Running Gparted i deleted all partitions on My disk ( leaving it just like extended )
[*]Booted my xp installation cd, and installed it
[*]After installing xp, get the Win7 cd in to the tray, and run the upgrade program.
[*]PRESTO!
[/LIST] 
Next thing i'm gonna do is install ubuntu, but that sould be no problem.
 
Really man, thanks!

---

### Post by NightwishFan on 2010-03-22
Good work. I am glad you got it. Happy Ubuntuing!

---

