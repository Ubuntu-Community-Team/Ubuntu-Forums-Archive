---
title: "NM 0.7 Still Isnt Fixed"
date: 2008-09-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-09-04
Well were now into beta 2 of gnome and network manager still isnt fixed :(

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/258743](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/258743)

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/256054](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/256054)

[http://bugzilla.gnome.org/show_bug.cgi?id=548114](http://bugzilla.gnome.org/show_bug.cgi?id=548114)

EDIT: Some other bugs reported by another person:

NM 0.7 Regression from 0.6.6 using VPNC plugin
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/262191](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/262191)
NM 0.7 Hard to fix if you have saved passwords for vpnc plugin (possible
others)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/262214](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/262214)
NM 0.7 GSM/3G signal strength is not reported by NM
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/262232](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/262232)
NM 0.7 VPNC plugin is missing option DNSUpdate No
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/262234](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/262234)
NM 0.7 Sony Ericsson P1i isn't recognized as a 3G modem
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/262399](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/262399)
NM 0.7 No option for connecting to L2TP IPSEC VPN
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/264691](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/264691)

---

### Post by beartard on 2008-09-04
Don't think it's just Gnome  ;)

---

### Post by Nullack on 2008-09-04
Its a gnome project

---

### Post by priegog on 2008-09-04
Hmm. 
Being this the most-wanted improvement in Ibex, I think maybe a Dapper kind of situation might be in order. A few months aren't gonna kill anyone, and Ibex without NM 0.7 isn't worth it IMHO. This would also solve the Firefox 3.1 debate. Any toughts?

---

### Post by vishalrao on 2008-09-05
yes, a delay in releasing ibex isnt the end of the world. will also make it easier for openoffice 3 to get in...

i dont care too much about ff 3.1 but OOo 3, NM7 (wireless) are what i'd mainly like to see get in.. then there are other packages which can be updated... GIMP, WINE etc...

---

### Post by BC7333 on 2008-09-05
Are these three bugs that critical?

NM 0.7 so far is already a breath of fresh air. Works much better than before.  Sure it ain't perfect, but wouldn't updates cure that?

---

### Post by meborc on 2008-09-05
Ibex isn't LTS ... it is meant to have "exiting new things"... and if you delay Ibex like Dapper was delayed, the 9.04 edition will be like Edgy - pointless

---

### Post by Nullack on 2008-09-05
> **BC7333 said:**
> Are these three bugs that critical?

NM 0.7 so far is already a breath of fresh air. Works much better than before.  Sure it ain't perfect, but wouldn't updates cure that?

I consider the ability to not be able to set static IP addresses and a specific maximum MTU to be critical. Not everyone uses DHCP.

The developer upstream commented that he thought it was a simple fix but its been a long time now.

---

### Post by xerosis on 2008-09-05
At least it vaguely works for you guys, knetworkmanager doesn't even work with the 0.7 APIs ;)

---

### Post by Sophont on 2008-09-05
I use DHCP but I need to lower MTU to have a stable VPN connection.

Currently I have to change MTU via a script that I have to run every time after VPN is connected.

Wouldn't have thought that setting MTU is so difficult.

In case any VPN users need this:
```
sudo ifconfig ppp0 mtu 1200
```

---

### Post by beartard on 2008-09-05
> **Nullack said:**
> Its a gnome project
Whose project it is hardly matters when it's not working.  Network Manager affects all the buntus.  I was just making the point that it's a larger problem than if it only affected gnome users.

---

### Post by ntetreau on 2008-09-05
> **Nullack said:**
> I consider the ability to not be able to set static IP addresses and a specific maximum MTU to be critical. Not everyone uses DHCP.

The developer upstream commented that he thought it was a simple fix but its been a long time now.

I don't mean to steal your thunder here but your point should be re-phrased: "There is the ability to set static IP addresses, but not when one wants to also set the maximum MTU".  Having the ability to set static IP in NM 0.7 is really great and has been working perfectly for me in all alphas. At least, for all those not using DHCP and, thus, using a static IP (without need to change MTU), NM 0.7 is a big step forward.

---

### Post by Exsecrabilus on 2008-09-05
> **meborc said:**
> Ibex isn't LTS ... it is meant to have "exiting new things"... and if you delay Ibex like Dapper was delayed, the 9.04 edition will be like Edgy - pointless
LTS doesn't mean extra stability, it means longer support.

---

### Post by dupondje on 2008-09-05
NetworkManager 0.7 is the biggest disaster in Ubuntu 8.10 :( Saving static IP's doesn't even work ... A BASIC function :( Sad But True :(

---

### Post by Nullack on 2008-09-05
> **ntetreau said:**
> I don't mean to steal your thunder here but your point should be re-phrased: "There is the ability to set static IP addresses, but not when one wants to also set the maximum MTU".  Having the ability to set static IP in NM 0.7 is really great and has been working perfectly for me in all alphas. At least, for all those not using DHCP and, thus, using a static IP (without need to change MTU), NM 0.7 is a big step forward.

Assigning a static IP doesnt work between reboots and requires manual intervention, which is why I consider it broken.

---

### Post by Nullack on 2008-09-05
Some bugs by another person who was posting on the dev mailing list:

NM 0.7 Regression from 0.6.6 using VPNC plugin
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/262191](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/262191)
NM 0.7 Hard to fix if you have saved passwords for vpnc plugin (possible
others)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/262214](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/262214)
NM 0.7 GSM/3G signal strength is not reported by NM
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/262232](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/262232)
NM 0.7 VPNC plugin is missing option DNSUpdate No
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/262234](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/262234)
NM 0.7 Sony Ericsson P1i isn't recognized as a 3G modem
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/262399](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/262399)
NM 0.7 No option for connecting to L2TP IPSEC VPN
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/264691](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/264691)

---

### Post by far_star on 2008-09-06
With Alpha 5 here, I can't get networking to work at all on my wired ethernet unless I use DHCP. Editing the settings for IP/netmask, etc via NM are ignored. Setting them with ifconfig breaks DNS resolution. 

Wow, I can't believe they would deliver a build with such a glaring problem.

---

### Post by meborc on 2008-09-06
> **Exsecrabilus said:**
> LTS doesn't mean extra stability, it means longer support.

i didn't say that ;) i was referring to the delay in dapper and what it caused

---

### Post by tawmas on 2008-09-06
> **Nullack said:**
> Assigning a static IP doesnt work between reboots and requires manual intervention, which is why I consider it broken.

Try to create a directory named [FONT="Courier New"]/etc/NetworkManager/system-connections/[/FONT], it fixed it for me (and others as well). After you've done that, you'll need to create or edit your settings to have NM save them...

---

### Post by dupondje on 2008-09-06
> **tawmas said:**
> Try to create a directory named [FONT="Courier New"]/etc/NetworkManager/system-connections/[/FONT], it fixed it for me (and others as well). After you've done that, you'll need to create or edit your settings to have NM save them...

Doesn't solve for me

---

### Post by Nullack on 2008-09-06
> **beartard said:**
> Whose project it is hardly matters when it's not working.  Network Manager affects all the buntus.  I was just making the point that it's a larger problem than if it only affected gnome users.

It matters because its driven by the gnome schedule as its a gnome project.

---

### Post by doorknob60 on 2008-09-06
> **xerosis said:**
> At least it vaguely works for you guys, knetworkmanager doesn't even work with the 0.7 APIs ;)

I know, I found that out the hard way :lolflag: I was trying to get my well supported atheros card to connect for hours with alpha 5, even though it worked fine in alpha 4 :-P Then I installed Wicd and it worked no problem :)

---

### Post by Nullack on 2008-09-07
Im also noticing that NM is not shutting down clean on restarts.

---

### Post by ntetreau on 2008-09-10
nm-applet is now broken for me after today's update...

---

### Post by UbuWu on 2008-09-10
Can't connect to any wireless network anymore after today's update.

---

### Post by ntetreau on 2008-09-10
Good, back to normal after latest update!

---

### Post by BC7333 on 2008-09-10
> **ntetreau said:**
> Good, back to normal after latest update!

No static ip's when wired though..

---

### Post by [r4] on 2008-09-11
It might not be the most appropriate place to ask, but I'm deperate.

I updated my II (Intrepid Ibex) yesterday and after reboot, my network (wired Ethernet + DHCP) was dead. Note that was the first time my system used NM version 0.7.

I tried to reconfigure it, but to no avail. I uninstalled it, but now my Ubuntu doesn't seem to recognize any of the interfaces besides "lo". I am unable to connect to the network to fix this :)

I have tried to install previous version of Network Manager from 8.04 CD, but it didn't work either. Could any of you help me please?

---

### Post by Nullack on 2008-09-11
r4 look up the doco for ifconfig

Also you have the tools for diagnostics - ping, traceroute, nslookup etc

---

### Post by [r4] on 2008-09-11
> **Nullack said:**
> r4 look up the doco for ifconfig

Also you have the tools for diagnostics - ping, traceroute, nslookup etc

Thanks for quick reply. The problem is, my ifconfig doesn't seem to recognize eth0 (or any other, for that matter). I can't "up" the interface, not mentioning setting up any parameters. :)

That fact alone renders the rest of the stuff you mentioned useless, I'm afraid.

---

### Post by Nullack on 2008-09-11
In your kern.log is the nic being setup at all?

---

### Post by ntetreau on 2008-09-11
> **BC7333 said:**
> No static ip's when wired though..

Actually, I do have a fixed IP when wired.  It's been working fine for me since I install alpha 4.

---

### Post by BC7333 on 2008-09-11
> **ntetreau said:**
> Actually, I do have a fixed IP when wired.  It's been working fine for me since I install alpha 4.

Doesn't look like my network manager.. what am I missing?

---

### Post by yostral on 2008-09-11
It's not the Network Manager (the 2 screens close to the time at the right top corner), it's the "old and classic" network setup you find in your menu.

---

### Post by nanog on 2008-09-12
I think you are still running the "old" network manager.

Check your packages with synaptic or dpkg -l.

---

### Post by ntetreau on 2008-09-12
I have these installed:

```
+++-=================================-=================================-==================================================================================
ii  network-manager                   0.7~~svn20080908t183521+eni0-0ubu network management framework daemon
ii  network-manager-gnome             0.7~~svn20080907t033843-0ubuntu2  network management framework (GNOME frontend)


```

---

### Post by listener on 2008-09-12
Hesitant to post, definitely being the newbie here, but I'm running Intrepid on one of my two machines, since Alpha 4. It would not do the static IP at first, but updates corrected that pretty quickly for me.  It allows entering static and it saves and almost immediately connects through ICS on login, to the 8.04 which gets DHCP.

I'm also new to DSL, so I have not that much idea what I'm doing, nor what I may be doing right.  I suspect many of you do not have everything in your system you are supposed to?  

I have my own problems going on with it, but desktop effects just got corrected for me (compiz no longer crashes at login) and really enjoying it.  

bob

---

### Post by [r4] on 2008-09-12
> **Nullack said:**
> In your kern.log is the nic being setup at all?

Well, I can't check it right now (will do tonight), but I got another suggestion: to reconfigure NICs manually in ```
/etc/network/interfaces
```How about that? Could the problem lie in there?

---

### Post by BC7333 on 2008-09-12
> **yostral said:**
> It's not the Network Manager (the 2 screens close to the time at the right top corner), it's the "old and classic" network setup you find in your menu.

I wish they would add the version number in help or in the title bar.

Here's what I show in Synaptic

---

### Post by Nullack on 2008-09-12
Ive put my thoughts into release blockers which includes these. Remember folks, in this thread Steve talks about how we can make a difference:

[http://ubuntuforums.org/showthread.php?t=917646](http://ubuntuforums.org/showthread.php?t=917646)

---

### Post by hexion on 2008-09-13
You can always downgrade NM to the last 6.x version uploaded to Intrepid and then hold the packages.
That's what I did.

I know it's against the testing thing, but in case the final release is launched and it's a showstopper for a particular user, you can always do that.

---

### Post by [r4] on 2008-09-15
> **hexion said:**
> You can always downgrade NM to the last 6.x version uploaded to Intrepid and then hold the packages.
That's what I did.

I know it's against the testing thing, but in case the final release is launched and it's a showstopper for a particular user, you can always do that.

Yup, seems to me it is the only reasonable solution. :) Could this be a reliable source? ([https://code.launchpad.net/ubuntu/intrepid/i386/network-manager](https://code.launchpad.net/ubuntu/intrepid/i386/network-manager))

I am going to try this today. I'm tired of trying and editing millions of files. The only problem is that I cannot be sure if it helps (I mean, after editing all of these different files)...

---

### Post by jackocleebrown on 2008-09-15
Does anyone else have problems with NM 0.7 on alpha 5 not remembering WEP keys? Is this a known bug?

---

### Post by Bossieman on 2008-09-15
I have a really bad feeling about NM and II. The connections are all messed up. I use a E220 HSPA Turbo 3G modem and it connects and works but NM says its connected to a GPRS network! :(
There is not even possible to choose HSPA.

---

### Post by plun on 2008-09-15
> **Bossieman said:**
> I have a really bad feeling about NM and II. The connections are all messed up. I use a E220 HSPA Turbo 3G modem and it connects and works but NM says its connected to a GPRS network! :(
There is not even possible to choose HSPA.

Well, "help your self" maybe...:)  

The recognition is obviosly wrong and wrong terms are used. (bug filed)

What gives a speed test  ?   

World wide
[http://www.speedtest.net/](http://www.speedtest.net/)

(Sweden >  [http://www.bredbandskollen.se/](http://www.bredbandskollen.se/))

When I tested it was never more then 0.8 Mbits (down)  (3G, ISP-3)

I have also tried to find out if there are settings for USB baudrate, difficult to find out  !?

---

### Post by [r4] on 2008-09-16
Okay, I'm posting it here for future reference: I have downgraded Network Manager to version 0.6(.6, I think) and now it works. (Refer to the link I have given in my previous post).

All one have to do to get working network connection (if it was broken because of NM 0.7) is to uninstall and reinstall the following packages:
network-monitor
network-monitor-gnome
libnm-util0
(don't pay attention to that libnm-glib0 being uninstalled as well, it is unnecessary for NM 0.6).

If you prefer this old version over the newer one, keep those old packages in a safe place: my Ubuntu chose to overwrite them even despite the fact I froze them.

Does anyone actually know what is broken in NM 0.7? I get mixed reports here and there; but throwing away my wired Ethernet connection over DHCP is definitely a showstopper for me.

---

