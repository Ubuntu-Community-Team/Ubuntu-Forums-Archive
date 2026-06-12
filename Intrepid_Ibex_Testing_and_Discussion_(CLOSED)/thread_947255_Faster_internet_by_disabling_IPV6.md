---
title: "Faster internet by disabling IPV6?"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bobnutfield on 2008-10-14
Hello Everyone,

I am getting painfully slow internet with Intrepid.  I have an (supposedly) 8mbit broadband connection with my internet provider, but I can achieve only about 100kb download speeds, and it often drops the speed to well below 30kb.

In Hardy, I never bothered disabling IPV6 in /etc/modprobe.d/aliases because speed didn't seem to be an issue.

I am just wondering if anyone has actually improved their internet speed by disabling IPV6 as it is my understanding is that it only affects DNS, which of course once resolved shouldn't be an issue.

Thanks for any comments.

---

### Post by TenPlus1 on 2008-10-14
Try going here and testing your line speed:

[http://www.speedtest.bbmax.co.uk/](http://www.speedtest.bbmax.co.uk/)

also, tweaking programs such as Firefox and Deluge you can achieve higher download speeds...

<-- 2mb line, can get 254kbp/s no problem...

note: which provider are you with and do they cut your line speed at a certain time of the day like VirginMedia does ?

---

### Post by philinux on 2008-10-14
What firefox tweaks did you do?

---

### Post by bobnutfield on 2008-10-14
Hi, TenPlus1.  Yes, I have been to that site and tested.  I am with BTInternet (have been for years), and as far as I know they do not cut download speeds.  I use a Belkin 54g router and used to get 700-800kb of download speed.  My my wife's Windows laptop still gets that kind of speed.  I have read that disabling IPV6 improves download speeds but I cannot understand how it could if it only affects DNS.  What tweaks would you make to Firefox?

---

### Post by philinux on 2008-10-14
I'm with tiscali uk on an upto 8meg line.

Just tested and got ~5meg download speed. I'm 1 kilometer from the exchange.

---

### Post by bobnutfield on 2008-10-14
> **philinux said:**
> I'm with tiscali uk on an upto 8meg line.

Just tested and got ~5meg download speed. I'm 1 kilometer from the exchange.


Would give a shiny new nickel for that kind of speed.  By the way, did you disable IPV6?

---

### Post by philinux on 2008-10-14
> **bobnutfield said:**
> Would give a shiny new nickel for that kind of speed.  By the way, did you disable IPV6?

No not tweaked anything by blacklisting etc. I did try it in the past and it made no difference. 

I did tweak pipelining though. But again I'm not sure it really made any diff.

---

### Post by bobnutfield on 2008-10-14
Thanks, never have tweaked about:config, and usually the defaults are just fine.  I am suspecting my router now, as I only get 209KB/ps on my desktop which is a wired connection.  That is why I was questioning whether anyone had achieved better performance with IPV6 disabled.

---

### Post by philinux on 2008-10-14
Yes Bob I'd look at the router settings.

---

### Post by ViRMiN on 2008-10-14
I've not disabled IPV6 and still max-out my connection (around 14Mbps)

---

### Post by ronacc on 2008-10-14
the effect I get from disabling IPV6 is that sites START to load much faster , my ISP does not play nice with IPV6 and if I do not disable it there is a very long lag between the time I click on a link or open a bookmark and the time the page starts to load , once it starts the speed is normal.

---

### Post by bobnutfield on 2008-10-14
> **ronacc said:**
> the effect I get from disabling IPV6 is that sites START to load much faster , my ISP does not play nice with IPV6 and if I do not disable it there is a very long lag between the time I click on a link or open a bookmark and the time the page starts to load , once it starts the speed is normal.

Yes, that supports the information I had that IPV6 only affects DNS.  Once DNS is resolved, speed of the connection is not affected.  But, since I have never disabled it (in Ubuntu anyway, I have in other distros), I wondered if anyone else had any luck with speed.

Thanks for that.

---

### Post by yorkie on 2008-10-14
Hi
I had the same problem  a couple of moths ago slow speeds. I tried everything all the tweaks but no joy had to call virgin media engineer out turs out faulty power unit even though it seemed o`k replaced unit everything o`k last thing

---

### Post by bobnutfield on 2008-10-14
> **yorkie said:**
> Hi
I had the same problem  a couple of moths ago slow speeds. I tried everything all the tweaks but no joy had to call virgin media engineer out turs out faulty power unit even though it seemed o`k replaced unit everything o`k last thing

I don't know how Virgin media is set up.  I am using a my own Belkin wired/wireless router (not using BT equipment, not linux friendly), so that probably wouldn't fix my problem.  I am, however, suspecting some set-up with Linux is causing the problem as my wife's XP laptop gets good speeds.  It is not Ubuntu specific, I do not believe, as I am triple booting this laptop with Intrepid, Fedora 10, and Slackware with kernel 2.6.27.  Since the same kernel is being used by all three distros, it may be something in the kernel.

---

### Post by bobnutfield on 2008-10-14
For anyone interested, I have now edited /etc/modprobe.d/aliases to disable IPV6 and it appears to have had no affect at all.  Will continue testing.

EDIT:  I spoke too soon.  I tested from here:

[http://www.speedtest.bbmax.co.uk/]("http://www.speedtest.bbmax.co.uk/")

and the results were similar to before editing.  However, since I have had time to actually browse the net for a while, pages are now opening considerably faster.  The real test will be to download a large file.  Will report back.

FINAL EDIT:  OK, downloaded a large update, and noticed two things:

   1.  The actual download speed had not changed. Still approximately 109KB/second.  But....
   2.  I was getting a wide varying range of speeds during downloads of about 30KB/second to 209KB/second, but after the edit, the download speed is constant and unchanging, stable.  The pages on the net DO open much more quickly and browsing is much smoother.

Conclusion:  Even if editing and turning off IPV6 doesn't give you greater download speeds, it will (at least for me) stabilize your connection and make browsing quicker and smoother.  So it is worth the edit.

---

### Post by ronacc on 2008-10-14
just for info , I also blacklist IPV6 in /etc/modprobe.d/blacklist as well as disabling it in aliases . 
also in another thread here someone was able to get some pages to load that were a problem by lowering his MTU , you might give that a try to see if it does anything , IIRC the value he used was 1430 .

---

### Post by raptor2552 on 2008-10-14
In the US I was supposed to have a 15 Mbit connection but at best made ~100k. Turned out Road Runner made some changes incompatible with the modem I had. After changing the modem I'm now up to speed. 

A check with your provider may prove useful.

---

### Post by bobnutfield on 2008-10-14
Thanks, but I am using a simple ADSL modem/router, which is up to speed in XP, so there hasn't been any changes from the provider.  I'll keep testing, but turning off IPV6 has helped greatly.

---

