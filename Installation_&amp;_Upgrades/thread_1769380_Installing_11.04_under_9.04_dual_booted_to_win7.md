---
title: "Installing 11.04 under 9.04 dual booted to win7"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by janno92 on 2011-05-27
hi guys, i want to upgrade from 9.04 jaunty to 11.04. i already have my 11.04 on my usb and will be booting from it,
 now, i dont know what to do to install it over my 9.04 having it dual booted to window 7.

need your inputs to help me,,tia

---

### Post by Hedgehog1 on 2011-05-27
If you have your data in a separate '/home' partition you can install 11.04 over your 9.04 '/' (root) partition.

First, define your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Then define your '/home' partition:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

***The Hedge***

:KS

p.s. To learn how to move your '/home' into it's own partition: **_[SeparateHomePartition]("http://www.psychocats.net/ubuntu/separatehome")_**

---

### Post by janno92 on 2011-05-27
fyi, my update manager and synaptic wont let me do it,saying some blahblah i dont understand(sorry in a newbie). it says something like out of date and the likes.

when it try to download packages, almost everything fails though im connected to the internet.

---

### Post by dFlyer on 2011-05-27
I'm not going to be of much help, I can only recommend that you backup all your data you want to keep before you proceed. I believe an option on 11.04 is to replace an older version of linux. Not sure how that will affect grub.

---

### Post by janno92 on 2011-05-27
> **Hedgehog1 said:**
> If you have your data in a separate '/home' partition you can install 11.04 over your 9.04 '/' (root) partition.

First, define your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Then define your '/home' partition:

**[SIZE=4]IF YOU ARE DOING AN UPGRADE, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

***The Hedge***

:KS

p.s. To learn how to move your '/home' into it's own partition: **_[SeparateHomePartition]("http://www.psychocats.net/ubuntu/separatehome")_**


thanks for the fas reply, ive already seen this post, but i cant understand.lol anyway cant you direct me to the  installing part, ive got nothing to have backup under 9.04 for ive got no file there .

---

### Post by janno92 on 2011-05-27
> **dFlyer said:**
> I'm not going to be of much help, I can only recommend that you backup all your data you want to keep before you proceed. I believe an option on 11.04 is to replace an older version of linux. Not sure how that will affect grub.

thanks,
yeah, thats is one that stops me,im afraid after installing 11.04 will affect grub loader and seeing i wont be able to boot to any of my OS

---

### Post by janno92 on 2011-05-27
just another quick question, since i will be using my usb flash drive to install ubuntu  11.04, im afraid i would have to lose it as a flash drive for it wil forever be some sort of installer cd

---

### Post by Hedgehog1 on 2011-05-27
If you have no data you wish to save, when you boot from the LiveUSB and select Install:

[IMG]http://img858.imageshack.us/img858/9995/small06tryubuntu.png[/IMG]

You will eventually get a screen with various install options:

[IMG]http://img848.imageshack.us/img848/874/upgradetonatty.png[/IMG]

Select the 'Erase Ubuntu XX.XX and reinstall'

This will reuse your current Ubuntu partitions(s) for Natty.

***The Hedge***

:KS

---

### Post by janno92 on 2011-05-27
should there be no truoble with grub loader?


edit, how will it know the partition for ubuntu?im afraid it will delete everything

---

### Post by Hedgehog1 on 2011-05-27
This install will replace the legacy grub you are running now with the new Grub.

There is a small chance that the new grub will want to use a higher resolution than your monitor can show.

**IN THE UNLIKELY EVENT THIS HAPPENS:**

Grub will still be running, and you can hit enter to select Ubuntu (assuming that is your default) or arrow up/down and hit enter so you get Ubuntu to boot up.

The you would do this:

```
gksudo gedit /etc/default/grub
```

[COLOR="Red"]and change this line:[/COLOR]

#GRUB_GFXMODE=640x480

[COLOR="red"]to this:[/COLOR]

GRUB_GFXMODE=640x480

[COLOR="red"]Then save and exit the document.[/COLOR]


Then do:

```
sudo update-grub
```


***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-27
> **janno92 said:**
> should there be no truoble with grub loader?


edit, how will it know the partition for ubuntu?im afraid it will delete everything

To avoid deleting things you do not want it to, you can instead select the 'something else' option here:

[IMG]http://img848.imageshack.us/img848/874/upgradetonatty.png[/IMG]

An manually select your Ubuntu partition yourself:

[IMG]http://img34.imageshack.us/img34/6017/08allocdrivespace6.png[/IMG]

Define your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

---

### Post by janno92 on 2011-05-28
gonna mark this thread now,
im done installing 11.04 under 9.04,

just followed mr, hedgehog, except i selected erase 9.04 and install 11.04..
thank you all

---

