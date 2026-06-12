---
title: "Apache security updates??"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by antiproduct on 2007-03-27
First off, sorry if this is in the wrong place, this is my first time posting in the forums. I tried searching for info on this matter and was unable to find anything.
I was doing a foundstone (security) scan on my ubuntu servers (I'm running 3 versions, 5.10, 6.06.1, and 6.10) and noticed that I get a critical vulnerability showing up for apache (and php 5.0.5-2 for my 5.10 system). I checked the apache site and noticed that the latest there is 2.0.59 featuring "an 'important' security patch to mod_rewrite." Sooo.... is this going to rollout in the automatic updates or am I just going to have to do a manual install and hope nothing breaks? 
Also, what about a php update for the 5.10 system? It'd be nice if there was still support for another month or so. My plan is to scrap the 5.10 and move to fiesty when it comes out next month, but wouldn't want my server to be hacked in the meantime.

Here's a list of the security vulnerabilities that foundstone informed me of:
[COLOR="Red"]Apache HTTP Server mod_rewrite Vulnerability [/COLOR]
[COLOR="Orange"]Apache HTTP Request Smuggling [/COLOR]
[COLOR="Red"]PHP HTML Entity Encoder Heap Overflow Vulnerability[/COLOR]
[COLOR="Orange"]PHP Security Multiple Bypass Vulnerabilities [/COLOR]

Thanks for any info.

---

