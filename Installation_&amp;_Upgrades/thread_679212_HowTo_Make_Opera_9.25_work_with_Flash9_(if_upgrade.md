---
title: "HowTo: Make Opera 9.25 work with Flash9 (if upgraded to r115)"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by oleoleole on 2008-01-26
This is not a howto to make newest stable Opera (today: 9.26) work with the newest stable Flash (today: v.9 r115). But at least make Opera 9.26 work with Flash 9 at all.

You can't use old .deb-files (since it's downloading the "current" from Adobe), and so you can't downgrade to flashplugin-version to work with Opera.

But it's anyway a solution, and I am one of those who don't want to run Opera 9.50b yet.

Anyway, the procedure is quite simple:

- start a terminal and go to or make a directory, name it to whatever you want and enter it. then do/write this:

Make sure you have "wget" and "alien" installed, just type "alien" or "wget" to find out, if not, install it using apt:
```
sudo aptitude install wget alien
```

Download Flash plugin v9 r48:
```
wget http://fpdownload.macromedia.com/get/flashplayer/current/flash-plugin-9.0.48.0-release.i386.rpm
```
(The .rpm-file includes the entire r48-module.)

Then convert the RPM to DEB:
```
sudo alien flash-plugin-9.0.48.0-release.i386.rpm
```
(Ignore the warning about --script)

Close your web browser(s).

Remove other flash versions:
```
sudo aptitude remove flashplugin-nonfree
sudo rm /usr/lib/flash-plugin/libflashplayer.so
```

Check if you have the plugin installed other places:
```
sudo updatedb
locate libflashplayer.so
```
(Delete any results you get (sudo rm /path/to/libflashplayer.so), if none, go to next step)

Install Flash plugin:
```
sudo dpkg -i flash-plugin_9.0.48.0-1_i386.deb
```

Now you can start your web browser(s). Opera should at least now be working with flashplugin.

NB! Upgrading flashplugin will destroy again.

---

### Post by MRSherman1 on 2008-02-07
After hours of trying to restore flash in Opera 9.25 and Ubuntu 7.10 this did the trick. Thank you.

---

### Post by taurusx5 on 2008-02-09
THANK YOU SO MUCH!!! Incredibly, I had been trying to find a viable solution to getting flash and opera to cooperate with each other since installing ubuntu a month ago. It was an uphill battle to say the least. Opera is the ONLY browser I use and respect so I didn't want to use firefox or other idiotic alternatives. Thankfully, I found the answer to my problem in this thread. Thanks a million !!!!

---

### Post by Ryzol on 2008-02-09
Thanks a lot, this was very helpful.

---

### Post by HoldSteady on 2008-02-11
Thank you so much for the fix.  I guess Adobe is slowly reaching out to the OSS community, but breakages like this make me wonder.  Maybe it is more Opera's fault than Adobe, but the point is I don't care - adding features or upgrading a program is fine, but not when it breaks a function that is sadly so ubiquitous (Flash).

---

### Post by UncleCz on 2008-02-11
Thank you very much, i started to use firefox much more because of the lack of flash in opera under ubuntu.
Thanks to you, i can come back to my favourite browser, which is much faster on my system ...thx :-)

---

### Post by banished_one on 2008-02-13
omg thank you so much

---

### Post by ubuntu-freak on 2008-02-13
Edit: Removed my post as it was incorrect.
 
Nathan

---

### Post by fkamp on 2008-02-24
> **oleoleole said:**
> This is not a howto to make newest stable Opera (today: 9.25) work with the newest stable Flash (today: v.9 r115). But at least make Opera 9.25 work with Flash 9 at all.

You can't use old .deb-files (since it's downloading the "current" from Adobe), and so you can't downgrade to flashplugin-version to work with Opera.

But it's anyway a solution, and I am one of those who don't want to run Opera 9.50b yet.

Anyway, the procedure is quite simple:

Thank you very much. Until I found this solution, I couldn't figure out why Opera stable wasn't utilizing the libflashplayer.so that I had installed in /usr/lib/opera/plugins. (Because it was the newest version 115). 

Thank you:)

---

### Post by oleoleole on 2008-02-24
This works also for Opera 9.26 ;]

---

### Post by bidjix on 2008-02-24
This doesn't work for me.

Doesn't work for 9.25, doesn't work for 9.26. I do the whole process word to word, still nothing.

9.50 crashes constantly. I don't like it one bit.

I'm extremely jealous.

---

### Post by oleoleole on 2008-02-25
> **bidjix said:**
> This doesn't work for me.

Doesn't work for 9.25, doesn't work for 9.26. I do the whole process word to word, still nothing.

9.50 crashes constantly. I don't like it one bit.

I'm extremely jealous.

Have you actually checked if Opera are even trying to use the plugin? Ev. check for path(s) to plugins.

Anyway, this should be added if not: /usr/lib/flash-plugin/

---

### Post by saperduper on 2008-04-01
thanks ;)
this howto also worked for Opera 9.26

---

### Post by sh1ma_tetsu0 on 2008-04-02
Didn't work for me too. I'm using Opera 9.26, also tried 9.50b - I can see flash movies' placeholders, but they are filled with white, when I click on them with right mouse button, I can see "About Abobe Flash Player 9" and "Movie not loaded". 
Checked everything, same result == no flash in Opera.

---

### Post by ciungan_marius on 2008-04-16
this solution also works for opera 9.27 and kubuntu 8.04 

thanks a lot !!!!!

---

### Post by spacejaysis on 2008-05-26
Thankyou!!! Very useful, now I can stop using firefox altogether!

---

### Post by cadcrazy on 2008-06-15
Will this method work with opera 9.5

---

### Post by oleoleole on 2008-06-15
> **cadcrazy said:**
> Will this method work with opera 9.5

Opera 9.5 works with Flash 9 ;D

---

### Post by taurusx5 on 2008-07-17
6 months ago I had installed Opera to work with Flash 9 through this method. Since then, I have upgraded to the most recent version of Opera 9.51, Build 2061. I'm able to play Youtube on it just fine. But, after several minutes of playing video clips, the clips become choppy and Opera freezes. What should I do?

Also, can I upgrade Flash to the most recent version? If so, then how?

---

### Post by oleoleole on 2008-07-18
> **taurusx5 said:**
> 6 months ago I had installed Opera to work with Flash 9 through this method. Since then, I have upgraded to the most recent version of Opera 9.51, Build 2061. I'm able to play Youtube on it just fine. But, after several minutes of playing video clips, the clips become choppy and Opera freezes. What should I do?

Also, can I upgrade Flash to the most recent version? If so, then how?

When using Opera 9.5x, you can freely use the normal flashplugin-nonfree from the lists, no need for "rebuilding" anything. But the problem you have, do lots of other people experience and I also. It's annoying when it freezes, but after some seconds its back in business. So far I haven't found anything that may help Opera+Flash, where the bug is I dunno, but Opera without Flash works perfectly fine. But the co-operation between Opera and Flash is still pretty poor.

---

### Post by johnnyxxxcakes on 2008-07-19
Thanks so much! After about an hour Google searching how to get Flash Player to work with Opera, I came accross this thread. It worked with the latest version of Opera (9.51).

Got it up and working within minutes. :)

---

### Post by taurusx5 on 2008-07-19
> **oleoleole said:**
> When using Opera 9.5x, you can freely use the normal flashplugin-nonfree from the lists, no need for "rebuilding" anything. But the problem you have, do lots of other people experience and I also. It's annoying when it freezes, but after some seconds its back in business. So far I haven't found anything that may help Opera+Flash, where the bug is I dunno, but Opera without Flash works perfectly fine. But the co-operation between Opera and Flash is still pretty poor.

oleoleole, thank you so much for your reply. At this time, I must ask you this question because I'm such a newbie. What do mean by I can use the flashplugin-non-free from the lists? What lists? Why is it "non-free"? Can I download the newest flash from the Adobe website?

Please, be a bit patient with me with these questions I'm asking you since I'm still a newbie and getting around to understaning ubuntu better. Thanks, man!

---

### Post by oleoleole on 2008-07-19
> **taurusx5 said:**
> oleoleole, thank you so much for your reply. At this time, I must ask you this question because I'm such a newbie. What do mean by I can use the flashplugin-non-free from the lists? What lists? Why is it "non-free"? Can I download the newest flash from the Adobe website?

Please, be a bit patient with me with these questions I'm asking you since I'm still a newbie and getting around to understaning ubuntu better. Thanks, man!

Hi! There's no need for downloading flash directly from Adobe, use the repositories (APT).
```
sudo aptitude install flashplugin-nonfree
``` and you will have the latest stable from Adobe ("supported" by *ubuntu). You may have to edit /etc/apt/sources.list since Adobe Flash is non-free.

"non-free" means it's not open source and free as in freedom to use it, even if the plugin itself is for free (no cost). You will find more information about this at tons of places at the internet, check out google:P

---

