---
title: "Broken upgrade: libavahi-client.so.3: cannont open shared object"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by Rebajas on 2006-06-18
Hiya,

System upgrade offered me an opportunity to upgrade to Dapper yesterday and I took it. I left it to do its thing and when I returned the computer had frozen so I switched it off and rebooted. I had been out about 4 hours...

Anyway, on reboot I got some errors which Googling helped me to fix. Now though, I have this error and I can find nothing about it:

x-session-manager: error while loading shared libraries: libavahi-client.so.3: cannot open shared object file: No such file or directory

This is the last line in my ~/xsession-errors file, any ideas? This issue is stopping my boot up Ubuntu meaning I have to use my Windows machine!!? :)

Cheers.

---

### Post by Rebajas on 2006-06-18
Okay - I've been playing and think I have made some progress (Or things are much worse). I am now unable to get into Gnome at all though.

Unable to find a valid framebuffer device
NV(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

<OK>

In my log I see there are errors relating to folders called fb1 through to 7 with No such file or directory after.

I'll have a little search around the forum but if anyone can help with this then that'd be cool.

Cheers.

---

### Post by Rebajas on 2006-06-18
Blast - have gone round in a big hour and a half long circle! :)

Ignore middle post, I am back at the beginning again :(

Cheers.

---

### Post by catlett on 2006-06-18
Can you get into grub's menu? Is that how you are booting to windows? If you can get to grub, select "recovery mode" instead of the plain ubuntu selection. See if you can get in to your setup. Or at least see if you can get a command prompt.
If you can get a command line anywhere run an upgrade with aptitude```
 sudo aptitude update 
``````
sudo aptitude upgrade
``` If you get the command line with the recovery mode you won't need sudo, you will be root already.

If that doesn't get it back you might have to try variations ```
aptitude dist-upgrade 
``````
aptitude install ubuntu-desktop
``` You might get going but your x session isn't configured so you will have to do ```
sudo dpkg-reconfigure xserver-xorg
```

If you can't get in at all, I would retrieve anything valuable from windows and then download the install cd. I had a horrible dist-upgrade and lost my entire configuration. Only a clean install from disk got me up and running. I hope you have better luck.

---

### Post by Rebajas on 2006-06-18
I've just followed your commands and I am in Dapper now. I specifically had to run the aptitude install ubuntu-desktop by looks of it. I am just downloading more updates via the update manager. 

Thanks for your help.

PS: I'm not dual booted. I have every intention of moving to Linux entirely on my work machine but still have an XP laptop while I save for a MacBook. I am using that.

---

### Post by catlett on 2006-06-18
Great! It looks like the update didn't entirely get through. You should be alright now. But post if you have any errors.

P.S. If you are going to be moving to Mac you might want to dual boot Ubuntu with PC BSD. As I'm sure you know OSX in Mac is based on BSD. PC BSD is another version of bsd that was created to make it easier to install and run bsd.
I only mention it because you can really wow your iBook friends when you first get it and open the terminal and start running off commands:grin: 
Here's it's website. [http://www.pcbsd.org/](http://www.pcbsd.org/)  It is easy to install and maintain. The best thing is it has pre-packaged apps, so you can use it while you learn the more complicated end of bsd. You'll really be a renaisance person then. You will be mainstream with XP and OSX but you'll also be schollarly anbd counter-cultural with your understanding of linux and bsd.:grin:

---

### Post by Rebajas on 2006-06-18
Oddly enough I am looking to build a file server - low power SSH/Shell only affair. Would PC-BSD be good for that?

I have really just outgrown Microsoft - Intending that the only install I have of it is on my games machine. Plus too expensive to upgrade. I have nearly £500 worth of upgrade and install discs for Windows (95, NT, 2000, XP Pro)!?! Could have bought a pretty hot machine for that :)

---

### Post by catlett on 2006-06-18
I don't want to say it here:-$  But BSD runs lighter than linux. PC BSD has everything  Free BSD has but is easier to interface with. PC BSD to Free BSD is alot like Ubuntu to Debian.
Ubuntu is Debian modified so it can be easily installed and used by linux novices. It still has all the capabilities of Debian if you want them. You can easily run a server off of Ubuntu.
Likewise with PC BSD it is based on Free BSD but has been modified to make it easier for bsd novices to work with. (I still haven't been able to install Free BSD. It has an incredibly unfriendly text installer. With no guidance for how to create slices and format them) 
The BSD's are true unix systems. So PC BSD  can definately handle server duty. There is plenty of documentation and forums. (bsd was one of the first off shoots of unix. bell labs wasn't allowed to make a profit from unix so it gave the code to some iniversities. Berkeley being one. They made their own variation of unix - [COLOR="Red"]B[/COLOR]erkeley [COLOR="Red"]S[/COLOR]oftware [COLOR="Red"]D[/COLOR]istribution) It is a solid system,  I just haven't gotten to spend alot of time with it.
Follow the link to PC BSD's website. You can also google Free Bsd to get the links for that.

Don't get me wrong, Ubuntu can handle anything you want it to, I just thought you might like bsd because OSX is based on it. 
As long as you're away from Gates you are doing alright.:p

---

### Post by Rebajas on 2006-06-18
Well - i'll definately look into that then. Sounds very promising.

I had Mandrake before on my desktop and just couldn't get on with it - I think it was more a case of I didn't like KDE than anything else, Gnome is so much more streamlined! I like the idea of a 'shell only' machine as I am a web developer and am used to looking after machines on the CLI rather than with GUIs. You know where you are when someone says 'open a terminal and type... etc' over explaining your way through 10 stages of wizard :)

Anyway, thanks again for your help.

---

