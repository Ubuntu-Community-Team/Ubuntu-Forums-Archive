---
title: "Installation"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by anathan591 on 2010-11-30
Hi Guys,
 
I am ridiculously new to ubuntu and I am sure this has probably been posted before... But I have built a computer for a friend and he wants to run only ubuntu on it. 
 
Mobo: Gigabyte G41MT-D3
CPU: Intel E5400
RAM: Kingston 4GB
HDD: WD Caviar Green 880GB
DVD: Samsung Spin
 
I have tried installing 10.10 and 10.04LTS. I have tried USB and CD. The closest I have gotten was last night with the 10.04LTS alternate version. But it told me it was unable to finish selecting all the software and only rebooted to the busybox menu. I tried a few commands that I have read in the forums in order to ATTEMP to load the GUI but got nothing. 
 
I have tried again this morning, with the standard 10.04LTS version, and have received the following error "[Errno 5] Input/output error" and it claiming that I have a faulty CD/DVD drive. :mad:
 
The issue for me is that I have installed Vista initially to install all the drivers etc. So IMO there can't be anything wrong with my optical drive. 
 
Any help would be much appreciated. BTW the CD versions have been burnt at x4, x8 and maximum speeds. All return the same outcome.

---

### Post by tommcd on 2010-11-30
> **anathan591 said:**
> 
 

I have tried again this morning, with the standard 10.04LTS version, and have received the following error "[Errno 5] Input/output error" and it claiming that I have a faulty CD/DVD drive.
If we assume that the cdrom drive is ok, this error would likely indicate a bad install CD.
When you boot the Ubuntu install CDs, the first thing you should do is to run the option "*Check CD for Defects*" as is shown here:
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
If the CD integrity check passes without errors, then the CD is good. If the CD does not pass the integrity check, then perhaps try burning the CD on a different computer if you can. And be sure to burn the CD at the slowest possible speed to reduce the chance for errors.
You should also check the *md5sum* of the iso image you downloaded to be sure it is not corupt:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

And welcome to the Ubuntu forums!

---

### Post by pricetech on 2010-11-30
My guess would be a bad ISO since you've burned more than one copy of it.

---

### Post by anathan591 on 2010-11-30
I thought the same thing about the ISO, but I have downloaded the versions from the ubuntu download page and I have downloaded bittorrent versions. I currently have 3 versions of each ISO. They all produce the same outcome. 
 
Frustrated because I was able to instal vista in all of about 12 minutes. 
 
I'm at work now so not able to check the ISOs or the disks. I will check when I get home tonight. Hopefully that sheds some light on it.

---

### Post by akand074 on 2010-11-30
Did you burn them at a slow speed? I usually always burn OS ISOs at the slowest possible speed and check the "verify after burn" box.

---

### Post by anathan591 on 2010-11-30
> **akand074 said:**
> Did you burn them at a slow speed? I usually always burn OS ISOs at the slowest possible speed and check the "verify after burn" box.
 Yes I burnt them at 4x, which is the slowest speed my burner will go. I didn't verify the burn though. 
 
My initial disk which was burnt at maximum and it barely reads at all. I really want it to work (obviously) so I'm willing to try anything.
 
Do you guys use Putty to run terminal sessions?

---

### Post by anathan591 on 2010-11-30
BTW would it be an issue that my CD/DVD drive is SATA?

---

### Post by pricetech on 2010-11-30
SATA drive should not make a difference.

Yes I use Putty under windows.  I also use NX from nomachine dot com which gives me the full desktop.  I like it.

---

### Post by akand074 on 2010-12-01
Hmm.. perhaps try to verify the disk after burning. You should also check the disk using that option from the installer. If both those pass then it's unlikely your cd/dvd drive. Where as I'm stumped. If it doesn't pass then that may just be the problem.

---

### Post by anathan591 on 2010-12-02
Well I've just rechecked the md5sum and it is different from the secure hash page... weird! 
 
I've just checked EVERY iso I have downloaded this week. 5 10.10s, 3 10.04.1s and 1 CentOS and none of them match the md5sums they're supposed to.
 
What does that mean?

---

### Post by anathan591 on 2010-12-02
Oh Oh Oh!
The 10.10 alternate ISO has the same number! 
Now if only I could figure out the way to install it lol

---

### Post by anathan591 on 2010-12-02
And it worked! Woo Hoo! Thanks for all your help guys

---

### Post by tommcd on 2010-12-02
> **anathan591 said:**
> 
I've just checked EVERY iso I have downloaded this week. 5 10.10s, 3 10.04.1s and 1 CentOS and none of them match the md5sums they're supposed to.

So the .iso files themselves are all corrupt? Or are you talking about the CDs that you have burned are all bad?
First, how are you checking the md5sum of the downloaded iso image? If you are checking the md5sum on linux, simply run: "*md5sum iso_name.iso*" where *iso_name* is the name of the iso file.
Also, try downloading the iso Ubuntu iso files from different mirrors.

EDIT: Sorry, I did not notice the second page of this thread when I posted.
Anyway, glad you got it worked out!

---

