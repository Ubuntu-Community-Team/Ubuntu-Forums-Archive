---
title: "Lamp"
date: 2005-09-07
forum: Installation &amp; Upgrades
---

### Post by jabb0 on 2005-09-07
I have setup Ubuntu on a test machine, just to make sure everything is fine before i move my real computer to linux.
 
I have been running WAMP on windows for ages now, and i have to say getting it to work on Ubunto was soooo easy, 2/3 lines into the CLI and hey presto, no crap about setting it up as a service, or Norton blocking access to the server, just great.
 
Except that i cannot modify any files in WWW folder, the ROOT is the owner of this folder, so i cannot touch it.
 
1) Is there a good reason for this?
2) Can it be changed so i can write to the folder?
3) Is it safe to change this?
4) Is there another method i should use?

---

### Post by KingBahamut on 2005-09-07
man chmod 

and 

man chown 

[http://httpd.apache.org/docs/1.3/misc/security_tips.html](http://httpd.apache.org/docs/1.3/misc/security_tips.html)
[http://httpd.apache.org/docs/2.0/misc/security_tips.html](http://httpd.apache.org/docs/2.0/misc/security_tips.html)

---

### Post by madjo on 2005-09-07
I think 
```
sudo chmod 777 /WWW/* -R
```
might help you (or perhaps 755) (where /WWW/ is your www-root folder)

and indeed what KingBahamut says :)

---

### Post by jabb0 on 2005-09-07
Are you saying that i should just chmod the dir so everyone can write to it?
 
If so happy days :razz:

---

### Post by madjo on 2005-09-07
[QUOTE=jabb0]Are you saying that i should just chmod the dir so everyone can write to it?
 
If so happy days :razz:[/QUOTE]
 it was just a suggestion... :) I think KingBahamuts info is more up to date, and more safe to do :)

---

### Post by jabb0 on 2005-09-07
Cool,
 
ur chmod syntax didnt work dude, but it set me on the right path.
 
I have chmod the folder now and i can write to it and stuff, just need to get php to work, but thats another story.
 
Does anyone have a good reason for me to go and do this the hard way?
I mean is there any security (or other) issues with chmodding my www dir to 777?

---

### Post by KingBahamut on 2005-09-07
755 is probably the safest. 

I have some good php references as well if you want those.

---

### Post by jabb0 on 2005-09-07
Surely.
 
My gran used to always say "never look a gift horse in the mouth" - and i never have.
 
Cheers man.

---

### Post by KingBahamut on 2005-09-07
[www.phpfreaks.com](www.phpfreaks.com)
[www.onlamp.com](www.onlamp.com)


Both of these I find indisposable at times.

---

### Post by jabb0 on 2005-09-07
nice one, cheers.

---

