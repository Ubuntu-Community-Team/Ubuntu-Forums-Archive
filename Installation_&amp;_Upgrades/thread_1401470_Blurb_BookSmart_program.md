---
title: "Blurb BookSmart program"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by kiomkids on 2010-02-08
hi, I successfully installed the win software, the BookSmart from Blurb using WINE...
but when I try to run the program, I encounter a problem as in the attached picture...

it's telling me that I do not have enough space to save the program output...
and it wants me to free some spaces up before running the program again!

I hope there's a way to tweak the space thing!

Please give some advices, thanks!!!

---

### Post by CrackersKeenan76 on 2010-04-10
I had the same problem - configure wine to be like Windows 98 and it works.  I don't know why.

BTW I had 20gig spare on my HDD, and the program only requires 1.  Not sure what happened there...

---

### Post by Achtel on 2010-06-01
Can you tell me how you got Booksmart working under Wine? I've downloaded the latest version (2.6.1) but when I try to execute it, I get an error message saying that the file isn't marked as an executable?

I've also tried to download the Mac version and tweak it according to this guideline here: [https://help.ubuntu.com/community/BookSmart](https://help.ubuntu.com/community/BookSmart) But when I click on the menu entry that's been created, it briefly thinks about something and then nothing happens.

Any ideas? I really like BookSmart and would like to use it...

---

### Post by Achtel on 2010-06-02
So I've followed a guideline on how to install Booksmart, which I found here: [http://www.binaryelysium.com/blog/2009/10/23/running-blurb-booksmart-in-linux-without-wine/](http://www.binaryelysium.com/blog/2009/10/23/running-blurb-booksmart-in-linux-without-wine/)

When I execute the script to run BookSmart I get the following Java error

> 
cd: 4: can't cd to /home/kirsten/Applications/booksmart
Exception in thread "main" java.lang.NoClassDefFoundError: com/blurb/booksmart/application/Booksmart
Caused by: java.lang.ClassNotFoundException: com.blurb.booksmart.application.BookSmart
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)  
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:334)
Could not find the main class: com.blurb.booksmart.application.BookSmart. Program will exit.


Does anybody know how to fix this?

---

### Post by simonrobidas on 2010-06-25
Achtel,

I don't know how to fix the problem you describe, but I successfully installed BookSmart 2.8 on Ubuntu 10.04 last night using the instructions found here: [https://help.ubuntu.com/community/BookSmart]("https://help.ubuntu.com/community/BookSmart")

I had to install sunjava 1.6 instead of using the openjdk.

One glitch: Booksmart can't pull pictures from the hard drive, but it can download them fine from SmugMug. Bit annoying, but it was enough to get me going.

---

