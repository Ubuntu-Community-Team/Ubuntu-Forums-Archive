---
title: "Installing Xubuntu/Ubuntu on Alienware M9700"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by raymondes on 2008-03-13
Hello Forums,

I have an Alienware M9700 Laptop.
Specs:
Windows XP Media Center Edition
AMD Turion 64 Mobile ML-37
2 Nvidia GeForce Go 7900 GS's in SLI
80GB 7200 RPM HDD (/w a 15 gig partition for Linux)
2GB RAM (dont remember the speed or specs)

I have tried numerous times to install both Ubuntu 7.10 and Xubuntu 7.10. Every time i try to boot it up using the LiveCD I see a loading screen and then nothing. I have tried installing the Nvidia drivers using the console but that didnt help either.

Can anyone please help me get Ubuntu/Xubuntu(preferably Xubuntu) installed on my laptop. I desperately want to get it installed.

I would be willing to chat over AIM/MSN or via email just to get this problem fixed.

Please help me

P.S. Sorry for the bad spelling/grammar

---

### Post by Rocket2DMn on 2008-03-13
The LiveCD doesn't work for everybody, often because it doesn't have the video drivers to support some hardware.  You can install with the alternate install cd which is a text based installer without a live session, but it is easy to use.  You can get it at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) by checking the box at the bottom for the alternate cd.

You may have problems setting up your SLI, and it might help to disconnect one of the cards during install.  You will need to use the restricted nvidia drivers to use SLI I think.

---

### Post by Wompus on 2008-03-17
I'm also using an m9700, the main problem I've found is getting Gutsy to recognize the raid array.

To get the graphics working, boot from the Live CD with your volume knob turned up.

Once you hear the ubuntu sound press Ctrl-Alt-F1

Type "sudo killall gdm"
         "cd ../../etc/X11"
        "sudo nano xorg.conf"

scroll down until you see the entry for the Nvidia Geforce Go 7900 GS
change the line that looks like this         "6:0:0:0"
To this                                                    "7:0:0:0"

press ctrl-o
press rtn
press ctrl-x

type "cd ../../"
type "sudo /etc/init.d/gdm restart"

You should now load into the desktop.

If you manage to carry out the install, I'd imagine that you'd have to carry out the above operation once booting from the hard-drive. But only once.

Hope this helps.

---

### Post by raymondes on 2008-03-18
Hey,

I havent tried that (previous post), but what would go inplace of the '...' would that just be the directory where the driver is.

What driver should i use and how should i go about putting it on my pc so linux could use it.

Im very new to linux and need to be babied thru it lol.

---

### Post by raymondes on 2008-03-19
> **Wompus said:**
> I'm also using an m9700, the main problem I've found is getting Gutsy to recognize the raid array.

To get the graphics working, boot from the Live CD with your volume knob turned up.

Once you hear the ubuntu sound press Ctrl-Alt-F1

Type "sudo killall gdm"
         "cd ../../etc/X11"
        "sudo nano xorg.conf"

scroll down until you see the entry for the Nvidia Geforce Go 7900 GS
change the line that looks like this         "6:0:0:0"
To this                                                    "7:0:0:0"

press ctrl-o
press rtn
press ctrl-x

type "cd ../../"
type "sudo /etc/init.d/gdm restart"

You should now load into the desktop.

If you manage to carry out the install, I'd imagine that you'd have to carry out the above operation once booting from the hard-drive. But only once.

Hope this helps.

OMG I used this guide exactly and it worked PERFECTLY. Many thanks to you and your family!!!! lol *THANKED*

---

