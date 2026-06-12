---
title: "UNetbootin won't boot"
date: 2010-07-16
forum: Installation &amp; Upgrades
---

### Post by Bag of Paper on 2010-07-16
'm trying to boot UNetbootin via USB on my ASUS 1000HE netbook to recover files i  got raped by a virus and windows crashed. When it comes to the boot  screen it says Default or Help i go Default and it says Automatic boot  in 10 seconds, counts down and then doesnt boot, just starts again from  10?

When i boot and use tab for "help" it has /ubnkern initrd=?ubninit file  =/cdrom/preseed/ubuntu.seed boot = casper quiet splash

i checked on the USB and that file path is correct, accept the  ubuntu.seed is 0kb so maybe that has something to do with it? not sure

I took a print screen from my desktop to show what the USB contains

[IMG]http://img62.imageshack.us/img62/670/ubuntuy.jpg[/IMG]

I've asked for help on a number of other forums but havn't got any replies as of yet, any help would be great because im really stuck atm.

---

### Post by Rubi1200 on 2010-07-16
Is BIOS set to boot from the USB? 

If you have more than one USB port, did you try switching to an alternative port?

How did you install (I presume Ubuntu 10.04?) on the USB stick; with UNetbootin from within Ubuntu or Windows and how did you install it?

The reason I ask is that there may have been a problem with the way you installed; in other words, was UNetbootin installed on the host machine or did you put the image on the USB by setting the executable bit for UNetbootin?

You could try and edit the syslinux.cfg file and remove quiet splash then save. When you next try to boot you will hopefully see the errors (?) that are preventing you from booting.

In Ubuntu: edit the file with gedit

In Windows: right-click open choose which program and use Notepad

---

### Post by matt90 on 2010-07-16
I have a similar problem.  I used Unetbootin (under Ubuntu) to make a DSL boot SD card for my netbook, and it only gives the "default" option and gets stuck in an infinite loop.  I've tried selecting the boot disk with ESC, and also setting it in the BIOS.

---

### Post by leclerc65 on 2010-07-16
Unetbootin, the Windows version works better than the Linux one.

I hate me for saying that.:p

---

### Post by Bag of Paper on 2010-07-16
> **Rubi1200 said:**
> Is BIOS set to boot from the USB? 

Yep, it boots straight away because i changed the options in the BIOS

> **Rubi1200 said:**
> If you have more than one USB port, did you try switching to an alternative port?
Yes, didnt make a difference

> **Rubi1200 said:**
> How did you install (I presume Ubuntu 10.04?) on the USB stick; with UNetbootin from within Ubuntu or Windows and how did you install it?

The reason I ask is that there may have been a problem with the way you installed; in other words, was UNetbootin installed on the host machine or did you put the image on the USB by setting the executable bit for UNetbootin? 

I did it on another windows xp desktop. I installed it with the UNetbootin downloader from a link i got off this youtube video 

[http://www.youtube.com/watch?v=2Zxh_R9eXmk](http://www.youtube.com/watch?v=2Zxh_R9eXmk)

What it did, was it told me to insert my USB stick, and it downloaded all the files to the USB drive (i selected this option) so installed it on the USB. Then the last step it said, was to take out the USB and put it in the computer i wish to boot it from.. so i did that.

> **Rubi1200 said:**
> You could try and edit the syslinux.cfg file and remove quiet splash then save. When you next try to boot you will hopefully see the errors (?) that are preventing you from booting.

Not sure what you mean by this, isnt the quiet splash part of the BIOS settings for boot? I know theres a quiet boot and one another option for boot i cant recall.

thanks.

---

### Post by Rubi1200 on 2010-07-17
Open the syslinux.cfg file with a text editor.

Under the menu label Default you should see a line like this:

```
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash
```Remove the quiet splash and add nosplash so that it looks like this:

```
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper nosplash
```All this does is tell it to be verbose during the boot process. In other words, you will see all the kernel messages flash by etc.

Make sure the line looks exactly as above!

Looking at the screenshot again, you appear to be missing some files on the USB stick. Are you sure you let the process complete the first time? 

Maybe try downloading and reinstalling the image to the USB stick.

---

### Post by Bag of Paper on 2010-07-22
i re-downloaded it and it worked fine, thanks for your help.

What i would like to know however is if i choose to keep ubuntu (which i think i will for my netbook and keep windows on pc), then how do i go about deleting all the windows files i don't need?

---

### Post by Bag of Paper on 2010-07-24
Bump??

---

### Post by anon.jdh on 2010-07-24
By deleting them. Im sorry you'll really have to clarify.

---

### Post by Bag of Paper on 2010-07-26
basically i want to do a fresh install of ubuntu, not over the top of windows, but i want to completely wipe any windows files, i've been runnings UNetbootin off the USB for about a week and i'm getting a bit past it.

---

### Post by P4man on 2010-07-26
unetbootin is just a little app to make a bootable USB stick. You dont boot it or use after you made it.

Anyway, I assume until now youve been running live sessions from the USB stick, and you havent installed ubuntu yet? If so; just install it. Boot from the stick and double click the ubuntu installer on the desktop. It will ask you to set up a dual boot or you can use it to format the drive entirely, wiping your windows (and all your data!) in the process.

---

### Post by Bag of Paper on 2010-07-27
> **P4man said:**
> unetbootin is just a little app to make a bootable USB stick. You dont boot it or use after you made it.

Anyway, I assume until now youve been running live sessions from the USB stick, and you havent installed ubuntu yet? If so; just install it. Boot from the stick and double click the ubuntu installer on the desktop. It will ask you to set up a dual boot or you can use it to format the drive entirely, wiping your windows (and all your data!) in the process.

cool thanks

---

