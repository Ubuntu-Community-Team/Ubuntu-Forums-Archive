---
title: "Unable To install any Program by Synaptic Package  Manager"
date: 2010-04-12
forum: Installation &amp; Upgrades
---

### Post by Jitu_123 on 2010-04-12
Whenever I try to install a program by  Synaptic Package  Manager, it downloads packages but it doesn't install those.It tries to connect to downloads.openwrt.org but unables to connect because of connection time out. I have attached a screenshot of it. please help me.
Thanks

---

### Post by Khakilang on 2010-04-12
I usually install program from Ubuntu Software Center. It is much easier. If you are using 9.10 it should be there. Not so confident in Synaptic unless I had no choice.

---

### Post by snowpine on 2010-04-12
Do you have a working internet connection? Can you surf to [http://downloads.openwrt.org](http://downloads.openwrt.org) in Firefox?

---

### Post by _0R10N on 2010-04-12
Assuming you have a network connection working, did you try with aptitute??

One more thing: did you changed the repository list, or added/removed any repo???

Kind regards!

_0R10N >>

---

### Post by Jitu_123 on 2010-04-13
@ snowpine Yes,i can.

---

### Post by Jitu_123 on 2010-04-13
@[Koh Kook Loon]("http://ubuntuforums.org/member.php?u=887793") same problem with Ubuntu Software Center.I can Neither install any program nor uninstall.Actually there is some problem with my linuxdc++,so I want to unistall it.While uninstalling it got stuck at 50%.

---

### Post by Jitu_123 on 2010-04-13
@ [_0R10N]("http://ubuntuforums.org/member.php?u=1052866") I am using ubuntu ultimate edition edition 2.4. I don't know about apititude and also the repository list.Please explain. 
thanks

---

### Post by _0R10N on 2010-04-20
I'm sorry for the late reply. I hope you already solved your problem!!! :grin:

Aptitude is a more advanced tool for installing new packages.
```
sudo aptitude install <package_name>
```

will download and install the specified package. You should try it!

```
/etc/apt-get/sources.list
```

it's a file containing the repositories list where your system looks for updates and new packages.

Kind regards!

_0R10N >>

---

