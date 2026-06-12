---
title: "How do I Upgrade CUPS?"
date: 2015-09-16
forum: Installation &amp; Upgrades
---

### Post by jonny13 on 2015-09-16
I am new to Ubuntu and Linux in general.

I have inherited CUPS version 1.39 Print Server and need to upgrade it.

I don't want to lose the config and need CUPS updated to at least 3.4.4 as it have read it fixes a Windows 7 printer installation bug.

Can anyone assist or point to a guide on the net?

---

### Post by ian-weisser on 2015-09-16
> **jonny13 said:**
> I don't want to lose the config and need CUPS updated to at least 3.4.4 

The latest release from cups.org is only 2.1.0...which is in Ubuntu 15.10.
Are you sure about needing 3.4.4? Where are you getting that version number from?

1.3.9 predates any supported release of Ubuntu, the oldest is 1.5.2 in Ubuntu 12.04. What release of Ubuntu are you running?

---

### Post by MAFoElffen on 2015-09-16
Do this and post the results
```

sudo lsb_release -a
sudo apt-cache show cups

```
From what you said... and from what ian-weisser noted... I wonder what version of what, you inherited.

Why do I wonder? Because cups 1.3.9 came with Ubuntu Jaunty 8.04. Whether Server or Desktop, it does not matter. There is no direct route to upgrade the system to a current LTS, because those repo's reach end-of-service many years ago. There is some work-around outside of Ubuntu, but I wouldn't recommend that to someone who is admittedly new to Ubuntu and new to Linux.

Do not try to do an update/upgrade on that old a system = that would fail outright.

What would I recommend? Analyze what is there and the config. Copy the config files, so you have a reference. Image or backup the server. Start fresh, with a current 14.04.03 LTS Server install. Configure to what settings the old server was set at, with installed services that the old server was providing.

That would be my recommendation.

---

### Post by jonny13 on 2015-09-30
Hi,

Thanks for the Replies, unfortunately I hadn't subscribed to the thread so have only just seen them.

I think it was Samba possibly that needs to 3.4.4 if that makes sense, so I think I may have been barking up the wrong tree here and it's samba I need updated.

I think MAFoElffen you are right it was a pre-packaged Ubuntu Jaunty 8.04 Package.

Unfortunately we do not have the ability to start fresh as it requires a bespoke package installer that we don't have.

The only option we have is to upgrade the current system.

If this requires Ubuntu to be updated before CUPS is updated I will need to do that or if it's just samba then I can do that.

---

### Post by ian-weisser on 2015-09-30
Well, a network-connected machine should certainly NOT be using 8.04. It is vulnerable to several published exploits, and has not received security updates since 2013, when that release reached EOL.

If that machine is accessible from the internet, raise a red flag and take that machine offline ASAP - a compromised server is a threat to your entire organization. It will be inconvenient, and perhaps expensive to replace in a hurry...but the potential liability of stolen information and further penetration may be greater. Only your organization can judge those risks.

Ubuntu is designed to have applications and OS upgrades as a whole - it's easier for us to test and support that way.
It's not designed to have some pieces upgraded and others not. You may get unexpected results, and our ability to help you will be limited.

Upgrading your current release of Ubuntu may work, though the path from 8.04 to 10.04 (also EOL) to 12.04 to 14.04 is rather chancy, especially since you have non-Ubuntu software installed. I have done that path, though not three release-upgrades in a row! I think the risk of breakage along that upgrade path is higher than I would be comfortable with. I recommend cloning your system, and experimenting on the clone. You may need to make fixes or changes after any of those release-upgrades.

Another option is to limit the scope of the problem - migrate the print server and other services onto a different (new) machine running, say, 14.04. Many services, like CUPS printsevers, can run on very lightweight hardware (like a Raspberry Pi), limiting your cost. This gives you a chance to secure and properly document those services so you never have this problem again. This solves your immediate problem with printing in a sustainable way...but does not solve the problem of your orphaned bespoke software. You already know you must solve that problem separately. Someday it will fail on you.

---

### Post by jonny13 on 2015-10-05
Thanks for the reply ian-weisser.

Unfortunately a new machine is not available otherwise I would have already done that.

I'm doing this on a side as I'm fed up getting the calls,which may last another year due to budget :(

The only option I have is the upgrade path due to the limitations of the hardware which will not allow me to put on a fresh install.

Fortunately I have a clone and will experiment on that.

Do you know of any guides on how to do an upgrade from 8.04 to 10.04 to 12.04 to 14.04?

---

