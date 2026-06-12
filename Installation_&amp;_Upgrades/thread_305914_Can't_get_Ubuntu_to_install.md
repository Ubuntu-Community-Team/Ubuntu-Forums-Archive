---
title: "Can't get Ubuntu to install"
date: 2006-11-24
forum: Installation &amp; Upgrades
---

### Post by britt-stinker on 2006-11-24
Hi I've been trying to install Ubuntu but i can't seem to get it to work. First I tried with the intslux installer, but that just began to unstall. Then I hve tried the manual way for xp. When I reboot my com it goes to the black screen where I choosed install ubuntu. After a while it asked for a cd rom that it doesn't say anyting about in wiki.

Can someone help me?

My computer is a 
Toshiba
intel(R)Celeron(R) M
processor: 1.40 GHz 
(I hope that is what you need to know)

---

### Post by Spin Doctor on 2006-11-24
Don't understand that you use intslux installer, when you can use an official LiveCD or an alternative installation cd.

I guess what the installer you are using are asking for is this:

[http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)

Hopefully you know which version of Ubuntu,  instlux installer is trying to install. Select corresponding cd to download using your windows system. Then burn that ISO file to a cd using some software that will convert that ISO file to a complete bootable cd.

I used Alex Feinman's Iso recorder. What u do then, is just right click on the isoImage and select burn image. Remember to burn at lowest possible speed available.

Link to Iso Recorder: [http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

---

### Post by britt-stinker on 2006-11-26
I've downloaded the installation disk file, burnt it and all, but it doesn't work. when I reboot nothing happens. It just starts back up in windows. when I open the cd it shows the "ubuntu tryout" disc tree.'

Any help?

---

### Post by vtel57 on 2006-11-26
> **britt-stinker said:**
> I've downloaded the installation disk file, burnt it and all, but it doesn't work. when I reboot nothing happens. It just starts back up in windows. when I open the cd it shows the "ubuntu tryout" disc tree.'

Any help?

The download you got was an .iso file. You can't just burn it as a data CD. You have to burn it as an .iso. In order to do this (Windows doesn't have the capability), you have to d-load and install a small application in Windows called [ISO Recorder]("http://isorecorder.alexfeinman.com/isorecorder.htm"). Once you've installed this application, RIGHT click on the .iso file that you d-loaded (Ubuntu) and choose "make disk" or "create disk"... I can't remember which. You'll see it, though. It's in the RIGHT click menu. Have your new blank CD in the drive. Voila! A couple minutes later you'll have a bootable image CD of Ubuntu Live. Restart your system and boot to the CD. Follow the directions....

Enjoy!

---

### Post by britt-stinker on 2006-11-26
Thats what i did. I used imgburn. and it doesn't open. I'm unshure if I accidently changed something in the system to make it unable to boot from the cd, since I have tried alot of the suggestions on the site to make it install but it wont work.

---

### Post by unisol on 2006-11-26
did you go in your bios and set yyour cdrom drive to be the boot drive

---

### Post by britt-stinker on 2006-11-26
no, how do i do that?

I will still like to have windows on this computer afterwards. Can you tell me if this way of installing it will delete windows?

Thanks

---

### Post by britt-stinker on 2006-11-26
anyone?

---

### Post by peebly on 2006-11-26
You need to find out how you select which drive your computer boots from, on my computer I keep pressing f12 at start-up, it then displays a menu of the drives installed on your computer. pick the one you need i.e cd-rom.

If you manage to get It installed, you will be presented with a menu at start-up, you can select Linux or Windows.

---

### Post by az on 2006-11-26
> **britt-stinker said:**
>  Can you tell me if this way of installing it will delete windows?

Thanks

You will be offered the option of completely erasing the hard drive to install Ubuntu or to install on a seperate partition.  If you pick the second option, you will be asked for a size for the current windows partition - shrink it and then Ubuntu will install itself besides the windows partition.

This is very very common and works well.

---

