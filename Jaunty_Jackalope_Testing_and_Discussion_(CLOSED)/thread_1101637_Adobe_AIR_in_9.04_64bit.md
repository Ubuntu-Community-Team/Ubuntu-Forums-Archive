---
title: "Adobe AIR in 9.04 64bit?"
date: 2009-03-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by aaronb on 2009-03-20
Is Adobe AIR available in 9.04 64bit in the same way that Adobe Flash is in 9.04?
(Using add/remove programs or Synaptic)

Thanks in advance!

---

### Post by Xehoz on 2009-03-31
I've [managed]("http://kb.adobe.com/selfservice/viewContent.do?externalId=kb408084") to install and run apps with it. However, the apps aren't able to connect to the internet. So, at least for me, it's a no go. I'll probably just install the 32 bit Jaunty. I pretty much depend on some Air apps.

---

### Post by Philip Farrugia on 2009-04-04
Just want to add I'm also looking to add Adobe Air to 64bit on 9.04beta.
Tried the Adobe site method without any joy on 9.04 Alpha. I want to down load BBC iPlayer programs. " get_iplayer " is good but takes ages using only a command line.


Just installed using instructions on this link ;

[http://www.64bitjungle.com/ubuntu/install-adobe-air-15-and-the-google-analytics-reporting-application-on-ubuntu/](http://www.64bitjungle.com/ubuntu/install-adobe-air-15-and-the-google-analytics-reporting-application-on-ubuntu/)

---

### Post by TyrosCenva on 2009-04-05
Same here, got apps working, but no internet.
Unfortunately no error messages either (other than that the app can't connect).

---

### Post by fridley on 2009-04-09
Same as the rest. Tried both TweetDeck and Seesmic, and neither could get through. Wonder if (like the ctrl+alt+backspace) ubuntu has disabled something important to let adobe air work??

---

### Post by antitezo on 2009-04-10
hi

you need the lib32nss-mdns package... just do

sudo apt-get install lib32nss-mdns 

and it will fix internet for your ia32-libs apps

---

### Post by PuPPeTeeR on 2009-04-11
> **antitezo said:**
> hi

you need the lib32nss-mdns package... just do

sudo apt-get install lib32nss-mdns 

and it will fix internet for your ia32-libs apps


Nice catch :) 
Thanks!

---

### Post by fridley on 2009-04-11
> **antitezo said:**
> hi

you need the lib32nss-mdns package... just do

sudo apt-get install lib32nss-mdns 

and it will fix internet for your ia32-libs apps


Ok, you have officially made my day. Thx for your brilliance.

---

### Post by fridley on 2009-04-11
Thanks to the new found solution, I have decided to make a post of the start to finish steps to install Adobe Air on 9.04 and specifically Tweetdeck. 

[http://bit.ly/3emmc](http://bit.ly/3emmc) 

Please let me know if I have missed anything important.

---

### Post by rathel on 2009-04-20
TweetDeck still doesn't work for me. lol DestroyTwitter is the only Twitter app I found that works.

---

### Post by TyrosCenva on 2009-04-21
Same here. I believe there's a bug registered somewhere about this and I subscribed to that, but no updates yet..

---

### Post by halovivek on 2009-04-21
Thanks for posting i will give a try and get back here.

---

### Post by antitezo on 2009-04-21
For TweetDeck you'll need the following libs

```
libgnome-keyring.so
libgnome-keyring.so.0
libgnome-keyring.so.0.1.1
```

To get those, you'll need the getlibs package located at [http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)

so install it, then just do:

```
sudo getlibs -l libgnome-keyring.so
sudo getlibs -l libgnome-keyring.so.0
sudo getlibs -l libgnome-keyring.so.0.1.1
```

And TweetDeck works for me now :)

If don't work for you, try 

```
/opt/TweetDeck/bin/TweetDeck
``` and maybe it will show some errors or something.

---

