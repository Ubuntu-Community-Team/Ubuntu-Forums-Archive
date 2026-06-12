---
title: "hard drive format"
date: 2011-09-09
forum: Installation &amp; Upgrades
---

### Post by waterpipes on 2011-09-09
How can I format my hard disc so I can make a clean ubuntu install. At the moment it will not accept any operating system(ubuntu) just goes thru post and then I just get a a blinking cursor and I cant enter anything.

---

### Post by Basher101 on 2011-09-09
if you want to wipe it completeley clean its quite easy.
step 1: get yourself a Ubuntu Live CD
step 2: Boot from the CD
step 3: select install
step 4: Choose use all space (or replace all? havent used the installer long time...) and then it should automatically reformat your whole drive and make a fresh install.

---

### Post by waterpipes on 2011-09-09
> **Basher101 said:**
> if you want to wipe it completeley clean its quite easy.
step 1: get yourself a Ubuntu Live CD
step 2: Boot from the CD
step 3: select install
step 4: Choose use all space (or replace all? havent used the installer long time...) and then it should automatically reformat your whole drive and make a fresh install.

I have all ready tried with ubuntu 7.10 but it only goes as far as configure screen parameters.

---

### Post by recluce on 2011-09-09
> **waterpipes said:**
> I have all ready tried with ubuntu 7.10 but it only goes as far as configure screen parameters.

Are you really trying to install 7.10 - as in Guty Gibbon, released in October of 2007 and unsupported since April 2009?

If so, please download Ubuntu 10.04LTS and retry. I don't believe anybody is willing to try to troubleshoot a release that has been dead and buried for almost 2.5 years....

---

### Post by Basher101 on 2011-09-09
amen to that

---

### Post by Enigmapond on 2011-09-09
Just download either 10.04 (I recommend) or the latest version 11.04., follow the instructions in burning it to a CD...boot and it will format as it installs. You will not get anywhere with 7.04...it's been dead for quite some time.

---

### Post by waterpipes on 2011-09-10
> **recluce said:**
> Are you really trying to install 7.10 - as in Guty Gibbon, released in October of 2007 and unsupported since April 2009?
 
If so, please download Ubuntu 10.04LTS and retry. I don't believe anybody is willing to try to troubleshoot a release that has been dead and buried for almost 2.5 years....
 I have downloaded 10.04 and tried to install but I get even less than 7.10, I only tried 7.10 because it was at hand, I then tried 10.04. The problem started with trying to upgrade from 11.04 to ubuntustudio 11.04.

---

### Post by waterpipes on 2011-09-10
> **recluce said:**
> Are you really trying to install 7.10 - as in Guty Gibbon, released in October of 2007 and unsupported since April 2009?
 
If so, please download Ubuntu 10.04LTS and retry. I don't believe anybody is willing to try to troubleshoot a release that has been dead and buried for almost 2.5 years....
 I have tried to install 11.04 but get even less than 7.10. The problem arose when I tried to update from 11.04 to Ubuntustudio, I got the message that the files in studio had become corrupted.

---

### Post by mörgæs on 2011-09-10
When booting a 11.04 CD, have you tried the 'check CD for defects' option?

Also, please give a complete hardware description.

---

### Post by waterpipes on 2011-09-10
> **mörgæs said:**
> When booting a 11.04 CD, have you tried the 'check CD for defects' option?
 
Also, please give a complete hardware description.
 When I try to boot from 11.04, all I get is is the blinking cursor, it goes thru p.o.s.t. to the cusor then nothing
asrock M/b
intel dual core procc.
Hitachi 1trb H/drive
4 G/byte memory
CD/DVD writer
Nvidia graphics card

---

### Post by mörgæs on 2011-09-10
My guess is that the Nvidia card causes trouble. There are several options:


You could try adding boot parameters. There are links explaining how in this post:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

You could try searching this thread. A lot of Nvidia problems are solved here:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

You could try a live boot of Xubuntu 11.04.

---

### Post by srs5694 on 2011-09-12
> **waterpipes said:**
> When I try to boot from 11.04, all I get is is the blinking cursor, it goes thru p.o.s.t. to the cusor then nothing
asrock M/b
intel dual core procc.
Hitachi 1trb H/drive
4 G/byte memory
CD/DVD writer
Nvidia graphics card

I have several ideas about this, but they all depend on various details that you haven't provided. Writing up all my ideas would be tedious, so it's best if you provide the necessary details to narrow the field a bit. Please post the precise model of your motherboard and describe how the disk has been used (is it brand-new, does it have any existing OS installation on it, has it been partitioned -- and if so, how?). Also, please check your firmware's current boot settings and report them. Finally, do you intend ultimately to install Ubuntu by itself or to dual- or multi-boot, and if so, with what other OS(es)?

---

### Post by waterpipes on 2011-09-14
> **srs5694 said:**
> I have several ideas about this, but they all depend on various details that you haven't provided. Writing up all my ideas would be tedious, so it's best if you provide the necessary details to narrow the field a bit. Please post the precise model of your motherboard and describe how the disk has been used (is it brand-new, does it have any existing OS installation on it, has it been partitioned -- and if so, how?). Also, please check your firmware's current boot settings and report them. Finally, do you intend ultimately to install Ubuntu by itself or to dual- or multi-boot, and if so, with what other OS(es)?
 asrock GM31-GS, the disc has been used from new on ubuntu 10.04 which I then ugradated to 11.04, these were on all off the disc. I intend ot use ubuntu as I did before trying to install ubuntustudio, the disc containing ubuntustudio files were corrupted, I hope this helps.
 
                    Geoof

---

### Post by srs5694 on 2011-09-14
The manual I downloaded [from ASRock](http://asrock.com/mb/manual.asp?Model=G31M-GS) gives no hint that the motherboard is UEFI-based, so we can probably rule out UEFI issues, which was one of my hypotheses. 
 
Are you saying that you can't boot the computer at all, from hard disk or from optical drive? When did it last boot at all, and was there any clear precipitating cause -- say, a system crash after which the computer no longer booted or a failed OS installation after which it stopped booting? 
 
If you can't boot at all, you might want to investigate your BIOS's boot options -- it could be it's set to boot from a floppy disk and nothing else, to name just one of many possible misconfigurations. If it boots from the hard disk but not from the optical drive, it could be that the optical drive is not listed among the BIOS's boot options. It's also possible that your optical drive is physically damaged or defective.

---

### Post by waterpipes on 2011-09-16
> **waterpipes said:**
> When I try to boot from 11.04, all I get is is the blinking cursor, it goes thru p.o.s.t. to the cusor then nothing
asrock M/b
intel dual core procc.
Hitachi 1trb H/drive
4 G/byte memory
CD/DVD writer
Nvidia graphics card
I downloaded 11.04 alternate i386 iso and installed it,and it worked thank you for advise.

      waterpipes

---

### Post by waterpipes on 2011-09-16
> **srs5694 said:**
> The manual I downloaded [from ASRock]("http://asrock.com/mb/manual.asp?Model=G31M-GS") gives no hint that the motherboard is UEFI-based, so we can probably rule out UEFI issues, which was one of my hypotheses. 
 
Are you saying that you can't boot the computer at all, from hard disk or from optical drive? When did it last boot at all, and was there any clear precipitating cause -- say, a system crash after which the computer no longer booted or a failed OS installation after which it stopped booting? 
 
If you can't boot at all, you might want to investigate your BIOS's boot options -- it could be it's set to boot from a floppy disk and nothing else, to name just one of many possible misconfigurations. If it boots from the hard disk but not from the optical drive, it could be that the optical drive is not listed among the BIOS's boot options. It's also possible that your optical drive is physically damaged or defective. 
I downloaded 11.04 alternate i386 iso from the live cd site, copied it and installed it and it works but it doesnt operate like th 11.04 I was using before also I have no sound but at least I an operating system, thank you for help.

---

### Post by mörgæs on 2011-09-16
Are you sure that you have unmuted the sound?

---

### Post by PayPaul on 2011-09-16
> **Enigmapond said:**
> Just download either 10.04 (I recommend) or the latest version 11.04., follow the instructions in burning it to a CD...boot and it will format as it installs. You will not get anywhere with 7.04...it's been dead for quite some time.


So one can format an entire drive or whatever partitions are on it directly from the live Cd or even a USB drive that has the Ubuntu installation media on it without any of the DOS or command line codes I've seen posted as solutions elsewhere?

---

### Post by mörgæs on 2011-09-17
Yes, running Gparted from a live boot will do this.

---

### Post by waterpipes on 2011-09-17
> **mörgæs said:**
> Yes, running Gparted from a live boot will do this.
I downloaded 11.04 from the ubuntu download site and installed it,but I had to install alongside the existing 11.04.The new installation works as exactly how it should,that is that the launcher is on the left hand side with icons and I have sound. How can I get rid of the 11.04 alternate i386 installation.

---

### Post by Hakunka-Matata on 2011-09-17
delete the partition that your 11.04 alternate i386 installation is located on.
Then update grub.  
```
sudo update-grub
```

---

