---
title: "dual boot situation"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by windowsfree on 2010-01-09
I need to install Windows 7, but I have Ubuntu 9.10 on a 160 gig HD right now.  There is a second 40 gig hard drive but it has backed up files etc on it and I don't want to use that.  Is there a way I can put win7 on the existing 160 gig drive without losing my boot record (grub) etc.?  

I have read many forum threads and did tons of google searchs.  I just don't want to burn the entire setup.

I have my Ubuntu setup exactly the way I want it and don't want to wipe anything.

Thanks

---

### Post by sanderd17 on 2010-01-09
I've never tried virtualisation but can't you use that?

---

### Post by starcannon on 2010-01-09
Here is a very nice, and simple tutorial that should get your Windows 7 and Grub dreams to come true.

[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

Good luck and have fun.

---

### Post by raymondh on 2010-01-09
the tutorial link provided by starcannon is an excellent how-to-go-about installing win7.  As you know, win7 will install it's bootloader in the MBR hence overwriting GRUB.  Also, if you create a NTFS partition beforehand and install win7 unto it, you will eliminate the 'extra' 100mb primary partition that win7 installs by default.  This 'extra' partition is a bootloader recovery/image partition which you can live without ... if you do choose to.  

Note that you are using 9.10 which by default uses GRUB2.  If indeed using that, here is a link on how to [re-install GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD") and possibly [editing grub.cfg]("http://ubuntuforums.org/showthread.php?t=1195275") to include the win7 install.

If you are using GRUB-Legacy ... just follow the tutorial linked by Starcannon.

As always, back-up your files first.

Regards,

raymond

---

### Post by windowsfree on 2010-01-09
The solutions provided do seem complete and not too dificult.  I have Win7 in a virtual machine right now, but my host only has 1 gigabyte of memory and I feel, if I update to 2 gigabytes (all that my older machine will allow), I should be able to run Windows 7 that way and not have such a slow experience.
Thank you both for your input and I did keep this thread saved in a word document if I do choose to try a Windows install. I think installing it will be best because then it can take advantage of my video card, in the virtual machine I can't load a decent driver.
Thanks!!!

---

