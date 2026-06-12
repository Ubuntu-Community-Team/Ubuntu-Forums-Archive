---
title: "Network Manager is rubbish"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Johnsie on 2008-10-11
it's too buggy. Half the time it forgets passwords etc. I also dont think it's very user friendly compared tot the network manager in older versions of Ubuntu. The best network manager I've used was the one that comes on the Eeepc version of Xandros.

---

### Post by psyke83 on 2008-10-11
> **Johnsie said:**
> it's too buggy. Half the time it forgets passwords etc. I also dont think it's very user friendly compared tot the network manager in older versions of Ubuntu. The best network manager I've used was the one that comes on the Eeepc version of Xandros.

Thanks for your feedback, very constructive.

There was a problem with the keyring integration in the beta release, but as far as I know, it's been fixed.

---

### Post by Johnsie on 2008-10-11
You're welcome. Let's hope the can improve this before the final release. What exactly does "system setting" mean? I've never seen that before on any network configuration tool.

---

### Post by gnomeuser on 2008-10-11
> **Johnsie said:**
> it's too buggy. Half the time it forgets passwords etc. I also dont think it's very user friendly compared tot the network manager in older versions of Ubuntu. The best network manager I've used was the one that comes on the Eeepc version of Xandros.

Do you have a bugreport on this issue?

---

### Post by plun on 2008-10-11
Well.. "johnsie" is right but perhaps wrong :)

Nullack started this thread

[http://ubuntuforums.org/showthread.php?t=910632](http://ubuntuforums.org/showthread.php?t=910632)


**NM 0.7 must be nearly perfect** and I noticed *one update today*.

There is no room for "Singing in the rain" with NM 0.7

I really hope that developers working with this skips other
less important issues.

---

### Post by techdude3177 on 2008-10-11
when i first got intrepid i would have to agree that it would always forget my password and it got annoying but maybe last week, i noticed that it remember my password and at the beginning of this week it would start connecting to my router at sign in right away.  however as of yesterday, it seems to be buggy....

---

### Post by bash on 2008-10-11
For me at least Network Manager works flawlessly. Either for wireless or wired network. Actually it works so good, I never have to deal with it, 'coz it just works. 

So at least I'm quite happy with the new NM.

---

### Post by plun on 2008-10-11
Many unhappy users

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bugs](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bugs)


The major goal for Intrepid

> A particular focus for us will be pervasive internet access, the
ability to tap into bandwidth whenever and wherever you happen to
be. No longer will you need to be a tethered, domesticated animal -
you'll be able to roam (and goats do roam!) the wild lands and
access the web through a variety of wireless technologies. We want
you to be able to move from the office, to the train, and home,
staying connected all the way.

[https://lists.ubuntu.com/archives/ubuntu-devel/2008-February/025136.html](https://lists.ubuntu.com/archives/ubuntu-devel/2008-February/025136.html)



Dan Wiliams also seems to have time now....this must be fixed !

---

### Post by caryb on 2008-10-11
The KDE4 implementation is 1/2 baked at best! with my wireless connection I have selected auto connect but I still have to right click the wireless connection & get it to manually connect on every boot.


Cary

---

### Post by techdude3177 on 2008-10-11
i also notice after a while, there is no wireless connection selected and if you hold the cursor over the network manager applet it says its connected to '(none)'.  just a minor issue.

---

### Post by FuturePilot on 2008-10-11
> **techdude3177 said:**
> i also notice after a while, there is no wireless connection selected and if you hold the cursor over the network manager applet it says its connected to '(none)'.  just a minor issue.

I've noticed that too. Not a huge deal, but kind of annoying that when it says 'none' it ends up spamming your .xsession-errors with 
```
** (nm-applet:6647): CRITICAL **: nm_utils_ssid_to_utf8: assertion `ssid != NULL' failed
```
over and over and over. :|

---

### Post by TheMono on 2008-10-11
Using Kubuntu, and I notice no problems at all. I walk into my room, it connects to the wireless there automatically. The main house, that wireless... uni, that wireless. All without being told. I'm not sure what causes the difference in user experiences though.

---

### Post by ShirishAg75 on 2008-10-11
Hi all, 
 I have been having all sorts of problems with the latest itertion of Network Manager. Also one learns and that's the good thing. 

I have actually illustrated my issue in the aptly titled thread 

" network-manager After reboot network is totally broken " 

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/279262](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/279262)

So while things are okish from now, I dunno what's going on the next reboot.  So if its possible lemme know how should I be writing stuff so it basically makes a clean breast of things. 

so I'm guessing that the ifconfig command is the key to the whole affair. Here's the command and please lemme know what's wrong or incomplete. 

```

sudo ifconfig eth0 inet 192.168.1.2 netmask 255.255.255.0 broadcast 61.1.96.69

``` 

From the /etc/network/interfaces file these are the contents which need to be filled in somewhere. 

address 192.168.1.2 netmask 255.255.255.0 gateway 192.168.1.1

The broadcast address which I have given is actually the nameserver (dunno if its a good idea or not, it works but that's about it)

Usually there are two nameservers, where or how should I put them across?

Then did one for something called 

```
route add default gw 192.168.1.1
```

which leads route to show me 

```

 route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

Again dunno if having a default gateway is a good idea or not. 

Comments and improvements to the same are encouraged :)
[B]
[/B]

---

### Post by plun on 2008-10-11
> **TheMono said:**
> Using Kubuntu, and I notice no problems at all. I walk into my room, it connects to the wireless there automatically. The main house, that wireless... uni, that wireless. All without being told. I'm not sure what causes the difference in user experiences though.

Please read bug reports...

For the majority it works but there are too many errors for 
functionality which just should work. (basic network connections)

So the challenge is to minimize all errors, but nothing can be perfect.

This is one of a handfull functions which just must be fixed, **_otherwise re-schedule Intrepid !_**


:)

---

### Post by caryb on 2008-10-11
I could be totally off beam here (Aussie expression) but I don't believe that the interfaces file is read when network mangler is installed. I deleted all but the loopback lines & it doesn't change anything. This has lead me to believe it is all but superfluous.

I would be happy for someone to correct me.


Cary

---

### Post by Johnsie on 2008-10-11
Aplogies for my use of the word 'rubbish'. That was a bit hash. I was extremely frustrated with this on one machine. It works ok on my eeepc and my desktop, but wont work at all on another computer that I use. I think the problem may be partly due to a broken wireless driver. Either way it appears to be a networking regression and I will file a bug report.

ps. I still think the gui is in the configuration area needs to be made more user friendly. Joe Sixpack and the hockey moms wouldn't have a clue how to use it.

---

