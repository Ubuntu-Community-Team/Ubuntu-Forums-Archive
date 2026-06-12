---
title: "Ubuntu Install doesn't work"
date: 2005-02-27
forum: Installation &amp; Upgrades
---

### Post by squirebug on 2005-02-27
Dear All,

I have a fairly old Intel PC with a dual boot installation of Windows XP and Libranet.    I attempted to install Ubuntu over Libranet with no success.  

After changing the bios to boot first from the CD, I put the Ubuntu installation CD in the CD drive and rebooted.  After some delay while it searched the CD, I was presented with the usual Libranet Grub start with my choice of windows or libranet.  It appears that it is unable to recognise the Ubuntu installation CD as a valid boot device. 

How can I fix this?

Thank you for your help.

---

### Post by Seandq on 2005-02-27
[QUOTE=squirebug]Dear All,

I have a fairly old Intel PC with a dual boot installation of Windows XP and Libranet.    I attempted to install Ubuntu over Libranet with no success.  

After changing the bios to boot first from the CD, I put the Ubuntu installation CD in the CD drive and rebooted.  After some delay while it searched the CD, I was presented with the usual Libranet Grub start with my choice of windows or libranet.  It appears that it is unable to recognise the Ubuntu installation CD as a valid boot device. 

How can I fix this?

Thank you for your help.[/QUOTE]
 First, make sure it is the Ubuntu disk. Countless times when I have done this, I have found I put the wrong disc in on mistake.

Secondly, if it IS Ubuntu's disk, go back to Libranet and re-burn another CD. Sometimes a bad  burn occurs, LINUXISO is corrupted, and the file's skipped.

Hope I helped.

Regards,

---

### Post by Eddie on 2005-02-27
[QUOTE=Seandq]First, make sure it is the Ubuntu disk. Countless times when I have done this, I have found I put the wrong disc in on mistake.

Secondly, if it IS Ubuntu's disk, go back to Libranet and re-burn another CD. Sometimes a bad  burn occurs, LINUXISO is corrupted, and the file's skipped.

Hope I helped.

Regards,[/QUOTE]
 I also had problems with installing ubuntu because my internet never worked  with the modem. And i wanna know how to fix  the problem. But i think its because of the comcast modem.    :-k

---

### Post by squirebug on 2005-03-06
Thank you for your  help, but unfortunately I still have had no luck.

I have burned the cd two additional times, verified that ubuntu is on the cd and verified that  the bios is looking at the cd first for boot.  But it still won't  install.  In fact it appears that the cd is being entirely ignored.

Is there any way to check that the file downloaded properly and was burned correctly to the cd?

Thank you.

---

### Post by Gary Powers on 2005-03-06
Google "WINMD5SUM" and download/install the program under XP.  I can't remember the link, but you will find it quickly.  Then get the proper md5sum from your Ubuntu download site and compare it to the results of your check.

It does sound like a bad download or burn.

All the best!

Gary

---

### Post by alastair on 2005-03-06
As well as the "md5" sum test, make sure you are burning the ISO image you downloaded as an "image" i.e. CD image, iso image or whatever.

---

### Post by squirebug on 2005-03-06
Thank you for the advice.  

I did do an md5sum check.  However,  I could not find an md5sum check number for the file i downloaded.  The file I downloaded was warty-release-install-i386.iso.  The only md5sum I could find on the ubuntu website was for warty-install-i386.iso and the numbers did not match.  Does the website have the proper checksum for the current download, and, if so, where can I find it?

Thank you.

---

### Post by alastair on 2005-03-06
Is there a file called "MD5SUMS"? It is in there e.g.

[http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/releases/warty/release/MD5SUMS](http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/releases/warty/release/MD5SUMS)

---

### Post by poofyhairguy on 2005-03-06
[QUOTE=Seandq]First, make sure it is the Ubuntu disk. Countless times when I have done this, I have found I put the wrong disc in on mistake.

Secondly, if it IS Ubuntu's disk, go back to Libranet and re-burn another CD. Sometimes a bad  burn occurs, LINUXISO is corrupted, and the file's skipped.

Hope I helped.

Regards,[/QUOTE]

Thirdly, make sure it is the right CD. Warty ISO. 500+megs. I pulled my hair out the first time trying to install the release cd!

---

### Post by Zyk0tiK on 2005-03-06
I had a lot of problems burning it in windows... made 4 coasters before I gave up, then in slackware i checked the md5 and it was spot on, so i tried burning it in linux and it worked perfectly.

Guess it may be a windows thing.

---

### Post by squirebug on 2005-03-07
Thank you for the info!!  I was trying to install the release cd.

Will switch to non-release, which does have an m d5sum.

---

### Post by Ray Hamilton on 2005-03-07
You mentioned that your machine was an older machine.  May be obvious but can your CD-ROM read CDs that have been burned rather than pressed?  Neither of my two older (pre-1995?)  machines can read CD-Rs let alone CD-RWs

---

### Post by Ray Hamilton on 2005-03-07
lol. posted my reply before I'd read all the thread, especially the last one!

---

