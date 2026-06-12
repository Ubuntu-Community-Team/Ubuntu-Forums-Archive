---
title: "install hangs at localechooser with 64MB RAM"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by red_fox on 2008-04-26
Hardware: Laptop Dell Inspiron 3500, PIII 400MHz, 64MB RAM, 5GB HDD, Dual boot with Win98SE
Install Disk: xubuntu 8.04 alternate install CD

Problem: Install hangs at "75% Storing Language"
VC4 shows 

l[FONT="Courier New"]ocalechooser: Generating locales 
localechooser: en_US.UTF-8[/FONT]  

I know this laptop may perform poorly after install with 64MB RAM, but I'd like to see whether it's acceptable or not. 

The install guidance says 
"The Alternate Install CD only requires you to have 64 MB RAM.". 

Any ideas ? I tried killing some of the locale related scripts from VC2, but no joy. Thanks in advance.

---

### Post by red_fox on 2008-05-01
In case anyone stumbles across this, I completed the install by 
- installing fluxbuntu 7.10rc 
- installing xubuntu 7.10 with 

sudo apt-get install xubuntu-desktop 


I would then have upgraded to 8.04 using the software update tool, but didn't bother because, as expected, the performance in 64MB was nothing to write home about. Startup time was very slow and Opera performance just about bearable for non-flash browsing. Flubox with rox offers a moderate improvement but was all a bit too bare boned for my taste.

Might try with 256MB RAM at some point.

---

