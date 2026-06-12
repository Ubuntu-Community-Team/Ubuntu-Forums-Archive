---
title: "Hardy Install In XP issues"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by oorat on 2008-04-30
Okay, I'm a first timer here with Linux, outside of trying out a Live CD of suse once and the Live CD of the Hardy beta.  But this is my first install.  I decided to go the installing in windows route.  

I got the iso of the standard version of 8.04 and burned it to cd.  Now when I go to install it in windows, it starts working to create the image, but once it gets all 724.2mb of data, it gives me an error saying 

"Could not access CD, please make sure other applications are not using it and try again"

I can guarantee that the cd is not being used by another application.  So I'm not sure what to do.  

I run a Intel Dual Core 2 2.44g pro with a 1g of DDR2, I'm using the standard XP pro.  

Any help would be awesome.

---

### Post by dstew on 2008-04-30
> Now when I go to install it in windowsWhat do you mean by this? Did you download a Live CD image, and burn it to a CD, then boot the CD? Are you using Wubi?

---

### Post by oorat on 2008-04-30
Well, it may be easier to show you, 
I load the cd into the tray, I get this, as I've read on a few sites I can install ubuntu this way, I select the center option of installation
[IMG]http://img.photobucket.com/albums/v98/oorat/ubunutissueone.jpg[/IMG]
It then gives me this screen, as it loads up creating the image to install ubuntu
[IMG]http://img.photobucket.com/albums/v98/oorat/ubunutissuetwo.jpg[/IMG]
But then errors out with this no matter how many times I retry.  
[IMG]http://img.photobucket.com/albums/v98/oorat/ubuntuissuethree.jpg[/IMG]

---

### Post by dstew on 2008-04-30
Thanks for showing me that, I did not know that was an option. I don't think I can help you with that, all I have ever done is install from booting the CD.

---

### Post by oorat on 2008-04-30
Okay, thankx anyway, hopefully someone will know.

---

### Post by oorat on 2008-04-30
It looks to be that the install program is wubi off of the cd, sorry if this all seems to common sense to others, I'm a noob, but it still errors out with the same message even after I downloaded a new iso of 8.04 from ubuntu's website itself, the previous one came from mininova.

---

### Post by dmj99 on 2008-04-30
To throw in my two cents worth . . . I've never had real problems with any ubuntu or debian installation messing up my WinXP.  When you install Linux, it does overwrite part of the MBR with the Linux bootloader, GRUB.  This creates a dual boot situation, which is nice.
If you decide you want to get rid of Linux, it is very easy to recreate your original MBR if you have your WinXP disk. You just boot up your WinXP disk, do a repair of windows, and use the FIXMBR command.  This rewrites the MBR to the way it was before Linux. If you have any program like partition magic, you can resize your windows partition back to its original size.

---

### Post by oorat on 2008-04-30
Thanks for the advice.  I finally got ubuntu working, though not from the cd.  I downloaded wubi, and even then I had to take the cd out of the dvd rom because it was still erroring out.  So I just let wubi run on its own and it worked fine for me after that.  I'm not certain what is the error.

---

### Post by RogerDaryl on 2008-05-01
I had a similar error after I had burnt the iso to cd, I don't have that error if I load the iso up in daemon tools

---

