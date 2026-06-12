---
title: "xserver crash after update"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by ajlapp on 2006-08-21
After a fresh install and a complete update my xserver crashed.....:( 

via sp13000
ubuntu 6

---

### Post by dmery on 2006-08-21
Same for me. Someone knows how to fix this mess
Regards,
dmery:frown:

---

### Post by xXx 0wn3d xXx on 2006-08-21
> **dmery said:**
> Same for me. Someone knows how to fix this mess
Regards,
dmery:frown:
Does it say "cannot find screens" if so I have the same problem. The new update is messed up :(

---

### Post by spectrum on 2006-08-21
Same trouble here after fresh install and update... integrated video, so nothing related with drivers.

The log is:

xserver fatal error: No screen found :confused:

---

### Post by rjg1021 on 2006-08-21
Is this issue new to today? I did a clean install of 6.06 LTS this afternoon. I did the server update and when I rebooted I could not get a screen to come up. Is this some kind of driver issue? What are the best threads already dealing with this topic?

---

### Post by dmery on 2006-08-21
> **xXx 0wn3d xXx said:**
> Does it say "cannot find screens" if so I have the same problem. The new update is messed up :(

(EE) No devices detected.
Fatal server error:
no screens found
X10: fatal iO error 104 on X server "0:0"

This report for me when I tried to run a "startx" command

Regards,
dmery

---

### Post by spectrum on 2006-08-21
> **rjg1021 said:**
> Is this issue new to today? I did a clean install of 6.06 LTS this afternoon. I did the server update and when I rebooted I could not get a screen to come up. Is this some kind of driver issue? What are the best threads already dealing with this topic?

For what i´ve seen, is this one... :( 

@dmery: Same thing for me in the advanced xserver log

---

### Post by OrionDX on 2006-08-21
> **xXx 0wn3d xXx said:**
> Does it say "cannot find screens" if so I have the same problem. The new update is messed up :(

Looks like the update deletes the xorg.conf in /etc/X11/ dir Havent tried this yet but if youre a nvidia user you might could try sudo nvidia-glx-config enable to reset the xorg.conf let me know if that works.

---

### Post by spectrum on 2006-08-21
in my case xorg.conf is not deleted, but i suspect that is corrupted.

---

### Post by dmery on 2006-08-21
Solution:
When your Xserver crash and you are at text console type this:
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

When finnish, reboot or just type startx. To reboot type:
sudo shutdown -r now

Now xserver-xorg-core is downgraded to prior working version.

First I thought it was something wrong with XGL/Compiz Quinn's packages. But I upgraded xserver-xorg-core in my laptop that has no compiz installed and Xserver was broken too. So it has to be a problem with dapper packages. Hope Ubuntu boys will fix it soon.

Regards.
Reply With Quote

---

### Post by jimmysz on 2006-08-21
Thanks so much for that fix.
I was nearly in tears trying to tweak xorg.cong

---

### Post by crane on 2006-08-21
No good, still get error.
Do I need to reinstall to fix this!

---

### Post by cmdMatt on 2006-08-21
Worked for me.  This was my first problem with Ubuntu and I really appreciate the quick response.

---

### Post by izahn on 2006-08-22
What a mess, I figured I broke my system installing a few programs from the edgy repos so I did a clean dapper install. Imagine my dismay when the problem was still there! Anyway, I don't know how to fix this problem, except to say DON'T install the xserver update! Open up synaptic, find xserver-xorg-core, then from the Package drop-down menu select "Lock". Of course if your reading this it's probably already too late . . .

[http://izahn.homedns.org](http://izahn.homedns.org)

---

### Post by crane on 2006-08-22
Well, it would appear that I have screwed it all up, BUT!
I fixed it as well. Some how GDM got corrupted and was causing errors. after reinstalling gdm all is well.
Thanks for the tip in fixing Xserver, You guys and girls are great.

---

### Post by cnhzcy14 on 2006-08-22
It is really a worldwide bug! Really a big bug!

---

### Post by beko on 2006-08-22
I just got the same problem now ... this is the first time something like this happend to me after clean install!!!!!!

---

### Post by beko on 2006-08-22
> **dmery said:**
> Solution:
When your Xserver crash and you are at text console type this:
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

When finnish, reboot or just type startx. To reboot type:
sudo shutdown -r now

Now xserver-xorg-core is downgraded to prior working version.

First I thought it was something wrong with XGL/Compiz Quinn's packages. But I upgraded xserver-xorg-core in my laptop that has no compiz installed and Xserver was broken too. So it has to be a problem with dapper packages. Hope Ubuntu boys will fix it soon.

Regards.
Reply With Quote


Worked perfect with me ... many thanks

---

### Post by notoriousdbp on 2006-08-22
Many, many thanks dmery - really thought ubuntu had died there.  I owe you a beer.

---

### Post by theadventuresofanidealist on 2006-08-22
did as you said but now it just stops booting.
what do i do now?

---

### Post by ezkim0x on 2006-08-22
same thing happened to me and I performed a clean install.. this time I locked the "xserver-xorg-core" from package manager before updating.. and it worked.. hopefully they fix it soon though.

---

### Post by XXFCTEXX on 2006-08-22
I didn't get the no screen error, just got the standard xserver crash and  error screen.

I did a fesh install on Sunday, today I get home from work log on, the update manager came up, I let it install some xserver update, rebooted, and it crashed my system. That's messed up.

I love ubuntu, but the xserver is becoming a nightmare, stable my ***. :evil:

---

### Post by XXFCTEXX on 2006-08-22
> **dmery said:**
> Solution:
When your Xserver crash and you are at text console type this:
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

When finnish, reboot or just type startx. To reboot type:
sudo shutdown -r now

Now xserver-xorg-core is downgraded to prior working version.

First I thought it was something wrong with XGL/Compiz Quinn's packages. But I upgraded xserver-xorg-core in my laptop that has no compiz installed and Xserver was broken too. So it has to be a problem with dapper packages. Hope Ubuntu boys will fix it soon.

Regards.
Reply With Quote

You rock. 

Worked perfectly, system fully restored. THANK YOU!!

=D>

---

### Post by smoothridersean on 2006-08-23
Just wanted to chip in that the same thing happened to me.  After downgrading the package my laptop is healthy, happy, and X-y again.  

To whom it may concern or be helpful, I'm on ThinkPad T42 with a Mob Radeon 9600 (I forget its M__ designation).

EDIT: Anyone else who finds themselves in this thread - don't be a dope in your first post (like I did); instead, go [here]("http://www.ubuntuforums.org/showthread.php?t=241254").  You'll see that the issue has been resolved, and that **1.0.2-0ubuntu10.4** fixes the problem.  Hooray for a quick response!

---

### Post by vonlochow on 2006-08-23
> **dmery said:**
> Solution:
When your Xserver crash and you are at text console type this:
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

When finnish, reboot or just type startx. To reboot type:
sudo shutdown -r now

Now xserver-xorg-core is downgraded to prior working version.

First I thought it was something wrong with XGL/Compiz Quinn's packages. But I upgraded xserver-xorg-core in my laptop that has no compiz installed and Xserver was broken too. So it has to be a problem with dapper packages. Hope Ubuntu boys will fix it soon.

Regards.
Reply With Quote

This works perfectly! Big thanks man, almost paniced there for a while.

---

### Post by henz on 2006-08-23
I did a down grading with the apt-get like u mentioned and succes!! tnx dmere

henz

---

### Post by Jakonavitch on 2006-08-28
after the 
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
sudo shutdown -r now

do this:
"sudo dpkg-reconfigure xserver-xorg"

and it finally came back for me

---

### Post by pafortin on 2007-06-24
For me the apt-get told me the package could not be found so I am re-installing dapper and I will do a "locked" upgrade from there..

---

### Post by bobonaut on 2007-11-25
> **dmery said:**
> Solution:
When your Xserver crash and you are at text console type this:
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

When finnish, reboot or just type startx. To reboot type:
sudo shutdown -r now

Now xserver-xorg-core is downgraded to prior working version.

First I thought it was something wrong with XGL/Compiz Quinn's packages. But I upgraded xserver-xorg-core in my laptop that has no compiz installed and Xserver was broken too. So it has to be a problem with dapper packages. Hope Ubuntu boys will fix it soon.

Regards.
Reply With Quote

after i do the sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10 

i get:  version "1:1.0.2-0ubuntu10" for xserver-xorg-core not found someone help plz :D

---

### Post by mali2297 on 2007-11-25
Hi Bobonaut.

The solution given in this thread seems to be outdated. Do you even use Dapper?
I suggest you try
```

sudo dpkg-reconfigure xserver-xorg

```
If that doesn't solve it, start a new thread here and describe your problem in detail.

---

