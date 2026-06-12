---
title: "Trying to install ubuntu on my pc..."
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by ferjonathas on 2010-04-24
I downloaded the ubuntu 9.10 yesterday. I burned it to a cd and everything but I'm getting the following message when I click "help boot from a CD"..

this is the following message.

AN ERROR OCCURRED:
COULD NOT RETRIEVE THE REQUIRED INSTALLATION FILES
FOR MORE INFORMATION, PLEASE SEE THE LONG FILE:  C:\DOCUMEN~......

I went to the file folder to see the log, but there is no file there!! 

Should I download again the ubuntu 9.10?? I also saw the remix that is good for laptops..

What should I do??  I have a HP G60 with a AMD dual core running 2gb of ram with a 160 gb of hd...

Each ubuntu should i download??

---

### Post by jaco223 on 2010-04-24
It could be the iso you downloaded is corrupt.
Maybe you should download the image again and burn it
at a slow speed 4x. 

[http://releases.ubuntu.com/10.04/](http://releases.ubuntu.com/10.04/)

You can download either the 32bit or 64bit iso.

Hope this helps.

Jaco

---

### Post by Naggobot on 2010-04-24
Since when Ubuntu has 

>  C:\DOCUMEN~......


folder?

Something strange going on here. 

If you boot from live cd Ubuntu should not mount your hard drive and it certainly should not attempt to read from windows specific folder. 

Do you have windows as pre installed and is it possible that your system is actually not booting from CD but trying to do windows recovery or something similar. 

Check from bios that your computer actually boots from CD-ROM first if disk is present. There is a boot order sequence section in the Bios, set CD-ROM as first entry.

---

### Post by philinux on 2010-04-24
Looks like a Wubi install.

---

### Post by P4man on 2010-04-24
Download the ubuntu iso using bittorrent. That way you are (virtually) guaranteed the download is not corrupted. It does sound like a bad download or a burn that failed.

If you have a slow internet and dont like downloading again, you can verify your downloaded iso using this here:
[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows)

If the hashes match, the download is okay, and the problem occured burning it to disc. Try again (slower speed) or use an usb stick instead of a cd. You can use a program called [unetbootin]("http://unetbootin.sourceforge.net/") to create a bootable ubuntu USB stick from windows.

---

### Post by ajgreeny on 2010-04-24
If you already have the iso file, even if it is corrupt, you can repair it with a torrent client by making sure the current iso file is in the same directory as the destination for your new one.  That way, only the "broken" parts will be downloaded again.

You can check your current live CD by booting to it and choosing Check CD from the menu when you hit F4 as it boots, (I think it's F4, but I can't remember for certain).

---

### Post by P4man on 2010-04-24
> **ajgreeny said:**
> If you already have the iso file, even if it is corrupt, you can repair it with a torrent client by making sure the current iso file is in the same directory as the destination for your new one.  That way, only the "broken" parts will be downloaded again..

Now that is clever. Why didnt I ever think of that? Good tip!

---

### Post by ferjonathas on 2010-04-24
I did change the the boot sequence!  I dont know what happened maybe its a bad download or I had a problem with the burning section!  Im downloading it again but Im downloading the 10.04 version... Ill try again to burn a cd at slow speed and I make a bootable pen drive..  

Am i going to have problems finding drives ?  I read that ubuntu has the best hardware data base, it said i should be fine with the drivers!!

How will the performance be?? with AMD DUAL CORE and 2 gb of ram and a 160 hd??

---

### Post by P4man on 2010-04-24
> Am i going to have problems finding drives ?

Not likely. Except when you hibernate windows,or dont properly shut it down. ubuntu will refuse to mount the drives then, but otherwise it reads and writes windows file systems just fine.
> 
 I read that ubuntu has the best hardware data base, it said i should be fine with the drivers!!

Dont bet your life on it. Its pretty good, but you may still run in to issues with network cards and other things. Find out. You can run ubuntu from the cd or usb stick so its easy to see if your monitor, sound, network etc work or not.

> How will the performance be?? with AMD DUAL CORE and 2 gb of ram and a 160 hd??

pretty fast for most things. It wont be any good at running your windows apps or games though, so it just depends what you want to do with it.

---

