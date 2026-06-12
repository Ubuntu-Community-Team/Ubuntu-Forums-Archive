---
title: "Making space for Edgy 6.10"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by akadruid on 2006-10-27
Hi forum,

I have 6.06 installed on a 4GB disk and would like to upgrade to 6.10, but I cannot make enough free disk space for the install.

Aplogies if this is too much info, but I'm not sure what will be useful...!

'System Monitor' reports I have 797MB free and 601MB available.

When I run gksu "update-manager -c" and click the button to upgrade to Edgy I get a message saying I must make 234MB available in /var/apt/cache/.

I already been through 'Add/Remove' and uninstalled all the software I am not currently using.  There is nothing significant in my /home/ apart from  .cpan which is 45MB.  Can I make this smaller without causing myself problems with perl?  I suspect I made it so big getting bugzilla installed.

The /usr/share/ takes the most space, at 1GB.  The largest parts being /usr/share/eclipse and /usr/share/fonts.  I've uninstalled eclipse, /usr/share/eclipse seems to contain plugins still though.  Can I safely delete this?  What about the fonts?  I don't think I use many.

Finally would it be feasible to mount /usr/ or /var/ or something on a network share of some kind?  I have access to terabytes of space on various servers which I can use for whatever.  I have no idea how to do this though, and my google-fu has failed me so far.

Unfortunately I cannot add a larger physical disk.  (Background: this machine belongs to my company, it's been discarded as too slow and I have permission to use alongside my main machine which suffers from a certain other operating system - I have blanket permission to do whatever I like for software, but cannot play with the hardware at all.  It runs 6.06 like a charm despite only having a 400Mhz Celeron w/256MB RAM.  Although I cheat and run firefox on a remote x session over ssh from a much more powerful machine)

Thanks!!

akadruid

---

### Post by akadruid on 2006-10-27
Solved.

I made another 400mb space (making 1.0Gib total) with deborphan, removing /usr/share/eclipse/ and using synaptic to remove all but the current kernal image.

The upgrade tool now seems to work, I have got as far as it asking to download the new packages now.

---

