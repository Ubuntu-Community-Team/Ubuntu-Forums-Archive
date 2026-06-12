---
title: "no file or directory? ipscan install"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by supadupadad1 on 2010-09-12
am trying to install angry ip scanner. i downloaded it and am trying to do the next command but i am being told there is no file or directory. here is what i did. any help would be greatly appreciated. I know i have to be close. Thanks.


$ wget [http://sourceforge.net/projects/ipscan/files/ipscan3-binary/3.0-beta4/ipscan-linux-3.0-beta4.jar/download](http://sourceforge.net/projects/ipscan/files/ipscan3-binary/3.0-beta4/ipscan-linux-3.0-beta4.jar/download)
--2010-09-12 20:46:17--  [http://sourceforge.net/projects/ipscan/files/ipscan3-binary/3.0-beta4/ipscan-linux-3.0-beta4.jar/download](http://sourceforge.net/projects/ipscan/files/ipscan3-binary/3.0-beta4/ipscan-linux-3.0-beta4.jar/download)
Resolving sourceforge.net... 216.34.181.60
Connecting to sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/project/ipscan/ipscan3-binary/3.0-beta4/ipscan-linux-3.0-beta4.jar?r=&ts=1284338777&use_mirror=softlayer](http://downloads.sourceforge.net/project/ipscan/ipscan3-binary/3.0-beta4/ipscan-linux-3.0-beta4.jar?r=&ts=1284338777&use_mirror=softlayer) [following]
--2010-09-12 20:46:17--  [http://downloads.sourceforge.net/project/ipscan/ipscan3-binary/3.0-beta4/ipscan-linux-3.0-beta4.jar?r=&ts=1284338777&use_mirror=softlayer](http://downloads.sourceforge.net/project/ipscan/ipscan3-binary/3.0-beta4/ipscan-linux-3.0-beta4.jar?r=&ts=1284338777&use_mirror=softlayer)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://softlayer.dl.sourceforge.net/project/ipscan/ipscan3-binary/3.0-beta4/ipscan-linux-3.0-beta4.jar](http://softlayer.dl.sourceforge.net/project/ipscan/ipscan3-binary/3.0-beta4/ipscan-linux-3.0-beta4.jar) [following]
--2010-09-12 20:46:17--  [http://softlayer.dl.sourceforge.net/project/ipscan/ipscan3-binary/3.0-beta4/ipscan-linux-3.0-beta4.jar](http://softlayer.dl.sourceforge.net/project/ipscan/ipscan3-binary/3.0-beta4/ipscan-linux-3.0-beta4.jar)
Resolving softlayer.dl.sourceforge.net... 74.86.229.28
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 820580 (801K) [application/java-archive]
Saving to: `download'

100%[======================================>] 820,580      590K/s   in 1.4s    

2010-09-12 20:46:19 (590 KB/s) - `download' saved [820580/820580]

greg@greg-laptop:~$ sudo mkdir /opt/angry-ip-scanner
greg@greg-laptop:~$ sudo mv ipscan/ipscan-linux-3.0-beta4.jar /opt/angry-ip-scanner
mv: cannot stat `ipscan/ipscan-linux-3.0-beta4.jar': No such file or directory
greg@greg-laptop:~$ sudo mv ipscan/ipscan3-binary/3.0-beta4/ipscan-linux-3.0-beta4.jar /opt/angry-ip-scanner
mv: cannot stat `ipscan/ipscan3-binary/3.0-beta4/ipscan-linux-3.0-beta4.jar': No such file or directory

---

### Post by lloyd_b on 2010-09-12
The critical part of that output is the section that says:```
Saving to: `download'

100%[======================================>] 820,580 590K/s in 1.4s

2010-09-12 20:46:19 (590 KB/s) - `download' saved [820580/820580]
```  It looks like it created a "download" directory, and then underneath of it saved the ipscan directory, and under that the .jar file you actually wanted.

If so,```
mv download/ipscan/ipscan-linux-3.0-beta4.jar /opt/angry-ip-scanner
``` should work.

Lloyd B.

---

### Post by supadupadad1 on 2010-09-13
I already tried that. I tried it again and this is what i get back.

greg@greg-laptop:~$ mv download/ipscan/ipscan-linux-3.0-beta4.jar /opt/angry-ip-scanner
mv: cannot stat `download/ipscan/ipscan-linux-3.0-beta4.jar': Not a directory
greg@greg-laptop:~$

---

### Post by supadupadad1 on 2010-09-13
i did make the directory. it is there. And i also have the ipscan file in my download folder. i double checked the name of the file as it is spelled in the download folder and is the same as what i entered in to move the file. There is actually two files downloaded in my download folder. one is zipped and one is not. but i don't think that would make a difference would it? i have also tried quotation marks around the file name to see if that helped and i still get the same result

---

### Post by supadupadad1 on 2010-09-13
the file shows in my download folder as  ipscan-linux-3.0-beta4   this is the unzipped file
the zipped file shows as  ipscan-linux-3.0-beta4.jar  not sure which one to try to move but tried both still gives me the error

---

### Post by oldos2er on 2010-09-13
Can you open a terminal and run **ls** then post the output here?

---

### Post by supadupadad1 on 2010-09-14
It is posted at the very top

---

### Post by supadupadad1 on 2010-09-14
I also tried to drag the file to the folder and it tells me permission denied.

---

