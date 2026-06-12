---
title: "I am receiving an error while installing, please help!"
date: 2013-01-31
forum: Installation &amp; Upgrades
---

### Post by FoggyMask on 2013-01-31
Every time I try to install Ubunut 12.10, I receive the following error:

[COLOR="Red"]An error occurred:

Error executing command
>>command=C:\Users\*****~1\AppData\Local\Temp\pylE2DF.tmp\bin\resize2fs.exe -f C:\ubunutu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage:
/cygdrive/c/Users/*****~1/AppData/Local/Temp/pylE2DF.tmp/bin/resize2fs.exe -f C:ubunut/disks/root.disk 17744M [-d debug_flags] [-f] [-F] [-p] device [new_size]

For more information, please see the log file:
c:\users\*****~1\appdata\local\temp\wubi-12.10-rev273.log[/COLOR]

Also, I am unable to find the log file location.
The "*****" in the error would be where my username is located, which is why it was removed.


**EDIT: I have solved the issue.**

---

### Post by bcbc on 2013-01-31
It's probably because the download was interrupted. You can look in the log file to confirm... 

The reason you cannot find the log file is that you are manually navigating to it and some of the directories in the path are hidden (to protect the innocent). You can just open up Notepad and stick in the path to the log file in a File Open dialog, or navigate to the %TEMP% directory.

But usually when that error occurs you'll see that the size of the file and the bytes downloaded don't match.

---

