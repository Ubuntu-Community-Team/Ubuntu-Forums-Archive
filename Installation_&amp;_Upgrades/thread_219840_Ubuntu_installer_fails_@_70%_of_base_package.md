---
title: "Ubuntu installer fails @ 70% of base package"
date: 2006-07-20
forum: Installation &amp; Upgrades
---

### Post by RandallC on 2006-07-20
Hi there,
I have been trying to install 6.06 for a while now, without success.  Here's a rundown of what I've tried.

First, I downloaded the desktop CD iso.  I was able to successfully boot into linux off the disc, but when I click on the install shortcut on the desktop it either becomes unresponsive immediately or it will let me choose my language then become unresponsive.  

After failing to get that working for a while, I downloaded the alternative install CD and tried a text-based install.  It worked!...up to 70% of the base package.  Then it gives an error about the installer being unable to install the base package and I can not continue.  Each time it dies exactly at 70%.

Does anyone have any ideas?  I'd really like to try out the latest Ubuntu but if I can't sort this out this evening I'm going to have to put Windows back on the machine...

Thanks!

---

### Post by jordilin on 2006-07-20
Perhaps is a hardware problem. Tell us what kind of hardware do you have. Take a look at your BIOS setup, to see all is ok, just in case.

---

### Post by RandallC on 2006-07-20
Sure.  I'm running a Shuttle SN45G with an XP2800+ and a gig of ram.  The DVD rom is a NEC 3500A, and I have 2 HD's, an 80 gig maxtor and a 120 gig Western Digital.

---

### Post by RandallC on 2006-07-20
Anyone?  I'm formatting in 3 hours, here's hoping for a solution or suggestion by then!

---

### Post by Aranel on 2006-07-20
I've had *exactly* the same problem, except in my case the alternate installation stopped at 60%. I'm now trying, with some difficulty, the [installation from Knoppix](https://help.ubuntu.com/community/Installation/FromKnoppix) method. You may have more luck at it than I have thus far had...*indicates his thread*

---

### Post by RandallC on 2006-07-20
> **Aranel said:**
> I've had *exactly* the same problem, except in my case the alternate installation stopped at 60%. I'm now trying, with some difficulty, the [installation from Knoppix](https://help.ubuntu.com/community/Installation/FromKnoppix) method. You may have more luck at it than I have thus far had...*indicates his thread*

Cool.  Can you link me your thread?

---

### Post by RandallC on 2006-07-20
OK, I'm trying the Knoppix method.  I get to making debootstrap and...I get "Input/output error".  What am I doing wrong?  I'm following all the instructions as given in the above link.

---

### Post by RandallC on 2006-07-20
This is ridiculous.  Ubuntu gets a black mark, and I'm going back to Windows.

---

### Post by nreddyk on 2006-07-20
Hi,

I have exacly the same problem with live CD and Alt. install. It either gets struck at 70% with a bootstrap error or just freezes.
 
Now I get an input-output error even before linux kernal is installed. So now i can't even get my computer to run the live CD.
 
I am trying to install ubuntu on HP 6730 with 600 MHz Intel Celeron processor and 192 RAM 10 GB Hard drive.

Ubuntu just refuses to install even after removing all trace of Windows and reformatting and partitioning the drive using GParted.

Should I give up? I dont want to because I run it on my Toshiba and love it.

Please Help.

---

### Post by K.Mandla on 2006-07-21
Has anyone tried a server installation?

I had a problem on an ancient laptop that would freeze part-way through a full Ubuntu installation. But I could finish a server install, then *sudo apt-get install ubuntu-desktop* for what I missed.

> **RandallC said:**
> This is ridiculous.  Ubuntu gets a black mark, and I'm going back to Windows.
Thou doth protest too much, methinks. 

Give it another shot. If you need an instant answer, try the Ubuntu chat. And [remember]("http://www.ubuntuforums.org/showthread.php?t=82471"). ...

[quote=aysiu]People here are very supportive and helpful when they can be. I'll tell you that 99% of the time when threads remain unanswered it's because no one knows the answer. Either your problem is too obscure, your hardware is too obscure, or the program you're having problems with is too obscure.[/quote]

---

### Post by cobray on 2006-08-29
Hi everybody,
I just installed Ubuntu 6.06 desktop CD on my SN45G and it rocks.
I have a Geforce 6800 AGP card and a 3com NIC.
I was able to get everything running including sound and 3d acceleration.
sound worked out of the box.
I did everything from System->Administration->Synaptic Package Manager.
All audio and video is working for MP3,MPEG,AVI, and some of my WMA and WMV files work (but not all)
The only problem I have left is I am having trouble setting the 6 channel surround sound.  Only the 2 front speakers work.  I tried changing all the settings in the volume control panel and nothing works.
There is plenty of information on this forum.
I love my Ubuntu system if they would port Battleground Europe to OpenGL on Linix I would toss my Windows machine.
Unfortunately I wish driver development and hardware recognition could be better but this rocks.

---

