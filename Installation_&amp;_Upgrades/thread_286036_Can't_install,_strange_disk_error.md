---
title: "Can't install, strange disk error"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by vreemde eend on 2006-10-27
I tried to install Edgy several times, but I can't boot from the (alternate) install cd. I get this error:
```
ISOLINUX 3.11 Debian-2006-03-16 isolinux: disk error 01, AX = 4240, drive 9F  
```

The cd is ok, I checked it on an other pc. What could be going wrong?

Thanks a lot,

Pieter

---

### Post by pradeepadapa on 2006-10-27
hii,

       just try to check whether u hav ur hdd has the required power or check for any loose connections nd also check whether the cd-rom is the first boot device nd then urr hdd. just try nd see whether the hardware devices are functioning correctly or not.

---

### Post by Paul Dufresne on 2006-10-27
See also on this:
[http://syslinux.zytor.com/archives/2004-December/004271.html](http://syslinux.zytor.com/archives/2004-December/004271.html)
With following comment:
In this case, it looks like it gets the whole El Torito "no emulation" 
commandset completely wrong; it looks like it doesn't respond to it at all.

[http://www.mail-archive.com/ubuntu-fr@lists.ubuntu.com/msg09948.html](http://www.mail-archive.com/ubuntu-fr@lists.ubuntu.com/msg09948.html) (french)

Would probably be worth opening a new bug, although I feel your drive might
have some kind of wrong firmware.Many drives can have their firmware
updated.

[https://launchpad.net/distros/ubuntu/+filebug](https://launchpad.net/distros/ubuntu/+filebug)

Please give model of the drive(s).

---

### Post by vreemde eend on 2006-10-27
I checked that, all seems fine. I just (accidently) booted without boot-cd and to my surprise an old WinXp installation on the hard dist started up, without a problem... .

I still have no clue why Ubuntu won't install. Can anybody help?

thanks a lot,

pieter

---

### Post by vreemde eend on 2006-10-27
> **Paul Dufresne said:**
> See also on this:
[http://syslinux.zytor.com/archives/2004-December/004271.html](http://syslinux.zytor.com/archives/2004-December/004271.html)
With following comment:
In this case, it looks like it gets the whole El Torito "no emulation" 
commandset completely wrong; it looks like it doesn't respond to it at all.

[http://www.mail-archive.com/ubuntu-fr@lists.ubuntu.com/msg09948.html](http://www.mail-archive.com/ubuntu-fr@lists.ubuntu.com/msg09948.html) (french)

Would probably be worth opening a new bug, although I feel your drive might
have some kind of wrong firmware.Many drives can have their firmware
updated.

[https://launchpad.net/distros/ubuntu/+filebug](https://launchpad.net/distros/ubuntu/+filebug)

Please give model of the drive(s).

I have two cdrom-drives and I tried them both. 


1. Lite-on cd-rw drive model ltr-16102
2. Gold star cd-rom Model no crd-8322B

I already used the second one to install the two previous releases of ubuntu (but with an other mobo and cpu).

I feel there could be a problem with the bios (from what I understood from the French link you provided.) The bios is: PHOENIX BIOS D686 Does someone know how I can make it work if at all?

(My input devices don't work in the WinXP install, but that could be due to software problems.)

---

### Post by vreemde eend on 2006-10-27
Okay,

WinXp is running 'fine', I didn't connect the input devices correct (I feel stupid), now they are working. The only option I can think of, is updating the Bios. However I don't know how to do it... . Or is there another possible solution?

---

### Post by pradeepadapa on 2006-10-27
u can update the bios by downloading the bios utility frm  the manufacturers website. nd directly installing frm the setup file.

---

### Post by Paul Dufresne on 2006-10-29
Hé, il faut pas suivre tous mes conseils stupides! :) 

En recherchant disk=9f à nouveau, je m'apperçois que plusieurs
ont réglé ce problème, simplement en s'assurant d'avoir le bon
md5 de l'image, avant de la graver.

Donc, si tu es déjà en Linux, fait:
$md5sum <cd_image_file>
et compare la valeur avec celle affiché sur le site où t'a télécharger
l'image.

Après seulement, je fait:
$sudo cdrecord <cd_image_file>
j'emploie sudo pour que ma protection contre les mauvaises gravures soit
activée. (CD burn free feature??).

Probablement mieux avec un CDRW, parce que vraiment pas sûr que ça va marcher.

---

### Post by vreemde eend on 2006-10-30
> **pradeepadapa said:**
> u can update the bios by downloading the bios utility frm  the manufacturers website. nd directly installing frm the setup file.

the bios update crashed ](*,) 

I'll reinstall WinXp and try to update the bios again (supposing that the crash was due to a messed up WinXp install)

---

### Post by vreemde eend on 2006-10-30
> **Paul Dufresne said:**
> Hé, il faut pas suivre tous mes conseils stupides! :) 

En recherchant disk=9f à nouveau, je m'apperçois que plusieurs
ont réglé ce problème, simplement en s'assurant d'avoir le bon
md5 de l'image, avant de la graver.

Donc, si tu es déjà en Linux, fait:
$md5sum <cd_image_file>
et compare la valeur avec celle affiché sur le site où t'a télécharger
l'image.

Après seulement, je fait:
$sudo cdrecord <cd_image_file>
j'emploie sudo pour que ma protection contre les mauvaises gravures soit
activée. (CD burn free feature??).

Probablement mieux avec un CDRW, parce que vraiment pas sûr que ça va marcher.

J'ai déjà essayé le cd dans un autre ordinateur et ça marche sans problèmes. Donc je pense qu'il y a pas d'erreurs sur le cd. 

Merci pour votre conseil

(Il faut m'excuser ma pauvre connaissance français.)

---

### Post by vreemde eend on 2006-11-01
Got it finally installed, by connecting the cd-drive to another bus.

---

### Post by Stonedeaf on 2006-11-05
For those that have similar problems, this is how I managed to get it running...

[http://www.ubuntuforums.org/showthread.php?p=1712765#post1712765](http://www.ubuntuforums.org/showthread.php?p=1712765#post1712765)

/ Stefan

---

### Post by mrshiney on 2006-11-12
I had the same problem (and initially thought it was the drive, too). Anyway, it's not. It's the controller card -- the Sil/CMD 0649 card's bios does not support the Torito format used by many linux live CDs (and at least one XP cd I tried).

The Sil/CMD 0649 also does not have a flash bios, so don't bother looking for a bios update. I suppose if you had an EEPROM programmer and access to appropriate code... pretty much you should do what I did: try another controller.

I can report that their newer model, the Sil/CMD 0680 doesn't have the problem.

[Mr. Shiney's Blog]("http://mrshiney.froppy.com/blog/")

[Invalid Link]("http://iamnotavalidfrigginlink.ok.yes.gotit")

---

### Post by CCam761 on 2006-12-21
Hi,
I'm getting the same error. Here's the sitrep:
IBM PC Server 330
Dual Pentium Pro 200MHz
CDR = IBM CR-506-B
SCSI = AIC-7880 Ultra/Ultra (built in)
My skill level:
Linux = newbie
CPM/DOS/WIN95/98/NT = VG
I ran the basic Xubuntu desktop on another machine, liked what I saw, and bought the Server version for the Tower. I had bought memory and adapter to get CD connected. It had WIN2000 someone else loaded on 4.5GB HDD that would not finish boot. 
System boots fine w/WIN98 FD. I tried loading WIN98 to try and have a good system running first. I found out at another page this will install but not do first run - too late for me. But CDR works.
Another forum suggested Disk may be bad. But from WIN98 boot FD, directories look fine so I used the CD on another system (IBM PII 350MHz) and it installed fine. So CD is good. I upgraded the BIOS successfully. Still I get the error:
ISOLINUX 3.11 Debian-2--6-03-16 isolinux Disk error 01, AX=4240, drive 9F
it says press a key and then it displays
ISOLINUX 3.11 Debian-2--6-03-16 isolinux Disk error 01, AX=4280, drive 9F
I read somewhere that the SCSI interface can be updated for ServerRAID but I doubt this is the problem. 
Thanks for any help you can be. After I get it loaded I promise to read all the materials before asking questions on the forum.

---

### Post by CCam761 on 2006-12-25
Do I need to post my problem to a new thread?
I posted here since my problem was related to the other one posted.

Follow up:
The BIOS does not recognize IDE adapters to boot from. When HDD is selected, it means the internal built-in SCSI interface. So I have to figure out how to deal with the hand dealt to me.

I have not seen any mention of Ubuntu used with the PC Server 330 although IBM's website lists other Linux systems that will work with it like SUSE, SCO, RedHat, and Caldera.

I would give the ServeRaid update a try but I am on dialup and downloading a CD image is problematic. There are also HDD upgrade programs for Linux (19MB D/L) at IBM's site but they tend to address drive reliability.

---

