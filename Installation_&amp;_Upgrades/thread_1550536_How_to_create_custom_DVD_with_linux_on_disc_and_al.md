---
title: "How to create custom DVD with linux on disc and all installed softwares"
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by farmerjohn73 on 2010-08-11
I am using lenovo g400 series laptop with dual core 80 GB HDD, 1GB Ram.  Recently I had to unfortunately format my laptop and had to install the linux and other softwares I use.

Due to this I had to download updates of around 400 MB and had to download softwares of another 200 MB around.  Like installing Chrominum and its add ons etc. This is taking a lot of time. To avoid this, I want to know :

Can I create custom Installation DVD with latest linux updates and other softwares and packages currently installed? 

So that when I format my HDD, I can install linux with latest updates and other currently running softwares with add ons etc.

If I can, How do I do that?

Please Help.

Thanks In Advance.

---

### Post by ronnielsen1 on 2010-08-11
Remastersys

>  [COLOR=#000099]**Remastersys**[/COLOR] is a tool that can be used to do 2 things with an existing Debian,  Ubuntu or derivative installation. 
[LIST]
[*]It can make a full system backup including personal data to a live cd or dvd that you can use anywhere and install.
[*]It can make a distributable copy you can share with friends.  This will not have any of your personal user data in it.
[/LIST]


[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by farmerjohn73 on 2010-08-11
Thank u ronnie,

I will try that.

thank you very much.

I will post back the results. :D

---

### Post by varunendra on 2010-08-12
Or you may try [this]("http://ubuntuforums.org/showthread.php?t=819396").

I have no idea about remastersys but as per its description, it seems like it is a "Live" image of installed system, hence has some restrictions regarding drivers, etc.

So remastersys and what is suggested in the above link are different things (I believe), & thus one maybe advantageous over the other depending upon user's needs.

---

### Post by farmerjohn73 on 2010-10-03
I tried remastersys.  But it is not working.  It is creating a back up of all the packages of the disk but at the end of creating the I.iso, it says the larger than 4 gb is not supported.  And even if I try to create distro back up, it creates iso and a few other files like md checkusm etc and two folders like isotmp and casper.  but when I burn the .iso (which is about 1.2 gb), it is written onto the dvd.  But if I try to boot my laptop with CD, it is displaying a few options  but none of them working.

I tried the other way suggested by varunendra at [this link]("http://ubuntuforums.org/showthread.php?t=819396").  That option has also failed me at the point of making selections.  (pls see that thread [here]("http://ubuntuforums.org/showthread.php?t=819396&page=5") for my post.

I tried aptoncd also.  But that also did not work for me.  coz I think it is taking back up of only the software packages like firefox, chromium, rhythmbox etc.  and not the linux OS.

Can't understand what to do ...?

Somebody please help..

thanks in advance.

---

