---
title: "64 bit upgrade to 12.04 froze when net dropped"
date: 2012-05-23
forum: Installation &amp; Upgrades
---

### Post by o1hattrick on 2012-05-23
I was progressing fine through the upgrade.
it made it to Installing the upgrades.
I opened the terminal and ok'd the sevral prompts.
It was trying to download the mscorefonts-installer from sorceforge when my internet dropped for a while. This froze the upgrade. 
I am still sitting at  that point with the terminal open.
Is there any way i can continue or restart the upgrade?
It has sat here for a full day cause i had to leave a while so i know it won't restart itself.
thanks for any help you can give.

---

### Post by zvacet on 2012-05-23
Try with 

```
sudo apt-get install ttf-mscorefonts-installer
```

If I remember correctly you have to agree with the license.

---

### Post by o1hattrick on 2012-05-23
It woundn't run from the installer terminal so i opened up terminal and tried and got this result.

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

prolly cause the upgrade has it locked?

---

### Post by jadtech on 2012-05-23
> **o1hattrick said:**
> It woundn't run from the installer terminal so i opened up terminal and tried and got this result.

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

prolly cause the upgrade has it locked?
try closing the install window :) it will continue to run untill you close  that terminal.. 

then try this in a new terminal if you net connection is again working 

```


sudo apt-get update
 sudo apt-get upgrade -f 


```
 upgrade -f will will build dependancy list and  finish installing any lost package  the install should continue from there

if not 

```


sudo apt-get install -f 

configure -a

```
 install -f again builds a priority or dependency list so packages open in order they are  needed  there are some package that are  required to open to be able toi install another 
 
sometimes  usually works sometime not

---

### Post by o1hattrick on 2012-05-23
thanks for your help!
I ran the first in terminal and it ran a while and then gave.

Get:74 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en [1,619 B]
Fetched 19.3 MB in 4min 26s (72.5 kB/s)                                        
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


like before.
I haven't tried the other yet beacuse i figure this might be a seperate issue.

thanks again of any help you can give.

---

### Post by jadtech on 2012-05-23
well see if you can get the upgrade -f to go that may well work  really want to avoid a reboot at this point if  you can .. 

worse comes to worse try a log out and log back in  if the error keeps persisting how ever I can not promise you will be able to get back in the desk top once you log out even if all goes bad and you are forced to reboot if you cant get to a terminal to use these comands try recovery mode it should turn things back or at least far enough back to hopefully get you booted up  to get in terminal.. 

beyond  that you  might want to find another computer and burn a install disk or make a boolable usb if you dont have one and start rescuing files and do a clean install ..

---

### Post by o1hattrick on 2012-05-23
I tried the 
sudo apt-get upgrade -f
It gave same locked error.
I am already dl'ing a new iso on other computer so will prolly go for the clean install after i backup everything that i dont have backed up.

Is there any way to completely backup firefox? 
As in open tabs and settings etc?
I have tried febe but it always crashes and runs for days.

---

### Post by zvacet on 2012-05-23
Go to your home folder and that press ctrl+h and you will see hidden folders.One of them is mozilla and in that folder should be your settings.

---

### Post by o1hattrick on 2012-05-23
Thanks! I will have to do that from the live cd i think because i can't seem to open any folders now.
I will try a re- boot to see if anything comes up.
If not i will backup mozilla from live cd if i can.

---

