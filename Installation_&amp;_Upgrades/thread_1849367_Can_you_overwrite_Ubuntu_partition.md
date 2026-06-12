---
title: "Can you overwrite Ubuntu partition?"
date: 2011-09-24
forum: Installation &amp; Upgrades
---

### Post by futralistic on 2011-09-24
I recently installed Ubuntu 11.04 on an old Dell laptop that I had laying around as a dual boot with XP. I found out after the installation that even in classic mode it is a little more than this laptop can comfortably run.

My question is can I install say Xubuntu over the Ubuntu partition without any major problems? Will the installer give that option?

Thank you.

---

### Post by raja.genupula on 2011-09-24
```
sudo apt-get install xubuntu-desktop
```
will installs xubuntu in your ubuntu system with out doing any damage to Ubuntu. From login screen you can choose the session you want.

---

### Post by dino99 on 2011-09-24
> **futralistic said:**
> I recently installed Ubuntu 11.04 on an old Dell laptop that I had laying around as a dual boot with XP. I found out after the installation that even in classic mode it is a little more than this laptop can comfortably run.

My question is can I install say Xubuntu over the Ubuntu partition without any major problems? Will the installer give that option?

Thank you.

Maybe you should use Lubuntu (lxde)

---

### Post by raja.genupula on 2011-09-24
Hi man 
        could you please give us your Laptop details , I mean RAM,Processor. 

ok go with this.

Xubuntu needs  512 MB(Recommended) For better performance.
&
Lubuntu needs  256 Mb(Recommended) for Better performance .

so choose any option from above.

all the best

---

### Post by SecretCode on 2011-09-24
While I'd go with adding xubuntu-desktop (or lubuntu-desktop) to your existing installation, yes you can definitely install Xubuntu in the same partition replacing Ubuntu. Note that this will reformat that partition and erase anything you have saved there.

---

### Post by futralistic on 2011-09-26
My details are:

Pentium M 1.5Ghz
512MB ram

---

### Post by raja.genupula on 2011-09-27
Then my choice for you is
1.Lubuntu
2.Xubuntu

for pkg details presented in that two OS's look at here in this two links 

[http://en.wikipedia.org/wiki/Xubuntu#Applications](http://en.wikipedia.org/wiki/Xubuntu#Applications)

[http://en.wikipedia.org/wiki/Lubuntu#Applications](http://en.wikipedia.org/wiki/Lubuntu#Applications)

All The Best.

---

### Post by Elfy on 2011-09-27
> **futralistic said:**
> My question is can I install say Xubuntu over the Ubuntu partition without any major problems? Will the installer give that option?

Thank you.

> **SecretCode said:**
>  yes you can definitely install Xubuntu in the same partition replacing Ubuntu. Note that this will reformat that partition and erase anything you have saved there.

As SecretCode says - it is possible.

Boot the livecd - when you reach the partitioning section - choose Manual/Something Else 

You'll get a new window showing your partitions - choose the partition currently housing your install and Edit

In the new window - format to ext4 (or whatever you want) then in the mountpoint - set that to /

If you have a seperate /home partition - do the same, but DO NOT format - just set mountpoint as /home

Then carry on - it will install to the partitions you've specified.

---

### Post by futralistic on 2011-09-27
Once again.

Thank you so much for your help!

---

