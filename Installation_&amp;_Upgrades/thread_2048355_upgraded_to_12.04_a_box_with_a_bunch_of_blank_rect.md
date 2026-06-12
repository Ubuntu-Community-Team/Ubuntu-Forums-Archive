---
title: "upgraded to 12.04 a box with a bunch of blank rectangles..."
date: 2012-08-26
forum: Installation &amp; Upgrades
---

### Post by ilovethislinuxstuff on 2012-08-26
showed up at the end of the upgrade. i just x'd out of. but now i'm not sure if every part of my upgrade was successful. how do i re-upgrade?

---

### Post by deadflowr on 2012-08-26
What happens when you restart?
Do you login as normal, or are there problems?

---

### Post by ilovethislinuxstuff on 2012-08-26
> **deadflowr said:**
> What happens when you restart?
Do you login as normal, or are there problems?

i'm able to login with no problems that i can see. however, at the point that the box with all the retangles appeared and I x'd out of it, the next box asked me if i wanted to delete some packages (maybe older packages, i don't know) and I said no to deleting them. now when I go into the software center and look at installed "unknown" packages, there are a ton of them. that's why i'm thinking maybe the install isn't perfect. i don't know...

---

### Post by Bucky Ball on 2012-08-26
*Moved to **Installation & Upgrades**.*

---

### Post by Tom Collier on 2012-08-26
Just upgraded last night from 10.04 LTS to 12.04.1 LTS on an eeePC H1000 netbook. Used the Upgrade button on the Update Manager.

Took about 2.5 hours. That box appeared on the screen during my upgrade, too. I just ignored it.  Everything turned out fine. All my data/files are where they are supposed to be, so onward and upward for the next 4 or 5 years......

---

### Post by Bucky Ball on 2012-08-26
Sometimes upgrades can be problematic. I'm thinking you should have said yes to deleting the packages. Try these two commands in a terminal:

```
sudo apt-get update
sudo apt-get upgrade
```The second one upgrades apps/dependencies/packages, etc, not the release. You can also try booting into the recovery kernel and choose 'Fix Broken Packages' from the options (or do it in Synaptics).

---

### Post by ilovethislinuxstuff on 2012-08-26
> **Bucky Ball said:**
> Sometimes upgrades can be problematic. I'm thinking you should have said yes to deleting the packages. Try these two commands in a terminal:

```
sudo apt-get update
sudo apt-get upgrade
```The second one upgrades apps/dependencies/packages, etc, not the release. You can also try booting into the recovery kernel and choose 'Fix Broken Packages' from the options (or do it in Synaptics).

ok, i did that and everything appears ok. what i don't understand is why i have a lot of packages listed in ubuntu software center/installed software/unknown. i have a lot of packages in the unknown category. they have the word gnome on a lot of them. isn't this 12.05 called unity? should i erase these? and how? thanks.

---

### Post by Bucky Ball on 2012-08-26
Update Manager>click 'Settings' in the bottom left corner>find the Lucid repositories>untick.

That will help. If you have done an upgrade from 10.04/11.10 then you probably have some residual repos still enabled. These kind of upgrades can be problematic and a clean install is generally better (good reason to keep your data on a separate /home partition or similar setup to your OS).

---

### Post by dr13 on 2012-08-27
Hi 
I have experienced the same situation when installing to 12.04. I did not x the book but rather "accepted" it by clicking the little book icon on it. Now when I restarted I only have access to 5 files that I have on my desktop and there is no access to a menu task bar etc.

What do I need to do to sort this problem?

---

### Post by dr13 on 2012-08-27
" I did not x the book"
Sorry meant box

---

### Post by Bucky Ball on 2012-08-27
> **dr13 said:**
> Hi 
I have experienced the same situation when installing to 12.04. I did not x the book but rather "accepted" it by clicking the little book icon on it. Now when I restarted I only have access to 5 files that I have on my desktop and there is no access to a menu task bar etc.

What do I need to do to sort this problem?

You need to start a new thread with a title describing your problem and as much info as you can give about the problem and hardware/software config rather than posting on this one. Keep subscribed to this one and learn/add anything relevant. Post a link to the new one here if you want. 

Hijacking a thread makes it confusing for everyone. ;)

---

### Post by ilovethislinuxstuff on 2012-08-27
> **Bucky Ball said:**
> Update Manager>click 'Settings' in the bottom left corner>find the Lucid repositories>untick.

That will help. If you have done an upgrade from 10.04/11.10 then you probably have some residual repos still enabled. These kind of upgrades can be problematic and a clean install is generally better (good reason to keep your data on a separate /home partition or similar setup to your OS).

bucky-
I went to settings, but couldn't find lucid repositories?...

---

### Post by Bucky Ball on 2012-08-27
In 'Other Software' tab?

---

### Post by ilovethislinuxstuff on 2012-08-27
> **Bucky Ball said:**
> In 'Other Software' tab?

ok, i found it by going to dash home typing in "update" which gave me the folder "update manager" i clicked it and went to "settings" then "other software" and the only thing checked is 
"canonical partners added by software center
sofware packaged by canonical for their partners"

---

### Post by stoneguy on 2012-08-27
Don't sweat the window of squares. It's supposed to be a warning message of some sort. You can either ignore them, or click the lower right rectangle. In English language installs, those 2 squares spell "NO". (I suppose in French it has three squares and in German four :)

---

### Post by jeremyPDX on 2012-08-29
Same thing happened to me on upgrade from 10.04 to 12.04.

I copied the boxes to the clipboard and quickly opened a text editor. When pasted the message appeared.

> 
An error occurred while loading or saving
configuration info for evolution-alarm-notify.
Some of your configuration settings may
not work properly.


---

### Post by kansasnoob on 2012-08-29
That's this bug:

[https://bugs.launchpad.net/ubuntu/+source/pango1.0/+bug/1038573](https://bugs.launchpad.net/ubuntu/+source/pango1.0/+bug/1038573)

It would be nice to get more people to click on "effects me too" to turn up the bug heat ;)

---

### Post by ilovethislinuxstuff on 2012-08-30
ok, so maybe that was it. 

the thing is, and i really have no idea what i'm doing with this computer stuff, during the installation i think i clicked "no" to something about removing old packages. I'm wondering if I have a bunch of old packages in here now from 10.04 that I don't need. 

Also, when i go to shut down now, I get a black screen with a bunch of writing on it, that I didn't get before. Also, it takes longer for the boot up and shutdown now.???

---

### Post by black veils on 2012-08-30
> **ilovethislinuxstuff said:**
> ok, so maybe that was it. 

the thing is, and i really have no idea what i'm doing with this computer stuff, during the installation i think i clicked "no" to something about removing old packages. I'm wondering if I have a bunch of old packages in here now from 10.04 that I don't need. 

Also, when i go to shut down now, I get a black screen with a bunch of writing on it, that I didn't get before. Also, it takes longer for the boot up and shutdown now.???

that might be trivial, you are now using unity, it must use more resources than your previous system.

---

