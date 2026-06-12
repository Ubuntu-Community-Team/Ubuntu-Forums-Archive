---
title: "NEWBIE - Trying to install Ubuntu on old DELL:"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by ranchie on 2008-08-03
Hello everyone, 

I am trying to install an older version of ubuntu on my DELL Dimension 4100. I downloaded and burned ubuntu version 6.06 onto a DVD-R. Now what I am trying to do is install it on my old DELL. I went into the BIOS and changed the boot sequence so that it loads from the CD-ROM first, and it still won't do that. Instead it keeps loading the old Windows version that I have on it. Do I have to remove Windows first or what? :confused: Any help is appreciated. Thanks.

---

### Post by xen-uno on 2008-08-03
This thread ...

[http://ubuntuforums.org/showthread.php?t=878349](http://ubuntuforums.org/showthread.php?t=878349)

... has many useful links. 6.06? Although it might be less demanding in terms of disk space and RAM requirements, the latest (8.04) is much better on the installation front AFAIK. How did you burn your 6.06 install disk ... as an image or as data? Image good ... data bad.

---

### Post by Mister.Vash on 2008-08-03
Could be a issue with how the disk burned - do you another disk that you could test test with?  Like Windows XP, or something that you that you know should boot.  That will either let you know that the disk is if it boots off the one and not the other.  If neither boot, then it may be that the bios settings were not save

---

### Post by ranchie on 2008-08-03
I burned it as an image (ISO). I even tried it on my new computer, changed the boot sequence and managed to get the installation menu to appear. But I just have trouble doing it with my old DELL.

---

### Post by kahlil88 on 2008-08-03
You said it was a DVD-R...this could be your problem. Does the old Dell for sure have DVD-ROM? My mom has a Dimension 4300 running 8.04 quite nicely (no Compiz though).

---

### Post by ranchie on 2008-08-03
Yes, my old DELL has a DVD-ROM. It looks like this:

[URL="http://sycs.eu/images/DELL_Dimension_4100__432992.jpg"]http://
sycs.eu/images/DELL_Dimension_4100__432992.jpg[/URL]

So if I put the DVD-R in the DVD-ROM, then that means I have to make it boot from the DVD-ROM first? I selected the CD-ROM. Is that the wrong one? lol

---

### Post by xen-uno on 2008-08-03
Try a Windows (any flavor) bootable disk to check if your CD drive is any good. System specs (RAM, HD space, CPU)? See if there is a BIOS upgrade available as well. You may want to check into Xubuntu if your machine isn't up to snuff. 256 MB RAM min to run Ubuntu Live proficiently and 2 partitions of 10 GB for system and 2 GB for swap if installed. 20 GB is a more realistic min if you plan on installing much on it.

edit: We've got 3 of those at work ... good machines. Pent III 700 MHz's?

edit II: ... Good eye 88. DVD is likely your problem since the Ubuntu iso is in iso-9660 (CD-ROM) format and the DVD requires UDF. Surprised you didn't get burn errors.

---

### Post by ranchie on 2008-08-03
It is a p.3 @ 866mHz, 256RAM and 60GB HD. How is Xubuntu different?

So I can only burn the ISO image onto a CD-R then?

---

### Post by Mister.Vash on 2008-08-03
I found a similar issues in another thread.  Basically they had to do a bios update on the 4100 to get some disks to boot.  The link below should be where you can get the bios update

[http://www.linuxquestions.org/questions/slackware-installation-40/cant-install-slackware-11-on-dell-dimension-4100-creepy-510648/page4.html#post2753176](http://www.linuxquestions.org/questions/slackware-installation-40/cant-install-slackware-11-on-dell-dimension-4100-creepy-510648/page4.html#post2753176)

---

### Post by xen-uno on 2008-08-03
Old but still applicable ...

[http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-vs.-xubuntu-questions-505390/](http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-vs.-xubuntu-questions-505390/)

I would still run the latest version of either (again ... 8.04)

If there is still a Dell tag # on the case, you can go to dell.com, go to Support (I think), and enter that tag (service code?). Updates may still be available that way.

---

### Post by zxscooby on 2008-08-03
Xubuntu uses xfce as the window manager and ubuntu uses grub.
xfce uses less system resources. 
  I would use the alternate install cd instead of the live cd for a system that is low on ram , it uses less memory as it doesn't load the whole OS  to mem.

---

### Post by xen-uno on 2008-08-03
-R or a fresh -RW

---

### Post by ranchie on 2008-08-03
DVD-R. :)

Thanks for all the help so far, folks.

---

### Post by kahlil88 on 2008-08-04
Does it have two CD/DVD drives as shown in that picture? The problem could be that it won't boot from both drives, so you might have to change jumpers.

---

### Post by ranchie on 2008-08-04
Yes, it looks exactly the same as the one in the picture.

---

### Post by ranchie on 2008-08-04
UPDATE: I listen to your advice, folks. And I realized that my old DELL Dimension 4100 will boot off a CD-R that has Windows XP installed on it. So does that mean I should install ubuntu on a CD-R instead of a DVD-R? I do have a DVD-ROM on my old DELL, but it just doesn't boot from the DVD-R that I used to burn the ubuntu onto. 

Also, my old Dell is 866mHz and 256RAM with 60GB HD. Which version should I use? I got 6.06 version, I believe. Is that one good? 

Thanks

---

### Post by xen-uno on 2008-08-05
I thought we scolded you already on that :). Ubuntu iso's are meant to be burnt on CD-R or -RW's (700's ... not 650's). You've got enough machine there to run 8.04 though Compiz may be a bit heavy for it.

---

### Post by ranchie on 2008-08-05
Thanks so much, xen-uno. The only reason why I burned it on a DVD-R was because I saw some dude on YouTube burn his on a DVD-R as well and got it to work. I also used the DVD-R on my new Dell 530S and managed to get it to work, just can't do it on my old one even though it has a DVD-ROM. 

Thanks again!

---

### Post by xen-uno on 2008-08-05
No sweat ranch ... not sure how the youtuber could have done it on a DVD ... if not the drive then the burn program would probably error as the format is incorrect for the media. However, I did burn a super long audio DVD without errors as I recall. Couldn't play it on anything including the computer.

---

### Post by snowpine on 2008-08-05
I have a Dell laptop from about that same era. For best results, I would recommend installing either Ubuntu from the Alternate CD (not the Live CD, as you have insufficient ram... and certainly not a DVD, lol) or Xubuntu.

---

### Post by SpiXe on 2008-08-05
If nothing else will work you could try enter BIOS and make the dvd-drive first-boot and then disable the harddrive as a boot-option. Then it wont boot your windows.. Dont know if this is for any good, but maybe .. :)

SpiXe - Sorry if ive got a few misspellings :)

---

