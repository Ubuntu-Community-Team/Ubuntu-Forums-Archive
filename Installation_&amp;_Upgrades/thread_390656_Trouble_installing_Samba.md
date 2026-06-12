---
title: "Trouble installing Samba"
date: 2007-03-22
forum: Installation &amp; Upgrades
---

### Post by tapeman on 2007-03-22
First off, hello there.

OK, enough with the pleasantries.

I am very new to Linux (going on 2 days :) ) and I'm already lost. I'm trying to install Samba and it isn't working. I opened the Add\Remover applications window and did a search for Samba. It found GSAMBAD, but when I tried to download and install it it failed. My internet connection is working fine so that's not it. I also downloaded version 3.0.24 directly from the Samba website, but of course I have no idea what to do now. 

Sorry for the totally newb question, but my years of double clicking setup.exe files in Windows have apparently made me a little bit stupid.

---

### Post by ffxr on 2007-03-22
```
 sudo apt-get install samba 
```

guide here: [http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba+how+to](http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba+how+to)

---

### Post by tapeman on 2007-03-22
Thanks! 

I got it installed now. 

OF course, now I have to figure out how to configure it. :) 

That link looks like it has everything I need. Thanks again.

---

### Post by tapeman on 2007-03-22
Now that I've got the Samba install worked out (thanks again) I'm wondering what is wrong with my Add/Remove programs update. It keeps failing to download anything. As I said before, my Internet connection is set up properly.

---

### Post by Robynsveil on 2007-03-22
From one n00b to another - how'rya goin'?

I've found I do a lot of Googling these days... but the best resource seems to be this forum!

K... I've found that the Synaptic Package Manager is kinda the first thing to be lookin' at for installing stuff, as it does a good job (not brilliant, but okay) at resolving dependencies - stuff that sits in what we Windows defectors remember as the C:\windows\system32 folder. No clue as to what that folder is in Ubuntu, or if it even all *sits* in one folder. I've found that kinda stuff in /home/usr/ and . The /home/bin/ folder seems to hold the same kinda stuff we saw in C:\windows\command\ in Windows 2K, and in C:\windows\system32 in XP... stuff like XCopy.exe and like that.

Now, if you get a .deb file which I guess is like an .msi, double-clicking pretty much does it all for you. I have found, tho, that the Applications--> Add/Remove... thingie seems to be more like a "let's put stuff into your menu that you've installed" than an actual install tool - the Synaptic Package Manager does that.

Oh, and "sudo apt-get install"...

Yes, it's all a bit more involved and complicated than just double-clicking on Setup.exe, but I can't help think it's just so worth it not having a system bogged down by anti-virus / anti-spyware / other-unknown-TSRs-that-the-anti-spyware/antivirus-software-failed-to-snag running, so I'm staying the course. I'm still struggling with Samba so, I'm going to have a re-read of:

[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

and figure out what I'm doing wrong... :confused: 

Cheers,
Robyn

---

