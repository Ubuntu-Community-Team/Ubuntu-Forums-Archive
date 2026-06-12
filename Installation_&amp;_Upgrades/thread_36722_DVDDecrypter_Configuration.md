---
title: "DVDDecrypter Configuration"
date: 2005-05-24
forum: Installation &amp; Upgrades
---

### Post by mjbeam on 2005-05-24
I am trying to get DVDDecrypter working and can't get it to recognize my CD ROM drive or my DVD drive. The dosdevices configurations look OK. I ran Notepad and can navigate to the DVD drive and see the VIDEO_TS and AUDIO_TS files.

Also, in DVDDecrypter, if I select Tools -> Create DVD MDS File then select Add, I can see my DVD in file selection dialog box, and even go into the VIDEO_TS and AUDIO_TS directories and see the files. But for Source it still says No Devices Detected. I do have the SPTI - Microsoft interface selected. Any ideas?


-Mike

---

### Post by logan2004 on 2005-05-24
did you try following the first section of this HOWTO: ?????

[http://ubuntuforums.org/showthread.php?t=27369&highlight=dvddecrypter](http://ubuntuforums.org/showthread.php?t=27369&highlight=dvddecrypter)

i followed this and that got wine/dvd decyp recognizing my dvd drive fine.

good luck

---

### Post by mjbeam on 2005-05-24
Thanks Logan. That and changing

 ~/.wine/config from

**"Windows"="winxp"**

to...

**"Windows"="nt40"**

fixed it up. 


Thanks again...Mike

---

### Post by oritpro on 2005-06-06
Some bad new today about DVDDecrypter. 

[http://www.cdfreaks.com/news/11914](http://www.cdfreaks.com/news/11914)

---

