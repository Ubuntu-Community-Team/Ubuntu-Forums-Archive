---
title: "Deployment on several computers (cloning)"
date: 2012-01-24
forum: Installation &amp; Upgrades
---

### Post by Braistorms on 2012-01-24
Hi there, I'm trying to deploy linux and ubuntu on 20 computers with identical hardware. It was decided (not by me) to install ubuntu over windows using wubi when preparing the master pc. I know what to do with windows before/after cloning, but my linux knowledge fails me. What should I do before/after the cloning? We are using a DHCP so network settings/ IPs are not a problem. Thanks in advance for your answers.

---

### Post by sanderd17 on 2012-01-24
If it were pure Linux, you can just clone the hard disk, and everything will work. There is no need to run scripts to recognise drivers or similar. This even works between different systems, as long as the architecture is the same (32-bit, 64-bit, arm, ...) and there are no proprietary drivers needed.

But with a Wubi install, I don't know how you can add the Linux entry to the Windows bootloader without doing a fresh installation.

---

### Post by darkod on 2012-01-24
If the person who made the decision about wubi is not aware that you can expect problems running wubi long term, you better warn him right now. I doubt 20 computers are for some short test.

Anyway, if you can clone it together with windows (not only wubi), I guess it should be easy. Same as with any program you have inside you cloned image of windows.

Not sure if UUIDs or similar will make a problem, but you can give it a go.

---

### Post by Braistorms on 2012-01-24
Hi, I went as far as installing the master pc and cloning it to another one, everything seems to be working fine. I can boot both Operating Systems. My question is, will i have problems if all the ubuntu installations have the same computer name? Or something in that direction.

---

### Post by Lars Noodén on 2012-01-24
If you can move away from Wubi, you could image using [radmind](http://rsug.itd.umich.edu/software/radmind/).  It's in wide use in university classroom labs.

---

### Post by darkod on 2012-01-24
> **Braistorms said:**
> Hi, I went as far as installing the master pc and cloning it to another one, everything seems to be working fine. I can boot both Operating Systems. My question is, will i have problems if all the ubuntu installations have the same computer name? Or something in that direction.

Of course you will not be able to put the same computer names on the same network (this also goes for static IP addresses but you alreadu said you use DHCP).

Once cloned change the name before plugging it into the network. This goes for windows and ubuntu, both.

---

### Post by Braistorms on 2012-01-24
Will "sudo hostname -v newhostname" do?

---

### Post by newbie-user on 2012-01-24
> **Braistorms said:**
> Will "sudo hostname -v newhostname" do?

Yes, you could do that. Alternatively, you could edit the hostname in /etc/hostname. Having the computers already plugged into the network before changing the hostname shouldn't be a problem, as the hostname is only local to each computer. Since you're using DHCP, and probably a local DNS, all your hostname references can be added to DNS so that you can access each computer over the network via its hostname.

---

### Post by oldfred on 2012-01-25
Wubi is fine for a longer term test of Ubuntu than the liveCD for those who are primarily Windows users and are not sure they want to keep Ubuntu.

But even the creator of wubi does not expect you to keep it.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

