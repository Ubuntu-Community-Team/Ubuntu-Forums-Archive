---
title: "Feisty Upgrade: Says I'm out of disk spac?"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by Mets on 2007-04-19
I've been having some trouble getting my system to upgrade to Feisty.  At first I was getting an error about antesis.freecontrib.org being down, so I commented those out in my etc/apt/sources.list file.  

I am now able to proceed through the upgrade until I need to start downloading files, upon which the update manager informs me that I am out of disk space and that I need to free up at least 407mb in /usr.  This is blatantly wrong, as I have gigs of free space left.  Does anybody know how to fix this?

---

### Post by Fittersman on 2007-04-19
im having the same problem, first it said about 315MB (i think) and then i ran sudo apt-get clean, now all i need to free is 54.3 MB

try that sudo apt-get clean command

but, you need to free memory in the /usr folder, it doesnt matter if you have alot of free space elsewhere (i just dont know what is ok to delete in there, so maybe someone that does know could help us out)

---

### Post by Mets on 2007-04-19
yes maybe somebody can help us out.  There's a cap on the space in /usr??  :???:

---

### Post by Fittersman on 2007-04-19
yeah, thats what im concluding because of what i have done so far (i tried freeing space in my /home folder but that didnt change the number)

do you have a separate /home folder partition? that could be our problem (i have a separate one, and maybe that separate one with the system files is full)

maybe we could go to add or remove and uninstall some programs? would that free up some space in the /usr folder?

maybe updating right away isnt such a good idea, there seem to be a few problems on the forum now, maybe i will wait until some of them get fixed, after all, why fix what isnt broken?

---

### Post by Mets on 2007-04-19
I don't have a seperate home folder partition so I don't think that is it.  Appearently freeing up space anywhere won't work, as I already have plenty of free space.  I was hoping I wouldn't have to wait, but I guess I don't have much of a choice unless somebody knows how to fix this.

---

### Post by Mets on 2007-04-19
Well, I found a way to increase the size of /usr here:
[http://forums1.itrc.hp.com/service/forums/questionanswer.do?threadId=571296](http://forums1.itrc.hp.com/service/forums/questionanswer.do?threadId=571296)

But that seems ridiculously complicated.  Maybe somebody knows a better way, or maybe it would be easier to just reformat and reinstall.

EDIT
Actually I think that is if /usr is on a separate partition only, so I wouldn't try it.  Hopefully we can  get some help on this.

---

### Post by Meister_Eder on 2007-04-19
Had the same problem. Solved it by freeing up more space. I had to have about 1.5 GB available to convince the upgrade-program.

---

### Post by Fittersman on 2007-04-19
...thanks for your help :D

---

### Post by Fittersman on 2007-04-20
...maybe now is a good time to download the cd image, burn it on the cd and format my HD so i can reinstall windows, its been givin me major problems for a while (i just gave up on it, its been like 2 years already, im happy with ubuntu, but i miss games :()

---

### Post by hagantic42 on 2008-04-15
Ok, I'm a moderately good user of linux. But I have a 32 mb /boot partition that is has 
```
hagantic@Gigantor:/boot$ ls
abi-2.6.20-16-generic         memtest86+.bin
config-2.6.20-16-generic      System.map-2.6.20-16-generic
grub                          vmlinuz-2.6.20-15-generic
initrd.img-2.6.20-16-generic  vmlinuz-2.6.20-16-generic
lost+found

``` 
means i have 
```
hagantic@Gigantor:/boot$ df -h /boot
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              31M   14M   16M  47% /boot

```
Now I know I have part of a kernal left (I've since removed it) but a partial upgrade from 7.04 to 7.10  yielded the same problem you have all been having over a year ago. The upgrade says it needs 31.5 megs of space on my 32 mb partition so yeah I NEED HELP.

---

