---
title: "VMWare with Win XP guest - antivirus needed?"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by Squrdel on 2006-10-25
I have VMWare running well on Dapper with WIN XP Home as guest. I use a D-Link router for my DSL and this has a hardware firewall. I have configured the VMWare network to run with NAT from the Dapper connection. I am not using   Windows for email and most of my internet work is done on Ubuntu.

Do I need antivirus protection? And spyware, trojans, etc.? And a firewall?

If anyone knows the answer to any or all of these questions I would be really happy for some guidance.

---

### Post by daou on 2006-10-25
Depends. I haven't installed any protection beyond the Windows firewall on my VMWare XP. It probably needs protection but because the Windows has no access to my system outside the virtual system, it isn't absolutely necessary. If it gets bogged down with viruses+spyware, I'll just reinstall it.

But surf the web through Linux and you'll dodge about 90% of potential viruses and spyware.

---

### Post by sharn on 2006-10-25
I would HIGHLY suggest an Antivirus anyhow. I'm mostly a Windows user, and just using your every day apps, its quite easy to get a virus. Just go get AVG Free. As the name suggests, it's free, it takes very little rescources... It's great, and what I use. (I use Ubuntu in VMWare.)

[http://free.grisoft.com/doc/avg-anti-virus-free/lng/us/tpl/v5](http://free.grisoft.com/doc/avg-anti-virus-free/lng/us/tpl/v5)

Looks like they also have Linux there too. I'm a newb to Linux, so I pose a questions back, do I need virus protection in Ubuntu?

I don't know just how much safer it is...

---

### Post by daou on 2006-10-25
I use NAT on my VMWare XP.
I attached the results of a port scan ([Shields UP]("https://www.grc.com/x/ne.dll?bh0bkyd2")) using Firefox in my VMWare XP. All ports stealthed because it's already protected by the Linux firewall.

---

### Post by daou on 2006-10-25
> 
Looks like they also have Linux there too. I'm a newb to Linux, so I pose a questions back, do I need virus protection in Ubuntu?

There is one common antivirus program for Linux, ClamAV. Not many people use antivirus in Linux however, because of the lack of developed viruses for Linux. In fact, probably the biggest reason you'd install antivirus on Linux is to prevent viruses spreading between Windows computers, if that's something you care about.

---

### Post by daou on 2006-10-25
But let's say a bad virus got onto the XP. Something that might erase an MBR or even mess up the BIOS. But what BIOS and MBR will it see? The virtual ones created by VMWare. Nothing a reinstall won't fix.

But yes, it's always better to be safe than sorry. I recommend using antivirus with a virtual XP, even though I don't use it myself.

---

