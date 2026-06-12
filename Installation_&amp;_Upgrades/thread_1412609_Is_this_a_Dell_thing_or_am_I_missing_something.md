---
title: "Is this a Dell thing or am I missing something?"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by Drewmusk on 2010-02-21
Okay here goes.  I have a friends Dell 4500s ( a 2.0g P4 with only 256 MB) I can not get  Ubuntu on. He has a fresh install of Windows XP Professional ( unregistered )   So I know this thing works, so does the CD and floppy drive and the network thru the Rj45.  I went to Bios to switch Boot order to floppy first, CD second, and hard Drive third.  When i start it with the Ubuntu CD it goes right to boot the Hard drive in XP. When I put in the sure fire Fedora 9 it boots the hard drive to XP. With a Dos 6 disk in I get an A: prompt.  When I type c: or d: or e: I get bad command or file name.  I wanted to format the hard drive like I have done on many computers over the years. What gives? 

Does Anyone have any ideas how I can get rid of the XP and get Ubuntu on it.   

I build all the computers at work, and install all the software. So I have some idea what i am doing. But I am stumped.  I have run Linux in the form of Fedora 9, 9 (since updated) used a free CD to put on a new computer i built. I still have that computer working fine.    its not a Dell, just inserted the CD and it took off and has been working beyond my expectaions.  Also I downloaded Ubuntu and installed it on an old Dell 500 P3 (with a Celeron 1.3 upgraded) I had to format the hard drive to get it to take from the CD i downloaded and burned.  Its working great and am on it right now typing this.  

Thank you 

Drew

---

### Post by darkod on 2010-02-21
256MB is too little to run the ubuntu live cd or to install ubuntu. It might detect that and go straight into windows (hdd).

I think 256MB is even too little for Xubuntu too.

You might try Puppy Linux (it also boots into live desktop) and that can also show you if it will boot puppy or go straight into XP again.

---

### Post by Onesimus on 2010-02-21
It may be a number of things. 

Did you burn the installation CD at the lowest speed, in order to minimise errors ?

With only 256Mb of RAM you will need to install using the alternative installation CD.  

I have run Ubuntu with that amount of memory and it works, but you may not be able to use the extra visual effects.

Hope this helps

---

### Post by Drewmusk on 2010-02-21
" With only 256Mb of RAM you will need to install using the alternative installation CD.  "  I am surprised that even the opening window of Ubuntu or Fedora did not load.  I don;t even hear the disk spin. 

I want to make this as easy for the user as possible. She only wnats to use it as an internet appliace and to use Yahoo Messenger, (and yes I know Yahoo does not work on Linux)  So I do not want her to have to use a live CD to load it every time. I want a clean install on the hard drive.

---

### Post by darkod on 2010-02-21
> **Drewmusk said:**
> " With only 256Mb of RAM you will need to install using the alternative installation CD.  "  I am surprised that even the opening window of Ubuntu or Fedora did not load.  I don;t even hear the disk spin. 

I want to make this as easy for the user as possible. She only wnats to use it as an internet appliace and to use Yahoo Messenger, (and yes I know Yahoo does not work on Linux)  So I do not want her to have to use a live CD to load it every time. I want a clean install on the hard drive.

Also, if you don't want the user pi**ed about everything taking too long and hanging, I guess you need to give Puppy a look too. When I said it runs from cd I meant to say you can test how you like it, of course you can install it on the hdd.

If it seems the cd is not even spinning, it sound like hardware issue. Are you sure it works fine?

As the previous poster said, ubuntu might run on 256MB but if that's pushing it too much it will be slow for most tasks.

---

### Post by confused57 on 2010-02-21
Have you tried pressing F12 when the Dell boots up, in order to boot from the CD drive, if I understand your problem correctly?

---

### Post by 4String_Gal on 2010-02-21
> **darkod said:**
> 256MB is too little to run the ubuntu live cd or to install ubuntu. It might detect that and go straight into windows (hdd).

I think 256MB is even too little for Xubuntu too.

You might try Puppy Linux (it also boots into live desktop) and that can also show you if it will boot puppy or go straight into XP again.

I have Xubuntu running on an old laptop with only 256MB RAM.  It works fine. But that is not enough RAM for regular Ubuntu.

---

### Post by Kixtosh on 2010-02-21
I have done this install very recently on an _**even older DELL**_ (see my signature) and an equally old Toshiba. Both are limited to a maximum of 256MB of RAM and very old processors. I was able to install and use a full Ubuntu Karmic Koala O.S. on both, and it worked much better than Windows 2000 in terms of speed. Yes, Firefox was slow to start (probably fifteen seconds or so), and yes, OpenOffice was slow to start as well, but everything did work and _**everything installed normally from the Live CD without resorting to using the alternative install method**_, the use of which I am not familiar with. I have now installed Xubuntu on both machines, just to be safe (because it's supposed to be a lighter version), but I can't say that I noticed a huge improvement in the speed of applications or even boot time. I eventually intend to use Lucid Lynx 10.4 (since it's a Long Term Support release) on both.
 
I'm sorry to suggest the obvious, but the problem described sounds like it might be a badly burnt ISO image? Are you sure you actually used ISO burning software to create your live CD, not just a copy of the ISO image file (which is not bootable)? If the machine you're using can boot from the CD drive you are using, then there's no reason the Live CD shouldn't at least start up IMHO.
 
I have also tried Puppy, BTW. It's interesting too, and there are some improvements in performance, but thus far, even on these laptop-o-saurs, they have not struck me as quite sufficient enough to attempt a hard drive install of Puppy (for which it's not really intended, by design, anyway). Before finally deciding between this option and Lucid Lynx, I intend to try out lighter office applications than OpenOffice and a less demanding browser than Firefox (maybe Sea Monkey), since boot times on these machines are already very reasonable (about 1m 40s on the Dell, and 75s on the Toshiba, and they both use hard drives limited to a 4,200 rpm rotation speed).

---

