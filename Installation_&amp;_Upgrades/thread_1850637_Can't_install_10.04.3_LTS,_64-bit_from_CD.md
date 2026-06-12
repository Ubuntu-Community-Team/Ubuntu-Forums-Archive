---
title: "Can't install 10.04.3 LTS, 64-bit from CD"
date: 2011-09-26
forum: Installation &amp; Upgrades
---

### Post by z61P on 2011-09-26
I have tried this several times, with the same result: 
 
Installing 10.04.3 LTS Server, 64-bit from CD; the install process gets to a point where it prompts me to insert the CD. Problem is, the CD is already in the drive! 
 
I've d/l and burned two CDs, and attempted the install 4 times, and the result is the same. 
 
My system has an Intel uP... I successfully installed an earlier distribution of 10.04.3 LTS on this same system, and it ran fine for over a year. Has something changed? Could it even have anything to do with Intel vs. AMD? 
 
THanks,
z

---

### Post by oldfred on 2011-09-27
I thought some Atom processors were 32bit? Have you confirmed that yours is 64Bit?

Did you check that ISO has correct MD5sum?

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by z61P on 2011-09-27
I ran the "Check disk for defects" option, and got the following msg: "Integrity Test Successful  The CD-ROM is valid" 
 
The system is definitely 64 bit - I ran 10.04-3 64-bit on it for over a year; I'm having to re-install due to a crash/HD failure.  
 
In the "for whatever it's worth" column: 
 
One of the CDs I burned failed integrity testing. The install software reported that hash values were incorrect. So I assume this "built-in routine does the same thing as a separate, stand-alone check would do. 
 
Here's an odd thing, though... just for grins I tried to install using the CD that failed integrity checks (the "good one didn't work, so why not?). The install script reported that the file was bad (there were many corrupted files, apparently), but then it also reported that it couldn't download a valid file... I don't understand why the download failed??? 
 
I have also tried installing an earlier version of the 10.04-3 LTS Server 64 distro (2010 vintage), and it still works! 
 
I wonder if the current distro is corrupt? Is there someone who checks these things? 
 
Thanks,
z

---

### Post by z61P on 2011-09-27
> **z61P said:**
> I have tried this several times, with the same result: 
 
Installing 10.04.3 LTS Server, 64-bit from CD; the install process gets to a point where it prompts me to insert the CD. Problem is, the CD is already in the drive! 

 
Ah - one additional tidbit that may be relevant: The screen that prompts to insert the CD refers to "20110719.2"... is there supposed to be a 2nd CD?? 
 
z

---

### Post by oldfred on 2011-09-28
10.04.03 was released July 21 so I would guess that the date shown is just the .03 update. Not sure if there is another disk or not?

---

### Post by VanR on 2011-09-28
Just a shot in the dark, but have you tried removing the CD and sticking it right back in? Though it sounds stupid I had to do this installing some Windows software one time. It asked for CD number 2, but there was only one. So I stuck the same one in again and it continued the install.

---

### Post by z61P on 2011-09-28
Apparently the issue(s) had to do with either CD media itself. I tried a DVD, and it worked perfectly the first time. 
 
And I don't know whether this is relevant or not: The CDs I tried were the 700 MB variety; the image itself is listed as 696 MB in Windows. Perhaps bad things happen being this close to capacity? 
 
z

---

### Post by rreyes3713 on 2011-09-28
Yeah, I had a similar problem too. I was installing 10.04 from a CD which worked fine before (I thought) but this time around I was running into problems. It would just hang there.

So I used a USB flash drive burned Ubuntu 10.04 that worked just fine.

---

