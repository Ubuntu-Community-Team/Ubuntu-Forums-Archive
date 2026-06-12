---
title: "Help to extract tar"
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by ozstar on 2010-07-03
HI,

I am a newby!!  :-(

I have downladed Xampp 1.7.3a and am trying to extract it to /opt.

I can see it in my /tmp/ dir.  (179 MB)

When I do it via the desktop panel it says I do not have the right permission to extract to /opt/ and when I do it in a terminal with this..

david@Linux:~$ sudo tar xvfz xamp-linux-1.7.3a.tar.gz -C /opt

I get..

tar: Cannot open" No such file or dir
tar: Error not recoverable etc etc

Please how do I extract this?

oz

---

### Post by Dr_Willis on 2010-07-03
Bash basics 101. :)  you want some commands similer to the following.

```
cd /opt/
sudo tar xzvf /path/to/the/file.tar.gz
```


that 'changes' directory to the location you want the thing to do into.
then extracts it.  use the TAB key to complete the proper path/name. 
and remember that linux IS case Sensitive.


 your error is because you are not giveing the proper path TO the file. Its not in the 'current directory' its in /tmp/ as you said.

The following Might work. Its all about paths and the directories


```
 sudo tar /tmp/xvfz xamp-linux-1.7.3a.tar.gz -C /opt
```

---

### Post by ozstar on 2010-07-03
Okay. Got it happening

---

