---
title: "edgy upgrade just completely hosed my system"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by aimless on 2006-10-28
My system is completely hosed after trying to upgrade to Edgy .Can't even boot into system. All I get is a blank black screen with a blinking cursor at the upper left hand corner.Cursor just keeps on blinking and there is no response when pressing any keyboard key.
   In the middle of the install, after all the files had been downloaded, a screen popped up saying it couldn't install my myth tv database. When I tried to enlarge the window to better read the message, the window disappeared and the installer completely died with no traces of any windows related to it.Tried to restart update-manager, entered my password and it just kept telling me I was entering the wrong password.I entered it several time.I know I couldn't have entered it wrong every time.
    What a mess!!! When I upgraded to Dapper,it broke my mythTV installation and my LIRC module.It took me quite a long time to figure out what was wrong and correct it;and now this!!!](*,) ](*,) ](*,) ](*,) ](*,) 
     I really think there's work to be done on the upgrade process in Ubuntu.In every other way I think Ubuntu is about the the best distro out there, but this upgrade HELL is really annoying and frustrating.As I have heard a lot of other similar horror stories, I think this  will turn a lot of people off to Ubuntu no matter how good of a distro it is otherwise.

---

### Post by aimless on 2006-10-28
View Poll Results: What level of success did you have when upgrading to Edgy?
The upgrade went perfectly! 		70 	18.72%
I had a few problems. 		119 	31.82%
I encountered serious problems. (for example, can't connect to Internet) 		83 	22.19%
Things went really badly and I can't [ log in, boot, etc ]! 		102 	27.27%

I think these poll results demonstrate the extent of the problem.The installation went perfectly for only about %19 of the   upgrades.%50 had serious to "really bad" problems.%80 had anywhere from some problems to "really bad" problems.
  I'm sure no one's claiming this is a scientific poll but I think it indicates a problem

---

### Post by aimless on 2006-10-28
Doesn't look like this thread is generating too much interest, but just in case someone stumbles across it, I got everything working by "busting" into my system with a knoppix live disk and running the command **gksu apt-get -f install** which I got from another thread on these forums.This restarted my install until it completed and everything worked fine after that. Hope this helps some others and they don't have to bang their head like I had to.

---

### Post by nbx909 on 2006-10-28
try 
```
Ctrl + alt + f1
```
You should then get a terminal, log in and then do
```
sudo apt-get install xserver-xorg
```
if it says it's already installed then this won't help but if it installs do
```
sudo gdm
```
or 
```
starx
```
or 
```
sudo reboot
```
also if it says X packages will not be installed force the install by doing ```
sudo apt-get install name of package
``` 
one by one.
I had to do this on an upgrade on my server. I'm too afraid that i won't be as lucky on this machine.

---

