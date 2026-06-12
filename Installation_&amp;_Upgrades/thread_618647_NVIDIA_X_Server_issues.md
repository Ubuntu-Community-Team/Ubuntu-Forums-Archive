---
title: "NVIDIA X Server issues"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by Holonet on 2007-11-20
I am having issues installing NVIDIA drivers.  I realize everybody and their brother has as well, and the topic has been covered, but I haven't found a solution to my particular problem.

Yes, I'm new to Linux, and I'm using Kubuntu.  I have a NVIDIA Geforce 7600 GS card, and I got the official driver off the website.  I know I can use sudo /etc/init.d/kdm stop to kill the X server (ctrl+alt+F1/backspace or both don't actually exit the X server, according to NVIDIA's installation package).

My problem is, once I've killed X, I'm left with a black screen and nothing but a cursor, no prompt or anything, and whatever I type does nothing--pressing enter just puts it on the next line, even ctrl+alt+backspace won't reset it, just gives me funky symbols.  It seems there is something, possibly obvious, that I'm missing, if anyone could give me a hand here, I'd be most appreciative.

---

### Post by Pumalite on 2007-11-20
Looks like a bug. You used the right command. It should give you a command line.

---

### Post by Pumalite on 2007-11-20
Try this:
Ctrl+Alt+F1
Login with your username
Password
Command line
sudo /etc/init.d/kdm stop
Run your driver
sudo /etc/init.d/kdm start

---

### Post by Holonet on 2007-11-20
Thanks for the reply.

Yeah, that's what I was doing, for the most part.  Same thing occurs.  I don't know what's relevant here, but I forgot to mention that when I stop the X server, the kubuntu startup logo comes up on the screen for about 10 seconds, then goes to that blank screen w/ cursor.

After that, like I said, nothing works, I can't run anything, it just goes down to the next line like it's a bloody word processor heh...  The ONLY thing that seems to do anything is pressing good ol' ctrl+alt+del, which it spits out some junk like K Display Manager stopping or something like that...kdm not running, then a bunch of stuff scrolls by and the computer restarts.

If it's relevant, speaking of bugs, another weird thing that happens (and has from the moment of install), is the sound always starts up muted.  If I remember correctly, this happened with regular ubuntu as well, which I tried previously.  Also, I have on-board sound but also a Sound Blaster Audigy SE card.  Without changing anything, it actually looks random as to whether kubuntu decides to spit my sound out through the board or the card!  Madness, I say...

If this is definitely a bug, what's the best way to fix it?  Should I get another copy of kubuntu (a recommended website would be great)?

EDIT:  Sorry, not muted, but with the volume all the way down.  Also, this is 64-bit dual core AMD 4200+

---

### Post by Pumalite on 2007-11-20
[http://mirrors.rit.edu/ubuntu-releases/kubuntu/gutsy/](http://mirrors.rit.edu/ubuntu-releases/kubuntu/gutsy/)

---

### Post by Holonet on 2007-11-20
Haha that's the site I got this off of...but there may be a detail...

I actually burned the CD with ubuntu when I was trying it, and twice, it gave me an error at the very end of the burn, and one time was at a slow speed.  Could that possibly have cause a bug like this?  It still booted and installed fine from everything I could see.

---

### Post by steveneddy on 2007-11-20
:-k  :-\"

---

### Post by Pumalite on 2007-11-20
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Do md5sum on your iso before burn, burn at 4x in good quality CD-R media

---

### Post by Holonet on 2007-11-21
Appreciate the input, but unfortunately, I just downloaded a new image from the site, hash checked out, so I burned it at the slowest speed I could, did a simulation and verified written data and all, then reinstalled kubuntu.  I even reformatted the partition (ext3) and such, and the very first thing I tried was to kill the x server, and the exact same thing I described before happens.

The volume is also acting the same way and booting up all the way down.  I don't care about that, but it doesn't seem like it's supposed to do that.

I'm forced to think that either there is a fundamental flaw in this distribution, or something on my machine is causing it.  The only other thing is I still have a Windows Xp (x64 Edition) installation (NTFS) on a different partition, but that partition has no errors, according to partition magic, and it certainly shouldn't have any effect here.  I'm stumped.

---

### Post by Newbie1978 on 2007-11-21
Well after a lot of frustration I discover that my new laptop don't work with Linux (hardware issues) this are my specs HP Pavilion Entertainment-center notebook PC DV6660se 64-bit 1.9 GHz AMD Turion 64 X2 TL-58 processor, 250 GB hard drive, 2 GB RAM Nvidia GeForce Go 7150 graphics if anyone manage to install a Linux distro in this model please help me

---

### Post by dream2xs on 2007-11-30
I too have an AMD dual core processor and I also get no prompt after sudo /etc/init.d/kdm stop.  However, I have found that when you are at that no prompt screen, hit ctrl-alt-F1 and you will get a prompt asking for your login then password.  after logging in you will get a prompt.

I am new to Linux and I am still learning.  I am wondering if this has something to do with libc as when I try to install the NVIDIA drivers, I get an error saying libc is not found.  I am still researching this issue.

---

### Post by Newbie1978 on 2007-12-03
Hello, I try again to install Linux Ubuntu in my HP dv 6660SE, unsuccessfully this time I use Ubuntu 7.10 Gusty, first I get a message "UBUNTU IS RUNNING IN LOW GRAPHICS MODE" I hit continue soon after I get "error microcode bcm43xx_microcode5.fw not available" some other time after the "UBUNTU IS RUNNING IN LOW GRAPHICS MODE" I try to configure the drivers for the graphics card and the screens with the same result and the same error message "error microcode bcm43xx_microcode5.fw not available" I think the problem is the graphic card, Please help me at this point I only have Linux at work. Thank you

---

### Post by Pumalite on 2007-12-04
[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

---

### Post by rakki on 2007-12-05
> **Newbie1978 said:**
> Hello, I try again to install Linux Ubuntu in my HP dv 6660SE, unsuccessfully this time I use Ubuntu 7.10 Gusty, first I get a message "UBUNTU IS RUNNING IN LOW GRAPHICS MODE" I hit continue soon after I get "error microcode bcm43xx_microcode5.fw not available" some other time after the "UBUNTU IS RUNNING IN LOW GRAPHICS MODE" I try to configure the drivers for the graphics card and the screens with the same result and the same error message "error microcode bcm43xx_microcode5.fw not available" I think the problem is the graphic card, Please help me at this point I only have Linux at work. Thank you

Hi, I've just same situation: HP Pavilion Media-center dv9643 notebook PC 
64-bit 1.9 GHz AMD Turion 64 X2 TL-58 processor, 160 GB hard drive, 2 GB RAM 
Nvidia GeForce Go 7150 graphics. The reason is prob. Nvidia: widescreen 1400*900.
Ubuntu 7.x runs well in my Desktop PC with NVIDIA GeForce 6200 TurboCache(TM).
"error microcode bcm43xx.." is related to WLAN: look at [http://ubuntuforums.org/showpost.php?p=3566393&postcount=7](http://ubuntuforums.org/showpost.php?p=3566393&postcount=7)

---

### Post by Pumalite on 2007-12-05
[http://ubuntuforums.org/showthread.php?t=431815](http://ubuntuforums.org/showthread.php?t=431815)

---

