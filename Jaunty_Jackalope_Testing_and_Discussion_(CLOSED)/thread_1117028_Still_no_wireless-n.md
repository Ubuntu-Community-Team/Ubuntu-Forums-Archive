---
title: "Still no wireless-n ?"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cdahmedeh on 2009-04-05
Hello,

I have a Intel Wireless 4965agn WIFI Mini-PCIE card in my laptop. I've notcied that I don't have wireless-n connectivity. This issue has existed previous versions of Ubuntu. Wireless-n worked fine in Windows, but non-existant in Ubuntu ? I can only get connect signals at 54Mbps and don't get the extra range from wireless-n. Anyone know how to enable Wireless-n in ubuntu ?

Thanks

---

### Post by hessczoo on 2009-04-05
Hey! i noticed this too. I have an Intel Wireless-N card, and a Wireless-N router and I don't get the speed, although I haven't tried the range, which I doubt I get it either.

---

### Post by cdahmedeh on 2009-04-05
It would be interesting if someone would shed some light on this issue...

---

### Post by syko21 on 2009-04-05
I think this is a case of misreporting. I had an intel 3945 before i upgraded to the 4965 and the speed, throughput, and range went up dramatically. Firefox downloads were going upwards of 1 MB/s on servers I never saw more than 500-600 KB/s before.

---

### Post by walmis on 2009-04-06
I get N speeds with iwl4965 + d-link dwa-547 pci card on a server running hostapd as an AP. The usual speed is about 5 MB/s, seen a few instances where it jumped to 10MB/s :)

---

### Post by cdahmedeh on 2009-04-07
Great to hear.. but how do I get wireless-n speeds ? Out-of-the-box it doesn't, is there some option that I need enabled to be able to do so ?  I really need to get n-speed/connection quality(allows for much better range).

Thanks

---

### Post by cdahmedeh on 2009-04-07
Bumping again, I really think this issue is to be solved. No resolutions on forum nor launchpad. In fact, n support isn't availaible in any Linux distribution I've tried : Fedora, Debian, Arch or Ubuntu. Also, any logs/dumps/information that I need to post to try to resolve this problem ?

---

### Post by Yashiro on 2009-04-07
Isn't the speed dictated by the driver for your device?

---

### Post by cdahmedeh on 2009-04-07
Indeed it probably is. The problem is that default (including backports) drivers don't include support for that.

---

### Post by dasme on 2009-04-07
> **cdahmedeh said:**
> Hello,

I have a Intel Wireless 4965agn WIFI Mini-PCIE card in my laptop. I've notcied that I don't have wireless-n connectivity. This issue has existed previous versions of Ubuntu. Wireless-n worked fine in Windows, but non-existant in Ubuntu ? I can only get connect signals at 54Mbps and don't get the extra range from wireless-n. Anyone know how to enable Wireless-n in ubuntu ?

Thanks

Same problem here getting less speed with 4965agn as compared to ethernet cable. In windows i get full speed.

Any1 knows how to fix this?

Thx

---

### Post by cariboo on 2009-04-07
I would suggest one of you create a bug report on [Launchpad]("http://bugs.launchpad.net/"). So that it can be pushed upstream to the kernel devs.

After all if the devs don't know there is a problem, they can't do anything about it.

Jim

---

### Post by Dougie187 on 2009-04-21
There was a bug for this a while ago, and I think it might even be there for Intrepid.

---

### Post by HankB on 2009-04-21
> **cdahmedeh said:**
> It would be interesting if someone would shed some light on this issue...
Something not obvious to me was that Wireless N does not support WEP security. So in my case when I had my AP set to use WEP, it seemed that it was pretty quiet about downgrading to G.

When I switched to WPA2, throughput went up. I wonder if others have also overlooked this because to me it seemed to be one of those things buried in the details. (It would have been useful for my router admin page to include a note about this or even disable WEP if I select N.)

HTH,
hank

---

