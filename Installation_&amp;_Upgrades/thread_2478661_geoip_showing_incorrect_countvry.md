---
title: "geoip showing incorrect countvry"
date: 2022-09-01
forum: Installation &amp; Upgrades
---

### Post by gwi on 2022-09-01
Ever since switching internet provider, [geoip.ubuntu.com/lookup]("https://geoip.ubuntu.com/lookup") is showing USA as country. I am however living in the Netherlands, which was reported as my country before the switch.
The command [FONT=Courier New]curl --silent ipinfo.io[/FONT] is returning the correct information.

Why does the geoip service show incorrect information? One of the side effects of this is that in the package sources I see a list of American mirrors, instead of European mirrors.

I asked the internet provider, but they could not explain why this is happening.

If this is a problem on the geoip side, who should I contact to get it fixed?

---

### Post by TheFu on 2022-09-01
> **gwi said:**
>  If this is a problem on the geoip side, who should I contact to get it fixed?

It is.  Sometimes services have wrong data.  I assume you aren't using a VPN.  OTOH, you aren't being hassled for all the EU "privacy warning/confirmation" crap anymore, right?  If you agree to those terms all the time, there's no difference. But if you don't agree to those terms, life sucks if you are not asked and want to refuse.

There isn't just 1 geoIP DB.  There are hundreds.  Each has failures.  It is unlikely that single website saying you are in the US really matters.  If there is a specific service where you see issues, contact them. Of course, if you are actually paying for the service then their bills should include a support phone number/contact.

If you aren't paying, then probably the most effective way of contact is over twitter. Sad, but true.

---

### Post by gwi on 2022-09-01
If I visit a site in the EU I get the cookie messages. I don't see what it has to do with the geo ip issue.

The Ubuntu geoip service has an issue (or I have an issue with the Ubuntu geoip service showing incorrect results). How can that be fixed? It's a free service, so no bill showing a contact.

BTW: I am not using twitter.

---

### Post by TheFu on 2022-09-01
The specific geoip DB isn't owned by Ubuntu or Canonical. It is just a DB they use and might be F/LOSS. I don't know.  Since nobody here works for Canonical, you might try opening a bug report in landscape.  They might report the issue to their Geoip provider, but that is doubtful.  

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

The ubuntu geoip service is off 50 miles from my location.  Most of them are off at least 20 miles. The closest that I've seen was 2 miles about a decade ago.

Of course, when I'm using a VPN service, the geoIP shows the exit node location, which can be the main reason to use a VPN.

---

### Post by Doug S on 2022-09-02
I often get annoyed by different geo ip lookups giving different answers.

Example 1: I recently noticed a significant number of firewall of entries from 193.201.8.121. When I looked it up manually on [https://ipstack.com/](https://ipstack.com/) it said Russia - Moscow. I use [https://www.ipdeny.com/](https://www.ipdeny.com/) for my ipblock lists and block all of Russia with an ipset in iptables (my firewall), but that ip wasn't included. I downloaded all zones from ipdeny.com and couldn't find that ip address allocated to any zone.

Example 2: Similarly, for 143.92.32.15. ipstack said Hong Kong, but I also block all of Hong Kong. For ipdeny the country was Singapore.

---

### Post by TheFu on 2022-09-02
I think the real complaint from the OP is that the USA isn't anywhere near his actual country.
Lots of cities straddle international boundaries, so while the laws are often very similar, sometimes the pesky details change ... and the expectations of an end user that computer data is 100% correct, always, gets burst.

The OP was hoping that someone here actually worked for Canonical and could get them to fix the data. I can understand that expectation and hope the bug report in landscape can make that happen. I fear it will be marked as extremely low priority and not even be attached to whatever geoIP DB contract Canonical has, so the provider is at least notified.  OTOH, I'd expect they get 20K similar issues each month.  There are lots of addresses in the world.  Wrong country, should be a higher priority, IMO.

Definitely a 1st world problem.  I'm really happy that all my personal problems are similar ... well except the personality issues that have no fix for 45 more years (hopefully). ;)

---

### Post by Skaperen on 2022-09-02
also, many providers offer services in more countries than they have allocations from.  that could have resulted in many of the GEOIP errors.  once website learn that GEOIP is not accurate, they will stop using it.

the popularity of VPNs could have polluted the GEOIP databases, too.  IMHO, VPNs make GEOIP useless.

---

### Post by gwi on 2022-09-03
> **TheFu said:**
> The specific geoip DB isn't owned by Ubuntu or Canonical. It is just a DB they use and might be F/LOSS. I don't know.  Since nobody here works for Canonical, you might try opening a bug report in landscape.  They might report the issue to their Geoip provider, but that is doubtful.  

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

The ubuntu geoip service is off 50 miles from my location.  Most of them are off at least 20 miles. The closest that I've seen was 2 miles about a decade ago.

Of course, when I'm using a VPN service, the geoIP shows the exit node location, which can be the main reason to use a VPN.

20 or 50 miles off would be OK for me. A lot better than reporting a location at the other side of the planet. Reporting the correct country (or even continent) would allow me to select a nearby software mirror. I will report a bug in Launchpad.

---

### Post by TheFu on 2022-09-03
> **gwi said:**
> 20 or 50 miles off would be OK for me. A lot better than reporting a location at the other side of the planet. Reporting the correct country (or even continent) would allow me to select a nearby software mirror. I will report a bug in Launchpad.

You can selected any specific mirror that you like for most downloads, including Ubuntu repos.  The GeoIP isn't forced.

If this is really the root issue, it is a specific reason why explaining the final goal is best when asking questions in forums.  Someone could have told you how to change the APT repo files to point at a local mirror last week.

---

### Post by gwi on 2022-09-05
It's not limited to the repo's. That was just an example.
I am not in the USA but in the EU. The fact that geoip says my IP address is in the USA is a bug or an error IMHO.

---

### Post by TheFu on 2022-09-05
> **gwi said:**
> It's not limited to the repo's. That was just an example.
I am not in the USA but in the EU. The fact that geoip says my IP address is in the USA is a bug or an error IMHO.

Completely agree.

---

