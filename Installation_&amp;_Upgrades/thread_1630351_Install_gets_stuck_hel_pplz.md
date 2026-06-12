---
title: "Install gets stuck hel pplz"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by HeZ on 2010-11-25
Hi all,
I am having a little trouble getting Ubuntu installed :/
I am installing on a ASUS-N10J.
I have downloaded Ubuntu 10.10 i386 and burnt it to a cd, it boots fine and the install runs OK up until the screen where i am to put in my username and such.
At that point the progress bar stops at about 80% and says "ready when you are" but the proceed button is still greyed out.
Have tried several times and always get stuck at this point.

I am thinking it is possible that the dvd drive i am using to install could be a problem, as it is a rather old drive connected via usb using a hacked up external hdd caddy :p
But as we speak it is just finishing installing windows server 2008 (which it also burnt to disk) on another computer with no problems. I have burnt Ubuntu 3 times also, none work.
Is there a way i can check if the Ubuntu cd has burnt correctly?

Seems my laptop doesn't like booting from flash disk either :/
Plop is an option however i have already formatted so windows is gone already :/


Other than that... i have no clue.. Please help :p
thanks
HeZ

Problem solved thanks sikander :D

---

### Post by sikander3786 on 2010-11-25
Did you try using a lower case username?

e.g,

hez instead of HeZ

It is a known bug with 10.10 :-( but has been fixed in 11.04 :-)

Good Luck!

---

### Post by HeZ on 2010-11-25
Teehee that would be funny, i will try that thanks :D

Also i was trying to check the md5 of the burnt disk. 
found the guide here : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

However this command i cant seem to get to work
```
dd if=/dev/cdrom bs=1 count=732766208 | md5sum

```
gives 
```
No such file or directory
```

I am using cygwin in win7, the "dev/cdrom" is giving me trouble, 

that is obviously for a linux filesystem but how do i do it for windows. The drive letter of my cd rom drive is F

Thanks 
HeZ

---

### Post by sikander3786 on 2010-11-25
winMD5sum would be a better and simpler option for that.

[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows)

---

### Post by HeZ on 2010-11-25
Ahh awesome i didnt read that far haha :p

ps. yes, Ubuntu WILL kill windows one day
pps. and I WILL kill everything mac one day :0

HeZ

---

