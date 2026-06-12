---
title: "installing problems"
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by skill1414 on 2007-08-02
Hi, All this linux stuff is new to me.

I downloaded the ubuntu iso and burned it onto disk but whenever I try to install, the splash screen comes up but always freezes at that screen.

My system specs are: 
AMD Athlon 64 processor 3000+
2.00 GHz, 1.00gb ram
Windows XP SP2
Nvidia Geforce FX 5200

---

### Post by waggygee on 2007-08-02
> **skill1414 said:**
> Hi, All this linux stuff is new to me.

I downloaded the ubuntu iso and burned it onto disk but whenever I try to install, the splash screen comes up but always freezes at that screen.

My system specs are: 
AMD Athlon 64 processor 3000+
2.00 GHz, 1.00gb ram
Windows XP SP2
Nvidia Geforce FX 5200

I hope you copied it at 1x's speed (that's what they always say is best) even though I copied mine at 2X's. Just a question, does Windows recognise the UbuntuCD? (What do you get when you insert the cd when Windows is booted?

---

### Post by skill1414 on 2007-08-02
yes I burned it at lowest speed and windows reads the disk. 

But when I try to install by booting the cd at start up is where the problem is.

---

### Post by davidjmayo on 2007-08-02
Did you check the download was correct with the MD5sum

if you don't know what MD5sum is, see here [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by waggygee on 2007-08-02
Im not sure then..... I see you have an AMD processor, I noticed that you should the AMD 64-bit's need don't work with the same Ubuntu version as other Intels and such([www.ubuntu.com](www.ubuntu.com)). But if you had the wrong version, I doubt it would have booted for the cd at all. Try the CD on another computer just to be sure

---

### Post by skill1414 on 2007-08-02
> **davidjmayo said:**
> Did you check the download was correct with the MD5sum

if you don't know what MD5sum is, see here [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Yes the download was correct
> **waggygee said:**
> Im not sure then..... I see you have an AMD processor, I noticed that you should the AMD 64-bit's need don't work with the same Ubuntu version as other Intels and such([www.ubuntu.com](www.ubuntu.com)). But if you had the wrong version, I doubt it would have booted for the cd at all. Try the CD on another computer just to be sure
I downloaded ubuntu-7.04-desktop-i386.iso, is this the right one?

---

### Post by waggygee on 2007-08-02
> **skill1414 said:**
> Yes the download was correct

I downloaded ubuntu-7.04-desktop-i386.iso, is this the right one?

i386 is what I am using, I have a Pentium4. Sadly I have no experience with AMD processors. Look at this site [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
There is a part where you tick what you have be it a 64bit AMD processor or Standard personal computer(x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)
Your processor is a 64bit AMD so it won't work with the other. Simply choose the edition of Ubuntu you want, tick that you have 64bit AMD, set your location (this is for setting which server you'll use, you should be able to change it later) then download from that site..... Good luck!

---

### Post by skill1414 on 2007-08-02
ok, i will download over the weekend.
hopefully it will work.

---

### Post by merlinus on 2007-08-02
I recommend using the text-based Alternate Install cd, no matter which architecture.  It can help avoid problems with video cards.

-merlin

---

### Post by skill1414 on 2007-08-03
I downloaded the amd version but it still doesn't work. this time the bar moves left and right for about 20-30 seconds but then freezes.

---

### Post by Pumalite on 2007-08-03
Did you follow merlinus advise to install with Alternate CD?

---

### Post by pigbig842001 on 2007-08-04
> **skill1414 said:**
> I downloaded the amd version but it still doesn't work. this time the bar moves left and right for about 20-30 seconds but then freezes.
first things first. maybe the burn is not successful. So get a rewritable disc and then try to burn it at the slowest speed.

and then, when u boot, select the option **check CD for defects**. if it shows error then you know what to do. erase the CD and burn again.

Check the iso image for any snags ie. md5sum check. the md5sum.txt file is given in the image.

and please, look for the right version, if u have an AMD system, go for the AMD image.

---

### Post by pigbig842001 on 2007-08-04
> **skill1414 said:**
> Hi, All this linux stuff is new to me.

I downloaded the ubuntu iso and burned it onto disk but whenever I try to install, the splash screen comes up but always freezes at that screen.

My system specs are: 
AMD Athlon 64 processor 3000+
2.00 GHz, 1.00gb ram
Windows XP SP2
Nvidia Geforce FX 5200
your system specs say that uhave a 64bit system. U will have to use the 64bit image.

after download, check md5sum.

---

### Post by Pumalite on 2007-08-04
I still think, like merlinus did, that you should use Alternate CD.

---

### Post by Pitwolf45 on 2007-08-04
Amd Work Just Like Intel That Part Does Not Matter, 386 Should Work

---

