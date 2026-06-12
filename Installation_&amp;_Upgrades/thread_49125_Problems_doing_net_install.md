---
title: "Problems doing net install"
date: 2005-07-15
forum: Installation &amp; Upgrades
---

### Post by Jeviar on 2005-07-15
Hi all! 

I managed to install ubunto a few days ago using netinstall. However, I did it manually because I wanted to dual boot my computer with Windows XP. Everything was alright however, the system was just too slow. OpenOffice takes ages to load. Firefox will open fast, but there will be a noticeable lag after 3 tabs are opened. Upon checking with a couple of my friends, I realised I hadn't created a swap partition while doing up the partitioning. One of them advised me to reinstall the whole OS since it's a fairly new install and there's nothing important in the files.

However, I've been trying for almost 2 days now but there seems to be something wrong connecting to the network. I haven't done anything differently with my very first installation. It seems that while connecting to any of the online archives, my installation will hang after awhile.

Can't remember any error messages now as I'm back on my laptop. However, I do remember getting prompts to change mirrors. I wonder is there a problem with the online archives instead of my computer?

---

### Post by codejunkie on 2005-07-15
alot of people have been having some issues like md5 checksum and timeout errors with the us mirrors like 
```
http://us.archive.ubuntu.com/ubuntu hoary main restricted
``` that might be your problem just remove the us. from the urls in your sources.list file they should look something like this when your done
```
http://archive.ubuntu.com/ubuntu hoary main restricted
``` 
dont know for sure if this cause of your problem but it might be something to check hope this helps.

---

### Post by Jeviar on 2005-07-15
okay. but where do i enter that? i don't seem to have a sources.lst file. all i see are those blue screens prior to installing (ie, partition manager, etc). there is a section where it does ask me to change mirrors but that's all. i tried to get into the australian mirrors, etc but all seemed to hang up after awhile.

---

### Post by codejunkie on 2005-07-15
[QUOTE=Jeviar]okay. but where do i enter that? i don't seem to have a sources.lst file. all i see are those blue screens prior to installing (ie, partition manager, etc). there is a section where it does ask me to change mirrors but that's all. i tried to get into the Australian mirrors, etc but all seemed to hang up after awhile.[/QUOTE]

i don't exactly know with the ubuntu installer because i have never done a net install but i know with the debian installer you can manually edit your apt/sources.list when doing a net install and ubuntu is based on debian so i would assume there is an option to do so i just don't know how because i have never tried to do it with ubuntu, if you can't find an option to manually edit your apt sources just try different non-us mirrors until you find one that works.

---

### Post by Jeviar on 2005-07-16
okay. thanks. actually i kinda gave up doing a net install. i think there's just some problems. waiting for my pressed cds to arrive. funny thing too actually. i downloaded the .iso files online and from 3 diff non-us servers. all 3 were burnt properly on to fresh cd-r discs.

i burnt them using different burn speeds. all in all, it was like a total of 9cds. none of them were detected by my cd-rom. i tried putting in the live cd, it boots straight. i put in the win xp installation cd, same thing. boots without a prob. so, is there a problem with the files i downloaded? and oh yes, the 3 .iso images i downloaded were also downloaded twice. just to make sure nothing was wrong with the download.

i have no idea with the md5checksum. not too sure where do i check it actually. but 3 diff servers, downloaded twice, burnt over 9 times, giving the same problem? i don't think it is my cd-rom drive that has a problem.

---

