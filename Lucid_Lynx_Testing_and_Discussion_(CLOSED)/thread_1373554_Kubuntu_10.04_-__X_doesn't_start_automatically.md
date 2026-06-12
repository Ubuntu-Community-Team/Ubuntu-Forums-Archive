---
title: "Kubuntu 10.04 -  X doesn't start automatically"
date: 2010-01-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by VMC on 2010-01-05
When I boot my Kubuntu 10.04, I'm brought to a terminal to login. After that, **startx** starts my X server. It worked without any issues until today.

I googled around trying to find this exact same probrlem. Someone in 08 had this issue. I didn't see his fix. I know, or think I know that init.d isn't the one to check anymore, what with upstart. So any fixes prior to 09 won't apply.

This is just a straight Kubuntu 1.04 install. No ppa's, nothing special, its plain vanilla.

I checked my xorg log files, but that is in my home dir, and X starts before anything there. Nothing in /var/logs that's suspicious.

What I'm asking is what now starts X automatically? 

Thanks.

---

### Post by cariboo on 2010-01-05
It sounds like kdm is starting automagically try:

```
sudo service kdm start
```

at the prompt to see if it will start X.

---

### Post by VMC on 2010-01-05
> **cariboo907 said:**
> It sounds like kdm is starting automagically try:

```
sudo service kdm start
```

at the prompt to see if it will start X.

I'll try that, but doesn't startx accomplished the same thing?

edit: Ok, I tried that. A little different. Your command starts a graphic login, then X starts, but once I reboot, I presented with the same dilema. No X.

---

### Post by LKjell on 2010-01-06
Well gdm does not start here too. I have to use service gdm start to get gnome.

---

### Post by VMC on 2010-01-06
> **LKjell said:**
> Well gdm does not start here too. I have to use service gdm start to get gnome.

Mine works on Ubuntu, and it use to work on Kubuntu. It just suddenly stopped.

---

### Post by LKjell on 2010-01-06
It is getting annoying. It works now. But I have done no updates. The only thing I did was to log into recovery mode. Though the auto login is disabled somehow. 

These kind of things is hard to file a bug report against. No way to reproduce...

---

### Post by kansasnoob on 2010-01-06
This may or may not apply, but some time ago I'd been playing with adding this stuff to my chroot:

[https://wiki.ubuntu.com/KarmicKoala/ReleaseNotes#Upstart%20jobs%20cannot%20be%20run%20in%20a%20chroot](https://wiki.ubuntu.com/KarmicKoala/ReleaseNotes#Upstart%20jobs%20cannot%20be%20run%20in%20a%20chroot)

**BTW that doesn't seem to apply in Lucid anymore!**

Anyway someone suggested that I should run:

rm /sbin/initctl
dpkg-divert --local --remove /sbin/initctl

before exiting the chroot?

After doing so I had the same propblem you're having and the fix was as simple as:

```
sudo apt-get install --reinstall upstart
```

Not at all sure if that will help but I'd think it can't actually blow anything up :P

---

### Post by tghe-retford on 2010-01-06
Known bug: [https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/503610](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/503610)

I edited my /etc/init/kdm.conf and removed (don't comment) the following line:

```
and started hal
```

KDE now works as expected. This line according to the bug report will be removed anyway when the KDE 4.4 release candidate is uploaded to the Lucid repositories.

---

### Post by VMC on 2010-01-06
> **tghe-retford said:**
> Known bug: [https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/503610](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/503610)

I edited my /etc/init/kdm.conf and removed (don't comment) the following line:

```
and started hal
```

KDE now works as expected. This line according to the bug report will be removed anyway when the KDE 4.4 release candidate is uploaded to the Lucid repositories.

Thanks for the bug reference! I clicked "it affects me too".
Will let you know if it worked.

edit: It **worked** !  Thank you tghe-retford !

---

### Post by caryb on 2010-01-06
Thanks that fixed it for me too.


Cary

---

