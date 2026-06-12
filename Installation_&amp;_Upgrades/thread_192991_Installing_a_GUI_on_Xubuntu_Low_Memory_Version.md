---
title: "Installing a GUI on Xubuntu Low Memory Version"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by mtn on 2006-06-09
Hi,

I have installed Xubuntu 6.06 Dapper on an old P166. Installed fine in low memory mode and boots to the terminal fine. All well and good, but I need a GUI for the machine to be useful and I have no idea how to do this. Has anyone got ideas about installing or running a GUI from the terminal? Fluxbox sounds good, but I can't find info about getting it going.

For background info please see my thread about getting Xubuntu installed in the first place: [http://ubuntuforums.org/showthread.php?t=190920](http://ubuntuforums.org/showthread.php?t=190920)

Cheers

---

### Post by John.Michael.Kane on 2006-06-09
**[Blackbox Guide]("http://www.ubuntuforums.org/showthread.php?t=125084&highlight=Fluxbox")** **[fluxbox how-to]("http://www.ubuntuforums.org/showthread.php?t=116759&highlight=Fluxbox")**

---

### Post by confused57 on 2006-06-09
[QUOTE=mtn]Hi,

I have installed Xubuntu 6.06 Dapper on an old P166. Installed fine in low memory mode and boots to the terminal fine. All well and good, but I need a GUI for the machine to be useful and I have no idea how to do this. Has anyone got ideas about installing or running a GUI from the terminal? Fluxbox sounds good, but I can't find info about getting it going.

For background info please see my thread about getting Xubuntu installed in the first place: [http://ubuntuforums.org/showthread.php?t=190920](http://ubuntuforums.org/showthread.php?t=190920)

Cheers[/QUOTE]

Have you been able to enable your network connection?  I'm not familiar with using the console to configure a connection, but try doing a "title" search for "network connection"...maybe there'll be something there.  If not you could start a new thread asking how to enable it in the console & be sure to mention what type of connection you have...dial-up, broadband, DSL, cable modem, ethos card, etc...the more info you can give, the more apt you are to find someone who knows, you could try in this thread & if no response, then start a new thread.   You'll definitely need a network connection to install the LowMemory GUI.

You may want to look into Puppy Linux, the basic Live CD is about 40 Mb:
[http://www.puppylinux.org/user/readarticle.php?article_id=4](http://www.puppylinux.org/user/readarticle.php?article_id=4)
[http://www.puppylinux.com/](http://www.puppylinux.com/)

Another alternative for your server install, if you can't get your internet connection configured, may be to go into your souces.list and comment(put a # in front of) all the sources, except for the CD-rom, and install some base packages from the Xubuntu CD rom to get a GUI.  Have you tried installing the entire Xubuntu desktop?  You may be able have the CD as the only source & type in   sudo apt-get install xubuntu-desktop    at the prompt.
This is if you don't mind possibly doing the entire server install again, you'll find out if Xubuntu will run at all on your computer.

---

### Post by mtn on 2006-06-13
Thanks Confused for your help. I started a new thread about the network cards - [http://ubuntuforums.org/showthread.php?t=193887](http://ubuntuforums.org/showthread.php?t=193887) - and have spent hours searching about trying to figure it out. I finally found a link to a Linux driver for one of the cards (Compaq TLAN Netflex 3) but the link was dead :o(. I have tried the Debian install disks, Gentoo basic install CD and of course Ubuntu and Xubuntu and got no whrere. When I do ipconfig it is not there when I do ipgonfig eth0 it does show up but I guess it needs a driver/configured. I don't know how to do this and so am going to admit defeat this time (this does not come naturally). Maybe I'll have another look in the future.

Thanks again.

Mike

---

### Post by confused57 on 2006-06-14
Sorry you didn't get it working, it does take a lot of time; found this link, but seems you may need a Linux driver:

[http://tldp.org/HOWTO/Ethernet-HOWTO-1.html#ss1.3](http://tldp.org/HOWTO/Ethernet-HOWTO-1.html#ss1.3)

I don't know if you'll be back to read this, I know you still need internet access; but you may be able to get a GUI by:

```
sudo nano /etc/apt/sources.list
```

Make sure there's a # in front of everything that looks like a url & make sure there isn't a # in front of the CD-rom entry at the top...close & save.

Then run something like:
```
sudo apt-get install xdm x-window-system-core xfce4 mozilla-firefox synaptic
```

Something to play around with, when you have time...it probably won't work, but you can try if you feel adventurous...

---

### Post by John.Michael.Kane on 2006-06-14
confused57 I posted links for two guides for the OP one on Fluxbox one on BlackBox. which obviously he/she never looked at.  xfce may not be lite enough for he/she computer. since you, and OP seem to have things handle i'm off this thread.

---

### Post by mtn on 2006-06-14
Hey,

Thanks again. That link looks good. I'm heading of to study at Aberdeen for the summer so this Friday was my cut off for messing about with this box. I have had a lot of time the last few weeks to mess about which has been very interesting, not least just reading different forums. Fortunately I have an AMD64 running Ubuntu Dapper really well. I have not had an MS box for 10 months or so and Dapper has confirmed that there is no reason to go back, it is a fantastic OS. The only thing is that I'm going to look about for a mobile phone that is compatible. I also have an older laptop that Ububtu is a bit slow on. I tried Xubuntu but didn't like the GUI (and can't figure out how to change it to a different one) too much so am going to try and get Gentoo going and see if that is more suitable speed wise and if I like the OS generally. It is funny but I have found it hardest to figure out what should be basic things like changing GUI. I guess it is so basic it's just not written about or I have to just read the documentation!

It would have been nice to get the P166 going so I could pass it on to a friend and give someone else some exposer to Linux but that is the way it goes. I could maybe try and get a different network card but as I said, time has run out.

I really appreciate your time and effort and don't take it for granted at all. It must be a pain responding to all the noobs that are flailing around in the dark. The Ubuntu forum is a great resource and it feels to me there is a really positive vibe with Linux at the moment. Things are going to be good for us Linux user in the future I feel. I also think that a bit of effort spent now reconditioning to a Linux way of doing things will pay huge divides in the future (rest of my computing life) financially due to saving license fees etc, and the ability to have a really flexible OS. The apps on Linux are generally excellent, in particular Sound Juicer has allowed me to rip all my CDs to oggs in no time and is fantastically user friendly. Same goes for Acidrip these 2 apps alone have given me great joy ;) Not to mentioning all the core apps that get the daily jobs done well and with a clear conscience.

I was reading an article on this forum about the user friendliness of the terminal and found it really enlightening and for the first time I think I got a grasp on why the terminal is so good (it is my freind). But it also got me thinking about Linux in general and I had a bit of an epiphany that the real practical reason for using Linux and going down this path is that you end up with an OS that is totally flexible (not just one big splurge) and every user has their own system that suits there needs, this is truly fantastic. Of course I support open source and freedom software. I would not want to live in a house that that I was not allowed to change, other than maybe a coat of paint and that the owner could install listening bugs in every room and I would not be allowed to check if this was the case, charge me every time I went to the bathroom etc etc.

Anyway...rambling on now. I'll be around the forum.

Take it easy and thanks again,

Mike

[EDIT]
Oh, hey SD-Plissken. Just seen your last post, thanks. Il'll have a look at the links. Cheers

---

