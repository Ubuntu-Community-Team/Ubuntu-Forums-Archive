---
title: "Skype no longer works ?"
date: 2014-08-13
forum: Installation &amp; Upgrades
---

### Post by Madman1978 on 2014-08-13
I see other people having this issue 
and resolve as of yet?

---

### Post by ElChapulin on 2014-08-14
Still unresolved for me, tried the tips given by other in the forums. Nothing works.
I suspect in my case related to my old PC...somewhere I read something about skype now
needing SSE2 (my PC can only SSE).
Does your equipment also happen to be a bit old?

---

### Post by kc1di on 2014-08-14
you may be able to install an older version of Skype if your equipment is not able to use the newer version.
[here is a thread]("http://community.skype.com/t5/Linux-archive/Where-can-I-download-old-version-of-skype-for-Linux/td-p/913586") from the skype forum on where to find them.  I've not tried this so can't vouch that it works , but worth a try.
good Luck. and Welcome to Ubuntu :)

---

### Post by Slithy2003 on 2014-08-14
Have you tried using the sound check in Skype? Also, check your mike is selected in System settings.

---

### Post by ElChapulin on 2014-08-14
Don't want to hijack the thread, but in my case -and I think also in Madman's- skype does not even start, so no way to check sound.
Regarding using an older skype, skype will not let you login if you are using anything older than 4.3...my 4.2 was working perfectly.

---

### Post by sudodus on 2014-08-15
In order to help a local friend, I tried Skype with 12.04 as well as 14.04 yesterday (Aug 14). Both worked for me. The problem for my friend was that he had not updated/dist-upgraded the system for some months. So after the following commands Skype started working for him too.

```
sudo apt-get update
sudo apt-get dist-upgrade
```

-o-

*Edit*: We use Skype from the repos: Enable the 'Canonical Partners' repo and install with

```
sudo apt-get install skype
```

or use ***Synaptic*** or the ***Ubuntu Software Center***

I don't know if there are problems with Skype if installed from a downloaded deb package from Skype's web page.

---

### Post by Andrew_Davis on 2014-08-15
My issue with Skype is 4.2 can't seem to connect to their servers anymore. My account does exsist with them still, but when I download the new update, it works till I quit the program, then it reverts back to 4.2. I have deleted all of the hidden files so i couldn't do it again. I'm completely puzzled now do to this issue.

---

### Post by Ferdinand_Van_Wich on 2014-08-22
Microsoft is now owner of Skype
I have Skype on a desk top PC using Win 7 but my two older PC's still using Win XP3 no longer can access my Skype account
I wonder if it is Microsoft pushing its users to upgrade to Win 7 or 8  ...and preventing Ubuntu users to use it

---

### Post by mastablasta on 2014-08-23
i can use skype just fine on WinXP SP3. all i had to do was update the skype. it seems latest version is required for it to work. same goes with Linux. update and it works.

---

