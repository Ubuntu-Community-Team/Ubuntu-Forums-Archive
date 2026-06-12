---
title: "Errors installing Ubuntu 10.4"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by jrob7489 on 2010-08-26
I am an absolute newbie to Ubuntu, but like the sound of it so wanted to try i tout.


I downloaded the latest desktop version and burnt a CD –no problems so far.
   
  I tried to install it on my PC, but get a page full of errors.
   
  Now the real issue may be the PC and not Ubuntu – this is where I need guidance.
   
  Its a Dell Pentium of some form – probably 7 years old ??    512MB ram, >2gig processor, and WAS running Windows XP.
   
  I say was as I had a kernel problem late 2009 that was not recoverable (at least not by me).
   
  The question I am hoping you can answer is – do I need a working OS to enable install of Ubuntu ?
   
  I replaced the PC just before Xmas and have it gathering dust.   If I could somehow resurrect it as a working PC I would be happy, and learning Ubuntu seems like a good reason.
   
  If the desktop version I downloaded [COLOR=Red]**_does_**[/COLOR] need a working OS underneath it, is there a version of Ubuntu that does NOT ?


At the end of the day the PC is a boat anchor if I cannot get it to run Ubuntu.

---

### Post by plucky on 2010-08-26
> The question I am hoping you can answer is – do I need a working OS to enable install of Ubuntu ?


No,you can install Ubuntu on a system without an operating system.

1) Did you check the MD5SUM of the download? See [Howto Md5sum](https://help.ubuntu.com/community/HowToMD5SUM)
2) Burn the CD image as slow as possible.
3) If the CD boots,there is an option to check the integrity of the CD.
  Use it just to make sure the Cd is readable by the Cd drive you are installing from.
4) There is also a memory test option on the install Cd,sometimes it is worth running on the machine you are installing on,as an additional safeguard.

Good Luck

p.s the specs on your machine are good enough to run the Live CD,but it will be slow as it is running off the CD

p.p.s What errors are you getting?

---

### Post by jrob7489 on 2010-08-26
Plucky,

Thanx for that.

I ran the md5sum and its all ok - so my downloads are the same.

Decided to do same on the CD file, but thats not an ISO it has been loaded (only way I can describe it)

What I DID see though is wubi.exe

As I understand it this is to install under windows - but my windows environment is dead - some form of kernel error..........

If I want to install it NOT under windows, did I still choose right by downloading 

ubuntu-10.04.1-desktop-i386.iso

or is there another i should use ?

The error messages - well the machine is no t"up" therefore I cant print - will need to try to write them down, OR take a picture of the screen....

Will get back to you later.

---

### Post by mörgæs on 2010-08-26
You could try the alternate installer downloaded from 
[http://www.releases.ubuntu.com/lucid/](http://www.releases.ubuntu.com/lucid/)

It suits older machines better. The installation process is different, but the installed system is the same.

---

