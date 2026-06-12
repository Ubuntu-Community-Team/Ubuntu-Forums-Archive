---
title: "USB install---too many methods"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by ubuntxp on 2010-02-05
I have been jumping from tutorial to tutorial, downloaded 2 programs on separate computers and got 5 sets of instructions. Problem is, they all make sense in their own way (or none at all). Here is what I'm trying to do:

-Download the ISO onto a USB stick
-I can use a laptop running Fedora or a desktop running Windows XP
-Goal: format older machine running Win-98 with Ubuntu

Apparently that last one is the sticking point, at least with Unetbootin. One site recommended usb-creator so I went ahead and d/l'd Unetbootin on the XP and usb-creator on the laptop. I'm concerned about the machine being too outdated, I'm unsure which program to use and am worried I'll screw something up and not install the MBR right. 

Of all the tutorials and howto's, which one do I use?

---

### Post by shriramrs31 on 2010-02-05
> **ubuntxp said:**
> 

Of all the tutorials and howto's, which one do I use?

If u want ubuntu iso on usb stick, use Unetbootin either from windows or from ubuntu itself

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

you dont need any tutorial. Just use the program from above link and point the iso and the target stick. boot from the stick and install.

Its prettttty safe and simple ;-)

---

### Post by darkod on 2010-02-05
Use unetbootin in windows but after it copies the files ignore the question to reboot, just close unetbootin. After that to get rid of the unetbootin menu and enable the main ubuntu menu, open the stick and do:
1. In the root folder rename syslinux.cfg to syslinux.old
2. In the folder isolinux find and rename isolinux.bin to syslinux.bin, isolinux.cfg to syslinux.cfg
3. Go back and rename the whole folder isolinux to syslinux

That enables the ubuntu menu with more options for you.

But, depending how old the machine with win98 is, you might not be able to run ubuntu on it. Not in live desktop mode, or as full install.

---

### Post by ubuntxp on 2010-02-05
There were Dell threads I also tracked down that had ideas, but do you think that maybe the Dell Support in my program manager might help me a little bit? 

Either way, from what I hear I've been walking in quicksand using Fedora on this thing, so if all else fails I'll be here asking for backup/recovery advice from Distro to Distro... :)

---

### Post by shriramrs31 on 2010-02-05
> **ubuntxp said:**
> There were Dell threads I also tracked down that had ideas, but do you think that maybe the Dell Support in my program manager might help me a little bit? 

Either way, from what I hear I've been walking in quicksand using Fedora on this thing, so if all else fails I'll be here asking for backup/recovery advice from Distro to Distro... :)

dont worry about the too outdated PC or corrupting some stuff. backup your data before attempting anything, then you are in safe side no matter what happens.

If your system is old and a not a "performance" system, i would recommend xubuntu. It has Light weight graphics and lesser RAM requirements.

In any case guys here will definitely help you ;-)

---

### Post by jenaniston on 2010-02-05
> **ubuntxp said:**
> 
-Goal: format older machine running Win-98 with Ubuntu

  which one do I use?

not to confuse you more . . .

But why not have BOTH **Windows 98** AND **Ubuntu** on the older machine . . . eventually **BOTH fully installed** ?

First, you should be able to find, make and then run a** live** version of **Ubuntu9.04** on a 1GB (only) USB stick . . .
(I have thought that U9.10 needed at least 2 GB to run - even if the same iso size moreorless)

If that works post for further instructions to full install,
but run Live Ubuntu without installing yet on the older machine -
Windows 98 will NOT be changed in the slightest.

Let us all on the forum know if any questions.

---

### Post by ubuntxp on 2010-02-05
> **darkod said:**
> Use unetbootin in windows but after it copies the files ignore the question to reboot, just close unetbootin. After that to get rid of the unetbootin menu and enable the main ubuntu menu, open the stick and do:
1. In the root folder rename syslinux.cfg to syslinux.old
2. In the folder isolinux find and rename isolinux.bin to syslinux.bin, isolinux.cfg to syslinux.cfg
3. Go back and rename the whole folder isolinux to syslinux

That enables the ubuntu menu with more options for you.

But, depending how old the machine with win98 is, you might not be able to run ubuntu on it. Not in live desktop mode, or as full install.

This is one of my problems, though---you're absolutely right but I got another guy pretty much predicting the apocalypse if I don't find some ISO to download before I remove the USB stick. Am I cool to take it out after renaming those files or am I not doing something?

---

### Post by darkod on 2010-02-05
> **ubuntxp said:**
> This is one of my problems, though---you're absolutely right but I got another guy pretty much predicting the apocalypse if I don't find some ISO to download before I remove the USB stick. Am I cool to take it out after renaming those files or am I not doing something?

I didn't quite understand your question, so lets start from the beginning:
1. You have your ISO downloaded on your computer, probably Ubuntu 9.10 Desktop 32bit or 64bit version.
2. Plug in your usb stick and format it as FAT32.
3. Start unetbootin, select the Diskimage option, select the ubuntu ISO image, and at the bottom select the usb stick letter that windows assigned it.
4. After the files are copied do not restart, just close unetbootin.
5. Do the renaming steps as explained.
6. Depending on windows version, use the Eject option to safely eject the usb stick, and unplug it.

That's it. Even if you messed up something, reformat the stick again and try the same. No harm done. :)

---

### Post by ubuntxp on 2010-02-05
> **darkod said:**
> I didn't quite understand your question, so lets start from the beginning:
1. You have your ISO downloaded on your computer, probably Ubuntu 9.10 Desktop 32bit or 64bit version.
2. Plug in your usb stick and format it as FAT32.
3. Start unetbootin, select the Diskimage option, select the ubuntu ISO image, and at the bottom select the usb stick letter that windows assigned it.
4. After the files are copied do not restart, just close unetbootin.
5. Do the renaming steps as explained.
6. Depending on windows version, use the Eject option to safely eject the usb stick, and unplug it.

That's it. Even if you messed up something, reformat the stick again and try the same. No harm done. :)

You probably didn't understand me because I forgot to post the link to the site telling me I'm screwed. Whoops, lol.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Turns out he was talking about not using the USB stick, so another false alarm. My only problem now is that Windows only allowed 8.4. Fedora would've given me the 9.10. I'll tackle that one if I'm extremely lucky and get this thing installed! :D

---

### Post by ubuntxp on 2010-02-08
Sorry for the delayed response, but the computer I used was a 2000 Dell running Windows '98. Luckily my idiocy here does not translate to other computer aspects, so I was able to locate a USB booter. Problem became a BIOS issue that almost took me down, then once it started to boot up the old Gateway monitor had a screen resolution problem. Took 3 days but I found a Zip drive for the BIOS and I got the USB stick with Ubuntu ready. 

New question: One of the tutorials said you could only do this once. Did the attempts with the BIOS and monitor problems count? I'm not worried about the BIOS thing, but it was booting up when the monitor soured. Also, there's a program on Fedora that promises the Live USB feature's time to be cut in half, but I also found some Distro manipulator (Beldi). Should I run that thing?

JenniferAniston- I'll answer your question and throw you ten more in a separate post, to ease issue congestion (I have plenty of issues here). BTW I loved you in Office Space...

---

### Post by ubuntxp on 2010-02-08
JenAniston- I would dual boot but Windows 98 is about as useful as last night without the Superbowl. Bad analogy---at least college basketball was on. With this Beldi thing would it be a good idea to throw Ubuntu on a partition on this laptop? I'd like to dump Fedora altogether without losing the data, and don't know how much partition space I set aside when blindly installing Fedora.

---

### Post by kronictokr on 2010-02-08
if you use karmic ubuntu 9.10, all you have to do is select the partition you want to install on manualy. the rest of the install is basic.
when you get to the partition editor, select manual and do the following

right click a partition and choose edit

choose a small part of your hard drive for swap, use 2 to 7 gigs, depending

/   <<< root partition as the partition you want your os installed on.
choose ext4 file type (its fast) , and primary partition

/home/username/media   <<<<<to add a partion as a media folder
i suggest fat 32 format for media, as almost all media devices detect fat 32.
as primary partition

then just install everything else as normal, click continue, at the end , nothing special, just click continue finish, and follow the instructions.

if you have messed upi partitions and you know how much space you have to play with, and are NOT keeping any info on those drives. delete them all, and create them in order , and choose to format partion. it make everything brand new again.

---

