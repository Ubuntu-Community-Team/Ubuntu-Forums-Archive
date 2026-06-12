---
title: "Edgy i386 desktop iso check CD failed"
date: 2006-12-20
forum: Installation &amp; Upgrades
---

### Post by ChM on 2006-12-20
Hello,

I have downloaded the edgy i386 desktop iso cd from three different mirror sources here in France. I checked the md5 checksum and it was ok. When I then request to check the CD prior to installation it reports that one checksum check failed. I tried on two different computer with two different downloads. 

I would like to know if this can be confirmed by others and if the "error" is critical or not. 
May I safely install it or will I have a bogus installation ?

---

### Post by wpshooter on 2006-12-20
What speed are you burning the CD at ?  You should use 4X or less.

Have you tried a different brand of CD ?  Are you using good quality name brand CDs ?

Try cleaning your CD drive.

Good luck.

---

### Post by ChM on 2006-12-20
Do I have to conclude from this reply that it is 100% sure that it is a local problem ? 

I used x52 cd-r and made them at x24 speed. Your reply made me notice that I used the same CD-R burner. The only thing I didn't change. Could it fail three time in nearly the same way ? Ok, I'll try at a much slower speed and if it still fail I will also try with another cd burner.  Thanx for answering.

---

### Post by Titus A Duxass on 2006-12-20
> I used x52 cd-r and made them at x24 speed. - This is probably the cause, as wpshooter stated burn iso files slow, I always go for X2.

---

### Post by ChM on 2006-12-20
I just tried with x4, still with the same CD burner, and I still get the 1 package checksum failed error. There is no x2 available with my nero program. x4 is the slowest. 
So I have to try with another CD bruner (writer). BTW I have burned 5 CD so far !
I never had any problems of this kind with this CD writer. 

Is it possible to check the ISO without burning the CD ? If I see a problem in this case then we will be sure it is not the burning process.

---

### Post by ChM on 2006-12-20
Ok, now I burned another CD on another computer (WinXP) using another program and at x2 speed. I then checked the CD after booting on it and it keep saying that one checksum failed. 

I really feel unconfortable to install this distribution, but I am pretty sure this is a feature inside the iso.  We still don't have any feedback from people that tested their version. 

Here is the result of the checkum test.
> b950a4d7cf3151e5f213843e2ad77fe3 *ubuntu-6.10-desktop-i386.iso

The iso was downloaded from here
[ftp://ftp.proxad.net/mirrors/ftp.ubuntu.com/releases/6.10/](ftp://ftp.proxad.net/mirrors/ftp.ubuntu.com/releases/6.10/)
But I saw an equivalent result with the iso downloaded from lip6.fr. 

It is an inconvenience that we don't get a feedback on what checksum failed. Is is critical or not for an installation ? 

I need to install my computer ASAP and I am now blocked because of this problem.

---

### Post by mcduck on 2006-12-20
you should check the MD5 sum ot the ISO file you downloaded before you even burn it to disk.

Also, I'd recommend downloading with torrent. That way the download is automatically checked and you wouldn't have to worry about bad downloads.

---

### Post by wpshooter on 2006-12-20
Try running memtest on your memory.

Might want to reseat the memory.

Did you try cleaning your CD-Rom drive ?

Did you check to see that you have the latest Firmware on your CD-Rom drive ?

Should consider investing in a few good name brand CD-RW medias.

---

### Post by ChM on 2006-12-20
Thank you for trying to be helpful.

Though I don't think the suggestions are appropriate. 

I downloaded the iso binary. The tool used doesn't matter. I then checked the md5 checksum of the iso. I did this on two different computers. Memory has nothing to do here and cd cleaning either. I downloaded the iso fro three different sources (all in France though) but all yield the same md5 value that matches the one published on the ubuntu web site. You can check by yourself if I did a mistake there. 

I burned the CD with two different computers, two different software, two different cd writer. All report exactly the same error. So I don't think memory or cd reader is in play here. There is no feedback on what is really the problem though. I tried with 6 CD now. Such a systematic error is not the usual signature of memory or CD reading errors. 

I booted on the cd with two different computers, and checked the CD. Both reported exactly the same problem and showed the same behaviour. It is very unlikely that that there is a memory error on both computers that would yield the same checksum failure.

So my tests led me to the conclusion that the problem is very likely in the ISO data.

Is there anyone who did the test to check this result ? How can I have more insight on the problem source ? What checksum failed ? Is it always the same checksum that failed ? There is currently no way for me to be sure of that. 


To avoid any confusion, let me clarify that there are two checkings involved here. The md5 checksum of the iso file which is reported as valid for all my download attempts and the command in the boot menu allowing to check the CD. I have no idea what this command is in fact doing and how it does it. All I know is that it reports that one checksum failed and I don't know what to deduce from this. Is it a critical problem for installing Ubuntu or is this not relevant ?

---

### Post by ceb004 on 2007-02-01
I get the same error -- I do not think it is a hardware problem with people's systems.  Doing the same check for the 6.06 (DD) version produces no such error report.

The annoying thing about 6.10 is, there is no error message telling one which checksum failed.  in 6.06, there is a separate report for each individual file.

---

### Post by stajo917 on 2007-02-12
I've spent most of my weekend trying to install Ubuntu 6.10 on my VIA Epia M10000 box with the same problem as you describe.

Downloaded iso-image is correct (checksum ok). Downloaded from severel different mirrors. Burnt in severeal different speeds. All result in 1 checksum failure when testing the integrity of the cd from the first cd boot menu.

Any solutions or is 6.06 the way to go?

---

