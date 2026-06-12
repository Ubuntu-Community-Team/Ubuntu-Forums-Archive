---
title: "install works, startup fails consistently"
date: 2006-04-07
forum: Installation &amp; Upgrades
---

### Post by Cleotis on 2006-04-07
AMD_64 3500+
NVidia GeForce 6800
1GB RAM (dual-channel)
Asus A8N-SLI Deluxe
NForce4 Chipset
80GB SATA

Installation works fine, but on first boot, X starts and hangs predictably at a blank (brown or blue) screen, with an operable mouse cursor.  ctl + alt + F_ has no effect.  Waiting overnight for some hung process to start doesn't help.  
It doesn't matter whether I'm trying to install Breezy or Dapper, Ubuntu or Kubuntu, 32-bit or 64-bit, same result every time.  Live CDs all work flawlessly.  
Fedora, SuSE, and Gentoo all work fine; the problem doesn't seem to be kernel version-related.  (Debian 3.1 presents a whole other set of problems).  Installing in "server" mode is successful, but manually updating/upgrading and then installing X, NVidia drivers, and KDE produces the same lockup issue.

---

### Post by bscbrit on 2006-04-07
Can you start it in recovery mode?

---

### Post by Cleotis on 2006-04-07
I tried that once and got nowhere with it.  I haven't spent much time going down that path though.

---

### Post by bscbrit on 2006-04-07
I know, but it would give those who are trying to help you a clue as to where the problem might be.  If you can start in recovery mode, then the kernel and essential software are correctly installed and we can try to fix your problem.  If you cannot, then you will need to reinstall I think.  If you can't start it, you can't fix it (unless you want to try to use a live disk - and I don't know how to do that to fix this problem - or you believe that you can will the computer to start regardless of any problems :-D )

---

### Post by Cleotis on 2006-04-07
Ok, I'll try it again this evening and post the results.  (If I could will my computer to do things, I would will it to run Kubuntu, and then go fetch me some beer!)

---

### Post by Cleotis on 2006-04-07
Fixed it!
1. booted to rescue mode.
2. edited /etc/X11/xorg.conf:
    - changed driver from 'nv' to 'vesa'
3. Rebooted.

Apparently there's some kind of issue between the nv driver and my video card.  I don't understand why that would be limited strictly to the Ubuntu distro, but that's the way it seems.

---

### Post by Iain on 2006-04-08
I also have problems with the stock "nv" driver (GeForce4 MX4000), with pretty much the same thing: X would lock up after logging in. The driver provided by nVidia worked fine though.

---

### Post by bscbrit on 2006-04-08
Glad that you've solved it.  See you around the forum.  :D

---

### Post by ME-MY-I on 2006-04-12
[QUOTE=Cleotis]Fixed it!
1. booted to rescue mode.
2. edited /etc/X11/xorg.conf:
    - changed driver from 'nv' to 'vesa'
3. Rebooted.

Apparently there's some kind of issue between the nv driver and my video card.  I don't understand why that would be limited strictly to the Ubuntu distro, but that's the way it seems.[/QUOTE]

[color=#cc22ff]I assume you are talking about using "sudo nano /ect/X11/xorg.conf"
which took me to a blank screen.  I also accessed that folder with a live and changed it and still no stinking go.  Glad it worked for you.](*,) ](*,) [/color]

---

### Post by Cleotis on 2006-04-13
Not to be a stickler, but make sure you are typing 

"sudo nano /e**t**c/X11/xorg.conf"

instead of 

"sudo nano /**ect**/X11/xorg.conf"

---

### Post by ME-MY-I on 2006-04-14
I am not sure now which way I did it, but if I used the 2nd would I have not gotten an invalid or unknown command instead of a window with that line at the top.

[IMG]http://nwinfo.net/~sourkraut/img_0036.jpg[/IMG]

---

### Post by ME-MY-I on 2006-04-15
OK, I'm in!!!! Apparently I  had a faulty burn.  We'll see if it boots up later.  One certainly hopes so.  
:D :D :D

---

### Post by ME-MY-I on 2006-04-15
Well, did a restart and I once again out in the cold.
right back at square one..........no ubuntu](*,) :( :(

---

### Post by bscbrit on 2006-04-15
OK, in /etc/X11/xorg.conf, you have tried 'nv' and 'vesa'.  Have you tried 'nvidia'?  (I've re-read the thread but can't see anything to help answer that particular question)

Have you got an Ubuntu live disk that you can try - or, in fact, any other linux live disk?  Once you have a working system you can simply copy the xorg.conf that gives you the best results.

---

### Post by ME-MY-I on 2006-04-15
something in my set up apparently don't like ubuntu!
In disgust I reinstalled with the disk that just worked and gee - -brown screen --cursor works for 30 seconds and  then "frozen". 
 I'm at the point where I will just forget this for a month or two and maybe try again then.  Thanks for ideas

[color=#cc33ff]below is my system:[/color]
450 WATT POWER SUPPLY
GIGABYTE GA-K8U MB  ULi M1689 chipset	
AMD 64 Sempron 2800+ cpu socket 754
1 GIG CORSAIR RAM
WD 80 GIG HD 7200 rpm
MEMOREX DVD R/RW
CISCO AIRONET 350 WIRELESS PCI CARD  
ON BOARD 6.1 SOUND
AGP VIDEO nVIDIA GeForce4 MX 420 (rev a3)
WD 80 GIG HD - -FOR DATA ONLY
YAMAHA FR1 CD/RW
HP 7260 USB PRINTER
SEAGATE 160GIG EXTERNAL HD USB 
and of course the mouse and keyboard. 
On occasion I use a mircrosoft wireless mouse!

---

### Post by Iain on 2006-04-15
Are you actually using nvidia's drivers, as suggested?

---

