---
title: "gnome wants to automount my partitions at login"
date: 2009-07-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by yelo3 on 2009-07-01
When I login I see an entry that asks me to insert the password to mount my partitions (I have 2 other partitions: windows and fedora).
I don't really want to auto mount them, since I don't need them. Do you know how to stop this?

---

### Post by doas777 on 2009-07-01
> **yelo3 said:**
> When I login I see an entry that asks me to insert the password to mount my partitions (I have 2 other partitions: windows and fedora).
I don't really want to auto mount them, since I don't need them. Do you know how to stop this?

are they listed in your fstab?
```
sudo cat /etc/fstab
```

---

### Post by yelo3 on 2009-07-01
Bo they aren't (they've never been in fstab because I don't want to mount them)
Just suddenly gvfs wants to mount them, there must be a configuration key...

---

### Post by davideotape on 2009-07-01
I'm getting the same behaviour. Don't know why it's happening but i'm happy just to click cancel until a fix is released :)

---

### Post by ronacc on 2009-07-01
on my sys it only wants to mount partitions that were mounted at the time of shutdown .

---

### Post by DougieFresh4U on 2009-07-01
Don't know why but when I finally get to desktop there is an 'icon' for my Windows 7 partition and I have to right click it and select 'unmount'.
this is happening every time I boot up.

---

### Post by tjeremiah on 2009-07-01
mines everytime I log on, wants to mount my restore factory settings partition :lolflag:

---

### Post by descendent87 on 2009-07-01
Yeah gnome seems to pick a random partition and try to mount it on login

---

### Post by tad1073 on 2009-07-02
same here

---

### Post by zoff_ita on 2009-07-02
confirmed here too

---

### Post by davideotape on 2009-07-02
Anyone done a bugreport yet?

---

### Post by tjeremiah on 2009-07-02
> **davideotape said:**
> Anyone done a bugreport yet?

Hopefully someone who knows how to initiate one in detail would.

---

### Post by Regenweald on 2009-07-02
System>>preferences>>Startup Applications>> Uncheck - PolicyKit authentication agent

---

### Post by zika on 2009-07-02
> **Regenweald said:**
> System>>preferences>>Startup Applications>> Uncheck - PolicyKit authentication agentGreat! Thank You!
There is a downside though. This prevents from mounting partition while in the session.

---

### Post by Regenweald on 2009-07-02
> **zika said:**
> Great! Thank You!
There is a downside though. This prevents from mounting partition while in the session.

Now that sounds buggish....
I'd assume the that policykit would be invoked upon request. But as it stands i like the feature, might as well mount what isn't in my fstab at boot.

---

### Post by Darkshade on 2009-07-02
Just wiped out my Kubuntu install and put Ubuntu again (I guess I missed too many things from Gnome, although KDE had its pros too... anyway not the right place for this).
I'm getting the same behavior, it's rather annoying but "fixing" it (clicking Cancel) isn't that hard. Been testing Ubuntu for about a year already and from what I've seen things like this get fixed pretty fast so have some patience and file a bug report :P

---

### Post by davideotape on 2009-07-03
[https://bugs.edge.launchpad.net/ubuntu/+source/policykit-1-gnome/+bug/395122](https://bugs.edge.launchpad.net/ubuntu/+source/policykit-1-gnome/+bug/395122) :D

---

### Post by scradock on 2009-07-05
> **davideotape said:**
> [https://bugs.edge.launchpad.net/ubuntu/+source/policykit-1-gnome/+bug/395122](https://bugs.edge.launchpad.net/ubuntu/+source/policykit-1-gnome/+bug/395122) :D
Confirmed and subscribed!

---

