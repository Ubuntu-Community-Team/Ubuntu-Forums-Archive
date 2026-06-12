---
title: "http://us.archive.ubuntu.com  can't download updates"
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by acoluthus on 2008-10-26
Today I updated Heron (2nd time) as a measure to get to other prob's..

I've tried over the last few hours to download from the main site using the Update Manager and the "add-remove" feature and I only get the following message:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz-fusion-plugins-main/compiz-fusion-plugins-main_0.7.4-0ubuntu6_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz-fusion-plugins-main/compiz-fusion-plugins-main_0.7.4-0ubuntu6_amd64.deb)
  Could not resolve 'us.archive.ubuntu.com'

*I did enter one of these addresses and I could "go direct" (but not for 121files, thank you..)

So, is it an internal/my end that's not allowing this or something on the other end at the Archives?

-very- inexperienced, so keep it -simple- on the explanations,please.


thanks
AC

---

### Post by lemming465 on 2008-10-28
Try browsing the web from firefox.  If you can, the problem is likely with Ubuntu; wait 12-24 hours and try again,  It is possible to change repositories, but that's more complicated than you want to get into.

If firefox doesn't work, the problem is on your end somewhere.  "Could not resolve use.archive.ubuntu.com" is typically a DNS failure.  That could mean your ethernet cable is unplugged, your modem is turned off, your ISP is broken, or any number of other possibilities.  Use Applications -> Accessories -> Terminal to get a command shell window, enter "cat /etc/resolv.conf" and look for a line like

nameserver 11.22.33.44

If there aren't any such lines, the DHCP process isn't working properly.  If there is such a line, try "ping -c3 11.22.33.44", substituting whatever 4-part number you found.  That should produce output like:

PING 24.196.64.53 (24.196.64.53) 56(84) bytes of data.
64 bytes from 24.196.64.53: icmp_seq=1 ttl=61 time=8.29 ms
64 bytes from 24.196.64.53: icmp_seq=2 ttl=61 time=6.86 ms
64 bytes from 24.196.64.53: icmp_seq=3 ttl=61 time=8.28 ms

--- 24.196.64.53 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2007ms
rtt min/avg/max/mdev = 6.864/7.813/8.294/0.679 ms

Post the output from "ip addr; cat /etc/resolv.conf" and we'll try to be more specific.

---

### Post by forger on 2008-10-29
> **lemming465 said:**
>  It is possible to change repositories, but that's more complicated than you want to get into.


It's not that complicated to go to menu System > Administration > Software Sources >  Download from: "Main Server" or "Other" :)
Then click "Close" and "Reload"

---

### Post by acoluthus on 2008-10-29
HI 
and THANK YOU!! 
I will try these options as soon as I get home..
it seems that last night i could not even get online anymore at -all-; I got to this forum's home page once and then could get no further.
 it is a connectivity issue, but after reloading Heron, i lost more than I've gained.
 Thank you again, and I'll try these options and report back before closing the post.

*I'm actually printing your advice out from work and taking it home to try.. `hope to post tomorrow /Thurs. and will try to get access for your replies.. thanks greatly!

---

### Post by acoluthus on 2008-10-30
Lemming 465:
I had to hand-write the results; so hopefully I&#8217;m not a character off.
Also: I tried removing my RJ-jack from the cable modem in order to see if that defaults to the Modem, but in Network config panels it shows both options but kept defaulting to the RJ-&#8220;cable&#8221; connection. I reconnected the cable internet jack & retried; got same results:
Re: cat /etc/resolv.conf: 
&#8220;search.cable.rcn.com&#8221;
&#8220;nameserver 192.168.0.1&#8221;

Re:Ping attempt: 
&#8220;network unavailable&#8221;

Re: ip addr; cat /etc/resolv.conf  ..here goes:
1: lo:<Loopback, UP, Lower_Up> mtu 16436 qdisc noqueue
link/ loopback 00: 00: 00: 00: 00: 00: brd 00: 00: 00: 00: 00: 00:
inet 127.0.0.1/8 scope host lo
inetlo:: 1/128 scope host
valid_lft forever preferred_lft forever
5: etho: <BROADCAST, MULTICAST, UP, LOWER_UP> mtu 1500 qdisc pfifo_fast qlen1000
link/ether 00:30:1b:bb:6b:57 brd ff: ff: ff: ff: ff: ff:
inet6 fe80::230:1bff:febb:6b:57/64 scope link
valid_lft forever preferred_lft forever

searchcable.rcn.com
nameserver 192.168.0.1
(myname)@(myname)-desktop:~$

That&#8217;s everthing I tried last night. It&#8217;s cable modem to a router then to me.
Also, if I could just default to my dialup that&#8217;d be great too; I&#8217;d like to have that as my mainstay; saves me a lot of cash.
*Also: my roommate had no problems off of the same ISP cablemodem last night.
I kept trying lo and etho and fiddling with settings to get the dialup to work; it dialed out but never engaged.  I did get the settings-Properties for Serial Modem, loaded the local phone#, myID & password, etc, but still didn&#8217;t work.
I have &#8211;no- idea what the settings are supposed to be; before I updated I had the PPPGnome (which still didn&#8217;t work but at least I had the program)


Alternatively:if you&#8217;d recommend/if necessary, how do I select the 127 update/downloads that the System/package manager recommends, download them to burn and re-upload to my non-communicative CPU?
-or, same instance, how do I select individual packages and burn from a Windows (roommate&#8217;s) cd-r to be read/imported on my linux-only CPU?  -would that help?

Or-what&#8217;s the equivalent of a Setup Wizard for ubuntu/linux stuff? (or are we already doing these steps and I&#8217;m talking to the Wizards? :) 
Is there a way to &#8220;reset&#8221; the system to detect dialup modem(serial cable), and /or have the option for the RJ-45 jack when/if I get hi-speed internet again in the future?

Again, lead me on and I&#8217;ll follow through.. `should be back on maybe late tonight or Friday evening.
-with great appreciation,
AC

---

### Post by acoluthus on 2008-10-30
Forger:
`will try once I can get something to communicate; right now i have -no- connectivity; I was able to get on to "first pages" (g-mail, this forum..)then when I got the system update alerts that said failed connections w/ us.archive for ubuntu I tried the 'other' route under systems>--etc()and even tried a couple of direct-links from the error message list and got those single-files(but not for 127, no thanks).. now I can't get on line at all.  
`will try your advice once reconnected in -some- way.
Thanks.. any further suggestions appreciated.
`AC

---

### Post by lemming465 on 2008-10-30
There is no IPv4 address (xxx.yyy.zzz.www) assigned to your eth0 LAN interface, which suggests DHCP is failing.  Try powering off both your router and your cable modem, and then powering them back up.  The first try, leave them off at least 10 seconds, power up the cable modem, wait a minute, power up the router, wait a minute, and then reboot your computer.  If that doesn't restore network connectivity, try the same thing, only leaving them off for about 15 minutes instead of 10 seconds.

Some cable companies fixate on the ethernet address of the first device they see, and refuse to talk to others; it's possible they like your roommate currently.  Hence the suggestion of the 15 minute wait; that is often enough to overcome that.

Also, it might be worth tracing both ends of your ethernet cable to make sure it's plugged in properly, or trying a different ethernet cable (computer <-> router); connectivity problems can often be due to cabling issues.

I'd have to research the download elsewhere option; it's definitely doable, but not something I have personal experience with.

---

### Post by acoluthus on 2008-10-31
well, nothing really changed except reloading Heron; though afterwards I started fiddling w/ settings.
I will try the connectivity trace; though oddly enough I have a phone/isp provider coming out to replace the modem since I took off the coaxial phone service.. maybe i can snag them for a moment and go direct from the modem and see that-way.. though I still want to be able to use the copper-dialup modem anyway to save a few more$/month.
Open to suggestions on managing both connections..
Thanks!
A.C.

---

### Post by solitaire on 2008-10-31
This has been happening to me with the Global and GB repositories since yesterday!

You just leave it for 5 - 10 mins and try again. (if urgent) or ignore it till it autoupdates.

Probably servers being hit with all the new 8.10 downloaders :D

---

### Post by acoluthus on 2008-10-31
> **solitaire said:**
> This has been happening to me with the Global and GB repositories since yesterday!

You just leave it for 5 - 10 mins and try again. (if urgent) or ignore it till it autoupdates.

Probably servers being hit with all the new 8.10 downloaders :D
actually I'm totally offline now; since I reloaded Heron there's something else wrong and I cannot get online at all, anywhere.
thanks for the input/reply!

---

### Post by acoluthus on 2008-11-02
my cable internet ISP came out to replace the modem (since I disconnected coaxial telephone service)and he did a run-through; showed him my Ubuntu pc and he really couldn't do anything. I cannot get online at all; the problem is in my PC/with Ubuntu ? - unknown. My roommates can get online and is how I"m posting now.
I lost all my bookmarks and probably more when I reloaded Heron.(see previous posts- I don't have many- for details)
Just when I reloaded Heron as per the advise given ,the us.archive server was too busy, / got failure messages, and then I couldn't access it at all, then I couldn't get on-line either. I have basic Heron, and not the recommended update package of 127 files because I can no longer get online to get them. 
Also, I cannot get the linux friendly external modem to work either. 
Please see other posts; same running problems cumulatively for a year since my iMac 9.1 died. Now: no internet access, while others on PC XP &Vista laptop from the same router & ISP are connected.
How do I re-set/re-wire/re-program-whatever to unscrew what I did?  And I don't know what I'm doing in the first place. 
Assistance or recommendations please!

---

### Post by acoluthus on 2008-11-10
continued issues/info on:
[http://ubuntuforums.org/showthread.php?t=973101](http://ubuntuforums.org/showthread.php?t=973101)

thank you!!

A.C.

---

### Post by toppervergara on 2009-06-05
if you right click your internet icon on the top right portion of the panel the enable networking should be checked. just my 5 cents worth happened to me once before.

---

