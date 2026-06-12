---
title: "Cant install java"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by TurtleJuice on 2010-03-30
I have downloaded java multiple times but cant complete the first step of installing it i'm following the isntructions at there site and it says to type it but also has a not about the version not sure if thats why but it wont finish the first step of identifying the file.  Is there an easier way to get java run time i have the basic ubuntu adn am very new have only the basics at the moment and any help is appreciated thanks.

---

### Post by TurtleJuice on 2010-03-30
someone please tell me how to get java

---

### Post by windoze1 on 2010-03-30
you just go to java website and download it, make sure u get correct version for your op system

---

### Post by TurtleJuice on 2010-03-30
thats the thing ok i downloaded ubuntu tooday whatever it recomended. i went to use something that required java and it sent me to their site to install it.  I've downloaded both 32 bit linux versions one a rpd or something the other regular but when i follow the install instructions it says file not found

---

### Post by PRC09 on 2010-03-30
The following link has never failed me yet....



[http://sites.google.com/site/easylinuxtipsproject/java#TOC-Removal1](http://sites.google.com/site/easylinuxtipsproject/java#TOC-Removal1)

---

### Post by garvinrick4 on 2010-03-30
It always downloaded when I updated and upgraded after install for me.

Other than that make sure you have all your repositories checked on in software sources
and add partners repository Google it if you do not how.

Then add code: sudo apt-get ubuntu-restricted-extras


That has all the flash, codecs, java, fonts and more. If you already got some of it installed
it will not harm anything just install what is not installed.

---

### Post by TurtleJuice on 2010-03-30
i'm trying to play a game called runescape and i just read the guide you talked about and wanted to try to get the iced tea thing or whatever but when i try to do that it says not available in the current data how do i change this this never appears in the guides.  and its happened a few times tonight.

---

### Post by TurtleJuice on 2010-03-30
ok i followed the guide you sent me too and i got all the way to executing the file and it says command not found but i'm copy and pasting it

---

### Post by PRC09 on 2010-03-31
I just noticed that the version on the Sun Java download page is jre-6u19-i586.bin so you have to change the file name in all the commands where the previous version is listed...Java has been updated since this tutorial was written....

---

### Post by kaizokuroof on 2010-03-31
You could always install it from synaptic packet manager.

---

### Post by PRC09 on 2010-03-31
I think the version in the repos is 1.6.0.15 so if you need the latest version for whatever reason, you will have to update after install anyway...

---

### Post by Anton_E on 2010-04-02
Thanks for the instillation and removal guide but I followed it to a T but can't seem to remove the error-ridden copy of java i have? 

Im running Ubuntu 9.10 i686. but when i try and remove it using synaptic package manager i get this message:

"E: sun-java6-bin: subprocess installed pre-removal script returned error exit status 2"

any ideas? its also affecting all subsequent instillations... for example during an install of 7zip i got this message (which is the normal message now):

(Reading database ... (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 143451 files and directories currently installed.) 
Unpacking p7zip-full (from .../p7zip-full_9.04~dfsg.1-1_i386.deb) ... 
Processing triggers for man-db ... 
Setting up sun-java6-bin (6-15-1) ... 
update-alternatives: error: /var/lib/dpkg/alternatives/javaws corrupt: invalid status 
dpkg: error processing sun-java6-bin (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up p7zip-full (9.04~dfsg.1-1) ... 
Errors were encountered while processing: 
 sun-java6-bin

Any help? and sorry for the question i only just changed from windows to ubuntu... i like it apart from this error lol

thanks in advance

---

