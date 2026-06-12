---
title: "Upgrade in Terminal"
date: 2014-04-04
forum: Installation &amp; Upgrades
---

### Post by The Frenchman on 2014-04-04
I'm running Lubuntu 12.04 but would like to upgrade to the latest LTS, on another machine I've experienced problems using Update Manager so is it possible to upgrade using terminal?

---

### Post by TheFu on 2014-04-04
12.04 is the latest LTS release.

Once 14.04 is available, you'll see an announcement to "do-upgrade" when you login.  Be certain to perform a 100% recoverable backup before.

When I say login - that means both thru the GUI and thru an ssh session.

On one of my 10.04 servers here, I see this at every ssh login:
> New release 'precise' available.
Run 'do-release-upgrade' to upgrade to it.

I expect the same with 14.04.  I'll wait at least a month after the official release for common bugs to be found and fixed. 12.04 has plenty of support left, so there isn't any hurry.

---

### Post by mörgæs on 2014-04-04
No, there's no support for Lubuntu.
You could install Lubuntu 14.04 now if you are ready for a beta or take 13.10 until June.

---

### Post by oldos2er on 2014-04-04
> **TheFu said:**
> 12.04 is the latest LTS release.

That's true for default Ubuntu, but Lubuntu 12.04 was not an LTS, as mörgæs said. I'd advise a clean install of 14.04 when it's released.

---

### Post by The Frenchman on 2014-04-05
I think a clean install after back-up is the way to go.Even though 12.04 is no longer supported I'm still getting daily updates,most of which are security based.is it still safe to use for internet banking, paypal etc?

---

### Post by mörgæs on 2014-04-05
It's very hard to promise that something is secure. 
I wouldn't take the chance but install one of the versions I mentioned.

---

### Post by grahammechanical on 2014-04-05
Update Manager is a GUI front end for running terminal commands. So, if Update manager is having problems it could be that you will get the same problems with running apt-get terminal commands.

```
sudo do-release-upgrade
```

Regards.

---

### Post by The Frenchman on 2014-04-06
After doing "sudo do-release-upgrade" getting "no new release found"

---

### Post by TheFu on 2014-04-06
> **The Frenchman said:**
> After doing "sudo do-release-upgrade" getting no new release found

14.04 has not been released. Check again next month.

2 moderators have been clear they don't believe the upgrade for LUBUNTU from 12.04 to 14.04 is supported. That is code for it isn't tested and there could be issues. Nobody knows how many big or small issues there could be. You will be taking 100% responsibility for any issues.  OTOH - if you aren't paying for support, then you are already responsible for everything anyway.

BTW - my signature says that I'm running Lubuntu - but that is not exactly correct.  I install Ubuntu server, then add LXDE manually over it.  Been doing that since 10.04 (really since 11.04 when Unity became the default), but since I'm an LTS-only guy ... 

As to safe for online banking - NO.  This is my opinion.  No general use desktop should be used for online banking.  Create a read-only OS (usually a live-CD is the easiest way) and use that for online banking. That means reboot to load the CD to do your banking. [This has been recommended by noted security writer Brian Krebs for years.]("http://krebsonsecurity.com/2012/07/banking-on-a-live-cd/")  The more money you have, the more important this is.  **If you doing banking for a business it is an absolute MUST since banking protections do not apply to businesses like those protections do for consumers.**

---

### Post by The Frenchman on 2014-04-06
> **TheFu said:**
> 14.04 has not been released. Check again next month.

2 moderators have been clear they don't believe the upgrade for LUBUNTU from 12.04 to 14.04 is supported. That is code for it isn't tested and there could be issues. Nobody knows how many big or small issues there could be. You will be taking 100% responsibility for any issues.  OTOH - if you aren't paying for support, then you are already responsible for everything anyway.

BTW - my signature says that I'm running Lubuntu - but that is not exactly correct.  I install Ubuntu server, then add LXDE manually over it.  Been doing that since 10.04 (really since 11.04 when Unity became the default), but since I'm an LTS-only guy ... 

As to safe for online banking - NO.  This is my opinion.  No general use desktop should be used for online banking.  Create a read-only OS (usually a live-CD is the easiest way) and use that for online banking. That means reboot to load the CD to do your banking. [This has been recommended by noted security writer Brian Krebs for years.]("http://krebsonsecurity.com/2012/07/banking-on-a-live-cd/")  The more money you have, the more important this is.  **If you doing banking for a business it is an absolute MUST since banking protections do not apply to businesses like those protections do for consumers.**
Thanks for the online banking info.I'm aware 14.04 is only beta at the moment,what I was attempting was to upgrade to a release that was still supported,just for that added bit of security, until the final version of the LTS was available.

---

### Post by TheFu on 2014-04-06
> **The Frenchman said:**
> Thanks for the online banking info.I'm aware 14.04 is only beta at the moment,what I was attempting was to upgrade to a release that was still supported until the final version of the LTS was available.

I wouldn't.  Here's why:
* 12.04 updates (not necessarily upgrades) to 12.10 or 14.04.
* Next need to update 12.10 --- > 13.04 ---> 13.10 ---> 14.04.
Wait until next month and try the direct route to 14.04. Must easier.

13.04 is NOT supported.  12.10 is supported for base Ubuntu and Server. I never ran that release - the main things that it adds (from my perspective) were added Canonical tracking and some better UEFI support. Doubtful you need either.

Going to 13.10 is a bad idea, since the support for it ends in July.  Better to stay on 12.04, IMHO.

Here's the official support doc: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

According to this: [https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu) any lubuntu release gets 18 months of support.

I can understand the need to migrate immediately - perhaps you are at a location TODAY that you won't be at next week or next month.  12.04 will get security patches for the non-GUI parts for a few more years.

Wish there was a better answer.

---

### Post by The Frenchman on 2014-04-06
Thanks, your answer is very comprehensive I'll wait to do the clean install........and stay away from paypal etc until then.And you've also answered why I can't get ClamTK  GUI updates

---

### Post by mörgæs on 2014-04-06
> **TheFu said:**
> 
According to this: [https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu) any lubuntu release gets 18 months of support.


No, support can never be longer than what Ubuntu offers.

---

### Post by mörgæs on 2014-04-06
> **The Frenchman said:**
> Thanks, your answer is very comprehensive I'll wait to do the clean install........and stay away from paypal etc until then.And you've also answered why I can't get ClamTK  GUI updates

If this solves the problem please mark the thread so.

---

