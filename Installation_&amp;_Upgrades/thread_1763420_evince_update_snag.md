---
title: "evince update snag"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by dhave-dhave on 2011-05-20
I'm running 11.04 with Gnome 3.0.1 desktop shell (not Unity).

When I attempt to update my system using Synaptic, I'm getting this error message:

```
E: /var/cache/apt/archives/evince-common_3.0.0-4ubuntu2~natty1_all.deb: trying to overwrite '/usr/share/GConf/gsettings/evince.convert', which is also in package evince 3.0.0-0ubuntu1~build1
```

Should I just wait for the repos to be updated, or what?

Thanks.

---

### Post by grubu on 2011-05-21
Hello dhave-dhave,
exactly the same happened to me when testing gnome3, here is what I just did:

```

sudo apt-get remove evince
sudo apt-get update
sudo apt-get upgrade
```Then evidence was again set up correctly and upgrading completed.
The idea came up when reading these information:

[http://www.ubuntuupdates.org/packages/show/305674](http://www.ubuntuupdates.org/packages/show/305674)
[http://www.ubuntuupdates.org/bugs?package_name=evince](http://www.ubuntuupdates.org/bugs?package_name=evince)
[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/766882](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/766882)

I hope that this might help you.

---

### Post by dhave-dhave on 2011-05-21
Thank you very much, grubu. That fixed my problem.

---

### Post by grubu on 2011-05-21
Ah, nice to hear, that feels like real time chat :)
As I am new to the forums it is nice that I could help you out.
Maybe you know some more about the activity-role in Gnome3 and
can help me too? As I am testing the Iso from [cbowman57]("http://ubuntuforums.org/member.php?u=1089002"),
I already posted the question in here:
[http://ubuntuforums.org/showpost.php?p=10847461&postcount=80](http://ubuntuforums.org/showpost.php?p=10847461&postcount=80)

---

### Post by 23dornot23d on 2011-05-21
It tries to update evince-common without updating evince .......

The easy way is just to go into synaptic and tick evince and evince-common

then it updates ok ...... glad you sorted it though .....

---

### Post by grubu on 2011-05-22
Yes 23dornot23d, thank you that should do it via synaptic.

As having a question on the activities I will bring it up at thread:
[http://ubuntuforums.org/showthread.php?t=1754198&page=67](http://ubuntuforums.org/showthread.php?t=1754198&page=67)

---

### Post by dhave-dhave on 2011-05-22
@grubu: I'm afraid I can't be much help in return, as I'm an Ubuntu newby, even though I joined the forum way back in 2007 when I wanted to post a question about something. I've been using Arch for the past five years, and before that Gentoo and Slackware. Mainly I've shied away from the big desktop environments like KDE and Gnome. Now I'm spending some time on the other end of the Linux spectrum. Overall, I'm pretty impressed.

---

### Post by grubu on 2011-05-22
Okay thank you. I am thinking in that way too and also have to say that I got impressed by using it.
I got very interested in using Gentoo too, because I like the idea of using exactly what is needed and 
having a state of what is reliable, but this only seems to be necessary for a special project, 
so as Ubuntu offers the way of an easy desktop-life I will mainly focus on what is possible within Ubuntu.
And at the moment it seems that there is nothing that is impossible :)

---

