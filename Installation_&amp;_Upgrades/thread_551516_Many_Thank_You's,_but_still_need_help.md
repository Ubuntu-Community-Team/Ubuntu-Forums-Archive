---
title: "Many Thank You's, but still need help"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by iheartubuntu on 2007-09-15
First off, I would like to thank everyone here on the message boards for guiding me along with my troublesome install. I managed to pull through, figured out why I was getting various errors, and fixed them.

That said, once I had a working Ubuntu ALT system up and running on an older PIII, I've so far enjoyed working with it.

Ubuntu ALT boots up very quickly on my PIII-900mhtz laptop, with 256 ram. How quickly? Faster than my XP computer which is a dual core 2.40ghtz desktop with 4gb RAM and 512mb video card! Of course once inside each operating system, the new desktop is really quick, my slow laptop is, well, slow, but still works pretty good. In fact im using it right now.

Some thoughts...

-For me, this isnt ready for primetime whereas I can go around and tell people about it and get them to switch over to Linux. Im fairly adept at computers, some programming, lots of networking, etc, but Ubuntu was a bit difficult at first. I look forward to the day I can get friends and family to use this.

-I dont know if in the regular newest Ubuntu out there makes it easy to get needed drivers, but I spent well over half the day yesterday learning that I needed drivers, where to get them, how to get them, how to install them, how to use them, etc just to get "sopcast" working. It was a royal pain in the ***. I must say, I did learn a heck of a lot about using the terminal, synaptic, etc. But Ubuntu needs to offer a link to these common drivers somehow. Everyone is gonna need them at some point.

-Does Ubuntu have a Guide to cover all these HIGHLY important things like terminal access, drivers, etc? I never came across one. It would be interesting to read.

-That brings me to another point. So many different command lines I probably should make a little folder with all the different commands I need to learn for using the terminal. This is far from XP. Its almost a bit archaic to have to go into a terminal and input some commands. I feel like Ive flown all the way back to DOS days.

[COLOR="Green"]Now Questions...

-if I download software (tz file or whatever it is) from a website, how do I properly install it? Ive used so many different commands in the last 24 hours, I can safely say I still dont know how to do this. Im not talking about Synaptic or the Add/Remove stuff. Im talking about Ive got the program or files on a folder made for Linux, where do I put that folder on my computer now and how do I install it?

-for me to make the full switch to Ubuntu (which I plan to do eventually), I'll still need some windows programs and for that I understand I need WINE or similar program to use the win-based files. Ive got WINE installed, now how the heck do I access one of those programs using WINE? Wine has to be used from the terminal? No GUI for wine?

-How do I make a link on the desktop for a windows program running through wine?

-I dont have a 3D card on my old laptop here... I think its only a 8mb or 16mb intel video card, so I probably dont have access to OpelGL, thus my fave backgammon game, GNUbg, doesnt work. I also think the backgammon program "Kbackgammon" for linux sucks. Does anyone else know of any other good "user vs. PC" backgammon games I can try?? I dont think Kbackgammon even allows user against a computer either.

-file structure. Im still not quite understanding this since I grew up with DOS and WIN, so please help me understand linux if you can. In linux, is there a c: drive? or is that just now called "file system" basically? What if I install a windows program to use through WINE, where does it put it in my file system? Ive seen people referring to typing "c:\****" to access windows programs through the terminal (still dont undertand wine), but where is c:\ on my hard drive or file system?

-lastly, once I get all my major problems and challenges solved, Ive got a P4 laptop with 2ghtz and 2gb RAM, 128mb video card, 80gb HD, sitting at home I use mostly for website programming (dreamweaver,flash,fireworks,illustrator,photoshop,etc). That is my next system I would like to put Ubuntu on, but not ready to just go 100% ubuntu. Can someone walk me through or direct me to a dual boot setup / weblink so i can do dual boot on that system? Ubuntu and XP? Ive looked all over the forums here and elsewhere online, and cant quite find something easy to understand to set up a dual boot.[/COLOR]

Thanks again for all the help and support. I enjoy the forums here and hope to one day be able to contribute more!

[COLOR="Green"]One more thing! Sorry, Im trying to click a sop:// link on a website, and have it open with my sopcast program, but firefox tells me it doesnt know how to open this address since "sop" is not associated with any program. How do I go about associating this with my sopcast program?[/COLOR]

---

### Post by maybeway36 on 2007-09-15
the wine "C:" is in ~/.wine/drive_c.
And if you download a linux program from a website, its usually source code which you have to compile. In my opinion, if its not in APT, its not worth it.

---

### Post by tgalati4 on 2007-09-15
Linux does have a learning curve.  Loan the laptop to one of your family members and get their impressions.  Once it is set up, it's not difficult to use.

---

### Post by Pumalite on 2007-09-15
You are all set man; you have it installed!. And once you have it installed the most fun is to learn how to use it. Trial and error is fine. You learn a lot. Besides, like in everything else; it's the road that matters, not what awaits us at the end. Learn to delay gratification and Linux will be a growing experience.

---

### Post by iheartubuntu on 2007-09-15
The questions I have ([COLOR="Green"]highlighted above in green[/COLOR]), I am having trouble finding answers to them. If anyone has some ideas for me, I would be very grateful! These are the key points Im having a lot of difficulty with. Otherwise, Im starting to get it (i think).

---

### Post by aysiu on 2007-09-15
> **shirteesdotnet said:**
> -I dont know if in the regular newest Ubuntu out there makes it easy to get needed drivers, but I spent well over half the day yesterday learning that I needed drivers, where to get them, how to get them, how to install them, how to use them, etc just to get "sopcast" working. It was a royal pain in the ***. I must say, I did learn a heck of a lot about using the terminal, synaptic, etc. But Ubuntu needs to offer a link to these common drivers somehow. Everyone is gonna need them at some point. Unless you have incompatible hardware, you shouldn't have to manually install drivers. All the drivers are included in the Linux kernel itself. There are some exceptions; for example, proprietary drivers (Nvidia or ATI, for example) cannot be distributed with the Linux kernel, so Ubuntu has created a "Restricted Drivers Manager." More details [here](http://www.psychocats.net/ubuntu/nvidia).

> -Does Ubuntu have a Guide to cover all these HIGHLY important things like terminal access, drivers, etc? I never came across one. It would be interesting to read. [http://www.ubuntuguide.org](http://www.ubuntuguide.org) and [http://www.psychocats.net](http://www.psychocats.net) and [http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing) are some good places to start.

> -That brings me to another point. So many different command lines I probably should make a little folder with all the different commands I need to learn for using the terminal. This is far from XP. Its almost a bit archaic to have to go into a terminal and input some commands. I feel like Ive flown all the way back to DOS days. [http://www.ubuntuguide.org](http://www.ubuntuguide.org) puts all the commands in one place. If you're following a guide, use your mouse to right-click and copy the command and then right-click and paste the command into the terminal. No reason to retype commands.

> -if I download software (tz file or whatever it is) from a website, how do I properly install it? Ive used so many different commands in the last 24 hours, I can safely say I still dont know how to do this. Im not talking about Synaptic or the Add/Remove stuff. Im talking about Ive got the program or files on a folder made for Linux, where do I put that folder on my computer now and how do I install it? Read [this](http://www.psychocats.net/ubuntu/installingsoftware).

> -for me to make the full switch to Ubuntu (which I plan to do eventually), I'll still need some windows programs and for that I understand I need WINE or similar program to use the win-based files. Ive got WINE installed, now how the heck do I access one of those programs using WINE? Wine has to be used from the terminal? No GUI for wine? Read [this](http://www.psychocats.net/ubuntu/wine)

> -How do I make a link on the desktop for a windows program running through wine? Right-click the desktop and select *Create Launcher* and put in the appropriate command. See the link above.

> -file structure. Im still not quite understanding this since I grew up with DOS and WIN, so please help me understand linux if you can. In linux, is there a c: drive? or is that just now called "file system" basically? What if I install a windows program to use through WINE, where does it put it in my file system? Ive seen people referring to typing "c:\****" to access windows programs through the terminal (still dont undertand wine), but where is c:\ on my hard drive or file system? The top-level folder is /

Every folder lives underneath that. There is no C:\, D:\, E:\, etc.

> -lastly, once I get all my major problems and challenges solved, Ive got a P4 laptop with 2ghtz and 2gb RAM, 128mb video card, 80gb HD, sitting at home I use mostly for website programming (dreamweaver,flash,fireworks,illustrator,photoshop,etc). That is my next system I would like to put Ubuntu on, but not ready to just go 100% ubuntu. Can someone walk me through or direct me to a dual boot setup / weblink so i can do dual boot on that system? Ubuntu and XP? Ive looked all over the forums here and elsewhere online, and cant quite find something easy to understand to set up a dual boot.[/COLOR] Read [this](http://www.psychocats.net/ubuntu/installing).

---

### Post by iheartubuntu on 2007-09-15
Many thanks aysiu for the help! I'll be learning all weekend long!

---

### Post by trippinnik on 2007-09-16
sopcast usually needs to be run from the command line.  the readme included in the package explains more about it.  But there are two commands to run in the terminal.  the first starts the connection, sets the channel and set the port number to use.  the second is for your video player to recieve the connection at that port number.

---

