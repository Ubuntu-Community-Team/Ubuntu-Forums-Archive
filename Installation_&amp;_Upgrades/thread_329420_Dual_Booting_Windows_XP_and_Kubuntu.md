---
title: "Dual Booting Windows XP and Kubuntu"
date: 2007-01-01
forum: Installation &amp; Upgrades
---

### Post by HarrisonHopkins on 2007-01-01
Ok, for Christmas I received a Dell Inspiron E1505. I have decided that I want to dual-boot Windows XP Media Center and Kubuntu 6.06 LTS. I am on the part of the installer now that is "Prepare Disk Space." Now, here is where I am getting confused. There are 3 options.

"Resize SCSI1 (0,0,0), partition #2 (sda) and use freed space"
"Erase entire disk: SCSI1 (0,0,0) (sda) - 120.0 GB ATA TOSHIBA MK1234GS" (Why does it say ATA? Its a SATA drive....)
"Manually edit partition table."


If I'm right, I should pick the first option. I have decided that I want a 25GB partition for Kubuntu, so I move the slider to 25GB. However, when I press continue, I get the message "Error freeing space to install" or something like that. What am I doing wrong?

I'm using a Live CD.

---

### Post by eggdeng on 2007-01-01
I had problems partitioning when I installed 6.06. In my case it seemed to be due to the version of the partitioning tool (gparted) on the installation cd. So I downloaded gparted live cd, (google for gparted) partitioned and then went ahead with the install.

---

### Post by confused57 on 2007-01-01
I agree, the gparted live cd is a more updated version of gparted, here's some screenshots:
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Get it here:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by HarrisonHopkins on 2007-01-01
So, with that CD, I can take 25GB out of my 102GB Windows partition, and use it to install Kubuntu?

---

### Post by Bartender on 2007-01-01
Should be able to.  Dell puts those stupid recovery/utility partitions all over the HDD and that seems to cause some people trouble.

Any way, download and burn the GPLCD and see what happens.

---

### Post by Rashid584 on 2007-01-01
try to defrag your windows partition before you repartition btw

-Rashid

---

### Post by HarrisonHopkins on 2007-01-01
I could have been warned before hand that it would take so long.... Almost 3 hours it says... Should have made the Windows Partition smaller so that it wouldn't take so long it seems....

@Rashid: I did that before hand. Need to, too. More red than I have seen in a while....

@Bartender: Don't forget the MediaDirect partition.... No point for it when you have a Windows Media Center PC. Just a modified version of it....

---

### Post by Rashid584 on 2007-01-01
3 hours??

didnt know it takes that long...it shouldnt :S although tbh iv never resized anything more than a couple gigs most (i have a relatively small hd)

-Rashid

---

### Post by HarrisonHopkins on 2007-01-01
Yea. 30 minutes to scan the 80GB left, and then 2 hours 30 minutes to copy. I have an hour left on the copy. I hope that is it....

---

### Post by HarrisonHopkins on 2007-01-01
Just so you all know, I got Kubuntu dual booted now. Thanks for all the help!

---

### Post by Rashid584 on 2007-01-02
excellent :D

-Rashid

---

