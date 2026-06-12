---
title: "Boot to linux"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by AJ2005 on 2007-05-01
Hi guys,

I'm completely new to this whole linux thing. I've searched the web and had a quick look at these forums; basically, i brought a new computer as the Windows on my old one was corrupt.

On the old computer, i formatted the hard drive, so it's completely blank. Now what i'm trying to do is install Ubuntu as the only OS on there. I've downloaded it ubuntu.com, extracted the ISO to a CD and burnt it on. I stick the CD in to the old computer and switch it on, however it doesn't seem to read from the CD. It says something along the lines of "F1 to retry or F2 to enter setup".

My CD drive is fully operational and the HD still works (albeit, with nothing on it). I've also got the correct boot sequence set in my bios settings.

Any idea how to install Ubuntu? Help would be greatly appreciated. Thanks!!

---

### Post by psusi on 2007-05-01
How did you burn the iso?  You must burn it as an iso image, not just a regular file.  If you place the cd in your windows computer, it should auto run a little greeter program and you should see a bunch of files on the disk.  If you see the .iso file on the cd, then you  burned it wrong.  

If it was burned right, then make sure the bios in this computer is set to boot from the cd first, rather than the hard disk.

---

### Post by AJ2005 on 2007-05-01
Wo0o! thanks for replying;

What i done was, i first created a new folder and extracted the ISO in to that. Then i burnt the contents of the new folder directly to the CD. I burnt the actual files themselves and not the folder i'd extracted them in. 

bios shows CD drive as the first to boot from.

When i put the CD in to my new computer, it comes up with a menu to install firefox and thunderbird(?) and some other stuff, so i'm guessing it's not really a burning issue. (although i haven't tried to install any of the stuff. It jsut asks me if i want to)

Could me not having ANYTHING on the HD of the old system be affecting the installation?

Thanks :-D

---

### Post by psusi on 2007-05-01
Yes, you burned it wrong.  You are not supposed to extract the iso.  The iso is already a prepared image of the cdrom, ready to burn.  By extracting the iso and burning the resulting files, you built and burned a new iso that is not bootable.

---

### Post by AJ2005 on 2007-05-01
oops. How would i go about solving this problem? Would i need nero or something? I'm sure i've got it somewhere in a pile of CDs.

Can i use the Windows burning software (just that generic type that lets you burn stuff to CDs?). And what would i do? Just burn the ISO as a single file straight to the CD? Would that be successful, even if i used the generic Microsoft burning software?

Again, Thanks for the help!!!

---

### Post by psusi on 2007-05-01
Windows does not know how to burn iso images, so yes, you will need to use nero.  Make sure you tell it you are burning an iso image rather than just ask it to burn the file normally.

---

### Post by pinoytechie on 2007-05-01
The LiveCD iso if burned correctly is bootable. don't extract the ISO. burn it as an image.

[http://www.petri.co.il/how_to_write_iso_files_to_cd.htm]("http://www.petri.co.il/how_to_write_iso_files_to_cd.htm")

---

### Post by AJ2005 on 2007-05-01
HOORAY! it worked!...Thanks for all the help!!

It's installing as we speak :-D

---

### Post by stchman on 2007-05-01
> **AJ2005 said:**
> oops. How would i go about solving this problem? Would i need nero or something? I'm sure i've got it somewhere in a pile of CDs.

Can i use the Windows burning software (just that generic type that lets you burn stuff to CDs?). And what would i do? Just burn the ISO as a single file straight to the CD? Would that be successful, even if i used the generic Microsoft burning software?

Again, Thanks for the help!!!

If you are using Windows you can download CD Burner XP Pro from this website.

[http://www.cdburnerxp.se/](http://www.cdburnerxp.se/)

It is a pretty darn good free burning program.  It will burn an image from a .iso file.

---

### Post by AJ2005 on 2007-05-01
Sorry to KEEP being a pain in the back, but abouts how long should it take to install?

I've put the CD in and clicked on "install ubuntu". I can hear the CD spinning and it does some checks. Then, the screen turns all black and that's it. I've restarted the process at this point.

Are long periods of "blankness" supposed to be happening? i don't think they are :-S

---

### Post by bulldog on 2007-05-01
Do you have the live cd or the alternative cd?
If you have the live cd,you boot from it and choose from the menu start or install ubuntu.
This will bring you a live session,although it should,and when you logged in,you see a install button on the desktop.

If you hit the install button,than actual you're going to install,not sooner.

---

### Post by psusi on 2007-05-01
Which iso are you using?  Try editing the kernel command line and changing the word splash to nosplash.

---

