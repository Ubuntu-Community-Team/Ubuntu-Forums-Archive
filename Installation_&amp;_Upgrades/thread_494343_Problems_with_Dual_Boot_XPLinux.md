---
title: "Problems with Dual Boot XP/Linux"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by patrickmc on 2007-07-06
Hello all
Just for starters I want to explain that I recently had to format my 80gb hard drive.  When I reinstalled a copy of Windows xp, I created two partitions. One was going to be for windows and the other for ubuntu. Now, for whatever reason I chose to place windows on the second partition. After getting drivers and audio working with windows, I popped in the ubuntu cd and installed it. The partition manager left me with the following info. 
hda1 (empty for linux)
hda2 (windows)
hda3(extension)
hda5(linux swap file)

I proceeded to install ubuntu onto hda1 with no problem at all. 
The real problem started when I rebooted after the install. there was no boot menu whatsoever. I was able to press esc to bring one up, and when I did that it presented me with 3 options, boot linux, boot linux recovery, or boot linux mem test. Alas, I have no windows option. Now upon starting linux, again with no problem...the partition containing windows is untouched. I called a computer guru I know and tried to get some over-the-phone aid. He said that it was probably bad that windows was installed on the second rather than the first partition. Then he led me into editing the grub file. 
When I edited the grub file, I removed the hidden menu option, and changed the time limit on the auto-boot.
I then added the following information
"
title                   Windows
root                  (hd0,1)
makeactive
chainloader        +

I saved the file with that and did a soft reboot. I now have a boot menu that lasts for thirty seconds. and the first option on the menu now says "Windows"
Here is the problem that I took forever to get to...when I click the windows option, it then says ntldr is missing. restart. Did I enter the code wrong in the grub file? Is something else wrong? I did not edit anything in the grub file beyond that which I've already shown. Please help me any way possible, I now have a computer that only boots ubuntu (which I cannot get to connect to my usb wireless adapter ((WHOLE NOTHER PROBLEM, DIFFERENT DAY))) and the inability to boot back to windows. I can be reached at my e-mail address which I will check throughout the night and would greatly appreciate help here. I want to add that i am a complete noob with linux, and installed it just to get a feel for it and see how it worked for me.

e-mail
[email]mcmahondynasty@att.net[/email]

Thanks again, this sure can be infuriating!

---

### Post by bmorency on 2007-07-06
I think your computer guy is right. windows should be on the first partition, I think it has a problem when it is past the 8gig or so mark on the hard drive. I don't think linux has that problem because grub takes care of this problem.

---

### Post by patrickmc on 2007-07-06
So I honestly need to just format again...and restart this entire process from scratch? Is it absolutely impossible to allow or edit something so that windows can be bootable? I can do this all over, but it is so tedious.

---

### Post by confused57 on 2007-07-06
Don't know if it was a typo, but the last line should be:
```
chainloader +1
```

i.e. chainloader + (one)

---

### Post by xfile087 on 2007-07-06
> **patrickmc said:**
> So I honestly need to just format again...and restart this entire process from scratch? Is it absolutely impossible to allow or edit something so that windows can be bootable? I can do this all over, but it is so tedious.

Unless you fancy making a backup with Acronis or ghost4linux and then restoring them to the right partitions?

---

### Post by Gremlinzzz on 2007-07-06
is there any reason for you not to start clean
just make 2 partitions one for windows other for linux then delete the linux partition making it free space .
when you install ubuntu  and comes the time for install choice choose use largest continuos free space then ubuntu does the rest works every time.
note install windows first.

---

### Post by patrickmc on 2007-07-06
yes it was a typo. I am now just reinstalling. Is everyone in agreeance that this is just a matter of windows being installed on the second rather than the first partition?

---

### Post by confused57 on 2007-07-06
> **patrickmc said:**
> yes it was a typo. I am now just reinstalling. Is everyone in agreeance that this is just a matter of windows being installed on the second rather than the first partition?
Yes, Windows on the first partition is  the preferred method for a successful dual boot of Windows/Ubuntu.  

It probably won't work, but you could try booting up the Window's XP install cd, press "r" for recovery mode, then enter FIXMBR...see if you can boot into Windows,if you can then boot up the live cd and try reinstalling grub to the mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

There's probably a "snowball's chance in..." it'll work, but may be worth trying.

---

