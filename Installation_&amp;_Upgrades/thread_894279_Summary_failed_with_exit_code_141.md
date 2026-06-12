---
title: "Summary failed with exit code 141 ???"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by empire_a on 2008-08-19
Hi all,

I have been trying to install Ubuntu 8.0.4. I "**think**" i have partitioned everything right but when I get to step 5 of 7 "WHO ARE YOU" and press the *FORWARD* button I get an error message : 

_"Summary failed with exit code 141. Further information may be found in /var/log/syslog. Do you want to try running this step again before continuing> If you do not, your installation may fail or may be broken."_

This is how I set everything up:


DEVICE            TYPE         SIZE       FREE
/dev/sdb
   /dev/sdb1      nfs          62561MB   4099MB
   /dev/sdb2      ext3         10001MB   251MB
   /dev/sdb3      swap         1019MB    unknown
   /dev/sdb4      ext3/home    46448MB   unknown

Was it something to do with the partitions? How I set them up?

Im a complete newbie to Ubuntu / Linux so a response in "Ubuntu speak for dummies" would be greatly appreciated.

Thanks in anticipation 
Regards
A

---

### Post by empire_a on 2008-08-19
any thoughts guys? still having the same problem ...

---

### Post by dstew on 2008-08-19
If your ext3 partition only has 251 Mb free, maybe there is not enough room to finish the installation.

---

### Post by empire_a on 2008-08-20
thanks dstew, seems like you may be right ...
I reformatted the HD. 

I chose the manual install option and install Ubuntu to my /sdb/ drive sector (as my vista is on the sda sector). 

Everything was going great until I got to 94% and then it gave me some error about the GRUB not being able to install .... some FATAL error. 

I then chose to install the GRUB in the **/dev/sdb2 ext3/** but it still gave me the same error?? Am I supposed to install it on the /sda/ sector (where Windows is installed)??

I tried most of the sectors? 

What am I doing wrong ???

Thanks for your help, appreciate it
A

---

### Post by dstew on 2008-08-20
I assume you mean "partition" when you say "sector".

> What am I doing wrong ???You are not doing anything wrong, but the grub-install program has a bug in it that sometimes causes this problem. You are correct in trying to install to a new partition such as /dev/sdb2. See [this thread]("http://ubuntuforums.org/showthread.php?t=894460&highlight=94%25+fatal+error+grub") for some ideas on how to work around the grub-install bug.

---

