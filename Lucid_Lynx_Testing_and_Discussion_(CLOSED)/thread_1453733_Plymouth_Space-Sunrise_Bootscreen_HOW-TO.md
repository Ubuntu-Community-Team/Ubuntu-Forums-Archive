---
title: "Plymouth Space-Sunrise Bootscreen HOW-TO"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by C0MM4NDER on 2010-04-13
Hi there. 

Reason i post this is because Plymouth is still a huge what.
There are some old threads but none of them have all the info for a new user
to try example the space-sunrise theme. 

This thread is detailed information on how to get that theme working and with few tweaks
make it work smoothly. 

I use some of the info from this thread = [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1381109](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1381109)
And I also use some from the help I got in #Plymouth channel (thanks to brejc8 that took a large chunk of his time, halfline, tseliot and few others)

This is how it should look like with the boot screen 
[http://www.youtube.com/watch?v=qaSg2rRj4HQ&feature=related](http://www.youtube.com/watch?v=qaSg2rRj4HQ&feature=related)

Step 1; Download his pkg.
[http://gitorious.org/oskude-plymouth-themes/space-sunrise/archive-tarball/ubuntu](http://gitorious.org/oskude-plymouth-themes/space-sunrise/archive-tarball/ubuntu)

Step 2; Extract and run as sudo build.sh You need inkscape to build it ($ apt-get install inkscape)

Step 3; Make a folder and copy.
Make a folder named space-sunrise in (/lib/plymouth/themes/space-sunrise) You can easy do this by "gksu nautilus" be careful when doing stuff!
Copy all the contents of oskude-plymouth-themes-space-sunrise to that folder.

Step 4; Installing the theme.
[Terminal]
To install the theme you need to do the following, 
$ sudo update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/space-sunrise/space-sunrise.plymouth 200

Step 5; Choose boot screen
[Terminal]
$ sudo update-alternatives --config default.plymouth
You should see the space-sunrise in terminal 

Step 6; Rebuild the initrd for the change to take affect
[Terminal]
$ sudo update-initramfs -u

Reboot and now it SHOULD work. The shutdown animation will be cut but the loading animation should work if not!
Do step 7,8 if that does not do it do step 9 and 10.

Step 7; Edit space-sunrise
For me to get it to work smoothly i had to edit the script a bit.
Open /lib/plymouth/themes/space-sunrise/space-sunrise.script
Add this line to it "p = (p * 100.0) / 15.0;" without the "" and save!
Like this on row 87 = [http://pastebin.ubuntu.com/359328/](http://pastebin.ubuntu.com/359328/)
This line defines how long the animation should work try a value from 10 to 20 to see what works best. For me 15 did it.

Step 8; Rebuild the initrd for the change to take affect
[Terminal]
$ sudo update-initramfs -u

Step 9; Framebuffer
Create a file named splash in /etc/initramfs-tools/conf.d/
Inside splash type "FRAMEBUFFER=y" without "" and save
This may slow down your boot by a sec but i did not notice any difference.

Step 10; Rebuild the initrd for the change to take affect
[Terminal]
$ sudo update-initramfs -u

I had to do all steps from 1 to 10 to make it work smoothly on my HP 6510b laptop.

Best Regards
Commander o7

---

### Post by ELD on 2010-04-13
Thanks for the guide i checked the video and love it, do you know if this will work on a HD4850, as currently the load screen is a stupidly low resolution and looks awful!

---

### Post by C0MM4NDER on 2010-04-13
> **ELD said:**
> Thanks for the guide i checked the video and love it, do you know if this will work on a HD4850, as currently the load screen is a stupidly low resolution and looks awful!

Try this.
[http://pastebin.ubuntu.com/413858/](http://pastebin.ubuntu.com/413858/)

---

### Post by zoomy942 on 2010-04-13
So this is something I would probably have to manually do huh?  since we are so close to release and plymouth is all botched....

---

### Post by ranch hand on 2010-04-13
Nice work and it may be of use to folks that do not have to boot through recovery or disable plymouth to boot at all.

---

### Post by ELD on 2010-04-13
I have tried the link, but it didn't seem to change the boot screen and i did it to the letter :(, i might remove plymouth from my desktop. It works great on my netbook, highly annoying. I guess that is the problem with using the closed source drivers.

---

### Post by jerrynewt on 2010-04-13
Not to sound too thick, but how do you use inkscape to build the splash image?? Do it manually by using the logo or what. Never used inkscape so kind of in the dark on that point. Thanks

---

### Post by C0MM4NDER on 2010-04-13
> **jerrynewt said:**
> Not to sound too thick, but how do you use inkscape to build the splash image?? Do it manually by using the logo or what. Never used inkscape so kind of in the dark on that point. Thanks

You only have to have inkscape installed. Then just start build.sh in terminal as super admin.

---

### Post by jerrynewt on 2010-04-13
Got it !! 
Thanks for the reply.

---

### Post by SevenMachines on 2010-04-14
thanks [C0MM4NDER]("http://ubuntuforums.org/member.php?u=680611") and oskude, you're never too old to enjoy a pretty boot :)

---

### Post by jdriessen on 2010-04-18
thanks Comm4nder!
My plymouth wasn't actually working until I used this guide, and I now even have a fancy boot animation to go with it.

Cheers.

---

### Post by tjeremiah on 2010-04-19
I could of sworn for a second I was about to watch a Universal movie.:popcorn:

---

### Post by zurien on 2010-04-21
Thank you for this guide, followed it and everything works.

Although about every 3rd boot or so the boot splash is somewhat askew (see screenshot).

[HTML]http://i973.photobucket.com/albums/ae213/zurien123/plymouth/DSC00146.jpg[/HTML]

any ideas why this i might be happening?

---

