---
title: "Not able to Log on - Kernel panic not syncing VFS"
date: 2011-07-03
forum: Installation &amp; Upgrades
---

### Post by ale_ramesh on 2011-07-03
Hi Everyone,

Last week i was playing with adding/removing items to the panel and some unknown error happened and suddenly my keyboard strokes are not recognized([COLOR="Red"]I can enter log-in password while logging but after that input from keyboard is not recognized[/COLOR]).

As per my friends suggestion i tried to update the ubuntu to the latest version 11.04 and during this process,System restarted by itself and it could not restart successfully and since then i am getting the below error:

> 
[COLOR="Red"]Kernel Panic not syncing VFS unable to mount root vfs on Unknown block(0,0)[/COLOR]

I tried with different options displayed on the boot up screen and the results are as below:

[LIST=1]
[*]Ubuntu-2.6.3-28-generic [COLOR="Red"]-- Not working[/COLOR]
[*]Ubuntu-2.6.3-28-generic-Recovery Mode [COLOR="Red"]-- Not working[/COLOR]
[*]Ubuntu-2.6.3-27-generic [COLOR="YellowGreen"]-- Working but input from keyboard is not recognized[/COLOR]
[*]Ubuntu-2.6.3-27-generic-Recovery Mode [COLOR="YellowGreen"]-- Working but input from keyboard is not recognized[/COLOR]
[*]Ubuntu-2.6.3-24-generic [COLOR="YellowGreen"]-- Working but input from keyboard is not recognized[/COLOR]
[*]Ubuntu-2.6.3-24-generic-Recovery Mode [COLOR="YellowGreen"]-- Working but input from keyboard is not recognized[/COLOR]
[*]Windows 7 [COLOR="YellowGreen"]-- working and keyboard also working[/COLOR]
[/LIST]

As the other options are working but input from keyboard is not recognized after logging in..

Please help me out of this situation..

Thanks in Advance..

---

### Post by mörgæs on 2011-07-03
Do you also have the problem when logging into Gnome Classic?

---

### Post by ale_ramesh on 2011-07-03
> **mörgæs said:**
> Do you also have the problem when logging into Gnome Classic?

I am just a beginner to the world of Linux..This is the first time i am hearing the term Gnome Classic..

At least to my knowledge i did not install any such thing..

Please let me know how can i check that so that i can confirm..

Thanks for looking into my question..

---

### Post by mörgæs on 2011-07-03
It is installed by default. At the bottom of the log-in screen you see a list of options, among others Gnome Classic.

[http://ubuntugenius.wordpress.com/2011/05/27/ubuntu-classic-desktop-how-to-log-into-the-old-gnome-environment-instead-of-unity/](http://ubuntugenius.wordpress.com/2011/05/27/ubuntu-classic-desktop-how-to-log-into-the-old-gnome-environment-instead-of-unity/)

---

### Post by ale_ramesh on 2011-07-03
> **mörgæs said:**
> It is installed by default. At the bottom of the log-in screen you see a list of options, among others Gnome Classic.

[http://ubuntugenius.wordpress.com/2011/05/27/ubuntu-classic-desktop-how-to-log-into-the-old-gnome-environment-instead-of-unity/](http://ubuntugenius.wordpress.com/2011/05/27/ubuntu-classic-desktop-how-to-log-into-the-old-gnome-environment-instead-of-unity/)

I dont get that far..it just shows me the error message as soon as i select the ubuntu option from boot up menu..

---

### Post by ale_ramesh on 2011-07-03
> **mörgæs said:**
> It is installed by default. At the bottom of the log-in screen you see a list of options, among others Gnome Classic.

[http://ubuntugenius.wordpress.com/2011/05/27/ubuntu-classic-desktop-how-to-log-into-the-old-gnome-environment-instead-of-unity/](http://ubuntugenius.wordpress.com/2011/05/27/ubuntu-classic-desktop-how-to-log-into-the-old-gnome-environment-instead-of-unity/)

Ok, I tried what u said and here are the observarions..

[LIST=1]
[*]Ubuntu-2.6.3-28-generic -- Does not even reach that far,Fails at the boot level only
[*]Ubuntu-2.6.3-28-generic-Recovery Mode -- Does not even reach that far,Fails at the boot level only


When tried with the other options Ubuntu-2.6.3-27,Ubuntu-2.6.3-24 i dont see the option 'Ubuntu Classic'.

The options displayed are:
Recovery Console
Ubuntu Desktop Edition
Ubuntu Desktop Edition(Safe Mode)
User Defined session


Am i missing anything here?

---

### Post by ale_ramesh on 2011-07-03
> **ale_ramesh said:**
> Ok, I tried what u said and here are the observarions..

[LIST=1]
1. Ubuntu-2.6.3-28-generic [COLOR="Red"]-- Does not even reach that far,Fails at the boot level only[/COLOR]

When tried with the other options Ubuntu-2.6.3-27,Ubuntu-2.6.3-24 [COLOR="Magenta"]i dont see the option 'Ubuntu Classic'[/COLOR].

The options displayed are:
Recovery Console
Ubuntu Desktop Edition
Ubuntu Desktop Edition(Safe Mode)
User Defined session


Am i missing anything here?
Instead of editing the previous post, accidentally i clicked on Quote button..Please bear with this

---

### Post by ale_ramesh on 2011-07-04
Any takers guys..

Please help me.

---

### Post by mörgæs on 2011-07-04
Maybe best is a reinstall. A kernel panic is the most severe error in Linux, and it rarely pays to spend long time mending it.

---

### Post by ale_ramesh on 2011-07-04
> **mörgæs said:**
> Maybe best is a reinstall. A kernel panic is the most severe error in Linux, and it rarely pays to spend long time mending it.

But i have lots of data in that partition and moreover i cannot access it through Windows..Is there any way i can take backup?

---

### Post by mörgæs on 2011-07-04
Yes, from a live boot.

---

