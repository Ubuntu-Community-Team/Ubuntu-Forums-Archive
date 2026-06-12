---
title: "`canonical-livepatch enable` fails"
date: 2019-06-14
forum: Installation &amp; Upgrades
---

### Post by dwater on 2019-06-14
Trying to enable livepatch using the command from [https://auth.livepatch.canonical.com/](https://auth.livepatch.canonical.com/), gives me:

```

09:30:30 ~$ sudo canonical-livepatch enable ~~~~~~~~~~~~~~~
2019/06/14 09:38:08 error executing enable: cannot enable machine: cannot send request: Post https://livepatch.canonical.com/api/machine-tokens: dial tcp: lookup livepatch.canonical.com on [::1]:53: dial udp [::1]:53: connect: cannot assign requested address
```

Software Updates says:

'You can use Livepatch to keep your computer more secure between restarts.',

 but when I launch it and select the 'Livepatch' tab, it is 'OFF' with the message 'Livepatch requires an internet connection.', and I can't turn it on.

I did a search for how you're supposed to turn it on, and [one page]("https://linuxhint.com/ubuntu_live_patch/") shows a screenshot of the `Software & Updates` window's 'Updates' tab, with some UI to allow you to log into Ubuntu One, but that isn't there for me.

Any ideas what might be wrong?

```
09:38:08 ~$ cat /etc/lsb-release
 DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.2 LTS"
09:39:41 ~$ uname -a
Linux davidmaxwaterman-XPS-13-9360 4.15.0-51-generic #55-Ubuntu SMP Wed May 15 14:27:21 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
09:39:42 ~$ 

```

---

### Post by jonnylinuxnerd on 2019-06-17
I also have come across this error and it's very frustrating and cryptic to figure out. The clue is in "dial tcp: **lookup** livepatch.canonical.com" and the reference to port 53 (which is the DNS port). in my case, livepatch was failing to lookup the DNS for livepatch.canonical.com on the internal loopback systemd-resolved server (which I believe should be at 127.0.0.53). However for whatever reason, canonical livepatch expects it to be on the normal loopback/localhost 127.0.0.**1** address. 

My workaround was to start unbound on 127.0.0.1 and then it could resolve the DNS and hey livepatch worked again. Kind of a ****** workaround solution and doesn't solve the internal issue in either Ubuntu's systemd config (which is new and I'm still getting to grips with) and/or Livepatch (or rather I expect something to do with Go's DNS resolver, as livepatch is written in Go I believe.) But for my purposes it worked enough. Let me know if my workaround works and maybe together we can put together a bug report that this happens sometimes and it didn't just happen to me randomly on one of my VPS's :P As this shouldn't be happening in the first place.

Edit: Oh and to confuse the issue even more, it appears to be trying to use the IPv6 loopback address, rather than the IPv4 loopback :P

---

### Post by dwater on 2019-06-17
HI,

Interesting...

I also noticed the IP6 thing, so I disabled that interface on my network, but it wasn't that if that was the problem so it had no effect. I guess I don't really know what I'm doing :)

As further evidence...what is 'start unbound on 127.0.0.1', and how does that translate to actual commands?

I hunted around for 127.0.0.53, and found it in /lib/systemd/resolv.conf, but changing that didn't seem to have any effect. I tried `sudo systemctl restart systemd-resolved` and rebooting, but it still didn't work...to test if it was working, I did `dig livepatch.canonical.com @127.0.0.1` (and also on .53, which always seemed to work).

I did have a VPN which seemed to get in the way some :/ I'll try to remember to not enable it, after rebooting, before I try it again.

---

### Post by jonnylinuxnerd on 2019-06-17
> **dwater said:**
> HI,

As further evidence...what is 'start unbound on 127.0.0.1', and how does that translate to actual commands?


Unbound is simply a completely separate DNS server/ resolver that I had installed (and you could do too with apt-get install). You shouldn't really need it if things are set up and configured properly in the first place, but in the case with my VPS it was running in a Docker container anyway, so I just exposed it on 127.0.0.1 as a workaround. By the sounds of it though 127.0.0.1 port 53 is resolving so maybe your problem is more to do with IPv6? Have you tried using sysctl commands (see  [https://www.techrepublic.com/article/how-to-disable-ipv6-on-linux/](https://www.techrepublic.com/article/how-to-disable-ipv6-on-linux/)) to completely disable it on ALL interfaces?

---

### Post by jonnylinuxnerd on 2019-06-17
And yes using a VPN will most likely be confusing/ complicating things for sure! They can also change DNS resolvers and not work for/ firewall IPv6 etc.

---

### Post by dwater on 2019-06-18
> By the sounds of it though 127.0.0.1 port 53 is resolving

I didn't think so...where did you get that from?

```

09:24:18 ~$ dig livepatch.canonical.com @127.0.0.1


; <<>> DiG 9.11.3-1ubuntu1.7-Ubuntu <<>> livepatch.canonical.com @127.0.0.1
;; global options: +cmd
;; connection timed out; no servers could be reached
09:26:28 ~$ dig livepatch.canonical.com @127.0.0.53


; <<>> DiG 9.11.3-1ubuntu1.7-Ubuntu <<>> livepatch.canonical.com @127.0.0.53
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 58524
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;livepatch.canonical.com.    IN    A


;; ANSWER SECTION:
livepatch.canonical.com. 454    IN    A    162.213.33.50
livepatch.canonical.com. 454    IN    A    162.213.33.49


;; Query time: 18 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Tue Jun 18 09:26:31 BST 2019
;; MSG SIZE  rcvd: 84

```

I tried to change it to 127.0.0.1, but the only reference I could find (outside of /run, which is overwritten, right?), is:

```

$ sudo grep -r 127.0.0.53 /lib
[sudo] password for davidmaxwaterman: 
Binary file /lib/systemd/systemd-resolved matches
/lib/systemd/resolv.conf:nameserver 127.0.0.53

```

...and changing that didn't seem to help. I'm not entirely sure I know how to restart the daemon that uses that file - I tried `$ sudo systemctl restart systemd-resolved`, but that didn't help, and neither did rebooting. I guess that file doesn't do what I thought it did.


Aha, now it's working...from a clean boot with never having enabled VPN...perhaps this livepatch thing simply doesn't work with VPN, and turning VPN off doesn't put the system back in the same state it was in before. I think I should probably contact my VPN provider...[I see they've released a new version, so I'm trying that].

---

### Post by jonnylinuxnerd on 2019-06-18
> **dwater said:**
> > By the sounds of it though 127.0.0.1 port 53 is resolving

I didn't think so...where did you get that from?

```

09:24:18 ~$ dig livepatch.canonical.com @127.0.0.1


; <<>> DiG 9.11.3-1ubuntu1.7-Ubuntu <<>> livepatch.canonical.com @127.0.0.1
;; global options: +cmd
;; connection timed out; no servers could be reached
09:26:28 ~$ dig livepatch.canonical.com @127.0.0.53


; <<>> DiG 9.11.3-1ubuntu1.7-Ubuntu <<>> livepatch.canonical.com @127.0.0.53
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 58524
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;livepatch.canonical.com.    IN    A


;; ANSWER SECTION:
livepatch.canonical.com. 454    IN    A    162.213.33.50
livepatch.canonical.com. 454    IN    A    162.213.33.49


;; Query time: 18 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Tue Jun 18 09:26:31 BST 2019
;; MSG SIZE  rcvd: 84

```



Apologies, misread! :lolflag: It seems indeed that livepatch cannot handle the situation where 127.0.0.1 is not available.

Glad to hear that you've solved the problem by disabling the VPN. It's probably messing with the firewall rules somehow. Still, I think this is something livepatch needs to handle better seeing as you clearly have internet connectivity still.:-k

---

### Post by dwater on 2019-06-18
Yeah, the error message is misleading, to say the least :)

I updated the vpn s/w, but it hasn't helped - though I did see the livepatch toggle in software updater come alive at one point, after disabling the vpn's dns option, but not any more. I think it really needs to be allowed to run right after a boot, before vpn is enabled even once.
I contacted the vpn provider and they said they're study what is happening there and attempt to get a fix out.

---

### Post by jonnylinuxnerd on 2019-06-18
It's probably being flaky depending on how often Livepatch tries to get a machine key (I know it checks for actual livepatch updates once an hour). Which is a long time to wait for a toggle switch to possibly start working again :P

---

### Post by jonnylinuxnerd on 2019-06-18
Tbf to your VPN provider I think it's more of a Ubuntu/ Systemd/ Livepatch issue than a VPN issue, seeing as I've encountered it on a machine that never ever used any kind of VPN. I'd be interested to here what they have to say though!

---

### Post by jonnylinuxnerd on 2019-06-18
Also DNS should resolve even with your VPN on (unless your VPN is explicitly blocking the lookup, which I doubt). This is the ****** livepatch DNS resolution issue I was on about :P

---

### Post by dwater on 2019-06-19
Well, my view is that there are two issues.
My usual work flow is to boot up the laptop and one of the very first things I do is open a terminal and enable the VPN (it's has a cli)...it's a habit. So, the icon for livepatch that appears at the top right of the screen is almost always 'broken'. If I disable the VPN, it remains broken, but perhaps it would fix itself after an hour, as you intimated - I've not bothered waiting. However, if I click on the icon and select 'Livepatch Settings', it opens 'Software & Updates' on the 'Livepatch' tab, and the toggle will then test itself and then toggle itself 'ON', and say 'Livepatch is on.'. However, the icon on the top of the screen remains broken - the UI in 'Software & Updates' doesn't seem to have a way to 'check now' or the like; but I see that the livepatch cli does - `sudo canonical-livepatch refresh` - and doing that then works:

```

Before refresh:


kernel: 4.15.0-52.56-generic
fully-patched: true
version: ""


After refresh:


kernel: 4.15.0-52.56-generic
fully-patched: true
version: ""

```

...and then the UI in 'Software & Updates' changes to indicate when it was last checked/etc, and the icon on the top of the screen goes 'green'. So, at this point, it seems to be working as designed.

So, as you've surmised, it seems to be an issue with the livepatch software DNS lookup - it seems to be specifying the DNS server to use for some reason, instead of using the one configured...in this case by the VPN. If I look up the address while connected to the VPN, it works just fine (162.213.33.[49,50]), but the UI in 'Software & Updates' then claims there is no internet connection.

I'm not sure about the whole '127.0.0.1' vs '127.0.0.53' issue - I think, maybe, it just looked like the same problem you're seeing. When connected via VPN, and I have its 'force_vpn_dns        true' set, then I don't get any DNS response from either 127.0.0.1 or 127.0.0.53, though I can ping both. I guess the VPN is doing its job then, but Livepatch is forcing use of 127.0.0.53 for some reason :/

Does that make sense?

---

### Post by jonnylinuxnerd on 2019-06-20
> **dwater said:**
> 

I'm not sure about the whole '127.0.0.1' vs '127.0.0.53' issue - I think, maybe, it just looked like the same problem you're seeing. When connected via VPN, and I have its 'force_vpn_dns        true' set, then I don't get any DNS response from either 127.0.0.1 or 127.0.0.53, though I can ping both. I guess the VPN is doing its job then, but Livepatch is forcing use of 127.0.0.53 for some reason :/

Does that make sense?


127.0.0.1 or 127.0.0.53 should always Ping as they're both localhost. However, it doesn't mean DNS is listening on both those (local) addresses. It used to be the case I believe that all DNS was done through a local dnsmasq instance (that would cache queries from your ISP/VPN) and that was on 127.0.0.1. However with sysetmd-resolved which has taken it's place, I believe the address is now listening at 127.0.0.53.

It's confusing as the caching servers exist as DNS servers in their own right, albeit only available to your local machine. If they were bypassed (and say livepatch went 8.8.8.8 directly or whatever your ISP DNS is) it wouldn't be a problem (apart from missing out on potential cache hits), but it appears livepatch client isn't even smart enough to do that and just completely gives up :P

---

### Post by michael-bielesky on 2019-10-16
Just FYI I have the same issue with Livepatch when I'm connected via nordvpn. The problem goes way once disconnected. Moreover, the connection icon in the left side of the upper GUI bar appears with a question mark few minutes into the connection, but the internet connection is not affected.


Mike

---

### Post by DinghySailor on 2020-07-05
I have the same issue on my fresh install of 20.04. 
I have installed 20.04 on two laptops within a week, and one has few issues, and the other has lots of issues, including this one.
Whether or not there is a VPN should be irrelevant. Livepatch SHOULD work over a VPN.

---

