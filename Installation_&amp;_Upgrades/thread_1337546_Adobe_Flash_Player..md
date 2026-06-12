---
title: "Adobe Flash Player."
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by Zerorebels on 2009-11-25
Hi, first let me just say i am new to the Linux world. and that i have 9.10 karmic koala. when ever i try to install Adobe Flash Player, i get an error stating in the status box of the package installer Error: Wrong Architecture 'i386' when i try to install it. anyway to fix it? 


Thank you for your time,
ZeroRebels.

[Edit]: quick edit. was using Firefox i am now using Opera because i thought firefox was the problem. seems its not. will it still work even if im on opera?

---

### Post by wilee-nilee on 2009-11-25
Have you loaded medibuntu and key
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by JBAlaska on 2009-11-25
Looks like your trying to install the x86_64(64bit) flash on a x86 (32bit) Ubuntu

---

### Post by Zerorebels on 2009-11-25
i downloaded the 64bit Ubuntu amd64 im pretty sure thats the 64bit one. so i dont know why im getting the error. as for medibuntu will be looking at that see if it fixes error.

---

### Post by audiomick on 2009-11-25
> **JBAlaska said:**
> Looks like your trying to install the x86_64(64bit) flash on a x86 (32bit) Ubuntu

or the other way around?

Anyway, go and look at this. You are interested in the Ubuntu-restricted-extras stuff

[https://help.ubuntu.com/9.10/internet/C/web-browsing.html](https://help.ubuntu.com/9.10/internet/C/web-browsing.html)

---

### Post by Zerorebels on 2009-11-25
> **audiomick said:**
> or the other way around?

Anyway, go and look at this. You are interested in the Ubuntu-restricted-extras stuff

[https://help.ubuntu.com/9.10/internet/C/web-browsing.html](https://help.ubuntu.com/9.10/internet/C/web-browsing.html)

will install the extras and see what happens thanks for all the help guys ^^.

---

### Post by Zerorebels on 2009-11-25
> **audiomick said:**
> or the other way around?

Anyway, go and look at this. You are interested in the Ubuntu-restricted-extras stuff

[https://help.ubuntu.com/9.10/internet/C/web-browsing.html](https://help.ubuntu.com/9.10/internet/C/web-browsing.html)

i cant seem to make the extras open/install using firefox(reinstalled it). i get a box prompting me on what application i want to use/associate the file with but i cant find the firefox.exe/tar.gz/.deb or anything. any help?

---

### Post by JBAlaska on 2009-11-25
Just type this in a terminal to install:
```
sudo apt-get install ubuntu-restricted-extras
```

Have FF closed when you do this.

---

### Post by wilee-nilee on 2009-11-25
Go to synaptic for the restricted extras it is a stock package you don't install it through the browser the link is helpful to a extent but confusing if you don't know the native package is on board. You may have to also enable the extra repositories in software sources to have access to the extras.

---

### Post by Zerorebels on 2009-11-25
> **JBAlaska said:**
> Just type this in a terminal to install:
```
sudo apt-get install ubuntu-restricted-extras
```Have FF closed when you do this.

~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ubuntu-restricted-extras is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ubuntu-restricted-extras has no installation candidate
i get this error. ](*,)

---

### Post by JBAlaska on 2009-11-25
Go to System, Administration, Software sources and make sure the (restricted) and (multiverse) sources are checked. Close software sources.

Open a terminal and do:
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

That should do it.

---

### Post by Zerorebels on 2009-11-26
where exactly is the software sources? :roll::roll: (hears face palms). ?

Edit: haha i heard your post incorrectly i thought you wanted me to find it and didn't realize you gave me the path to it -face palm- my bad. tired been trying to fix this and the sound all day.

Edit: another quick edit. i am still using Vista(since this is a brand new pc it came with it) for now till i get everything working should i leave vista? or uninstall completely? i do play games which is why i am wondering if i should even uninstall vista seeing as a lot of games wont be compatible with Ubuntu. the Hard drive is a 320GB had drive. around 60 of it used already by vista so i have around 245GB. would 100GB be good enough? do i need more? also about the sound. big issue there seeing as how i listen to the radio all day and i need to be able to hear it. any ideas on that? sorry for all the questions need to know ^^. also would Aol's radio pop out radio thing work on linux ?

also  JBAlaska thanks for the help will try to see if it works tomorrow morning and will post results for those who are having same problems to help them if it works ^^.

---

### Post by Zerorebels on 2009-11-26
Well JBAlaska it worked i can now see flash animations and youtube videos. now i just cant hear em :roll::roll::roll::roll::roll::roll::roll:

---

