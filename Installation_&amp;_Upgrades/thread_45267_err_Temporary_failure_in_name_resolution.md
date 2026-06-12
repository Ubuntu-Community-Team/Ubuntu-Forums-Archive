---
title: "*err Temporary failure in name resolution"
date: 2005-06-29
forum: Installation &amp; Upgrades
---

### Post by polloz on 2005-06-29
Hello,

i have the following problem. everytime i boot up my machine, at the boot up log, everything goes fine except for a part that says "*err Temporary failure in name resolution". anyone knows why this is? everything works fine in my machine, except for one small thing, which is probably related to that error. my clock in the panel always gets desconfigured everytime i boot the pc, well it isn' really desconfigured, the time zone is right always (zone: America/Argentina/Buenos Aires) but the hour shown is wrong, its like 2 hours behind all the time.
are these two problems related? anyone knows how to solve both of them?
Thanks,

polloz

---

### Post by alastair on 2005-06-29
When your computer boot, after networking is up and (supposedly) configured, the system tries to do something like sync to a network time server (NTP, "network time protocol") e.g. ntp.ubuntulinux.org.

To find "ntp.ubuntulinux.org" requires DNS name resolution to be working i.e. working DNS,network etc.

This sounds like you have a network problem - at least at boot.

Also, the clock skew (drift in time) sounds like a h/w clock issue perhaps (or BIOS).

---

### Post by polloz on 2005-06-29
hmmmm
ok, I get it. my machine probably fails to get connected at boot up but once i enter gnome its already connected. is there something i can do to avoid the "fail" thing beeing shown at boot up? or instruct it not to connect at that moment? don't know, it took me some time to get my machine to recognize my modem and everything (i have an adsl usb modem). i don't want to do anything that might break my connection or what not.
regarding the clock issue, i know it's not a bios problem since in my other partition, i got crappy xp, and the time works fine in it. also at installing ubuntu, there was a part in the installation were it showed me if the time being displayed in it was ok, and it was. so i don't think it's really a bios issue.
what could it be?
thanks,

polloz

---

### Post by alastair on 2005-06-30
Is it the "NTP" (time server) failing DNS name resolution at boot?

If so, you could check by just disabling it i.e.

update-rc.d -f ntpdate remove

To stop the script (/etc/init.d/ntpdate) running at boot.

Is your timezone correct :

cat /etc/timezone

---

### Post by flytopia on 2005-07-01
[QUOTE=polloz]hmmmm
ok, I get it. my machine probably fails to get connected at boot up but once i enter gnome its already connected. is there something i can do to avoid the "fail" thing beeing shown at boot up? or instruct it not to connect at that moment? don't know, it took me some time to get my machine to recognize my modem and everything (i have an adsl usb modem). i don't want to do anything that might break my connection or what not.
regarding the clock issue, i know it's not a bios problem since in my other partition, i got crappy xp, and the time works fine in it. also at installing ubuntu, there was a part in the installation were it showed me if the time being displayed in it was ok, and it was. so i don't think it's really a bios issue.
what could it be?
thanks,

polloz[/QUOTE]
 I installed Ubuntu yesterday, and I'm getting the same problem with the NTP name resolution at boot.

I was also occasionally getting the same error (temporary failure in name resolution) in Synaptic when downloading packages from gb.archive.ubuntu.org. However, other times it worked fine. Everything else internet-ty works fine.

Could it just be that Ubuntu are having some problems with their DNS servers?

flytopia

---

### Post by alastair on 2005-07-01
[QUOTE=flytopia]Could it just be that Ubuntu are having some problems with their DNS servers?
[/QUOTE]

Either that ... or it's just you :-)

Could be your DNS server - router or ISP.

I have to admit that, for the past day, I have had extreme problems connecting to the update servers - extreme slowness, and failure. At first, I thought it was Ubuntu's servers, but today I checked to see if I had resolution via :

dig archive.ubuntu.com

This was fine on my desktop, but not on my laptop.

It turned out that I had forgotten that my /etc/resolv.conf file was still setup for a DNS server at work. I fixed this and all is well again.

---

