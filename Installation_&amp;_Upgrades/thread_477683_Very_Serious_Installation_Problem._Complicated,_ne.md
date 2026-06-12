---
title: "Very Serious Installation Problem. Complicated, need advanced help."
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by mastergandalf19 on 2007-06-18
Im installing ubuntu studio alternate i386 on a DVD burnt ISO. The first time i inserted the disk it chucked out this:

/------------pstk--------------rstk----------\0, Drive9F
|         :                         :
|         :                         :
|         :                         :
|         :                         :
|         :                         :
|       0:            0.0
|       1:            0.0
|       2:            0.0         0.0 ffffffff.5
|       3:            0.0         0.1    121d.15
\---------------------------------------------/
err8ip21d4:                10.7
|
|
\---------------------------------------------/

when i press C (random discovery, after hours of key bashing and anger)

a part of the message changes, below the 2nd part of the message
err 8
ip6ab: 2c.7


END

ok after that error came up i looked in the forums and found nothing, so i thought "Here we go again, i hope this isnt the 9th time of a bad burn, ill restart and try again."

so i restarted it, and magically, the install screen splashes up, but not before displaying "Uknown keyword in config file" as an error message. This then disappears and when i click on install ubuntu studio, or even check disk option, it loads the kernel then dumps this almighty pile of rubbish on you.

Int14: C122e0000000 e00000000 EIPc020c384 c000000060 flags 00010003 Stack: c00f7d20 c03f129b c037b18c 00000002 c00f7d29 000fd20 00000000 00000000


Does anybody have the FAINTEST idea what the HELL that means? Has anybody had this problem? Before you say it, yes ive downloaded and burnt multiple versions on multiple disk brands from http and torrent/ftp sources, all the md5 hash sums dont match but i burned anyway. I burnt at 1x, 2x 4x 8x and x16, and im running a p4 2.8ghz 512mb ddr 400, 120gb hdd samsung, nvidia 128mb geforce fx5200 w/wireless connection 802.11g. Have windows XP on a different partition. 

Any ideas/suggestions/solutions here: mastergandalf19 -at- hotmail -dot- com, or use this post.

thanks matt

---

### Post by bapoumba on 2007-06-18
> **mastergandalf19 said:**
>  all the md5 hash sums dont match but i burned anyway.
If the md5 sum fails, then the files you downloaded are corrupted.
Did you dl from here ?
[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

In addition, I'm editing your email in first post to be readable by members but not by bots.

---

### Post by mastergandalf19 on 2007-06-18
Ok i finally managed to get a MD5 matched download, am burning it now at 1x speed. its slower than an asthmatic ant with some heavy shopping, but ittl have to do. if this doesnt work Im going to go and buy another hdd to install it onto, and get them to send me a disk. and no i got it from the official ubuntu STUDIO site. thanks anyway

---

### Post by bapoumba on 2007-06-18
Ubuntu-studio, hmm, sorry I over read that in your post...
[http://ubuntustudio.org/downloads]("http://ubuntustudio.org/downloads")

---

### Post by mastergandalf19 on 2007-06-18
ok. from that last post, would I be wrong in deducing that this forum, the only ubuntu support forum around, doesnt support ubuntu studio installation problems?...

Anyway, i burnt it, it crashed, same error, im fed up. good night. any other ideas please come forward.

---

### Post by crxvfr on 2007-06-18
[You could get a free copy from ubuntu and circumvent lots of potential problems.]("https://shipit.ubuntu.com/")

---

### Post by bapoumba on 2007-06-18
> **mastergandalf19 said:**
> ok. from that last post, would I be wrong in deducing that this forum, the only ubuntu support forum around, doesnt support ubuntu studio installation problems?...
No no :)
I just corrected the dl link and apologized. I could have given you the correct link in the first place, and was quite mad at myself :)
Support is here.

---

### Post by mastergandalf19 on 2007-06-18
Ok. i havent got 10 weeks, i have 10 days perhaps? How does i take 10 weeks to send a CD via airmail. Jeesus. Is there anyone on this forum with sufficient Ubuntu knowledge to figure out that error message i first posted? If so, please help me! the DVD image is not corrupt, so it must be something to do with my machine. 

[http://rapidshare.com/files/38015005/dxdiag.JPG](http://rapidshare.com/files/38015005/dxdiag.JPG)

a link to show my dxdiag results. 

What would stop the linux kernel from loading off the cd? Perhaps i need to install ubuntu 7.04 normal before i upgrade to studio? "sigh".

---

### Post by zettberlin on 2007-06-18
> **mastergandalf19 said:**
> 
Perhaps i need to install ubuntu 7.04 normal before i upgrade to studio? "sigh".

At east I did so several times with good success. Just fire up a Standard-U/K/Xbuntu-Disk, install ist and apply the Metapackages for linux-lowlatency and ubuntustudio.

---

