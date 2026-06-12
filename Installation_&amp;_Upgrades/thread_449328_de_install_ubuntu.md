---
title: "de install ubuntu"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by aliyanage on 2007-05-20
Good day everyone,

No worries, I am still sticking to Ubuntu :-D but I installed Ubuntu on my laptop at work as well and now that I am leaving the company I need to uninstall or just basically format the whole disc.

How exactly do I do that...? You know never really was interested in finding out :-D could someone please help me? There is no Windows on the machine just ubuntu and all I need to do is to wipe the whole disk...


regards
aliyanage

---

### Post by mikewhatever on 2007-05-20
Wiping the whole disk is an easy task with [gparted live cd]("http://http://gparted.sourceforge.net/livecd.php")
Ubuntu desktop install cd has that too under System>Administration. Just delete the partitions, and, if you are worried of any possible data recovering, reformat several times.
If you wanted to un-install Ubuntu while dual booting with Windows or other, [THIS PAGE]("http://www.users.bigpond.net.au/hermanzone/p18.htm") would prove useful.

---

### Post by aliyanage on 2007-05-20
thanks a lot for that help, I just downloaded gparted live cd and wiped ubuntu, but now what happens is when I try to reboot I get an error message saying:

```
GRUB Loading stage1.5

GRUB loading, please wait...
Error 22
```

How do I get rid of this message or is that normal...?

Regards
aliyanage

---

### Post by mikewhatever on 2007-05-20
Hm..., Grub is looking for Ubuntu partition which is obviously not there. I was under the impression, the process would overwrite the mbr too, but apparently it did not. Don't know, I'll look for some answers.

---

### Post by aliyanage on 2007-05-20
well, that's okay... I guess it will anyway install the MBR and use it as soon as someone starts installing windows on it right?
And if the next guy would be using Linux it's okay as well... 


regards
aliyanage

---

