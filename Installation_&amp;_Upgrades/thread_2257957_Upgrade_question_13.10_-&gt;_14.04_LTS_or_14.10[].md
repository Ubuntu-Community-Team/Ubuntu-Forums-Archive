---
title: "Upgrade question 13.10 -&gt; 14.04 LTS or 14.10[?]"
date: 2014-12-23
forum: Installation &amp; Upgrades
---

### Post by rreyes3713 on 2014-12-23
I had Ubuntu 12.10 and has been upgraded to 13.10.

Now I want to upgrade to 14.04 LTS (or 14.10) but I get the following: 
[IMG]http://rolandr.x10host.com/misc/UpgradeErrorMsg_14_10.png[/IMG].


Note my laptop is ASUS K55A if that's any help 'cause it was troublesome to install Ubuntu 12.10 dual boot with Windows 8. But you guys lead me through the installation process! Thanks!

Just curious,could I download 14.04 LTS, burn a DVD and upgrade from the DVD? Or will I run into the same problem? Sorry if that's a lame question.

What's the difference between 14.04 LTS and 14.10? Which version should I upgrade to?

Thanks in advance.

---

### Post by grahammechanical on 2014-12-23
Ubuntu 13.01 has reached end of life and its repositories have been closed or to put it more accurately moved. It should be possible to upgrade from a 14.04 DVD but you may hit the same problem unless you follow the instructions in this wiki page. Then you should be able to upgrade either over the Internet or from the DVD.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

By the way, my advice would be to stick with 14.04 once you get to it as 14.10 only has 9 months support. Unless we are willing to get into the habit of upgrading every 6 - 9 months then it is best if we get onto  the latest LTS release (14.04) and only upgrade to the next LTS every two or three years or so.

Regards.

---

### Post by rreyes3713 on 2014-12-23
Thanks, 

Do I upgrade on the desktop ( and DVD loaded) or do I upgrade from the BIOs, (hit alt-F2, I think for ASUS, select booting order, disc drive first)?

---

### Post by kansasnoob on 2014-12-23
The live DVD/USB does offer an upgrade path but it's known to also eat Windows in a dual boot:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

Now, that problem is supposed to be fixed in 14.10 but I've not verified that myself.

---

### Post by rreyes3713 on 2014-12-24
Thanks for the heads up ...

( fundamental question )
So what do I type in the Terminal Display to upgrade to 14.04 LTS?

The above error was when Ubuntu asks me if I want upgrade from 13.10 (my current) to 14.04 LTS. Seems like if I upgrade from the terminal perhaps that maybe a better way.

I'm persistent.

---

### Post by mörgæs on 2014-12-25
Have you considered 14.04.1 in a fresh install? Just choose 'something else' during install to be sure that the Windows partition is not lost.

---

### Post by rreyes3713 on 2014-12-25
You do a "fresh" installation leaving Window partition intact? Sorry if I'm naive. It has been a while since my last installation of Ubuntu. I just may do that once I backup my files on to external hard drive (or put them in the Window partition). 

Let read up on that. I'm prefer to read up on installation than jumping head first - lol 

Thanks.

---

