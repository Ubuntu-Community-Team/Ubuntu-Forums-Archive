---
title: "Why is edubuntu acting as dhcp server?"
date: 2013-02-25
forum: Installation &amp; Upgrades
---

### Post by mraiwalmsley on 2013-02-25
Hi everyone

Weird question for you?  We installed Edubuntu 12 on a crappy old desktop that was attached to our windows domain.  Came to work today and found this computer has been acting a DHCP server and providing IP's to various computers around the school for no apparent reason.  Our system worked fine prior and today this caused chaos.  Why does edubuntu do this on a fresh install?  I've used various linux distro's and never seen this happen.

I'm bothered it has put off my manager about trying edubuntu around the school now,as it suddenly became a PXE server too - as i was walking around the school last week I noticed edubuntu on a computer.

How is this possible?

---

### Post by benj23673 on 2013-04-24
I am having the same issue and let me tell you the ITdesk at my university was PISSED I was messing up all the network traffic during finals week at the library. I have ubuntu 12.10 but I am using wicd and I have purged network manager because they said that was the issue? I have a Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter.

---

### Post by lykwydchykyn on 2013-04-25
That's what edubuntu *is*.  It's designed for deployment on a PXE-boot server for use in school computer labs.  PXE booting requires a DHCP server configured to point clients to the PXE boot server, hence the DHCP services configured out of the box.

It's been a while since I set up edubuntu, but if I'm not mistaken it gives you the option of setting up a server install or a standalone workstation install.  Did you not see this when you set it up?

---

### Post by benj23673 on 2013-04-25
Why did this happen to me I am only running 12.10 ubuntu (I think ssh is the only server type thing I have installed) when I was connecting to the school wifi network I guess it was causing some trouble?

---

### Post by lykwydchykyn on 2013-04-25
> **benj23673 said:**
> Why did this happen to me I am only running 12.10 ubuntu (I think ssh is the only server type thing I have installed) when I was connecting to the school wifi network I guess it was causing some trouble?

No idea; I assumed since you said you were having the same issue that it was, well, the same issue.  Sounds like it's probably something totally other.

---

### Post by benj23673 on 2013-04-25
They said I was DCHPing on their network, and my computer was giving out IP addresses, they wouldn't explain anything else to me? They commented out dnsmasq in network manager and said that was the issue? If anyone has some more insight on this issue I would love to know more about what was going on and how a university's wireless network couldn't stop this?

---

### Post by lykwydchykyn on 2013-04-25
dnsmasq *can* be configured as a DHCP server.  It's installed on Ubuntu by default because it's used to cache DNS records (an optimization thing), but it's most definitely not configured by default to be a DHCP server.  Why yours was doing this, I can't guess.  Maybe you had an old config file in there from something set up before, who knows.

I would bet most networks don't protect against this kind of thing; their wireless hardware or switch would have to have the ability to filter out certain types of traffic on certain ports, and it would have to be configured.  Probably nobody thought that anyone would have a DHCP server running on his wireless device.

---

