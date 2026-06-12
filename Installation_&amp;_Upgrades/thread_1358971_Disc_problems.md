---
title: "Disc problems"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by Pokesomi on 2009-12-19
Ok I have an iso for 9.10 and every time I burn it with disk utility on mac several errors crop up in 53 files and it's preventing me from installing it on an old laptop.  I can't get the disk to burn properly. The image is 32mb larger than what the cd-r can hold.  I can't use a DVD cause the laptop only ha a cd-rom drive and can't boot via USB.  Any ideas

---

### Post by raymondh on 2009-12-19
> **Pokesomi said:**
> Ok I have an iso for 9.10 and every time I burn it with disk utility on mac several errors crop up in 53 files and it's preventing me from installing it on an old laptop.  I can't get the disk to burn properly. The image is 32mb larger than what the cd-r can hold.  I can't use a DVD cause the laptop only ha a cd-rom drive and can't boot via USB.  Any ideas

Karmic amd64-bit is 690.8mb using a torrent. I'm curious about the file size of your iso.

Also, see if the "old" computer will meet the minimum specs of karmic.  Otherwise, you'll might have to consider downloading and burning a 'lighter version' or the 'alternate install'.

Regards,

---

### Post by Pokesomi on 2009-12-20
> **raymondh said:**
> Karmic amd64-bit is 690.8mb using a torrent. I'm curious about the file size of your iso.

Also, see if the "old" computer will meet the minimum specs of karmic.  Otherwise, you'll might have to consider downloading and burning a 'lighter version' or the 'alternate install'.

Regards,

turns out there were two issues going on. One the optical disk drive was going bad and two the space problem wasn't one.  The way mac reads file sizes is more accurate. I.e. 1024 bytes = 1kilobyte. As for the opticle drive, I got it replaced and burned from windows. It worked fine

---

### Post by lmarmisa on 2009-12-20
You probably have a wrong iso file. 

I would recommend you to check the integrity of your iso file (md5 or sha1).

These are the correct values of md5sums and sha1sums for the iso files of Karmic:

[http://releases.ubuntu.com/karmic/MD5SUMS](http://releases.ubuntu.com/karmic/MD5SUMS) 
[http://releases.ubuntu.com/karmic/SHA1SUMS](http://releases.ubuntu.com/karmic/SHA1SUMS) 

If your ISO file is not correct, download it again from

[http://www.ubuntu.com/](http://www.ubuntu.com/)

Best regards,

Luis

---

