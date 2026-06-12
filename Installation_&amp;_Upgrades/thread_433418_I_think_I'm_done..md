---
title: "I think I'm done."
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by DNSBubba on 2007-05-04
I've tried for the better part of two days to get Ubuntu (FF) up and running, with somewhat limited success. My problems are in two areas, neither of which I can seem to get past.

1. Ubuntu will install from the DVD drive in my system, but once installed, it won't boot as long as that drive is working. In order to get it to boot, I have to disconnect the power from that drive. Not really a deal killer, but a royal pain nonetheless.

2. Here's the biggie. If I attempt to use the fglrx driver, I get the "boot to black" issue. The system boots to a black screen once I install that, and there doesnt seem to be a way out of it. I've tried everything I can find on the board's to correct it, including downloading and using the alternate install CD to do a text based install. That DID solved my resolution issue, but acceleration is a no show. I won't be using the Linux install for games, but still it's a pain that it won't work.

My Video Card is a ATI X1600 by the by.

Any suggestions would be greatly appreciated. Right now, the Ubuntu partition is just sitting there, as I can't get past that black screen.

---

### Post by ticopelp on 2007-05-04
That's unfortunate. I don't have the technical expertise to suggest much -- it does seem that in general, ATI cards and Ubuntu don't seem to get along well at all. I've had a couple of friends try to install Ubuntu using ATI cards and have a lot of issues. 

I don't know if "buy another video card lol" will really help you much, of course. :)

---

### Post by phidia on 2007-05-05
Sorry to hear you're having problems. I'm not sure why the optical drive would need to be disconnected to boot. How is your dvd connected? i.e ide, sata? What happens when you try to boot with the drive powered up?

On the ati drivers-it looks like support is improving even though alot of us use nvidia. Have you tried the drivers from the ati site? [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

"The black screen" have you tried opening a terminal? Press Alt+Ctrl+F1 keys together/at the same time.
then type sudo dpkg-reconfigure xserver-xorg for a video driver try ati or even vesa to get a basic screen working.

---

### Post by trents on 2007-05-05
On my system whenever I install the firegl drivers to give 3D to my Radeon 9700 pro I start to have various problems, chief among which is that certain aps will no longer load, like Open Office or K3b. This has been the case with Dapper, Edgy and FF.

Steve

---

### Post by tgalati4 on 2007-05-05
The drive problem could be due to a jumper setting on either the DVD drive or another device on the same ribbon cable.  The Live CD probably uses a simpler hardware detection algorithm, whereas the full boot tries to enumerate everything.  If there is a bus conflict, then that will cause a problem.  Try moving the jumpers around.  

For the ATI card, a forum search will pull up several ideas.  Unfortunately it takes some time to try each one.  Make backups of your /etc/X11/xorg.conf file because you may need to restore it after an xserver crash.

The good news, once you get it working, you can post and save someone else from this configuration file hassle.

Good luck.

---

### Post by DNSBubba on 2007-05-05
Thanks to everyone for replying. I've tried pretty much everything suggested (expect for the bus factors for the drive) to no avail.

I do have another box with a GeForce 6200 that I could attempt an install on, but I was hoping to do it on the ATI box. It's a PCI-Express card, and I was hoping for the performance. The Geforce box is AGP, which would be acceptable for what I'm going to be doing (Mostly basic stuff. Internet use, word processing, Linux education, etc.).

Any thoughts or known issues with that card that anyone is aware of?

Again, thanks to all who replied.

---

### Post by DNSBubba on 2007-05-05
> **tgalati4 said:**
> The drive problem could be due to a jumper setting on either the DVD drive or another device on the same ribbon cable.  The Live CD probably uses a simpler hardware detection algorithm, whereas the full boot tries to enumerate everything.  If there is a bus conflict, then that will cause a problem.  Try moving the jumpers around.  

For the ATI card, a forum search will pull up several ideas.  Unfortunately it takes some time to try each one.  Make backups of your /etc/X11/xorg.conf file because you may need to restore it after an xserver crash.

The good news, once you get it working, you can post and save someone else from this configuration file hassle.

Good luck.

The jumper setting was hosed. I have two IDE channels, with the DVD drive on the primary and the HD on the secondary. I switched the jumper on the DVD to Master, and that solved it. Thanks mucho!

---

### Post by tgalati4 on 2007-05-05
I LOVE it when a plan comes together.

Can't help with the video.  I did try SUSE 10 (SLED 10) and it's default video driver worked great on an old Dell GX1 with a crappy, on-board, S3, 8MB video chip.  I was able to get 1280 by 1024 in 24 color at 100 Hz!  With Dapper, I was only able to get 75 Hz.  Don't know why.  I tried fiddling with H and V refresh rates in the Monitor description, but it wouldn't go above 75 Hz.

The bottom line:  Don't feel constrained by Ubuntu.  There are a good 10 to 15 popular Linux distros out there.  Find one that works with your hardware.  Capture all of the /etc configuration files (xorg.conf, modules, etc--gee I wonder why they call it etc?)  Then try Ubuntu again armed with your configuration files (printed out of course).  You may have better luck.

SUSE is a great distro.  It's just difficult to install deb packages where all the neat stuff is being developed.  You can't underestimate the power of the Debian package management system that Ubuntu is based on.

Try a wider Google search for your video card and Linux and see what distros come up.  Then try that distro first.  If it works, then you will appreciate Linux even more.  To save yourself from downloading several CD's, do a search for a local Linux group.  Go to one of their meetings.  You may be surprised by the support.

---

### Post by DNSBubba on 2007-05-06
Ooookkkaaayyy. Well, the drive did work, until I rebooted the machine. Now, it won't boot with the drive connected again. 

I did a fresh install (Alternate CD, text based) and it still won't boot with that drive attached again.

Later today, I'll be doing an install on a box with a generic CD-ROM/Burner drive (As opposed to this one, with the DVD drive) and a GeForce card, so we'll see how that one goes.

The comment concerning other distro's is well noted. But, I was hoping to get to know Ubuntu quite well, so I could recommend and install it for friends and family.  Given it's ease of use (Once properly configured) I was somewhat on a mission to convert my entire family to Linux. :)

---

### Post by tgalati4 on 2007-05-06
The controller chip on the DVD could be going.  The laser diode could also be crapping out.  Either one will lead to intermittent bus errors that can freeze the machine.  Put your finger on the controller chip of the DVD.  If it is super hot (as in you can't keep your finger on it, consider it hosed.)  If it is made by a company that you can't pronounce, then that would add confidence to the previous assessment.

The only reason that I recommend trying other distros is that some detect unusual/older hardware better than others.  What good is Ubuntu if you can't get full video resolution or sound to work?  If the Live CD of any distro doesn't work out of the box, an install of it won't automatically fix those problems.  You will have to fix them yourself.

First try a Dapper 6.06.1 Live CD.  If that works, then install it so you have a working machine.  Afterall, it's only an operating system.  You really need something stable so you can play will all of the Linux applications.  That is where the power is.

Don't let a new distribution delay your access to the 18K packages available.

---

### Post by DNSBubba on 2007-05-07
Just posting an update. I finally got around to installing Ubuntu on my box with the Nvidia card (6200), and it went flawlessly. It sees all drives,  the card driver installed without a hitch, and I was even able to enable Desktop Effects with no problems (The wobble and cube effects literally made me laugh out loud).

The only thing I have left to do is find a way to up the resolution just a bit, but I can live with 1024x768 if I have to.

So, what I have learned so far? If at all possible, install Ubuntu on a box with an Nvidia card. It will save you loads of aggravation.

Also, make sure the jumpers on your drives (assuming they use them, i.e. non-SATA) are in a traditional master/slave setting. This will also save you a ton of headaches.

Really looking forward to delving more into Ubuntu, now that I have a good install going.

Thanks again to all who replied,  especially to **tgalati4**. Friendly support is always a blessing when your delving into something new, even for an old IT dog like me.

Thanks much.

---

### Post by tgalati4 on 2007-05-07
Great, now you can help others.  I'm tired.

With 3D effects, you may need to keep a lower resolution so that the desktop will fit within the video memory space.  If you go to higher desktop resolution, you will get a nice desktop, but then lose 3D.  Most games take advantage of this by running at a lower resolution, but then you don't really care as long as the game works.

ATI cards do work with Ubuntu, they are just fiddly.  You need to find the right combination of distro/driver/xorg.conf and you are golden.  Some ATI cards are more troublesome then others.

I've notice on the forums about 1000 registered users vs 4000 lurkers.  That's 20%  Not bad.  At least it's not  3% helping the other 97%.

You will quickly forget your initial setup frustration when your machine works for months on end without a reboot or even a hiccup.

---

### Post by DNSBubba on 2007-05-07
> **tgalati4 said:**
> Great, now you can help others.  I'm tired.

With 3D effects, you may need to keep a lower resolution so that the desktop will fit within the video memory space.  If you go to higher desktop resolution, you will get a nice desktop, but then lose 3D.  Most games take advantage of this by running at a lower resolution, but then you don't really care as long as the game works.

ATI cards do work with Ubuntu, they are just fiddly.  You need to find the right combination of distro/driver/xorg.conf and you are golden.  Some ATI cards are more troublesome then others.

I've notice on the forums about 1000 registered users vs 4000 lurkers.  That's 20%  Not bad.  At least it's not  3% helping the other 97%.

You will quickly forget your initial setup frustration when your machine works for months on end without a reboot or even a hiccup.

I wasn't aware of the resolution restrictions regarding the 3D effects. Good to know. However, I've disabled them anyway, as they had some weird consequences that I didn't want to deal with. 

Thanks again.

---

### Post by wpshooter on 2007-05-07
> **DNSBubba said:**
> The jumper setting was hosed. I have two IDE channels, with the DVD drive on the primary and the HD on the secondary. I switched the jumper on the DVD to Master, and that solved it. Thanks mucho!

Have you tried putting the hard drive on primary socket jumper as MASTER and the CD-Rom on the secondary socket jumpered as MASTER ?  That is the way that I would set them.

I think your problem with the video is that you need to install the fglrx drivers from Synaptic Manager and then edit the video card driver setting in your /etc/X11/xorg.conf file from "ATI" setting to read "fglrx".

Good luck.

---

### Post by DNSBubba on 2007-05-07
> **wpshooter said:**
> Have you tried putting the hard drive on primary socket jumper as MASTER and the CD-Rom on the secondary socket jumpered as MASTER ?  That is the way that I would set them.

I think your problem with the video is that you need to install the fglrx drivers from Synaptic Manager and then edit the video card driver setting in your /etc/X11/xorg.conf file from "ATI" setting to read "fglrx".

Good luck.

Thanks for the suggestions, but I had already tried the fglrx driver when I called it quits on that particular system. Now that I've got Ubuntu installed on my other box, I'm no longer working on the one with the ATI card. 

I'll just leave that one as an XP box.

---

### Post by tgalati4 on 2007-05-07
You can sometimes get higher 2D resolution by tweaking your monitor in xorg.conf

Section "Monitor"
        Identifier      "Dell IBM OEM LCD Display with new hinge"
        Option          "DPMS"
        HorizSync       30-67
        VertRefresh     50-75
EndSection


Just extend the upper values of HorizSync and VertRefresh.  Then add "1280 x 1024"  to your modes.

Close all of your applications, control-alt-backspace,  and wait the the desktop to come up again.

Save a backup copy of xorg.conf first.

---

### Post by orb9220 on 2007-05-07
Then add "1280 x 1024" to your modes

Yep just open your xorg.conf file and insert it in front of the "1024x768"  in each depth line for 16 and 24bit modes.

---

### Post by DNSBubba on 2007-05-09
Update*

Well, I got the resolution working, using the suggestions mentioned here. Mucho thanks for that. Now, if I can just work out this mouse issue...:)

---

### Post by DNSBubba on 2007-05-10
*Update*

Last update for this thread, from me at least.

DOES TAP-DANCE OF GEEKISH JOY!!!!

I got Beryl working. HOW FLIPPIN COOL IS THAT THING?!

I swear, everyone I've showed it to, and I'm showing it to EVERYONE, now wants their own Ubuntu disk! I've burned 3 just today for family and friends.

And then, to top it off, I found out about desklets. That is just handy as heck.

I'm in such a state of nerdish joy, I don't even care about my mouse issue at the moment. :)

---

### Post by ticopelp on 2007-05-10
Awesome to hear, DNSBubba. I love Beryl as well -- it not only looks pretty, but it's tremendously handy.

---

### Post by Dave67 on 2007-05-10
Hmm 

If I read this post right you have a HD on the secondary IDE  and it is mainly your primary drive right? ok if this is the case this will not work change your HD to the first IDE and set it as master than have your CD/DVD drive
on the second IDE as a master. 

the computer can not have to masters devices on the same channel both devices will conflict for the primary
master. one master device for each channel. 

I have 2 HD the slave is Ubuntu and the primary is win2000 pro, my CD/DVD is on the secondary channel as  master.

---

### Post by DNSBubba on 2007-05-10
> **Dave67 said:**
> Hmm 

If I read this post right you have a HD on the secondary IDE  and it is mainly your primary drive right? ok if this is the case this will not work change your HD to the first IDE and set it as master than have your CD/DVD drive
on the second IDE as a master. 

the computer can not have to masters devices on the same channel both devices will conflict for the primary
master. one master device for each channel. 

I have 2 HD the slave is Ubuntu and the primary is win2000 pro, my CD/DVD is on the secondary channel as  master.

Thanks for responding, but that issue was already fixed. I have two IDE channels, with the HD on one and the CD-Rom on another. For some reason,  Ubuntu  simply didn't like the CD-Rom being on cable select, and wouldn't see it. Once I changed it to master, for that channel, it was fine.

It's always the little things isn't it? Thanks for being willing to help. :)

---

