---
title: "Reinstalling from LiveCD"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by kuxpac383 on 2008-08-06
I want to reinstall Ubuntu because I had some GNOME errors.  I'd like to keep my /home intact because I have some files on there I'd rather not lose.  I also am enclosing a photo of what Gparted shows me.

sda6=my /home folder I believe.
sda5=GRUB...I think
sda7...not sure what that is for. 

Your help would be much apprecaited.  Or any guides that you I can be pointed to would be great also.  I just am really scared of destroying my photos and music on /home.

Thanks again,

---

### Post by kuxpac383 on 2008-08-06
oops forgot to include the photo. Here is how my Gparted looks....[IMG]http://i38.tinypic.com/nlzo7c.png[/IMG]

---

### Post by Pumalite on 2008-08-06
Backup in DVD's whatever you have in /home. Then delete sda4, sda5, sda6 and sda7. This will give you a large free space (it will merge with the present unallocated space). Make an extended partition of that free space and inside that install Ubuntu.
You can use Gparted Live CD for the job:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779&abmode=1](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779&abmode=1)
Burn the iso to disk and boot from it.

---

### Post by kuxpac383 on 2008-08-06
Thanks! Here goes nothing.....

---

### Post by Pumalite on 2008-08-06
Don't forget to backup your Windows before you start.

---

### Post by dynamethod on 2008-08-06
Yeah just make sure you backup your stuff dude, i had a partitions almost identical to yours last night, and i got the "Grub Error 17", done all everything to fix it and now its finally kaput, i then had to format the entire Harddrive and guess what, the Live CD installation still gives me Grub 17 lol(from one partition, being ext3(and space for swap)) I've unfortuantly had to revert back to windows xp temporarily lol

---

### Post by kuxpac383 on 2008-08-06
This might be a stupid question but I am going to ask anyway. If I am running off the liveCD. How am I supposed to back-up stuff to DVD's?

---

### Post by dynamethod on 2008-08-06
Use a flash drive thats large enough to hold your back'd up data, if you dont have one well.... welcome to my world lol

---

### Post by kuxpac383 on 2008-08-06
How do I get premission to copy my files to my flash drive?  It keeps saying I don't have premission.

---

### Post by kuxpac383 on 2008-08-06
> **kuxpac383 said:**
> How do I get premission to copy my files to my flash drive?  It keeps saying I don't have premission.

nevermind, figured it out

---

