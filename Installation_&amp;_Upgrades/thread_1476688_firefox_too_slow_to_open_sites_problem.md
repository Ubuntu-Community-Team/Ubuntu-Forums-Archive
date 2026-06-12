---
title: "firefox too slow to open sites problem"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2010-05-08
I am using lucid has anybody experience that Firefox is slow to open sites ?
I have this problem, any help ?

---

### Post by P4man on 2010-05-08
Try disabling IPv6
[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

---

### Post by hoboy on 2010-05-08
> **P4man said:**
> Try disabling IPv6
[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

I have tried it it is still very slow.
this is waht I use.
Linux ubuntu 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

---

### Post by P4man on 2010-05-08
IF you download a file, is the speed of the download normal or not? Is this a wireless or wired connection?

---

### Post by hoboy on 2010-05-08
> **P4man said:**
> IF you download a file, is the speed of the download normal or not? Is this a wireless or wired connection?

When I download something the speed is fine, it is bough wireless and wired
connection.
Firefox is just very slow to connect

---

### Post by dave37 on 2010-05-08
I've been experiencing the same thing, downloads and speed tests are fine, but some sites are painfully slow to open or some of the images only partially load.  Hitting refresh several times sometimes causes all the images to load, sometimes not.  The problem sites display fine using firefox in windows, and IE.  It also works fine on another Ubuntu 8.04 workstation, just the one workstation is a problem.

---

### Post by jerenept on 2010-05-08
Try Epiphany- superfast opensource browser in the Software Center.

---

### Post by pmerner on 2010-05-08
> **dave37 said:**
> I've been experiencing the same thing, downloads and speed tests are fine, but some sites are painfully slow to open or some of the images only partially load.  Hitting refresh several times sometimes causes all the images to load, sometimes not.  The problem sites display fine using firefox in windows, and IE.  It also works fine on another Ubuntu 8.04 workstation, just the one workstation is a problem.

I have got what appears to be a good install of the final release of 10.04 using the ISO image burned to a boot CD. Only problem I have encountered is that Firefox is either slow or freezes entirely when an attempt is made to access the Firefox menu, Edit, File, etc.

I was wondering whether a fresh install on top of the existing one might be appropriate here?

I went to [http://www.ubuntugeek.com/how-to-fix-firefox-slow-problem-in-ubuntu-10-04lucid.html](http://www.ubuntugeek.com/how-to-fix-firefox-slow-problem-in-ubuntu-10-04lucid.html) and followed the instructions. Had to reboot but then it was all good. Not sure at this point whether the disableIPv6 becoming "True" was what did the trick or not. But how would I have been able to edit the config file for Firefox if Firefox itself was broken?

---

### Post by hoboy on 2010-05-08
Bumps

---

### Post by P4man on 2010-05-08
if download speeds are normal, then its probably either a DNS or IPv6 problem. Start by disabling IPv6 (unless you know you need it, which is unlikely):

[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

If that doesnt help, try setting your DNS servers to google's DNS (8.8.8.8 and 8.8.4.4). Some ISPs have crappy DNS servers that dont play nice with linux.

---

### Post by infamous-online on 2010-05-08
> **jerenept said:**
> Try Epiphany- superfast opensource browser in the Software Center.

Or try Opera, it loads fast even on this old IBM I'm on now!

---

### Post by wm_brant on 2010-05-09
I had the same issue with Firefox (FF).  However, opening sites was not the issue for me, it was the slow display of content  from sites that I noticed.

One of the fixes linked to above has you just shut off IPv6 in FF.  That is easy, and did the trick for me.

Type "about:config" into the address bar and press enter.  After a warning you get a pretty blank screen.  

Search for "network.dns.disableIPv6" (control-F). One line should be displayed.

Right click on that line and select 'Toggle' from the pop-up menu.  That fixed it for me.

---

### Post by wkulecz on 2010-05-11
What are your DNS lookup times?

In a terminal window give the following command:
```

data && nslookup msdn.com && date
```


At home its instantaneous, at work its 4-5 seconds.  Have had this issue in the 10.04beta (although I never tried the beta at home).  It has come and gone and come again in 9.10 across various updates, but I pretty much quit playing with 9.10 once 10.04Beta came out.

If your DNS lookups are fast try the about:config Firefox suggestions, if they are slow, this is your problem too -- most modern web pages do several DNS lookups in the process of rendering.


The Ubuntu launchpad powers that be have declared it "broken routers"  But since at work Ubuntu 6.06 & 8.04, Windows 2000 XP Vista & Win7, and MacOS machines on the same subnet all have no such issues,  its gonna be a real tough sell to get our networking powers that be to spend any money to fix this even if the Ubuntu folks are indeed correct (which I find incredibly hard to believe).

--wally.

Edit:
Followup, the command:
```
sudo su -
echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6
```

makes no difference to my DNS look up times.  Actual page loading or downloads after the DNS look up is fast.

---

### Post by wkulecz on 2010-05-11
> If that doesn't help, try setting your DNS servers to google's DNS (8.8.8.8 and 8.8.4.4). Some ISPs have crappy DNS servers that don't play nice with linux.

date && nslookup msdn.com 8.8.4.4 && date

Still takes 5 seconds here even after setting the /proc ipv6 disable :(

Edit:
More followup, doing: 

date && nslookup 8.8.8.8 && date

in a Cygwin window on a Windows 2000 box on the same subnet takes 2 seconds, but that delay is a reverse lookup failure to get the name of 8.8.8.8 which Linux is not doing

---

### Post by P4man on 2010-05-12
what happens when you ping 8.8.8.8 ?

---

### Post by moodle on 2010-05-13
I have the exact same problem.  Download speed is fine, but web pages take 3-10 seconds to load in firefox.  I want to use firefox.

On my same PC (2gb RAM), firefox works at lightening speed in Windows Vista.

---

### Post by wojox on 2010-05-13
[Try this]("http://ubuntuforums.org/showthread.php?t=1467763")

---

### Post by wkulecz on 2010-05-13
> what happens when you ping 8.8.8.8 ?

Instant ~47 mS responses.

data && nslookup msdn.com 8.8.8.8 && date still shows a 5 second delta :( it ran closer to four seconds on 9.10.


> Try this

Wrong issue.  Problem I'm having is that DNS lookups are really slow, you aren't going to fix it by dicking around with Firefox.

If your browsing is slow, try the date && nslookup && date command I've posted to time it.  If its fast tweaking Firefox would be your only hope, but if the DNS lookup is slow you are hosed for all net usage -- I can clearly see the namesuerver lookup delays when doing apt-get update :(

---

### Post by Skaperen on 2010-05-13
While it is possible to work around this problem, the real cause is a modification to the DNS resolver library that was made somewhere since Debian (since a test with a plain Debian installation showed this to not be happening).  Also to blame is the design/implementation of the resolver library that provides only a one-way feature.

Background.

The transition to IPv6 involves a new address lookup type in DNS.  A new record type called AAAA carries IPv6 addresses.  There is no way to get both the IPv4 address and IPv6 address at the same time.  Lookup requests must be for one or the other.  The "ANY" request type will not reliably perform this function, since it will be considered successful by a DNS cache server even if a partial set of records exist (e.g. if the previous request that populated the cache was for IPv6's AAAA records, the next request for "ANY" only gets the AAAA records and no recursion to get IPv4's A records is performed).

The resolver library code runs when programs use the standard socket calls to look up IP addresses.  It is possible to select which address family to request, but this is a programming (or configuration, if the program delegates to that) decision.

The resolver code reads the file /etc/resolv.conf for configuration.  This config file includes options, and one of these options is called "inet6".  Do "man resolv.conf"  in a terminal shell to read about this.  This option tells the resolver to perform IPv6 lookups first, before the IPv4 lookups, for programs that support IPv6 (almost all do, now).  The problem with this design is there is no configuration option to turn this OFF.  There is no "noinet6" or "inet4" option.

Someone modified the resolver library code for Ubuntu 9.10 and 10.04 to make "option inet6" be the default.  Maybe they didn't think about the consequences of that decision.

For a hostname which has NO AAAA records, this will have very little, probably not noticed, impact.  The query for AAAA records will be quickly responded to with a failure answer indicating no such records are available.  Then a query for A records is made, and that should succeed.

For a hostname which does have AAAA records, because that site does have IPv6 connectivity, the big delay will happen.  The query for the AAAA record will succeed.  The program, such as a web browser, will now attempt to connect to that IPv6 address.  It will fail unless the connecting client computer has real IPv6 connectivity.  It will time out.  Then it will query for the A record and try an IPv4 connection.  But this can take a few to several seconds.

The transition to IPv6 will be a bumpy one because there is no way to make ONE request in DNS for "both IPv4 and IPv6 at the same time".  The approximation to this is the v4-in-v6 addresses, but sites with genuine IPv6 addresses won't use that since it defeats having IPv6 in the first place.

If your computer has IPv6 disabled, then the resolver won't query for AAAA records.  So that is a solution most people can use.  If you have limited IPv6 (for example you are testing IPv6 within your LAN to become ready for IPv6 connectivity), you probably can't disabled it.  Or maybe you do have IPv6 over a slower tunnel that you don't want to just casually be using, but still want to use it for certain cases.

I have discussed this situation on IRC and found people willing to run a test scenarion with other systems.  Only Ubuntu experiences this problem.  Debian, Fedora, FreeBSD, and Slackware did not experience this problem.

If whoever made this change had been wise enough to do it another way, by putting "option inet6" into the /etc/resolve.conf file, then we could have fixed this by just taking that out.  Or if they had added a new "option noinet6" or "option inet4" when they modified the code, then we could have fixed this by using those options.

This is a feature that will be a good thing for those with IPv6 connectivity.  But it's something that should only be enabled in those cases.  Not everyone has IPv6, yet.  And many who do have only limited bandwidth over tunnels.  Some ISPs are working out the transition (e.g Comcast in the USA).  Many others are dragging their feet (e.g. Verizon in the USA).  It can still be a long time before IPv6 works for everyone. It will be even longer before IPv4 begins to fade out.

Have fun!

---

### Post by hoboy on 2010-05-13
> **skaperen said:**
> while it is possible to work around this problem, the real cause is a modification to the dns resolver library that was made somewhere since debian (since a test with a plain debian installation showed this to not be happening).  Also to blame is the design/implementation of the resolver library that provides only a one-way feature.

Background.

The transition to ipv6 involves a new address lookup type in dns.  A new record type called aaaa carries ipv6 addresses.  There is no way to get both the ipv4 address and ipv6 address at the same time.  Lookup requests must be for one or the other.  The "any" request type will not reliably perform this function, since it will be considered successful by a dns cache server even if a partial set of records exist (e.g. If the previous request that populated the cache was for ipv6's aaaa records, the next request for "any" only gets the aaaa records and no recursion to get ipv4's a records is performed).

The resolver library code runs when programs use the standard socket calls to look up ip addresses.  It is possible to select which address family to request, but this is a programming (or configuration, if the program delegates to that) decision.

The resolver code reads the file /etc/resolv.conf for configuration.  This config file includes options, and one of these options is called "inet6".  Do "man resolv.conf"  in a terminal shell to read about this.  This option tells the resolver to perform ipv6 lookups first, before the ipv4 lookups, for programs that support ipv6 (almost all do, now).  The problem with this design is there is no configuration option to turn this off.  There is no "noinet6" or "inet4" option.

Someone modified the resolver library code for ubuntu 9.10 and 10.04 to make "option inet6" be the default.  Maybe they didn't think about the consequences of that decision.

For a hostname which has no aaaa records, this will have very little, probably not noticed, impact.  The query for aaaa records will be quickly responded to with a failure answer indicating no such records are available.  Then a query for a records is made, and that should succeed.

For a hostname which does have aaaa records, because that site does have ipv6 connectivity, the big delay will happen.  The query for the aaaa record will succeed.  The program, such as a web browser, will now attempt to connect to that ipv6 address.  It will fail unless the connecting client computer has real ipv6 connectivity.  It will time out.  Then it will query for the a record and try an ipv4 connection.  But this can take a few to several seconds.

The transition to ipv6 will be a bumpy one because there is no way to make one request in dns for "both ipv4 and ipv6 at the same time".  The approximation to this is the v4-in-v6 addresses, but sites with genuine ipv6 addresses won't use that since it defeats having ipv6 in the first place.

If your computer has ipv6 disabled, then the resolver won't query for aaaa records.  So that is a solution most people can use.  If you have limited ipv6 (for example you are testing ipv6 within your lan to become ready for ipv6 connectivity), you probably can't disabled it.  Or maybe you do have ipv6 over a slower tunnel that you don't want to just casually be using, but still want to use it for certain cases.

I have discussed this situation on irc and found people willing to run a test scenarion with other systems.  Only ubuntu experiences this problem.  Debian, fedora, freebsd, and slackware did not experience this problem.

If whoever made this change had been wise enough to do it another way, by putting "option inet6" into the /etc/resolve.conf file, then we could have fixed this by just taking that out.  Or if they had added a new "option noinet6" or "option inet4" when they modified the code, then we could have fixed this by using those options.

This is a feature that will be a good thing for those with ipv6 connectivity.  But it's something that should only be enabled in those cases.  Not everyone has ipv6, yet.  And many who do have only limited bandwidth over tunnels.  Some isps are working out the transition (e.g comcast in the usa).  Many others are dragging their feet (e.g. Verizon in the usa).  It can still be a long time before ipv6 works for everyone. It will be even longer before ipv4 begins to fade out.

Have fun!

That was bad news

---

### Post by (^_^)Smiley on 2010-05-13
Firefox in linux is insane slow on loading a page takes 1 minute, also firefox is very heavy on ram and crashes to much.
I hope they will fix the problems because firefox is my favorite browser. I´m now using Opera it´s very fast and light the bad thing about Opera is it doesn´t have addon support.

---

### Post by Splork on 2010-05-13
@Skaparen - OK, IPv6 runs fine under my MS Windows XP OS, as soon as I boot Lucid Lynx all hell breaks loose and the only site I can navigate 100% is [www.google.com](www.google.com), all other sites that I can browse are the ones that stem off of a google search, that are cached and can be viewed in a text-only version.

So, how can I totally disable IPv6 on my Ubuntu? Honestly, I'm about to admit defeat and stroll over to my wife and tell her she was right.... NOOOOOOOOOO!!! :(

Otherwise I'll just install a distro that doesn't support IPv6, like you mentioned...

---

### Post by hoboy on 2010-05-13
I have just installed Opera that seem to do the job for me.

---

### Post by wojox on 2010-05-13
Just disable ipv6 [http://wojox.homelinux.org/?p=46](http://wojox.homelinux.org/?p=46)

And set your DNS servers to google's

---

### Post by hoboy on 2010-05-13
> **wojox said:**
> Just disable ipv6 [http://wojox.homelinux.org/?p=46](http://wojox.homelinux.org/?p=46)

And set your DNS servers to google's

OOOOOOO how come people know thinks like that ???????
tks

---

### Post by JohnDoe365 on 2010-05-19
Well, I do not think that the speed issue is related to IPv6 as IPv6 will AFAIK only be used as long as an IPv6 router is detected. You will wittness that IPv6 is disabled during system bootup when no IPv& router is detected, watch dmesg.

Currently the forum is full of complaints about WiFi speed, and it's not hardware  related, at least not to a single chipset. As it seems to me it is a  WiFi subsystem or even kernel regression.

Try the following:

When speed is slow: disable WiFi
re-enable WiFi and wait for re-association with AP. Is speed back to  normal?

Also see [http://ubuntuforums.org/showthread.php?t=1473022&page=3](http://ubuntuforums.org/showthread.php?t=1473022&page=3) and  [http://ubuntuforums.org/showthread.php?t=1487039](http://ubuntuforums.org/showthread.php?t=1487039)

If it has helped, it won't last for long, speed drops back to painful  slow after some time.
Consider assigning yourself to
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/581936](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/581936) 
to raise awareness.

---

### Post by mixtri on 2010-05-19
That is very strange as my Internet connection worked fine prior to upgrading to Ubuntu 10.04. I have deactivated ipv6, i can honestly say that I do not notice any change in my connection speed.

---

### Post by JohnDoe365 on 2010-05-19
Do you mean by that

* it is still slow
or
* disabling IPv6 brought back speed?

If it's still slow, try disabling and re-enabling Wifi. Now fast?

---

### Post by mixtri on 2010-05-19
As in disabling ipv6 did not make a difference. still slow. I have a wired connection, not even tried wifi yet.
Just tried this tut [http://www.ubuntugeek.com/how-to-fix-firefox-slow-problem-in-ubuntu-10-04lucid.html](http://www.ubuntugeek.com/how-to-fix-firefox-slow-problem-in-ubuntu-10-04lucid.html), not sure its made much of a difference.
Is there anyway of rewinding/rolling back the upgrade: (to 10.04lts) to the previous working state?

---

### Post by mixtri on 2010-05-19
I have also lost my volume icon; usually top left panel by date @ time. i can't seem to reenable it when choosing sound from system-preferences-sound

---

### Post by kamikazepsi on 2010-05-19
i had this issue for the first few months of 9.10 karmic koala.

firefox ran fine in 8.04, 8.10, 9.04 and 10.04

none of the config changes helped at all.  

a few months later, the issue fixed itself in 9.10 through updates i assume. 


but anyways, during that period, i switched to google chrome beta and haven't looked back. great browser that's extremely stable for being in beta.

---

### Post by JohnDoe365 on 2010-05-19
@[mixtri]("http://ubuntuforums.org/member.php?u=311273"): Thank you to affirming my observations that this is for most people not IPv6 related.

On a sidenote I wittness a lot of people beeing disappointed with this LTS release .. me personally too.

---

### Post by moodle on 2010-05-20
According to the Mozilla forums, this is a problem with Firefox 3.6.

See:

[http://support.mozilla.com/tiki-view_forum_thread.php?comments_parentId=658535&forumId=1](http://support.mozilla.com/tiki-view_forum_thread.php?comments_parentId=658535&forumId=1)

---

### Post by AryHann on 2010-05-23
Hi, 

I suffer of the same issue.
I have tried to load two sites both with Chrome and Firefox.
Even though it is not exactly smooth with Chrome, it works, while Firefox grays out and becomes useless and I could see the CPU frying :)
On Ubuntu KK I had to make some fixes to the graphics card parameters since there is some incompatibility between that and flash, however, this doesn't appear to be at all related to the graphics card (Chrome would have not worked) and not to the internet connection either.
I am from Ethernet cable and I can open pages quite fast, however, it simply hangs on heavy jpeg/flash rich pages.
(I have already made the ipv6 change)

---

### Post by P4man on 2010-05-23
Try launching firefox in safemode:

```
firefox -safe-mode
```

and/or with a fresh profile

```
firefox -profilemanager
```

---

### Post by kamikazepsi on 2010-05-25
> **AryHann said:**
> it simply hangs on heavy jpeg/flash rich pages.


if you're on a 64 bit machine, get rid of the 32 bit flash and install flash 10 beta 64 bit. it makes a world of difference.

---

### Post by AryHann on 2010-06-02
I am on a 32-bit computer.

Firefox has become also deadly slow in opening gmail!
Hence, I have decided to switch to Chrome. 

It seems many people have problems with Firefox on 10.4

---

### Post by Johan Gambolputty on 2010-06-28
This suggestion fixed it for me:


[http://ubuntuforums.org/showthread.php?t=1467763](http://ubuntuforums.org/showthread.php?t=1467763)

ie go to about:config and change the following:

- network.http.pipelining > Make it True
- network.http.pipelining.maxrequests > Make it 8 or 10
- network.http.proxy.pipelining > Make it True
- network.dns.disableIPv6 > Make it True

(I had already done the disableIPv6 thing to no effect, but doing all those together and restarting firefox have made it snappy again - can't believe this made it into an ubuntu LTS release and has taken so long to figure out)

---

### Post by Johan Gambolputty on 2010-06-28
> **Johan Gambolputty said:**
> This suggestion fixed it for me:


[http://ubuntuforums.org/showthread.php?t=1467763](http://ubuntuforums.org/showthread.php?t=1467763)

ie go to about:config and change the following:

- network.http.pipelining > Make it True
- network.http.pipelining.maxrequests > Make it 8 or 10
- network.http.proxy.pipelining > Make it True
- network.dns.disableIPv6 > Make it True

(I had already done the disableIPv6 thing to no effect, but doing all those together and restarting firefox have made it snappy again - can't believe this made it into an ubuntu LTS release and has taken so long to figure out)

That's weird, the first few sites I checked went very fast, but now maybe 1-2 hours later its back to crawling... hope someone finds the answer and fast. Seriously considering chrome now.

---

### Post by Johan Gambolputty on 2010-09-16
> **Johan Gambolputty said:**
> That's weird, the first few sites I checked went very fast, but now maybe 1-2 hours later its back to crawling... hope someone finds the answer and fast. Seriously considering chrome now.

Really have solved it now. The problem was not firefox/chromium/ubuntu/linux but NETWORK.

I had a wireless router dhcp'ing on 192.168.10.X
Due to fairly frequent network provider changes, I was in the habit of plugging this into their routers as they arrived, so I did not need to change all the WPA/network settings on all the computers in the house.

Well, after installing the latest firmware on my wireless router (last attempt at solving the problem) it automatically changed its settings to 10.0.0.X so I reset all the networking on all my machines again with the new network and now everything is blazingly fast.

So if you are running chained routers, both on differing 192.168 subnets and dns lookups are sporadically very slow, you may be having the same problem I was.

Good luck):P

---

