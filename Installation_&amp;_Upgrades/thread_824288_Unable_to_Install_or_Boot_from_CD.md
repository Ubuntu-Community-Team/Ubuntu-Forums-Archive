---
title: "Unable to Install or Boot from CD"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by Buschbarber on 2008-06-09
I downloaded v8.04 for Desktop with my 3Ghz P4 XP MCE. I burned the iso image to CD using Nero 8. I did this twice - once on each of my PC's.

Each time, when I tried to boot either PC, the boot asks me to choose English and then I choose either Try Ubuntu from CD or Install. In either case, I get a never ending list of SQUASHFS error:sb_bread failed unable to read page

Am I missing a config step?

---

### Post by atoponce on 2008-06-09
Have you checked the MD5SUM of the iso before burning it to disk?  Does it match what's provided on the download page?

```
md5sum ubuntu-8.04-desktop-i386.iso
```

---

### Post by Buschbarber on 2008-06-10
I do not know what md5sum means, but the name of the file I downloaded is the same name you quoted. I downloaded the file from two different mirror sites on two different computers. I successfully burned CD's and tried to either Boot from CD or Install. On the 2Ghz Celeron machine it let me choose the English language and let me choose Run Unbuntu from CD. It then showed me an Unbuntu splash screen and a status bar. After a minute or so I saw the blinking cursor and then an endless scrolling screen of similiar error messages

On my 3Ghz P4 machine, I followed the same procedure only upon Boot, I just got the Splash screen and then a Status bar. After a couple of minutes, I received the following screen:

Preparing restricted drives
Setting System Clock
Starting Basic Networking
Starting Kernel Event Manager
Loading Hardware Drivers
ubevd-event [6698]8run_programs/sbin/modprobe abnormal exit

I got several of the ubevd-event errors and then several other lines of messages

---

### Post by wpshooter on 2008-06-10
Have you tried checking the integrity of your Ubuntu CDs by running the verification function that is found on the initial Ubuntu boot screen menu ?

What speed is your program burning the ISO files at ?  It needs to be slow.  4X or slower is probably going to give you the most accurate results.

---

### Post by atoponce on 2008-06-10
> **Buschbarber said:**
> I do not know what md5sum means, but the name of the file I downloaded is the same name you quoted. I downloaded the file from two different mirror sites on two different computers. I successfully burned CD's and tried to either Boot from CD or Install. On the 2Ghz Celeron machine it let me choose the English language and let me choose Run Unbuntu from CD. It then showed me an Unbuntu splash screen and a status bar. After a minute or so I saw the blinking cursor and then an endless scrolling screen of similiar error messages

I believe the download of your ISO to be bad.  MD5SUM is a utility to create an MD5 hash from a file.  As MD5 hashes are unique given any input (or should be at least), this is a great way to test that your ISO has been downloaded correctly.  From the download mirror you got the ISO from, there is an MD5SUMS text file as well.  You'll see a long hash next to the file you downloaded, in this case, ubuntu-8.04-desktop-i386.iso.  Use an MD5 utility on that file to create an MD5 output, and check your result against the one on the mirror from which you downloaded the ISO.

---

### Post by Buschbarber on 2008-06-10
I read the information, on the Ubuntu web site, regarding the md5sun, and I installed winmd5sum. I ran it an used Compare to check the download. It compares.

I was burning the ISO image, using Nero 8, at 48x (the default), on both machines. The media is Sony CD-R 700.

I then downloaded the InfraRecorder, from the Ubuntu web site, installed it, and burned another CD of the Desktop version.

I booted the Celeron machine, again, with the same results. I just get an endless scrolling screen of squashfs error:sb_read failed reading block 0x70397 and unable to read page, block 1e8da709, size b5ad

---

### Post by Buschbarber on 2008-06-10
Well I did as you requested and on the Ubuntu Boot Screen I chose the "Check the Integrity of the CD" menu choice. It found 3 bad files.

I looked at Nero 8 Express and InfraRecorder and I cannot see where I can change the default Write speed

---

### Post by wpshooter on 2008-06-10
Well, my "guess" is that the write speed is the problem.

Do you have some media on which the write speed is 1x to 4x range ?

If not then you need to find a program which will allow you to adjust the write speed.  I use Ubuntu's K3b which handles this perfectly.  I don't know what M/S program might allow you to do this.  Perhaps you can google and find one or someone else on the forum can suggest one.

Good luck.

---

### Post by sapph on 2008-06-10
Nero can burn at any integral speed that both the burner and media are capable of.

On the last screen before you click 'Burn' there is a dropdown labeled 'Writing speed'.  It defaults to Maximum.  You should be able to change it from this to 4x, 2.4x, 2x or 1x.

---

### Post by Buschbarber on 2008-06-10
Gentleman and Ladies - I finally have an error free Boot CD. I have used Nero 8 Express, Nero 8 Burning Rom, InfraRecorder (from this site), and finally ISORecorder (from this site). Even Nero 8 Burning Rom, at 4x record speed, did not yield an error free CD.

ISO Recorder is the winner. I was able to boot my 2Ghz Celeron machine. I have that machine set up with Vista Home Upgrade on drive D. Vista would only install as an Upgrade and it would not let me Replace Windows on Drive C.

I was only testing Vista and I really don't have a need to keep it, but can I install Ubuntu on Drive C and Dual Boot with Vista?

If so, is it better to Boot with the Ubuntu CD and run Install from the Desktop, or is it better to Boot with the Ubuntu CD and Install from the Boot menu?

Thanks!!!

---

