---
title: "This is ridiculous"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by unoooo on 2008-01-06
Ok i have downloaded and burned ubuntu 3 times.  I first burned it at full speed and it didn't work.  i re-downloaded it and burned it at 2x speed and it didn't work then i re-downloaded it again and burned it at 4x speed and once again it doesn't work WTF and i doing wrong?

---

### Post by Bachstelze on 2008-01-06
Now, now, now... How about calming down a bit to begin with, and then telling us *exactly* what doesn't work ? :)

Also, did you check the MD5 hashes before burning ?

---

### Post by taurus on 2008-01-06
How did you burn it?  Did you burn the ISO as an image file with your burner software?

[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29)

---

### Post by adam.tropics on 2008-01-06
How exactly are you burning the cd? [Perhaps this]("http://www.psychocats.net/ubuntu/iso") may help.

edit: wow, it's a race!!

---

### Post by unoooo on 2008-01-06
Ok ok ok.  Yes i have checked the md5 everytime.  Ok so i burn the cd (burning it as an image not a data disk) then i restart my computer and it boots into live cd (so far so good) so i click install chose my settings and then click install and it says formating and 5% then then about a minutes after it says checking files then copying files.  About 30 seconds after that it says error there might be a problem with your disk, dvd drive, or hard drive.  But my hard drive is fine i have install windows on it many times and install ubuntu 7.04 (my brother downloaded and burned it and then he lost the cd) on it with no problem.

now i just burned the disk so i dunno what could be wrong with that.  Like no scratches or anything.  I just got my dvd burner like 2 months ago so it is pretty much brand new.  And I have never had a problem with my hard drive.

sorry but this is so frustrating

---

### Post by taurus on 2008-01-06
At the first screen, instead of picking the first option to boot from the CD, why don't you have it scan your disc to see if there is something wrong with it first?

---

### Post by unoooo on 2008-01-06
ok ill try that and see what it says

edit*** ok i did that check cd for defects and it says there is 13 errors on the disk

---

### Post by Craigus on 2008-01-06
Are you using CD-RW or CD-R media ?

---

### Post by taurus on 2008-01-06
> **unoooo said:**
> ok ill try that and see what it says

edit*** ok i did that check cd for defects and it says there is 13 errors on the disk

If there are errors, don't even waste your time running or installing from that disc.  It will not work.

---

### Post by unoooo on 2008-01-06
Craigus: i am using cd-R
taurus: do you have any advice for how i should burn it? what program i should use?

---

### Post by taurus on 2008-01-06
There's a link in post #3.

---

### Post by unoooo on 2008-01-06
ok i followed that guide and then i restarted and checked the cd for errors and now it says 21 errors...

---

### Post by Craigus on 2008-01-06
Try different media. Sometimes RW works better with a particular combination of optical drives.

---

### Post by unoooo on 2008-01-06
i only have cd-R type cd's

---

### Post by shifty2 on 2008-01-06
I had a similar sort of issue. My installation hung at a certain point everytime and whinged about similar things to what oyours does. I solved it by running chdsk in windows and then rebooting windows a couple of time. 

Haha woops. wrote assuming you had a windows partition - if you don't totally ignore that advice.

---

### Post by Shazaam on 2008-01-06
It could be a bad cd/dvdrw drive too. Take the disk that you burned the slowest and try it on another pc (a friends or at a computer store). If it still shows errors  try different media; also check the data cables on your drive.

---

### Post by Bllasae on 2008-01-06
If you're not using Windows XP, there's a program in the Accessories folder that checks the disk. Otherwise, I think that chkdsk works on a disk drive.

---

### Post by Gina on 2008-01-09
If you have A DVD writer on the download machine and at least a DVD-ROM drive on the destination I recommend using DVDs.  I've found DVDs much more reliable than CDs and much faster in use.  On my desktop I need to burn CDs very slowly ie. at about 6x whereas DVDs are fine burnt at full speed.  This is using the built-in burner in Ubuntu.  Go to the directory/folder containing the ISO file and right-click on it - choose **Write to CD**.

Before getting Ubuntu going fully I used Windows XP and Nero to burn discs.

Although all the info is available here and on the Ubuntu main website, there is so much info that it is sometimes not that easy to find things so I created my own website to help online friends - [http://www,ginad.org.uk]("http://www,ginad.org.uk") - you might find that helpful.

---

### Post by Sef on 2008-01-09
> do you have any advice for how i should burn it? what program i should use?

Advice on how to burn:  [How to Write ISO Files to CD]("http://www.petri.co.il/how_to_write_iso_files_to_cd.htm").

To burn an iso, use [Isorecorder]("http://isorecorder.alexfeinman.com/isorecorder.htm").

---

### Post by strip21 on 2008-01-09
unooo

May i ask if you are using a Dell PC, As i had a problem just like this on a Insiron 530

I found that it was due to dell having a SATA Raid card and i have to set this (in bios) to RAID and not standard. After i did this Ubuntu installed. When its finnshed i swopped it back to standarded and all was well. 

I don't know why it did but it did. hope this helps

---

