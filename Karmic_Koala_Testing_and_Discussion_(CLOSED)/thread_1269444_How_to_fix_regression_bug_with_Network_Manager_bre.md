---
title: "How to fix regression bug with Network Manager breaking 3G modem: downgrade"
date: 2009-09-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andresmh on 2009-09-18
I had to downgrade to network-manager to 0.7.1.git.5.272c6a626-0ubuntu1 and network-manager-gnome to 0.7.1.git.3.0461fff8-0ubuntu2 in order to get my 3G modem to work.

I am not sure if I reported this bug in the wrong place (I did it a while ago) but no one has changed its status:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/410942](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/410942)

I have the feeling Karmic might be released with this bug since it doesn't seem to affect a lot of people, so if that's the case here is how to fix it:

Anyway, in case there is someone else out there who is experiencing this problem simply add this to your source list:
deb [http://ppa.launchpad.net/network-manager/ppa/ubuntu](http://ppa.launchpad.net/network-manager/ppa/ubuntu) karmic main

And then force version 0.7.1 for those two packages.

---

### Post by handaxe on 2009-09-18
I recall seeing a bug report about modem-manager causing problems for nm v0.8 and that it worked if you killed the running instance of modem-manager after plugging in the modem.

Poke around and see if I am right....

HA

---

### Post by andresmh on 2009-09-18
well, my modem is internal so I cannot really unplug it :)

---

### Post by tekstr1der on 2009-09-18
I had a lengthy thread concerning these issues:

[http://ubuntuforums.org/showthread.php?t=1234128](http://ubuntuforums.org/showthread.php?t=1234128)

Also, other bugs filed in regards to this:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/410386](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/410386)

and

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/416913](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/416913)


> I recall seeing a bug report about modem-manager causing problems for nm v0.8 and that it worked if you killed the running instance of modem-manager after plugging in the modem.

Yes, at least for me prior to the latest batch of network-manager, modemmanager package updates (all is working as expected now), I still had connection/reconnection issues and the workaround was simply:

```
sudo killall modem-manager
```

After which I could connect.

---

### Post by handaxe on 2009-09-18
Thanks for the info re the bugs - you should prolly mark [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/416913](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/416913)  as fixed (I assume you can do that as the original reporter?).

@andresmh: update your bug report with the fact that the problem persists with the latest n-m updates (assuming that it does of course:)) and see if someone notices and can confirm. Does not seem like a bug that would be ignored UNLESS no-one else has it.

HA

---

### Post by tekstr1der on 2009-09-18
> **handaxe said:**
> Thanks for the info re the bugs - you should prolly mark [https://bugs.launchpad.net/ubuntu/+s...er/+bug/416913](https://bugs.launchpad.net/ubuntu/+s...er/+bug/416913)  as fixed (I assume you can do that as the original reporter?).

Nope. Can't do that. Just imagine the chaos and confusion that would ensue on Launchpad if users could assign bug status. That's one purpose of "this affects me too" and "this doesn't affect me".

---

### Post by handaxe on 2009-09-18
Of course not ordinary users:P - but I did think that the original reporter had that right. 

And testing such rights, I managed to change the OPs bug report from new to invalid (and then in in utter surprise) back to new.  Sorry! Should I have been able to do that?  This isoff topic, I know.

HA

---

### Post by tekstr1der on 2009-09-18
hmm... I stand corrected, I can indeed change the status of my bug reports to "fix released". Still best to let the devs or package maintainers handle this though, I believe.

---

