---
title: "Help/Thoughts/Comments on Copying Installers to another computer"
date: 2011-08-28
forum: Installation &amp; Upgrades
---

### Post by Xmetalfanx on 2011-08-28
Hello 
  I am going to post this, and then double check I did not overlook an obvious answer somewhere else and if it has been answered, please just link me in the "right direction" and I will read up on it. 

  I have two laptops and one has Ubuntu 11.04 (just upgraded from 9.04 ... I knew I didn't want to upgrade with every version ... mainly due to the fact I am on dialup at home, but have access to a high speed WIFI Point ... it takes a little while, but I can do it.  The Point is my old "work-horse" laptop is up to date I think (not only with Ubunutu 11.04, but all the software I install).  I KNOW and have already backed up "/var/apt/cache" (I am typing this quick, so i may have the directory wrong) DEBs and a few others I have installed from different PPAs.  
  
  What I want to do is to just copy the files over to the other directory from my old laptop to my new laptop (same directory, different computer, running v11.04) and have Synaptec install all needed dependencies, ...etc etc. 
  
  What is happening (as I said I am on dialup and THINK when i tried this last night, that the repository "info"/"database may not have downloaded correctly/completely ... I WILL TRY THAT FIRST, as it may be a simple fix) 
  
  What is it doing now, hence me asking the question?  Almost any packages I go to install it says that the dependencies (certain ones) are "not installable" and when searching for a few of them in the package manager, they are not listed (WHICH LEADS ME TO THINK its the rep "Database" being incomplete)... others like Thunderbird that I just installed 2 days ago on the old laptop now say its a different version of 3.x which means I need to download alot of the packages I have (in DEB form from old laptop) all over again with a slightly newer version.  I plan on bringing my new (the one with the issues) laptop to the wifi point next week if I cant figure out how to do this (the simple way) ... but I was trying to avoid that, since "I have everything I needed" already.  
  
  I did what I describe with 9.04 and other than a @300kb lib file or something, I can not recall now, it worked without any issue.  
  
  I thought a few years back (at the time, not a PC, or even a Linux newb, but a Ubuntu newb) that "dpkg -i *.deb" in the folder that had all my DEBs downloaded from another PC (same Ubuntu version) would do what I want, but what I didn't account for is that A) though all dep's WOULD be installed at the time they were all installed ....any package trying to be installed ("in order") that had missing dep's wouldn't installed ... that idea of mine backfired and I do remember (still having the DEBs on a different location) that I just reinstalled Ubuntu 9.04
  
  -----------------
  A main question I have (If this wouldn't goof anything up) is where does Synaptec store the "database info" ... I would wonder IF I could in theroy copy not only the DEBS over (which I have done) but the "database" file too.  Of course after copying and pasting the DB file from one PC to another, I would hit "refresh" to get any NEW updates, but like the concept with the DEBs .. Synaptec would say "hey ... I have to download tha.... oh ... its already there.. never-mind" so that would save me like 70+ Minutes of updating the "Database" (as I call it) for DEBS that are already there.  SO I could (not that I ever had to reinstall 9.04) install on another PC and not have top worry able HAVING to get online.
  
  Thank you all in advanced for your help and advice

---

### Post by Xmetalfanx on 2011-08-28
Looking at [http://wiki.debian.org/AptMedium](http://wiki.debian.org/AptMedium) now ... saw another page with some scripting I have to do and not sure if I want to go that route ... I know I can do it. .. I just think it would end up being easier bring new laptop to wifi spot, but if I feel like it later, I could give it a shot

---

