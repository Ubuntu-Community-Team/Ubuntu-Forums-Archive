---
title: "Gutsy Beta, No Updates Upon Final?"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by phalkon30 on 2007-10-19
To start off, yes, I have searched (for about the last half hour actually) to find a solution or answer to this problem, but haven't found an answer yet (just speculation).

I followed some advice in the forums to install the Gutsy Beta before the release, so that when the servers were swamped, I could just upgrade a few little patches when final came out. I did this 2 days before the final release. I expected some updates when the final came out, but nothing came. I've checked a few times since it came out (about 12 hours ago was the last try), no updates.

To get the beta, I did something like
```
update-manager -d
``` (there might have been a -c in there as well, don't remember)

I tried repeating this, thinking maybe it would find the updates, nope. I tried removing the -d when I did the terminal command, nope.

Any suggestions? Did I really get the full version 2 days before release? Is there a way to check? I'm a very very recent linux user with little to no console command knowledge, but am willing to learn.

---

### Post by dpar on 2007-10-19
Did you get a pile of updates right after installing the beta?? If so, you are up to date and are on the final.

---

### Post by phalkon30 on 2007-10-19
I realized I've been saying beta when I meant RC (I think), but either way.

No, I do not remember seeing any updates after installing the RC. I'll admit however that I'm very tired, and could be wrong on that.

---

### Post by elnur on 2007-10-19
So there is no reason to do clean reinstall after final release to switch from beta to final? 
I see no update in last two days. Does this mean that beta will not receive any updates and I should do clean reinstall to get final version or there weren't any updates in last two days?

---

### Post by PriceChild on 2007-10-19
> <ubotu> If you installed a Tribe/Beta/RC version of Ubuntu 7.10 (Gutsy Gibbon) and have been keeping it up to date, then you are already running the latest version of Gutsy. To make sure, type « sudo apt-get update && sudo apt-get dist-upgrade » in a console.:)

---

### Post by HappyChriss on 2007-10-19
Hi,
I got a lot of update for the beta (even 2 days ago).
Questions - as above:  

Will Ubuntu move automatically from beta to final ?
How can I didentify, if am "final" ?

I belive quite a lot people who installed the beta would like to go to final. Maybe a short section in the upgrade part in ubuntu.com would help a lot.

Thanks a lot & Regards
 Christian

---

### Post by phalkon30 on 2007-10-19
Ok, thanks PriceChild, I will try that when I get home.

As others have said though, is there a way to find out if you're on the final, or is final just a term used to describe what level of updates you have?

---

### Post by Topsiho on 2007-10-19
I got no updates for Gutsy the last two days, so I think this is OK. Before that I was swamped with updates for RC, but it is quite quiet now :)
It should get far more quiet now that Gutsy is final.
Topsiho

---

### Post by nike984 on 2007-10-19
Type 

```
cat /etc/issue.net ; uname -a
```

if you have something like

```

Ubuntu 7.10
Linux nike984-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
```

then, yes, you are using the final version.

---

### Post by prizrak on 2007-10-19
I got a somewhat related question, any time I try to reload all the repo information it hangs on about half of them. Anyone else see that?

---

### Post by phalkon30 on 2007-10-19
Ok, PriceChild, I did what you said and it found nothing to update.

Nike, I did what you said and got exactly the same thing (with a different username obviously). 

So that means that I am up to date. I appreciate the help everybody. Should I tag the thread title as solved?

---

### Post by WebDrake on 2007-10-21
> **Topsiho said:**
> I got no updates for Gutsy the last two days, so I think this is OK. Before that I was swamped with updates for RC, but it is quite quiet now :)
It should get far more quiet now that Gutsy is final.
Topsiho

I do hope there will be further updates soon.  That "swamp" included some regressions so that things working perfectly on my machine in the beta ceased to function ... :-(

To date: kernel upgrades (2.6.22-13 and -14) hang at boot with a COMRESET error (a bug which doesn't appear to be getting any attention on Launchpad), and Kopete crashes (this I think is a bug in kdelibs which a fix has been made for, but not released).

I would do a dist-upgrade but really don't want to lose the kernel 2.6.22-12 that successfully boots.

---

