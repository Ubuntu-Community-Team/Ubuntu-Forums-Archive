---
title: "problem creating dvd for Ubuntu 20.04"
date: 2020-05-22
forum: Installation &amp; Upgrades
---

### Post by lyni on 2020-05-22
I've tried to create a dvd so I can install Ubuntu 20.04. I've gone thru 4 dvds and still I can't install from any of them. I checked them and they are okay. I currently have Ubuntu 18.04.
would appreciate some assistance.
thanks
lyn

---

### Post by daniewicz on 2020-05-22
What program are using to create the DVD?

---

### Post by lyni on 2020-05-22
brasero which is on the system and then I burn the dvd and it all looks okay until I try to install. each time I restart the computer it just goes straight to the desktop. it totally ignores the dvd.

---

### Post by mörgæs on 2020-05-23
Have you checked the boot order in BIOS/UEFI?

---

### Post by ajgreeny on 2020-05-23
Did you burn the .iso file as an image rather than simply copy it to the DVD?
Does the DVD contain just the one file, the iso you burned, or does it contain several folders and files which is what you need for it to be bootable?

---

### Post by lyni on 2020-05-23
thanks morgaes I checked the BIOS and it appears to be alright. 
thanks ajgreeny - there are 9 folders burned onto the DVDs.  
I did things the same way as I've always done it. I change over to the LTS every 2 years and its always worked. I don't know why its not working this time.
lyn

---

### Post by ajgreeny on 2020-05-24
I haven't  used brasero for many years but I seem to remember it having problems in the past and many users replaced it with xfburn very successfully.

Perhaps this is worth trying.

---

### Post by jp41 on 2020-05-24
just yesterday i burned an iso image on a dvd and installed 20.04 with no hiccups
i used xfburn.
make sure in BIOS 1st boot is dvd drive.

---

### Post by lyni on 2020-06-01
thank you for all your replies. I may need to try xfburn.
lyn

---

