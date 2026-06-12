---
title: "Install freezing up"
date: 2005-08-11
forum: Installation &amp; Upgrades
---

### Post by Ds136 on 2005-08-11
While trying to install Ubuntu 5.04 it seems to freeze up during the install of the base system right after doing partitions. At first it would randomly freeze up on different files, but when I would run it again it would go past that file and freeze up on something else. Now it seems to just lock up on "extracting  dpkg..." 

Also a few times during the install it would just go to a black screen or a screen of scrolling data saying the kernel failed.

I'm fairly new to Linux, any help would be greatly apperciated.

---

### Post by FLeiXiuS on 2005-08-11
Sounds like this could possibly be a bad burn but I don't want to jump the gun.  

Check the ISO to see if it was burned bad.  You can do so by using the md5 hashes.  If the hashes return as what the download locations says so.  In this case, it's Ubuntu, then you've got a great download.  If not, then you better get downloading.

**Linux**
md5sum filename.iso

**Windows**
Download md5sum.exe and extract to where ever.  Then change directories to wher ever you exctracted it to.
[http://www.etree.org/md5com.html](http://www.etree.org/md5com.html)

I'd extract it to the C drive to make it simpler.  This way you can just * cd C:/* then run the program from there.

---

### Post by zarathustra on 2005-08-11
I have the same problem. I've checked the md5 of the downloaded iso and there is nothing wrong.

---

### Post by Ds136 on 2005-08-11
ok well I ran an md5sum check and a bunch of .gz files and such came up as could not open/read. 

So I'll try downloading it again and hope it helps.

---

### Post by hexo on 2005-08-13
Hi,
I have similar installation problems as well. My pc is an old PIII 450Mhz with 128mb RAM. 

I've downloaded ubuntu 5.04. Thing is, the installation hangs at random areas. I would be considered lucky to even get to the menu page (choosing language etc which I managed to get to about 1 in 10 tries, but it hangs after that). I also tried using different parameters eg. no387, acpi=off, nolapic noapic. But it would still hang at random parts. That's why I cant pinpoint the exact problem.

I have also tried to boot using knoppix but it would fail as well. I know that the cds are working fine as I have tried them on my newer machines. I can install Ubuntu and also run knoppix on them. No problem whatsoever. Please help. 

Thanks!

---

### Post by RedTigeris on 2005-08-14
HI,
same problem here
maybe something wrong with some downloading sources? becasue i downloaded from same source 2 times but both are freezing  :???:  
could anyone who was successful to download live cd give an exact address form which to download?  :) 
thnx

---

### Post by woodfine on 2005-08-15
Also Having problem with freezing up have tried a few different installaton CDs with no luck.  It seems to freeze when  "Configuraing Apt" gets to about 50%.  I have left it all night and still no luck.

---

### Post by woodfine on 2005-08-15
just found the following fix:

Configuring apt...
 
 [=====================50%                       ]

 Testing network repository...
Press ctrl-rightarrow and then Enter to activate a console. Use 

 ps aux
to look for a process called /usr/lib/apt/methods/http and kill it: 

 kill PID
Obviously, where PID is the process id listed on the left hand side. 

(You may have to do this a few times as the installer tries to connect to different repositories.)

---

### Post by jameso on 2005-10-13
[QUOTE=woodfine]just found the following fix:

Configuring apt...
 
 [=====================50%                       ]

 Testing network repository...
Press ctrl-rightarrow and then Enter to activate a console. Use 

 ps aux
to look for a process called /usr/lib/apt/methods/http and kill it: 

 kill PID
Obviously, where PID is the process id listed on the left hand side. 

(You may have to do this a few times as the installer tries to connect to different repositories.)[/QUOTE]Thanks for the suggestion!

It worked like a charm - I had to kill 3 processes.

I assume this problem is occuring because the repositories are too busy at the moment?

---

